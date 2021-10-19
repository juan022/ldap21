# LDAP Server
## @edt ASIX M06-ASO 2021-2022
### Servidor LDAP (Debian 11)

Podeu trobar les imatges docker al Dockehub de [edtasixm06](https://hub.docker.com/u/edtasixm06/)

Podeu trobar la documentació del mòdul a [ASIX-M06](https://sites.google.com/site/asixm06edt/)

ASIX M06-ASO Escola del treball de barcelona


 * **edtasixm06/ldap21:schema** Servidor LDAP amb la base de dades edt.org
   S'ha fet el següent:

   * futbolista.schema DErivat de inetOrgPerson, structural, injectat dades de dades-futbolistaA.ldif
```
docker run --rm --name phpldapadmin.edt.org -h phpldapadmin.edt.org --net 2hisix -p 80:80 -d edtasixm06/phpldapadmin:20
docker run --rm --name ldap.edt.org -h ldap.edt.org --net 2hisix -p389:389 -it juan22/ldap21:schema /bin/bash
```


```
docker network create hisx2
docker build -t edtasixm06/ldap21:editat .

docker run --rm --name ldap.edt.org -h ldap.edt.org --net hisx2 -p 389:389 -d edtasixm06/ldap21:base

docker ps

ldapsearch -x -LLL -h ldap.edt.org -b 'dc=edt,dc=org'
``` 


