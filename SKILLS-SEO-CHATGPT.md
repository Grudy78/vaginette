# SKILLS SEO — Méthodologies complètes
## Document de référence pour ChatGPT · claude-seo v1.9.9
### Source : github.com/AgriciDaniel/claude-seo

---

> **Comment utiliser ce document avec ChatGPT :**
> Copie-colle la ou les sections dont tu as besoin selon ta demande.
> Ex : tu veux optimiser ton SEO local → copie la section "SKILL 2 : SEO Local".
> Tu veux rédiger du contenu → copie "SKILL 3 : Contenu & E-E-A-T".

---

## SKILL 1 : SEO TECHNIQUE

**Ce que ça couvre :** 9 catégories d'audit technique complet.

---

### 1.1 Crawlabilité
**Vérifications :**
- robots.txt : existe, valide, ne bloque pas les ressources importantes
- Sitemap XML : existe, référencé dans robots.txt, format valide
- Balises noindex : intentionnelles vs accidentelles
- Profondeur de crawl : pages importantes accessibles en < 3 clics depuis la homepage
- Rendu JavaScript : le contenu critique ne doit pas dépendre du JS pour être visible
- Budget de crawl : pour les grands sites (+10 000 pages)

**Gestion des crawlers IA (2025-2026) :**
| Crawler | Entreprise | robots.txt | Usage |
|---------|-----------|-----------|-------|
| GPTBot | OpenAI | `GPTBot` | Entraînement modèle |
| ChatGPT-User | OpenAI | `ChatGPT-User` | Navigation temps réel |
| ClaudeBot | Anthropic | `ClaudeBot` | Entraînement modèle |
| PerplexityBot | Perplexity | `PerplexityBot` | Index + entraînement |
| Bytespider | ByteDance | `Bytespider` | Entraînement modèle |
| Google-Extended | Google | `Google-Extended` | Entraînement Gemini (pas Search) |

⚠️ Bloquer `Google-Extended` n'affecte PAS le référencement Google Search ni les AI Overviews.

---

### 1.2 Indexabilité
- Canonical tags : auto-référençants, sans conflit avec noindex
- Contenu dupliqué : quasi-duplicates, URLs avec paramètres, www vs non-www
- Contenu thin : pages en dessous du minimum de mots selon le type
- Pagination : rel=next/prev ou pattern load-more
- Hreflang : correct pour sites multi-langues/multi-régions
- Gonflement d'index : pages inutiles qui consomment du budget de crawl

---

### 1.3 Sécurité
**Headers à vérifier et implémenter :**
```
Content-Security-Policy (CSP)
Strict-Transport-Security (HSTS)
X-Frame-Options
X-Content-Type-Options
Referrer-Policy
```

---

### 1.4 Structure d'URL
- URLs propres : descriptives, avec tirets, sans paramètres de requête pour le contenu
- Hiérarchie : structure de dossiers logique reflétant l'architecture du site
- Redirections : pas de chaînes (max 1 saut), 301 pour les déplacements permanents
- Longueur d'URL : signaler > 100 caractères
- Slashes finaux : usage cohérent

---

### 1.5 Mobile
- Responsive design : balise viewport, CSS responsive
- Cibles tactiles : minimum 48×48px avec 8px d'espacement
- Taille de police : minimum 16px de base
- Pas de scroll horizontal
- **Mobile-first indexing : 100% effectif depuis le 5 juillet 2024.** Google indexe EXCLUSIVEMENT avec le Googlebot mobile.

---

### 1.6 Core Web Vitals (mise à jour 2024)
| Métrique | Cible | Notes |
|---------|-------|-------|
| **LCP** (Largest Contentful Paint) | < 2,5s | Temps de chargement principal |
| **INP** (Interaction to Next Paint) | < 200ms | Remplace FID depuis mars 2024. FID retiré définitivement en sept. 2024. Ne JAMAIS mentionner FID. |
| **CLS** (Cumulative Layout Shift) | < 0,1 | Stabilité visuelle |
- Évaluation au 75e percentile des données utilisateurs réels

