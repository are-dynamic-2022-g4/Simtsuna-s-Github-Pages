## Expériences à réaliser:
-Pour 1 même magnitude de vague:
	-taux de destructions de la ville par rapport à la norme moyenne instaurée.
	-taux de morts par rapport à la norme moyenne.
	-taux de morts par rapport au budget dépensé ? 

-Pour 1 même vague et une même ville: 
	-impact des défenses (une différence ?)
	-taux de destructions & morts par rapport aux défenses implantées (coût des défenses ?).

-Pour 1 norme moyenne de ville || 1 budget moyen:
	-taux de destructions &/ou morts par rapport à différentes magnitudes de tsunami.


# Expéricences réalisées: 

## Expérience 1:

Moyenne de destruction (sur 100 répétitions) d'une même ville, face aux différentes magnitudes d'un tsunami.
![taux_destruction](https://user-images.githubusercontent.com/101204424/164016936-7e122b77-b9d2-41f5-9e04-ef409e2712e1.png)



## Expérience 2:
![image](https://user-images.githubusercontent.com/101204424/164679547-d6d31878-4087-44ab-9201-f81afa060ef4.png)

Il faut d'abord noter que les données les plus à gauche sont à ne pas prendre en compte car elles proviennent de la limite de nôtre code: nous générons les villes aléatoirement, ce qui fait que des fois, la ville peut-être partiellement détruite par des vagues de magnitude 0 dans des conditions très précises (la ville est composée du matériaux le plus faible (que de briques)).

On observe que les taux de civils morts ET de destruction de la ville baissent considérablement lorsqu'il y a un mur (ici de résistance 5(max)). Cela signifie que le mur permet effectivement de sauver des civils et des bâtiments.

Ensuite, nous pouvons observer une corrélation entre le taux de destruction et la proportion de civil morts. Cela s'explique par la manière dont nous les avons implentés dans le code. Nous plaçons des civils dans des batiments, et lorsque ceux-ci sont détruit à un certain pourcentage on tue le même pourcentage de civil (dur de trouver une manière plus réaliste sans tuer tout le monde). Ainsi lorsqu'un batiment est détruit à 50% alors 50% des civils du batiments meurent.

On observe aussi par les courbes jaune et rose, la limite de notre mur. On note que le pourcentage de la population sauvée (qui était croissante jusque là) décroit pour les magnitudes 3 et 4. On voit aussi que le taux de destruction augmente "sèchement"// nettement plus. 
De cela nous pouvons interpréter le "point" à partir duquel notre mur( de résistance 5, le plus résistant) perd de son efficacité. Cela signifie qu'un tel mur (qui coûte cher) est beaucoup moins éfficace pour les magnitudes 3 et 4.


### Conclusion: 
Un mur de résistance maximale permet bien de sauver des infrastructures et des vies humaines, mais cependant il pert de son efficacité face aux tsunami  de magnitudes 3 et 4.


## Expérience 3: Taux de destruction en fonction du budget de la ville (en million): 

*nous n'avons malheuresement pas pu faire varier le budget de la ville, car nous n'avons pas implémenté ce paramètre dans ce code, on reste donc sur un même budget (== même ville) mais face à des tsunamis de magnitudes différentes)

**Magnitude 4**
![image](https://user-images.githubusercontent.com/101204424/164708511-eae3352a-1745-4b86-8dab-8413fac43bc7.png)
On observe ici la taux de destruction d'une même ville face à un tsunami de magnitude 4, selon le budget d'une ville de 50 bâtiments.
On note que le taux de destruction fluctue, mais qu'il reste entre 52 et 56%. On peut en tirer l'affirmation suivante: Une ville de 50 bâtiments ayant un budget entre 205 et 210 million d'euros subira en moyenne 53% de destruction face à un tsunami de magnitude 4.

**Magnitude 3**
![image](https://user-images.githubusercontent.com/101204424/164708558-7a075dd4-cba1-4514-bccf-08e0cffd1a34.png)
On note que le taux de destruction fluctue cette fois entre 28 et 34% pour ce même budget face à un tsunami de magnitude 3.
Ainsi on en déduit qu'une ville de 50 bâtiments ayant un budget entre 200 et 210 million sera détruite en moyenne de 50% face à un tsunami de magnitude 3. 

**Magnitude 2**
![image](https://user-images.githubusercontent.com/101204424/164708786-dc9da05b-ca72-4169-a512-88ad08653a23.png)
De même face aux tsunamis de magnitude 2, le taux de destruction varie entre 15 et 16%  (il y plus de point car nous avons éffectué plus de calcul pour moyenner les résultats avec plus de précision).

**Magnitude 1**
![image](https://user-images.githubusercontent.com/101204424/164708927-cf7630cf-7e02-42c2-a979-428bed9cd936.png)
Idem pour les tsunamis de magnitude 1

**Remarque** 
En dessous de la magnitude 2, les vagues atteignent au maximum 2 mètres, et ne devraient pas causer tant de dégâts (10 à 15% de destruction). Cependant comme expliqué précédemment, cela provient de la manière de générer la ville, il suffit qu'un seul élément "faible" (du au hasard) pour détruire une fraction de la ville. (n'ayant "que" 50 batiments, 10 bâtiments détruit par ce hasard représentent déjà 20%).


### Conclusion: avec un budget de 210 millions en moyenne pour une ville de 50 bâtiments, (soit des bâtiments en bois en moyenne), une ville peut résister jusqu'à un tsunami de magnitude 2, avant d'être détruite dans des proportions considérables (30+% pour les tsunamis de magnitude 3+).








