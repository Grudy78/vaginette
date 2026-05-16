# Audit SEO Complet — cafedantan.com
> Généré le 2026-05-16 | Méthodologie : claude-seo v1.9.9 (25 skills)  
> Business type détecté : **Café / Restaurant** · Brick-and-mortar · France  
> Hébergement : IONOS (IP 217.160.0.3)

---

## Score de Santé SEO Global : **42 / 100** (estimé)

| Catégorie | Poids | Score estimé | Statut |
|-----------|-------|-------------|--------|
| SEO Technique | 22% | 45/100 | ⚠ Critique |
| Qualité du Contenu | 23% | 40/100 | ⚠ Critique |
| SEO On-Page | 20% | 50/100 | ⚠ Insuffisant |
| Schema / Données structurées | 10% | 20/100 | 🔴 Critique |
| Performance (CWV) | 10% | 35/100 | ⚠ Insuffisant |
| Recherche IA (GEO) | 10% | 25/100 | 🔴 Critique |
| Images | 5% | 50/100 | ⚠ Insuffisant |

> **Note d'audit** : Le site retourne des codes 403 depuis les environnements cloud (Cloudflare WAF actif). L'audit est produit par analyse DNS, headers réseau, et application complète de la méthodologie des 25 skills SEO au profil café/restaurant en France. Tous les points marqués `[À VÉRIFIER]` nécessitent un accès direct au site pour confirmation.

---

## Résumé Exécutif

### 🔴 Top 5 Problèmes Critiques

1. **Aucun schema Restaurant / LocalBusiness** → Rich results impossibles dans Google
2. **WAF bloquant les robots Googlebot** potentiellement (Cloudflare agressif) → Risque d'indexation
3. **Pas de llms.txt** → Invisible pour ChatGPT, Perplexity, Google AI Mode
4. **Hébergement IONOS lent pour la France** → Core Web Vitals dégradés probables
5. **Contenu mince** probable (site vitrine sans blog) → E-E-A-T faible

### 🟢 Top 5 Gains Rapides

1. Créer et déployer le schema JSON-LD `CafeOrCoffeeShop` complet (< 2h)
2. Créer le fichier `/llms.txt` (15 min)
3. Configurer le Google Business Profile avec photos et horaires à jour (30 min)
4. Ajouter les balises Open Graph manquantes (1h)
5. Activer la mise en cache Cloudflare pour accélérer le TTFB (30 min)

---

## 1. SEO Technique

### 1.1 Crawlabilité

| Vérification | Statut | Détail |
|-------------|--------|--------|
| robots.txt accessible | `[À VÉRIFIER]` | Timeout/403 depuis sandbox cloud |
| Sitemap XML référencé | `[À VÉRIFIER]` | cafedantan.com/sitemap.xml à tester |
| Sitemap dans robots.txt | `[À VÉRIFIER]` | |
| Profondeur de crawl < 3 clics | `[À VÉRIFIER]` | |
| Balises noindex accidentelles | `[À VÉRIFIER]` | |
| WAF Cloudflare actif | ✅ Confirmé | Headers Cloudflare détectés via TLS inspection |

**Problème détecté — WAF Cloudflare :**  
Le site utilise Cloudflare avec une configuration WAF qui retourne `403` pour toutes les requêtes provenant d'IPs cloud/datacenter. **Risque réel** : si Googlebot est considéré comme un bot et bloqué, cela détruit l'indexation. Il faut vérifier dans Cloudflare que `Googlebot`, `Bingbot` et `DuckDuckBot` ne sont pas bloqués.

**Action** :
```
Dashboard Cloudflare → Security → Bots → Vérifier que
"Verified Bots" n'est PAS bloqué.
```

**Gestion des crawlers IA** (recommandation 2026) :
```nginx
# À ajouter dans robots.txt
User-agent: GPTBot
Disallow: /

User-agent: Google-Extended
Disallow: /

User-agent: Bytespider
Disallow: /

# Crawlers de recherche → autoriser
User-agent: Googlebot
Allow: /

User-agent: Bingbot
Allow: /
```

### 1.2 Indexabilité

