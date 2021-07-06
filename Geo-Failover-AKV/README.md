Geo-Failover AKV

## 1. Introduction
SQL Managed Instance (SQL MI) provides a SQL database with near 100% compatibility with the latest version of SQL Server Enterprise Edition. Many organizations choose SQL MI because of that compatibility, its ability to be deployed into a VNET, its built-in high availability, and because there are no virtual machines or operating systems to manage. The architecture described in this article will present a highly available SQL Managed Instance deployment with geo-replication and customer-managed TDE keys as well as Private Endpoint enabled for Key Vault.

## 2. What is TDE?
Before we dive into the design, it's important to understand some of the components that make this possible. There are a number of things that are recommended when designing a secure system. One important practice is to encrypt your database. This ensures that if a malicious party steals a physical device with your data on it, the data on that device cannot be read without the certificates used to encrypt them. Transparent Data Encryption (TDE) does real-time I/O encryption / decryption of data and log files of a SQL Server database. TDE protects data at rest as opposed to across communication channels (in flight). Click [here](https://docs.microsoft.com/en-us/sql/relational-databases/security/encryption/transparent-data-encryption?view=azuresqldb-mi-current) to read more about how TDE works, specifically with SQL MI.

There are two options When customers want to manage their own TDE keys: Customer-Managed keys (CMK) or Microsoft-Managed. if you decide to go with CMK, [Azure Key Vault](https://docs.microsoft.com/en-us/azure/key-vault/general/overview) is required to securely stores secrets and keys required by TDE.



## 3. Architecture Overview
SQL MI will be deployed in a primary region and a secondary region. Microsoft recommends using paired regions as it will significantly improve replication performance. SQL MI requires a subnet in your VNET to be deployed into:

![](./media/sqlmi-akv.png)


You will also need to deploy Azure Key Vault. This is a PaaS service so it gets deployed with a public IP address. Like most organizations, you probably want to restrict access to public IPs as much as possible. This can be done using Private Link / Private Endpoint.

 However, when you're using customer-managed keys (CMK), you're now required to use a Key Vault that cannot be deployed in your VNET. You can use Private Link / Private Endpoint to have a virtual NIC representing your Key Vault get dropped into your VNET to overcome this.

Geo-Replication
Customers need to plan for disaster. With SQL MI, you can create failover groups and add your primary and secondary Managed Instances to that failover group.

3. Paired Regions
4. Azure Key Vault



![](./media/sqlmi-akv.png)