---

### 1.7 Rendu JavaScript — Règles critiques (décembre 2025)
1. **Conflits canonical :** Si un canonical dans le HTML brut diffère d'un injecté par JS, Google peut utiliser l'un OU l'autre. S'assurer qu'ils sont identiques.
2. **noindex avec JavaScript :** Si le HTML brut contient `noindex` mais que JS le retire, Google PEUT quand même honorer le noindex du HTML.
3. **Codes HTTP non-200 :** Google ne rend PAS le JS sur les pages retournant un non-200.
4. **Données structurées en JS :** Peuvent subir un traitement retardé. Pour les données sensibles au temps (e-commerce), les inclure dans le HTML initial rendu côté serveur.

---

### 1.8 Protocole IndexNow
- Permet une indexation instantanée sur Bing, Yandex, Naver (pas Google)
- Recommandé pour toutes les publications et mises à jour de contenu
- Implémentation : générer une clé, déposer le fichier, appeler l'API

---

## SKILL 2 : SEO LOCAL (Mars 2026)

**Ce que ça couvre :** Google Business Profile, cohérence NAP, avis, schema local, pages de localisation.

---

### 2.1 Statistiques clés 2026
| Métrique | Valeur | Source |
|---------|--------|-------|
| Poids signaux GBP dans le Local Pack | 32% | Whitespark 2026 |
| Part de proximité dans la variance de ranking | 55,2% | Search Atlas ML |
| Signaux avis (hausse vs 16%) | ~20% | Whitespark 2026 |
| Recherches locales Google | 46% | Industry data |
| Recherches mobile "près de moi" → visite en 24h | 76% | Google confirmé |
| Usage ChatGPT/IA pour recommandations locales | 45% (vs 6%) | BrightLocal LCRS 2026 |
| Taux de conversion ChatGPT local | 15,9% | Seer Interactive |
| Taux de conversion organique local Google | 1,76% | Seer Interactive |

---

### 2.2 Détection du type de business
- **Brick-and-Mortar :** adresse physique visible, Google Maps embed, LocalBusiness schema
- **Service Area Business (SAB) :** pas d'adresse visible, mentions "nous intervenons à...", `areaServed` dans schema
- **Hybride :** les deux

---

### 2.3 Google Business Profile (GBP) — Facteurs de ranking

**Top 15 facteurs individuels Local Pack (Whitespark 2026) :**
1. Catégorie principale GBP (score : 193) — **#1 facteur positif ET négatif**
2. Mots-clés dans le nom GBP (score : 181)
3. Proximité de l'adresse au point de recherche (score : 176)
4. GBP vérifié
5. Business ouvert au moment de la recherche
6. Hautes notes Google (numériques)
7. Quantité d'avis Google natifs
8. Catégories GBP supplémentaires
9. Récence/vélocité des avis
10. Pages de services dédiées
11. Autorité de domaine
12. Cohérence NAP
13. Suppression de fiches spam
14. Backlinks de qualité
15. Sentiment des avis

**Top facteur négatif :** Catégorie principale incorrecte (score : 176)

**Checklist GBP :**
- [ ] Catégorie principale appropriée
- [ ] Description optimisée (750 chars max) avec mots-clés locaux
- [ ] Minimum 10 photos + 1 vidéo
- [ ] Posts GBP actifs (1-2/semaine → génère des "Post Justifications")
- [ ] Menu/services uploadés directement
- [ ] Attributs remplis
- [ ] Horaires complets incluant jours fériés
- [ ] URL du site = homepage (PAS une page profonde — risque "Diversity Update" Sterling Sky)

⚠️ **Note Q&A GBP :** La fonctionnalité Q&A a été supprimée en décembre 2025, remplacée par "Ask Maps Gemini AI". Recréer le contenu Q&A en sections FAQ sur le site web.

