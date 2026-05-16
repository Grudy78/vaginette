# Plan d'Action SEO — cafedantan.com
> Café d'Antan | 36 rue de la Lune, 75002 Paris  
> Coffee Shop · Matcha Bar · Torréfacteur · B2B

---

## 🔴 CRITIQUE — À faire cette semaine

| # | Action | Impact | Effort | Skill |
|---|--------|--------|--------|-------|
| 1 | Ajouter `<meta name="robots" content="noindex, nofollow">` sur `/cuisine` | Évite pénalité indexation | 15 min | seo-technical |
| 2 | Résoudre cannibalisation `/site` vs `/coffee-shop-pro` → rediriger `/site` vers `/coffee-shop-pro` | Rankings B2B unifiés | 30 min | seo-technical |
| 3 | Déployer schema JSON-LD `CafeOrCoffeeShop` complet sur toutes pages | Rich results + GBP sync | 2h | seo-schema |
| 4 | Modifier H1 homepage → "Café d'Antan — Coffee Shop, Matcha Bar & Torréfacteur à Paris 2" | Rankings + CTR | 15 min | seo-page |
| 5 | Mettre à jour title tag homepage → "Coffee Shop Paris 2 | Café d'Antan — Matcha & Café de Spécialité" | CTR +20% estimé | 15 min | seo-page |
| 6 | Créer `/llms.txt` avec infos business complètes | Visibilité IA | 30 min | seo-geo |

---

## 🟠 HAUTE PRIORITÉ — Dans les 2 semaines

| # | Action | Impact | Effort | Skill |
|---|--------|--------|--------|-------|
| 7 | Créer page `/matcha-bar-paris` avec contenu unique 1000+ mots | Nouveau mot-clé à fort volume | 3h | seo-content |
| 8 | Créer page `/cafe-de-specialite-paris` | Mot-clé principal | 3h | seo-content |
| 9 | Créer page `/torrefacteur-paris` | B2C + B2B | 3h | seo-content |
| 10 | Créer page `/coffee-shop-bonne-nouvelle` | SEO local géo | 2h | seo-local |
| 11 | Créer page `/coffee-shop-grands-boulevards` | SEO local géo | 2h | seo-local |
| 12 | Ajouter FAQ structurée sur homepage (8 questions) | Featured snippets + E-E-A-T | 2h | seo-content |
| 13 | Optimiser Google Business Profile : photos, posts, attributs | Local Pack ranking | 2h | seo-local |
| 14 | Ajouter NAP complet dans footer (HTML, pas image) | NAP consistency | 1h | seo-local |
| 15 | Intégrer Google Maps embed (lazy-loaded) | Signal géo local | 30 min | seo-local |

---

## 🟡 MOYEN TERME — Dans le mois

| # | Action | Impact | Effort | Skill |
|---|--------|--------|--------|-------|
| 16 | Créer `/coffee-shop-paris-2` comme page pilier | Volume fort | 4h | seo-content |
| 17 | Créer `/cafe-en-grain-paris` | E-commerce + B2B | 3h | seo-content |
| 18 | Créer `/cafe-professionnel-paris` | B2B pipeline | 3h | seo-content |
| 19 | Créer `/cafe-pour-restaurants` | B2B niche | 3h | seo-content |
| 20 | Créer `/matcha-latte-paris` | Volume moyen, faible concurrence | 2h | seo-content |
| 21 | Créer `/coffee-shop-sentier` | SEO local géo | 2h | seo-local |
| 22 | Créer `/coffee-shop-montorgueil` | SEO local géo | 2h | seo-local |
| 23 | Passer toutes les images en WebP + lazy loading | LCP -40%, CLS → 0 | 3h | seo-images |
| 24 | Implémenter preload image hero | LCP -0,5s | 30 min | seo-technical |
| 25 | Activer IndexNow pour Bing | Indexation rapide | 1h | seo-technical |

---

## 🟢 BACKLOG — Quand possible

| # | Action | Impact | Effort |
|---|--------|--------|--------|
| 26 | Créer blog avec premier article "Les meilleurs coffee shops Paris 2" | Backlinks + longue traîne | 1 jour |
| 27 | Inscription TripAdvisor, TheFork, Foursquare | Citations locales | 2h |
| 28 | Implémenter schema `Menu` + `MenuItem` sur page carte | Rich results | 2h |
| 29 | Ajouter Open Graph + Twitter Card sur toutes les pages | Social sharing | 1h |
| 30 | Mettre en place suivi avis (objectif 1-2/semaine) | Local Pack ranking | Continu |
| 31 | Créer page `/a-propos` avec histoire du torréfacteur | E-E-A-T brand | 3h |

---

## Architecture de site finale recommandée

```
cafedantan.com/
├── [Homepage] Coffee Shop, Matcha Bar & Torréfacteur Paris 2
├── /menu/                    → Carte complète
├── /coffee-shop-paris-2/     → Page pilier SEO local (PRIORITÉ 1)
├── /matcha-bar-paris/        → Vertical matcha (PRIORITÉ 1)
├── /torrefacteur-paris/      → Vertical torréfaction
├── /cafe-de-specialite-paris/ → Vertical spécialité
├── /cafe-en-grain-paris/     → E-commerce / B2C
├── /coffee-shop-bonne-nouvelle/ → SEO géo
├── /coffee-shop-grands-boulevards/ → SEO géo
├── /coffee-shop-sentier/     → SEO géo
├── /coffee-shop-montorgueil/ → SEO géo
├── /cafe-professionnel-paris/ → B2B Hub
├── /cafe-pour-restaurants/   → B2B restaurants
├── /matcha-latte-paris/      → Longue traîne
├── /coffee-shop-pro/         → Page B2B principale (garder, consolider)
├── /reservation/             → CTA conversion
├── /a-propos/                → E-E-A-T
├── /blog/                    → Contenu longue traîne
├── /contact/                 → NAP + Maps
└── [/cuisine → NOINDEX]     → Page interne à masquer
```

---

## Mots-clés & Pages — Mapping

| Mot-clé | Volume FR/mois | Concurrence | Page cible |
|---------|---------------|-------------|------------|
| coffee shop paris 2 | 1 000-2 000 | Moyenne | /coffee-shop-paris-2 |
| matcha bar paris | 2 000-5 000 | Faible | /matcha-bar-paris |
| matcha latte paris | 1 000-2 000 | Faible | /matcha-latte-paris |
| café de spécialité paris | 2 000-5 000 | Moyenne | /cafe-de-specialite-paris |
| coffee shop bonne nouvelle | 500-1 000 | Faible | /coffee-shop-bonne-nouvelle |
| coffee shop grands boulevards | 500-1 000 | Faible | /coffee-shop-grands-boulevards |
| torréfacteur paris | 1 000-2 000 | Faible | /torrefacteur-paris |
| café en grain paris | 500-1 000 | Faible | /cafe-en-grain-paris |
| café pour restaurant paris | 200-500 | Très faible | /cafe-pour-restaurants |

---

## KPIs à suivre (Google Search Console + GA4)

- Impressions sur les mots-clés cibles
- CTR moyen (objectif > 5%)
- Position moyenne (objectif < 5 sur mots-clés ciblés)
- Clics organiques totaux
- Trafic local (géolocalisation Paris)
- Conversions : réservations + demandes B2B

*Plan d'action généré par claude-seo v1.9.9*
