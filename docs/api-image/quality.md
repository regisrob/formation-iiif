# Quality

<script src="../../viewer.js"></script>

Le paramètre `quality` définit le mode de couleur de l'image:

| Nom | Définition  |
| --- | --- |
| Default | Le mode de couleur par défaut de l'image |
| Gray | Niveau de gris |
| Bitonal | Chaque pixel est noir ou blanc | 
| Color  | L'image couleur | 

Cette fonctionnalité peut être utile à des outils de traitement et d'analyse d'image, par exemple pour de l'OCR/HTR.

Les valeurs de `quality` supportées par un serveur d'images IIIF sont indiquées dans le fichier `info.json`.

[https://ids.lib.harvard.edu/ids/iiif/25286607/info.json](https://ids.lib.harvard.edu/ids/iiif/25286607/info.json)

``` json
"profile": [
    "http://iiif.io/api/image/2/level2.json",
    {
        "supports": [
            "canonicalLinkHeader",
            "profileLinkHeader",
            "mirroring",
            "rotationArbitrary",
            "regionSquare",
            "sizeAboveFull"
        ],
        "qualities": [
            "default",
            "bitonal",
            "gray",
            "color"
        ],
        "formats": [
            "jpg",
            "png",
            "gif",
            "webp"
        ]
    }
],
```

<div id="image_api_demo2">
</div>
<script>
   addViewer({
        div: 'image_api_demo2',
        images: [
            'https://ids.lib.harvard.edu/ids/iiif/25286607'
            ],
        sizes: [
            '500,',
            '250,'
        ],
        highlight: [
            'quality'
        ]
   });
</script>  
