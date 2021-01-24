# DevOps Interview Test

This repository contains two short simple troubleshooting exercises.

The goal of the test is to run the Ansible playbook and install the Helm chart, identify and fix the errors that have been intentionally introdcued.

The result should be provided in the form of a Pull Request with all the errors fixed.

We will discuss the results of the test in the face-to-face interview.

## Prerequisites

* A Linux machine with Ansible installed
* Access to a Kubernetes cluster or Docker for Desktop installed
* kubectl and helm installed on your local machine

## Ansible

The Ansible playbook installs ActiveMQ on the local system and configures it as a service.

To run the playbook execute the following commands:

```bash
cd ansible
ansible-playbook playbooks/acs.yml
```

The playbook will fail with a couple of different errors, your challenge is to identify and fix the errors.

## Kubernetes

The [Helm chart](helm/alfresco-content-services/README.md) installs Postrges, ActiveMQ and the Alfresco repository.

To deploy the Helm chart execute the following commands:

```bash
kubectl create namespace devops-test
cd helm
helm dependency update alfresco-content-services
helm install acs alfresco-content-services -n devops-test
```

Although the Helm install command appears to work the deployment will actually fail with a couple of different errors, your challenge is to identify and fix the errors.

Once the system is running successfully the Alfresco repository will be available at `http://NodeIp:NodePort/alfresco`. If you are using a cluster that does not expose the worker nodes to the outside world the service won't be accessible. Please also explain in the Pull Request description what other techniques you could use to access the Alfresco repository.
