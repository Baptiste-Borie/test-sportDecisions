# test-technique

### Comment lancer :

```
npm install
npm run serve
```

cliquer sur le lien après la mise en place du serveur

### Attention ! : Sur le dépot github il y a 2 contributeurs.

Cela correspond à mes deux comptes github je me suis rendu compte, au milieu du projet que quand je pushais cela le faisait depuis le mauvais compte. Vous pourrez voir dans l'historique des commit que je me suis un peu battu avec git. Pour au final me rendre compte que j'avais inversé les emails correspondant à chaque compte ...

### Architecture du projet

```
> src
    | assets
    # C'est ici que sont mis les outils tel que les images ou les svg

    | components
    # Ici on retrouvera tous les composants de notre site web

    |constant
    # Ce fichier n'étais sans doute pas nécessaire, cependant je voulais un code propre.
    # Ici serait donc stockés l'ensemble des constantes.

    |store
    # C'est ici que sont stockés les données bruts de l'applications
```

### Bonus :

- Les chevrons de l'entête de colonne disparaissent au dessus de 768px
- Les chevrons de l'entête de colonne disparaissent quand on est au début/à la fin de la liste -> ex : si il n'y a plus d'élément après on ne peut pas scroll à droite.
- Effet de hover sur les lignes
- Si on clique sur l'entete "END OF CONTRACT" on change l'ordre de tri des infos

### Mon expérience :

La principale difficulté pour moi dans la réalisation de ce projet était la découverte de Vue.js & Bootstrap.
J'ai passé la soirée,suite à notre entretien, à lire la documentation afin de me familiariser avec ce framework et cette librairie. J'ai y découvert 4 choses dont je savais que j'allais me servir : "v-for" & "v-if" qui correspondent à de l'affichage dynamique et conditionnel. "mounted" qui correspond à un hook react nommé "useEffect". Enfin j'ai découvert que bootstrap avait un système de grille très poussé.

Ainsi dès le lendemain, j'ai débuté ce projet. Je n'ai pas rencontré de difficulté particulière durant le projet. Même si je doute d'avoir choisi la méthode la plus simple pour arriver à ce résultat, je suis tout de même heureux du résultat final. J'ai pu réalisé un nombre de bonus honorable, et j'approche grandement du rendu fourni par l'UI/UX designer.

J'ai pu graçe à ce projet découvrir un nouveau framework qui m'intéressait depuis longtemps. Je pense appronfondir mes recherches sur Vue.js afin de mieux percevoir les avantages de ce framework. Enfin j'ai pu découvrir bootstrap, cela m'as donné grandement de le réutiliser dans d'autre projet.

### Bug connu:

En mode mobile le tri ascendant/descendant à bien était desactivté, mais le curseur reste en pointer alors qu'il devrait passer en default quand je n'affiche pas la colonne "END OF CONTRACTS".
