#Commandes pour DiskUtil

##Créer un ramdisk
diskutil erasevolume HFS+ 'RAM Disk' `hdiutil attach -nomount ram://102400`

formule = taille souhaité en Mo * 2048 = le nombre à placé dans la commande hdiutil.
