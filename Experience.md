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


Conclusion: 
-Un mur de résistance maximale permet bien de sauver des infrastructures et des vies humaines, mais cependant il pert de son efficacité face aux tsunami  de magnitudes 3 et 4.






