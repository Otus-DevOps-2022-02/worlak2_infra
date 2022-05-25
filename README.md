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
