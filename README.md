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

To delete the cluster run following command

```
$ ansible-playbook teardown-k8s-cluster.yml -vvv --extra-vars "aws_profile=<env> cluster_name=<cluster-name> state_store=s3://<bucket>"
```

To create the rds and vpc peering run following

$ ansible-playbook setup-rds-vpcPeering.yaml --extra-vars "aws_profile=<env> cluster_name=<cluster-name>"

To delete the rds and vpc peering run following

$ ansible-playbook teardown-rds-vpcPeering.yml -vvv --extra-vars "aws_profile=<env> cluster_name=<env>"
