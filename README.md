# nodejs-demo-app — CI/CD with GitHub Actions

A small Node.js app with a GitHub Actions pipeline that tests, builds and pushes a Docker image to DockerHub on every push to `main`.

## Pipeline (`.github/workflows/main.yml`)
1. **test** — checkout, set up Node 20, `npm install`, `npm test`
2. **build-and-push** (runs only if `test` passes) — log in to DockerHub, build the image with Buildx, push `latest` and the commit SHA tag

## Setup
1. Create a DockerHub access token (Account Settings → Security).
2. In the GitHub repo: Settings → Secrets and variables → Actions, add:
   - `DOCKERHUB_USERNAME`
   - `DOCKERHUB_TOKEN`
3. Push to `main` and watch the **Actions** tab.

## Run locally
```bash
npm test
docker build -t nodejs-demo-app .
docker run -p 3000:3000 nodejs-demo-app
curl localhost:3000/health
```

## Screenshots
Add screenshots of the successful workflow run and the image on DockerHub here.
