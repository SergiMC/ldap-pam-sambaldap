# SAMBA ldap+pam+ldapsmb
@edt Sergi Muñoz Carmona ASIX M06 2018-2019

Pràctica el qual muntarem un sitema de servidord LDAP, PAM i SAMBA o SAMBA tindrà LDAP com a backend.

Podeu trobar les imatges docker al Dockerhub de [sergimc](https://hub.docker.com/u/sergimc/)
ldap: [ldap](https://cloud.docker.com/repository/docker/sergimc/serversmb)
hpam: [hpam](https://cloud.docker.com/repository/docker/sergimc/hpamsmb)
samba: [samba](https://cloud.docker.com/repository/docker/sergimc/serversmb) #tag :19smb
## Imatges:
**sergimc/ldapserver:19smb** Servidor LDAP amb les dades de la base de dades dc=edt,dc=org Requereix de l'ús d'un servidor ldap.

**sergimc/hpamsmb:19smb** Servidor PAM que l'utilitzarem per connectar-nos i muntar els directoris dels usuaris samba. Requereix
server ldap+pam+samba.

**sergimc/serversmb:19smb** Servidor SAMBA que l'utilitzarem per tal de compartir els homes dels usuaris samba. 
Requereix de l'ús d'un servidor ldap, hostpam i ssh.

## Arquitectura

sambanet: Una xarxa propia per als containers implicats.

**sergimc/ldapserver:19smb**  Un servidor ldap en funcionament amb els usuaris de xarxa.

**sergimc/hpamsmb:19smb** Un servidor PAM per connectar-nos i poder montar els directoris dels usuaris samba.

**sergimc/serversmb:19smb** Un servidor SAMBA que l'utilitzarem per tal de compartit els homes dels usuaris samba.

## Execució

```
docker network create sambanet

docker run --rm --name ldap --hostname ldap --network sambanet -d sergimc/ldapserver:19smb

docker run --rm --name host --hostname host --network sambanet -it sergimc/hpamsmb:19smb

docker run --rm --name samba --hostname samba --network sambanet -it sergimc/serversmb:19smb
```
Explicació de configuració de cada servidor dins dels README de cada directori/server.
