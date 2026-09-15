# ÉCRIN — landing page de test d'intérêt

Page unique (Astro, statique) destinée à mesurer l'intérêt pour ÉCRIN : une gamme de
compléments alimentaires pour les femmes actives dont le quotidien mobilise fortement les
ressources physiques et mentales.

Contenu dérivé du *Value Proposition Canvas* (document interne, non versionné) : territoire
« préserver et restaurer ses ressources », bénéfices Récupération / Énergie stable /
Concentration / Lucidité, différenciation par la formule unique et l'observance.

**Direction artistique :** variante **1A « Éditorial clair »** de la maquette Claude Design
(`docs/SPIRIT Landing.dc.html`, non versionné). Fond `#f6f4ef`, encre `#1c1a17`, accent
terracotta `#8a5a3b`, Instrument Serif en display, IBM Plex Mono pour les labels, angles
vifs. Aucun texte en italique (choix explicite).

**Images :** Pexels (licence libre, usage commercial sans attribution obligatoire), stockées
dans `src/assets/` et optimisées en WebP au build par `astro:assets`. Aucun hotlink.

**En ligne :** https://dimgladieux.github.io/spirit-landing

## Développer

```bash
npm install
npm run dev      # http://localhost:4321/é-landing
npm run build
```

## Brancher le formulaire (obligatoire avant de diffuser)

Sans endpoint, le formulaire affiche un message d'erreur et **aucun email n'est collecté**.

1. Créer un formulaire sur [Formspree](https://formspree.io) (gratuit jusqu'à 50 soumissions /
   mois) et récupérer l'URL `https://formspree.io/f/xxxxxxx`.
2. GitHub → *Settings* → *Secrets and variables* → *Actions* → onglet **Variables** →
   *New repository variable* :
   - nom : `PUBLIC_FORM_ENDPOINT`
   - valeur : l'URL Formspree
3. Relancer le workflow *Deploy to GitHub Pages*.

En local, créer un fichier `.env` :

```
PUBLIC_FORM_ENDPOINT=https://formspree.io/f/xxxxxxx
```

## Déploiement

Push sur `main` → GitHub Actions build et publie sur GitHub Pages.
Prérequis une seule fois : *Settings* → *Pages* → *Source* = **GitHub Actions**.

## Lire le résultat du test

Le signal principal est le **taux de conversion visite → email**. Repères usuels pour une
landing page de pré-lancement avec trafic qualifié :

| Conversion | Lecture |
|---|---|
| < 3 % | la proposition ne fait pas mouche, ou le trafic n'est pas la bonne cible |
| 5–10 % | intérêt réel, on creuse |
| > 15 % | signal fort |

La question « ce qui vous manque le plus » remontée avec chaque email indique quel bénéfice
tire la demande — utile pour prioriser la formulation.

Sans outil d'analytics installé, le nombre de visites doit venir de la source de trafic
(LinkedIn, Meta Ads, newsletter…). Ajouter [Plausible](https://plausible.io) ou PostHog si un
suivi plus fin est nécessaire.

## Structure

```
src/pages/index.astro          toute la page (contenu + styles)
src/components/Waitlist.astro  formulaire email, réutilisé 2×
.github/workflows/deploy.yml   build + déploiement Pages
docs/                          Value Proposition Canvas (local, gitignoré)
```

## Mentions

Aucun produit n'est commercialisé à ce stade — la page l'indique explicitement. Les
formulations sont volontairement dépourvues d'allégations de santé non autorisées : pas de
promesse thérapeutique, pas de délai d'effet, pas d'avis client fabriqué. À faire relire
avant toute diffusion payante.
