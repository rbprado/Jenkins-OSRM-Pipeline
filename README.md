# Jenkins-OSRM-Pipelin
This repository stores a Dockerfile on the dockefile branch with an application container.
The provision branche stores the recipe to provision a jenkins with the pipeline of this application configured and also a slave to run it.

###Requirements:

- Vagrant 1.9.1
  - Vagrant digital_ocean plugin
- Ansible 2.0.0.2
- Digital Ocean credentials as environmental variables:
  - export DO_TOKEN="xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
  - export DO_KEY_NAME="Key Name"

###How to run:

$ vagrant up --provider digital_ocean

- On your browser access the Jenkins IP shown on the end of the provision.

- On the end of the provision of the slave took it's IP and inset as a new slave on Jenkins using credentials with jenkins/jenkins credentials.



