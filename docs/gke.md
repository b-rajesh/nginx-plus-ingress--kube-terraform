# Pre-requsite  - Install and configure GCloud & initialise

[Go back to main page](../README.md)


# Enable the gke module
Step 1
```
Append  `.disabled` to the file called local_module.tf. It should look like  'local_module.tf.disabled'
```
Step 2
```
Append  `.disabled` to the file called aks_module.tf. It should look like  'aks_module.tf.disabled'
```
Step 3
```
Remove `.disabled` from the file called gke_module.tf.disabled. It should look like 'gke_module.tf'
```

# Install appropriate GCP/GKE tools
First, install the [Google Cloud CLI](https://cloud.google.com/sdk/docs/quickstarts) 
```
Install gcloud sdk  - <Google Cloud SDK 284.0.0>

```
Initialize it...

```shell
$ gcloud init
```
gcloud Configure 
```shell
$ gcloud auth login
```
Configure glcoud to work with your Terraform.
```shell
$ gcloud auth application-default login
```
Configure local docker to work with google container repo GCR.
```shell
gcloud auth configure-docker
```

# Pre-requsite  - Important to read  terraform.tfvars and variable.tf

```
* Replace `terraform.tfvars` values with your `project_id` , `region` and other variables. Your  `project_id` &  `region`  must match the project you've initialized gcloud with. 

* You may not need project_id, region and few otehr variabled if you are running locally

* Do NOT use upper case for the value you are going to replace.
```
# Components created
```
* GKE default node is deleted , one application node pool is created.
* Uses GCR to upload the nginx plus image
* Public load balancer
```


# Known challenges
```
You would be likely have an error while running terraform apply like
---
Error: clusterrolebindings.rbac.authorization.k8s.io is forbidden: User "<user>@<email>.com" cannot create resource "clusterrolebindings" in API group "rbac.authorization.k8s.io" at the cluster scope: requires one of ["container.clusterRoleBindings.create"] permission(s).
---
** If you are NOT an admin, You may need to raise a ticket with your admin to elevant the access to create cluster role  binding.
** If you are an admin , then refere here https://cloud.google.com/kubernetes-engine/docs/how-to/role-based-access-control
```


[Go back to main page](../README.md)