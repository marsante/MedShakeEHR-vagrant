# MedShakeEHR-vagrant
### Un fichier Vagrant pour déployer rapidement un environnement de développement approvisionné par Ansible pour MedShakeEHR 

## Prérequis
- Avoir [VirtualBox](https://www.virtualbox.org/wiki/Downloads), [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) > 2.9 et [Vagrant](https://www.vagrantup.com/docs/installation) de configuré sur votre machine.
- Crée dans un but de démo ou de développement, ne pas utiliser en production avec des données réelles sans ajouter des paramètres de sécurité (mot de passe fort, https, contrôle d'accès).

## Installation 
- Cloner le projet.
- Créer un fichier `secrets.yml` à la racine du projet pour personnaliser les noms et mots de passes de la base de données comme dans l'exemple :

```yml
---
sqlRootPassword: motDePasseRoot
sqlUserAccount: user
sqlUserPassword: motDePasseUser
```

- Ouvrir un terminal à la racine du projet.
- Taper la commande suivante `vagrant up`.
- A la fin de l'exécution de la commande, ouvrir le navigateur se rendre à l'adresse suivante `http://55.55.55.5/install.php`.
- Vous pouvez finir la configuration de MedShakeEHR.
- Dans l'écran de configuration rapide cochez la case : `Ne pas créer la base de donnée`
- Le nom d'utilisateur et le mot de passe utilisateur correspondent à ce que vous avez choisi pour les variables `sqlUserAccount:` et `sqlUserPassword:`
- [Documentation de MedShakeEHR](https://www.logiciel-cabinet-medical.fr/documentation-technique/)

## Déploiement avec https
- Commencez par supprimer les fichiers du dossier cert `rm templates/cert/*`
- Rendez-vous dans le dossier cert `cd templates/cert`
- Tapez ces commandes :
```bash
domaine=msehr.local
openssl genrsa -out $domaine.key 4096
openssl req -new -key $domaine.key -out $domaine.csr
openssl x509 -req -days 3650 -in $domaine.csr -signkey $domaine.key -out $domaine.crt
```

- Au cours de la procédure plusieurs questions vous seront posées, voici un exemple de réponse :
    - Country Name (2 letter code) : `FR`
    - State or Province Name : «Votre Département ou Région » `Paris`
    - Locality Name : «Votre ville» `Paris`
    - Organization Name : «Votre Raison Sociale» `Cabinet Dr Strange`
    - Organization Unit Name :«Votre unit» `Direction`
    - Common Name (e.g. server FQDN or your name) : `msehr.local`
    - Email Address : «adresse mail du webmaster» `example@example.com`
    - A challenge password : «Mot de passe Certificat» : `supermotdepasselong`
    - An optional company name : 
- Une fois la machine virtuelle lancée, rendez-vous dans votre navigateur à l'adresse `https://55.55.55.5/install.php`

## Modifications de la configuration
- Pour arrêter la machine virtuelle taper `vagrant halt`.
- Pour détruire les fichiers de la machine virtuelle taper `vagrant destroy`.
- Vous pouvez modifier, les caractéristiques (ip, nombre de CPU, RAM, nom, distribution ...etc) de votre machine virtuelle dans `Vagrantfile`. Par exemple utiliser un `public network`
- Vous pouvez modifier l'approvisionnement de la machine virtuelle dans le fichier `main.yml`.
- Vous pouvez modifier la configuration d'Apache via les fichiers de configurations placés dans le dossier `templates`.
- Pour réapprovisionner la machine virtuelle avec les nouveaux paramètres taper `vagrant provision`.

MedShakeEHR est un projet crée par le Dr Bertrand Boutillier et rejoint par fr33z00, Abeldvlpr, indelog, gby. Merci à eux. [Dépôt du projet](https://github.com/MedShake/MedShakeEHR-base)