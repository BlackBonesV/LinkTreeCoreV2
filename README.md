# 🎮 LinkTree Streamer — Cyberpunk / Néon

> Un LinkTree ultra fluide, style cyberpunk, entièrement personnalisable via un seul fichier.

![Preview](https://img.shields.io/badge/style-cyberpunk%20néon-00fff7?style=for-the-badge&logo=twitch)
![GitHub Pages](https://img.shields.io/badge/hébergement-GitHub%20Pages-bf00ff?style=for-the-badge&logo=github)

---

## ✨ Fonctionnalités

- 🎨 **Thème Cyberpunk / Néon** avec grille animée et scanlines
- ✨ **Fond de particules** connectées et interactives
- 🔴 **Badge "EN LIVE"** animé (manuel ou via API Twitch)
- 🖱️ **Curseur personnalisé** néon (desktop uniquement)
- 💥 **Effet ripple** au clic sur chaque lien
- ⚡ **Animations fluides** en cascade à l'entrée
- 📱 **100% responsive** mobile / desktop
- 🔧 **Un seul fichier** à modifier : `config.js`

---

## 📁 Structure du projet

```
linktree-streamer/
├── index.html      ← Structure HTML (ne pas modifier)
├── style.css       ← Styles cyberpunk (ne pas modifier)
├── script.js       ← Logique JS (ne pas modifier)
├── config.js       ← ✅ TON FICHIER DE CONFIG
├── avatar.jpg      ← Ta photo de profil (optionnel)
└── README.md       ← Ce fichier
```

---

## ⚙️ Configuration — `config.js`

Tout se passe dans `config.js`. Voici le guide complet section par section.

---

### 👤 Profil

```js
streamer: {
  pseudo:   "StreamerXX",               // Ton pseudo affiché en haut
  tagline:  "Bienvenue dans ma zone 🎮", // Phrase sous le pseudo
  avatar:   "avatar.jpg",               // Nom du fichier image (voir section Avatar)
},
```

**Modifier le pseudo :** remplace `"StreamerXX"` par ton vrai pseudo.  
**Modifier la tagline :** remplace le texte entre guillemets par ce que tu veux.

---

### 🖼️ Avatar (photo de profil)

1. Place ton image à la **racine du projet** (même dossier que `index.html`)
2. Nomme-la `avatar.jpg` (ou n'importe quel nom)
3. Indique le nom dans `config.js` :

```js
avatar: "avatar.jpg",    // JPG, PNG, WEBP, GIF acceptés
```

> 💡 **Si tu ne mets pas d'image**, le site affiche automatiquement tes initiales en néon.  
> Pour forcer les initiales : laisse `avatar: ""` (chaîne vide).

---

### 🔴 Statut Live

```js
live: {
  isLive:        false,                // true = badge rouge animé visible
  liveLabel:     "🔴 EN LIVE MAINTENANT",
  offlineLabel:  "⚫ HORS LIGNE",
  twitchChannel: "streamerxx",         // Ton nom de chaîne Twitch
},
```

**Pour afficher le badge "EN LIVE" :**  
Change simplement `isLive: false` en `isLive: true` quand tu commences à streamer, puis remet `false` quand tu arrêtes.

> ⚡ **Astuce avancée — Automatiser avec l'API Twitch :**  
> Tu peux appeler l'API Twitch pour détecter automatiquement si tu es live.  
> Ajoute dans `script.js` après `renderLiveBadge()` :
>
> ```js
> // Exemple (nécessite un Client-ID Twitch)
> // fetch(`https://api.twitch.tv/helix/streams?user_login=${CONFIG.live.twitchChannel}`, {
> //   headers: { 'Client-ID': 'TON_CLIENT_ID', 'Authorization': 'Bearer TON_TOKEN' }
> // }).then(r => r.json()).then(d => {
> //   CONFIG.live.isLive = d.data.length > 0;
> //   renderLiveBadge();
> // });
> ```

---

### 🔗 Liens / Réseaux Sociaux

```js
links: [
  {
    id: "twitch",
    label: "Twitch",
    sublabel: "Viens me watch en live !",
    url: "https://twitch.tv/streamerxx", // ← Ton URL
    icon: "twitch",
    color: "#9147ff",
  },
  // ... autres liens
];
```

**Modifier une URL :** remplace la valeur de `url` par ton lien.  
**Modifier le texte :** change `label` (titre) et `sublabel` (sous-titre).  
**Changer la couleur d'un bouton :** modifie `color` (code hexadécimal).  
**Masquer un lien :** mets `url: ""` (chaîne vide).  
**Réordonner les liens :** déplace les blocs `{ ... }` dans l'ordre voulu.

**Ajouter un nouveau lien :**

```js
{
  id:       "kofi",                        // Identifiant unique (ton choix)
  label:    "Ko-fi",                       // Nom affiché
  sublabel: "Offre-moi un café ☕",        // Sous-titre
  url:      "https://ko-fi.com/tonpseudo", // URL
  icon:     "kofi",                        // Voir liste des icônes ci-dessous
  color:    "#ff5e5b",                     // Couleur néon du bouton
},
```

#### 🎨 Icônes disponibles

| `icon`      | Réseau      |
| ----------- | ----------- |
| `twitch`    | Twitch      |
| `discord`   | Discord     |
| `youtube`   | YouTube     |
| `tiktok`    | TikTok      |
| `instagram` | Instagram   |
| `twitter`   | Twitter / X |
| `kofi`      | Ko-fi       |
| `tipee`     | Tipee / Don |

> Si ton icône n'est pas dans la liste, tu peux utiliser n'importe quelle classe **Font Awesome 6** :  
> Ajoute dans `script.js` dans l'objet `ICONS` :
>
> ```js
> monreseau: { fa: "fas fa-star" },  // remplace "fa-star" par la classe Font Awesome
> ```
>
> Trouve les icônes sur [fontawesome.com/icons](https://fontawesome.com/icons)

---

### 🎨 Thème & Couleurs

```js
theme: {
  primaryColor:   "#00fff7",   // Cyan néon — couleur principale
  secondaryColor: "#bf00ff",   // Violet néon — anneau avatar, accents
  accentColor:    "#ff00aa",   // Rose néon — cœur, détails
  bgColor:        "#06000f",   // Couleur du fond
  cardBg:         "rgba(255,255,255,0.03)", // Fond des cartes (transparence)
  fontTitle:      "'Orbitron', sans-serif",  // Police des titres
  fontBody:       "'Rajdhani', sans-serif",  // Police du corps
},
```

**Changer la couleur principale :** modifie `primaryColor` (ex: `"#ff6b00"` pour un style orange).  
**Changer le fond :** modifie `bgColor` (ex: `"#000a0a"` pour un fond plus sombre).

> 🔧 Les polices viennent de Google Fonts. Pour en changer, ajoute le lien `<link>` dans `index.html` et mets à jour `fontTitle` / `fontBody`.

---

### ✨ Particules

```js
particles: {
  enabled:  true,    // false = désactiver les particules
  count:    80,      // Nombre de particules (60–120 recommandé)
  speed:    0.4,     // Vitesse (0.2 = très lent, 1 = rapide)
  size:     2,       // Taille max en pixels
  color:    "#00fff7",
  linked:   true,    // Relier les particules proches
  linkDist: 130,     // Distance de liaison en pixels
},
```

---

### 🌐 SEO & Métadonnées

```js
meta: {
  title:       "StreamerXX — Links",
  description: "Tous mes liens en un seul endroit !",
  url:         "https://streamerxx.github.io", // ← Ton URL GitHub Pages
  themeColor:  "#06000f",
},
```

---

## 🚀 Déploiement sur GitHub Pages

### Étape 1 — Créer le dépôt

1. Va sur [github.com](https://github.com) et crée un **nouveau dépôt public**
2. Nomme-le : `ton-pseudo.github.io` _(remplace `ton-pseudo` par ton vrai pseudo GitHub)_  
   — OU — n'importe quel nom (ex: `linktree`)

### Étape 2 — Pousser les fichiers

Ouvre un terminal dans le dossier du projet (clic droit > "Ouvrir dans le terminal" sur VS Code) :

```bash
git init
git add .
git commit -m "🎮 Initial commit — LinkTree Streamer"
git branch -M main
git remote add origin https://github.com/TON-PSEUDO/NOM-DU-REPO.git
git push -u origin main
```

### Étape 3 — Activer GitHub Pages

1. Va sur ton dépôt GitHub
2. **Settings** → **Pages** (dans le menu gauche)
3. Source : **Deploy from a branch**
4. Branch : `main` / `/(root)`
5. Clique **Save**

Ton site sera en ligne en 1–2 minutes à l'adresse affichée. 🎉

### Étape 4 — Mises à jour

À chaque modification de `config.js` :

```bash
git add config.js
git commit -m "✏️ Mise à jour config"
git push
```

---

## 💻 Développement local

Ouvre `index.html` directement dans ton navigateur — **aucun serveur requis** !

Ou avec l'extension **Live Server** dans VS Code :

1. Clic droit sur `index.html`
2. "Open with Live Server"

---

## ❓ FAQ

**Q : Mon avatar ne s'affiche pas**  
R : Vérifie que le fichier image est bien à la racine du projet et que le nom dans `config.js` correspond exactement (majuscules/minuscules incluses).

**Q : Les icônes ne s'affichent pas**  
R : Font Awesome est chargé depuis CDN. Assure-toi d'avoir une connexion internet. En local sans connexion, utilise des emojis dans le `label`.

**Q : Comment changer le domaine ?**  
R : Achète un domaine, puis dans les **Settings > Pages** de GitHub, configure un _Custom domain_.

**Q : Les particules ralentissent mon PC**  
R : Diminue `count` à 40 ou passe `enabled: false`.

---

## 📄 Licence

Libre d'utilisation et de modification. Un crédit apprécié mais pas obligatoire. 🙂
