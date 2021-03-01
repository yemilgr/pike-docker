# Pike docker image

## How to use

Mount your pike project and run a script

```bash
docker run -it --rm  -v "$PWD":/usr/src/app -w /usr/src/app yemilgr/pike pike app.pike
```

Run an interactive console

```bash
docker run -it --rm yemilgr/pike /bin/ash
```
