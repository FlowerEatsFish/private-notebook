# To learn how to run Electron on Ubuntu

- [To learn how to run Electron on Ubuntu](#to-learn-how-to-run-electron-on-ubuntu)
  - [Add access of Docker to xhost](#add-access-of-docker-to-xhost)
  - [Create a container](#create-a-container)
  - [Run electron-quick-start in Docker container](#run-electron-quick-start-in-docker-container)

## Add access of Docker to xhost

[Reference: couldn't open display unix:0](https://github.com/jessfraz/dockerfiles/issues/329#issuecomment-368262183)

```shell
xhost +"local:docker@"
```

## Create a container

```shell
NODE=10
docker run -itd /
  --net host /
  --name electron /
  -v /tmp/.X11-unix:/tmp/.X11-unix /
  -e DISPLAY=unix$DISPLAY
  node:$NODE
```

## Run electron-quick-start in Docker container

```shell
apt update && /
apt install -y /
  libgtkextra-dev /
  libgconf2-dev /
  libnss3 /
  libasound2 /
  libxtst-dev /
  libxss1 /
  libgtk-3-0 /
  libgtk-3-dev && /
git clone https://github.com/electron/electron.git && /
cd electron-quick-start && /
npm install && /
npm start
```
