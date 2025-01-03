# helm-kubectl-nexus-push

Build utilites image for CI/CD process, ex: Gitlab CI pipeline image.

## Build

```bash
# build
docker build -t helm-kubectl-nexus-push:v1.0.0 .

# run
docker run --rm -it helm-kubectl-nexus-push:v1.0.0

# list installed packages
apk info --installed --all
```
