Credentials mit Proxmox API Key anpassen, ISO name anpassen


..\packer validate -var-file='..\credentials.pkr.hcl' .\ubuntu-server-jammy.pkr.hcl

..\packer build -var-file='..\credentials.pkr.hcl' .\ubuntu-server-jammy.pkr.hcl