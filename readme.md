# container compose

## containerfile

`docker build -t xxx .`

## run

`docker run -it xxx`

## compose

1. `cd` to service dir
2. `docker compose up -d` to start service
3. `docker compose down` to stop service

## notice

- `./data` is service data stored locally, which is added to `.gitirnore`
- `.env`

## podman

```sh
podman machine init
podman machine start
podman info
```
