#Configuration et commandes GIT


##Configuration

###Git global setup

git config --global user.name "Thomas"
git config --global user.email "thomas.roueche@protonmail.com"
git config --global core.autocrlf input


##Commandes GIT

###Informations
GitHub : ThomasRoueche
Répertoire local ~/Documents/Code/
Clé GPG : keybase.io


###Créer un repo local
cd code/mon-repo
git init

###Cloner un repo local
cd code/mon-repo2
git clone code/mon-repo

###Create a new repository

git clone http://gitlab.example.com/TomRou/Homelab.git
cd Homelab
touch README.md
git add README.md
git commit -m "add README"
git push -u origin master

Existing folder or Git repository

cd existing_folder
git init
git remote add origin http://gitlab.example.com/TomRou/Homelab.git
git add .
git commit
git push -u origin master
