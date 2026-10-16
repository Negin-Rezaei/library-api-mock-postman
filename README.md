# Library API – Postman Mock Server

A Postman mock server that simulates a **Library REST API**, with automated API tests.

This project shows how a QA engineer can start API testing **before the backend is ready**: the API contract is defined first, a mock server is generated from saved examples, and the tests run against the mock. When the real backend is ready, only `baseUrl` has to change.

## What This Project Demonstrates

- **Contract-first testing:** each endpoint is defined with its request and its expected responses (success and error)
- **Postman Mock Server:** a mock server generated from the collection's saved examples
- **Response selection:** the `x-mock-response-code` and `x-mock-response-name` headers choose which example the mock returns
- **Error simulation:** 400, 404 and 500 responses are tested without a real backend
- **Dynamic mock data:** Postman dynamic variables (`{{$randomInt}}`, `{{$randomUUID}}`, `{{$isoTimestamp}}`) make each response realistic and different
- **Automated tests:** status codes, response time, headers and response body structure are checked
- **Environments:** `baseUrl` is stored in an environment, so tests can move from the mock to the real API without changes
- **Execution:** the collection runs in the Postman Collection Runner and in Newman (CLI)

## API Under Test

| Method | Endpoint      | Description          |
|--------|---------------|----------------------|
| GET    | `/books`      | Get all books        |
| GET    | `/books/{id}` | Get a book by its id |
| POST   | `/books`      | Create a new book    |

## Test Scenarios

| Type     | Scenario                        | Expected |
|----------|---------------------------------|----------|
| Positive | Get all books                   | 200      |
| Positive | Get a book by id                | 200      |
| Positive | Create a book                   | 201      |
| Negative | Server error on get all books   | 500      |
| Negative | Book not found                  | 404      |
| Negative | Create a book without a title   | 400      |

## Project Structure

```
.
├── collections/    # Postman collection: requests, saved examples and tests
└── environments/   # Mock server environment (baseUrl)
```

## Tools

Postman · Postman Mock Server · Newman · JavaScript (Postman test scripts)
