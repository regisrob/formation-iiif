# Identifier

<script src="../../viewer.js"></script>
<script src="../../extras.js"></script>

L'exemple ci-dessous décompose les différentes parties d'une requête d'image IIIF.

La partie surlignée ci-dessous est l'**URL de base** (_Base URL_), elle se compose :

  - du protocole : `https`
  - du nom de domaine : `ids.lib.harvard.edu`
  - d'un préfixe optionnel : `/ids/iiif`
  - de la partie **identifier** : `25286607`

Cette dernière partie est **l'identifiant unique de l'image** dans l'entrepôt source. Ce peut être un ARK, un URN, un simple nom de fichier, ou tout autre identifiant alphanumérique. L'API Image ne spécifie rien quant à la forme de cet identifiant, à part que certains caractères spéciaux (y compris le slash) doivent être encodés ("encodage-pourcent").

Tout ce qui est situé à droite de cette "URL de base" est contrôlé par l'API Image.

<div id="image_api_demo2">
</div>
<script>
   addViewer({
        div: 'image_api_demo2',
        images: [
            'https://ids.lib.harvard.edu/ids/iiif/25286607',
            'https://dlcs.io/iiif-img/wellcome/5/b14658197.jp2',
            'https://ids.si.edu/ids/iiif/CHSDM-317E001E9E352-000001'
            ],
        sizes: [
            '500,',
            '500,500',
            '!500,500'
        ],
        regions: [
            'full',
            'square',
            '1000,100,3000,2000',
            '2000,3000,2000,2000',
        ],
        highlight: [
            'identifier'
        ]
   });
</script>  

## Info.json

L'API Image définit un autre type de requête qui se construit en ajoutant le suffixe `info.json` à l'URL de base (juste après la partie `identifier`).

Cette requête permet de fournir des métadonnées techniques de l'image, utilisables par une application cliente (visualiseur ou autre logiciel) sous la forme de données au format JSON.

Exemple : [https://iiif.library.ucla.edu/iiif/2/ark%3A%2F21198%2Fzz00090nmj/info.json](https://iiif.library.ucla.edu/iiif/2/ark%3A%2F21198%2Fzz00090nmj/info.json)

```json
{
  "@context": "http://iiif.io/api/image/2/context.json",
  "@id": "https://iiif.library.ucla.edu/iiif/2/ark%3A%2F21198%2Fzz00090nmj",
  "protocol": "http://iiif.io/api/image",
  "width": 3315,
  "height": 2140,
  "sizes": [
    {
      "width": 104,
      "height": 67
    },
    {
      "width": 207,
      "height": 134
    },
    {
      "width": 414,
      "height": 268
    },
    {
      "width": 829,
      "height": 535
    },
    {
      "width": 1658,
      "height": 1070
    },
    {
      "width": 3315,
      "height": 2140
    }
  ],
  "tiles": [
    {
      "width": 512,
      "height": 512,
      "scaleFactors": [
        1,
        2,
        4,
        8,
        16,
        32
      ]
    }
  ],
  "profile": [
    "http://iiif.io/api/image/2/level2.json",
    {
      "formats": [
        "jpg",
        "tif",
        "gif",
        "png"
      ],
      "maxArea": 7094100,
      "qualities": [
        "bitonal",
        "default",
        "gray",
        "color"
      ],
      "supports": [
        "regionByPx",
        "sizeByW",
        "sizeByWhListed",
        "cors",
        "regionSquare",
        "sizeByDistortedWh",
        "canonicalLinkHeader",
        "sizeByConfinedWh",
        "sizeByPct",
        "jsonldMediaType",
        "regionByPct",
        "rotationArbitrary",
        "sizeByH",
        "baseUriRedirect",
        "rotationBy90s",
        "profileLinkHeader",
        "sizeByForcedWh",
        "sizeByWh",
        "mirroring"
      ]
    }
  ]
}
```

Ces métadonnées techniques sur l’image comprennent notamment :

- les dimensions de l’image (`width` / `height`)
- tailles préférées du serveur qui délivre l'image (`sizes`)
- les dimensions des tuiles d'image le cas échéant, utilisées pour le zoom (`tiles`)
- des informations de conformité (`profile`) : version de l’API Image supportée par le serveur, niveau de compatibilité avec l'API Image (level), autres fonctionnalités supportées

Ces fonctionnalités sont définies dans la spécification de l'API Image, dans l'annexe _[Image API Compliance](https://iiif.io/api/image/2.1/compliance/)_.
