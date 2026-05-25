# AUDIT SEO COMPLET — CAFÉ D'ANTAN
## Document de briefing pour ChatGPT — SEO Local Paris

---

## 1. IDENTITÉ DU BUSINESS

| Champ | Info |
|-------|------|
| **Nom** | Café d'Antan |
| **Type** | Coffee Shop · Matcha Bar · Torréfacteur artisanal · Fournisseur B2B |
| **Adresse** | 36 rue de la Lune, 75002 Paris, France |
| **Arrondissement** | Paris 2e — Quartier Bonne Nouvelle |
| **Métro** | Bonne Nouvelle (L8, L9) · Strasbourg-Saint-Denis (L4, L8, L9) |
| **Quartiers proches** | Bonne Nouvelle, Grands Boulevards, Sentier, Montorgueil, République |
| **Hébergement** | IONOS (IP : 217.160.0.3) — serveur Allemagne |
| **Domaine** | cafedantan.com |
| **SSL** | ✅ Valide (TLS 1.3) |
| **CDN** | Cloudflare actif |

---

## 2. OFFRE COMMERCIALE

### B2C (Grand public)
- Café de spécialité (espresso, V60, Chemex, Cold Brew, AeroPress)
- Matcha bar (matcha latte, matcha glacé, matcha cérémonial pur)
- Torréfaction artisanale — vente café en grain (250g, 500g, 1kg)
- Pâtisseries maison
- Espace de travail (wifi, prises électriques)

### B2B (Professionnels)
- Fournisseur café de spécialité pour restaurants, hôtels, coffee shops
- Formation barista sur site
- Livraison Paris & Île-de-France
- Contrats de fourniture sur mesure

### Style / positionnement
- Premium, haut de gamme
- Café de spécialité (score SCA > 85/100)
- Matcha de grade cérémonial importé du Japon (Uji, Nishio)
- Origines café directes : Brésil (Serra do Caparaó), Éthiopie (Yirgacheffe), Colombie (Huila), Guatemala (Antigua)

---

## 3. MOTS-CLÉS CIBLES (validés)

### Priorité 1 — Volume fort, intention locale directe
```
coffee shop paris 2
matcha bar paris
matcha latte paris
café de spécialité paris
coffee shop bonne nouvelle
coffee shop grands boulevards
torréfacteur paris
café en grain paris
```

### Priorité 2 — B2B
```
café professionnel paris
café pour restaurant paris
fournisseur café paris
café pour coffee shop paris
```

### Priorité 3 — Longue traîne géographique
```
coffee shop sentier paris
coffee shop montorgueil paris
coffee shop strasbourg saint-denis
café de spécialité paris 2
matcha paris 2
coffee shop laptop paris 2
```

---

## 4. ARCHITECTURE DE SITE RECOMMANDÉE

```
cafedantan.com/                        → Homepage (pilier central)
├── /coffee-shop-paris-2/              → Page pilier SEO local (PRIORITÉ 1)
├── /matcha-bar-paris/                 → Vertical matcha
├── /matcha-latte-paris/               → Longue traîne matcha
├── /torrefacteur-paris/               → Vertical torréfaction
├── /cafe-de-specialite-paris/         → Café de spécialité
├── /cafe-en-grain-paris/              → E-commerce / achat
├── /menu/                             → Carte complète
├── /reservation/                      → Réservation
│
├── SEO GÉOGRAPHIQUE
│   ├── /coffee-shop-bonne-nouvelle/
│   ├── /coffee-shop-grands-boulevards/
│   ├── /coffee-shop-sentier/
│   └── /coffee-shop-montorgueil/
│
├── B2B
│   ├── /cafe-professionnel-paris/     → Hub B2B
│   └── /cafe-pour-restaurants/        → Niche restaurant
│
├── /a-propos/                         → E-E-A-T / histoire
├── /blog/                             → Contenu longue traîne
└── /contact/                          → NAP + Maps
```

**Problèmes existants à corriger :**
- `/cuisine` → ajouter `<meta name="robots" content="noindex, nofollow">` (page interne à masquer)
- `/site` → cannibalise `/coffee-shop-pro` → rediriger 301 `/site` vers `/coffee-shop-pro`

