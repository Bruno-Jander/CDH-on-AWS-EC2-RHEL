PREVIOUS: [Creating a Bare Metal cluster](https://github.com/Bruno-Jander/CDH-on-AWS-EC2-RHEL/blob/2b823edea22b0d2e26fd811012c3cc7abb93b11b/Cloudera_CDH_on_AWS%20(Part%203).md)

# Adding services to your Bare Metal Cluster

## Add Cluster - Configuration

1) On the `Select Services` page you can choose if you want to install a predefined combination of services (data engineering, data mart, operational database) or manually pick the services for your cluster.
*Tip: install basic services (HDFS, YARN and Zookeeper) first, so you don't have to configure a lot of parameters all at once. Install additional services later.*

2) On the `Assign Roles` page you can configure what hosts will run the component services.

3) On the `Setup Database` page you can configure the database credentials for your services:
	- `Use Embedded Database`: for testing purposes (not recommended for production environment);
	- `Use Custom Databases`: manually configure the credentials before using them;

*Tip: do not forget to save your database credentials.*

4) You will only have to provide some information on the `Enter Required Parameters` page if asked.

5) On the `Review Changes` page you can see and change (if needed) the default parameters for some of your services.

6) On the `Command Details` page you'll see the progress of services installation on the hosts in your cluster.

7) The services addition configuration will end on the `Summary` page.

- That's all folks! Enjoy your new CDH cluster! :)

THE END
