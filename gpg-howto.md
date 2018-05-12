#Configuration de gpg avec Github

##Configuration

Prérequis : avoir un compte keybase.io avec une clé gpg dedans

Importer votre clé public dans le ring gnupg local
curl https://keybase.io/<your-username>/key.asc | gpg --import

Importer votre clé privée dans le ring gnupg
 - créer un ramdisk afin de pouvoir y stocker votre clé privé temporairement
sur l'interface de keybase web cliquez sur edit en face de la clé gph et choissisez l'option "export my private key from keybase"
copiez le contenu du pop-up et collez le dans un fichier keybase-private.key
gpg --allow-secret-key-import --import keybase-private.key

prenez l'ID de votre clé
 - soit au niveau de keybase web
 - soit via gpg --list-keys, les 8 derniers chiffres

copiez votre clé public dans la page de configuration gpg de votre compte github

## configurer git en local
git config --global commit.gpgsign true
git config --global user.signingkey <key-id>
Préciser à git quelle commande utiliser pour signer avec gnupg
git config --global gpg.program gpg2

##Références
https://meedamian.com/post/keybase-signed-github/
la page de doc accessible depuis la page de conf gpg de votre compte github


#Installation des outils sur le système

Installation de gnupg2. par défaut sur macos 10.11 la version et 2.1.7
brew install gpg2

Configuration : ajouter dans .bashrc ou .bash_profile
GPG_TTY=$(tty)
export GPG_TTY
ou export GPG_TTY=$(tty)

brew install pinentry-mac
echo "pinentry-program /usr/local/bin/pinentry-mac" >> ~/.gnupg/gpg-agent.conf
killall gpg-agent

#Commandes de test

Vous pouvez avoir plusieurs commandes gpg, vérifier le bon fonctionnement
echo "test" | gpg2 --clearsign
si besoin essayer avec la commande gpg aussi
vérifier l'existance d'une clé
gpg2 -K --keyid-format SHORT

#Commandes classiques

##Créer une clé
gpg2 --gen-key


##Références
https://github.com/Homebrew/homebrew-core/issues/14737
