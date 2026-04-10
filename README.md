# Blog — Guide d'utilisation

Minimaliste sombre, zéro dépendance, HTML/CSS pur. Ça vivra 10 ans sans toucher quoi que ce soit.

---

## Structure des fichiers

```
blog/
├── index.html          ← page d'accueil (liste des articles)
├── about.html          ← page à propos
├── style.css           ← tout le design, ne touche qu'ici pour styler
├── posts/
│   ├── post-template.html   ← MODÈLE — duplique ce fichier pour chaque article
│   └── mon-article.html     ← tes articles vont ici
└── README.md
```

---

## Ajouter un article (2 minutes)

### 1. Crée le fichier de l'article

```bash
cp posts/post-template.html posts/nom-de-l-article.html
```

Nomme le fichier avec des tirets, pas d'espaces :
- ✅ `posts/sqli-blind-parametre-order.html`
- ✅ `posts/xss-stored-commentaire.html`
- ❌ `posts/Mon Article.html`

### 2. Remplis le template

Ouvre le fichier et modifie les sections marquées. Les commentaires dans le fichier t'indiquent quoi changer :

```html
<!-- ═══ MODIFIE CES 3 LIGNES pour chaque article ═══ -->
<meta name="description" content="Ta description ici.">
<title>Ton titre — tonblog</title>
```

Puis l'en-tête de l'article :
```html
<div class="meta">
  <span>2025-01-15</span>   ← date
  <span>XSS · Recon</span>  ← tags séparés par ·
  <span>~5 min</span>       ← temps de lecture estimé
</div>
<h1>Ton titre</h1>
<p class="summary">Résumé en une ou deux phrases.</p>
```

### 3. Ajoute l'article à l'index

Dans `index.html`, copie ce bloc dans la liste `<ul class="post-list">` :

```html
<li class="post-item">
  <span class="post-date">2025-01-15</span>
  <a href="posts/nom-de-l-article.html" class="post-title">
    Titre de l'article
  </a>
  <div class="post-tags">
    <span class="tag">xss</span>
    <span class="tag">recon</span>
  </div>
</li>
```

**L'article le plus récent en premier** dans la liste.

### 4. Commit & push

```bash
git add .
git commit -m "post: titre de l'article"
git push
```

GitHub Pages publie automatiquement en quelques secondes.

---

## Éléments disponibles dans un article

### Titre de section
```html
<h2>Titre principal</h2>     <!-- italique élégant -->
<h3>Sous-titre</h3>          <!-- petites caps, discret -->
```

### Code en ligne
```html
Le payload <code>alert(1)</code> dans le paramètre <code>q</code>.
```

### Bloc de code
```html
<pre data-lang="bash"><code>nmap -sV target.com</code></pre>
<pre data-lang="python"><code>print("hello")</code></pre>
<pre data-lang="http"><code>GET /api/user?id=1 HTTP/1.1</code></pre>
```
`data-lang` est optionnel — ça affiche juste un label en haut à droite.

### Encadrés
```html
<div class="note">
  <strong>note</strong>
  Un truc à retenir.
</div>

<div class="note tip">
  <strong>tip</strong>
  Une astuce utile.
</div>

<div class="note warn">
  <strong>attention</strong>
  Un avertissement.
</div>
```

### Séparateur
```html
<hr>
```

### Liens
```html
<a href="https://portswigger.net">PortSwigger</a>
```

---

## GitHub Pages — activation

Si ce n'est pas encore fait :

1. Aller dans **Settings → Pages**
2. Source : **Deploy from a branch**
3. Branch : **main** · Folder : **/ (root)**
4. Save

L'URL sera `https://tonpseudo.github.io/nom-du-repo/`

---

## Personnalisation

Tout le design est dans `style.css`. Les variables en haut du fichier contrôlent les couleurs :

```css
:root {
  --bg:      #0c0c0c;   /* fond de page */
  --accent:  #e8e0d0;   /* couleur des liens */
  /* ... */
}
```

Pour changer le nom du blog, cherche `tonblog` dans tous les fichiers HTML.

---

*Dernière mise à jour : 2025*
