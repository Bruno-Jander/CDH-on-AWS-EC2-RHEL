## Creating a new EC2 instance (Master)

1) On AWS portal, launch a new EC2 instance with the following configuration:
```
| Names and Tags 
Name: Master

| Application and OS Images
Name: Red Hat Enterprise Linux 8
Amazon Machine Image (AMI): RHEL-8.9.0_HVM-20240327-x86_64-4-Hourly2-GP3

| Instance type 
Instance type: t2.xLarge

| Key Pair (login)
Key pair name: create new key pair
Key pair type: RSA
Private key file format: .pem

| Network settings 
Firewall (security groups): Create security group
Allow SSH traffic from: `Anywhere [0.0.0.0/0]` (do not do this in production environment ---PLEASE---)

| Configure storage 
1x `200` GB GP3 root volume

| Advanced details
None

| Summary 
Number of instances: 1

Launch instance
```
*Tip: do not forget to save your private key securely.*

## Creating a new EC2 instance (Worker)

2) On AWS portal, launch a new instance with the following configuration:
```
| Names and Tags 
Name: Worker

| Application and OS Images
Name: Red Hat Enterprise Linux 8
Amazon Machine Image (AMI): RHEL-8.9.0_HVM-20240327-x86_64-4-Hourly2-GP3

| Instance type 
Instance type: t2.micro

| Key Pair (login)
Key pair name: RHEL_keys_new (the same pair that you have created for the MASTER instance)

| Network settings 
Firewall (security groups): (the same settings that you have configured for the MASTER instance)

| Configure storage 
1x `20` GB GP3 root volume

| Advanced details
None

| Summary 
Number of instances: 3-4

Launch instance
```
*Tip: do not forget to use the same keys/network that you declared before.*

## Configuring your firewall access permissions

3) Go to the `Security` tab of the recently created `Master` instance and access the `Security Groups` option. Select the `Edit inbound rules` option and add the following configuration:

| Security group rule | Type    | Protocol | Port range | Source 1 | Source 2  |
| ------------------- | ------- | -------- | ---------- | -------- | --------- |
| —                   | SSH     | TCP      | 22         | Custom   | 0.0.0.0/0 |
| —                   | ALL TCP | TCP      | 0-65535    | Custom   | 0.0.0.0/0 |

*Tip: remember not to do this in a production environment, just for testing purposes*

Cloudera standard ports:

| Protocol | Port | Process                                           |
| -------- | ---- | ------------------------------------------------- |
| TCP      | 22   | SSH                                               |
| TCP      | 7180 | Cloudera Manager web console                      |
| TCP      | 7182 | Agent heartbeat                                   |
| TCP      | 7183 | (optional, Cloudera Manager web console with TLS) |
| TCP      | 7432 | Embedded PostgreSQL                               |
| icmp     | -1   | ping echo                                         |

## Connecting to your Master instance with SSH

4) Open an SSH client in the terminal (e.g.: PowerShell on Windows).

5) Navigate to your private key file location:
```PowerShell
cd "C:\Users\{replace_for_your_user}\Downloads\RHEL_keys_new.pem"
```

- Run this command, if necessary, to ensure your key is not publicly viewable:
```Bash
chmod 400 "RHEL_keys_new.pem"
```

6) Connect to your RHEL instance using its Public DNS:
```PowerShell
ssh -i "RHEL_keys_new.pem" ec2-user@ec2-13-489-19-3.sa-east-1.compute.amazonaws.com
```
*Tip: you can find the publica DNS of your instance on EC2 settings, it is something like `ec2-13-489-19-3.sa-east-1.compute.amazonaws.com`*

- After connecting, you can see your RHEL version:
```Bash
cat /etc/redhat-release
```

## Disabling the SELinux parameter

7) It is important to disable the `SELinux` config before proceeding with the installation:

- Seeing the current `SELinux` setting:
```Bash
cat /etc/selinux/config
```
*Tip: read more about it here [Disable SELinux](https://docs.cloudera.com/cdp-private-cloud-base/7.1.9/installation/topics/cdpdc-before-you-begin-trial-install.html#pnavId2).*

- Acquiring the necessary permission:
```Bash
sudo su
```

- Disabling the SELinux config:
```Bash
sed -i 's/SELINUX=enforcing/SELINUX=disabled/' /etc/selinux/config
```
*Tip: return it to the default value once the process is complete.*

8) Restart the machine, log back in with SSH and see if the change worked:
```Bash
reboot

getenforce
```

NEXT: [[Installing Cloudera on AWS RHEL]](https://github.com/Bruno-Jander/CDH-on-AWS-EC2-RHEL/blob/64ef5c6cf58a8982cd8c8c010ac172a1f7469260/Cloudera_CDH_on_AWS%20(Part%202).md)
