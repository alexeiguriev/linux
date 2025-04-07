***users***


**Get users list**

```cat /etc/passwd```

**set use password**

```sudo passwd <username>```

**Add user**

```adduser <user name>```

**Switch user**

```sudo su```


**check the user group**

```groups <username>```

**delete the user**

```sudo userdel <user name>```

**make user admin**

```# When creating new users, give them appropriate sudo rights
sudo usermod -aG sudo newusername```


```# Or add them to the sudo group during creation
sudo useradd -m -G sudo newusername```


**create a group**
```sudo groupadd <new group name>
getent group <group name>```
