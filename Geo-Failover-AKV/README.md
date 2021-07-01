Geo-Failover AKV

## 1. Introduction
SQL Managed Instance (SQL MI) provides a SQL database with near 100% compatibility with the latest version of SQL Enterprise Edition. The architecture described in this article will provide a highly available SQL Managed Instance deployment with geo-replication and customer-managed TDE keys as well as Private Endpoint enabled for Key Vault.

## 2. What is TDE?
Transparent Data Encryption (TDE) is a method of encrypting a SQL Server database (at rest). Click [here](https://docs.microsoft.com/en-us/sql/relational-databases/security/encryption/transparent-data-encryption?view=azuresqldb-mi-current) to read more about how TDE works specifically with SQL MI.

When customers want to manage their own TDE keys (as opposed to having Microsoft manage them), a customer-managed Key Vault is required. Key Vault is an Azure service that securely stores secrets and keys. To read more about Key Vault, click [here](https://azure.microsoft.com/en-us/services/key-vault).

## 3. SQL MI Geo-Replication

3. Paired Regions
4. Azure Key Vault



![](./media/sqlmi-akv.png)