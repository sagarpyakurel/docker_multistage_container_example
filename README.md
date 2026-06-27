# 🚀 Multi-stage Docker example — Go app

A tiny, practical example that shows how to build and run a Go application with a multi-stage Docker setup. The first stage compiles the Go binary; the runtime stage produces a small image that only contains the compiled executable.

Why this repo
- Demonstrates multi-stage Dockerfile patterns that keep runtime images minimal.
- Includes simple, ready-to-run commands so you can build, run, and inspect the container quickly.

Quick start (most important commands)

1) Build the image

```bash
# Build a multi-stage image (produces a compact runtime image)
docker build -t multi-stage_go_image .
```

2) Run the container

```bash
# Run detached, name it, and map port 8080
docker run --name multi-stage_container -p 8080:8080 -d multi-stage_go_image
```

Inspect & debug

```bash
# Open an interactive shell inside the running container
docker exec -it multi-stage_container sh

# View container logs
docker logs -f multi-stage_container
```

Helpful cleanup commands

```bash
# Remove dangling and unused images
docker image prune -a -f

# Full system prune including unused volumes
docker system prune -a --volumes -f
```

Files of interest
- Dockerfile.build — build stage (compiles the Go binary)
  https://github.com/sagarpyakurel/docker_multistage_container_example/blob/main/Dockerfile.build
- Dockerfile.runtime — runtime stage (small final image)
  https://github.com/sagarpyakurel/docker_multistage_container_example/blob/main/Dockerfile.runtime
- main.go — example Go source
  https://github.com/sagarpyakurel/docker_multistage_container_example/blob/main/main.go

Notes
- Build first, then run. The app listens on port 8080 by default (see main.go).
- If you want this README to show on the repo front page, I created README.md — you can remove the old `Readme` file if you prefer.

If you'd like, I can:
- Replace the old `Readme` file with this one (rename/cleanup).
- Add a short example of the app’s HTTP response.
