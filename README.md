# building

## build rustup
```
docker build -t jgerber/rustup:latest rustup/
```

## build nightly using rustup
```
docker build --build-arg RUST_VERSION=nightly-2018-11-11 -t jgerber/nightly:2018-11-11
```

## using container
```
docker run  --rm -v "$PWD":/usr/src/myapp -w /usr/src/myapp jgerber/rust:nightly-2018-11-12 cargo build
```
