# Format

<script src="../../viewer.js"></script>
<script src="../../extras.js"></script>

Le format de l'image renvoyée par le serveur, par exemple `jpg` ou `png`. La liste des formats supportés par le serveur d'image est indiquée dans le `info.json`.

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
            'full',
            'max',
            '250,',
            ',250',
            '250,250',
            '!250,250'
        ],
        regions: [
            'full',
            'square',
            '1000,100,3000,2000',
            '2000,3000,2000,2000',
        ],
        highlight: [
            'format'
        ]
   });
</script>
