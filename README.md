# TelecomSSH
Tutoriel sur la configuration ssh pour se connecter en ssh au ordi de Telecom Paris pour Unix (Macos, Linux).

## IMPORTANT : WIFI

Vous devez etre connecter au wifi "Campus-Telecom" pour pouvoir etablir une connexion ssh.

Vous pouvez aussi utiliser un VPN ([tuto](https://eole.telecom-paris.fr/vos-services/services-numeriques/connexions-aux-reseaux#exterieur)).

## Instruction

Ouvrer un terminal et taper :
```sh
cd ~
touch telecom_ssh_config.sh
chmod u+x telecom_ssh_config.sh
nano telecom_ssh_config.sh
```
Puis :
- Copier coller le fichier telecom_ssh_config.sh (disponible ci-dessous)
- Modifier email, user et host (modifiable seulement au clavier)
- Controle + O (sauvegarde le fichier)
- Entrer
- Controle + X (quitte nano)
- Taper `./telecom_ssh_config.sh`
- Entrer le mot de passe Telecom Paris / Synapse
- Taper `rm telecom_ssh_config.sh`


### Etablir la connection : `ssh telecom`

### Arret de la connexion : `exit`


## telecom_ssh_config.sh :
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

