# Implémentation

## Comment créer un Manifeste IIIF ?

### Génération automatique

Il n'y a pas de recette unique ou de méthode universellement applicable pour créer des Manifestes : la production d'un Manifeste est souvent une opération spécifique à un environnement institutionnel ou informatique donné.

Dans la plupart des cas, un Manifeste résulte de la combinaison de plusieurs types d'informations (qui peuvent potentiellement provenir de systèmes ou de sources différentes) :

- **des images IIIF accessibles**
- **un ensemble de métadonnées descriptives** de l'objet, dérivé par exemple d'une notice catalographique, d'un instrument de recherche, d'un enregistrement dans une base de données ou un fichier quelconque
- **des informations de séquence et de structure** de l'objet numérique : en premier lieu la liste ordonnée des images qui le constitue, avec leurs identifiants et leurs dimensions en pixels.

Ces métadonnées nécessaires à la génération d'un Manifeste peuvent être structurées dans différents formats source (METS/MODS, XML-TEI, XML-EAD, tableur type CSV, base de données relationnelle etc.).

Un Manifeste IIIF est le plus souvent généré de façon dynamique par un outil plus large : système de gestion d'actifs numériques (DAM), système de gestion de contenus (CMS), système de gestion de collections etc. Une [liste d'outils et plateformes compatibles](https://iiif.io/get-started/vendors/) est disponible sur le site de IIIF.

Une alternative à ces systèmes (en majorité propriétaires) est de générer soi-même ses Manifests, en fonction des données et des moyens disponibles. Il existe un certain nombre de librairies qui peuvent aider dans ce processus, comme par exemple :

- [biiif](https://github.com/edsilv/biiif/), qui permet de générer des Manifests à partir d'une simple arborescence de fichiers et de dossiers organisés selon une certaine convention.
- [demetsiiify](https://github.com/jbaiter/demetsiiify), un web service pour créer des Manifests à partir de fichiers METS/MODS.
- et [d'autres librairies](https://github.com/IIIF/awesome-iiif/#presentation-api-libraries), codées dans différentes langages, qui facilitent la génération de Manifestes (mais ce ne sont pas des outils "clés en main").

Quel que soit l'outil ou la librairie utilisée, un Manifeste peut très bien être pré-généré en amont et stocké comme un simple fichier JSON sur un serveur Web classique. Nulle nécessité d'avoir un système complexe de génération à la volée, de stockage en base de données etc.

### Création manuelle

Il existe aussi des éditeurs en ligne qui offrent une interface utilisateur pour créer des Manifestes, mais aussi éditer et combiner entre eux des Manifestes existants.

On peut citer notamment le [IIIF Manifest Editor](https://digital.bodleian.ox.ac.uk/manifest-editor) (Bodleian / text&bytes) et celui de [Digirati Manifest Editor](https://github.com/digirati-co-uk/iiif-manifest-editor).


## Lien avec l'API Image

L'API Présentation est le plus souvent utilisée conjointement à l'API Image. 

En termes d'implémentation, le fait de coupler les deux API implique d'être capable, lors de la génération des Manifestes, d'établir le lien entre une vue au sein de l'objet (Canevas) et le service API Image de l'image correspondante.

Comme on l'a vu au chapitre précédent, l'API Image permet à un visualiseur de supporter le zoom et de gérer au mieux l'affichage des différents dérivés d'une image pour proposer différents types de vues (vignette, aperçu).

Cependant, il est possible d'implémenter uniquement l'API Présentation, sans l'API Image. Cela peut se justifier, en particulier si les images sont en faible résolution et ne nécessitent pas de zoom. Mais il faut être conscient des limites...

Prenons l'exemple du portail [Paris Musées](https://www.parismuseescollections.paris.fr), qui propose des Manifestes pour les objets dont les images sont libres de droits, mais sans l'API Image :

- _Carte géologique de la ville de Paris_ | [Page web](https://www.parismuseescollections.paris.fr/fr/musee-carnavalet/oeuvres/carte-geologique-de-la-ville-de-paris-inspection-generale-des-carrieres) -- [Manifeste JSON (v2)](https://apicollections.parismusees.paris.fr/iiif/320296507/manifest) -- [Ouvrir dans Mirador](https://portail.biblissima.fr/m3/?theme=light&iiif-content=https://apicollections.parismusees.paris.fr/iiif/320296507/manifest) 
- _Le Figaro Illustré. Exposition Universelle de 1900_ | [Page web](https://www.parismuseescollections.paris.fr/fr/petit-palais/oeuvres/le-figaro-illustre-exposition-universelle-de-1900-0) -- [Manifeste JSON (v2)](https://apicollections.parismusees.paris.fr/iiif/160040011/manifest) -- [Ouvrir dans Mirador](https://portail.biblissima.fr/m3/?theme=light&iiif-content=https://apicollections.parismusees.paris.fr/iiif/160040011/manifest)

En ouvrant dans Mirador le 2e exemple, on constate que l'affichage des vignettes est lent et que globalement toutes les images mettent du temps à se charger. Cela est dû au fait que, à défaut de pouvoir interagir avec l'API Image, Mirador est obligé de télécharger à chaque fois l'image pleine taille (qui peut aller jusqu'à plusieurs Mo).


## Bonnes pratiques

Pour terminer cette partie, énumérons quelques bonnes pratiques à respecter en tant qu'implémenteur de l'API Présentation :

1. fournir si possible l'API Image en complément de l'API Présentation (question de performance et de fonctionnalités étendues).
2. mettre en place des URI stables pour toutes les ressources IIIF, à tous les niveaux (tous les `@id` ou `id`) : `Manifest`, `Canvas`, `Annotation`, `Content` (images etc.)
3. inclure un maximum de métadonnées descriptives dans les propriétés idoines du Manifeste (en particulier dans `metadata`). Ces informations doivent "voyager" avec l'objet et pouvoir être affichées à l'utilisateur quel que soit le contexte dans lequel il le visualise ou l'application dans lequel il l'a importé.
4. toujours pointer vers la page de l'objet sur le site d'origine, pour permettre à l'utilisateur de rebondir vers la page de la notice ou vers le visualiseur (propriétés `related` ou `homepage`)
5. fournir via la propriété `seeAlso` un lien vers des métadonnées structurées, dans l’idéal conformes à un standard reconnu (Dublin Core, TEI, EAD, MODS etc.). Cela permet à des scripts de moissonnage de suivre ce lien pour indexer des métadonnées riches et sémantisées. Voir [_IIIF Cookbook - Linking to Structured Metadata_](https://iiif.io/api/cookbook/recipe/0053-seeAlso/).
6. à l'inverse, inclure si possible l'URL du Manifeste dans un champ de métadonnées ou une propriété adéquate dans les données structurées mises à disposition. L’idée est de pouvoir isoler facilement cette URL au moment de la collecte des métadonnées, quelle que soit la procédure employée pour cette opération (moissonnage d’un entrepôt OAI-PMH, moissonnage de fichiers XML, requête SPARQL dans un entrepôt RDF etc.) ;
7. rendre visible l'URL du Manifeste sur la page de l'objet dans le site d'origine, si possible accompagnée de l'icône IIIF. Un bouton "Copier" facilite la récupération de cette URL par les utilisateurs.
8. vérifier la conformité des Manifestes en utilisant le [validateur officiel](https://presentation-validator.iiif.io/)
9. respecter certains pré-requis techniques dans la configuration du serveur (protocole HTTPS et entêtes HTTP CORS).

Voir aussi les [recommandations pour les bibliothèques numériques IIIF](https://doc.biblissima.fr/vademecum-biblissima/#recommandations-pour-les-bibliotheques-numeriques-iiif) dans la documentation de Biblissima.
