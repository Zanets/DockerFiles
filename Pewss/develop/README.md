```shell
git clone https://gist.github.com/darg20127/03709547d03161d68a6a9ba19872af86

docker build -t pewss_dev .

# -p publish private port (expose in dockerfile)
docker run -it -p 8081:8081 --name pewss_dev pewss_dev 
```
