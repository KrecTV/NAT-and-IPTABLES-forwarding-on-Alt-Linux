# NAT-and-IPTABLES-forwarding-on-Alt-Linux

# https://habr.com/ru/sandbox/274318/


apt-get update

apt-get install -y nano

apt-get install -y iptables

nano /etc/net/sysctl.conf

net.ipv4.ip_forward = 1

sysctl -p /etc/net/sysctl.conf

iptables -t nat -A POSTROUTING -o enp7s1 -j MASQUERADE

iptables-save > /etc/sysconfig/iptables

systemctl enable --now iptables
