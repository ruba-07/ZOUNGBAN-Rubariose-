QUESTION 1 : Représentation précise et formelle des états présent dans l'espace 

Soit S un état étant la quantité d’eau dans chaque cruche.
s=(x,y)
Avec : 
0 ≤ x ≤ 3
0 ≤ y ≤ 5
L’espace d’états est :S={(x,y)∣x∈{0,…,3},y∈{0,…,5}}
État initial :S0​=(0,0)
État objectifs : y=4 

QUESTION 2 : Modélisation formelle et précise pour le problème 

1- États 
- s=(x,y)x∈{0..3},y∈{0..5}
  
- États intial :s0​=(0,0)
  
- États des objectifs : G:y=4
  
- Actions : A ( x,y)
a1. Remplir x = (3,y)

a2. Remplir y = ( x,5)

a3. Vider x = (0,y)

a4.Vider y =(x,0)

a5. Verser x dans y (x,y)=(x−min(x,5−y),y+min(x,5−y))

a6. Verser y dans x (x,y)=(x+min(y,3−x),y−min(y,3−x))

- 5. Fonction de succession
Succ ( S,a) = S+ A 
Succ(x,y)={
(3,y),
(x,5),
(0,y)si x>0,
(x,0)si y>0,
(x−min(x,5−y),y+min(x,5−y)),
(x+min(y,3−x),y−min(y,3−x))}

QUESTION 3 : Taille de l’espace de recherche

La cruche 3 L peut contenir 4 quantités
La cruche 5 L peut contenir 6 quantités  
∣S∣=4×6=24
L’espace d’états total contient 24 états possibles.

QUESTION 4 : Dessin du graphes 
seules les transitions utiles vers la solution sont représentées
(0,0)→(3,0)
(3,0)→(0,3)
(0,3)→(3,3)
(3,3)→(1,5)
(1,5)→(1,0)
(1,0)→(0,1)
(0,1)→(3,1)
(3,1)→(0,4)

L’état objectif est atteint : (0,4)

QUESTION 5:  Meilleure solution (chemin optimal)

Pour minimiser le nombre d’actions, on suit le plus court chemin dans le graphe :

Remplir x → (3,0)

Verrser x dans y  → (0,3)

Remplir x  → (3,3)

Verser x dans y → (1,5)

Vider y → (1,0)

Verser 1 L de x vers y → (0,1)

Remplir x → (3,1)

Verser x dans y → (0,4) 

Nombre total d’actions : 8 (optimal)
