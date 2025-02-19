# ZLI-Modul-109 HTML Docker App (Lösung 3.2)

## Technologies
- Docker
- NGINX
- HTML

## How To Use

### 1. Set Github Login
#### Set a variable with your Github token
```sh
export CR_PAT=<Github_Token>
```

#### Login to Github with your personal token
```sh
echo $CR_PAT | docker login ghcr.io -u <githubusername> --password-stdin
```

### 2. Set Docker Platform (for ARM)
```sh
export DOCKER_DEFAULT_PLATFORM=linux/amd64
```

### 3. Build and Run with Docker

#### Build Image
```sh
docker build -f Dockerfile.web -t ghcr.io/<githubusername>/html-docker-app:latest .
```

#### Push Image
```sh
docker push ghcr.io/<githubusername>/html-docker-app:latest
```

#### Start Container with Port 8080 and Name
```sh
docker run -d -p 8080:80 --name html-docker-app ghcr.io/<githubusername>/html-docker-app:latest
```

#### Stop Container
```sh
docker stop html-docker-app
```

#### Delete Container
```sh
docker rm html-docker-app
```

#### Delete Image
```sh
docker rmi ghcr.io/<githubusername>/html-docker-app:latest
```

