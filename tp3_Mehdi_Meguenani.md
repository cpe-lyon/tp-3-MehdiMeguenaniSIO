

# Exercice 1. Gestion des utilisateurs et des groupes

1. Utilisez la commande groupadd pour créer deux groupes dev et infra  
Pour ajouter les groupes dev et infra il faut faire  
``` bash
groupadd dev ; groupadd infra 
```  
![ScreenShot](./assetp3/Q1.PNG)  
2. Créez ensuite 4 utilisateurs alice, bob, charlie, dave avec la commande useradd, en demandant la création de leur dossier personnel et avec bash pour shell  
Afin d'ajouter les 4 utiliseurs en demandant la création de leur dissier bash avec bahs il faut effectuer les commandes suivante pour chaque utilisateur
``` bash
 useradd -m alice
 usermod --shell /bin/bash alice
 
 useradd -m alice
 usermod --shell /bin/bash bob

 useradd -m alice
 usermod --shell /bin/bash charlie
 
 useradd -m alice
 usermod --shell /bin/bash dave
 
```  
![ScreenShot](./assetp3/Q2.PNG)

3. Ajoutez les utilisateurs dans les groupes créés : alice, bob, dave dans dev // bob, charlie, dave dans infra  

``` bash

 usermod -a -G dev alice
 usermod -a -G dev bob 
 usermod -a -G dev dave
 

 usermod -a -G infra bob
 usermod -a -G infra charlie 
 usermod -a -G infra dave
 
```  
![ScreenShot](./assetp3/Q3.PNG)

4. Donnez deux moyens d’afficher les membres de infra  
Les deux moyens pour afficher les membres de infra sont : 
``` bash

grep infra /etc/group

getent group dinfra

 ``` 
 ![ScreenShot](./assetp3/Q4.PNG)
 
5. Faites de dev le groupe propriétaire des répertoires /home/alice et /home/bob et de infra le groupe
propriétaire de /home/charlie et /home/dave

Pour faire de dev le groupe prioritaire de bob et alice il faut faire : 

``` bash
   chgrp -R dev /home/alice
   chgrp -R dev /home/bob
   
 ```
 Pour faire de infra le groupe prioritaire de bob et alice il faut faire : 
 
 ``` bash
   chgrp -R infra /home/charlie
   chgrp -R infra /home/dave
   
 ```
 
 usermod -g dev alice

6. Remplacez le groupe primaire des utilisateurs :  dev pour alice et bob // infra pour charlie et dav

Pour faire de dev le groupe primaire de bob et alice il faut faire : 

``` bash
    usermod alice -g dev
    usermod bob -g dev
 ```
Pour faire de infra le groupe primaire de dave et charlie il faut faire : 
 
 ``` bash
    usermod charlie -g infra
    usermod dave -g infra
 ```
7. Créez deux répertoires /home/dev et /home/infra pour le contenu commun aux membres de chaque groupe, et mettez en place les permissions leur permettant d’écrire dans ces dossiers. 
Il faut créer deux répertoire : 
```bash
mkdir dev
mkdir infra

```
Il faut ensuite modifier le groupe cible du dossier : 
```bash
chgrp -R infra ./infra
chgrp -R dev ./dev
```
Ensuite pour ajuter les droit d'écriture sur le dossier au groupe il faut faire : 
```bash
chmod 720 dev
chmod 720 infra
```
On peut aussi autoriser les groupes a entrer dans le fichier en faisant : 
```bash
chmod 730 dev
chmod 730 infra
```
![ScreenShot](./assetp3/Q7.PNG)

8. Comment faire pour que, dans ces dossiers, seul le propriétaire d’un fichier ait le droit de renommer
ou supprimer ce fichier ?  

Afin que seul le propriétaire du fichier est le droit de supprimer ou de renommer le fichier il faut faire la commande : 
```bash
 sudo chmod 700 dev
 sudo chmod 700 infra
```

9. Pouvez-vous ouvrir une session en tant que alice ? Pourquoi ?

On ne peut pas ouvrir une session en tant que Alice car aucun mot de passe n'a été défini

10. Activez le compte de l’utilisateur alice et vérifiez que vous pouvez désormais vous connecter avec son
compte.

Pour acctive le compte d'un utilisateur il faut lui ajouter un mot de passe qui en faisant la commande : 
```bash
passwd alice
```
Pour verifier la connexion il faut utiliser la commande : 
```bash
su alice
```
![ScreenShot](./assetp3/Q10.PNG)

11. Comment obtenir l’uid et le gid de alice ?

Pour obtenir l'udi et le gid de Alice il faut effectuer la commande : 
```bash
id alice
```
![ScreenShot](./assetp3/Q11.PNG)


12. Quelle commande permet de retrouver l’utilisateur dont l’uid est 1003 ?

La commande qui permet de trouver un utilisateur en fonction de son Id est : 

```bash
id 1003
```
![ScreenShot](./assetp3/Q12.PNG)

13. Quel est l’id du groupe dev ?

Pour trouver l'ID du groupe dev il faut faire la commande suivante : 

```bash
grep dev /etc/group
```
![ScreenShot](./assetp3/Q13.PNG)

grep 1002 /etc/group

14. Quel groupe a pour gid 1002 ?

Pour trouver le groupe dont l'ID est 1002 il faut faire la commande : 

```bash
grep 1002 /etc/group
```
15. Retirez l’utilisateur charlie du groupe infra. Que se passe-t-il ? Expliquez.

Pour retirer l'utilisateur du groupe il faut effectuer : 
gpasswd --delete charlie infra
```bash
gpasswd -d charlie infra
``` 
Après cela Charlie a toujours accès au différent groupe primaire et prioritaire état infra

