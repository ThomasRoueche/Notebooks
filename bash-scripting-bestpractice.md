#Best practice pour l'écriture de script bash

##bash ou sh ?
Pour être portable ==> /bin/sh
pour utiliser bash si besoin ==> attention bash n'est pas forcement dans /bin suivant les distributions
/usr/bin/env bash
Avantages :
 - Utilise le PATH pour trouver le premier binaire bash

Inconvénients :
 - Il utilise le premier executable qui porte le nom. si plusieurs versions sont présentes sur le système alors ce n'est pas forcement la bonne qui est utilisé (voir l'usage de brew lorsque macos possède un vieux binaire)
 - empêche de passer des arguments
 - cron peut réduire le path donc la commande env pourra ne pas être trouvée
 - empêche de trouver le script avec ps|grep ou ps -C

##Strict mode bash
#!/bin/bash
set -euo pipefail
IFS=$'\n\t

##Mettre une fonction de nettoyage
function finish {
  blablabla
}
trap finish EXIT

##Divers

Utiliser les noms longs pour les options car plus lisible 

Au lieu de : if [ $NAME = "Kevin" ]
mettre : if [ "${NAME:-}" = "Kevin" ]
permet de se protéger des syntax error renvoyé par une var non déclarée.
permet de tester l'existance d'une var et le cas échéant de la mettre à ""


##Références
https://unix.stackexchange.com/questions/240749/bash-script-best-practice#240755
https://stackoverflow.com/questions/21612980/why-is-usr-bin-env-bash-superior-to-bin-bash
https://unix.stackexchange.com/questions/29608/why-is-it-better-to-use-usr-bin-env-name-instead-of-path-to-name-as-my
https://www.in-ulm.de/~mascheck/various/shebang/#splitting
http://kvz.io/blog/2013/11/21/bash-best-practices/
http://redsymbol.net/articles/unofficial-bash-strict-mode/
https://stackoverflow.com/questions/78497/design-patterns-or-best-practices-for-shell-scripts
https://fahdshariff.blogspot.fr/2013/10/shell-scripting-best-practices.html

