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
- Import and examine various dashboards in grafana directory

### Add Jenkins monitoring

Demonstration of how to add a new server
- Install prometheus plugin in Jenkins (external Jenkins - reachable from container)
- Configure prometheus to connect with the Jenkins server
- View the server stats in dashboards
- Create alerts

### Ports usage

- 8080: Jenkins on localhost
- 5000: Docker registery on Docker
- 3000: Grafana on Docker via monitoring stack
- 9093: Alert manager on Docker via monitoring stack
- 9090: Prometheus on Docker via monitoring stack
- 9000: Sonarqube server URL on Docker
- 9092: Sonar scanner port on Docker

### Sonarqube

- Start SonarQube
```shell
  docker run \
  -d \
  --name sonarqube \
  -p 9000:9000 \
  -p 9092:9092 \
  localhost:5000/sonarqube:6.2-alpine
```
- Install SonarQube scanner plugin in Jenkins
