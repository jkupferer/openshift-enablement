## Basic Requirements

### Ability to authenticate at the master console

Configured in `group_vars/OSEv3/auth.yml`. Authentication with htpasswd
and three preconfigured users:

* adminuser - user with cluster-admin rights, password "r3dh4t1!"

* alice - normal user password "password"

* bob - normal user password "password"

The cluster-admin role is assigned in `tasks/cluster-admin.yml`.

### Registry has storage attached and working

Configured in `group_vars/OSEv3/registry.yml`

Need to use openshift-ansible version 3.3 or later. Registry s3 bucket needed
to be pre-created within the aws console.

### Router is configured on each infranode

Configured in `group_vars/OSEv3/router.yml`. I decided to split out router
infranodes from other infrastructure tasks as the routers have different network
access patterns and so fit a different network security configuration. The
"region=router" tag was used.

### Different PVs are available for users to consume

### Ability to deploy a simple app

## HA Deployment

### There are three masters working

### There are three etcd instances working

### There is a load balancer to access the masters

### There is a load balancer/DNS for both infranodes

### There are at least two infranodes

## Environment Configuration

### Multitenancy is configured and working

### Node selector is defined in the default namespace

### Node selector is defined in the openshift-infra and logging projects

### Aggregated logging is configured and working

### Metrics collection is configured and working

## CICD Workflow

### Jenkins pod is running with a persistent volume

### Jenkins deploys openshift-tasks app

### Jenkins OpenShift plugin is used to create a CICD workflow

### HPA is configured and working on production deployment of openshift-tasks

## Multitenancy Spin

### Multiple clients created

### Multiple registries, dedicated registry per client

### Dedicated node for client

### admissionControl plugin sets specific limits per label (client)

### A new project template is modified so that it includes a LimitRange

### A new user template is used to create a user object with the specific label value

### On-boarding new client documentation