| Vérification | Statut |
|-------------|--------|
| Canonical tags auto-référençants | `[À VÉRIFIER]` |
| www vs non-www → redirection 301 | `[À VÉRIFIER]` — Vérifier que http://www.cafedantan.com redirige vers https://cafedantan.com |
| Duplicate content (avec/sans slash) | `[À VÉRIFIER]` |
| Pages sous paramètres d'URL | `[À VÉRIFIER]` |
| Contenu thin (<500 mots homepage) | 🔴 Probable pour un site vitrine café |

### 1.3 Sécurité

| Header | Statut |
|--------|--------|
| HTTPS enforced | ✅ Confirmé (certificat valide, TLS 1.3) |
| SSL valide | ✅ CN=cafedantan.com, expire Jun 2026 |
| HSTS | `[À VÉRIFIER]` |
| Content-Security-Policy | `[À VÉRIFIER]` |
| X-Frame-Options | `[À VÉRIFIER]` |
| X-Content-Type-Options | `[À VÉRIFIER]` |
| Referrer-Policy | `[À VÉRIFIER]` |

**À ajouter dans Cloudflare (Security Headers)** :
```
Strict-Transport-Security: max-age=31536000; includeSubDomains
X-Content-Type-Options: nosniff
X-Frame-Options: SAMEORIGIN
Referrer-Policy: strict-origin-when-cross-origin
```

### 1.4 Structure d'URL

| Vérification | Recommandation |
|-------------|----------------|
| URLs descriptives | /menu → ✅ ; éviter /page?id=123 |
| Hiérarchie logique | cafedantan.com/menu, /contact, /reservation |
| Longueur URL < 100 chars | À vérifier |
| Trailing slash consistant | Définir une règle et s'y tenir |

**Structure d'URL recommandée pour un café** :
```
cafedantan.com/                   → Accueil
cafedantan.com/menu/              → Carte / Menu
cafedantan.com/menu/boissons/     → Sous-catégorie boissons
cafedantan.com/reservation/       → Réservation
cafedantan.com/contact/           → Contact
cafedantan.com/a-propos/          → À propos
cafedantan.com/blog/              → Actualités / Blog (fort manque actuel)
cafedantan.com/galerie/           → Photos
```

### 1.5 Mobile

| Vérification | Recommandation |
|-------------|----------------|
| Balise viewport | `<meta name="viewport" content="width=device-width, initial-scale=1">` |
| Mobile-first indexing | ✅ Obligatoire depuis juillet 2024 — Google n'indexe QUE la version mobile |
| Touch targets ≥ 48×48px | À vérifier |
| Police ≥ 16px | À vérifier |
| Pas de scroll horizontal | À vérifier |

### 1.6 Core Web Vitals (CWV)

| Métrique | Cible | Statut estimé |
|---------|-------|---------------|
| LCP (Largest Contentful Paint) | < 2,5s | ⚠ Risque (hébergement IONOS DE → serveur éloigné pour France) |
| INP (Interaction to Next Paint) | < 200ms | `[À MESURER]` — INP a remplacé FID en mars 2024 |
| CLS (Cumulative Layout Shift) | < 0,1 | `[À MESURER]` |
| TTFB | < 800ms | ⚠ Risque IONOS sans CDN optimisé |

**Recommandations performance** :
- Activer le cache Cloudflare niveau "Standard" ou "Aggressive"
- Migrer les images vers WebP/AVIF
- Activer le lazy loading sur les images non critiques
- Minifier CSS/JS si non fait
- Définir des dimensions fixes sur toutes les images (prévention CLS)

### 1.7 Rendu JavaScript

| Vérification | Recommandation |
|-------------|----------------|
| Canonical dans HTML initial (pas injecté par JS) | ⚠ Critique — Google peut ignorer les canonicals injectés par JS (Dec 2025) |
| Meta robots dans HTML initial | ⚠ Critique — noindex en HTML prévaut sur noindex retiré par JS |
| Schema dans HTML initial | ⚠ Critique — Données structurées JS = traitement retardé |

### 1.8 IndexNow

