# Atelier 3 : créer une exposition virtuelle avec Storiiies

Storiiies est un outil d'exposition virtuelle permettant de créer des parcours guidés au sein d'une image. Il s'appuie à la fois sur des images et des annotations IIIF pour proposer ces parcours. Il est développé par la société britannique Cogapp.

Il est constitué de deux applications :

- le [Storiiies Editor](https://storiiies-editor.cogapp.com) : éditeur pour créer et modifier une exposition virtuelle, utilisable uniquement via le site de Cogapp
- le [Storiiies Viewer](https://www.cogapp.com/r-d/storiiies) : visualiseur d'exposition virtuelle, disponible en open source ([Github](https://github.com/CogappLabs/StoriiiesViewer))

Pour cet atelier nous allons utiliser une version du Storiiies Viewer hébergée par Biblissima : [https://demos.biblissima.fr/storiiies-viewer/](https://demos.biblissima.fr/storiiies-viewer/). Cette instance supporte le paramètre `iiif-content` de l'API Content State, ce qui signifie qu'il est possible de charger un Manifeste en passant son adresse dans ce paramètre d'URL.

``` title="Modèle d'URL pour ouvrir un Manifeste dans le Storiiies Viewer"
https://demos.biblissima.fr/storiiies-viewer/?iiif-content={url_manifeste_story}
```


!!! tip "Consignes"

    Dans cet exercice nous allons tous partir du même Manifest : [https://www.loc.gov/item/2003626426/manifest.json](https://www.loc.gov/item/2003626426/manifest.json) (Library of Congress : [Waldseemüller’s 1507 Map](https://www.loc.gov/item/2003626426/)).


    1. **Ouvrir le [Storiiies Editor](https://storiiies-editor.cogapp.com) pour créer votre "story"**
        - coller l'URL du Manifeste dans le champ `IIIF manifest or info.json URL`
        - renseigner les autres champs proposés

    2. **Créer un parcours en zoomant sur différents détails dans l'image :**
        - zommer sur un détail et créer une annotation en cliquant sur le bouton "Add new +" en haut à gauche. Chaque annotation correspondra à une étape du parcours au sein de l'image
        - répéter l'opération de façon à créer 3 ou 4 annotations

    3. **Prévisualiser votre story et récupérer l'URL du Manifeste correspondant :**
        - cliquer sur le bouton "Preview" (ouvre un nouvel onglet) et tester votre story
        - reconstruire l'URL du Manifeste de votre story en suivant les indications ci-dessous :

        L'URL de la page du Preview est sous la forme suivante : 

        `https://storiiies.cogapp.com/viewer/{id}/{story_name}`

        Pour récupérer l'URL du Manifeste de votre story, il faut d'abord prendre son identifiant (valeur de `{id}`) et construire l'URL suivante :

        ```
        https://manifest.storiiies-editor.cogapp.com/v3/{id}
        ```

    4. **Ouvrir le Manifeste et repérer dans le JSON les annotations créées dans le Storiiies Editor :**
        - repérer la propriété `"annotations"` au niveau de l'unique Canevas présent dans votre Manifest

    5. **Importer le Manifeste dans le Storiiies Viewer :**
        - utiliser pour cela le paramètre `iiif-content` de l'API Content State vu précédemment :

        Modèle : 

        ```
        https://demos.biblissima.fr/storiiies-viewer/?iiif-content={url_manifeste_story}
        ```

    6. **Importer le Manifeste dans l'outil Annona :**
        - utiliser pour cela le même paramètre `iiif-content` :

        Modèle : 

        ```
        https://demos.biblissima.fr/annona/?iiif-content={url_manifeste_story}
        ```


Il existe d'autres outils dans la galaxie IIIF qui permettent de créer des expériences similaires, parmi lesquels :

- [Exhibit.so](https://www.exhibit.so/#getting-started) est plus perfectionné que Storiiies (prend en charge plusieurs images issues de plusieurs Manifests, propose différents templates), mais le code source est fermé et il n'est possible de récupérer ni le Manifest généré par l'application, ni les annotations créées.

Exemple : [The Voyage of Life, par Thomas Cole](https://www.exhibit.so/exhibits/t153UkCxJXovu1jeuLV3)

- [Adno](https://adno.app/fr/) a l'avantage d'être entièrement open source mais, comme Storiiies, il ne prend en charge qu'une seule image par parcours. De plus il ne supporte IIIF qu'en entrée, pas en sortie (l'outil permet néanmoins d'exporter un projet au format Web Annotation, puis de réimporter le projet par la suite). Il est basé sur les librairies Annona, Annotorious et OpenSeaDragon.

Pour une liste plus complète, voir la section [Exhibition and Guided Viewing Tools](https://github.com/IIIF/awesome-iiif/#exhibition-and-guided-viewing-tools) de awesome-iiif.


!!! question "Questions"

