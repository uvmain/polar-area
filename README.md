# Local
```
npm run dev
```

# Docker
```
docker build -t polararea:latest -f Dockerfile .
docker run -p 8084:8084 -d polararea:latest
```

# Azure Container Instance
```
az container create --resource-group rg-microservices --name polararea --image polararea:latest --cpu 1 --memory 1 --os-type Linux --ip-address Public --ports 8084 --dns-name-label portalarea
```
