```shell
### create builder image
docker build --tag builder:pewss --file Builder "$(pwd)"

### create pewss image
docker build --tag instance:pewss --file Pewss "$(pwd)"

# -p publish private port (expose in dockerfile)
docker run -d -p 8081:8081 instance:pewss --name pewss
```
