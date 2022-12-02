# Rotation

<script src="../../viewer.js"></script>
<script src="../../extras.js"></script>

La paramètre `rotation` permet de faire pivoter l'image jusqu'à 360°. Il est possible d'utiliser un point d'exclamation devant la valeur (`!n`) afin de retourner l'image sur l'axe vertical (_mirroring_). Tous les serveurs d'image ne supportent pas la rotation. Les différents niveaux de support sont détaillées dans l'annexe _[Image API Compliance](https://iiif.io/api/image/2.1/compliance/)_

| Fonctionnalité | Niveau |
| --- | --- |
| Rotation non supportée | Level 0 |
| Seule la rotation à 90° est supportée | Optionnel au Level 1, requis au Level 2 |
| Rotation arbitraire | Toujours optionnel |
| Mirroring | Toujours optionnel |

Le service API Image d'Harvard supporte tous les paramètres de rotation (implémentation du Level 2). 

<div id="image_api_demo2">
</div>
<script>
   addViewer({
        div: 'image_api_demo2',
        images: [
            'https://ids.lib.harvard.edu/ids/iiif/25286607'
            ],
        sizes: [
            '500,'
        ],
        regions: [
            'full',
            'max',
            'square',
            '1000,100,3000,2000',
            '2000,3000,2000,2000',
        ],
        rotation: [
            '90',
            '45',
            '135',
            '!135'
        ],
        highlight: [
            'rotation'
        ]
   });
</script>
