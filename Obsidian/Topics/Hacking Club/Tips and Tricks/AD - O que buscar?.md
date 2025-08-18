
### Low hangig fruits
Para explorar um ambiente de Active Directory de forma eficiente é necessário entender os caminhos mais curtos para se atingir o objetivo de obter controle de um Domain Admin.

```
Compartilhamentos disponiveis
NTLM Relay
AD CS
Password Spary
Senhas padrão
Aplicações Internas
Versões com CVE
```

### Recon
Recon a melhor forma de verificar qual o caminho mais curto é a partir de um recon bem feito, para isso, exitem diversas técnicas e ferramentas.
**ldp.exe** - Ferramenta da microsoft para fazer consultas LDAP.
**BloodyAD** - Fazer consultas no domínio se houver credenciais válidas.
**NetExec** - Principal ferramenta para enumerar um Active Directory.
**BloodHound** - Ferramenta para fazer um mapa do Domínio.
**Impacket** - Um canivete Suíço para explorar de ambientes Windows.
**Consultas PowerShell / Powerview** - Podemos utilizar se tivermos acesso em alguma máquina dentro do domínio.

### Checklist / Cheatsheet
 - 1.Enumeração LDAP com usuário guest ou baixo privilégio
 - 2.Usuários sem pré-autenticação habilitada.
 - 3.Interpretação man-in-the-middle e relay
 Interceptar o trafego na rede e encaminha hashes NTLM.
  - 4. AD CS e templates de certificado vulneráveis
  O AD CS permite que usuários configurem templates de certificado e quando há uma má configuração desses templates podemos escalar privilégios para esse usuário.
  - 5. Compartilhamentos de SMB
  - 6. Bloodhound
  E podemos continuar com delegações, privilégios de contas, aplicações, etc...







