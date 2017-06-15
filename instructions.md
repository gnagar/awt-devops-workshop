## Commands for the workshop

We will use the Lubuntu VM we had used earlier in the session

### Install jre 8 on the VM

http://download.oracle.com/otn-pub/java/jdk/8u131-b11/d54c1d3a095b4ff2b6607d096fa80163/jre-8u131-linux-x64.tar.gz

### Install Jenkins on the VM

Download Jenkins war file in the VM. The LTS version can be found here: http://mirrors.jenkins.io/war-stable/latest/jenkins.war

### Run the following command on terminal - this is required for ELK stack to run properly

```shell
sudo sysctl -w vm.max_map_count=262144
```

