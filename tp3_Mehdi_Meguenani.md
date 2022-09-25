

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

