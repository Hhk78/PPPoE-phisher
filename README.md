# ilk önce çalıştırılması gerekenler
```touch /var/log/pppoe-server-log
chmod 0774 /var/log/pppoe-server-log
```

# /etc/ppp/pppoe-server-options içeriği
```
require-pap
login
lcp-echo-interval 10
lcp-echo-failure 2
show-password
debug
logfile /var/log/pppoe-server-log
```
# /etc/ppp/pap-secrets içeriği
```
# Kullanıcı Adı       Sunucu (Server)      Şifre            Kullanılabilir IP
*                     *                   ""               *

```
# en son çalışacaklar (sırasıyla)
```
sudo tail -f /var/log/pppoe-server-log
```

```
sudo pppoe-server -F -I enp6s0.35 -O /etc/ppp/pppoe-server-options
```

# eğer vlan varsa (telekomda vlan id 35tir)

```
sudo ip link add link enp6s0 name enp6s0.35 type vlan id 35
sudo ip link set dev enp6s0.35 up
```
