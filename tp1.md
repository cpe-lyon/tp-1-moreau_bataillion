# TP 1 - Installation d’Ubuntu Server et prise en main du shell  



## Exercice 2. Prise en main de l’interpréteur de commandes  
  

* Manuel  

**1. A l’aide du manuel, identifiez le rôle de la commande which**  

*which* localise une commande dans les dossiers et retourne le chemin de ficher pour accéder à la commande.

**2. Quand on consulte une page du manuel, comment peut-on rechercher un terme (par exemple, chercher
le terme option dans la page de manuel de which ?**  

Pour trouver un mot dans une page on utilise la commande */mot*.   
Pour rechercher option sur la page which on fait : *man which* suivit de */option*  

**3. Comment quitte-t-on le manuel ?**  

En utilisant la touche q.  

**4. Chaque section du manuel a une première page, qui présente le contenu de la section. Afficher la
première page de la section 6 ; de quoi parle cette section ?**  

Pour obtenir une brève introduction d'une section on utilise la commande *man 6 intro* avec ici la section numéro 6.  
La section  6  décrit tous les jeux et les programmes amusants disponibles sur le système.  




  
  



* Navigation dans l’arborescence des fichiers  


**1. allez dans le dossier /var/log**  

Nous sommes remontés à la racine en répétant la commande *cd ..* autant de fois que nécessaire.  
Puis nous avons utilisé : *cd var/log*  

**2. remontez dans le dossier parent (/var) en utilisant un chemin relatif**  

chemin absolu: chemin complet depuis la racine et commence par un /  
chemin relatif: par rapport à l'endroit où l'on se trouve actuellement  
Ici on utilise *cd ..* pour remonter au dossier parent. *..* symbolise le dossier parent, *.* symbolise le dossier courant.  

**3. retournez dans le dossier personnel**  

*cd ~*  

**4. revenez au dossier précédent (/var) sans utiliser de chemin**  

*cd -*  

**5. essayez d’accéder au dossier /root ; que se passe-t-il ?**  

Nous n'avons pas la permission d'accéder à ce dossier.  

**6. essayez la commande sudo cd /root ; que se passe-t-il ? Expliquez**  

Cela ne fonctionne pas : la commande *cd* est introuvable.  
Cela est dû au fait que cd est une commande bash interne et que sudo ne s'applique qu'à des programmes et pas à des commandes.  

**7. à partir de votre dossier personnel, créez l’arborescence suivante :**  

*cd ~  
mkdir -p Dossier1 Dossier2/{Dossier2.1,Dossier2.2}  
cd Dossier2/Dossier2.2  
touch Fichier2 Fichier3  
cd ../../Dossier1  
cd touch Fichier1*  

**8. revenez dans votre dossier personnel ; à l’aide de la commande rm, essayez de supprimer Fichier1, puis
Dossier1 ; que se passe-t-il ?**  

*cd ~  
rm Fichier1* Action impossible : il n'existe pas de fichier de ce nom à cet étage de l'arborescence.  
*rm Dossier1* Action impossible : la commande rm n'est utilisable que sur les fichiers, pas sur les dossiers.  

**9. quelle commande permet de supprimer un dossier ?**  

*rmdir Dossier2*  

**10. que se passe-t-il quand on applique cette commande à Dossier2 ?**  

Cela ne fonctionne pas :  en effet le Dossier2 n'est pas vide et cette commande est valable uniquement pour supprimer les dossiers vides.  

**11. comment supprimer en une seule commande Dossier2 et son contenu ?**  

*rm -r Dossier2* Le -r indique que la suppression est récursive : on parcourt le dossier et tous les sous dossiers pour supprimer chaque élément présent.  









* Commandes importantes  

**1. Quelle commande permet d’afficher l’heure ? A quoi sert la commande time ?**  

*date* affiche l'heure et le jour  
*time nom_commande* permet d'obtenir les statistiques relatives au temps d'exécution d'une commande pour les différents exécuteurs de commande.  

**2. Dans votre dossier personnel, tapez successivement les commandes ls puis la ; que peut-on en déduire
sur les fichiers commençant par un point ?**  

*ls* affiche les éléments présents dans le dossier courant.  
*la* affiche les éléments présents dans le dossier courant, y compris les éléments cachés, qui sont identifiés clairement en commençant par un point.  

**3. Où se situe le programme ls ?**  

On utilise la commande *which ls* et on obtient : */usr/bin/ls*  

**4. Essayez la commande ll. Existe-t-il une entrée de manuel pour cette commande ? Utilisez les commandes
alias ou alias pour en savoir plus sur la nature de cette commande.**  

Grâce à *ll* on obtient la liste des éléments du dossier courant détaillée avec notamment les droits d'accès en fonction des accesseurs.  
Il n'existe pas d'entrée pour cette commande : c'est en réalité la contraction de la commande répertoriée *ls -alF* comme nous l'indique la commande *alias ll*.  

**5. Quelle commande permet d’afficher les fichiers contenus dans le dossier /bin ?**  

*ls /bin*  

**6. Que fait la commande ls .. ?**  

*ls ..* nous affiche le contenu du dossier parent au dossier courant.  

**7. Quelle commande donne le chemin complet du dossier courant ?**  

*pwd* donne le chemin complet du dossier courant.  

**8. Que fait la commande echo 'yo' > plop exécutée 2 fois ?**  

*echo 'yo' > plop* crée un fichier plop dans le répertoire courant avec en contenu yo.  
Lorsque l'on répète cette opération, le 'yo' initial est écrasé par un nouveau 'yo' et donc le contenu du fichier ne change pas.  
Si l'on avait effectué la commande *echo 'ma' > plop, on aurait remplacé le 'yo' du fichier plop par le contenu 'ma'.  

**9. Que fait la commande echo 'yo' >> plop exécutée 2 fois ?**  

*echo 'yo' >> plop* crée un fichier plop dans le répertoire courant avec en contenu yo.  
Lorsque l'on répète cette opération, un nouveau 'yo' est ajouté au contenu du fichier plop à la suite du premier. Le fichier plop contient donc 2 lignes contenant respectivement: 'yo' et 'yo'. On ajoute un élément sans écraser le précédent rentré.  

**10. A quoi sert la commande file ? Essayez la sur des fichiers de types différents.**  

La commande *file nom_fichier* affiche le type du fichier donné en paramètre (txt, sh...).  

**11. Créez un fichier toto qui contient la chaîne Hello Toto ! ; créer ensuite un lien titi vers ce fichier
avec la commande ln toto titi. Modifiez à présent le contenu de toto et affichez le contenu de titi :
qu’observe-t-on ? Supprimez le fichier toto ; quelle conséquence cela a-t-il sur titi ?**  

*echo 'Hello Toto !' > toto* crée le fichier toto contenant la chaîne Hello Toto !.  
*ln toto titi* crée un fichier titi en lien physique avec toto : ils ont accès au même contenu hébergé au même emplacement mémoire.  
*echo 'Hello World !' >> toto* ajoute 'Hello World' dans le fichier toto, c'est à dire à l'emplacement mémoire dédié. Ainsi, lorsque l'on affiche le contenu de titi avec *cat titi*, on voit bien que le contenu de titi a également changé : c'est parce qu'il s'agit en réalité du même contenu pointé par deux noms de fichiers différents.  

Si l'on supprime fichier toto, titi continue à pointer vers le contenu de toto. Il existe un compteur qui compte le nombre d'accesseur possible d'un contenu (=le nombre de fichier qui ont accès à ce contenu = le nombre de copie); ce compteur est décrémenté à chaque fois qu'un fichier est supprimé :  on perd un accesseur. Ici, le compteur passe de 2 (pour toto et titi) à 1 (uniquement titi). Nous avons toujours accès au contenu malgré la suppression du fichier toto. Si l'on supprimait le fichier titi, nous n'aurions plus accès au contenu.  

**12. Créez à présent un lien symbolique tutu sur titi avec la commande ln -s titi tutu. Modifiez le
contenu de titi ; quelle conséquence pour tutu ? Et inversement ? Supprimez le fichier titi ; quelle
conséquence cela a-t-il sur tutu ?**  

*ln -s titi tutu* crée un fichier tutu lié symboliquement à titi.  
Si l'on modifie le contenu de titi, le contenu de tutu est également modifié. En effet, tutu contient un lien vers titi. Toute modification du contenu de titi entraine une modification de tutu : le lien de tutu pointe vers le titi modifié.  
Si l'on modifie le contenu de tutu, le contenu de titi est également modifié. Le lien de tutu pointant vers titi, on modifie en réalité directement le contenu de titi.  
Après suppression de titi, on ne peut plus accéder au fichier tutu. En effet, le lien de tutu pointant vers titi et titi n'existant plus, le lien est mort.  

**13. Affichez à l’écran le fichier /var/log/syslog. Quels raccourcis clavier permettent d’interrompre et
reprendre le défilement à l’écran ?**  

*cat /var/log/syslog* pour afficher le contenu du fichier  
CTRL + S : interrompt le défilement  
CTRL + Q : reprend le défilement  

**14. Affichez les 5 premières lignes du fichier /var/log/syslog, puis les 15 dernières, puis seulement les
lignes 10 à 20.**  

*head -5 /var/log/syslog* : affiche les 5 premières lignes de /var/log/syslog  
*tail -15 /var/log/syslog* : affiche les 15 dernières lignes de /var/log/syslog  
*head -n 20 /var/log/syslog | tail -n 11* : affiche les lignes 10 à 20 de /var/log/syslog (lignes 10 et 20 comprises)  
*head* sélectionne les 20 premières lignes qu'il passe par un pipe *|* à *tail* qui sélectionne les 10 dernières lignes de la sélection précédente. Finalement, on obtient les lignes 10 à 20.  

**15. Que fait la commande dmesg | less ?**  

*dmesg* affiche et contrôle le tampon des messages du noyau, l'ajout de *|less* permet d'afficher les informations page par page.  

**16. Affichez à l’écran le fichier /etc/passwd ; que contient-il ? Quelle commande permet d’afficher la page
de manuel de ce fichier ?**  

Le fichier */etc/passwd* contient les références des différents utilisateurs qui peuvent se connecter au système. On a accès à des informations sur chaque utilisateur : son login, l'identifiant de l'utilisateur et l'identifiant du groupe, un ensemble de valeurs décrivants l'utilisateur (nom, emplacement...), le chemin vers le répertoire personnel de l'utilisateur et le programme qui est lancé chaque fois que l'utilisateur se connecte au système.  
Avec la commande *man 5 passwd*, on accède à la section 5 du manuel et à la page sur passwd : on y découvre le format du fichier /etc/passwd, comme détaillé à la question précédente.  

**17. Affichez seulement la première colonne triée par ordre alphabétique inverse**  


*cut -d: -f1 /etc/passwd* affiche la première colonne de */etc/passwd*.  
On indique le symbole (ici :) qui délimite les colonnes (*-d:*) et on indique la colonne que l'on sélectionne dans le fichier (*-f1*). On obtient la liste des logins des utilisateurs de la machine.  
En ajoutant *| sort -d -r*, on trie cette colonne par ordre alphabétique (*-d*) inverse (*-r*).  
Finalement, on a : *cut -d: -f1 /etc/passwd | sort -dr*   

**18. Quelle commande nous donne le nombre d’utilisateurs ayant un compte sur cette machine (pas seulement
les utilisateurs connectés) ?**  

*lslogins* ???  

**19. Combien de pages de manuel comportent le mot-clé conversion dans leur description ?**  

*apropos conversion* ou *man -k conversion* listent toutes les pages où le mot conversion est présent dans le résumé.  
Ici, on en compte 4.  

**20. A l’aide de la commande find, recherchez tous les fichiers se nommant passwd présents sur la machine**  

On remonte à la racine de la machine et on utilise *find . -name "passwd"*  

**21. Modifiez la commande précédente pour que la liste des fichiers trouvés soit enregistrée dans le fichier
~/list_passwd_files.txt et que les erreurs soient redirigées vers le fichier spécial /dev/null**  

*find . -name "passwd" >~/list_passwd_files.txt 2>/dev/null*  
Il y a deux redirections ici :  
>~/list_passwd_files.txt : redirige le résultat de la commande (sauf les erreurs) dans le fichier list_passwd_files.txt  
>2>/dev/null : redirige les erreurs éventuelles dans le fichier /dev/null.  

**22. Dans votre dossier personnel, utilisez la commande grep pour chercher où est défini l’alias ll vu
précédemment**  

On utilise *$grep -r ll ./*. Ainsi on obtient toutes les correspondances à "ll" dans tous les fichiers présents au sein de notre dossier personnel (grâce à la récursivité de la recherche : -r). On obtient la correspondance suivante : dans ./.bashrc : alias ll='ls -alF'  

**23. Utilisez la commande locate pour trouver le fichier history.log.**  

On doit d'abord installer la commande locate avec *$sudo apt install mlocate*.  
Ainsi, avec *$locate history.log*, on obtient : /var/log/apt/history.log  

**24. Créer un fichier dans votre dossier personnel puis utilisez locate pour le trouver. Apparaît-il ? Pourquoi ?**  

On a créé un fichier dans notre dossier personnel grâce à *$touch Fichier*. En utilisant *$locate Fichier*, on n'obtient aucun résultat.  
En effet, le fichier Fichier vient d'être créé, il n'a pas encore été répertorié dans la base de données de la machine. La commande locate ne peut donc pas le détecter : elle ne lit pas le disque dur entier, seulement cette base de données.  
Une fois par jour, le système met à jour la base de données. On peut forcer la mise à jour avec *$sudo updatedb*. Ainsi, on peut trouver le fichier Fichier.  






## Exercice 3. Découverte de l’éditeur de texte nano  

**1. Copiez le fichier /var/log/syslog dans votre dossier personnel sous le nom log.txt, puis ouvrez-le avec
nano**  

*$cp /var/log/syslog ~/log.txt* pour copier le fichier  
*$nano log.txt* pour ouvrir le fichier grâce à nano  

**2. Remplacez toutes les occurrences du mot kernel par le mot noyau**  

On effectue un CTRL + | pou ouvrir la zone d'entrée. On entre d'abord le terme 'kernel' à remplacer, puis le terme 'noyau' en remplacement. On sélectionne 'A' pour remplacer toutes les occurences de kernel du fichier.  

**3. Déplacer les 10 premières lignes à la fin du fichier**  

Se placer grâce aux flèches au début du fichier (ou grâce à CTRL + début). Faire Alt + A pour démarrer la sélection et sélectionner les lignes à déplacer grâce aux flèches. Faire CTRL + K pour couper la sélection. Se déplacer à la fin du fichier grâce à CTRL + Fin. Coller la sélection des 10 lignes grâce à CTRL + U.  

**4. Annulez cette action**  

On annule une action grâce à Alt + U. On doit répéter cette action 2 fois : pour coller et couper.  

**5. Enregistrez le fichier avant de quitter nano**  

On enregistre grâce à CTRL + S.  
On quitte grâce à CTRL + X.  














## Exercice 4. Personnalisation du shell  

Le shell par défaut est plutôt austère, mais il existe de nombreux moyens de le personnaliser, en modifiant
le fichier ~/.bashrc.  

**1. Commencez par créer une copie de ce fichier, que vous appellerez .bashrc_bak**  

*$cp ~/.bashrc ~/.bashrc_bak*  

**2. Editez le fichier .bashrc avec nano et décommentez la ligne force_color_prompt=yes pour activer
la couleur. Enregistrez le fichier et quittez nano.**  

*$nano .bashrc*  
On fait CTRL + W pour trouver la ligne force_color_prompt=yes  
On l'active en retirant le # en début de ligne.  
On enregistre grâce à CTRL + S et on quitte grâce à CTRL + X.  

**3. Le fichier .bashrc est lu au démarrage du shell ; pour le recharger, il faudrait donc se déconnecter
puis se reconnecter ; mais il existe un autre moyen : la commande source .bashrc. Testez-la, l’invite
de commande devrait immédiatement passer en couleurs.**  

*$source .bashrc* passe le terminal en couleur.  



**4. Modifiez l’invite de commande pour qu’elle s’aﬀiche sous la forme suivante :[heure]-user@host:chemin_courant$ où l’heure est aﬀichée en violet et entre crochets, et le chemin du dossier courant en cyan**  


Pour faire l’heure entourée par des crochets en rouge : *\[033[01;31m\]\[[\A]\]:*  
Pour faire le chemin en cyan : *\[\033[01;96m\]\w*  
Ne pas oublier d’actualiser avec *$source .bashrc*  























NOTES:  

-Fichier original stocké dans la mémoire à une adresse connue. Inode  
-Fichier en lien physique : le contenu est stocké au même endroit que le fichier original : c'est le même contenu. Si l'on supprime fichier original, fichier_physique continu à stocker le contenu d'original et à toujours accès à ce contenu. Il existe un compteur qui compte le nombre d'accesseur possible d'un contenu (=le nombre de fichier qui ont accès à ce contenu = le nombre de copie); ce compteur est décrémenté à chaque fois qu'un fichier est supprimé :  on perd un accesseur.  
-Fichier en lien symbolique : contient un lien vers le fichier original. Si le fichier original est détruit, le lien est mort et le fichier_symbolique n'a plus accès au contenu.  

le nom d'un fichier n'est pas enregistré au même endroit que son contenu  