---

### 2.4 Avis & Réputation

**Règle des 18 jours (Sterling Sky) :** Les rankings "chutent d'une falaise" si aucun nouvel avis pendant 3 semaines. **La vélocité > le volume.**

**Benchmarks BrightLocal LCRS 2026 :**
| Métrique | Valeur |
|---------|--------|
| Ne regardent que les avis des 3 derniers mois | 74% |
| N'utilisent que les 4,5 étoiles et plus | 31% |
| N'utilisent que les 4 étoiles et plus | 68% |
| Nombre moyen de plateformes consultées | 6 |
| "Toujours" lisent les avis | 41% (vs 29% en 2025) |

**Seuil magique :** 10 avis Google = boost de ranking significatif (Sterling Sky).

**Interdit :** Le review gating (pré-sélection de satisfaction avant de diriger vers Google) est prohibé par Google ET la FTC ($53 088/violation, effectif oct. 2024).

**Plateformes d'avis 2026 :**
| Plateforme | Usage |
|-----------|-------|
| Google | 71% |
| Instagram | 37% |
| TikTok | 29% |
| Apple Maps | 27% (vs 14% en 2025) |

---

### 2.5 SEO local On-Page

**Pages de services dédiées = facteur #1 organique local ET #2 visibilité IA (Whitespark 2026)**

**Éléments requis :**
- Title tag avec ville + service (ex: "Coffee Shop Paris 2 | Café d'Antan")
- H1 avec intention locale (ville + service)
- NAP (Nom, Adresse, Téléphone) visible en HTML dans le footer
- Pages de services dédiées (une page par service principal)
- Google Maps embed (lazy-load pour la vitesse)
- Bouton click-to-call (`tel:` link) et formulaire de contact au-dessus de la ligne de flottaison
- 2-5 liens internes contextuels par 1 000 mots

**Schéma d'URL recommandé :**
```
domaine.com/locations/nom-ville/        (multi-localisation)
domaine.com/service-ville/              (SEO local)
domaine.com/service-quartier-ville/     (hyper-local)
```

---

### 2.6 Citations locales prioritaires (France — Restauration)
1. TripAdvisor
2. TheFork / LaFourchette (réservations)
3. Pages Jaunes
4. Foursquare (alimente Apple Maps, Uber)
5. Guide Michelin (si éligible)
6. Yelp France

---

## SKILL 3 : CONTENU & E-E-A-T

**Ce que ça couvre :** Qualité du contenu, signaux E-E-A-T, préparation pour citations IA.

---

### 3.1 Framework E-E-A-T (mis à jour QRG sept. 2025)

> **Mise à jour critique — Core Update décembre 2025 :**
> L'E-E-A-T s'applique désormais à TOUTES les requêtes compétitives, pas seulement YMYL.
> Le contenu anonyme ou générique ne rankera plus, même hors thématiques YMYL.

**4 dimensions :**

**Experience (Expérience) — Poids 20%**
- Contenu de recherche originale, études de cas, résultats avant/après
- Anecdotes personnelles, documentation de processus
- Photos/vidéos de l'expérience directe
- Données uniques et propriétaires

**Expertise — Poids 25%**
- Crédentiels de l'auteur, certifications, bio visible
- Précision technique appropriée à l'audience
- Affirmations sourcées
- Byline avec nom et crédentiels de l'auteur visible

**Authoritativeness (Autorité) — Poids 30%**
- Citations externes, backlinks de sources autoritaires
- Mentions de marque, reconnaissance du secteur
- Publié dans des outlets reconnus
- Cité par d'autres experts

**Trustworthiness (Confiance) — Poids 25%**
- Informations de contact, adresse physique
- Politique de confidentialité, CGU
- Témoignages clients, avis
- Site sécurisé (HTTPS)
- Dates de publication et de mise à jour visibles

---

