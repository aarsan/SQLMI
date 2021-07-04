Geo-Failover AKV

## 1. Introduction
SQL Managed Instance (SQL MI) provides a SQL database with near 100% compatibility with the latest version of SQL Enterprise Edition. Many organizations choose SQL MI because of its compatibility with on-premises SQL Server Enterprise Edition, its ability to be deployed in your VNET, its built-in high availability, and because there are no virtual machines to be managed. The architecture described in this article will provide a highly available SQL Managed Instance deployment with geo-replication and customer-managed TDE keys as well as Private Endpoint enabled for Key Vault.

## 2. What is TDE?
Before we dive into the design, it's important to understand some of the components we're dealing with. There are a number of things that are recommended when designing a secure system. One important practice is to encrypt your database. This ensures that if a malicious party steals your physical device, the data on that device cannot be read without the certificates used to encrypt them. Transparent Data Encryption (TDE) does real-time I/O encryption / decryption of data and log files of a SQL Server database. TDE protects data at rest as opposed to across communication channels (in flight). Click [here](https://docs.microsoft.com/en-us/sql/relational-databases/security/encryption/transparent-data-encryption?view=azuresqldb-mi-current) to read more about how TDE works specifically with SQL MI.

There are two options When customers want to manage their own TDE keys (as opposed to having Microsoft manage them), a customer-managed Key Vault is required. Key Vault is an Azure service that securely stores secrets and keys. To read more about Key Vault, click [here](https://azure.microsoft.com/en-us/services/key-vault).



## 3. Architecture Overview
 However, when you're using customer-managed keys (CMK), you're now required to use a Key Vault that cannot be deployed in your VNET. You can use Private Link / Private Endpoint to have a virtual NIC representing your Key Vault get dropped into your VNET to overcome this.

Geo-Replication
Customers need to plan for disaster. With SQL MI, you can create failover groups and add your primary and secondary Managed Instances to that failover group.

3. Paired Regions
4. Azure Key Vault



![](./media/sqlmi-akv.png)