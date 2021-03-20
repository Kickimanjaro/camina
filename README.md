# camina

Gist:
Goal is to have at least two nodes handling traffic for a VIP in a highly-available fashion


Ubuntu Server 20.04 LTS
NICs:
- corporate
- __heartbeat__
- __management?__

Ansible playbook to:
- [ ] configure vrrpd
- [ ] configure haproxy
- [ ] configure keepalived


# basics
## VRRP
first, is this required or is it handled as part of keepalived install?
- install vrrpd
## sysctl configuration
- configure system networking to accept connections from a VIP
- lineinfile (`/etc/sysctl.conf`)
  - net.ipv4.ip_nonlocal_bind=1
- restart sysctl
## keepalived
install keepalived
configure keepalived (`/etc/keepalived/keepalived.conf`)
  - current node IP for config
  - peer node IPs for config
  - state and priority of current node
  - which interface has VRRP (`corporate_interface`)
  - what is the VIP?

http://docs.podman.io/en/latest/

## VRRP
- https://manpages.ubuntu.com/manpages/focal/man8/vrrpd.8.html
- https://medium.com/@abhilashkulkarni340/vrrp-and-4-simple-steps-to-set-it-up-on-ubuntu-454c46abb3b4

## HAproxy
https://cbonte.github.io/haproxy-dconv/2.4/configuration.html
https://www.linode.com/docs/guides/how-to-use-haproxy-for-load-balancing/

## keepalived
- https://www.digitalocean.com/community/tutorials/how-to-set-up-highly-available-haproxy-servers-with-keepalived-and-floating-ips-on-ubuntu-14-04



how others have done this:
https://geek-cookbook.funkypenguin.co.nz/ha-docker-swarm/keepalived/
https://akshayuppal90.medium.com/setting-up-a-ha-cluster-using-docker-swarm-and-keepalived-f158aeba2fe9