---

## 5. AUDIT TECHNIQUE

### 5.1 Problèmes critiques détectés

| Problème | Impact | Correction |
|---------|--------|------------|
| **Schema JSON-LD absent** | Pas de rich results Google | Implémenter CafeOrCoffeeShop |
| **Cloudflare WAF trop agressif** | Risque blocage Googlebot | Autoriser "Verified Bots" dans Cloudflare |
| **Pas de llms.txt** | Invisible pour ChatGPT/Perplexity | Créer /llms.txt |
| **Cannibalisation /site vs /coffee-shop-pro** | Dilution SEO B2B | Redirection 301 |
| **/cuisine indexée** | Page interne dans Google | Noindex |
| **Hébergement IONOS Allemagne** | LCP lent pour Paris | Activer cache Cloudflare niveau "Standard" |
| **Pas de sitemap déclaré** | Crawl sous-optimal | Créer et soumettre sitemap.xml |
| **Pas de IndexNow** | Indexation Bing lente | Implémenter IndexNow |

### 5.2 Sécurité — Headers manquants (à ajouter dans Cloudflare)
```
Strict-Transport-Security: max-age=31536000; includeSubDomains
X-Content-Type-Options: nosniff
X-Frame-Options: SAMEORIGIN
Referrer-Policy: strict-origin-when-cross-origin
```

### 5.3 Core Web Vitals — Objectifs
| Métrique | Cible | Risque actuel |
|---------|-------|---------------|
| LCP | < 2,5s | ⚠ Hébergement DE sans cache |
| INP | < 200ms | À mesurer |
| CLS | < 0,1 | Risque si images sans dimensions |

### 5.4 robots.txt recommandé
```
User-agent: *
Allow: /
Disallow: /cuisine
Disallow: /wp-admin/

# Bloquer entraînement IA
User-agent: GPTBot
Disallow: /
User-agent: Google-Extended
Disallow: /
User-agent: Bytespider
Disallow: /

# Autoriser recherche IA (visibilité ChatGPT, Perplexity)
User-agent: ChatGPT-User
Allow: /
User-agent: PerplexityBot
Allow: /

Sitemap: https://cafedantan.com/sitemap.xml
```

---

## 6. SCHEMA JSON-LD À IMPLÉMENTER

### 6.1 Schema principal (toutes pages)
```json
{
  "@context": "https://schema.org",
  "@type": ["CafeOrCoffeeShop", "Restaurant"],
  "@id": "https://cafedantan.com/#business",
  "name": "Café d'Antan",
  "url": "https://cafedantan.com",
  "description": "Coffee shop premium, matcha bar et torréfacteur artisanal au 36 rue de la Lune, Paris 2e. Café de spécialité, matcha japonais, offre B2B.",
  "servesCuisine": ["Café de spécialité", "Matcha", "Pâtisseries"],
  "priceRange": "€€",
  "acceptsReservations": true,
  "menu": "https://cafedantan.com/menu/",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "36 rue de la Lune",
    "addressLocality": "Paris",
    "postalCode": "75002",
    "addressCountry": "FR"
  },
  "geo": {
    "@type": "GeoCoordinates",
    "latitude": 48.8671,
    "longitude": 2.3504
  },
  "telephone": "[À REMPLIR]",
  "openingHoursSpecification": [
    {
      "@type": "OpeningHoursSpecification",
      "dayOfWeek": ["Monday","Tuesday","Wednesday","Thursday","Friday"],
      "opens": "08:00",
      "closes": "18:00"
    },
    {
      "@type": "OpeningHoursSpecification",
      "dayOfWeek": ["Saturday","Sunday"],
      "opens": "09:00",
      "closes": "19:00"
    }
  ],
  "aggregateRating": {
    "@type": "AggregateRating",
    "ratingValue": "[NOTE GOOGLE]",
    "reviewCount": "[NOMBRE D'AVIS]",
    "bestRating": "5"
  },
  "sameAs": [
    "https://www.facebook.com/[PAGE]",
    "https://www.instagram.com/[COMPTE]",
    "https://www.tripadvisor.fr/[PROFIL]"
  ]
}
```

