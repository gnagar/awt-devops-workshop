### Run cAdvisor

```shell
docker run \
  --v /:/rootfs:ro \
  --v /var/run:/var/run:rw \
  --v /sys:/sys:ro \
  --v /var/lib/docker/:/var/lib/docker:ro \
  --p 8010:8080 \
  --d \
  --name=cadvisor \
  localhost:5000/google/cadvisor:latest
```
