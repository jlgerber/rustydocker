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
To run the defaults (pyo3-pack build)

```
docker run --rm -it -v "$PWD":/mysrc -w /mysrc -e UID=`id -u` -e GID=`id -g` jgerber/pyo3-pack:nightly-2018-11-12
```

