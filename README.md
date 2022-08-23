
# AWS Real World Tasks
## AWS Tasks I've worked in my Projects
<details><summary>Send alerts if AWS KMS is not rotated</summary>

  ```css
  Fetch all AWS KMS keys and if KMS is not rotated in 90 days and emails using SES, this should
  be impletented by scheduling lambda function
  ```
</details>
<details><summary>Automatically tag EC2,ALB,Autoscaling, RDS instances using Lambda</summary>

  ```css
  Keep common tags in s3 bucket, trigger lambda function when EC2,ALB,Auto Scaling,RDS 
  resources are created and tag them automatically
  ```
</details>
<details><summary>Automatically shutdown Dev EC2 and RDS instance on weekends</summary>

  ```css
  Group EC2 and RDS by taging appropriately and stop them weekends and start them on weekdays
  ```
</details>
<details><summary>Automate RDS native backups of Microsoft SQL Server</summary>

  ```css
  Lambda function should be deployed in private subnet, database credentials should be stored in
  secrets manager, configure secrets manager interface endpoint in a VPC so lambda can accesss
  secrets manager over aws private network.
  ```
</details>
<details><summary>Grant S3 Bucket access only to specifc users</summary>

  ```css
  For our client we are storing PII data in S3 bucket and to protect that from ananymous users 
  we should create S3 bucket policy so that only selective users can read
  ```
</details>
<details><summary>Deny S3 Uploads if encryption at rest is not enabled</summary>

  ```css
  For our client we are storing PII data in S3 bucket and to protect that from ananymous users 
  we should create S3 bucket policy so that only selective users can read
  ```
</details>

<details><summary>Enable DynamoDB table backup</summary>

  ```css
      Enable backups on specified dynamoDB backups
  ```
</details>

## AWS Issues faced
<details><summary>CNAMEAlreadyExists Exception</summary>
  
  ```
     Read the following link about the issues
     https://aws.amazon.com/premiumsupport/knowledge-center/resolve-cnamealreadyexists-error/
  ```
  
</details>

## Kubernetes issues

<details><summary>Metrics server certificates issue</summary>
  
  ```
 "Failed to scrape node" err="Get \"https://IP:10250/metrics/resource\": x509: cannot validate certificate for IP because it doesn't contain any IP SANs" node="node01"
  ```
  If we see above error in metrics server deployment. we need to add **- --kubelet-insecure-tls** in container args which will disable tls verification. as shown below screenshoot. This won't fix the actual issue. Temporarily mitigate the problem.
  ![metrics-servers-certs-issue](https://github.com/javahometech/aws-real-work/blob/main/images/metrics-servers-certs-issue.png)
  
  To fix this permanently. we need to configure signed certificates. To enable signed kubelet serving certificates follow the below links.
  
  https://github.com/kubernetes-sigs/metrics-server/issues/196#issuecomment-1006601727
  
  https://kubernetes.io/docs/tasks/administer-cluster/kubeadm/kubeadm-certs/#kubelet-serving-certs
</details>

<details><summary>Join Worker Nodes to Cluster set EC2 Security Group Inbound Rules</summary>

When we run [kubeadm join command](https://github.com/javahometech/kubernetes/blob/master/setup-kubernetes-with-kubeadmn.md#6-take-note-of-kubeadm-command-and-run-on-all-workers) If your Security Group inbound rules are not set properly, you will notice that the process waits indefinitely after the below output is shown. Step 6 shows how to solve this

![kubeadm join port issue](https://github.com/javahometech/kubernetes/blob/master/images/kubeadm%20join%20port%20issue.png)

If both master and worker nodes use the same security group, you have the option to allow all inbound traffic originating from the same security group


```
#Kubernetes Control Plane Nodes
6443/tcp
2379-2380/tcp
10250-10252/tcp
#Kubernetes Worker Nodes
10250/tcp
30000-32767/tcp
# Flannel
8285/udp 
8472/udp
# CoreDNS 
9153/tcp (metrics port)
```
</details>
