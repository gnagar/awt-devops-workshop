### Run monitoring stack

```shell
cd /home/appworks/Documents/awt-devops-workshop
git pull
cd monitoring
docker-compose up -d
```

### Ports usage

8080: Jenkins on localhost
5000: Docker registery on Docker
3000: Grafana on Docker via monitoring stack
9093: Alert manager on Docker via monitoring stack
9090: Prometheus on Docker via monitoring stack
