# Liste des fonctions et explications de leurs fonctionnement

## Note:
Il y a eu des changements radicaux dans le code, je n'ai donc pas eu le temps de tout retranscrire. 
Les fonctions suivantes sont issues de la version précédente de notre code.


### Classes 
    -Batiment(norme:int,rési:int,hauteur:int,etat:float,coords:tuple)

    -Vague(magnitude:int ,coords:tuple)-> [magnitude:int ,hauteur:int ,pression:float ,coords:tuple]


### Construction pour la ville

    -getnorme(moy,ecart_type): 
    Permet de générer une norme pour la création d'un batiment. Cette norme est issue de la moyenne (de la ville), et de l'écart à la moyenne (inégalité au sein de la ville)
    -getresi(norme): 
    Permet de générer une résistance à partir de la norme (de manière cohérente)
    -gethauteur(norme):
    Permet de générer une hauteur aléatoire dans un préset selon la norme (pour la cohérence de la norme)



    -aff(objet,taillex,tailley,what): 
    fonction de visualisation, elle permet de visualiser les ."what" en tout points d'un objet(de taille taillex,tailley)
    -liste_voisins(coords:tuple,taille:int): 
    permet de calculer les coordonnées des voisins d'une case (utilisée pour les profondeurs de la mer


### Fonction principale
#### genBoard(taille_ville:int ,taille_littoral:int ,taille_mer:int ,norme_moyenne:int ,nb_bats:int,nb_civils:int,infos_murs:list,profondeur_max):
	return un tuple (matrice environnement, matrice civile)

	permet de générer une matrice environnement, composée de la manière suivante:
	-de taille taille_ville sur y (nb lignes)
	-de taille taille_ville+taille_littoral+taille_mer sur x (nb élement par lignes)

	Dans cette matrice, les taille_ville premiers élements représentent la ville, ce sont des éléments de classe Batiment lorsqu'il y a un bâtiment à ces coords 0sinon.
	Pour construire cela, on utilise les paramètres taille_ville, norme_moyenne, nb_bats.
	La ville a donc pour taille taille_ville, une norme moyenne permettant de calculer les normes de chaque bâtiments et nb_bats le nb de bâtiments à poser, on présuppose arbitrairement les inégalités dans la ville à "2"
	afin d'avoir des variations dans le paysage, sans pour autant s'engager sur trop de paramètres, qui rendrait le code encore + confus.
	(la ville est donc stockée dans board[i][:taille_ville])



	Nous avons ensuite dans l'environnement la partie littoral. 
	matrice de taille [taille_ville][taille_littoral]
	Pour la construire, nous utilisons taille_littoral, pour en définir l'épaisseur, et infos_mur.
	infos_mur est une liste, dans laquelle on met si l'on souhaite en avoir des informations sur le(s) mur(s) selon le modèle suivant:
	[[(coords y départ, épaisseur mur),(hauteur x départ, taille du mur),hauteur,resistance],[idem pour le mur2]].
	(Cette partie est conservée dans board[i][taille_ville:taille_ville+taille_littoral])

	Enfin nous avons dans la dernière partie de la matrice environnement la mer.
	pour la mer, on utilise taille_mer, pour en set la longueur (donc de taille [taille_ville][taille_mer].
	et on utilise la variable profondeur_max pour set la profondeur maximale atteinte.
	Ensuite la matrice est initialisée avec des valeurs dynamique jusqu'à atteindre la profondeur maximale tout à droite (profondeur atteinte).
	Ces valeurs sont prises par rapport à leurs voisins, donc pas tout à fait linéaire, ce qui fait un sol marin un petit peu irrégulier (réalisme)

	La matrice civile quant à elle est de même dimension que la partie civile de la matrice environnement, et elle contient des civils jusque là placer aléatoirement dans des coordonnées ayant des bâtiments placés (on prévoit de les placer selon des places disponibles plus réaliste et de placer les autres dehors, mais on verra avec le temps)
	Pour la générer, on utilise donc la partie ville de la matrice environnement.
	Et nb_civils, pour savoir le nombre de civil à placer. 




### Tsunami 
    -distance(a:tuple,b:tuple):
	    permet de calculer la distance euclidienne entre 2 points 2 dimensions
	    sera peut-être utilisé pour la vague, (distance épicentre)


    -hauteur_max(magnitude):
	    étant donné que l'on suit l'échelle d'Imamura, la hauteur de la vague est définie par la magnitude choisie.
	    alors cette fonction permet de générer(avec un peu de rdm) la hauteur MAX de la vague arrivant au côte selon la magnitude (selon l'échelle d'Imamura)


    -Tsunami3(board,taille_ville,taille_littoral,taille_mer,magnitude):
	    fonction modélisant le tsunami.

	    fonction qui crée une matrice Vague de même dimension que board
	    dans cette matrice, on calcule puis stocke les informations du tsunami par coordonnées (hauteur, vitesse, force...) par coordonnées.
	    Elle est donc remplie d'élément de classe Vagues, et pour l'instant on ne conserve que la hauteur (faut de savoir calculer les chocs autrement pour le moment).

	    Ainsi elle retourne pour l'instant une matrice, avec dans Vague pour les coordonnées correspondant à la mer dans board, la hauteur des vagues. (calculée selon Imamura pour la plus grande, et un calcul arbitraire selon l'échelle des houles par Percy Douglas (car le calcul de l'amplitude pour un tsunami est trop complexe)

	    -tsunami4(board,taille_ville,taille_littoral,taille_mer,magnitude):
	    pareil que tsunami 3 mais les vagues sont placés à la place de la mer
  
### Collision
    -choc(coords:tuple,ville,vague,mcivil):
    fonction qui permettra à terme de simuler une collision à l'emplacement coords.
    Cette collision résultera en une destruction du batiment si:
      -la vague est plus grande que le batiment (quelque soit la norme)
      -la vague est + forte que ce que peut supporter le batiment (par la norme)
      -si la résistance restante est plus faible que la force de la vague (résistance par poids du matériaux face à l'Energie de la vague convertie en Newton) (à faire)
    Lorsqu'il y a destruction, on "tue" les habitants de cette case.


    Ainsi si l'on manipule bien cette fonction, on pourra avoir au final un taux de destruction, de mort et ptt de budget.

	(force et resistance en MPA)
	-tsunami(ville,taille,mat_civil,nb_civil_total):
		ville: matrice de l'environnement, avec la ville, le littoral et la mer(ayant les caractéristiques de la vague)
		taille: taille de la matrice 
		mat_civil: matrice avec les civils stocké dans des cases
		nb_civil_total: nb de civil dans la ville
	
	Cette fonction permet de calculer en tout point de la ville, l'impact entre une vague ayant des caractéristiques (hauteur et pression (déduit dans la classe vague de la force)) et un batiment ayant pour caractéristiques (resistance,hauteur). 
	Le résultat de cette rencontre est le suivant:
		
		-Cas où la vague est plus grande que 100% du bâtiment: on détruit 100% du batiment, et on tue tout les civils. La vague perd en "force"(on soustrait à la pression la resistance du batiment, et on baisse la hauteur selon le pourcentage perdu)
		-Cas où la force vague est presque similaire à la résistance du bâtiment: On déduit un pourcentage entre les 2, et on va détruire le batiment à ce pourcentage, tuant ce même pourcentage de civil. On affaiblit ensuite la vague du même pourcentage (sa hauteur et sa pression)
		-Cas où la vague est strictement plus faible (donc moins de pression ET moins haute) que le bâtiment: 
	


### à faire: 
	-fonction attribuant un prix aux bâtiments selons leurs normes/hauteurs etc 
	-finaliser choc
	-fonction d'analyses...



# Sum Up: les paramètres modifiables:

	-taille de la ville	(taille_ville)
	-norme_moyenne de la ville (norme_moyenne)
	-inégalité dans la ville (pas sous forme de variable)
	-nb_batiment dans la ville (nb_bats)
	-taille du littoral	(taille_littoral)
	-taille de la mer	(taille_mer)
	-profondeur maximale de la mer	(profondeur_max)
	-nb de civil présent (nb_civil)
	-Magnitude du Tsunami (magnitude)
	-
	
	à ajt: 
	-budget_max ?  requiert de refaire la fonction ville à 0 :/
	-placer les civils dans les batiments en fonction de la place dispo dans le bat  ?(calc nb étage par la hauteur/3.3 et surface par étage predef) le reste reste dans la rue et meurent (+réaliste)
	-





















