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
Hosted in Azure; documentation and scripts are available here.

## Why is This Important?
Storing credentials and sensitive information in code repositories or environment variables poses a security risk. Azure Key Vault provides a centralized and secure method for managing and retrieving secrets.

---

## Steps to Complete This Lab

### Step 1: Create an Azure Key Vault
**Azure Key Vault** is a cloud service provided by Microsoft that securely stores and manages sensitive information such as **secrets**, **encryption keys**, and **certificates**. It is designed to help safeguard cryptographic keys and secrets used by cloud applications and services.

---

### Key Capabilities:
- **Secrets Management**: Securely store API keys, passwords, database connection strings, and other confidential information.
- **Key Management**: Generate and manage encryption keys used for data protection.
- **Certificate Management**: Provision, manage, and deploy SSL/TLS certificates for secure communication.
- **Access Control**: Integrates with Azure Active Directory (Microsoft Entra ID) to enforce fine-grained access policies using role-based access control (RBAC) or access policies.

---

### Why It Matters:
- **Security**: Secrets and keys are stored in a hardware security module (HSM)-backed vault.
- **Centralized Management**: Provides a centralized and consistent method for managing sensitive information across applications.
- **Compliance**: Helps meet compliance requirements by keeping audit logs of secret usage and access.
- **Automation**: Supports integration with scripts, applications, and services through Azure SDKs and REST APIs.


1. Open the Azure portal and navigate to **Key Vaults**.  
![image](https://github.com/user-attachments/assets/86117e64-f788-4616-9cbf-78dfb330c012)

2. Click **Create** and configure the following:  
![image](https://github.com/user-attachments/assets/5106f54a-ac99-49bc-94cf-2f61da3d5187)

    - **Subscription:** Select the free-tier subscription.  
   - **Resource Group:** Create a new resource group or use an existing one.  
   - **Key Vault Name:** Enter a globally unique name.  
   - **Region:** Choose the appropriate Azure region.  
   - **Pricing Tier:** Select **Standard** (free-tier supports basic features).  
3. Click **Review + Create** and then **Create**.
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
![image](https://github.com/user-attachments/assets/25c2f867-ed03-486d-a65f-d9a70fa55b32)



4. Enter the **Name** (e.g., `DBPassword`) and **Value** (e.g., `MyStrongP@ssw0rd`).  
5. Click **Create**.
![image](https://github.com/user-attachments/assets/f2710bbe-e4ed-4dc1-930a-99321ba031ad)
![image](https://github.com/user-attachments/assets/cc5ca411-f174-474b-bf72-7af450ef7369)


### Step 3: Retrieve a Secret Using Azure CLI
**Definition:** The Azure CLI (Command-Line Interface) is a cross-platform tool that allows users to manage Azure resources from a terminal or command prompt using commands. The CLI simplifies automation, scripting, and remote management of Azure services.
![image](https://github.com/user-attachments/assets/8d55ae91-d8da-4c87-98c8-97f21eb8a278)

1. Retrieve the secret value:  
   ```sh
   az keyvault secret show --name DBPassword --vault-name <YourKeyVaultName> --query value -o tsv
   ```  
2. The output should display the stored secret value securely.
![image](https://github.com/user-attachments/assets/e7771a05-78b0-4c97-a65e-192c81d7d8ae)

Secure Access to Secrets (Optional)
**Managed Identities for Azure resources** provide Azure services with an automatically managed identity in Microsoft Entra ID (Azure AD). This identity can be used to authenticate securely to other services—like Azure Key Vault—without needing to store credentials in application code, environment variables, or configuration files.

**Why it matters:**
- Eliminates the need to manage credentials manually.
- Enhances security by avoiding hardcoded secrets in source code.
- Supports both **system-assigned** and **user-assigned** identities for flexible access control.

---

### Enable Azure Private Link to Restrict Key Vault Access to Private Networks

**Azure Private Link** enables private and secure connectivity from virtual networks to Azure Key Vault using a **private endpoint**. This ensures that traffic between the virtual network and the Key Vault remains entirely within the Microsoft backbone network, avoiding exposure to the public internet.

**Why it matters:**
- Reduces the risk of data exfiltration and exposure to external threats.
- Provides secure, internal-only access to secrets and keys.
- Aligns with zero-trust and defense-in-depth security models.

---

### Enable Logging and Monitoring with Azure Monitor and Diagnostic Settings

**Azure Monitor** and **Diagnostic settings** allow for the collection, analysis, and alerting of telemetry data from Azure Key Vault. Logs can be sent to **Log Analytics**, **Event Hubs**, or a **Storage Account** for auditing, troubleshooting, and compliance purposes.

**Why it matters:**
- Tracks who accessed secrets and when.
- Detects unusual or unauthorized access attempts.
- Supports compliance reporting and forensics.

**Common logs enabled:**
- **AuditEvent**: Logs all access and management operations.
- **AllMetrics**: Monitors performance and request metrics like latency, success/failure rates, etc.

---

## Conclusion
Azure Key Vault ensures that sensitive information such as passwords, API keys, and certificates are securely managed. Implementing strict access controls and logging mechanisms further enhances security in cloud environments.

---

## Next Steps
- Automate secret retrieval in applications using Azure SDKs.  
- Integrate Key Vault with Azure DevOps for CI/CD secrets management.  
- Enable soft delete and purge protection to prevent accidental data loss.

