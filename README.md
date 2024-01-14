# Privilege Escalation - NGINX / SUDO

Condition - You must have sudo permission on `nginx`:

```bash
user@host:~$ sudo -l
Matching Defaults entries for user on host:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin, use_pty

User user may run the following commands on host:
    (ALL : ALL) NOPASSWD: /usr/sbin/nginx
```

From an existing interractive session create or upload the `exploit.sh` script.

This exploit will create a nginx configuration and load it.
The configuration will allow you to `PUT` resources in the system with root permission. 
The script will generate a SSH key and store it as authorized key to connect to the root account.

Run the exploit on the target: 
```bash
./exploit.sh
```

Store the SSH Private Key then use it to connect to the host: 
```bash
chmod 600 root_key
ssh -i root_key root@host
```


## Credit 

- Exploit redaction - GRILL Dylan
- Based on Darren Martyn exploit - https://darrenmartynie.wordpress.com/2021/10/25/zimbra-nginx-local-root-exploit/
