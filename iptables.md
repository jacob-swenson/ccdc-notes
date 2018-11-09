# iptables
## Get info
```
iptables -L # List current rules
iptables -S # List current rules in input format
iptables -L --line-numbers # List rules with line-numbers
```

## Changing rules
```
iptables -F # Revert to default policies

iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
# -A INPUT: Append rule to INPUT chain
# -m conntrack: An extension module that gives access to commands that make decisions based on packet's relationship to previous connections
# --ctstate: child of conntrack module, matches packets based on how they are related to packets we've seen before
# ESTABLISHED: Part of existing connection
# RELATED: Part of an established connection
# -j ACCEPT: Behavior

iptables -A INPUT -p tcp --dport 22 -j ACCEPT # Accept connections on port 22

iptables -I INPUT 1 -i lo -j ACCEPT: Accept loopback packets

iptables -P INPUT DROP # Set default input policy to drop

iptables -A INPUT -j DROP # Default policy remains intact, sets drop rule after existing rules (prevents issues when reverting)

iptables -D INPUT -j DROP # Remove drop rule (to add new rule) 

iptables -I INPUT 4 <new_rule> # Insert rule at line 4
```

## Ban/Allow IP Address
```
iptables -A INPUT -s <ip> -j DROP
iptables -A OUTPUT -s <ip> -j DROP
iptables -A INPUT -s <ip> -j ALLOW
```


## Persistent Rules
```
apt-get install iptables-persistent
invoke-rc.d iptables-persistent save # save rules, will remain on server restart
```
