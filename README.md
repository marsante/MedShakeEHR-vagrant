# MedShakeEHR-vagrant
### Un fichier Vagrant pour déployer rapidement un environnement de développement approvisionné par Ansible pour MedShakeEHR 

## Prérequis
- Avoir [VirtualBox](https://www.virtualbox.org/wiki/Downloads), [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) et [Vagrant](https://www.vagrantup.com/docs/installation) de configuré sur votre machine :
- Crée dans un but de démo ou de développement, ne pas utiliser en production avec des données réelles sans ajouter des paramètres de sécurité (mot de passe fort, pare-feu, https, contrôle d'accès).

## Installation 
- cloner le projet.
- créer un fichier `secrets.yml` à la racine du projet pour personnaliser les noms et mots de passes de la base de données comme dans l'exemple :

```yml
---
root_password: motdepasseroot
admin_account: nomdecompteadmin
admin_password: motdepasseadmin
```

- ouvrir un terminal à la racine du projet.
- taper la commande suivante `vagrant up`.
- A la fin de l'exécution de la commande, ouvrir le navigateur se rendre à l'adresse suivante `http://55.55.55.5`.
- Vous pouvez finir la configuration de MedShakeEHR.
- le nom d'utilisateur et le mot de passe root qui vous seront demandé est en fait le nom et mot de passe que vous avez rempli pour les variables `admin_account:` `admin_password:`
- [Documentation de MedShakeEHR](https://www.logiciel-cabinet-medical.fr/documentation-technique/)
## Modifications de la configuration
- Pour arrêter la machine virtuelle taper `vagrant halt`.
- Pour détruire les fichiers de la machine virtuelle taper `vagrant destroy`.
- Vous pouvez modifier, les caractérisitques (ip, nombre de CPU, RAM, nom, distribution ...etc) de votre machine virtuelle dans `Vagrantfile`.
- Vous pouvez modifier l'approvisionnement de la machine virtuelle dans le fichier `main.yml`.
- Vous pouvez modifier la configuration d'Apache et de PHP via les fichiers de configurations placés dans le dossier `templates`.
- Pour réapprovisionner la machine virtuelle avec les nouveaux paramètres taper `vagrant provision`.

Pour rappel MedShakeEHR est un projet crée par le Dr Bertrand Boutillieret et rejoint par fr33z00, Abeldvlpr, indelog, gby. Merci à eux. [Dépôt du projet](https://github.com/MedShake/MedShakeEHR-base)