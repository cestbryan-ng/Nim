# Nim avec un agent basé sur le Q-learning

Jeu de Nim en console où le joueur affronte une intelligence artificielle. L'agent apprend à choisir ses coups en jouant plusieurs parties contre lui-même avant le début de la partie.

## Fonctionnalités

- Quatre piles contenant initialement **1, 3, 5 et 7 jetons**.
- Retrait d'un ou plusieurs jetons d'une seule pile à chaque tour.
- Choix aléatoire du joueur qui commence.
- Entraînement de l'IA par Q-learning avant la partie.
- Affichage des piles et du gagnant dans la console.

## Comment jouer

1. Lance le programme et attends la fin de l'entraînement de l'IA (`Done training`).
2. À ton tour, repère les piles affichées et entre l'indice de la pile à jouer. Les indices commencent à `0`.
3. Entre le nombre de jetons à retirer de cette pile.
4. Continue à jouer à tour de rôle avec l'IA jusqu'à la fin de la partie.

Exemple de coup :

```text
Piles:
Pile 0: 1
Pile 1: 3
Pile 2: 5
Pile 3: 7

Your Turn
Choose Pile: 3
Choose Count: 2
```

Ici, le joueur retire 2 jetons de la pile 3. Le coup est accepté si l'indice de pile existe et si le nombre choisi est compris entre `1` et le nombre de jetons présents dans cette pile. Une saisie invalide est refusée et le programme redemande un coup.

La partie s'arrête lorsque toutes les piles sont vides ; le résultat est ensuite affiché.

## Algorithme de l'IA

L'agent utilise une table Q qui associe les configurations de piles et les coups possibles à une valeur estimée. Pendant l'entraînement, il joue contre lui-même et ajuste ces valeurs selon les résultats. Sa stratégie epsilon-greedy lui permet d'essayer parfois des coups aléatoires, puis de privilégier les coups évalués comme les meilleurs.

## Installation et lancement

```bash
python play.py
```

Le script entraîne l'IA sur 10 000 parties avant de démarrer la partie interactive. L'entraînement affiche la progression dans la console et peut prendre un moment.
