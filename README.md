## 📝 Prerequisites

Before venturing into deploying Azure VMs using Ansible, ensure you have the following:

1. **Azure Subscription**: An active Microsoft Azure subscription is essential for VM management. If you're new to Azure, sign up for a [free trial](https://azure.microsoft.com/en-us/free/).
2. **Azure CLI**: The Azure Command-Line Interface (CLI) should be installed on your workstation. Grab it from the [Azure CLI installation page](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli).
3. **Ansible**: Ansible should be set up either on your local machine or on a dedicated control node. Here's the official Ansible [installation guide](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) for assistance.

## 🛠 Installation Steps

Deploying Azure VMs using Ansible is straightforward. Follow these steps:

### 1. **Open the Azure Portal and Access Cloud Shell**

Navigate to the Azure Portal and initiate the Cloud Shell via its icon adjacent to the Search bar. Install the necessary `pywinrm` package with:
```bash
pip install pywinrm>=0.3.0
```

### 2. Craft a Resource Group Using the Ansible Playbook

Launch a text editor of your choice and create `azure_vm_deployment.yml`. Inject the content provided below:

```yaml
---
- name: Create Azure VM
  hosts: localhost
  connection: local
  tasks:
    - name: Create resource group
      azure_rm_resourcegroup:
        name: asarmyResourceGroup
        location: eastus
```

### 3. Additional Variable Incorporation (Optional)

Feel free to tweak and customize your playbook by integrating more variables.

### 4. Execute the Ansible Playbook

Deploy the Azure Virtual Machines with:
```bash
ansible-playbook azure_vm_deployment.yml
```

### 5. Monitor Your Deployment

After the playbook execution, monitor the console output for any discrepancies. The Azure VMs should instantiate based on your playbook's configurations.

### 6. Post-Deployment Configuration (Optional)

If necessary, append more Ansible tasks to fine-tune the Azure VMs. This can include tasks like software installation, networking adjustments, or security configurations.

## 🚫 Troubleshooting

Encountered an issue? Consult the Troubleshooting Guide in this repository for guidance.

## 📚 Additional Resources:

- **Azure Ansible Modules Documentation**: Detailed information about using Ansible for Azure resources management.
  - [Azure Ansible Modules Documentation](https://docs.ansible.com/ansible/latest/collections/azure/azcollection/index.html)

- **Azure's Official Documentation**: The central portal for comprehensive Azure-related documentation.
  - [Azure's Official Documentation](https://docs.microsoft.com/en-us/azure/)

- **Ansible's Official Documentation**: Comprehensive guide and details about Ansible and its modules.
  - [Ansible's Official Documentation](https://docs.ansible.com/)