### 6.2 Schema FAQ (homepage + pages ciblées)
Questions validées SEO :
1. Où trouver un coffee shop à Paris 2 ?
2. Où boire un matcha latte à Paris ?
3. Peut-on acheter du café en grain sur place ?
4. Le café est-il torréfié à Paris ?
5. Proposez-vous du café pour les restaurants ?
6. Peut-on travailler dans le coffee shop ?
7. Quels types de cafés proposez-vous ?
8. Quelle est la différence entre café de spécialité et café classique ?

### 6.3 BreadcrumbList (chaque page interne)
```json
{
  "@type": "BreadcrumbList",
  "itemListElement": [
    {"@type":"ListItem","position":1,"name":"Accueil","item":"https://cafedantan.com/"},
    {"@type":"ListItem","position":2,"name":"[Titre page]","item":"https://cafedantan.com/[slug]/"}
  ]
}
```

---

## 7. SEO LOCAL — ANALYSE COMPLÈTE

### 7.1 Google Business Profile (GBP) — Checklist prioritaire

**Catégorie principale recommandée :** `Café` (ou `Coffee shop`)

**Catégories secondaires (max 9) :**
- Salon de thé
- Restaurant
- Torréfacteur
- Boutique de café
- Bar à thé

**Facteurs de ranking local (Whitespark 2026) :**
| Facteur | Poids | Statut |
|---------|-------|--------|
| Catégorie GBP principale | 32% signaux GBP | À vérifier |
| Mots-clés dans titre GBP | Élevé | À vérifier |
| Proximité utilisateur | 55,2% variance | Géographique |
| GBP vérifié | Critique | À confirmer |
| Quantité avis Google | 19,2% variance | À développer |
| Vitesse des avis (18 jours) | Critique | Stratégie à mettre en place |

**Checklist GBP à compléter :**
- [ ] Nom exact : "Café d'Antan" (respecter apostrophe)
- [ ] Adresse : 36 rue de la Lune, 75002 Paris
- [ ] Téléphone cliquable (même numéro partout = NAP consistency)
- [ ] Horaires complets + jours fériés
- [ ] Description 750 caractères avec mots-clés locaux
- [ ] Minimum 10 photos (façade, intérieur, menu, matcha, ambiance)
- [ ] 1 vidéo 30 secondes
- [ ] Menu uploadé dans GBP
- [ ] Attributs : "Wi-Fi gratuit", "Prises électriques", "Terrasse", "Adapté au télétravail"
- [ ] Posts GBP actifs (1-2 par semaine)
- [ ] URL du site = cafedantan.com (pas une page profonde)

⚠️ **Règle Sterling Sky :** Ne jamais linker vers votre meilleure page depuis GBP — risque de pénalité rankings organiques.

### 7.2 Règle des 18 jours (Sterling Sky)
> Si aucun nouvel avis pendant 3 semaines → chute des rankings dans le Local Pack.

**Stratégie avis :**
- Créer un lien court Google Review (sur reçus, cartes de visite, tableau en caisse)
- Former le personnel à demander oralement
- Objectif court terme : **10 avis** (seuil de boost Sterling Sky)
- Objectif moyen terme : **1-2 avis/semaine** minimum
- Note cible : **4,5 étoiles** (31% des consommateurs en-dessous ne cliquent pas)
- Répondre à 100% des avis (88% préfèrent les établissements qui répondent)
- ❌ **Interdit** : review gating (pré-sélection satisfaction avant Google) → FTC $53 088/violation

### 7.3 NAP Consistency — À uniformiser partout
```
Nom      : Café d'Antan
Adresse  : 36 rue de la Lune, 75002 Paris
Téléphone: [Même numéro partout]
```

**Plateformes à aligner :**
1. Site web (footer, page contact, header)
2. Google Business Profile
3. TripAdvisor
4. TheFork / LaFourchette (+ réservations)
5. Pages Jaunes
6. Foursquare → alimente Apple Maps
7. Yelp France
8. Facebook Business Page
9. Instagram Bio

