# Contributing to Russkiy

Thanks for your interest in contributing! This guide will help you get set up and submit changes.

## Development Setup

1. **Clone the repo**

   ```bash
   git clone https://github.com/Muhoro-art/ruskiy.git
   cd ruskiy
   ```

2. **Install dependencies**

   ```bash
   npm install
   ```

3. **Start infrastructure**

   ```bash
   docker compose -f infra/docker/docker-compose.yml up -d
   ```

4. **Start the services** (in separate terminals)

   ```bash
   # API
   cd services/api && cp .env.example .env && go run cmd/server/main.go

   # ML
   cd services/ml && pip install -r requirements.txt && uvicorn src.main:app --port 8090

   # Web
   npm run dev:web

   # Mobile
   npm run dev:mobile
   ```

## Project Structure

| Directory | Language | Description |
|-----------|----------|-------------|
| `apps/web` | TypeScript | Next.js web app |
| `apps/mobile` | TypeScript | Expo / React Native mobile app |
| `services/api` | Go | REST API server |
| `services/ml` | Python | ML error classifier & pronunciation |
| `packages/shared` | TypeScript | Shared types across apps |
| `infra/docker` | YAML | Docker Compose for local infra |

## Branching

- `main` — stable, production-ready code
- Feature branches — `feature/<short-description>`
- Bug fixes — `fix/<short-description>`

## Making Changes

1. Create a branch off `main`:

   ```bash
   git checkout -b feature/your-feature
   ```

2. Make your changes. Follow the conventions of the existing code.

3. **Run tests** before committing:

   ```bash
   # Go tests
   cd services/api && go test ./...

   # Python tests
   cd services/ml && python -m pytest

   # TypeScript
   npm run typecheck
   npm run lint
   ```

4. Commit with a clear message:

   ```bash
   git commit -m "Add brief description of your change"
   ```

5. Push and open a pull request:

   ```bash
   git push origin feature/your-feature
   ```

## Commit Messages

Keep them short and descriptive:

- `Add placement test scoring logic`
- `Fix session XP calculation for streaks`
- `Update seed data for beginner content`

## Code Style

- **Go** — `gofmt` formatting, standard project layout
- **TypeScript** — follow existing ESLint config
- **Python** — PEP 8, type hints where practical

## Pull Requests

- Keep PRs focused — one feature or fix per PR
- Include a brief description of what changed and why
- Make sure all tests pass
- Link related issues if applicable

## Reporting Issues

Open an issue on GitHub with:

- A clear title
- Steps to reproduce (if it's a bug)
- Expected vs actual behavior
- Environment details (OS, browser, etc.)

## Questions?

Open a discussion or issue — happy to help.
