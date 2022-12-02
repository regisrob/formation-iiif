# Atelier 2 : annoter un Manifeste avec SimpleAnnotationServer

!!! info "SimpleAnnotationServer"

    [SimpleAnnotationServer](https://github.com/glenrobson/SimpleAnnotationServer) (SAS) est un serveur d'annotations IIIF écrit en Java et développé par Glen Robson (coordinateur technique de IIIF) :
    
    - il est couplé à la version 2 de Mirador pour la partie cliente dédiée à la visualisation des images et à la création des annotations.
    - la partie serveur sert à stocker les annotations de façon persistente. Différents backend sont possibles : Jena, ElasticSearch, Solr
    - il supporte l'API Content Search et fournit un point d'accès (_endpoint_) permettant de rechercher dans les annotations créées.

Pour cet exercice, nous allons utiliser l'instance de test de Biblissima, activée pour les besoins de la formation : [https://demos-dev.biblissima.fr/simpleAnnotationStore/](https://demos-dev.biblissima.fr/simpleAnnotationStore/)

Avant de commencer l'exercice, voyons un exemple d'exploitation des annotations IIIF créées via Mirador et stockées dans SAS :

- *Ovide moralisé ou La Bible des poètes en images. Comparaison de deux cycles iconographiques avec IIIF et Mirador*. Démos Biblissima. [https://demos.biblissima.fr/ovide-moralise/](https://demos.biblissima.fr/ovide-moralise/)


!!! tip "Consignes"

    1. **Importer un Manifeste dans SAS :**
        - cliquer sur `Index Manifest` puis entrer l'URL de votre Manifeste créé à l'étape précédente
        - une page dédiée à votre Manifeste devrait s'afficher, avec son `label` en tant que titre principal de la page
        - votre Manifeste devrait aussi s'afficher dans l'onglet `View annotations`, parmi la liste des `Indexed Manifests`

    2. **Annoter votre Manifeste dans Mirador :**
        - revenir sur la page de votre Manifeste dans SAS
        - cliquer sur le lien `Annotate` : votre Manifeste devrait alors s'ouvrir dans Mirador
        - cliquer sur l'icône en forme de bulles en haut à gauche de la vue image
        - sélectionner une forme de tracé (rectangle, ovale, tracé libre, polygone, marqueur) et changer si vous le souhaitez l'épaisseur et la couleur du trait, ainsi que la couleur de remplissage de la forme
        - délimiter la zone (ou le point) de l'image à annoter ; une fenêtre devrait apparaître au-dessus de l'image
        - saisir votre annotation dans l'éditeur (un formatage html de base est possible) ; un champ "Tags" est aussi disponible
        - cliquer sur `Enregistrer` pour sauvegarder l'annotation : celle-ci est désormais stockée de manière persistente dans SAS (dans l'entrepôt RDF de Jena, plus précisément)
        - répéter l'opération pour créer 2 ou 3 annotations sur une ou plusieurs images

    3. **Voir dans SAS le détail des annotations créées :**
        - cliquer sur `View annotations` dans le menu supérieur, puis cliquer sur votre Manifeste
        - cliquer ensuite sur `Download annotations`, puis sur un lien situé en dessous de l'encadré gris : un document JSON s'ouvre, il contient la liste des annotations qui ont été créées (ce document JSON est une `AnnotationList` conforme à l'[API Presentation 2.1](https://iiif.io/api/presentation/2.1/#annotation-list))

    4. **Activer et tester la recherche dans ces annotations** (API Content Search) :
        - revenir sur la page de votre Manifeste dans `View annotations`
        - dans la section `IIIF Search Service`, copier le morceau de JSON du 1er encadré gris (celui qui commence par `"service"`) : ceci est la référence au service API Content Search actif pour votre Manifeste
        - mais pour qu'un visualiseur tiers puisse utiliser ce service, il va falloir éditer votre Manifeste et inclure cette référence dans le fichier JSON source
        - pour ce faire, ouvrir dans un nouvel onglet la page npoint ou Github de votre Manifeste (selon le choix fait lors de l'atelier 1) de façon à pouvoir l'éditer
        - coller le morceau de JSON juste après le `label` par exemple, puis enregistrer la modification
        - ouvrir votre Manifeste dans un autre onglet et vérifier que la modification a bien été appliquée (avec Github il peut y avoir un petit délai avant que le changement ne soit effectif)
        - une fois le Manifeste mis à jour, l'importer dans l'instance Mirador 3 utilisée tout à l'heure : [https://portail.biblissima.fr/m3/?theme=light&context=collection](https://portail.biblissima.fr/m3/?theme=light&context=collection)
        - il ne vous reste plus qu'à tester la recherche ! Dans la barre d'outils à gauche, cliquer sur l'icône en forme de loupe, puis rechercher un terme parmi ceux que vous avez saisis dans vos annotations créées plus haut (attention la recherche est sensible à la casse). Vous pouvez rechercher un terme dans le texte de l'annotation ou dans les tags (si vous en avez saisis). Des résultats devraient s'afficher dans le panneau de gauche.

    5. **Activer et tester l'affichage des annotations** (annotationList) :
        - revenir sur la page de votre Manifeste dans `View annotations`
        - cliquer sur `Download annotations` : cette page liste les Canevas qui ont été annotés dans votre Manifeste (les liens vers les `AnnotationLists` de chaque Canevas apparaissent sous l'encadré gris) 
        - l'encadré gris avec le morceau de JSON présente un exemple de comment ces `AnnotationLists` doivent être incluses dans votre Manifeste au niveau de chaque Canevas. C'est ce que nous allons essayer de faire dans la suite de l'exercice. L'idée est de référencer ces `AnnotationLists` dans votre Manifeste pour que n'importe quel client soit en mesure de les afficher.
        - au préalable, essayer de retenir sur quel(s) Canevas(s) vous avez fait des annotations. En principe le libellé de chaque Canevas est indiqué dans la liste de liens en dessous de l'encadré gris (par exemple `Page 1`)
        - copier uniquement la partie `otherContent` du morceau de JSON :

        ```
        "otherContent": [ {
          "@id": "http://example.com/sas/annotation/list/4f0d84d2b3a3788a1d4a4faf7cc22b56.json",
          "@type": "sc:AnnotationList",
          "label": "Example annotations"
        }],
        ```

        - dans un nouvel onglet, revenir à la page d'édition de votre Manifeste sur npoint ou Github (selon le choix fait lors de l'atelier 1)
        - coller le morceau `otherContent` dans le Canevas correspondant (de préférence vers le début pour que ce soit plus facile de se repérer) : vous pouvez par exemple le copier juste après le `@id` du Canevas en question
        - si vous avez fait des annotations sur plusieurs Canevas, et donc si vous avez plusieurs `AnnotationLists`, répéter l'opération pour chaque Canevas concerné
        - maintenant il va falloir remplacer la fausse URL `http://example.com/sas/annotation/list` par la vraie, là encore pour tous les Canevas concernés
        - pour ce faire, retourner dans SAS et copier l'URL de chaque `AnnotationLists`
        - revenir ensuite dans npoint ou Github puis remplacer l'URL présente dans le `@id` du `otherContent` (`http://example.org/sas/...`) par celle de votre propre `AnnotationLists` :

        ```
        "otherContent": [ {
          "@id": "https://demos-dev.biblissima.fr/simpleAnnotationStore/annotation/list/7c6c5b88519132f268f89b96674ece81.json",
          "@type": "sc:AnnotationList",
          "label": "Mes annotations test"
        }],
        ```

        - une fois cela fait pour un ou plusieurs Canevas, enregistrer la modification de votre Manifeste
        - ouvrir votre Manifeste dans un autre onglet et vérifier que la modification a bien été appliquée (avec Github il peut y avoir un petit délai avant que le changement ne soit effectif)
        - une fois le Manifeste mis à jour, l'importer dans l'instance Mirador 3 utilisée tout à l'heure : [https://portail.biblissima.fr/m3/?theme=light&context=collection](https://portail.biblissima.fr/m3/?theme=light&context=collection)
        - vous devriez remarquer qu'une icône `Annotations` avec une pastille orange est désormais présente dans la barre d'outils à gauche
        - cliquer sur cette icône pour déplier le panneau : vos annotations devraient y être listées et apparaître sur l'image

**Mais pour quelle raison étrange avons-nous dû faire toutes ces manipulations fastidieuses ?**

Pour mieux comprendre, revenons dans l'instance Mirador de SAS : 

- On peut constater que les annotations s'affichent bien pour tous les Manifestes qui ont été importés et annotés dans la plateforme, sans qu'on ait eu besoin de faire toute cette tambouille. **Pourquoi ?** 
- Cela est dû au fait que cette instance de Mirador est en quelque sorte "branchée" au serveur d'annotations SAS : le visualiseur "sait" où et comment il doit envoyer des requêtes pour récupérer les annotations associées à chaque Canevas. Il est d'une certaine manière "connecté" à la base de stockage de ces annotations.
- En revanche, une autre instance de Mirador ou de n'importe quel autre visualiseur n'a pas cette connaissance et ne pourra donc pas accéder aux annotations créées dans SAS. Le seul moyen pour qu'il puisse les afficher est de les inclure, ou plutôt de les référencer, dans le Manifeste. C'est par ce biais que les annotations vont pouvoir "voyager" avec le Manifeste...

**Dans ce cas, pourquoi SAS n'inclut-il pas lui-même ces annotations dans le Manifeste ?**

Lorsque SAS importe et indexe un Manifeste, il ne crée pas une copie de ce dernier : il importe le contenu du Manifeste tel quel, en conservant tous les `@id` d'origine (URI du Manifest, URI des Canevas, URI des images). Ce qui veut dire que toutes les annotations créées seront rattachées à ces URI : ainsi chaque annotation va cibler un Canevas en particulier, identifié par telle URI, provenant de tel Manifest, identifié par telle URI, etc. C'est là qu'on entre dans la dimension proprement "web sémantique" de IIIF. Toutes ces données sont en réalité des triplets RDF dans lesquels chaque ressource (_Manifest_, _Canvas_, _Annotation_ etc.) est identifiée de manière unique par une URI sur le Web.

Pour revenir à la question de départ, si SAS ne crée pas une copie d'un Manifeste importé, c'est justement pour conserver la relation entre les annotations créées et les ressources IIIF d'origine (à la fois le Manifest et le Canevas cible, grâce à leurs URI). Moralité : ces annotations restent de fait séparées du Manifest d'origine. Les annotations sont stockées dans SAS, mais les Manifests auxquels elles sont associées restent inchangés et sont toujours appelés à distance (depuis n'importe quel entrepôt IIIF). Évidemment SAS n'a pas la main pour modifier les Manifests à la source...

Dans cet exercice nous avons créé au préalable notre propre Manifeste, auquel nous avons accès en écriture (via npoint ou Github). C'est ce qui nous a permis d'ajouter à la main à la fois la référence au service API Content Search puis aux `AnnotationLists`. Ainsi un visualiseur externe tel que l'instance Mirador de Biblissima a pu avoir accès à ces données et à cette fonctionnalité via notre Manifeste, comme nous avons pu l'expérimenter. Mais si nous étions parti par exemple d'un Manifeste de Gallica, nous n'aurions pas pu faire la même chose, en tout cas pas sans dupliquer ce Manifeste pour le restocker quelque part où on puisse le modifier...

Il serait certes envisageable que SAS crée un dérivé du Manifest d'origine au moment de l'import, tout en conservant les URI des Canevas, mais ce n'est pas le choix qui a été fait par le développeur. En faisant cela, on se retrouverait dans une situation dans laquelle chaque annotateur ou projet d'annotation devrait travailler sur un clone du Manifest d'origine. Ce n'est pas optimal, mais c'est la seule solution possible à l'heure actuelle. Et c'est ainsi que procèdent beaucoup de projets qui utilisent des Manifestes fournis par des institutions patrimoniales et qui y apportent des enrichissements (annotations, transcriptions etc.). On peut citer notamment les plateformes de transcription _FromThePage_ aux États-Unis, et _Arkindex_ en France (Teklia), qui chacune recrée dans son propre système un Manifeste dérivé pour pouvoir avoir la main dessus et ainsi l'enrichir avec ses propres données. 

Le plus important dans ce cas de figure est que le Manifeste dérivé et les annotations créées conservent quelque part dans les données les références aux ressources IIIF d'origine, de façon à ce que ces annotations puissent à un moment donné être reversées dans le Manifest source (maintenu par telle ou telle bibliothèque, service d'archives, musée etc.).

Voyons quelques exemples pour illustrer ce propos :

- Page d'un manuscrit de Parker Library (Corpus Christi College, Cambridge) dans le Portail Biblissima, avec affichage des annotations (Manifeste IIIF délivré par Stanford) : [https://portail.biblissima.fr/fr/ark:/43093/mdata52c0e7fe45e95a834dfdcbfb9704c8c3774988b6](https://portail.biblissima.fr/fr/ark:/43093/mdata52c0e7fe45e95a834dfdcbfb9704c8c3774988b6)
- Page du site _Thematic Pathways on the Web - IIIF annotations of manuscripts from the Vatican collections_ : [28r: Urb.lat.365 — Miniatura tabellare assegnata a](https://spotlight.vatlib.it/latin-paleography/catalog/433953b3-64ec-486e-8bfb-8a7ba4cf0b6b), où l'on peut voir des annotations IIIF, mais celles-ci ne sont pas répercutées dans le Manifest d'origine publié par la Bibliothèque Vaticane (voir ce manuscrit sur [DigiVatLib](https://digi.vatlib.it/view/MSS_Urb.lat.365) et sur le [Mirador Biblissima](https://portail.biblissima.fr/m3/?theme=light&iiif-content=https://digi.vatlib.it/iiif/MSS_Urb.lat.365/manifest.json))
- Page d'un manuscrit de la BnF dans _FromThePage_, importé via IIIF et transcrit dans le cadre d'un projet collaboratif : [BnF. Bibliothèque de l'Arsenal. Ms-8536](https://fromthepage.com/stanfordlibraries/the-international-la-sfera-challenge/bnf-bibliotheque-de-l-arsenal-ms-8536). La plateforme a recréé un Manifeste ([https://fromthepage.com/iiif/34889/manifest](https://fromthepage.com/iiif/34889/manifest)) et propose de façon assez astucieuse une API qui permettrait par exemple à la BnF de récupérer facilement les données produites (transcription + traduction) : 
[https://fromthepage.com/iiif/for/https://gallica.bnf.fr/iiif/ark:/12148/btv1b55013450m/manifest.json](https://fromthepage.com/iiif/for/https://gallica.bnf.fr/iiif/ark:/12148/btv1b55013450m/manifest.json) (`https://fromthepage.com/iiif/{URL_MANIFESTE_SOURCE}`)
