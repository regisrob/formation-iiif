# Size

<script src="../../viewer.js"></script>
<script src="../../extras.js"></script>

Le paramètre `size` agit sur la taille de l'image en sortie. La liste complète des valeurs possibles est disponibles dans la [spécification de l'API Image](https://iiif.io/api/image/2.1/#size). Parmi les plus courants, on trouve :

| Forme | Description |
| -- | -- |
| full | Image pleine taille (renommé `max` dans l'API 3.0) |
| w, | Seule la largeur est spécifiée et le serveur doit calculer la bonne hauteur pour conserver le ratio d'aspect. Exemple `500,`|
| ,h | Équivalent avec la hauteur seule. Exemple `,250`|
| w,h | Largeur et hauteur fixes. Cela va distordre l'image. Exemple: `250,250` |
| !w,h | L'image extraite est mise à l'échelle de sorte que la largeur et la hauteur ne soient pas supérieures à w et h, tout en conservant le ratio d'aspect. Exemple `!250,150`  |
| pct:n | L'image extraite est mise à l'échelle selon un facteur de n pourcent. Exemple `pct:10` |

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
            '250,',
            ',250',
            'full',
            'max',
            '250,250',
            '!250,150',
            'pct:10'
        ],
        regions: [
            'full',
            'square',
            '1000,100,3000,2000',
            '2000,3000,2000,2000',
        ],
        highlight: [
            'size'
        ]
   });
</script>  