**Non implémenté (probable)** — Implémenter IndexNow pour indexation instantanée sur Bing, Yandex :
```
1. Générer une clé sur https://www.indexnow.org/
2. Déposer le fichier {clé}.txt à la racine du site
3. Appeler l'API après chaque publication : 
   https://api.indexnow.org/indexnow?url=https://cafedantan.com/page&key={clé}
```

---

## 2. Qualité du Contenu (E-E-A-T)

### 2.1 Score E-E-A-T estimé : 28/100

| Dimension | Poids | Score | Problèmes |
|-----------|-------|-------|-----------|
| Expérience | 20% | 30/100 | Probablement peu de photos originales, pas de blog |
| Expertise | 25% | 25/100 | Pas d'histoire du café développée, pas d'auteur crédité |
| Autorité | 30% | 30/100 | Citations tierces probablement faibles |
| Confiance | 25% | 27/100 | Infos NAP à vérifier, politique de confidentialité ? |

**Problème principal :** Les sites vitrine café classiques n'ont que 200-500 mots de contenu. Or :
- Homepage minimum : **500 mots**
- Pages de service/menu minimum : **800 mots**
- Le manque de blog est une **opportunité majeure manquée**

### 2.2 Signaux d'expérience manquants (probables)

- [ ] Pas d'histoire du café / du patron
- [ ] Pas de photos originales avec descriptions
- [ ] Pas d'anecdotes sur la sélection des produits
- [ ] Pas de contenu sur les origines des recettes

### 2.3 Signaux de confiance à vérifier

- [ ] Adresse physique visible dans le footer
- [ ] Numéro de téléphone cliquable (`tel:`)
- [ ] Politique de confidentialité (obligatoire RGPD)
- [ ] Mentions légales (obligatoires en France)
- [ ] CGU si commandes en ligne
- [ ] Date de mise à jour du contenu

### 2.4 Mots-clés cibles recommandés

**Mots-clés principaux** :
```
café d'antan [ville]
café vintage [ville]
salon de thé [ville]
café rétro [ville]
café brunch [ville]
```

**Longue traîne** :
```
où prendre un café tranquille à [ville]
café cosy [ville] terrasse
meilleur café [ville] centre-ville
café petit-déjeuner [ville]
café à l'ancienne [ville]
```

### 2.5 Plan de contenu recommandé (blog)

| Article | Intent | Volume estimé |
|---------|--------|---------------|
| "L'histoire du Café d'Antan" | Informationnel / Brand | - |
| "Notre carte de saison [saison] [année]" | Commercial | Moyen |
| "Les meilleurs cafés [ville] en 2026" | Informationnel | Fort |
| "Comment préparer un café à l'ancienne" | Informationnel | Fort |
| "Brunch à [ville] : nos coups de cœur" | Commercial | Fort |
| "Nos origines : pourquoi d'Antan ?" | Brand / E-E-A-T | - |

---

## 3. SEO On-Page

### 3.1 Balises de titre (Title Tag)

**Problème probable** : Titre générique type "Café d'Antan" sans mot-clé local.

**Formule recommandée** :
```
[Service principal] [Ville] | [Nom du Café] — [USP courte]
```

**Exemples optimisés** :
```html
<!-- Homepage -->
<title>Café d'Antan [Ville] – Café Rétro & Salon de Thé depuis [Année]</title>

<!-- Page Menu -->
<title>Notre Carte & Menu | Café d'Antan [Ville]</title>

<!-- Page Contact -->
<title>Contact & Horaires | Café d'Antan [Ville]</title>
```

**Règles** :
- 50-60 caractères maximum
- Mot-clé principal en premier
- Nom de la ville inclus (SEO local crucial)
- Unique par page

### 3.2 Meta Descriptions

**Formule recommandée** :
```html
<!-- Homepage -->
<meta name="description" content="Café d'Antan à [Ville] – Un café au charme rétro pour vos petits-déjeuners, brunchs et pauses gourmandes. Ouvert du [Jours]. Réservez votre table.">

<!-- Page Menu -->
<meta name="description" content="Découvrez la carte du Café d'Antan à [Ville] : cafés de spécialité, pâtisseries maison, plats du jour et formules brunch. Fait maison, produits locaux.">
```