### 3.2 Minimums de contenu par type de page
| Type de page | Minimum |
|-------------|---------|
| Homepage | 500 mots |
| Page de service | 800 mots |
| Article de blog | 1 500 mots |
| Page produit | 300+ mots (400+ pour produits complexes) |
| Page de localisation | 500-600 mots |

⚠️ Ces minimums sont des **planchers de couverture thématique**, pas des cibles. Google ne classe pas le nombre de mots directement. Une page de 500 mots qui répond parfaitement à la requête surclassera une page de 2 000 mots qui ne le fait pas.

---

### 3.3 Préparation pour citations IA (GEO)

**Longueur de passage optimale pour citation IA : 134-167 mots**

**Signaux forts :**
- Phrases claires et citables avec faits/statistiques spécifiques
- Blocs de réponse autonomes (extractibles sans contexte)
- Réponse directe dans les 40-60 premiers mots d'une section
- Affirmations attribuées à des sources spécifiques
- Définitions suivant le pattern "X est..." ou "X désigne..."
- Données uniques non trouvables ailleurs

**Format recommandé pour une page :**
```
## Question directe en H2 ?

Réponse directe en 1-2 phrases (les 40 premiers mots).
Développement avec données factuelles spécifiques.
Exemple concret ou statistique avec source.
Conclusion actionnable.
[134-167 mots total pour le paragraphe]
```

---

### 3.4 Contenu IA — Ce qui est acceptable vs problématique

**Acceptable :**
- Démontre un vrai E-E-A-T
- Apporte une valeur unique
- Supervision et édition humaine
- Contient des insights originaux

**Marqueurs de mauvais contenu IA :**
- Formulations génériques, manque de spécificité
- Pas d'insight original
- Structure répétitive d'une page à l'autre
- Pas d'attribution d'auteur
- Inexactitudes factuelles

---

## SKILL 4 : SCHEMA & DONNÉES STRUCTURÉES

**Ce que ça couvre :** Détection, validation, génération de schema.org en JSON-LD.

---

### 4.1 Statut des types schema (février 2026)

**ACTIF — Recommander librement :**
Organization, LocalBusiness, SoftwareApplication, Product, Offer, Service, Article, BlogPosting, Review, AggregateRating, BreadcrumbList, WebSite, WebPage, Person, Event, JobPosting, Menu, MenuItem

**RESTREINT :**
- **FAQ** : UNIQUEMENT pour sites gouvernementaux et autorités de santé (restreint août 2023)

**DÉPRÉCIÉ — Ne JAMAIS recommander :**
- **HowTo** : Rich results supprimés septembre 2023
- **SpecialAnnouncement** : Déprécié juillet 2025
- **CourseInfo, EstimatedSalary, LearningVideo** : Retirés juin 2025
- **ClaimReview** : Retiré des rich results juin 2025
- **VehicleListing** : Retiré juin 2025

---

### 4.2 Templates schema essentiels

**CafeOrCoffeeShop (pour cafés/coffee shops) :**
```json
{
  "@context": "https://schema.org",
  "@type": ["CafeOrCoffeeShop", "Restaurant"],
  "@id": "https://exemple.com/#business",
  "name": "Nom de l'établissement",
  "url": "https://exemple.com",
  "description": "Description optimisée SEO",
  "servesCuisine": ["Café de spécialité", "Matcha"],
  "priceRange": "€€",
  "acceptsReservations": true,
  "menu": "https://exemple.com/menu/",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "Numéro Rue",
    "addressLocality": "Paris",
    "postalCode": "75002",
    "addressCountry": "FR"
  },
  "geo": {
    "@type": "GeoCoordinates",
    "latitude": 48.8671,
    "longitude": 2.3504
  },
  "telephone": "+33XXXXXXXXX",
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
    "ratingValue": "4.9",
    "reviewCount": "187",
    "bestRating": "5"
  },
  "sameAs": [
    "https://www.facebook.com/[PAGE]",
    "https://www.instagram.com/[COMPTE]",
    "https://www.tripadvisor.fr/[PROFIL]"
  ]
}
```

