Générateur _serverless_ d'attestation dérogatoire de déplacement
================================================================

Éléments et bibliothéques incorporés à cette page
-------------------------------------------------

*   PDF-LIB ([pdf-lib.js.org/](https://pdf-lib.js.org/))
*   qrjs2 ([github.com/englishextra/qrjs2](https://github.com/englishextra/qrjs2))
*   Morceaux de code du générateur officiel d'attestation dérogratoire de déplacement ([media.interieur.gouv.fr/deplacement-covid-19/](https://media.interieur.gouv.fr/deplacement-covid-19/))
*   `getAllUrlParams` (modifié) ([gist.github.com/juanbrujo/fbc26b73fdad17605b5ba7d5922b44e4](https://gist.github.com/juanbrujo/fbc26b73fdad17605b5ba7d5922b44e4))
*   PDF de l'attestation dérogratoire de déplacement (en base64)

Données et vie privée
---------------------

Aucune donnée ne quitte votre appareil. C'est votre navigateur qui fait toutes les actions qui permettent la génération du PDF, de la récupération des informations au téléchargement du fichier. Vous avez la possibilité d'inspecter le code source de la page pour vous en assurer, tout est ici.  
Si vous en cherchez une preuve, coupez votre connexion internet et générez un PDF.

Comment l'utiliser
------------------

Dans l'URL, ajoutez `?` puis les différents paramètres séparés par des `&` sous la forme `parametre=valeur`.  
Exemple : `.../attestation.html?firstname=Jean&lastname=Jacques`

**Si un paramètre n'est pas fourni, c'est sa valeur par défaut qui sera utilisée.**  
Une fois l'URL complétée avec vos valeurs, accèdez à la page, le téléchargement de votre attestation se fait automatiquement.

Liste des paramètres
--------------------

*   Nom : `lastname` (par défaut "`Dupont`")
*   Prénom : `firstname` (par défaut "`Camille`")
*   Adresse : `address` (par défaut "`999 avenue de France`")
*   Ville : `city` (par défaut "`Paris`")
*   Code postal : `zipcode` (par défaut "`75001`")
*   Date de naissance : `birthday` (par défaut "`01/01/1970`")
*   Ville de naissance : `placeofbirth` (par défaut "`Lyon`")
*   Date de sortie : `datesortie` (par défaut la date actuelle sauf en cas d'antidate où la valeur est celle de l'antidate ; format `_dd_/_MM_/_yyyy_`)
*   Heure de sortie : `heuresortie` (par défaut l'heure actuelle sauf en cas d'antidate où la valeur est celle de l'antidat ; format `_hh_:_mm_`)
*   Raison du déplacement : `raison` (par défaut "`0`") **Impossible de combiner plusieurs raisons**
  0.  `travail`
  1.  `achats`
  2.  `sante`
  3.  `famille`
  4.  `handicap`
  5.  `sport_animaux`
  6.  `convocation`
  7.  `missions`
  8.  `enfants`
*   Antidate : `antidate` (par défaut "`0`")

**Toute valeur incorrecte peut provoquer des choses étranges.**

Antidate
--------

Cette fonctionnalité permet d'antidater l'attestation (notamment au niveau du QRCode) la valeur à mettre est le nombre de minutes qui doivent être retranchées à l'heure actuelle.  
Exemple : (il est 18:45) `.../attestation.html?firstname=Jean&lastname=Jacques&antidate=6`, l'attestation sera datée à 18:39

**Si cette valeur est négative, l'attestation sera post-datée.**
