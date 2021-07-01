Geo-Failover AKV

## 1. Introduction
SQL Managed Instance (SQL MI) provides a SQL database with near 100% compatibility with the latest version of SQL Enterprise Edition. The architecture described in this article will provide a highly available SQL Managed Instance deployment with geo-replication and customer-managed TDE keys as well as Private Endpoint enabled for Key Vault.

## 2. What is TDE?
Transparent Data Encryption (TDE) is a method of encrypting a SQL Server database (at rest). Click [here](https://docs.microsoft.com/en-us/sql/relational-databases/security/encryption/transparent-data-encryption?view=azuresqldb-mi-current) to read more about how TDE works specifically with SQL MI.

When customers want to manage their own TDE keys (as opposed to having Microsoft manage them), a customer-managed Key Vault is required. Key Vault is an Azure service that securely stores secrets and keys. To read more about Key Vault, click [here](https://azure.microsoft.com/en-us/services/key-vault).



## 3. Architecture Overview
Many organizations choose SQL MI because of its compatibility with on-premises SQL Server Enterprise, because it can be deployed in your VNET, and because they don't have to manage it like they do SQL Server on virtual machines. However, when you're using customer-managed keys (CMK), you're now required to use a Key Vault that cannot be deployed in your VNET. You can use Private Link / Private Endpoint to have a virtual NIC representing your Key Vault get dropped into your VNET to overcome this.

Geo-Replication
Customers need to plan for disaster. With SQL MI, you can 

3. Paired Regions
4. Azure Key Vault



![](./media/sqlmi-akv.png)