**BreadcrumbList :**
```json
{
  "@type": "BreadcrumbList",
  "itemListElement": [
    {"@type":"ListItem","position":1,"name":"Accueil","item":"https://exemple.com/"},
    {"@type":"ListItem","position":2,"name":"Matcha Bar","item":"https://exemple.com/matcha-bar/"}
  ]
}
```

**WebSite avec SearchAction :**
```json
{
  "@type": "WebSite",
  "name": "Café d'Antan",
  "url": "https://cafedantan.com",
  "potentialAction": {
    "@type": "SearchAction",
    "target": {"@type":"EntryPoint","urlTemplate":"https://cafedantan.com/recherche/?q={search_term_string}"},
    "query-input": "required name=search_term_string"
  }
}
```

**Schema Restaurant — Propriétés spécifiques :**
```
Restaurant (ou sous-type spécifique)
  + Menu > MenuSection > MenuItem (name, price, nutrition, suitableForDiet)
  + ReserveAction (capacités de réservation)
  + OrderAction (à emporter/livraison)
  + servesCuisine, acceptsReservations
```
Note : Google Food Ordering (GFO) checkout direct supprimé en juin 2024. Le bouton "Commander en ligne" redirige maintenant vers des plateformes tierces.

---

## SKILL 5 : SEO IA & GEO (Générative Engine Optimization)

**Ce que ça couvre :** Optimisation pour Google AI Mode, ChatGPT, Perplexity.

---

### 5.1 Statistiques clés 2026
| Métrique | Valeur | Source |
|---------|--------|-------|
| Portée AI Overviews | 1,5 milliard users/mois, 200+ pays | Google |
| Couverture des requêtes AI Overviews | 50%+ de toutes les requêtes | Industry |
| Croissance sessions via IA | +527% (jan-mai 2025) | SparkToro |
| Utilisateurs hebdomadaires ChatGPT | 900 millions | OpenAI |
| Requêtes mensuelles Perplexity | 500+ millions | Perplexity |

**Google AI Mode** (lancé publiquement mai 2025) : disponible dans 180+ pays. **Zéro lien organique bleu** — seules les citations IA donnent de la visibilité dans cette interface.

---

### 5.2 Signaux de marque > Backlinks pour les IA
**Les mentions de marque corrèlent 3× plus fortement avec la visibilité IA que les backlinks.**
(Étude Ahrefs décembre 2025, 75 000 marques)

| Signal | Corrélation avec citations IA |
|-------|------------------------------|
| Mentions YouTube | ~0,737 (le plus fort) |
| Mentions Reddit | Élevé |
| Présence Wikipedia | Élevé |
| Présence LinkedIn | Modéré |
| Domain Rating (backlinks) | ~0,266 (faible) |

**Seulement 11% des domaines** sont cités à la fois par ChatGPT ET Google AI Overviews pour la même requête.

---

### 5.3 Critères GEO

**1. Score de citabilité (25%)**
- Longueur optimale : 134-167 mots
- Réponse directe dans les 40-60 premiers mots de chaque section
- Blocs autonomes extractibles sans contexte
- Données factuelles précises avec chiffres

**2. Lisibilité structurelle (20%)**
- 92% des citations AI Overviews viennent des 10 premiers résultats
- Mais 47% viennent de pages classées après la position 5
- Hiérarchie H1→H2→H3 propre
- Questions en titres H2/H3 (correspond aux patterns de requêtes)
- Paragraphes courts (2-4 phrases)
- Tableaux pour données comparatives
- Sections FAQ avec format Q/R clair

**3. Contenu multi-modal (15%)**
- Contenu avec éléments multi-modaux = taux de sélection +156%

