# Installation Guide
Installing Terraform on any OS is very simple. Kindly follow the instruction on the official documentation page

## Installation on Ubuntu
Since I am running on ubuntu, here is how to setup Terraform on Ubuntu


```shell
wget -O - https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(grep -oP '(?<=UBUNTU_CODENAME=).*' /etc/os-release || lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update && sudo apt install terraform

```

## Testing the installation
To test if your installation is successful run this command: `terraform --version`

## Installing other key resources
- Install Terraform plugin on vscode
- Install autocomplete for terraform 

```shell
touch ~/.bashrc
terraform -install-autocomplete
```
