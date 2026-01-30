## 📚 Projet : Application de gestion de livres (Book Manager)

### 🎯 Objectif pédagogique

Créer une application web simple permettant de gérer une bibliothèque de livres afin de pratiquer :

* La **découpe en composants**
* Le **rendu de liste** (`v-for`)
* Les **conditions** (`v-if`, `v-else`, `v-show`)
* Les **props & events**
* Les **bindings** (`v-model`)
* La **gestion d’état local**
* Les **computed properties**
* Les **émissions d’événements**
* (Bonus) Filtrage et recherche

---

## 🧱 Structure de l’application

### 1️⃣ Composants attendus

#### 🔹 `App.vue`

* Composant racine
* Contient la liste globale des livres
* Gère les actions principales (ajout, suppression, changement de statut)

#### 🔹 `BookForm.vue`

* Formulaire d’ajout de livre
* Champs :

  * Titre
  * Auteur
  * Année
  * Catégorie
* Bouton **Ajouter**
* Émet un événement `add-book`

#### 🔹 `BookList.vue`

* Reçoit la liste des livres via `props`
* Affiche les livres avec `v-for`
* Gère le cas :

  * Liste vide → message conditionnel

#### 🔹 `BookItem.vue`

* Affiche les infos d’un livre
* Boutons :

  * 📖 Marquer comme lu / non lu
  * ❌ Supprimer
* Applique un style conditionnel selon le statut

---

## 📦 Modèle de données (exemple)

```js
{
  id: 1,
  title: "Clean Code",
  author: "Robert C. Martin",
  year: 2008,
  category: "Programmation",
  isRead: false
}
```

---

## 🧠 Fonctionnalités à implémenter

### ✅ Fonctionnalités de base

* Ajouter un livre
* Afficher la liste des livres
* Supprimer un livre
* Marquer un livre comme **lu / non lu**

---

### 🔀 Rendu conditionnel

* Si la liste est vide →
  👉 *“Aucun livre dans la bibliothèque”*
* Si un livre est lu :

  * Texte barré
  * Badge “Lu”
* Sinon :

  * Badge “À lire”

---

### 🔁 Rendu de liste

* Utiliser `v-for` avec une clé unique
* Afficher :

  * Numéro d'ordre du livre
  * Titre
  * Auteur

---

## 🎨 Style conditionnel

* Livre lu → fond vert clair
* Livre non lu → fond gris / blanc
* Boutons visibles selon le statut

---

## 🔎 BONUS (à faire)

* Filtrer les livres :

  * Tous
  * Lus
  * Non lus
* Recherche par titre ou auteur
* Compteur :

  * Total de livres
  * Livres lus
* Sauvegarde dans `localStorage`

---

## 🧪 Contraintes techniques

* ❌ Pas de `onclick` dans le HTML
* ✅ Utiliser `@click`
* ❌ Pas de logique métier dans le template
* ✅ Utiliser des méthodes / computed

---
