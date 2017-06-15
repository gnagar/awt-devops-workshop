## Commands for the workshop

We will use the Lubuntu VM we had used earlier in the session

### Install Jenkins on the VM

Download Jenkins war file in the VM. The LTS version can be found here: http://mirrors.jenkins.io/war-stable/latest/jenkins.war

### Run the following command on terminal - this is required for ELK stack to run properly

```shell
sudo sysctl -w vm.max_map_count=262144
```

