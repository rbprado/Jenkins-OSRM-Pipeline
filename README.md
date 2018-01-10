# Jenkins-OSRM-Pipeline

This repository stores the following data:

```
.
├── dockerfile/
│   └── Dockerfile to build the containers application.
├── provision/
│   └── The full provisioning of a Jenkins, a Slave and the pileline.
└── pipeline/
    └── The pipeline code.
```


### Requirements:

- Vagrant 1.9.1
  - Vagrant digital_ocean plugin
- Ansible 2.0.0.2
- Digital Ocean credentials as environmental variables:
  - export DO_TOKEN="xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
  - export DO_KEY_NAME="Key Name"


### Bringing up the environment:

You will need an account on Digital Ocean (https://cloud.digitalocean.com/) with an access token and a registered ssh key.
On the `provision/` folder, run the following command to bring up the Jenkins server with a slave:
```
$ vagrant up --provider digital_ocean
```

If you want to provision the VMs separately run:
```
$ vagrant up sentiance-jenkins --provider digital_ocean
$ vagrant up sentiance-slave --provider digital_ocean
```

- On your browser access the Jenkins IP shown on the end of the `sentiance-jenkins` provision.
- On the Jenkins web interface create a slave node, with:
  - name `slave`
  - workspace `/home/jenkins`
  - launch method `via SSH`
  - with the IP shown on the end of the provision of `sentiance-slave`
  - Set this slave to use jenkins/jenkins credentials and the `Host Key Verification Strategy` with `non verifying`


### To Do:

- Docker build is failing with the following error:
  `CMake Error: The source directory "/src" does not appear to contain CMakeLists.txt.`
  So I am using docker pull to test the application.
- Reduce the downtime of the application by just killing the older container when the newone is already done.
- Publish a final link for the application running (same link of the curl executed)
- Provision with the node already attached on Jenkins.
- Provision with valid credentials already configured.
- Configure iptables on the VMs.
- Configure reverse proxy for https.

### References:
- Doc about how to bring up the container with berlin OSRM data:
https://github.com/Project-OSRM/osrm-backend#using-docker/
https://hub.docker.com/r/osrm/osrm-backend/
- Jenkins provision reference:
https://github.com/balamaci/jenkins-ansible/
- DockerCE provision reference:
https://github.com/opichon/ansible-install-docker-ce/