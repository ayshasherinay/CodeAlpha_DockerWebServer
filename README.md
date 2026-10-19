# CodeAlpha Task 4: Web Server using Docker

A simple Nginx web server running inside a Docker container.
Built for the CodeAlpha DevOps Internship by Aysha Sherin.

## What I learned
- What Docker images and containers are
- How to write a Dockerfile
- Container lifecycle commands
- Health checks and troubleshooting
- Running the project with Docker Compose

## Files
- `index.html`: the web page
- `Dockerfile`: instructions to build the image
- `docker-compose.yml`: one-command setup

## How to run
```
docker compose up -d --build
```
Open http://localhost:8080

## Lifecycle commands
| Command | What it does |
|---|---|
| `docker compose up -d --build` | Build and start |
| `docker ps` | List running containers |
| `docker stop webserver` | Stop |
| `docker start webserver` | Start again |
| `docker restart webserver` | Restart |
| `docker logs webserver` | View logs |
| `docker exec -it webserver sh` | Open a shell inside |
| `docker compose down` | Stop and remove |

## Health check
The Dockerfile has a HEALTHCHECK that checks the server every 30 seconds.
Check it with:
```
docker inspect --format='{{.State.Health.Status}}' webserver
```

## Troubleshooting
- Port 8080 already in use: change it to `8081:80` in docker-compose.yml
- Page not updating: rebuild with `docker compose up -d --build`, then press Ctrl+F5
- `docker compose` not found: install `docker-compose-v2`
