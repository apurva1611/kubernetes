# kubernetes
#### Team Information
| Name  | NEU ID | Email Address
| ------------- | ------------- | ------------- |
| Achira Shah  | 001409351  | shah.ac@northeastern.edu |
| Apurva Mathur  | 001088100  | mathur.ap@northeastern.edu |
| Boran Yildirim | 001054080 | yildirim.b@northeastern.edu |
		
  

Run Ansible Playbook <br>
Open terminal and run the ansible-playbook command in the below format with parameters

To create the cluster run following command

```
$ ansible-playbook setup-k8s-cluster.yml -vvv --extra-vars "env=<env> aws_profile=<env> dns_zone=<zoneid> cluster_name=<cluster-name> state_store=s3://<bucket> ssh_public_key=<yourpublickey>"
```

To install ingress-controller and cert-manager
```
$ ansible-playbook install-nginx-controller.yaml -vvv
```


To delete the cluster run following command

```
$ ansible-playbook teardown-k8s-cluster.yml -vvv --extra-vars "aws_profile=<env> cluster_name=<cluster-name> state_store=s3://<bucket>"
```

To create the rds and vpc peering run following

$ ansible-playbook setup-rds-vpcPeering.yaml --extra-vars "aws_profile=<env> cluster_name=<cluster-name>"

To delete the rds and vpc peering run following

$ ansible-playbook teardown-rds-vpcPeering.yml -vvv --extra-vars "aws_profile=<env> cluster_name=<env>"


Steps
1) app-prereq
run app-prereq jenkins 
or
``` 
$ helm upgrade --install app-prereq app-prereq -n monitoring
$ helm upgrade --install elasticsearch-exporter prometheus-community/prometheus-elasticsearch-exporter -n monitoring
```

2) create namespace
```
$ kubectl create namespace cert-manager
```
3) run
```
$ kubectl apply -f letsencrypt-prod.yaml 
$ kubectl apply -f letsencrypt-staging.yaml 
```
4) run
```
$ ansible-playbook install-nginx-controller.yaml -vvv --extra-vars
$ ansible-playbook setup-cluster-autoscaler.yml -vvv --extra-vars
$ ansible-playbook setup-metric-server.yaml -vvv --extra-vars
```
5) run
```
$ kubectl apply -f letsencrypt-prod.yaml 
$ kubectl apply -f letsencrypt-staging.yaml 
```
6) microservices
run jenkins to deploy microservices - webapp, poller, notifier

7) register externalip to route53
