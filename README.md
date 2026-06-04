# Exercice 6 - Héritage `static`

Ce projet Java montre la difference entre un champ `static` et un champ non statique.

## Objectif

Créer une classe `Personne` avec deux compteurs :

- `nbInstances` : compteur `static`, partagé par toutes les instances de la classe.
- `nbLocal` : compteur non statique, propre à chaque objet `Personne`.

Les deux compteurs sont incrémentés dans le constructeur.

## Structure du projet

```text
src/
  Main.java
  Personne.java
```

## Classe `Personne`

```java
public class Personne {
    public static int nbInstances;
    public int nbLocal;

    public Personne() {
        nbInstances++;
        nbLocal++;
    }
}
```

## Programme principal

Dans `Main.java`, on crée quatre instances de `Personne` :

```java
Personne personne1 = new Personne();
Personne personne2 = new Personne();
Personne personne3 = new Personne();
Personne personne4 = new Personne();
```

Puis on affiche :

```java
System.out.println("(" + personne4.nbLocal + "," + Personne.nbInstances + ")");
```

## Résultat attendu

```text
(1,4)
```

Explication :

- `personne4.nbLocal` vaut `1`, car `nbLocal` appartient uniquement à l'objet `personne4`.
- `Personne.nbInstances` vaut `4`, car `nbInstances` est partagé par toutes les instances et a été incrémenté quatre fois.

## Compiler et exécuter

Depuis la racine du projet :

```powershell
javac .\src\Personne.java .\src\Main.java
java -cp .\src Main
```

## Sortie complète

```text
(1,4)
personne1.nbLocal = 1
personne2.nbLocal = 1
personne3.nbLocal = 1
personne4.nbLocal = 1
Personne.nbInstances = 4
```
