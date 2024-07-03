# Installing Cloudera CDH on AWS RHEL

*Tip: you just need to install Cloudera manager on `Master`.*
## Installing Cloudera - Part 1 (SSH Shell)

1) Install a prerequisite for the process:
```Bash
sudo yum install wget
```

2) Download the CDP installer to the machine: 
```Bash
wget https://archive.cloudera.com/cm7/7.4.4/cloudera-manager-installer.bin
```

3) Change the permissions of the Cloudera Manager Installer file to allow execution:
```Bash
chmod u+x cloudera-manager-installer.bin
```

4) Execute the installer with the elevated permissions:
```Bash
sudo ./cloudera-manager-installer.bin
```
*Tip: it will start the installation of Cloudera Manager repository files, Oracle JDK, Cloudera Manager Server along with embedded PostgreSQL packages and other libraries.

5) After the installation is complete, you'll get an `URL` with a `port` to open in your Web browser, remember the port configuration. 

6) Do not forget to start the server on the machine and see it running:
```Bash
sudo systemctl start cloudera-scm-server

sudo systemctl status cloudera-scm-server
```

## Installing Cloudera - Part 2 (Web browser)

7) Go to the `networking` tab of your `Master` instance on AWS EC2 settings and copy the `Public IPv4 address`. Paste it in a new tab in your web browser followed by the `port` number you got in the [[Installing Cloudera on AWS RHEL#Installing Cloudera - Part 1 (SSH Shell)]] last step. It will look like (i.e.: `http://26.649.20.2:7180/`);

8) Log in to Cloudera Manager with the default credentials (Username: admin, Password: admin).

9) When logged in, you'll see a welcome page and two installation options (`Upload Cloudera Data Platform License` and `Try Cloudera Data Platform for 60 days`). Choose the one that suits you best;

Continue
[[Creating a Bare Metal cluster]]
