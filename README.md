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
docker run  --rm -v "$PWD":/usr/src/myapp -w /usr/src/myapp jgerber/pyo3-pack:nightly-2018-11-12 
```

You can override the subcommand (for instance, to get the version number)

```
docker run  --rm -v "$PWD":/usr/src/myapp -w /usr/src/myapp jgerber/pyo3-pack:nightly-2018-11-12 -V
```