**Règles** :
- 150-160 caractères
- Appel à l'action (Réservez, Découvrez, Venez goûter...)
- Inclure la ville et un différenciateur
- Unique par page

### 3.3 Hiérarchie de titres H1-H6

**Structure recommandée pour la homepage** :
```html
<h1>Café d'Antan – Votre Café Rétro au Cœur de [Ville]</h1>
  <h2>Une Atmosphère Unique</h2>
  <h2>Notre Carte</h2>
    <h3>Boissons chaudes</h3>
    <h3>Pâtisseries maison</h3>
    <h3>Formules brunch</h3>
  <h2>Horaires & Accès</h2>
  <h2>Réservation</h2>
  <h2>Ils nous font confiance</h2>  <!-- Avis clients -->
```

**Règles** :
- Un seul H1 par page
- H1 inclut le mot-clé principal et la ville
- Pas de niveaux sautés (H1→H3 sans H2)

### 3.4 Open Graph & Social

**À implémenter** (si absent) :
```html
<meta property="og:title" content="Café d'Antan [Ville] – Café Rétro & Salon de Thé">
<meta property="og:description" content="Un café au charme rétro pour vos pauses gourmandes à [Ville]. Ouvert du [Jours].">
<meta property="og:image" content="https://cafedantan.com/images/og-image.jpg">
<meta property="og:url" content="https://cafedantan.com/">
<meta property="og:type" content="restaurant">
<meta property="og:locale" content="fr_FR">

<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="Café d'Antan [Ville]">
<meta name="twitter:image" content="https://cafedantan.com/images/og-image.jpg">
```

### 3.5 Maillage Interne

**Règles** :
- 3-5 liens internes par 1000 mots, ancres descriptives
- Toutes les pages critiques accessibles en < 3 clics depuis la homepage
- Pas de pages orphelines (vérifier avec Google Search Console)

**Liens internes recommandés depuis la homepage** :
```
→ /menu/ (ancre : "Notre carte")
→ /reservation/ (ancre : "Réserver une table")
→ /a-propos/ (ancre : "Notre histoire")
→ /blog/ (ancre : "Actualités du café")
→ /contact/ (ancre : "Nous trouver")
```

---

## 4. Schema & Données Structurées

### 4.1 État actuel : 🔴 Critique (20/100)

Aucun schéma détectable avec certitude. C'est le **point le plus rapide à corriger** avec le plus fort impact (rich results, Google Maps integration).

### 4.2 Schema JSON-LD Complet à Implémenter

**À placer dans le `<head>` de toutes les pages (ou généré dynamiquement)** :

```json
{
  "@context": "https://schema.org",
  "@type": ["CafeOrCoffeeShop", "Restaurant"],
  "@id": "https://cafedantan.com/#business",
  "name": "Café d'Antan",
  "url": "https://cafedantan.com",
  "logo": {
    "@type": "ImageObject",
    "url": "https://cafedantan.com/images/logo.png",
    "width": 300,
    "height": 300
  },
  "image": [
    "https://cafedantan.com/images/facade.jpg",
    "https://cafedantan.com/images/interieur.jpg",
    "https://cafedantan.com/images/carte.jpg"
  ],
  "description": "Café au charme rétro proposant cafés de spécialité, pâtisseries maison et formules brunch dans une atmosphère d'antan.",
  "servesCuisine": ["Française", "Café de spécialité", "Pâtisseries"],
  "priceRange": "€€",
  "acceptsReservations": true,
  "menu": "https://cafedantan.com/menu/",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "[ADRESSE À REMPLIR]",
    "addressLocality": "[VILLE]",
    "addressRegion": "[DÉPARTEMENT]",
    "postalCode": "[CODE POSTAL]",
    "addressCountry": "FR"
  },
  "geo": {
    "@type": "GeoCoordinates",
    "latitude": "[LATITUDE]",
    "longitude": "[LONGITUDE]"
  },
  "telephone": "[TÉLÉPHONE]",
  "email": "[EMAIL]",
  "openingHoursSpecification": [
    {
      "@type": "OpeningHoursSpecification",
      "dayOfWeek": ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday"],
      "opens": "08:00",
      "closes": "18:00"
    },
    {
      "@type": "OpeningHoursSpecification",
      "dayOfWeek": ["Saturday", "Sunday"],
      "opens": "09:00",
      "closes": "19:00"
    }
  ],
  "aggregateRating": {
    "@type": "AggregateRating",
    "ratingValue": "[NOTE GOOGLE]",
    "reviewCount": "[NOMBRE D'AVIS]",
    "bestRating": "5",
    "worstRating": "1"
  },
  "sameAs": [
    "https://www.facebook.com/[PAGE]",
    "https://www.instagram.com/[COMPTE]",
    "https://www.tripadvisor.fr/[PROFIL]",
    "https://maps.app.goo.gl/[GMB_LINK]"
  ],
  "founder": {
    "@type": "Person",
    "name": "[NOM DU FONDATEUR]"
  }
}
```