**4. Signaux d'autorité & marque (20%)**
- Mentions sur YouTube, Reddit, Wikipedia
- Présence dans les médias spécialisés
- Citations cross-plateforme cohérentes
- Schéma Organization avec sameAs vers profils sociaux

---

### 5.4 Fichier llms.txt

Créer à la racine du site (`/llms.txt`) — standard émergent pour guider les IA :
```
# [Nom du Business]

> [Description en 1-2 phrases claires et factuelles]

## Informations principales
- Adresse : [adresse complète]
- Téléphone : [numéro]
- Horaires : [jours et horaires]

## Ce que nous proposons
[Liste structurée des services/produits]

## Pages clés
- [URL 1] : [description]
- [URL 2] : [description]

## Politique d'accès IA
Les moteurs de recherche et systèmes IA peuvent librement
indexer et citer ce contenu.
```

---

## SKILL 6 : SXO (Search Experience Optimization)

**Ce que ça couvre :** Pourquoi une page bien optimisée ne ranke pas — analyse de l'intention de recherche.

---

### 6.1 Concept central

Une page peut scorer 95/100 en SEO technique et ne jamais ranker parce qu'elle est **le mauvais type de page** pour le mot-clé.

**Si Google affiche 8 pages produit et 2 pages de comparaison pour ta requête, ton article de blog ne percera jamais — peu importe son optimisation.**

---

### 6.2 Taxonomie des types de pages
| Type | Signaux | Intent |
|------|---------|--------|
| Page produit/service | Prix, CTA d'achat, specs | Transactionnel |
| Page de comparaison | Tableau, pros/cons, "vs" | Commercial Investigation |
| Article informatif | Date, auteur, contenu long | Informationnel |
| Page de liste | "Les meilleurs X", numérotation | Commercial Investigation |
| Page de localisation | Adresse, carte, horaires | Local |
| Homepage/marque | Logo, nav principale | Navigationnel |
| Page outil/calculateur | Formulaire interactif | Informationnel/Transactionnel |

---

### 6.3 Mapping intention → type de page (restauration/café)
| Query | Intent | Type de page recommandé |
|-------|--------|------------------------|
| "café d'antan" | Navigationnel | Homepage |
| "coffee shop paris 2" | Local / Commercial | Homepage + GBP |
| "brunch paris 2" | Commercial Investigation | Page /brunch/ dédiée |
| "où boire matcha paris" | Local / Commercial | Page /matcha-bar-paris/ |
| "meilleur café de spécialité paris" | Commercial Investigation | Page pilier + blog |
| "réserver café d'antan" | Transactionnel | Page /reservation/ |
| "horaires café d'antan" | Informationnel | GBP + Homepage |
| "matcha c'est quoi" | Informationnel | Article de blog |

---

## SKILL 7 : BACKLINKS & AUTORITÉ

**Ce que ça couvre :** Profil de liens, distribution des ancres, liens toxiques.

---

### 7.1 Distribution d'ancres saine
| Type d'ancre | Fourchette cible | Signal de sur-optimisation |
|-------------|-----------------|--------------------------|
| Brandée (nom/domaine) | 30-50% | < 15% |
| URL nue | 15-25% | N/A |
| Générique ("cliquez ici") | 10-20% | N/A |
| Exact match mot-clé | 3-10% | > 15% |
| Partial match | 5-15% | > 25% |

---

### 7.2 Sources de liens pour un café local (gratuites)
1. TripAdvisor → lien vers le site
2. TheFork/LaFourchette → profil avec lien
3. Pages Jaunes → profil gratuit
4. Foursquare → profil gratuit
5. Yelp France → profil gratuit
6. Office de tourisme local → demande d'inclusion
7. Presse food locale → relations presse
8. Blogs food locaux → visite presse
9. Mairie / listes "restaurants" → inclusion gratuite

---

## SKILL 8 : PERFORMANCE & IMAGES SEO

**Ce que ça couvre :** Core Web Vitals, optimisation images, lazy loading.

---

