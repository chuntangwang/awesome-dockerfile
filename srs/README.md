# SRS

Repack [ossrs/srs](https://github.com/ossrs/srs) with ffmpeg 6.1.1

## Requirement

Build [Dockerfile.static.6.1.1](../ffmpeg) image first.

## Build

### **[Dockerfile.src](Dockerfile.src)**

build srs source code on latest `6.0release` branch.

* Update branch name on `line 17` if needed.
```dockerfile
ENV SRS_BRANCH="6.0release"
```

Build image
```bash
docker build -t srs:v6.0.158-ff6 -f Dockerfile.src .
```

### **[Dockerfile.srs](Dockerfile.src)**

repack official srs image with new ffmpeg.

Update version on `line 5` if needed.
```dockerfile
FROM ossrs/srs:v6.0.158
```

Build image
```bash
docker build -t srs:v6.0.158-ff6 -f Dockerfile.srs .
```
