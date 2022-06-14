# renovate-docker-404

In oder to reproduce the error run the following two commands.

```sh
# start local docker registry
docker run \
  -d -p 5000:5000 \
  -e REGISTRY_PROXY_REMOTEURL="https://registry-1.docker.io" \
  registry:latest
```

```sh
# run renovate
docker run \
  --rm \
  -v $PWD/renovate.json:/usr/src/app/renovate.json \
  -e RENOVATE_TOKEN=YOUR_TOKEN_HERE \
  -e RENOVATE_REPOSITORIES="jmueller42/renovate-docker-404" \
  --network host \
  -it \
  renovate/renovate
```
