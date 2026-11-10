# Nim - Apprentissage par renforcement avec Q-learning

Ce projet implémente le jeu de Nim avec un agent d'intelligence artificielle entraîné par apprentissage par renforcement, plus précisément par la méthode Q-learning. L'objectif est que l'IA apprenne à jouer au mieux en explorant les états du jeu et en maximisant ses récompenses à long terme.

## Description du projet

Nim est un jeu de logique simple :
- plusieurs piles contiennent un nombre de jetons,
- à tour de rôle, un joueur retire un ou plusieurs jetons d'une seule pile,
- le joueur qui prend le dernier jeton gagne la partie.

Dans ce projet, l'IA apprend à choisir les meilleurs coups à partir d'un grand nombre de parties jouées contre elle-même.

## Fonctionnement du modèle

Le code utilise une table Q pour associer chaque état et chaque action à une valeur estimée :
- état : configuration actuelle des piles,
- action : retirer `j` jetons de la pile `i`,
- récompense : positive si la partie est gagnée, négative si elle est perdue, nulle sinon.

L'algorithme applique la stratégie epsilon-greedy :
- avec une faible probabilité, l'IA explore un coup aléatoire,
- sinon, elle choisit le coup ayant la meilleure valeur Q connue.

## Structure du projet

- `nim.py` : contient la logique du jeu, l'agent Q-learning et la boucle d'entraînement.
- `play.py` : lance l'entraînement puis permet de jouer contre l'IA.
- `README.md` : documentation du projet.

## Règles du jeu

Une partie se déroule ainsi :
1. Le jeu démarre avec une configuration initiale de piles.
2. Le joueur actif choisit une pile et le nombre de jetons à retirer.
3. Le coup est validé uniquement si la pile contient assez de jetons.
4. Le dernier jeton retiré détermine le gagnant.

## Prérequis

- Python 3.9+
- aucune dépendance externe n'est requise

## Installation

```bash
python play.py
```

## Utilisation

### Lancer une partie contre l'IA

Le fichier `play.py` entraîne automatiquement l'IA puis lance une partie interactive :

```python
from nim import train, play

ai = train(10000)
play(ai)
```

### Modifier le nombre d'itérations d'entraînement

Dans `play.py`, tu peux ajuster le nombre de parties utilisées pour l'apprentissage :

```python
ai = train(10000)
```

Plus ce nombre est élevé, plus l'IA a de chances d'apprendre une stratégie solide.

## Points clés de l'implémentation

### Classe `Nim`
La classe `Nim` gère :
- l'état du plateau,
- le tour du joueur,
- la détection du gagnant,
- les actions possibles à partir d'un état donné.

### Classe `NimAI`
La classe `NimAI` gère :
- la table Q,
- la mise à jour des valeurs Q,
- le choix des meilleures actions,
- l'exploration aléatoire via epsilon.

### Fonction `train(n)`
Cette fonction :
- crée un nouvel agent,
- joue `n` parties autonomes,
- met à jour la table Q après chaque coup,
- retourne l'agent entraîné.

### Fonction `play(ai, human_player=None)`
Cette fonction permet :
- de jouer contre l'IA,
- de choisir si l'humain commence ou non,
- de visualiser les piles restantes et les coups possibles.

## Exemple de gameplay

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

L'IA répond ensuite en jouant son propre coup selon son apprentissage.

## Objectif pédagogique

Ce projet est un excellent exemple d'apprentissage par renforcement appliqué à un jeu discret. Il montre de manière simple :
- comment modéliser un jeu comme un problème de décision,
- comment représenter les états et les actions,
- comment utiliser une table Q pour apprendre des stratégies efficaces,
- comment tester le comportement appris face à un joueur humain.
