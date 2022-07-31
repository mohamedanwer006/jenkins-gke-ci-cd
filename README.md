# Provision GKE cluster on GCP 
- Deploy jenkins as pod on GKE cluster
- Create a jenkins ci/cd pipeline to deploy a nodejs app on GKE cluster

![infrastructure](./assets/images/draw.png)

### Provision infrastructure on GCP 🚀
1. Create a GCP project
2. ToDo : Create GS bucket and enable versioning to store the terraform state file
3. Clone repo 
4. edit project_id in terraform.tfvars with your project id and edit provider configuration 

#### Finally  Run the following command to provision the infrastructure 🚀
```bash
# initialize terraform
terraform init
# check plan
terraform plan 
# apply the plan it will take some time to complete 😴
terraform apply --auto-approve
```

### Use output command to auth with the cluster 🔐 and open connection through proxy 💻

```bash
gcloud container clusters get-credentials gke-cluster --zone us-central1-a --project anwer-gcp ; gcloud compute ssh bastion-vm --project anwer-gcp  --zone us-central1-a -- -4 -L8888:localhost:8888 -N -q -f && export HTTPS_PROXY=localhost:8888
```

### Deploy the jenkins using kubectl 🚀

### Start deploy by using the following command 🚀
```bash
kubectl apply -f ./jenkins/namespace.yaml
kubectl apply -Rf ./jenkins
```



### ToDo: Deploy jenkins using ansible

---

### ToDo: Create ci/cd pipeline on jenkins to deploy the application 🚀


-----

### Clean up 💣

```bash
terraform destroy --auto-approve

```
