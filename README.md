# worlak2_infra
worlak2 Infra repository

1 Connect via one host to another
ssh -A -J unwork@51.250.74.185 unwork@10.128.0.10
2 Connect to host via alias
alias someinternalhost='ssh -A -J unwork@51.250.74.185 unwork@10.128.0.10'
ssh someinternalhost

3 Vpn load
bastion_IP = 51.250.74.185
someinternalhost_IP = 10.128.0.10

Deploy test app
testapp_IP = 51.250.77.247 
testapp_port = 9292

yc compute instance create \
  --name reddit-app \
  --hostname reddit-app \
  --memory=4 \
  --create-boot-disk image-folder-id=standard-images,image-family=ubuntu-1604-lts,size=10GB \
  --network-interface subnet-name=default-ru-central1-a,nat-ip-version=ipv4,nat-address=51.250.77.247 \
  --metadata serial-port-enable=1 \
  --metadata-from-file user-data=metadata.yml
