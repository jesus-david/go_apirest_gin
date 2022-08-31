```
docker build --platform linux/amd64 -t go_apirest_gin -f docker/go/Dockerfile .  
docker run -it --rm -p 8080:8080 go_apirest_gin
```

