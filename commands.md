### Run registry (should already be running in the VM)

```shell
docker run \
  -d \
  -p 5000:5000 \
  --restart always \
  -v /home/appworks/Documents/docker-registry/data:/var/lib/registry:rw
  --name registry \
  registry:2.6
```

### Run monitoring stack

```shell
cd /home/appworks/Documents/awt-devops-workshop
git pull
cd monitoring
docker-compose up -d
```

### Ports usage

- 8080: Jenkins on localhost
- 5000: Docker registery on Docker
- 3000: Grafana on Docker via monitoring stack
- 9093: Alert manager on Docker via monitoring stack
- 9090: Prometheus on Docker via monitoring stack