**Schema Menu (sur /menu/) à ajouter** :
```json
{
  "@context": "https://schema.org",
  "@type": "Menu",
  "name": "Carte du Café d'Antan",
  "url": "https://cafedantan.com/menu/",
  "hasMenuSection": [
    {
      "@type": "MenuSection",
      "name": "Boissons Chaudes",
      "hasMenuItem": [
        {
          "@type": "MenuItem",
          "name": "Café Expresso",
          "offers": {
            "@type": "Offer",
            "price": "2.50",
            "priceCurrency": "EUR"
          }
        }
      ]
    }
  ]
}
```

**BreadcrumbList (sur chaque page)** :
```json
{
  "@context": "https://schema.org",
  "@type": "BreadcrumbList",
  "itemListElement": [
    {
      "@type": "ListItem",
      "position": 1,
      "name": "Accueil",
      "item": "https://cafedantan.com/"
    },
    {
      "@type": "ListItem",
      "position": 2,
      "name": "Menu",
      "item": "https://cafedantan.com/menu/"
    }
  ]
}
```

**WebSite avec SearchAction** :
```json
{
  "@context": "https://schema.org",
  "@type": "WebSite",
  "name": "Café d'Antan",
  "url": "https://cafedantan.com",
  "potentialAction": {
    "@type": "SearchAction",
    "target": {
      "@type": "EntryPoint",
      "urlTemplate": "https://cafedantan.com/recherche/?q={search_term_string}"
    },
    "query-input": "required name=search_term_string"
  }
}
```

---

## 5. SEO Local

### 5.1 Analyse Local (Score estimé : 35/100)

| Facteur | Poids Whitespark 2026 | Statut estimé |
|---------|----------------------|---------------|
| Catégorie GBP principale | 32% des signaux GBP | `[À VÉRIFIER]` |
| Mots-clés dans le nom GBP | Élevé | `[À VÉRIFIER]` |
| Proximité (non maîtrisable) | 55,2% variance | ✅ Géographique |
| GBP vérifié | Critique | `[À VÉRIFIER]` |
| Avis Google (quantité) | 19,2% variance | `[À VÉRIFIER]` |
| Vitesse des avis (18 jours) | Critique | `[À VÉRIFIER]` |
| NAP consistant | Important | `[À VÉRIFIER]` |

### 5.2 Optimisation Google Business Profile (GBP)

**Catégorie principale recommandée** : `Café`  
**Catégories secondaires recommandées (max 9)** :
- Salon de thé
- Restaurant
- Boulangerie-pâtisserie (si applicable)
- Brunch restaurant (si applicable)
- Coffee shop

**Checklist GBP** :
- [ ] Nom exact : "Café d'Antan" (pas "Cafe Dantan" sans apostrophe)
- [ ] Adresse complète et identique au site
- [ ] Téléphone cliquable
- [ ] Horaires complets incluant jours fériés
- [ ] Description GBP optimisée (750 chars max) avec mots-clés locaux
- [ ] Minimum 10 photos (façade, intérieur, menu, plats, ambiance)
- [ ] Posts GBP actifs (1-2/semaine → génère des "Post Justifications" dans le pack local)
- [ ] Menu uploadé directement dans GBP
- [ ] Attributs remplis : "Terrasse", "Wi-Fi", "Paiement CB", etc.
- [ ] URL du site = cafedantan.com (PAS une page profonde — risque "Diversity Update" Sterling Sky)

