# Secure Secrets Management with Azure Key Vault

## Summary
This lab demonstrates how to securely store and manage secrets, encryption keys, and certificates using Azure Key Vault. Azure Key Vault provides centralized secret management to safeguard sensitive data and enforce security best practices.

---

## Lab Requirements
- Azure free tier subscription  
- Azure CLI or Azure PowerShell  
- Azure portal access  
- Basic understanding of Azure security principles  

---

## Who is This For?
IT professionals, security engineers, and cloud administrators looking to implement secure secret management in Azure.  

## What Will You Learn?
This lab covers the setup of Azure Key Vault, storing secrets, managing access permissions, and retrieving secrets securely.  

## When to Use This Lab?
When handling credentials, API keys, or encryption keys that must be securely stored and accessed in cloud environments.  

## Where is This Lab Hosted?
Hosted in Azure; documentation and scripts will be available in GitHub.  

## Why is This Important?
Storing credentials and sensitive information in code repositories or environment variables poses a security risk. Azure Key Vault provides a centralized and secure method for managing and retrieving secrets.

---

## Steps to Complete This Lab

### Step 1: Create an Azure Key Vault
**Definition:** Azure Key Vault is a cloud service that securely stores and controls access to secrets, encryption keys, and certificates. Creating a Key Vault ensures that sensitive information remains protected from unauthorized access.

1. Open the Azure portal and navigate to **Key Vaults**.  
2. Click **Create** and configure the following:  
   - **Subscription:** Select the free-tier subscription.  
   - **Resource Group:** Create a new resource group or use an existing one.  
   - **Key Vault Name:** Enter a globally unique name.  
   - **Region:** Choose the appropriate Azure region.  
   - **Pricing Tier:** Select **Standard** (free-tier supports basic features).  
3. Click **Review + Create** and then **Create**.

### Step 2: Store a Secret in Azure Key Vault
**Definition:** Secrets in Azure Key Vault are sensitive information such as passwords, API keys, and connection strings that need to be securely stored and accessed when needed.

**Definition:** An API (Application Programming Interface) is a set of protocols and tools that allow different software applications to communicate. API keys are used to authenticate and authorize access to services and resources.

1. Open the newly created Key Vault.  
2. Navigate to **Secrets** and click **+ Generate/Import**.  
3. Enter the **Name** (e.g., `DBPassword`) and **Value** (e.g., `MyStrongP@ssw0rd`).  
4. Click **Create**.

### Step 3: Configure Access Control (IAM)
**Definition:** Access control in Azure Key Vault ensures that only authorized users and applications can retrieve or modify secrets. This step sets the permissions for accessing stored secrets securely.

1. Go to the **Access policies** section in the Key Vault.  
2. Click **+ Create** and assign appropriate permissions:  
   - **Select principal:** Choose a user, service principal, or managed identity.  
   - **Secret permissions:** Select **Get, List, Set** for secret management.  
3. Click **Review + Add**, then **Save**.

### Step 4: Retrieve a Secret Using Azure CLI
**Definition:** The Azure CLI (Command-Line Interface) is a cross-platform tool that allows users to manage Azure resources from a terminal or command prompt using commands. The CLI simplifies automation, scripting, and remote management of Azure services.

1. Open a terminal and authenticate to Azure:  
   ```sh
   az login
   ```  
2. Retrieve the secret value:  
   ```sh
   az keyvault secret show --name DBPassword --vault-name <YourKeyVaultName> --query value -o tsv
   ```  
3. The output should display the stored secret value securely.

### Step 5: Secure Access to Secrets
**Definition:** Implementing additional security measures ensures that secrets stored in Azure Key Vault remain protected against unauthorized access and potential breaches.

- Use **Managed Identities** for Azure resources instead of storing credentials in application configurations.  
- Enable **Azure Private Link** to restrict Key Vault access to private networks.  
- Enable **logging and monitoring** with Azure Monitor and Diagnostic settings.

---

## Conclusion
Azure Key Vault ensures that sensitive information such as passwords, API keys, and certificates are securely managed. Implementing strict access controls and logging mechanisms further enhances security in cloud environments.

---

## Next Steps
- Automate secret retrieval in applications using Azure SDKs.  
- Integrate Key Vault with Azure DevOps for CI/CD secrets management.  
- Enable soft delete and purge protection to prevent accidental data loss.

