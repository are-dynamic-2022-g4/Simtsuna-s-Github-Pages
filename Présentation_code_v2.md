# Sum up
Les variables que l'on peut modifier dans le code, pour agir sur l'environnement sont:

    -Taille de l'environnement(dont 2/3 seront dédié à la ville, 1tier pour la mer et la dernière colonne de la ville est remplacée par du littoral)
    -Densité pour la population (agit sur le nombre de civil)
    -Force/Magnitude de la vague (agit sur la hauteur et pression exercé par la vague)
    -Nombre de vagues (représente la "gravité du tsunami)
    -Type de protection posé (pour le même emplacement) : (agit sur les protections de la ville) 
    -
Ce qu'on arrive à tirer des résultats:

    -Nombre de morts avec et sans mur
    -Nombre de bâtiments détruit avec et sans mur
    -état global de la ville en %tage avec et sans mur
    -moyenne des matériaux et hauteurs utilisés dans la ville
    -hauteur de la vague par la magnitude utilisée



# Justification: 
    -on suppose qu'une case de la ville fait ~100m2 (pour les calculs)
    -On suppose que la ville est déjà construite, et qu'on ne peut pas modifier la taille du littoral et que donc les protections s'adaptent à la taille du littoral et pas l'inverse (on ne manipule donc pas la taille du littoral contrairement à ce qui était prévu initialement.
    -On place des bâtiments partout (pas de nombre de batiments) car on considère qu'il n'y a pas de grands espaces vide dans notre ville (pas de parc) (par exemple à paris, il y a presque forcément une habitation par 100m2
    -Force/magnitude des vagues sont données selons l'échelle d'Imamura et Iida, car ce qui nous intéresse est de voir définir l'échelle de résistance de nos protection (face à quelle magnitude de tsunami sont-elle éfficace ?)
    
    -On ne fait pas jouer de normes moyennes et d'écart à la moyenne (inégalités) car nous n'avons pas eu le temps de le traduire et de l'adapter pour ce code (marche dans l'ancien).
    -On n'utilisera pas non plus la profondeur de la mer, pour les mêmes raisons 
    
    
    







