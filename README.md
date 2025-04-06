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
![image](https://github.com/user-attachments/assets/86117e64-f788-4616-9cbf-78dfb330c012)

2. Click **Create** and configure the following:  
![image](https://github.com/user-attachments/assets/bed9eb28-fab2-4cc7-9857-d109a982afe0)

    - **Subscription:** Select the free-tier subscription.  
   - **Resource Group:** Create a new resource group or use an existing one.  
   - **Key Vault Name:** Enter a globally unique name.  
   - **Region:** Choose the appropriate Azure region.  
   - **Pricing Tier:** Select **Standard** (free-tier supports basic features).  
4. Click **Review + Create** and then **Create**.
![image](https://github.com/user-attachments/assets/4ab1ea07-751c-4ba1-a0fa-914bcc7facaa)
![image](https://github.com/user-attachments/assets/2273155a-249f-48ee-9719-11242364eaf1)
![image](https://github.com/user-attachments/assets/0c44ddcb-50c7-4c9d-916b-fec43f5ec488)

### Step 2: Store a Secret in Azure Key Vault
**Definition:** Secrets in Azure Key Vault are sensitive information such as passwords, API keys, and connection strings that need to be securely stored and accessed when needed.

**Definition:** An API (Application Programming Interface) is a set of protocols and tools that allow different software applications to communicate. API keys are used to authenticate and authorize access to services and resources.

1. Open the newly created Key Vault.  
2. Navigate to **Objects** and click **Secrets**.
![image](https://github.com/user-attachments/assets/6b178d0f-3115-4055-a5d1-ee231d4a7ec8)
3. Click **+Generate/Import**  
![image](https://github.com/user-attachments/assets/28989349-4e68-4ccc-8454-de6ce9f41b70)


4. Enter the **Name** (e.g., `DBPassword`) and **Value** (e.g., `MyStrongP@ssw0rd`).  
5. Click **Create**.
![image](https://github.com/user-attachments/assets/f2710bbe-e4ed-4dc1-930a-99321ba031ad)
![image](https://github.com/user-attachments/assets/809babc4-c3fc-4082-9503-030394b9518c)


### Step 3: Retrieve a Secret Using Azure CLI
**Definition:** The Azure CLI (Command-Line Interface) is a cross-platform tool that allows users to manage Azure resources from a terminal or command prompt using commands. The CLI simplifies automation, scripting, and remote management of Azure services.
![image](https://github.com/user-attachments/assets/8d55ae91-d8da-4c87-98c8-97f21eb8a278)

1. Retrieve the secret value:  
   ```sh
   az keyvault secret show --name DBPassword --vault-name <YourKeyVaultName> --query value -o tsv
   ```  
2. The output should display the stored secret value securely.
![image](https://github.com/user-attachments/assets/3caee9db-47eb-4213-8260-4c09cba3e864)

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

