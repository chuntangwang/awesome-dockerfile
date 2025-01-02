# ffmpeg

Build static ffmpeg binary on Ubuntu 20.04

## Build

### [Dockerfile.static.6.1.1](Dockerfile.static.6.1.1)

Build static binary of ffmpeg 6.1.1

```bash
docker build -t ffmpeg-static:6.1.1 -f Dockerfile.static.6.1.1 .
```