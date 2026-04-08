# Introduction à Jupyter et Python pour le calcul scientifique

---

## **1. Introduction aux notebooks Jupyter**

Un **notebook Jupyter** est un environnement interactif qui permet de combiner du **code**, du **texte formaté** (Markdown), des **équations mathématiques** et des **visualisations**.

### **Utilisation de base**

- **Double-clique** sur une cellule pour l'éditer.
- **Exécute** une cellule avec `MAJ+ENTRÉE` ou `CTRL+ENTRÉE`.
- **Change le type** de cellule (Code/Markdown) via le menu déroulant.
- **Formatage Markdown** :
  - `#` pour les titres, `-` pour les listes, `$...$` pour les équations LaTeX.

---

## **2. Premiers pas avec Python**

### **2.1. Types de base et variables**

En Python, tout est un **objet** avec un **type** :

- **Entiers** (`int`), **flottants** (`float`), **chaînes de caractères** (`str`), **booléens** (`bool`).

```python
a = 1          # int
b = 1.0        # float
c = 'char'     # str
d = True       # bool

print(type(a)) # Affiche <class 'int'>
```

- **Addition** : Python convertit automatiquement les types si possible.
  ```python
  print(a + b) # 2.0 (int + float = float)
  ```
- **Égalité** : Attention aux flottants (précision limitée) !
  ```python
  print(0.1 + 0.1 + 0.1 == 0.3) # False (0.30000000000000004 != 0.3)
  ```

---

### **2.2. Listes, tuples et dictionnaires**

- **Liste** : Collection ordonnée et modifiable.
  ```python
  l = [a, b, c, d]
  print(l[0]) # Affiche 1 (index 0)
  l[0] = 0.0  # Modification possible
  ```
- **Tuple** : Collection ordonnée et **immuable**.
  ```python
  t = (a, b, c, d)
  # t[0] = 0.0  # Erreur : les tuples ne sont pas modifiables !
  ```
- **Dictionnaire** : Collection de paires `clé:valeur`.
  ```python
  dic = {'weight': 12.3, 'height': 50.9}
  print(dic['weight']) # Affiche 12.3
  ```

---

### **2.3. Boucles et tests**

- **Boucle `for` :**
  ```python
  for i in [a, b, c, d]:
      print(i)  # Indentation obligatoire !
  ```
- **`range`** : Génère une séquence d'entiers.
  ```python
  for i in range(4):  # 0, 1, 2, 3
      print(i)
  ```
- **Tests conditionnels** :
  ```python
  for i in [a, b, c, d]:
      if type(i) == int:
          print(f"{i} est un entier")
      else:
          print(f"{i} n'est pas un entier")
  ```

---

### **2.4. Fonctions**

- **Définition** avec `def` :
  ```python
  def double(x):
      return x + x

  print(double(a))  # Affiche 2
  ```
- **Portée des variables** :
  ```python
  def shift(x):
      return x + e  # Erreur si `e` n'est pas défini !

  e = -3
  print(shift(a))  # Affiche -2
  ```

---

## **3. Bibliothèque NumPy**

NumPy permet de manipuler des **tableaux multidimensionnels** et d'effectuer des calculs scientifiques efficaces.

### **3.1. Tableaux NumPy**

- **Création** :
  ```python
  import numpy as np
  x = np.array([0, 2, 8, -3])
  print(x.dtype)  # Type des éléments (ex: int64)
  ```
- **Opérations** :
  ```python
  y = np.array([10, 4, 6, 3])
  print(x + y)  # Addition élément par élément
  print(x * y)  # Multiplication élément par élément
  ```

### **3.2. Indexation et découpage**

- **Accès aux éléments** :
  ```python
  v = np.arange(0.0, 2.0, 0.4)  # [0.0, 0.4, 0.8, 1.2, 1.6]
  print(v[1:3])  # [0.4, 0.8]
  ```
- **Redimensionnement** :
  ```python
  A = np.arange(6).reshape([2, 3])  # [[0, 1, 2], [3, 4, 5]]
  ```

### **3.3. Sauvegarde et chargement**

- **Sauvegarder** :
  ```python
  np.save('A.npy', A)
  ```
- **Charger** :
  ```python
  C = np.load('A.npy')
  print(A == C)  # Vérifie si les tableaux sont identiques
  ```

---

### **3.4. Tableaux 2D et 3D**

- **Transposition** :
  ```python
  D = np.array([[0, 1, 2], [3, 4, 5]])
  print(D.T)  # [[0, 3], [1, 4], [2, 5]]
  ```
- **Indexation booléenne** :
  ```python
  sel_j = np.arange(74) < 10  # Tableau de booléens
  M[:, sel_j, :].shape  # Sélectionne les colonnes où sel_j est True
  ```

---

## **4. Exercices corrigés**

### **Exercice 1 : Afficher les caractères d'une chaîne**

```python
def print_chars(s):
    for char in s:
        print(char)

print_chars("hello")
```

**Sortie attendue** :

```
h
e
l
l
o
```

---

### **Exercice 2 : Doubler les voyelles**

```python
def double_vowels(s):
    vowels = "aeiouAEIOU"
    result = []
    for char in s:
        if char in vowels:
            result.append(char * 2)
        else:
            result.append(char)
    return ''.join(result)

print(double_vowels("hello"))  # "heelloo"
```

---

### **Exercice 3 : Somme des entiers de 1 à n**

```python
def sum_up_to(n):
    return n * (n + 1) // 2  # Formule mathématique

print(sum_up_to(10))  # 55
```

---

### **Exercice 4 : Accès aléatoire à un tableau**

```python
import numpy as np

M = np.load('BOLD_image.npy')

# 1. Élément aléatoire
random_element = M[np.random.randint(0, M.shape[0]),
                   np.random.randint(0, M.shape[1]),
                   np.random.randint(0, M.shape[2])]
print(random_element)

# 2. Sujet aléatoire (1er indice)
random_subject = M[np.random.randint(0, M.shape[0]), :, :]
print(random_subject.shape)
```

---

## **5. Ressources utiles**

- [Documentation Python](https://docs.python.org/3/)
- [Tutoriel NumPy](https://numpy.org/doc/stable/user/quickstart.html)
- [Aide en ligne](https://docs.python.org/3/reference/index.html) (`help(range)` dans l'interpréteur)