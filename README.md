# jwt-auth-example

A simple JWT authentication middleware example for Express.js applications.

## Installation

```bash
npm install
```

## Usage

The `auth.js` file provides an `authenticate` middleware function that can be used to protect routes in an Express application.

### Authentication Middleware

```javascript
const { authenticate } = require("./auth");

// Use in your Express routes
app.get("/protected", authenticate, (req, res) => {
  res.json({ user: req.user });
});
```

### How it works

1. Extracts the JWT token from the `Authorization` header
2. Supports "Bearer " prefix (e.g., "Bearer your-token-here")
3. Verifies the token using the `JWT_SECRET` environment variable
4. Sets `req.user` with the decoded token payload
5. Returns 401 status for missing or invalid tokens

### Environment Variables

- `JWT_SECRET` - Secret key used to verify JWT tokens
- `PORT` - Server port (default: 3000)

### Running the Example Server

```bash
# Set your JWT secret
export JWT_SECRET=your-secret-key

# Start the server
npm start
```

## API Endpoints

- `GET /public` - Public endpoint (no authentication required)
- `GET /protected` - Protected endpoint (requires valid JWT token)

## Testing Authentication

To test the protected endpoint, include the JWT token in the Authorization header:

```bash
curl -H "Authorization: Bearer your-jwt-token" http://localhost:3000/protected
```
# jwt-auth-example
