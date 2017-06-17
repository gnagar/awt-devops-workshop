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
- Go to Manage jenkins > Configure system
- Add a new SonarQube server
  - Name: SonarQube
  - URL: http://localhost:9000
- Install SonarQube Quality Gate plugin in Jenkins
  - Name: SonarQube Quality gate
  - URL: http://localhost:9000

### Job configuration
- Git repo: https://github.com/gnagar/node-sample.git
- Execute shell commands
  - docker-compose -f docker-compose-test.yml up
  - `sed -i.bak 's@^SF:/app/@SF:@' coverage/lcov.info`
  - Sonar scanner configuration
  - docker-compose build
  - docker-compose push

### ELK

Check the max map count using `sysctl vm.max_map_count`. If it is less than `262144`, run this command `sudo sysctl -w vm.max_map_count=262144`

Send arbitrary logs to logstash
```shell
echo Hello World! | nc 192.168.99.101 8062
```

Use this resource to auto-detect logstash patterns [grokdebug.herokuapp.com](https://grokdebug.herokuapp.com/discover)

e.g. `14:14:21.363 INFO  an exception hapened at 2017-06-10T14:20:52.938Z`

### Sample node project with tests

[node-sample on Github](https://github.com/gnagar/node-sample)

### Ports usage

- 8080: Jenkins on localhost
- 5000: Docker registery on Docker
- 3000: Grafana on Docker from monitoring stack
- 9093: Alert manager on Docker from monitoring stack
- 9090: Prometheus on Docker from monitoring stack
- 9000: SonarQube server URL on Docker
- 9092: SonarQube scanner port on Docker
- 8065: Kibana on Docker from ELK stack
- 8062: Logstash on Docker from ELK stack
- 9200: Elasticsearch on Docker from ELK stack
- 9300: Elasticsearch on Docker from ELK stack
- 8061: Nginx on Docker from ELK stack

