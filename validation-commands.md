# Validation Commands

```bash
sudo containerlab deploy -t clos-lab.yml
sudo containerlab inspect -t clos-lab.yml
sudo docker ps --format "table {{.Names}}\t{{.Status}}"
sudo docker exec -it clab-clos-lab-spine1 vtysh
show bgp summary
show bgp l2vpn evpn
sudo docker exec -it clab-clos-lab-leaf1 vtysh
show running-config
sudo containerlab destroy -t clos-lab.yml
```
