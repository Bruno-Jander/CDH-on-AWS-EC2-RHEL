# CDH on AWS EC2 RHEL

### Overview 🙇‍♂️
A simple tutorial of how to deploy a Cloudera Distribution for Hadoop (CDH) cluster on AWS Elastic Compute Cloud (EC2) instances running Red Hat Enterprise Linux (RHEL). It was written while I was watching this excellent [video tutorial](https://youtu.be/HH64EcI26qE?si=tQKYzKyaFYvJDebw).

#### Reading order 📖
1) [Configuring_EC2_instances_on_AWS (PART 1)](https://github.com/Bruno-Jander/CDH-on-AWS-EC2-RHEL/blob/main/docs/Configuring_EC2_instances_on_AWS%20(PART%201).md)
2) [Installing_Cloudera_CDH_on_AWS_RHEL (PART 2)](https://github.com/Bruno-Jander/CDH-on-AWS-EC2-RHEL/blob/main/docs/Installing_Cloudera_CDH_on_AWS_RHEL%20(PART%202).md)
3) [Creating_a_bare_metal_cluster (PART 3)](https://github.com/Bruno-Jander/CDH-on-AWS-EC2-RHEL/blob/main/docs/Creating_a_bare_metal_cluster%20(PART%203).md)
4) [Adding_services_to_your_bare_metal_cluster (PART 4)](https://github.com/Bruno-Jander/CDH-on-AWS-EC2-RHEL/blob/main/docs/Adding_services_to_your_bare_metal_cluster%20(PART%204).md)

#### The basic deployment architecture consists of the following components 🧰
- **EC2 Instances**: Virtual machines on AWS running RHEL, configured to host CDH services.
- **Cloudera Manager**: A centralized management tool for CDH deployments, installed on one of the EC2 instances (MASTER).
- **CDH Services**: Hadoop components such as HDFS, YARN, Hive, and Impala, distributed across the EC2 instances (MASTER/WORKERs).
- **SSH client**: A program that allows establishing secure and authenticated SSH connections to SSH servers (PowerShell/Bash).

GitHub Repository: @CDH-on-AWS-EC2-RHEL 🦫
