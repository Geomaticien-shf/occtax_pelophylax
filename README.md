# Contexte

Les Pelophylax sont des taxons difficiles à déterminer.
Aussi, il est parfois nécessaire de récolter des informations complémentaires, à la fois sur le milieu d'observation, sur l'observateur et sur l'observation en elle-même.

Pierre-André CROCHET avait réalisé un protocole (sans coordination/animation au niveau national par la SHF) pour l'identification des Pelophylax. Notamment, avec l'enregistrement des chants et la prise de photos, pour pouvoir déterminer les taxons.

La SHF travaille avec l'outil GeoNature. En 2020, elle a donc fait le choix d'enrichir le formulaire de saisie "OccTax", pour un jeu de données spécifique dédié à la collecte des données de Pelophylax. Cela correspondait à l'implémentation de ce "protocole". Ce développement repose sur deux aspects :
- des champs additionnels ont été ajoutés pour ces attributs non standards. Ces ajouts se font à travers l'interface "Admin" de GeoNature ([cf documentation de GeoNature sur l'ajout de champs additionnels](https://docs.geonature.fr/admin-manual.html#administration-des-champs-additionnels)).
- la SHF a ajouté un "pseudo-module" pour qu'un raccourci soit créé et accessible depuis le menu de gauche, sur GeoNature. C'est simplement un lien vers le module de saisie "OccTax" qui pointe directement sur le bon jeu de données ([cf issue à ce sujet](https://github.com/PnX-SI/GeoNature/issues/1071))

# Implémentation des champs

**ATTENTION** Les URLs des médias ne sont pas bonnes dans la suite du document : à terme, les médias seront intégrés au dépôt, et il faudra les déployer (URLs relatives, ou absolues publiées sur le site de la SHF). Mais dans l'attente de la publicaiton du protocole, ces URLs ne sont pas définitives.

## Liés aux relevés
3 champs de saisie rattachés au relevé (contexte des observations) :
![Pasted image 20240618121746](https://github.com/Geomaticien-shf/occtax_pelophylax/assets/170406939/9a00c72b-7f40-4407-b91d-102f64d832ab)

Informations en commun :
- Modules : Saisie OccTax
- Objects : OCCTAX_RELEVE (pr_occtax.t_releves_occtax)
- Datasets : Le jeu de données que vous aurez créé, spécifique aux Pelophylax
- Obligatoire : Non
### Expertise
- Nom du champ : expert_level
- Label du champ : Expertise
- Type Widget : Select (choix simple)
- Description : Niveau d'expertise
- Quantitatif : Non
- Valeurs : ["Débutant", "Expérimenté", "Chevronné"]
- Ordre : 1
- Exportable : Oui

### Catégorie paysagère
- Nom du champ : landscape_category
- Label du champ : Catégorie paysagère
- Type Widget : Select (choix simple)
- Description : Description de la catégorie paysagère du relevé
- Quantitatif : Non
- Valeurs : ["Eaux continentales", "Eaux maritimes", "Zones urbanisées", "Zones industrielles ou commerciales et réseaux de communication", "Prairies", "Mines, décharges et chantiers", "Espaces verts artificialisés, non agricoles", "Terres arables", "Forêts", "Cultures permanentes", "Zones agricoles hétérogènes", "Milieux à végétation arbustive et/ou herbacée", "Espaces ouverts, sans ou avec peu de végétation", "Zones humides intérieures", "Zones humides maritimes"]
- Ordre : 2
- Exportable : Oui

### Description du milieu aquatique
- Nom du champ : wet_zone_description
- Label du champ : Description du milieu aquatique
- Type Widget : Select (choix simple)
- Description : Description du milieu aquatique
- Quantitatif : Non
- Valeurs : ["Source", "Ruisselet / Ruisseau (< 3m de large)", "Rivière (3 à 10m de large)", "Grand cours d'eau (> 10m de large)", "Canal navigable", "Marais saumâtre", "Mare (< 50m²)", "Étang (50 à 450m²)", "Fossé", "Marais / tourbière", "Lac / grand réservoir", "Milieu aquatique cultivé", "Prairie humide", "Estuaire"]
- Ordre : 3
- Exportable : Oui

## Liés à l'observation
2 champs rattachés à l'occurrence (observation du taxon) : un d'information et un de saisie
![Pasted image 20240618121712](https://github.com/Geomaticien-shf/occtax_pelophylax/assets/170406939/cb0a681f-e172-4764-b4fb-935d66530834)

Informations en commun :
- Modules : Saisie OccTax
- Objects : OCCTAX_OCCURENCE (pr_occtax.t_occurrences_occtax)
- Datasets : Le jeu de données que vous aurez créé, spécifique aux Pelophylax
- Obligatoire : Non
### Avertissement occurrence
- Nom du champ : info_genius
- Label du champ : Modalités de saisie
- Type Widget : Html
- Description : Informations sur les modalités de saisie
- Quantitatif : Non
- Valeurs : {}
- Ordre : 1
- Exportable : Non
- Attribut additionnel : 
```html
{"html": "<div class=\"alert alert-warning\">Jusqu'à détermination par un expert, les Pélophylax doivent être saisies uniquement au Genre sous le nom <strong>Pelophylax =   Pelophylax Fitzinger, 1843 - [GN - 444436]</strong>.</div>"}
```
### Dérogation
- Nom du champ : exemption_number
- Label du champ : Numéro de la dérogation de capture
- Type Widget : Text
- Description :
- Quantitatif : Non
- Valeurs : {}
- Ordre : 2
- Exportable : Non

## Liés au dénombrement
4 champs rattachés au dénombrement (observation d'un individu / ponte / ...) : deux d'information et deux de saisie
![Pasted image 20240618121656](https://github.com/Geomaticien-shf/occtax_pelophylax/assets/170406939/f3be9404-2483-482a-be75-9ec14e18d61a)

Informations en commun :
- Modules : Saisie OccTax
- Objects : OCCTAX_DENOMBREMENT (pr_occtax.cor_counting_occtax)
- Datasets : Le jeu de données que vous aurez créé, spécifique aux Pelophylax
- 
### Avertissement prélèvement ADN
- Nom du champ : dna_sampling_detail
- Label du champ : Détails sur le prélèvement ADN
- Type Widget : Html
- Obligatoire : Non
- Description :
- Quantitatif : Non
- Valeurs : {}
- Ordre : 1
- Exportable : Non
- Attribut additionnel:
```html
"html": "<div class=\"alert alert-warning\">Informations sur le prélèvement ADN :<div><a data-toggle=\"collapse\" href=\"#infoprelev\" role=\"button\" aria-expanded=\"false\" aria-controls=\"infoprelev\"><i class=\"fa fa-question-circle\"></i>&nbsp;Afficher les informations complémentaires</a><div class=\"collapse\" id=\"infoprelev\"><img src=\"custom/images/prelev1.JPG\" alt=\"\" style=\"max-width:300px; max-height:300px\"></img><img src=\"custom/images/prelev2.JPG\" alt=\"\" style=\"max-width:300px; max-height:300px\"></img><img src=\"custom/images/prelev3.JPG\" alt=\"\" style=\"max-width:300px; max-height:300px\"></img><img src=\"custom/images/prelev4.JPG\" alt=\"\" style=\"max-width:300px; max-height:300px\"></img><br><br><p><strong>Les échantillons ADN sont à envoyer à l'adresse suivante :</strong><br>Pierre-André Crochet <br> UMR5175 CEFE <br> 1919 route de Mende <br> 34293 Montpellier cedex 5</p></div></div></div>"}
```
### Prélèvement ADN effectué
- Nom du champ : dna_sample
- Label du champ : Prélèvement ADN effectué
- Type Widget : Radio
- Obligatoire : Oui
- Description :
- Quantitatif : Non
- Valeurs : ["Vrai", "Faux"]
- Ordre : 2
- Exportable : Non

### Lieu de stockage ADN
- Nom du champ : dna_storage_location
- Label du champ : Lieu de stockage de l'ADN
- Type Widget : Text
- Obligatoire : Non
- Description :
- Quantitatif : Non
- Valeurs : 
- Ordre : 3
- Exportable : Oui

### Avertissement médias
- Nom du champ : media_notice
- Label du champ : Notice des médias attendus
- Type Widget : Html
- Obligatoire : Non
- Description : Détail des médias attendus
- Quantitatif : Non
- Valeurs :
- Ordre : 4
- Exportable : Non
- Attribut additionnel :
```html
{"html": "<div class = \"alert alert-warning\"> Liste des médias attendus :<div><a data-toggle=\"collapse\" href=\"#photo1\" role=\"button\" aria-expanded=\"false\" aria-controls=\"photo1\"><i class=\"fa fa-question-circle\"></i>&nbsp;Prise de vue générale avec l'individu en main à côté d'un papier avec le code de l'individu</a><div class=\"collapse\" id=\"photo1\"><img src=\"custom/images/vue_general.JPG\" alt=\"\" style=\"max-width:300px; max-height:300px\"></img></div></div><div><a data-toggle=\"collapse\" href=\"#photo2\" role=\"button\" aria-expanded=\"false\" aria-controls=\"photo2\"><i class=\"fa fa-question-circle\"></i>&nbsp;Prise de vue détaillée des palmures étendues de l'individu</a><div class=\"collapse\" id=\"photo2\"><img src=\"custom/images/palmure1.JPG\" alt=\"\" style=\"max-width:300px; max-height:300px\"></img><img src=\"custom/images/palmure2.JPG\" alt=\"\" style=\"max-width:300px; max-height:300px\"></img></div></div><div><a data-toggle=\"collapse\" href=\"#photo3\" role=\"button\" aria-expanded=\"false\" aria-controls=\"photo3\"><i class=\"fa fa-question-circle\"></i>&nbsp;Prise de vue détaillée du tubercule métatarsien de l'individu</a><div class=\"collapse\" id=\"photo3\"><img src=\"custom/images/tubercule.jpg\" alt=\"\" style=\"max-width:300px; max-height:300px\"></img></div></div><div><a data-toggle=\"collapse\" href=\"#photo4\" role=\"button\" aria-expanded=\"false\" aria-controls=\"photo4\"><i class=\"fa fa-question-circle\"></i>&nbsp;Prise de vue détaillée des bourrelets vomériens de l'individu</a><div class=\"collapse\" id=\"photo4\"><p>Pour ouvrir la bouche d'une grenouille, il est préférable d'utiliser un instrument (couteau pas trop pointu, critériumavec pointe plastique), ou une brindille. Pour procéder, tenir la grenouille face ventrale vers soi, placer l'outil dans lacommissure, et dès que la bouche s'ouvre glisser le pouce pour baisser la mâchoire inférieure. Pour prendre lecliché, il est plus simple d'être à deux: l'un tient la grenouille et l'autre prend la photo</p><img src=\"custom/images/bourrelet.jpg\" alt=\"\" style=\"max-width:300px; max-height:300px\"></img><img src=\"custom/images/bourrelet2.jpg\" alt=\"\" style=\"max-width:300px; max-height:300px\"></img><img src=\"custom/images/bourrelet3.jpg\" alt=\"\" style=\"max-width:300px; max-height:300px\"></img></div></div><div><a data-toggle=\"collapse\" href=\"#photo5\" role=\"button\" aria-expanded=\"false\" aria-controls=\"photo5\"><i class=\"fa fa-question-circle\"></i>&nbsp;Prise de vue détaillée de l'arrière des cuisses de l'individu</a><div class=\"collapse\" id=\"photo5\"><img src=\"custom/images/cuisse.JPG\" alt=\"\" style=\"max-width:300px; max-height:300px\"></img></div></div><div><a data-toggle=\"collapse\" href=\"#photo6\" role=\"button\" aria-expanded=\"false\" aria-controls=\"photo6\"><i class=\"fa fa-question-circle\"></i>&nbsp;Prise de vue détaillée de l'aine de l'individu</a><div class=\"collapse\" id=\"photo6\"><img src=\"custom/images/aine.JPG\" alt=\"\" style=\"max-width:300px; max-height:300px\"></img><img src=\"custom/images/aine2.JPG\" alt=\"\" style=\"max-width:300px; max-height:300px\"></img></div></div><div><a data-toggle=\"collapse\" href=\"#photo7\" role=\"button\" aria-expanded=\"false\" aria-controls=\"photo7\"><i class=\"fa fa-question-circle\"></i>&nbsp;Prise de vue d'ensemble en milieu naturel</a><div class=\"collapse\" id=\"photo7\"><img src=\"custom/images/naturel.JPG\" alt=\"\" style=\"max-width:300px; max-height:300px\"></img></div></div><div><a data-toggle=\"collapse\" href=\"#son1\" role=\"button\" aria-expanded=\"false\" aria-controls=\"son1\"><i class=\"fa fa-question-circle\"></i>&nbsp;Fichier audio</a><div class=\"collapse\" id=\"son1\"><p>Pour les enregistrements : à la fin de chaque enregistrement, parler dans le micro pour indiquer le lieu, la date etl'heure de prise de son.Pour enregistrer, il est important d'essayer d'avoirdes phrases longues ou \"excitées\" (ce qui peutnécessiter d'attendre un peu). Un chant aboutit à 2ou 3 phrases excitées, puis à une dernière, bâclée.Cette manière de chanter, si elle est enregistréedans sa totalité, est celle qui permet de déterminerles phrases excitées. Dans ces phrases, lescaractéristiques du chant sont plus marquées(augmentation du nombre de notes, phrasesrapprochées, volume plus fort) et les différencesentre les espèces s'en trouvent accrues. Il estpossible d'utiliser différents outils pour enregistrer:dictaphone, téléphone portable, appareil photo,etc. Dans tous les cas, tenir compte du fait que,plus les bruits de fonds sont importants (rainettes,vent, etc.), plus l'analyse du chant sera difficile.</p><img src=\"custom/images/son.jpg\" alt=\"\" style=\"max-width:300px; max-height:300px\"></img></div></div></div>"}
```
## Autres aspects techniques
- Une fois les champs ajoutés, il faut, comme pour tout jeu de données / module, accorder les permissions cohérentes par utilisateur et utilisatrice, pour permettre la saisie dans GeoNature.
- Faire une liste des taxons (Pelophylax) liée à ce jeu de données, éventuellement restreinte à votre périmètre géographique.