### 7.4 Citations locales prioritaires (restaurants Paris)
| Plateforme | Priorité | Action |
|-----------|---------|--------|
| TripAdvisor | 🔴 Critique | Créer/revendiquer profil |
| TheFork | 🔴 Critique | Activer réservations |
| Pages Jaunes | 🟠 Haute | Vérifier fiche |
| Foursquare | 🟠 Haute | Créer profil (Apple Maps) |
| Michelin Guide | 🟡 Moyenne | Demander inclusion |
| Yelp France | 🟡 Moyenne | Créer profil |

### 7.5 SEO local on-page — Éléments requis

**Dans le footer (HTML texte, jamais une image) :**
```html
<address>
  <strong>Café d'Antan</strong><br>
  36 rue de la Lune, 75002 Paris<br>
  <a href="tel:+33XXXXXXXXX">+33 1 XX XX XX XX</a>
</address>
```

**Dans le titre de la homepage :**
`Coffee Shop Paris 2 | Café d'Antan — Matcha Bar & Torréfacteur`

**Dans le H1 de la homepage :**
`Café d'Antan — Coffee Shop, Matcha Bar & Torréfacteur à Paris 2`

**Pages géo-ciblées à créer :**
- `/coffee-shop-bonne-nouvelle/` → 500+ mots, métro L8-L9
- `/coffee-shop-grands-boulevards/` → 500+ mots
- `/coffee-shop-sentier/` → 500+ mots
- `/coffee-shop-montorgueil/` → 500+ mots

**Contenu géo à intégrer sur toutes les pages :**
```
"situé à 3 minutes du métro Bonne Nouvelle (lignes 8 et 9)"
"à 5 minutes du quartier Sentier"
"à 2 minutes des Grands Boulevards"
"à 7 minutes de la rue Montorgueil"
"proche de Strasbourg-Saint-Denis"
"au cœur du 2e arrondissement de Paris"
```

---

## 8. CONTENU — RECOMMANDATIONS E-E-A-T

### 8.1 Score E-E-A-T estimé : 28/100

| Dimension | Problème | Solution |
|-----------|---------|---------|
| Expérience | Pas d'histoire du fondateur | Page /a-propos/ avec vraie histoire |
| Expertise | Pas de bio du torréfacteur | Présenter le maître torréfacteur |
| Autorité | Peu de backlinks | Citations TripAdvisor, presse locale |
| Confiance | Mentions légales/RGPD ? | Vérifier et compléter |

### 8.2 Plan de contenu blog (longue traîne)
| Article | Intent | Priorité |
|---------|--------|---------|
| "Les meilleurs coffee shops de Paris 2 en 2026" | Informationnel | 🔴 |
| "Qu'est-ce que le café de spécialité ?" | Informationnel | 🔴 |
| "Matcha vs café : lequel choisir ?" | Informationnel | 🟠 |
| "Notre sélection de cafés Brésil" | Commercial | 🟠 |
| "Guide du brunch à Bonne Nouvelle" | Commercial | 🟡 |
| "Comment préparer un V60 à la maison" | Informationnel | 🟡 |

---

## 9. OPTIMISATION PERFORMANCE

### Checklist technique immédiate
```
☐ Activer cache Cloudflare (niveau Standard ou Aggressive)
☐ Convertir toutes les images en WebP/AVIF
☐ Ajouter loading="lazy" sur images hors-écran
☐ Ajouter width/height sur toutes les images (prévention CLS)
☐ Preload image hero : <link rel="preload" as="image" href="/hero.webp" fetchpriority="high">
☐ font-display: swap sur toutes les polices
☐ Minifier CSS et JS
☐ Supprimer scripts tiers inutiles
```

### Objectif Lighthouse
- Mobile : > 85/100
- Desktop : > 90/100

---

## 10. VISIBILITÉ IA (GEO — Google AI Mode, ChatGPT, Perplexity)

### Contexte 2026
- Google AI Mode lancé dans 180+ pays (mai 2025) avec **zéro lien bleu** → seules les citations IA donnent de la visibilité
- ChatGPT local conversion rate : **15,9%** vs 1,76% pour Google organique (Seer Interactive)
- 45% des recherches locales passent par ChatGPT/IA (BrightLocal 2026)