### 8.1 Checklist performance
```
☐ Images en WebP/AVIF (taille fichier -30-40% vs JPEG)
☐ loading="lazy" sur toutes les images hors-écran
☐ width et height définis sur TOUTES les images (prévention CLS)
☐ Preload image hero : <link rel="preload" as="image" href="/hero.webp" fetchpriority="high">
☐ fetchpriority="high" sur l'image hero (pas de lazy loading sur le hero)
☐ font-display: swap sur toutes les polices web
☐ Cache CDN activé (Cloudflare niveau Standard ou Aggressive)
☐ Minification CSS et JS
☐ Suppression des scripts tiers inutiles
```

### 8.2 Format recommandé pour les balises image
```html
<!-- Image hero (above the fold) — NE PAS mettre lazy -->
<img
  src="/images/hero.webp"
  alt="Description SEO précise avec mot-clé naturel"
  width="1920"
  height="1080"
  fetchpriority="high"
>

<!-- Toutes les autres images -->
<img
  src="/images/photo.webp"
  alt="Description SEO précise"
  width="800"
  height="600"
  loading="lazy"
>
```

### 8.3 Nommage de fichiers SEO
```
❌ IMG_20241205.jpg
✅ coffee-shop-paris-2-interieur.webp
✅ matcha-latte-cafe-dantan-paris.webp
✅ torrefacteur-paris-cafe-en-grain.webp
```

---

## SKILL 9 : SITEMAP XML

**Règles de validation :**
- Maximum 50 000 URLs par fichier sitemap (protocole)
- Toutes les URLs retournent HTTP 200
- Pas de balises `<priority>` ni `<changefreq>` : **ignorées par Google**
- Pas d'URLs noindexées dans le sitemap
- Pas d'URLs redirigées dans le sitemap
- HTTPS uniquement (pas HTTP)
- Déclaré dans robots.txt : `Sitemap: https://exemple.com/sitemap.xml`

**Template sitemap.xml :**
```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>https://cafedantan.com/</loc>
    <lastmod>2026-05-16</lastmod>
  </url>
  <url>
    <loc>https://cafedantan.com/matcha-bar-paris/</loc>
    <lastmod>2026-05-16</lastmod>
  </url>
</urlset>
```

---

## GLOSSAIRE RAPIDE

| Terme | Définition |
|-------|-----------|
| **E-E-A-T** | Experience, Expertise, Authoritativeness, Trustworthiness — signaux de qualité Google |
| **Core Web Vitals** | LCP, INP, CLS — métriques de performance UX utilisées pour le ranking |
| **INP** | Interaction to Next Paint — remplace FID depuis mars 2024 |
| **GBP** | Google Business Profile — fiche établissement Google |
| **NAP** | Name, Address, Phone — données de cohérence locale |
| **Local Pack** | Les 3 résultats locaux avec carte en haut des résultats Google |
| **Schema / JSON-LD** | Données structurées qui aident Google à comprendre le contenu |
| **GEO** | Generative Engine Optimization — optimisation pour les réponses IA |
| **SXO** | Search Experience Optimization — alignement contenu/intention de recherche |
| **Canonical** | Balise indiquant à Google la version officielle d'une page dupliquée |
| **Hreflang** | Balise signalant la langue/région d'une page (sites multilingues) |
| **CLS** | Cumulative Layout Shift — mesure les décalages visuels inattendus |
| **LCP** | Largest Contentful Paint — temps de chargement de l'élément principal |
| **YMYL** | Your Money Your Life — thématiques à haute responsabilité (santé, finance, droit) |
| **SCA** | Specialty Coffee Association — score de qualité du café (>80 = spécialité) |
| **llms.txt** | Fichier standard émergent pour guider les IA sur le contenu d'un site |

---

*Source : claude-seo v1.9.9 par AgriciDaniel (github.com/AgriciDaniel/claude-seo)*
*Compilé le 2026-05-16 pour utilisation avec ChatGPT*
