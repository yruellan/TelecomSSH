# TelecomSSH

Tutoriel sur la configuration ssh pour se connecter aux ordi de Telecom Paris.

## IMPORTANT : WIFI

Vous devez etre connecter au wifi "Campus-Telecom" pour pouvoir etablir une connexion ssh.

Vous pouvez aussi utiliser un VPN ([tuto](https://eole.telecom-paris.fr/vos-services/services-numeriques/connexions-aux-reseaux#exterieur)).

## Configuration ssh

Ouvrer un terminal et taper :
```sh
cd ~
touch telecom_ssh_config.sh
chmod u+x telecom_ssh_config.sh
nano telecom_ssh_config.sh
```
Puis :
- Copier coller le fichier suivant
  ```sh
  email="yann.ruellan@telecom-paris.fr"
  user="yruellan-24"
  host="tp-1a201-10"
  
  mkdir ~/.ssh
  
  ssh-keygen -t rsa -C $email -q -N "" -f ~/.ssh/telecom
  
  ssh-copy-id -i ~/.ssh/telecom user@host
  
  touch ~/.ssh/config
  echo "Host telecom" >> ~/.ssh/config
  echo "  User $user" >> ~/.ssh/config
  echo "  HostName $host" >> ~/.ssh/config
  echo "  IdentityFile ~/.ssh/telecom" >> ~/.ssh/config
  echo "" >> ~/.ssh/config
  ```
- Modifier email, user et host (**modifiable seulement au clavier**)
- Controle + O (sauvegarde le fichier)
- Entrer
- Controle + X (quitte nano)
- Taper `./telecom_ssh_config.sh`
- Entrer le mot de passe Telecom Paris / Synapse
- Taper `rm telecom_ssh_config.sh`


### Etablir la connection : `ssh telecom`

### Arret de la connexion : `exit`

## Utilisation avec Visual Studio Code


### Pour Unix (Linux et MacOS)
- Ouvrer VS Code
- Appuyer sur le bouton vert en bas a gauche
- Selectionner l'option 'Connect to host' ou 'ssh'
- Selectionner l'option 'telecom'

### Pour Windows (avec WSL)

- Ouvrer l'explorateur de fichier
- Aller dans le dossier Utilisateur (ou User)
- Aller dans le dossier votre_utilisateur
- Copier le dossier .ssh
- Aller sur votre dossier utilisateur Windows
- Coller le dossier .ssh
- Suivre la procédure Unix

## Configuration X11

### MacOS

## Installation LOGISIM

Il faut être connecter en ssh avec X11 activé

### Telechargement
```sh
wget https://inf107.telecom-paris.fr/exercises/part-1/files/td-logisim.tar.gz
tar xzf td-logisim.tar.gz
```

### Lancement de l'application
```sh
cd ~/td-logisim/mux
make
```
