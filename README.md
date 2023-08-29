# Hello Service

## Build Native Binary

```
quarkus build --native --no-tests -Dquarkus.native.container-build=true
```

```
%> file target/hello-service-1.0.0-SNAPSHOT-runner
target/hello-service-1.0.0-SNAPSHOT-runner: ELF 64-bit LSB executable, ARM aarch64, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux-aarch64.so.1, for GNU/Linux 3.7.0, BuildID[sha1]=881de1a5ab48d0f7c4202c64c0628247d53def8a, not stripped
```

## Create Docker Image

```
docker buildx build --platform linux/arm64,linux/amd64 -t chengkuan/quarkus-hello:1.0.0-native -f src/main/docker/Dockerfile.native --push .
```

## Deploy to OCP

```
oc apply -f yaml/hello.yaml
```

Error ecountered and POD failed to start:

```
exec ./application: exec format error
```