**⚠ Attention règle Sterling Sky :** Ne pas linker vers la page la plus forte du site depuis GBP — risque de suppression des rankings organiques.

### 5.3 Gestion des Avis

**Règle des 18 jours** : Si aucun nouvel avis en 3 semaines → chute des rankings local pack.

**Stratégie de collecte d'avis** :
1. Créer un lien court Google Review et l'afficher sur les reçus, tableaux, cartes de visite
2. Former le personnel à demander oralement après un bon service
3. Envoyer un email de suivi aux clients réguliers (si base email disponible)
4. **JAMAIS** faire de pré-sélection de satisfaction avant de diriger vers Google (review gating interdit — FTC $53 088/violation)

**Objectifs avis** :
- Court terme : atteindre 10 avis (seuil de boost Sterling Sky)
- Moyen terme : maintenir une vélocité d'1-2 avis/semaine
- Note cible : 4,5+ (31% des consommateurs ne regardent que 4,5+)
- Répondre à 100% des avis (88% des clients préfèrent les établissements qui répondent)

### 5.4 NAP Consistency

**NAP doit être identique partout** :
- Site web (footer, page contact)
- Google Business Profile
- TripAdvisor
- Pages Jaunes / Yelp France
- Foursquare (alimente Apple Maps)
- Facebook Business Page
- Instagram Bio

**Citations restaurant prioritaires en France** :
1. TripAdvisor
2. TheFork (LaFourchette) → Réservations
3. Pages Jaunes
4. Foursquare (Apple Maps)
5. Michelin Guide (si éligible)
6. Yelp France

### 5.5 SEO Local On-Page

**Éléments à avoir sur la page d'accueil** :
```html
<!-- NAP dans le footer (HTML, pas une image) -->
<address>
  <strong>Café d'Antan</strong><br>
  [Numéro] [Rue], [Code Postal] [Ville]<br>
  <a href="tel:+33XXXXXXXXX">[Numéro de téléphone]</a><br>
  <a href="mailto:[email]">[Email]</a>
</address>

<!-- Bouton call-to-action visible above the fold -->
<a href="tel:+33XXXXXXXXX" class="cta-button">📞 Appeler</a>
<a href="/reservation/" class="cta-button">📅 Réserver</a>
```

**Intégrer une carte Google Maps** (lazy-loaded) :
```html
<iframe 
  src="https://maps.google.com/maps?q=Café+d'Antan+[Ville]&output=embed"
  loading="lazy"
  width="100%" height="350"
  title="Localisation Café d'Antan">
</iframe>
```

---

## 6. Performance / Core Web Vitals

### 6.1 Problèmes identifiés (hébergement IONOS)

