# Python Web App mit Docker Compose

## Überblick
Dies ist eine einfache Webanwendung, die mit Flask und Redis entwickelt wurde und mit Docker Compose verwaltet wird.

## Technologien
- **Docker**
- **Docker Compose**
- **Flask**
- **Redis**
- **HTML**

## Installation & Nutzung

### 1. Github Login setzen
Falls du ein privates Repository verwendest, musst du dich mit deinem Github Token anmelden.

Setze eine Umgebungsvariable mit deinem Github Token:
```sh
export CR_PAT=<Github_Token>
```
Melde dich mit deinem persönlichen Token bei Github an:
```sh
echo $CR_PAT | docker login ghcr.io -u <githubusername> --password-stdin
```

### 2. Docker Plattform setzen (bei ARM-Architektur)
Falls du eine ARM-Architektur verwendest (z. B. Apple M1/M2), setze die Docker Plattform auf AMD64:
```sh
export DOCKER_DEFAULT_PLATFORM=linux/amd64
```

### 3. Docker Compose Befehle

#### Starten der Anwendung
```sh
docker-compose -p python-web up --build -d
```

#### Stoppen der Anwendung
```sh
docker-compose -p python-web down
```

#### Aufräumen
Lösche ungenutzte Docker-Images, Volumes, Netzwerke und Systeme:
```sh
docker image prune -a
```
```sh
docker volume prune
```
```sh
docker network prune
```
```sh
docker system prune -a --volumes
```

### 4. OpenShift Anwendung verwalten
Falls du OpenShift nutzt, kannst du die Anwendung mit folgenden Befehlen verwalten:

Löschen der Anwendung:
```sh
oc delete all --selector=app=html-openshift-app
```

Anwenden der Konfiguration:
```sh
oc apply -f oc/01-with-deployment --recursiive
```

Setzen von Triggers für das Deployment:
```sh
oc set triggers deploy/html-openshift-app --from-image=html-openshift-app:latest -c html-openshift-app
```

## Lizenz
Dieses Projekt steht unter der MIT-Lizenz.

