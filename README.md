# kubernetes
Team Information
Name	NEU ID	Email Address
Achira Shah	001409351	shah.ac@northeastern.edu
Apurva Mathur 001088100 mathur.ap@northeastern.edu

Run Ansible Playbook
Open terminal and run the ansible-playbook command in the below format with parameters

To create the cluster run following command

$ ansible-playbook setup-k8s-cluster.yml -vvv --extra-vars "aws_profile=<env> dns_zone=<zoneid> cluster_name=<cluster-name> state_store=s3://<bucket> ssh_public_key=<yourpublickey>"

To delete the cluster run following command

$ ansible-playbook delete-k8s-cluster.yml -vvv --extra-vars "aws_profile=<env> cluster_name=<cluster-name> state_store=s3://<bucket>"