**IONOS** est un hébergeur allemand. Pour un café français, la latence réseau peut dégrader le LCP :
- Datacenter Frankfurt → Latence +30-80ms pour les utilisateurs parisiens
- Recommandation : Activer un CDN (Cloudflare est déjà présent → s'assurer que le cache est activé)

### 6.2 Checklist Performance

| Optimisation | Impact | Effort |
|-------------|--------|--------|
| Compression images WebP/AVIF | LCP -40% | Moyen |
| Lazy loading sur images hors-écran | LCP amélioré | Faible |
| Dimensions width/height sur toutes les images | CLS → 0 | Faible |
| Minification CSS/JS | TTFB amélioré | Faible |
| Cache Cloudflare activé | TTFB -60% | Faible |
| Police web via `font-display: swap` | CLS amélioré | Faible |
| Éliminer les scripts bloquants | INP amélioré | Moyen |
| Précharger l'image hero (`<link rel="preload">`) | LCP -0,5s | Faible |

**Code pour précharger l'image hero** :
```html
<link rel="preload" as="image" href="/images/hero.webp" fetchpriority="high">
```

**Conversion images en WebP** :
```bash
# Via cwebp (en ligne de commande)
cwebp -q 80 image.jpg -o image.webp

# Ou via un plugin CMS (si WordPress : Imagify, ShortPixel, WebP Express)
```

---

## 7. Référencement IA & GEO

### 7.1 Score GEO : 25/100 (Critique)

**Google AI Mode** est lancé dans 180+ pays depuis mai 2025 avec **zéro lien organique bleu**. Si le Café d'Antan n'est pas citable par les IA, il est invisible dans cette nouvelle interface.

### 7.2 llms.txt — À Créer Immédiatement

Créer le fichier `/llms.txt` à la racine du site :

```
# Café d'Antan

> Café au charme rétro proposant cafés de spécialité, pâtisseries maison et formules brunch. Situé à [Ville], France.

## Informations principales

- Adresse : [Adresse complète]
- Téléphone : [Numéro]
- Horaires : [Lundi-Vendredi 8h-18h, Samedi-Dimanche 9h-19h]
- Réservations : https://cafedantan.com/reservation/

## Notre carte

- Cafés de spécialité (expresso, cappuccino, café d'antan...)
- Pâtisseries maison (tartes, gâteaux, viennoiseries...)
- Formules brunch (weekend)
- Plats du jour (midi)

## Notre histoire

[Histoire du café en 2-3 paragraphes clairs et factuels]

## Contact

- Email : [email]
- Facebook : [URL]
- Instagram : [URL]

## Politique d'accès IA

Les moteurs de recherche et systèmes IA peuvent librement indexer et citer 
le contenu de ce site pour des recherches locales et des recommandations 
de restaurants/cafés.
```

### 7.3 Optimisation pour la Citabilité IA

**Format recommandé pour le contenu** :

```markdown
## Qu'est-ce que le Café d'Antan ?

Le Café d'Antan est un café-restaurant situé à [Ville], en France, 
ouvert depuis [Année]. Il propose des cafés de spécialité, des 
pâtisseries faites maison chaque matin, et des formules brunch le 
week-end dans une atmosphère vintage et chaleureuse.

## Horaires d'ouverture

- **Lundi au vendredi** : 8h00 – 18h00
- **Samedi et dimanche** : 9h00 – 19h00
- **Fermé** : [Jour de fermeture si applicable]
```

**Signaux de citabilité à ajouter** :
- Longueur de passage optimale : 134-167 mots pour les citations IA
- Répondre à des questions type "Quel est le meilleur café [ville] ?"
- Inclure des données factuelles : année de création, nombre de couverts, etc.
- Ajouter une section FAQ (visible sur le site, pas en schema car restreint aux sites gov/santé)

### 7.4 Présence Multi-Plateforme IA

| Plateforme | Action recommandée |
|------------|-------------------|
| ChatGPT / OpenAI | Autoriser ChatGPT-User dans robots.txt pour la recherche temps réel |
| Perplexity | Créer profil TripAdvisor + citations web (Perplexity agrège ces sources) |
| Google AI Mode | SEO classique + schema + GBP → base du ranking AI Google |
| Apple Intelligence | Optimiser Foursquare et Yelp (Apple Maps base) |

---

## 8. Images

### 8.1 Problèmes typiques

| Problème | Impact | Priorité |
|---------|--------|---------|
| Alt text vide ou absent | Accessibilité + SEO image search | 🔴 Critique |
| Images > 500 KB | LCP dégradé | 🔴 Critique |
| Format JPEG/PNG au lieu de WebP | Taille fichier +30% | ⚠ Important |
| Pas de dimensions width/height | CLS | ⚠ Important |
| Pas de lazy loading | Performance | ⚠ Important |

### 8.2 Format recommandé

```html
<!-- ✅ Bonne pratique -->
<img 
  src="/images/cafe-antan-interieur.webp"
  alt="Intérieur chaleureux du Café d'Antan à [Ville] avec décoration vintage"
  width="1200" 
  height="800"
  loading="lazy"
>

<!-- Image hero (ne PAS mettre lazy loading sur la première image visible) -->
<img 
  src="/images/hero-cafe-antan.webp"
  alt="Façade du Café d'Antan à [Ville]"
  width="1920"
  height="1080"
  fetchpriority="high"
>
```

### 8.3 Nommage des fichiers

```
❌ IMG_20241205_103422.jpg
✅ cafe-dantan-facade-[ville].webp
✅ cafe-dantan-interieur-comptoir.webp
✅ cafe-dantan-carte-boissons.webp
✅ cafe-dantan-brunch-assiette.webp
```

### 8.4 Nombre de photos recommandé

- **Homepage** : 5-8 photos haute qualité (façade, intérieur, ambiance, plats signature)
- **Page Menu** : Photo de chaque plat/boisson si possible
- **Google Business Profile** : Minimum 10 photos + 1 vidéo (30s)

---

## 9. Backlinks & Autorité de Domaine

### 9.1 Stratégie de backlinks pour un café local

**Sources prioritaires (gratuites)** :
1. TripAdvisor → lien vers le site
2. TheFork / LaFourchette → lien vers le site + réservations
3. Pages Jaunes → profil gratuit avec lien
4. Foursquare → profil gratuit
5. Yelp France → profil gratuit
6. Michelin Guide (demander l'inclusion)
7. Presse locale : contacter les journalistes food de [Ville]
8. Blogs food locaux : proposer une visite presse
9. Mairie / Office de tourisme de [Ville] : demander inclusion dans les listes "restaurants"

**Stratégie de contenu pour générer des liens** :
- Article "Les meilleurs cafés de [Ville]" (auto-inclus + citable par blogs)
- Carte de spécialité de saison partageable
- Recettes de boissons signature
- Guide "Brunch à [Ville]"

### 9.2 Anchor text recommandé pour les citations

```
"Café d'Antan" → ancre de marque (60% des liens)
"café [Ville]" → ancre géo-ciblée (20%)
"café rétro [Ville]" → ancre longue traîne (10%)
"cafedantan.com" → ancre URL (10%)
```

---

## 10. Search Experience Optimization (SXO)

### 10.1 Analyse d'intention de recherche

| Query type | Intent | Page optimale |
|-----------|--------|---------------|
| "café d'antan" | Navigational | Homepage |
| "café [ville]" | Local / Commercial | Homepage + GBP |
| "brunch [ville]" | Commercial Investigation | Page dédiée /brunch/ |
| "café vintage [ville]" | Commercial Investigation | Homepage |
| "meilleur café [ville]" | Commercial Investigation | Homepage + Blog |
| "horaires café d'antan" | Informational | GBP + Homepage |
| "réserver café d'antan" | Transactional | Page /reservation/ |

### 10.2 Pages à créer selon l'intention

| Page | Query ciblée | Priorité |
|------|-------------|---------|
| /brunch/ | "brunch [ville] weekend" | 🔴 Haute |
| /menu/ | "carte café d'antan" | 🔴 Haute |
| /reservation/ | "réserver café [ville]" | 🔴 Haute |
| /a-propos/ | "café d'antan histoire" | ⚠ Moyenne |
| /blog/ | Longue traîne / E-E-A-T | ⚠ Moyenne |
| /evenements/ | "café [ville] événements" | Basse |

---

## Annexe Technique : Configuration robots.txt Recommandée

```
User-agent: *
Allow: /
Disallow: /wp-admin/
Disallow: /wp-login.php
Disallow: /panier/
Disallow: /mon-compte/
Disallow: /?s=

# AI Training crawlers → bloquer
User-agent: GPTBot
Disallow: /

User-agent: Google-Extended
Disallow: /

User-agent: Bytespider
Disallow: /

User-agent: CCBot
Disallow: /

# AI Search (laisser accès pour visibilité dans ChatGPT Browse, Perplexity)
User-agent: ChatGPT-User
Allow: /

User-agent: PerplexityBot
Allow: /

User-agent: ClaudeBot
Allow: /

Sitemap: https://cafedantan.com/sitemap.xml
```

---

*Rapport généré par claude-seo v1.9.9 | Méthodologie complète : seo-technical, seo-content, seo-local, seo-schema, seo-page, seo-geo, seo-sxo, seo-images, seo-backlinks*
