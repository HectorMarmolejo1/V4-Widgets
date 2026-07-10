# Bibliothèque Widgets V4

Bibliothèque interne de widgets premium destinés aux sites V4.

Chaque widget est développé en HTML/CSS/JavaScript, publié via GitHub Pages et intégré dans les sites V4 au moyen d'un iframe.

---

# Architecture

```
V4-Widgets/
│
├── iframe/
│   ├── reviews-premium/
│   ├── gooey-agence/
│   ├── expand-map/
│   ├── vertical-real-estate-stack/
│   ├── calculateur-rentabilite/
│   └── ...
│
├── database/
│   └── agencies/
│       ├── maison-horizon.json
│       ├── agence-strasbourg.json
│       └── ...
│
└── README.md
```

---

# Principe général

Les widgets ne contiennent jamais les données du client.

Ils récupèrent les informations depuis un profil d'agence situé dans :

```
database/agencies/
```

Le widget reste donc totalement réutilisable.

---

# Structure d'un profil agence

Chaque agence possède un identifiant unique.

Exemple :

```
maison-horizon.json
```

Structure :

```json
{
  "id": "...",
  "agencyName": "...",
  "clientType": "...",
  "businessModel": "...",
  "specialties": [],
  "territory": {},
  "brand": {},
  "contact": {},
  "location": {},
  "stats": {},
  "reviews": {}
}
```

Tous les futurs profils devront respecter cette structure.

---

# Convention de nommage

Toujours utiliser :

- minuscules
- tirets (-)
- aucun accent
- aucun espace
- aucun caractère spécial

Exemples :

```
maison-horizon
agence-strasbourg
loire-investissement
agence-des-arenes
```

---

# Fonctionnement des widgets

Chaque widget reçoit un identifiant :

```
?client=maison-horizon
```

Puis charge automatiquement le profil correspondant :

```
database/agencies/maison-horizon.json
```

Le widget n'a jamais besoin d'être modifié.

---

# Ajouter une nouvelle agence

Créer :

```
database/agencies/nouvelle-agence.json
```

Compléter toutes les informations.

Le widget fonctionnera immédiatement avec :

```
?client=nouvelle-agence
```

---

# Ajouter un nouveau widget

Créer un nouveau dossier :

```
iframe/nom-du-widget/
```

Créer :

```
index.html
```

Publier sur GitHub Pages.

Ajouter le lien dans :

```
iframe/index.html
```

---

# Widgets actuellement disponibles

- Reviews Premium
- Gooey Agence
- Expand Map
- Vertical Real Estate Stack
- Calculateur de rentabilité

---

# Vision du projet

L'objectif n'est pas seulement de créer des widgets.

Le projet vise à construire une plateforme interne de composants réutilisables alimentés par des profils d'agence centralisés.

À terme, les profils pourront être alimentés automatiquement via une API interne (Google Business Profile, CRM, statistiques immobilières, etc.), sans modifier les widgets existants.

Chaque widget deviendra ainsi un simple composant d'affichage connecté à une source de données unique.