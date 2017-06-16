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
- Access http://localhost:3000 to open Grafana's UI
- Use credentials `appworks/appworks` to login
- Click 'Add data source'
- Add prometheus as data source
  - Name: Prometheus
  - Type: Prometheus
  - URL: <What should it be? `http://localhost:9090`?>
  - Access: Proxy
- Save and test, grafana should be able to connect to prometheus

Import the dashboard temples from grafana directory
- From the Grafana menu, choose Dashboards and click on Import

### Ports usage

- 8080: Jenkins on localhost
- 5000: Docker registery on Docker
- 3000: Grafana on Docker via monitoring stack
- 9093: Alert manager on Docker via monitoring stack
- 9090: Prometheus on Docker via monitoring stack
