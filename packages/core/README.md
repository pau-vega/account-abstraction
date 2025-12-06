# @passkeys-server/errors

A centralized error handling package for the passkeys server, providing standardized error classes and error codes for consistent error management across the application.

## Features

- **Base Error Class**: Extensible `BaseError` with HTTP status codes and operational flags
- **HTTP Error Classes**: Standard HTTP errors (400, 401, 404, 409)
- **Domain-Specific Errors**: Custom errors for authentication and user management
- **Error Codes**: Predefined constants for consistent error identification
- **Type-Safe**: Full TypeScript support

## Installation

```bash
# From workspace root
pnpm install @passkeys-server/errors
```

## Usage

### Using Helper Functions

```typescript
import { BadRequestError, UnauthorizedError, ERROR_CODES } from "@passkeys-server/errors";

// Throw an error with a predefined error code
throw BadRequestError("Invalid request", ERROR_CODES.INVALID_REQUEST);

// Throw an error without a code
throw UnauthorizedError("Access denied");
```

### Using Error Classes

```typescript
import { BaseError } from "@passkeys-server/errors";

class CustomError extends BaseError {
  constructor(message: string, code?: string) {
    super("CustomError", message, 500, code);
  }
}
```

### Available Error Types

- `BadRequestError` (400)
- `UnauthorizedError` (401)
- `NotFoundError` (404)
- `ConflictError` (409)
- `InvalidCredentialsError` (401)
- `UserAlreadyExistsError` (409)

### Error Codes

The package exports predefined error codes via `ERROR_CODES`:

```typescript
ERROR_CODES.AUTHENTICATION_FAILED;
ERROR_CODES.CHALLENGE_EXPIRED;
ERROR_CODES.USER_NOT_FOUND;
// ... and more
```

## Error Properties

All errors extend `BaseError` and include:

- `name`: Error name
- `message`: Error message
- `statusCode`: HTTP status code
- `code`: Optional error code for identification
- `isOperational`: Flag indicating if error is operational (default: true)
- `stack`: Stack trace

## License

MIT
