# Daily Quote API

A RESTful API for managing daily quotes, built with TypeScript, Node.js, Express.js, and PostgreSQL using TypeORM. Deployed on Render.

## Features

- Full CRUD operations (Create, Read, Update, Delete)
- Support for all HTTP verbs (GET, POST, PUT, DELETE)
- PostgreSQL database with TypeORM
- Express.js for routing and middleware
- Built-in JSON body parsing
- CORS support
- Environment-based configuration (.env.dev and .env.prod)
- Authentication and authorization support
- Heavily commented codebase for educational purposes
- Functional programming paradigm
- Pure functions with minimal side effects
- No classes or stateful objects (except for TypeORM entities)
- Deployed on Render platform

## API Endpoints

| Method | Endpoint       | Description              |
| ------ | -------------- | ------------------------ |
| GET    | /quotes        | Get all quotes           |
| GET    | /quotes/random | Get a random quote       |
| GET    | /quotes/:id    | Get quote by ID          |
| POST   | /quotes        | Create a new quote       |
| PUT    | /quotes/:id    | Update an existing quote |
| DELETE | /quotes/:id    | Delete a quote           |

## Project Structure

```
DSA/
├── dist/               # Compiled JavaScript files
├── src/                # TypeScript source code
│   ├── config/         # Configuration files
│   │   ├── database.ts # TypeORM configuration
│   │   └── auth.ts     # Authentication configuration
│   ├── entities/       # TypeORM entities
│   │   ├── Quote.ts    # Quote entity definition
│   │   └── User.ts     # User entity definition
│   ├── index.ts        # Main entry point
│   ├── server.ts       # Express server and route handlers
│   └── quoteService.ts # Database operations handler
├── package.json        # Project dependencies
├── tsconfig.json       # TypeScript configuration
├── render.yaml         # Render deployment configuration
├── .env.dev           # Development environment variables
├── .env.prod          # Production environment variables
└── README.md          # Project documentation
```

## Environment Configuration

The project uses different environment files for development and production:

### Development Environment (.env.dev)
```env
DB_HOST=localhost
DB_PORT=5432
DB_USERNAME=postgres
DB_PASSWORD=postgres
DB_NAME=quotes_db
PORT=4000
JWT_SECRET=your_development_secret
```

### Production Environment (.env.prod)
```env
DB_HOST=your_production_host
DB_PORT=5432
DB_USERNAME=your_production_username
DB_PASSWORD=your_production_password
DB_NAME=quotes_db
PORT=4000
JWT_SECRET=your_production_secret
```

The environment file is automatically selected based on the `NODE_ENV` environment variable:
- Development: `NODE_ENV=development` (default)
- Production: `NODE_ENV=production`

## Installation Steps

1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd DSA
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Create environment files:
   - Copy `.env.dev.example` to `.env.dev` for development
   - Copy `.env.prod.example` to `.env.prod` for production
   - Update the values according to your environment

4. Build the project:
   ```bash
   npm run build
   ```

5. Start the server:
   ```bash
   # Development
   npm start

   # Production
   NODE_ENV=production npm start
   ```

## Deployment on Render

The project is configured for deployment on Render using the `render.yaml` configuration file. The configuration includes:

```yaml
services:
  - type: web
    name: dsa-quotes-api
    env: node
    buildCommand: npm install
    startCommand: npm start
```

To deploy on Render:

1. Create a new Web Service on Render
2. Connect your GitHub repository
3. Render will automatically detect the `render.yaml` configuration
4. Set up the following environment variables in Render's dashboard:
   - `DB_HOST`
   - `DB_PORT`
   - `DB_USERNAME`
   - `DB_PASSWORD`
   - `DB_NAME`
   - `PORT`
   - `JWT_SECRET`
   - `NODE_ENV=production`

## Available Scripts

- `npm start`: Start the development server
- `npm run build`: Build the TypeScript project
- `npm run typeorm`: Run TypeORM CLI commands
- `npm run migration:generate`: Generate a new migration
- `npm run migration:run`: Run pending migrations
- `npm run migration:revert`: Revert the last migration

## Dependencies

### Main Dependencies
- express: ^5.1.0
- typeorm: ^0.3.20
- pg: ^8.11.3
- dotenv: ^16.5.0
- bcrypt: ^6.0.0
- jsonwebtoken: ^9.0.2
- reflect-metadata: ^0.1.13

### Development Dependencies
- typescript: ^5.3.3
- ts-node: ^10.9.2
- @types/node: ^20.11.19
- @types/express: ^5.0.2
- @types/bcrypt: ^5.0.2
- @types/jsonwebtoken: ^9.0.9

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License.
