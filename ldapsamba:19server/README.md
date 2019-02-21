# LDAP
## @edt Sergi Muñoz Carmona ASIX M06-ASO Curs 2018-2019

Podeu trobar les imatges docker al Dockerhub de [sergimc](https://cloud.docker.com/repository/docker/sergimc/serversmb)

ASIX M06-ASO Escola del treball de barcelona

* **sergimc/ldapserver:19smb**  servidor ldap amb la base la dades dc=edt,dc=org.
Per posar en funcionament aquest model només es necessita un servidor ldap.


#### Execució

```
docker run --rm --name ldap --hostname ldap --network sambanet -d sergimc/ldapserver:19smb

```
En aquesta pràctica, afegirem un schema de samba per tal de que funcioni el server smb amb ldap com a backend.

- sambaSergi.schema

