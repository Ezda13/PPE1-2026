# journal de bord du projet encadré

## Séance de [23 esptembre : git et manipulation de fichiers 

-Création de mon dépot PPE1-2026 sur GitHub et clonage en SSH

-Création du journal de bord directement sur GitHub

-Syncronisation : : 'git fetch' + 'git status' pour voir le retard, 'git pull'pour le rattraper

-Problème rencontré : J'avais cloné le débôt du cours une deuxième fois à l'intérieur de lui mếme -> supprimé le doublon

**Échec du `git push` :** j'avais cloné mon dépôt avec l'adresse HTTPS, et GitHub refusait l'authentification par mot de passe (*Password authentication is not supported*). Solution :
vérifier que j'avais déjà une clé SSH avec `ls ~/.ssh` ;
tester la connexion avec `ssh -T git@github.com` (il faut taper la phrase de passe de la clé) ;
changer l'adresse du dépôt avec `git remote set-url origin git@github.com:Ezda13/PPE1-2026.git`.

**Fichiers cachés :** le `.gitignore` n'apparaît pas avec `ls` car son nom commence par un point. Il faut utiliser `ls -a` pour l'afficher.

**Tags :** `git push` n'envoie pas les tags, il faut les pousser avec `git push origin <nom-du-tag>`.



## Séance du 30 septembre : les pipelines

### Ce que j'ai fait

- Décompression de l'archive des données avec `unzip archive-17.zip -d donnees`, dans un dossier à part (hors des dépôts git)
- Comptage des annotations par année avec `cat` et `wc -l`
- Comptage des lieux uniquement en ajoutant `grep Location`
- Écriture des résultats dans des fichiers avec `echo`, `>` et `>>`
- Classement des 15 lieux les plus cités, par année puis pour un mois, avec `cut -f3 | sort | uniq -c | sort -n | tail -15`

### Solutions que je veux partager

- `>` écrase le fichier, `>>` ajoute à la fin : il faut utiliser `>` seulement pour la première ligne.
- Il faut faire `sort` **avant** `uniq -c`, car `uniq` ne fusionne que les lignes identiques qui se suivent.
- Le `?` remplace un seul caractère : `????_03_*.ann` prend tous les fichiers de mars, quelle que soit l'année.
- Erreur rencontrée : j'avais oublié le `grep Location` pour 2017 et 2018 dans `locations.txt`, les nombres étaient les mêmes que dans `comptes.txt`. J'ai refait le fichier.

### Questions à discuter

- Le même lieu peut être compté plusieurs fois sous des écritures différentes (`Abou Dhabi` et `Abu Dhabi`, `18e arrondissement` et `18 e arrondissement`). Comment les regrouper ?
