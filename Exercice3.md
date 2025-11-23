QUESTION 1 : Modélisation formelle du problème du cavalier 

Considérons une grille n x n 
- Ensemble des états : 
Soit E cet état , E = (p,V) 
avec : - p = (x,y) 
       - 𝑉 ⊆ {1,...,n} × {1...,n}
 - Etat initial : 
  Eo = ((1,1),{ 1,1)}
 - Etat des objectifs :
     G = n^2
- Actions :
(+2, +1), (+2, -1),
(-2, +1), (-2, -1),
(+1, +2), (+1, -2),
(-1, +2), (-1, -2)

-Fonctions de succession : 
S=(x,y,V) un état 
où
(x,y) = position courante du cavalier
V = ensemble des cases déjà visitées
a=(dx,dy) ,une action

La fonction de succession est une fonction :

Succ:état ×Action

telle que :

Succ((x,y,V),(dx,dy))={
(x+dx,y+dy,V∪{(x+dx,y+dy)})}

Question 2 : Taille de l’espace d’états

Le cavalier doit visiter toutes les cases sans répétition.
une case:  𝑛 x 𝑚
un ensemble de cases visitées :2^nm
∣E∣=(n×m)⋅2^nm = (n × m)!

Question 3 :  méthodes manquantes


Méthode initialState()
public State initialState() {
    boolean[][] visited = new boolean[NB_ROWS][NB_COLS];
    visited[0][0] = true;
    return new State(0, 0, visited, 1);
}

 Méthode actions()
 
public List<Action> actions() {
    return List.of(
        new Action(2, 1), new Action(2, -1),
        new Action(-2, 1), new Action(-2, -1),
        new Action(1, 2), new Action(1, -2),
        new Action(-1, 2), new Action(-1, -2)
    );
}

Test de but

public boolean isGoalState(State state) {
    return state.visitedCount == NB_ROWS * NB_COLS;
}

Succession()

public State succession(State state, Action action) {
    int nx = state.x + action.dx;
    int ny = state.y + action.dy;

    if (nx < 0 || ny < 0 || nx >= NB_ROWS || ny >= NB_COLS)
        return null;

    if (state.visited[nx][ny])
        return null;

    boolean[][] newVisited = new boolean[NB_ROWS][NB_COLS];
    for (int i = 0; i < NB_ROWS; i++)
        newVisited[i] = state.visited[i].clone();

    newVisited[nx][ny] = true;

    return new State(nx, ny, newVisited, state.visitedCount + 1);
}	
​
QUESTION 4 :la recherche avec la modélisation proposée devient prohibitive vers 6×6 ou 7×7

QUESTION 5 : 

Question 6 — Tour fermé du Cavalier

 modification de  isGoalState :

public boolean isGoalState(State state) {
    if (state.visitedCount != NB_ROWS * NB_COLS)
        return false;

    // mouvement final doit revenir sur (0,0)
    for (Action a : actions()) {
        if (state.x + a.dx == 0 && state.y + a.dy == 0)
            return true;
    }
    return false;
}
