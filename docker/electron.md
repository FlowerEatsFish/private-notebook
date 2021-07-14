# To run Electron in Docker

- [To run Electron in Docker](#to-run-electron-in-docker)
  - [1. Ubuntu v18.04](#1-ubuntu-v1804)
    - [1-1. Add access of Docker to X11](#1-1-add-access-of-docker-to-x11)
    - [1-2. Create a container](#1-2-create-a-container)
    - [1-3. Run electron-quick-start in Docker container](#1-3-run-electron-quick-start-in-docker-container)
  - [2. macOS v10.14](#2-macos-v1014)
    - [2-1. Install XQuartz (X11)](#2-1-install-xquartz-x11)
    - [2-2. Add access of Docker to XQuartz](#2-2-add-access-of-docker-to-xquartz)
    - [2-3. Create a container](#2-3-create-a-container)
    - [2-4. Run electron-quick-start in Docker container](#2-4-run-electron-quick-start-in-docker-container)

## 1. Ubuntu v18.04

### 1-1. Add access of Docker to X11

Reference: [couldn't open display unix:0](https://github.com/jessfraz/dockerfiles/issues/329#issuecomment-368262183)

```shell
xhost + "local:docker@"
```

### 1-2. Create a container

```shell
docker run -itd \
  --net host \
  --name electron \
  -v /tmp/.X11-unix:/tmp/.X11-unix \
  -e DISPLAY=unix:0
  node:10
```

### 1-3. Run electron-quick-start in Docker container

```shell
cd electron-quick-start && \
apt update && \
apt install -y \
  libasound2 \
  libgtk-3-0 \
  libnss3 \
  libxss1 \
  libcanberra-gtk-module \
  libcanberra-gtk3-module && \
git clone https://github.com/electron/electron-quick-start && \
npm install && \
npm start
```

## 2. macOS v10.14

### 2-1. Install XQuartz (X11)

- Install XQuartz:

  ```shell
  brew cask install xquartz
  ```

- Run XQuartz -> `X11 Preferences` -> `Security` -> `Allow connections from network clients` is checked `on`

- Restart XQuartz to activate the setting as above.

### 2-2. Add access of Docker to XQuartz

Reference: [couldn't open display unix:0](https://github.com/jessfraz/dockerfiles/issues/329#issuecomment-368262183)

```shell
xhost + 127.0.0.1
```

### 2-3. Create a container

```shell
docker run \
  -it \
  -e DISPLAY=host.docker.internal:0 \
  --name electron \
  -d \
  node:10
```

### 2-4. Run electron-quick-start in Docker container

```shell
cd electron-quick-start && \
apt update && \
apt install -y \
  libasound2 \
  libgtk-3-0 \
  libnss3 \
  libxss1 \
  libcanberra-gtk-module \
  libcanberra-gtk3-module && \
git clone https://github.com/electron/electron-quick-start && \
npm install && \
npm start
```
