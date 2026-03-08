# Legacy Python

Base images for all end-of-life Python versions (0.9.1, 1.x, 2.x, and select 3.x releases). More recent versions of Python 3 are readily available through the official [Docker Python image](https://hub.docker.com/_/python) and version management tools like [pyenv](https://github.com/pyenv/pyenv) or [uv](https://github.com/astral-sh/uv).

## Versions

Images are available on [Docker Hub](https://hub.docker.com/r/j4ckofalltrades/legacy-python/tags) and [GitHub Container Registry](https://github.com/j4ckofalltrades/legacy-python/pkgs/container/legacy-python/versions?filters%5Bversion_type%5D=tagged).

| Version | Dockerfile                           | Docker Hub                                                                                                    |
|---------|--------------------------------------|---------------------------------------------------------------------------------------------------------------|
| 0.9.1   | [0.9.1/Dockerfile](0.9.1/Dockerfile) | [j4ckofalltrades/legacy-python:0.9.1](https://hub.docker.com/r/j4ckofalltrades/legacy-python/tags?name=0.9.1) |
| 1.0.1   | [1.0.1/Dockerfile](1.0.1/Dockerfile) | [j4ckofalltrades/legacy-python:1.0.1](https://hub.docker.com/r/j4ckofalltrades/legacy-python/tags?name=1.0.1) |
| 1.1     | [1.1/Dockerfile](1.1/Dockerfile)     | [j4ckofalltrades/legacy-python:1.1](https://hub.docker.com/r/j4ckofalltrades/legacy-python/tags?name=1.1)     |
| 1.2     | [1.2/Dockerfile](1.2/Dockerfile)     | [j4ckofalltrades/legacy-python:1.2](https://hub.docker.com/r/j4ckofalltrades/legacy-python/tags?name=1.2)     |
| 1.3     | [1.3/Dockerfile](1.3/Dockerfile)     | [j4ckofalltrades/legacy-python:1.3](https://hub.docker.com/r/j4ckofalltrades/legacy-python/tags?name=1.3)     |
| 1.4     | [1.4/Dockerfile](1.4/Dockerfile)     | [j4ckofalltrades/legacy-python:1.4](https://hub.docker.com/r/j4ckofalltrades/legacy-python/tags?name=1.4)     |
| 1.5     | [1.5/Dockerfile](1.5/Dockerfile)     | [j4ckofalltrades/legacy-python:1.5](https://hub.docker.com/r/j4ckofalltrades/legacy-python/tags?name=1.5)     |
| 1.6     | [1.6/Dockerfile](1.6/Dockerfile)     | [j4ckofalltrades/legacy-python:1.6](https://hub.docker.com/r/j4ckofalltrades/legacy-python/tags?name=1.6)     |
| 2.0     | [2.0/Dockerfile](2.0/Dockerfile)     | [j4ckofalltrades/legacy-python:2.0](https://hub.docker.com/r/j4ckofalltrades/legacy-python/tags?name=2.0)     |
| 2.1.3   | [2.1.3/Dockerfile](2.1.3/Dockerfile) | [j4ckofalltrades/legacy-python:2.1.3](https://hub.docker.com/r/j4ckofalltrades/legacy-python/tags?name=2.1.3) |
| 2.2     | [2.2/Dockerfile](2.2/Dockerfile)     | [j4ckofalltrades/legacy-python:2.2](https://hub.docker.com/r/j4ckofalltrades/legacy-python/tags?name=2.2)     |
| 2.3     | [2.3/Dockerfile](2.3/Dockerfile)     | [j4ckofalltrades/legacy-python:2.3](https://hub.docker.com/r/j4ckofalltrades/legacy-python/tags?name=2.3)     |
| 2.4     | [2.4/Dockerfile](2.4/Dockerfile)     | [j4ckofalltrades/legacy-python:2.4](https://hub.docker.com/r/j4ckofalltrades/legacy-python/tags?name=2.4)     |
| 2.5     | [2.5/Dockerfile](2.5/Dockerfile)     | [j4ckofalltrades/legacy-python:2.5](https://hub.docker.com/r/j4ckofalltrades/legacy-python/tags?name=2.5)     |
| 2.6     | [2.6/Dockerfile](2.6/Dockerfile)     | [j4ckofalltrades/legacy-python:2.6](https://hub.docker.com/r/j4ckofalltrades/legacy-python/tags?name=2.6)     |
| 2.7     | [2.7/Dockerfile](2.7/Dockerfile)     | [j4ckofalltrades/legacy-python:2.7](https://hub.docker.com/r/j4ckofalltrades/legacy-python/tags?name=2.7)     |
| 3.0     | [3.0/Dockerfile](3.0/Dockerfile)     | [j4ckofalltrades/legacy-python:3.0](https://hub.docker.com/r/j4ckofalltrades/legacy-python/tags?name=3.0)     |
| 3.1     | [3.1/Dockerfile](3.1/Dockerfile)     | [j4ckofalltrades/legacy-python:3.1](https://hub.docker.com/r/j4ckofalltrades/legacy-python/tags?name=3.1)     |
| 3.2     | [3.2/Dockerfile](3.2/Dockerfile)     | [j4ckofalltrades/legacy-python:3.2](https://hub.docker.com/r/j4ckofalltrades/legacy-python/tags?name=3.2)     |

## Usage

### Build and run locally

```sh
docker build -t legacy-python:2.0 ./2.0
docker run -it legacy-python:2.0
```

### Pulling from Docker Hub or GitHub Container Registry

```sh
# from Docker Hub
docker pull j4ckofalltrades/legacy-python:2.0
docker run -it j4ckofalltrades/legacy-python:2.0
```

```sh
# from GitHub Container Registry
docker pull ghcr.io/j4ckofalltrades/legacy-python:3.0
docker run -it ghcr.io/j4ckofalltrades/legacy-python:3.0
```

## Attribution and sources

- [python-0.9.1](https://github.com/smontanaro/python-0.9.1): Python 0.9.1 source release
- [vintage-python](https://github.com/di/vintage-python):  Base images for vintage Python distributions (used as a reference for this repository) 
- [Legacy Python Source Releases](https://legacy.python.org/download/releases/src/): Source releases for Python 1.x, 2.0 
- [Python Source Releases](https://www.python.org/downloads/source/): Source releases for Python 2.0.1+
