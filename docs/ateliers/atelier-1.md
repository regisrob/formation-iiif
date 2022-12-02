# Atelier 1 : créer un Manifeste avec le Manifest Editor

Le IIIF Manifest Editor est une application Web pour éditer des Manifestes développée par Bodleian Libraries (Oxford) et text & bytes LLC.

Accéder au Manifest Editor : [https://digital.bodleian.ox.ac.uk/manifest-editor](https://digital.bodleian.ox.ac.uk/manifest-editor)

!!! tip "Consignes"

    Dans cet exercice nous allons créer un nouveau Manifest à partir de plusieurs Manifestes. Vous pouvez utiliser ceux sélectionnés à l'exercice précédent.

    1. **Créer un nouveau Manifeste et importer des images** :
        - cliquer sur `New Manifest`
        - dans le panneau à droite, aller sur `Manifest Actions` > `Import Canvases`
        - cliquer ensuite sur le bouton `Open Sequence`, puis copier-coller une URL de Manifeste dans le champ "Enter a remote Manifest URL", puis cliquer sur `Open`. Une vue zoomable de l'objet devrait s'ouvrir dans la fenêtre à gauche.
        - répéter ces actions pour chaque Manifeste choisi.

    2. **Composer/éditer la séquence de votre Manifeste :**

        - Une fois vos Manifestes chargés dans l'éditeur, vous pouvez glisser-déposer une à une les images de votre choix dans la partie inférieure de la page (dans l'espace horizontal blanc avec l'indication `+ Add Canvas`) :
            - pour cela, survoler la partie inférieure d'une image, un bandeau avec des vignettes devrait apparaître.
            - glisser-déposer la vignette de votre choix dans le bandeau inférieue (au niveau de `Add Canvas`)
            - répéter l'opération pour chaque image que vous souhaitez incorporer dans votre Manifeste.
        - vous pouvez réordonner la séquence d'images en faisant glisser chaque Canevas, vous pouvez aussi dupliquer ou supprimer un *Canevas*
        - en cliquant sur un Canvevas, on active le panneau `Canvas Metadata` à droite qui permet de modifier les métadonnées du Canevas ou d'en renseigner de nouvelles

    3. **Éditer les métadonnées de votre Manifeste :**

        - Une fois votre séquence faite, cliquer sur `Return to Edit Manifest` dans le panneau à droite
        - Dans ce même panneau latéral, vous pouvez éditer les métadonnées de votre Manifeste dans la section `Manifest Metadata` : 
            - éditer les champs pré-existants du Manifeste d'origine, ou ajouter un nouveau champ en cliquant sur `Add metadata field` : renseigner au moins le `label` et la `description`.

    4. **Sauvegarder votre Manifeste :**

        - Dans le panneau latéral, cliquer sur `Save Manifest` puis `Download Manifest`.
        - Un document `manifest.json` devrait avoir été téléchargé sur votre ordinateur

    5. **Publier le Manifest sur le Web :**

        - Pour pouvoir utiliser un Manifeste dans une application, il faut pouvoir le rendre accessible à travers une URL, et donc le déposer quelque part sur un serveur Web. Pour cela, deux options s'offrent à nous :

            1. **Option A** : Si vous disposez d'un compte Github (sinon, n'hésitez pas à en créer un !), vous pouvez utiliser le **[IIIF Workbench](https://workbench.gdmrdigital.com)** :
                - une fois connecté, vous pouvez charger votre fichier "manifest.json" via l'onglet `Manifests` : celui-ci sera alors déposé automatiquement sur Github et se verra ainsi attribué une URL
                - une fois le chargement effectué, les informations de votre Manifeste devraient apparaître sur la page
                - ensuite cliquer sur le logo IIIF pour ouvrir le Manifeste. On constate qu'il est désormais accessible à une URL *.github.io.
                - copier cette URL et coller là dans le pad ou dans un fichier texte
                - si besoin vous pouvez continuer à éditer le Manifeste à la main directement via Github : pour cela, cliquer sur le 2e bouton `Edit manifest in Github`
                - copier aussi l'URL pour éditer le Manifest sur Github et coller là dans le pad, nous en aurons besoin plus loin

            2. **Option B** : Si vous ne souhaitez pas créer de compte Github, vous pouvez utiliser un service de stockage en ligne de documents JSON : **[n:point](https://www.npoint.io)** La pérennité du service n'est en aucun cas garantie mais cela suffit amplement pour l'exercice.
                - tout d'abord, retourner dans vos fichiers sur votre ordinateur, ouvrir votre `manifest.json` et copier-coller tout le contenu JSON (Ctrl+A puis Ctrl+C)
                - revenir sur le site n:point et cliquer sur `Create JSON Bin`
                - supprimer le JSON présent par défaut dans la fenêtre et collez le contenu de votre Manifeste (Ctrl+V)
                - cliquer ensuite sur `Save` pour sauvegarder les données
                - puis cliquer sur `Share`, une fenêtre modale devrait s'ouvrir au milieu de l'écran.
                - copier la première URL (celle juste en dessous de `Access this bin via the API at:`). Vous pouvez la coller dans le pad ou dans un fichier texte. Cette URL sera désormais celle de votre Manifeste sur le Web, elle est utilisable dans n'importe quelle application compatible.
                - copier aussi l'URL npoint de la page de votre Manifeste et coller là dans le pad, nous en aurons besoin plus loin pour éditer le Manifeste
