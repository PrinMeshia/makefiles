# Angular SSR Project - Makefile Commands

This project uses Makefile commands to simplify development, testing, and deployment of an Angular Server-Side Rendering (SSR) application. Below you will find instructions and descriptions for each available command.

## Prerequisites

- Make sure you have [Make](https://www.gnu.org/software/make/) installed on your machine.
- Docker is required for running the application in containers.

## Installation

Install all required dependencies:

```bash
make install
```

## Local Development

Start the Angular SSR server locally:

```bash
make start-ssr
```

## Docker Usage

Build and start the application in Docker containers:

```bash
make docker-up
```

Stop and remove the running Docker containers:

```bash
make docker-down
```

## Build

Perform a full SSR build of the project:

```bash
make build-ssr
```

## Testing

Run all unit and integration tests:

```bash
make test
```

## Additional Information

- These commands are managed via the project's `Makefile` and streamline common development workflows.
- For custom configuration, refer to the project's Makefile and Dockerfile.

---

Feel free to contribute or open issues for improvements!
