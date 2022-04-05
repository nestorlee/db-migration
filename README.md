# db-migration

1. You will need to install Azure CLI first. Instructions here: https://docs.microsoft.com/en-us/cli/azure/install-azure-cli
2. After installing Azure CLI, run a "az login" to get the necessary credentials to run the TF script.
3. "terraform plan" then "terraform apply" to build the infrastructure on Azure.
4. The Public IP of the VM should be listed as part of the outputs after the TF script runs successfully.
5. "ssh azureuser@<publicIP>" to access the VM. The password is described in the TF script.
6. You will need to chmod and chown the script that was downloaded. Perform the following: "sudo chown azureuser /home/azureuser/download_scripts.sh" and "sudo chmod 700 /home/azureuser/download_scripts.sh".
7. Run the script by executing "sh download_scripts.sh".
8. Init the VM and install MySQL with the command "sudo sh init_script.sh". You may encounter an issue which it gets stuck during the MySQL installation with the following error: "Processing triggers for ureadahead". Continue to let it run for 5 minutes and see if it unfreezes itself. Otherwise do a "Ctrl+C" to exit.
9. Run a "sudo sh init_mysql.sh" to init the MySQL database. Ignore the warnings about using passwords on the CLI interfaces.
10. Connect to the MySQL database with "mysql -u root -p". Password is "password".
11. The TF script also creates a Azure Databse for MySQL instance. It's FQDN should be listed as part of outputs.
12. To connect to the Azure DB for MySQL instance, run a "mysql -h <fqdn> -u mysqladmin -p" on the VM created via the script.
