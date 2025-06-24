# 📚 Trucs & Astuces CMD – Technicien Support & Réseau

Bienvenue dans ce guide complet sur les commandes essentielles de l’invite de commandes Windows (CMD) pour les techniciens support et réseau.  
Ici, vous trouverez des commandes pratiques, avancées, ainsi que des astuces pour diagnostiquer, dépanner et maintenir les postes et réseaux informatiques sous Windows.

---

## Sommaire

1. [Diagnostic réseau](#1-diagnostic-réseau)  
2. [Partage & gestion réseau](#2-partage--gestion-réseau)  
3. [Assistance utilisateur](#3-assistance-utilisateur)  
4. [Gestion et dépannage système](#4-gestion-et-dépannage-système)  
5. [Utilisateurs & mots de passe](#5-utilisateurs--mots-de-passe)  
6. [Astuces pratiques](#6-astuces-pratiques)  
7. [Gestion avancée des disques (DISKPART)](#7-gestion-avancée-des-disques-diskpart)  
8. [Démarrage et services (MSCONFIG, BOOTREC)](#8-démarrage-et-services-msconfig-bootrec)  
9. [Surveillance & sécurité](#9-surveillance--sécurité)  
10. [Inventaire & maintenance](#10-inventaire--maintenance)  
11. [Audit & journalisation](#11-audit--journalisation)  
12. [Groupes, fichiers & accès réseau](#12-groupes-fichiers--accès-réseau)  
13. [Divers & bonus](#13-divers--bonus)  
14. [Exemple de script de dépannage réseau](#14-exemple-de-script-de-dépannage-réseau)  

---

## 1. Diagnostic réseau

- **Vérifier l’adresse IP**
  - `ipconfig /all`  
    Détaille toutes les interfaces réseau (IP, masque, passerelle, DNS, MAC...)

- **Renouveler l’adresse IP**
  - `ipconfig /release`
  - `ipconfig /renew`

- **Vider le cache DNS**
  - `ipconfig /flushdns`

- **Tester la connexion à un hôte**
  - `ping adresse`
    - Ex : `ping 8.8.8.8` ou `ping google.com`

- **Tracer la route vers un hôte**
  - `tracert adresse`
    - Ex : `tracert google.com`

- **Afficher les ports ouverts et connexions**
  - `netstat -an`

- **Afficher la table ARP**
  - `arp -a`

- **Afficher la table de routage**
  - `route print`

---

## 2. Partage & gestion réseau

- **Afficher les partages réseau**
  - `net share`

- **Afficher les ressources connectées**
  - `net use`

- **Connecter un lecteur réseau**
  - `net use X: \\serveur\partage`

- **Déconnecter un lecteur réseau**
  - `net use X: /delete`

- **Rechercher un PC sur le réseau**
  - `net view \\nom_pc` (voir partages)
  - `net view` (voir les PC du réseau)

---

## 3. Assistance utilisateur

- **Lister les sessions**
  - `query user`

- **Fermer la session d’un utilisateur**
  - `logoff ID`

- **Gestion des tâches/processus**
  - `tasklist` (affiche tous les processus)
  - `taskkill /IM nom_processus.exe /F`
    - Ex : `taskkill /IM notepad.exe /F`

---

## 4. Gestion et dépannage système

- **Vérification des fichiers système**
  - `sfc /scannow`

- **Vérifier l’intégrité du disque**
  - `chkdsk C: /F /R`

- **Redémarrer ou arrêter le PC**
  - `shutdown /r /t 0` (redémarrer)
  - `shutdown /s /t 0` (éteindre)

- **Ouvrir le gestionnaire de périphériques**
  - `devmgmt.msc`

- **Ouvrir la gestion des services**
  - `services.msc`

---

## 5. Utilisateurs & mots de passe

- **Lister les utilisateurs**
  - `net user`

- **Créer un utilisateur**
  - `net user nom password /add`

- **Modifier un mot de passe**
  - `net user nom nouveau_pass`

- **Ajouter un utilisateur à un groupe**
  - `net localgroup Administrateurs nom /add`

---

## 6. Astuces pratiques

- **Effacer l’écran**
  - `cls`

- **Obtenir de l’aide**
  - `help commande` ou `commande /?`
    - Ex : `net /?`

- **Rediriger la sortie vers un fichier**
  - `ipconfig /all > reseau.txt`

---

## 7. Gestion avancée des disques (DISKPART)

- **Lancer l’outil DiskPart**
  - `diskpart`

- **Lister les disques**
  - `list disk` (dans DiskPart)

- **Lister les volumes**
  - `list volume` (dans DiskPart)

- **Sélectionner un disque**
  - `select disk N` (N = numéro du disque)

- **Créer une partition**
  - `create partition primary`

- **Formater une partition**
  - `format fs=ntfs quick`

- **Attribuer une lettre à un volume**
  - `assign letter=Z`

- **Supprimer une partition**
  - `delete partition`

> ⚠️ **Attention :** Utiliser DiskPart avec précaution, car la suppression/formattage est irréversible.

---

## 8. Démarrage et services (MSCONFIG, BOOTREC)

- **Ouvrir la configuration du démarrage**
  - `msconfig`

- **Récupération du démarrage Windows**
  - (à lancer depuis l’environnement de récupération WinRE)
    - `bootrec /fixmbr`
    - `bootrec /fixboot`
    - `bootrec /scanos`
    - `bootrec /rebuildbcd`

---

## 9. Surveillance & sécurité

- **Afficher les connexions réseau actives avec le PID**
  - `netstat -ano`

- **Lister les ports d’écoute**
  - `netstat -ab`

- **Lister les services en cours**
  - `sc query`

- **Arrêter, démarrer, redémarrer un service**
  - `net stop nom_service`
  - `net start nom_service`

- **Voir les connexions réseau partagées (admin)**
  - `net session`

---

## 10. Inventaire & maintenance

- **Afficher les infos matérielles et système**
  - `systeminfo`
  - `wmic cpu get name`
  - `wmic memorychip get capacity`
  - `wmic diskdrive get model,size`

- **Lister les drivers**
  - `driverquery`

- **Vérifier la version de Windows**
  - `winver`
  - `ver`

- **Lister les applications installées**
  - `wmic product get name,version`

- **Lister les mises à jour Windows**
  - `wmic qfe list`

---

## 11. Audit & journalisation

- **Ouvrir l’observateur d’événements**
  - `eventvwr.msc`

- **Afficher les 10 derniers logs Système en ligne de commande**
  - `wevtutil qe System /c:10 /f:text`

---

## 12. Groupes, fichiers & accès réseau

- **Lister les groupes locaux**
  - `net localgroup`

- **Voir les membres d’un groupe**
  - `net localgroup Administrateurs`

- **Vérifier les fichiers ouverts sur le réseau**
  - `openfiles /query`
    - (Activer le suivi local : `openfiles /local on` puis redémarrer)

---

## 13. Divers & bonus

- **Planifier une tâche**
  - `schtasks /create /sc once /tn "NomTâche" /tr "commande" /st 12:00`

- **Connexion à distance PowerShell**
  - `Enter-PSSession -ComputerName NOM_PC`

- **Lancer cmd en administrateur via script**
  - `powershell Start-Process cmd -Verb runAs`

---

## 14. Exemple de script de dépannage réseau

```bat
@echo off
echo Diagnostic IP...
ipconfig /all
echo Test de connexion Google...
ping 8.8.8.8
echo Vidage du cache DNS...
ipconfig /flushdns
pause
```

---

## 🚩 Conseils

- Sauvegardez vos commandes utiles dans des fichiers batch (`.bat`) pour les réutiliser facilement.
- Utilisez la touche **Tab** pour l’auto-complétion et **flèche ↑** pour rappeler vos commandes précédentes.
- N’hésitez pas à consulter l’aide intégrée à chaque commande avec `/h` ou `/?`.

---

**Besoin d’une commande avancée, d’un script ou d’un cas concret ? Ouvrez une issue ou une discussion !**
