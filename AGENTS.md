
# Instructions pour agents IA – Documentation projet

## 1. Contexte général

Tu es un **agent IA** intervenant sur la documentation d’un projet logiciel.

La documentation est gérée avec **MkDocs** et stockée dans ce dépôt.

- **Répertoire de documentation** : `./docs`
- **Configuration principale** : `mkdocs.yml`
- **Navigation** :
  - Peut être définie directement dans `mkdocs.yml`
  - Ou générée automatiquement (ex: via un script de build)
- **Langue par défaut** : Français (sauf indication contraire explicite)
- **Outil de génération** : MkDocs

Ton rôle est de créer, modifier et organiser les fichiers de documentation en respectant les règles ci-dessous.

---

## 2. Règles d’écriture

### 2.1 Langue
- Par défaut : **français clair, précis et technique**
- Adapter uniquement si le projet impose une autre langue

### 2.2 Titres
- Ne jamais ajouter de titre de niveau 1 (`#`)
- Le premier niveau utilisé est toujours :
  - `##` → sections principales
  - `###`, `####` → sous-sections

### 2.3 Style
- Phrases courtes et lisibles
- Ton neutre, factuel, non marketing
- Aller à l’essentiel
- Expliquer les concepts de manière structurée

### 2.4 Cohérence
- Utiliser un vocabulaire homogène
- Respecter les conventions déjà présentes dans le projet
- Ne pas introduire de terminologie incohérente

### 2.5 Qualité
- Orthographe correcte
- Typographie cohérente
- Pas d’ambiguïté ni d’interprétation personnelle

---

## 3. Structure des fichiers

### 3.1 Emplacement
- Tous les fichiers `.md` doivent être dans :
  - `./docs`
  - ou un sous-dossier de `./docs`

### 3.2 Nommage
- minuscules uniquement
- sans accents
- sans espaces (utiliser `_` ou `-`)

Exemples :
- `installation.md`
- `user_guide.md`
- `api-reference.md`

### 3.3 Organisation
- Structurer les dossiers de manière logique
- Limiter la profondeur inutile
- Regrouper les contenus par thématique

---

## 4. Liens internes

- Toujours utiliser des **liens relatifs**

```markdown
[Installation](../guide/installation.md)
````

* Vérifier systématiquement :

  * que le fichier cible existe
  * que le chemin est correct

---

## 5. Navigation (mkdocs)

### Cas 1 — navigation manuelle

* Mettre à jour `mkdocs.yml` (clé `nav`) lors de l’ajout de pages

Exemple :

```yaml
nav:
  - Home: index.md
  - Guide:
      - Installation: guide/installation.md
```

---

### Cas 2 — navigation générée automatiquement

* Ne pas modifier `nav` manuellement
* Respecter la structure attendue :

  * `nav.yml` par module
  * ou conventions du script de build

---

## 6. Actions autorisées

✅ Créer de nouveaux fichiers Markdown
✅ Modifier le contenu pour améliorer clarté et précision
✅ Réorganiser les sections pour une meilleure lisibilité
✅ Corriger les liens internes
✅ Harmoniser le style global
✅ Ajouter ou adapter la navigation (si applicable)

---

## 7. Actions interdites

❌ Supprimer des fichiers sans instruction explicite
❌ Modifier la configuration MkDocs (hors navigation)
❌ Changer la langue sans instruction
❌ Introduire du contenu non vérifié
❌ Ajouter du contenu marketing ou subjectif
❌ Modifier des fichiers hors documentation

---

## 8. Bonnes pratiques

### 8.1 Lisibilité

* Une idée = un paragraphe
* Structurer avec des titres clairs
* Éviter les blocs de texte trop longs

### 8.2 Documentation technique

* Donner des exemples concrets
* Expliquer le "pourquoi", pas seulement le "comment"
* Préciser les prérequis si nécessaire

### 8.3 Cohérence globale

* S’aligner sur les pages existantes
* Ne pas créer de structure parallèle incohérente

### 8.4 Validation

* Vérifier le rendu avec :

```bash
mkdocs serve
```

---

## 9. Interaction avec un système de build

Dans certains projets, la documentation peut être :

* assemblée depuis plusieurs sources
* transformée automatiquement (scripts, pipelines)
* intégrée dans un site global

Dans ce cas :

* respecter les conventions définies (ex: `nav.yml`, `sources.yml`)
* ne pas casser la structure attendue par le build
* ne pas déplacer arbitrairement les fichiers

---

## 10. Exemple d’intervention

### Tâche

Ajouter une page FAQ.

### Étapes

1. Créer le fichier :

```text
./docs/faq.md
```

2. Contenu :

```markdown
## Foire aux questions

### Qu’est-ce que ce projet ?
Description du projet.

### Comment l’installer ?
Voir [Installation](guide/installation.md).

### Où obtenir de l’aide ?
Voir la section support.
```

3. Ajouter à la navigation (si applicable) :

```yaml
nav:
  - FAQ: faq.md
```

4. Vérifier :

* rendu correct
* liens valides
* cohérence avec le reste de la documentation

---

## 11. Règle fondamentale

Toute modification doit :

* améliorer la compréhension
* respecter la structure existante
* rester cohérente avec l’ensemble du projet

---

**Ces instructions sont permanentes et doivent être respectées pour toute intervention IA sur ce dépôt.**

