# Region

<script src="../../viewer.js"></script>

Le paramètre de région permet d'extraire une portion de l'image adressée sous la forme `/x,y,width,height/`, en partant du coin supérieur gauche de l'image.

![region example (Copyright © 2012-2022 Editors and contributors. Published by the IIIF Consortium under the CC-BY license)](https://iiif.io/api/image/2.1/img/region_px.png)

La région correspondante serait ainsi notée `/125,15,120,140/` :

 * x = 125 pixels du bord gauche
 * y = 15 pixels du bord supérieur
 * width = 120 pixels de largeur
 * height = 140 pixels de hauteur
 
 Les valeurs en pixels sont relatives à l'image pleine taille (largeur et hauteur). Elles peuvent aussi être exprimées en pourcentage : `/pct:x,y,w,h/`.

En plus des dimensions en pixels ou en pourcentage, il y a deux autres valeurs possibles pour ce paramètre :

 * `full` : l'image entière  
 * `square` : une portion pour laquelle la largeur et la hauteur sont égales. La position de la région est déterminée par le serveur (peut être utile pour générer des vignettes de forme carrée).

Utilisez la liste déroulante pour cibler différentes portions de l'image :

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
        ],
        regions: [
            'full',
            'square',
            '1000,100,3000,2000',
            '2000,3000,2000,2000',
        ],
        highlight: [
            'region'
        ]
   });
</script>  