### Actions immédiates
1. **Créer /llms.txt** à la racine du site avec toutes les infos business
2. **Autoriser ChatGPT-User et PerplexityBot** dans robots.txt
3. **Structurer le contenu** en blocs de 134-167 mots (longueur optimale pour citation IA)
4. **Format question/réponse** sur les pages (répond aux queries conversationnelles)
5. **Données factuelles précises** : adresse exacte, horaires, prix, coordonnées GPS

### Exemple contenu optimisé IA
```
Café d'Antan est un coffee shop situé au 36 rue de la Lune,
dans le 2e arrondissement de Paris (75002). Ouvert depuis [année],
l'établissement propose des cafés de spécialité torréfiés artisanalement
sur place, un matcha bar avec des matchas de grade cérémonial importés
du Japon, et une offre B2B pour restaurants et hôtels.
Horaires : lundi-vendredi 8h-18h, samedi-dimanche 9h-19h.
Métro : Bonne Nouvelle (lignes 8 et 9).
```

---

## 11. PLAN D'ACTION PRIORISÉ

### 🔴 CETTE SEMAINE (impact immédiat)
1. Noindex sur `/cuisine`
2. Redirection 301 `/site` → `/coffee-shop-pro`
3. Déployer schema JSON-LD `CafeOrCoffeeShop` sur toutes les pages
4. Modifier H1 homepage
5. Corriger title tags toutes les pages (inclure la ville)
6. Créer `/llms.txt`
7. Vérifier et optimiser Google Business Profile

### 🟠 DANS 2 SEMAINES
8. Créer page `/matcha-bar-paris/` (1000+ mots)
9. Créer page `/coffee-shop-paris-2/` (1200+ mots)
10. Créer page `/torrefacteur-paris/` (1000+ mots)
11. Ajouter NAP dans footer (HTML)
12. Intégrer Google Maps embed (lazy-load)
13. Stratégie avis : viser 10 avis Google

### 🟡 DANS LE MOIS
14. 4 pages géo-ciblées (Bonne Nouvelle, Grands Boulevards, Sentier, Montorgueil)
15. 2 pages B2B (`/cafe-professionnel-paris/`, `/cafe-pour-restaurants/`)
16. Optimisation images WebP + lazy loading
17. Inscription TripAdvisor, TheFork, Foursquare
18. Premier article de blog (longue traîne)

---

## 12. PROMPT À DONNER À CHATGPT

```
Tu es un expert SEO local spécialisé dans les coffee shops et restaurants à Paris.

CONTEXTE BUSINESS :
- Établissement : Café d'Antan
- Type : Coffee Shop + Matcha Bar + Torréfacteur artisanal + B2B
- Adresse : 36 rue de la Lune, 75002 Paris (quartier Bonne Nouvelle)
- Métro : Bonne Nouvelle (L8-L9)
- Quartiers proches : Bonne Nouvelle, Grands Boulevards, Sentier, Montorgueil
- Horaires : Lun-Ven 8h-18h / Sam-Dim 9h-19h
- Positionnement : Premium, café de spécialité (score SCA > 85), matcha japonais grade cérémonial, torréfacteur indépendant

PROBLÈMES À RÉSOUDRE :
[Copier les sections 5, 6 ou 7 de ce document selon le besoin]

DEMANDE :
[Ex: "Rédige le contenu SEO optimisé pour la page /matcha-bar-paris/ (1200 mots, inclus FAQ, ciblé Paris 2)"]
[Ex: "Génère le schema JSON-LD complet pour la homepage"]
[Ex: "Rédige une description GBP optimisée de 750 caractères"]
[Ex: "Crée 10 questions/réponses FAQ optimisées SEO local pour Paris 2"]
```

---

*Audit réalisé avec claude-seo v1.9.9 (25 skills) — Méthodologie : seo-technical, seo-local, seo-schema, seo-content, seo-geo, seo-page, seo-sxo*
*Date : 2026-05-16 | Business : Café d'Antan, 36 rue de la Lune, 75002 Paris*
