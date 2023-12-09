# Exercices

## 1. Test

!!! tip "Questions"

    1. **Ouvrir le Manifeste suivant :** [https://lbiiif.riksarkivet.se/arkis!R0002063/manifest](https://lbiiif.riksarkivet.se/arkis!R0002063/manifest)
        1. Quelle est l'URL du service API Image de l'unique Canevas de ce Manifeste ?
        2. Quelle est la particularité de l'implémentation de ce service API Image ?

    2. **Ouvrir le Manifeste suivant :** [https://ramp.avalonmediasystem.org/manifests/prod/lunchroom_manners.json](https://ramp.avalonmediasystem.org/manifests/prod/lunchroom_manners.json)
        1. Quelle est l'URL du fichier vidéo référencé dans l'unique Canevas de ce Manifeste ?
        2. Quelle est la particularité du "body" de cette annotation ?
        3. Comment cela se traduit-il dans l'interface du visualiseur [Clover](https://samvera-labs.github.io/clover-iiif/docs/viewer/demo?iiif-content=https://ramp.avalonmediasystem.org/manifests/prod/lunchroom_manners.json) ? Observer la différence avec l'interface de [Ramp](https://ramp.avalonmediasystem.org/?iiif-content=https://ramp.avalonmediasystem.org/manifests/prod/lunchroom_manners.json).

    3. **Tester le Manifeste suivant** (version 2.1) dans le [validateur officiel](https://presentation-validator.iiif.io) de l'API Présentation : [https://archives.lamayenne.fr/archives-en-ligne/iiif/ark:/37963/r314582ww55k/manifest.json](https://archives.lamayenne.fr/archives-en-ligne/iiif/ark:/37963/r314582ww55k/manifest.json)
        1. [Ouvrir ce Manifest dans Mirador](https://portail.biblissima.fr/m3/?theme=light&iiif-content=https://archives.lamayenne.fr/archives-en-ligne/iiif/ark:/37963/r314582ww55k/f1/manifest.json). Quelle pourrait être la source du problème ?

    4. **Ouvrir le Manifest suivant :** [https://figgy.princeton.edu/manifests/d58761ca-d7c3-4276-97f3-fe7e437b1af0/v3](https://figgy.princeton.edu/manifests/d58761ca-d7c3-4276-97f3-fe7e437b1af0/v3)
        1. Quels fichiers de métadonnées structurées est-il possible de récupérer via ce Manifeste ?


## 2. Identifier et sélectionner des ressources IIIF

Vous trouverez ci-dessous une liste de sites qui proposent des objets numérisés compatibles avec IIIF (bibliothèques, archives, musées, agrégateurs). Les sites affichant clairement leur conformité et donnant accès aux Manifestes ont été privilégiés.

!!! tip "Consignes"

    1. Parcourir quelques sites ci-dessous et conserver dans des onglets séparés les différentes pages ouvertes
        - Vous pouvez rechercher des objets qui vous intéressent parmi ces sites, ou pour aller plus vite vous pouvez aussi cliquer sur les exemples donnés dans la liste.
    2. Copier quelques URL de Manifestes dans le pad partagé ou dans un fichier texte sur votre ordinateur (au moins 3 ou 4 si possible)
        - Astuce : l'URL du Manifeste est parfois présente dans une section "métadonnées", parfois située ailleurs dans la page (souvent "cachée" derrière le logo IIIF)

### Liste d'entrepôts IIIF

#### Agrégateurs, portails, banques d'images

- [Biblissima IIIF-Collections](https://iiif.biblissima.fr/collections/) ([exemple](https://iiif.biblissima.fr/collections/manifest/ff0b1858186147611a78292d57f1f1537c6e6df3))
- [Portail Biblissima](https://portail.biblissima.fr) ([exemple](https://portail.biblissima.fr/fr/ark:/43093/descdbf571c2dcac868496312bf36d449401e4ac0af4))
- [FranceArchives](https://francearchives.gouv.fr) ([exemple](https://francearchives.gouv.fr/fr/facomponent/25703128b0cc973ba68db6f938388cf104f3bad9))
- [HeidICON](https://heidicon.ub.uni-heidelberg.de/search) ([exemple](https://heidicon.ub.uni-heidelberg.de/detail/762656))
- [Qatar Digital Library](https://www.qdl.qa/en/search/site/?f%255B0%255D=document_source%3Aarchive_source) ([exemple](https://www.qdl.qa/en/archive/81055/vdc_100027090276.0x000004)) 

#### Bibliothèques

- [Biblioteca Apostolica Vaticana](https://digi.vatlib.it) ([exemple](https://digi.vatlib.it/view/MSS_Vat.lat.3225))
- [Bayerische StaatsBibliothek, Munich](https://www.digitale-sammlungen.de/en/) ([exemple](https://www.digitale-sammlungen.de/en/view/bsb00003881?page=,1))
- [Bodleian Libraries, Oxford](https://digital.bodleian.ox.ac.uk) ([exemple](https://digital.bodleian.ox.ac.uk/objects/faeff7fb-f8a7-44b5-95ed-cff9a9ffd198))
- [e-codices - Virtual Manuscript Library of Switzerland](https://e-codices.ch) ([exemple](https://e-codices.ch/en/searchresult/list/one/fmb/cb-0007))
- [Cambridge University Library](https://cudl.lib.cam.ac.uk) ([exemple](https://cudl.lib.cam.ac.uk/view/MS-ADD-03965/1))
- [Durham University and Cathedral Library](https://collections.durham.ac.uk) ([exemple](https://iiif.durham.ac.uk/index.html?manifest=t1mk930bx00d))
- [Harvard University](https://library.harvard.edu/digital-collections) ([exemple](https://curiosity.lib.harvard.edu/immigration-to-the-united-states-1789-1930/catalog/39-HUAM11324soc_urn-3:HUAM:OCP14752_dynmc))

#### Musées

- [Art Gallery of Ontario](https://ago.ca/collection/browse) ([exemple](https://ago.ca/mirador/compare?objects=5997,6275))
- [Belvedere](https://sammlung.belvedere.at/) ([exemple](https://sammlung.belvedere.at/objects/6289/der-koch-le-pere-paul))
- [Germanisches Nationalmuseum - GMN](https://www.gnm.de/en/collections/collections/) ([exemple](https://tafelmalerei.gnm.de/wisski/navigate/161/view))
- [Harvard Art Museums](https://www.harvardartmuseums.org/collections) ([exemple](https://hvrd.art/o/296313))
- [J. Paul Getty Museum](http://www.getty.edu/art/collection/) ([exemple](https://www.getty.edu/art/collection/objects/144/vincent-van-gogh-portrait-of-joseph-roulin-dutch-1888/))
- [National Gallery of Art - USA](https://www.nga.gov/collection.html) ([exemple](https://www.nga.gov/collection/art-object-page.95419.html))
- [Princeton Art Museum](https://artmuseum.princeton.edu/collections/explore) ([exemple](https://artmuseum.princeton.edu/collections/objects/22783))
- [Smithsonian Institution](https://collections.si.edu/search/results.htm?q=&iiif.enabled=true) ([exemple](http://n2t.net/ark:/65665/sm489c1c193-694a-4012-8517-03ae07c89191))
- [SMK](https://open.smk.dk/en/) ([exemple](https://open.smk.dk/en/artwork/image/KMSsp292))
- [The Royal Collection Trust](https://albert.rct.uk) ([exemple](https://albert.rct.uk/collections/raphael-collection/vatican-frescoes/raphael-collection-portfolio-26))
- [The Frick Collection](https://www.frick.org/art) ([exemple](https://collections.frick.org/objects/265/antwerp-van-goyen-looking-out-for-a-subject))
- [The Huntington](https://emuseum.huntington.org/collections) ([exemple](https://emuseum.huntington.org/objects/12176/santuarioleon))
- [The Leiden Collection](https://www.theleidencollection.com/) ([exemple](https://www.theleidencollection.com/viewer/satyrs-nymphs-putti-and-leopards-in-a-landscape/))
- [Yale Center for British Art](https://collections.britishart.yale.edu/) ([exemple](https://collections.britishart.yale.edu/catalog/tms:1153))

#### Archives

- [National Archives of Japan](https://www.digital.archives.go.jp) ([exemple](https://www.digital.archives.go.jp/DAS/pickup/view/detail/detailArchivesEn/0305000000_5/0000000443/00))
- [Archives fédérales suisses](https://www.chgov.bar.admin.ch) ([exemple](https://www.chgov.bar.admin.ch/protocol?manifest=https://api.chgov.bar.admin.ch/manifests/32322135/32322135.json))
- [Archives départementales des Deux-Sèvres et de la Vienne](https://archives-deux-sevres-vienne.fr) ([exemple](https://archives-deux-sevres-vienne.fr/ark:/28387/vta563c56f414a055ae/daogrp/0/1))
- [Dublin City Library and Archive](https://www.virtualtreasury.ie) ([exemple](https://www.virtualtreasury.ie/item?isadgReferenceCode=DCLA%20Royal%20Charters%2F41))

D'autres listes d'entrepôts IIIF :

- [https://iiif.io/guides/finding_resources/](https://iiif.io/guides/finding_resources/)
- [https://dnoneill.github.io/annotate/getIIIFresources/](https://dnoneill.github.io/annotate/getIIIFresources/)

## 3. Prise en main de Mirador

Mirador est un visualiseur d'images configurable, extensible et facile à intégrer, qui permet d'annoter et de comparer des images provenant de différents entrepôts IIIF. Plus d'informations sur [projectmirador.org](https://projectmirador.org/).

Nous allons utiliser **l'instance Mirador du Portail Biblissima** :

- interface sombre : [https://portail.biblissima.fr/m3/?theme=dark](https://portail.biblissima.fr/m3/?theme=dark)
- interface claire : [https://portail.biblissima.fr/m3/?theme=light](https://portail.biblissima.fr/m3/?theme=light)

!!! tip "Consignes"

    1. **Importer dans Mirador au moins 2 ou 3 Manifestes** de votre choix parmi ceux sélectionnés lors de l'exercice précédent.
    2. **Créer un environnement multi-fenêtres (mode comparaison)** :
        - Expérimenter les deux types d'espaces de travail "Elastique" et "Mosaïque" (icône "roue dentée" dans la barre de menu à gauche)
        - Explorer les différents panneaux disponibles (informations, index, droits) et les options disponibles au niveau d'une fenêtre individuelle
    3. **Modifier les réglages d'une image** (luminosité, contraste, saturation, rotation etc.)
    4. **Utiliser la fonction de téléchargement** (icône "flèche vers le bas")
    5. **Importer d'autres ressources IIIF dans votre espace de travail** :
        - une image de votre ordinateur (glisser-déposer l'image dans la fenêtre Mirador)
        - à partir de l'un des sites suivants : Getty, National Gallery of Art, Princeton Art Museum, Harvard Art Museums, Yale Center for British Art, Biblissima
    6. **Importer/exporter votre session Mirador** :
        - dans la barre de menu principal (à gauche), cliquer sur l'icône avec les trois petits points horizontaux
        - cliquer sur _Exporter l'espace de travail_ puis _Copier_
        - recharger la page, ou bien ouvrir un Mirador vide dans un nouvel onglet ou dans un autre navigateur
        - cliquer sur _Importer un espace de travail_, puis faire un "coller" (Ctrl+V) dans la fenêtre vide, et cliquer sur _Importer_
