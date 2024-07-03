PREVIOUS: [Installing Cloudera CDH on AWS RHEL](https://github.com/Bruno-Jander/CDH-on-AWS-EC2-RHEL/blob/64ef5c6cf58a8982cd8c8c010ac172a1f7469260/Cloudera_CDH_on_AWS%20(Part%202).md)

# Creating a Bare Metal cluster

*Tip: Do not configure AutoTL or Kerberos yet.*
*Tip: Cloudera strongly recommends that you install and configure the Cloudera Manager Server and Cloudera Manager Agents and CDP to set up a fully-functional CDP cluster _before_ trying to configure Kerberos authentication for the cluster.*

## Add Traditional Bare Metal Cluster

1) On the `Cluster Basics` page you just have to specify the name of your new cluster.

2) Go to the `Networking` page of your instances, copy the `Public IPv4 DNS` and paste it in the `Specify Hosts` page.

*Tip: do not forget to add all the hosts, including the `Master` instance.*

3) On the `Select Repository` page choose `Cloudera Repository` as the default repository. Also choose `Use Parcels` as Install method option.

4) On the `Select JDK` page choose `Install a Cloudera-provided version of OpenJDK` option.

5) On the `Enter Login Credentials` page fill in the *SSH Username* option with your user (AWS EC2 default is `ec2-user`); in the *Authentication Method* option choose `All hosts accept same private key` and provide the key you created earlier.

6) The installation will continue in the next page, `Install Agents`, where you'll see the process of installation of the `Cloudera Agent` in your hosts.

7) On the page `Install Parcels` Cloudera will download, distribute, unpack and activate the parcels through `Cloudera Runtime`.

8) On the last page,`Inspect Cluster`, you'll have to run two inspections:`Inspect Network Perfomance` and `Inspect Hosts`. After passing both checks, your cluster will be available. 

NEXT: [Adding services to your Bare Metal Cluster]()
