# Event Ticketing Backend API

A backend service built with Elixir and Phoenix for managing live events, ticket inventory, and attendee check-ins.

## Project Overview

This project is a backend API built with Elixir and the Phoenix Framework that models a simplified live event ticketing system.

The goal of the project was to learn Elixir and Phoenix by building a real-world backend service focused on concurrency-safe operations, clean domain modeling, and scalable API design.

Inspired by real-world ticketing platforms such as DICE.

## Features

- Create and list live events
- Ticket inventory management per event
- Concurrency-safe ticket reservation
- Ticket lifecycle management (available → reserved → checked-in)
- API endpoints for event browsing and ticket check-in
- Dockerised local development environment

## Tech Stack

- Elixir
- Phoenix Framework
- Ecto + PostgreSQL
- RESTful JSON APIs
- Docker & Docker Compose
- ExUnit (testing)

## Architecture Overview

The application follows Phoenix’s context-based architecture:

- Contexts encapsulate business logic and domain rules
- Controllers handle HTTP requests and responses
- Ecto schemas represent persisted data models
- Database operations are handled via Ecto repositories and transactions

This separation allows the application to remain scalable, testable, and easy to extend.

## API Endpoints

### Events

- `POST /api/events` – Create a new event
- `GET /api/events` – List upcoming events
- `GET /api/events/:id` – View event details

### Tickets

- `POST /api/tickets/reserve` – Reserve a ticket for an event
- `POST /api/tickets/:id/check_in` – Check in a ticket

## Concurrency & Business Logic

Ticket reservations are handled using database transactions to ensure that ticket inventory cannot be oversold, even under concurrent requests.

Elixir’s functional design and Ecto transactions are used to ensure data consistency and predictable state transitions throughout the ticket lifecycle.

## Running the Project Locally

### Prerequisites

- Elixir
- Erlang
- Docker & Docker Compose
- PostgreSQL (if running without Docker)

#### Windows notes

If you're on Windows, you can either:

- Use WSL2 (recommended) and follow the Linux instructions above.
- Or install native Windows versions of Elixir/Erlang and PostgreSQL, and run commands in PowerShell.

If you choose WSL2, make sure Docker Desktop is configured to use the WSL2 backend.

### Setup

```bash
git clone https://github.com/your-username/event_ticketing_api.git
cd event_ticketing_api
mix setup
mix phx.server
```

Visit:

http://localhost:4000

(You’ll refine this once Docker is added.)

## Tests

Basic tests are included to verify:

- Event creation
- Ticket reservation logic
- Ticket status transitions

Tests can be run with:

```bash
mix test
```

## What I Learned

- Fundamentals of Elixir and functional programming
- Phoenix context-based architecture
- Designing concurrency-safe backend logic
- Modeling real-world business rules in a backend system
- Using Ecto transactions to maintain data integrity

## Future Improvements

- Add authentication and authorization
- Introduce background jobs for ticket expiration
- WebSocket support for live ticket availability
- GraphQL API layer
- Rate limiting on ticket reservations

## License

MIT
