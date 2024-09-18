# TelecomSSH

Tutoriel sur la configuration ssh pour se connecter aux ordi de Telecom Paris.

## IMPORTANT : WIFI

Vous devez etre connecter au wifi "Campus-Telecom" pour pouvoir etablir une connexion ssh.

Vous pouvez aussi utiliser un VPN ([tuto](https://eole.telecom-paris.fr/vos-services/services-numeriques/connexions-aux-reseaux#exterieur)).

## Configuration ssh

- Ouvrer un terminal
- Taper :
```sh
mkdir ~/.ssh
touch ~/.ssh/config

function new_config(){

  cd ~
  key=".ssh/my_key_of_test"
  
  ssh-keygen -t rsa -C $1 -q -N "" -f $key
  
  ssh-copy-id -i $key $2@$3
  
  echo "Host telecom" >> ~/.ssh/config
  echo "  User $2" >> ~/.ssh/config
  echo "  HostName $3" >> ~/.ssh/config
  echo "  IdentityFile ~/$key" >> ~/.ssh/config
  echo " " >> ~/.ssh/config
}
```
- Taper `new_config "yann.ruellan@telecom-paris.fr" "yruellan-24" "tp-1a201-10"` en modifiant votre email et votre identifiant
  Vous pouvez aussi modifier le numéro du poste. Voici la liste des [postes](https://tp.telecom-paris.fr/).
- Entrer le mot de passe Telecom Paris / Synapse
- La connexion ssh est configurée 

## Utilisation de ssh

Etablir la connection : `ssh telecom`
Arret de la connexion : `exit`

## Utilisation de ssh avec Visual Studio Code

Vous pouvez vous connectez en ssh au serveur avec VS Code sans utiliser de terminal.

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

X11 permet d'avoir un retour vidéo de la connexion ssh.

### MacOS

https://www.cyberciti.biz/faq/apple-osx-mountain-lion-mavericks-install-xquartz-server/

### Linux - WSL

Voir sur internet. Tutoriel à venir...

## Installation LOGISIM

Il faut être connecté en ssh avec X11 activé.

### Téléchargement
```sh
wget https://inf107.telecom-paris.fr/exercises/part-1/files/td-logisim.tar.gz
tar xzf td-logisim.tar.gz
```

### Lancement de l'application
```sh
cd ~/td-logisim/mux
make
```

## Synchronisation via SSHFS

SSHFS permet de vous connecter au serveur comme si c'était une clé USB.

### MacOS

Tutoriel sur https://www.petergirnus.com/blog/how-to-use-sshfs-on-macos.

### Linux - WSL

Voir sur internet. Tutoriel à venir...

### Utilisation

Monter le server : `sshfs user@post:directory ~/mount_dir -o IdentityFile=key_dir`

Déconnexion : ` diskutil umount force ~/mount_dir`
