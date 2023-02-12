# DNS Client Tools

**Install DNS Client Tool.**

```
# yum install bind-utils
```
Find Available Package.
```
# rpm -ql bind-utils
```

# <font size=5>Commands</font>

### dig

```
# dig IP/domain name
```
```
# dig IP/Domain_name @localdomain
```

```
# dig IP/Domain _Name Enter_Record_Type
```

```
# dig -4 Enter_IPv4
```

```
# dig -6 Enter_IPv6
```

```
# dig IP/Domain_Name +sort
```

```
# dig 8.8.8.8 +short
```

```
# dig example.com AAAA +noquestion
```

```
# dig example.com MX +short
```

```
# dig -4 8.8.8.8 NS +noanswer
```

```
# dig -t AAAA example.com
```

```
# dig -t A example.com +short
```

```
# dig example.com any
```

### host

```
# host  IP/Domain_Name
```

```
# host -t Enter_Domain_Record IP/Domain_Name`
```
```
# hosr -t A example.com
```

```
# host example.com
```

```
# host 8.8.8.8
```

```
# host -a example.com
```

```
# host -4 8.8.8.8
```

### nslookup

```
# nslookup example.com
````

```
# nslookup -type=SOA example.com
```
```
nslookup example.com localdomain
```
