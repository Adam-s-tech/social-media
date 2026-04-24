# 🎬 Social Media AI — Générateur de Reels Instagram Viraux

> **FR** | [EN below ↓](#-social-media-ai--viral-instagram-reels-generator)

Analysez vos concurrents, identifiez leurs vidéos virales et générez automatiquement des concepts adaptés à votre marque — en quelques minutes, sans compétences techniques avancées.

Forké depuis [melnikoff-oleg/social-media](https://github.com/melnikoff-oleg/social-media).

---

## Vue d'ensemble

**Social Media AI** est un pipeline IA complet pour créer des Instagram Reels viraux :

1. 🔍 **Scraping** — récupère les Reels récents de vos concurrents via Apify
2. 📊 **Filtrage & Ranking** — identifie automatiquement les vidéos les plus virales
3. 🧠 **Analyse IA** — Google Gemini 2.0 Flash décompose chaque vidéo (concept, hook, rétention, récompense, script)
4. ✍️ **Génération de concepts** — Anthropic Claude Sonnet adapte les formules virales à votre marque
5. 💾 **Stockage & Consultation** — résultats sauvegardés en CSV, consultables dans l'interface

**Stack** : Next.js 16 · TypeScript · Tailwind CSS · Apify · Google Gemini · Anthropic Claude

---

## Fonctionnalités

| Fonctionnalité | Description |
|---|---|
| 📥 Scraping concurrent | Récupère les Reels de n'importe quel compte Instagram public |
| 🏆 Classement viral | Trie par vues, filtre par date, sélectionne les top-K |
| 🎥 Analyse vidéo IA | Gemini analyse hook, rétention, concept et script |
| 💡 Concepts adaptés | Claude génère des idées vidéo pour votre marque |
| ⚙️ Configs personnalisables | Prompts et créateurs configurables par projet |
| 📋 Interface web | Dashboard, historique vidéos, lancement en temps réel |

---

## Comment ça marche (pipeline)

```
Créateurs concurrents
        │
        ▼
  [Apify Scraper]  ──► Reels récents
        │
        ▼
  [Filtre & Rank]  ──► Top-K vidéos virales
        │
        ▼
 [Gemini Analysis] ──► Concept · Hook · Rétention · Script
        │
        ▼
[Claude Generation] ──► Nouveaux concepts adaptés à votre marque
        │
        ▼
   [CSV + UI]      ──► Consultable dans /videos
```

---

## Démarrage rapide (5 minutes)

### Prérequis

- **Node.js 18+** (LTS recommandé) — [nodejs.org](https://nodejs.org)
- **npm** (inclus avec Node.js)
- 3 clés API : Apify, Google Gemini, Anthropic (voir [docs/API_KEYS.md](docs/API_KEYS.md))

> 📖 Guide d'installation détaillé → [docs/INSTALLATION.md](docs/INSTALLATION.md)

### 1. Cloner le dépôt

```bash
git clone https://github.com/Adam-s-tech/social-media.git
cd social-media
```

### 2. Configurer les variables d'environnement

```bash
cp .env.example .env
```

Ouvrez `.env` et remplissez vos 3 clés API :

```env
APIFY_API_TOKEN=apify_api_xxxxxxxxxxxxxxxxxxxxxxxx
GEMINI_API_KEY=AIzaSyxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
ANTHROPIC_API_KEY=sk-ant-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

> 🔑 Comment obtenir ces clés → [docs/API_KEYS.md](docs/API_KEYS.md)

### 3. Installer les dépendances

```bash
cd app
npm install
```

### 4. Lancer l'application

```bash
npm run dev
```

Ouvrez [http://localhost:3000](http://localhost:3000) dans votre navigateur.

---

## Utilisation

### Étape 1 — Ajouter des créateurs concurrents

Allez sur `/creators` → ajoutez les comptes Instagram à analyser (ex: `@nateherk`, `@leomessi`).

### Étape 2 — Créer une configuration

Allez sur `/configs` → créez une config avec :
- un prompt d'analyse (comment Gemini doit analyser)
- un prompt de génération (comment Claude doit adapter pour votre marque)

### Étape 3 — Lancer le pipeline

Allez sur `/run` → sélectionnez votre config, définissez les paramètres et lancez.

### Étape 4 — Consulter les résultats

Allez sur `/videos` → parcourez les vidéos analysées avec leurs concepts générés.

> 📖 Guide d'utilisation complet → [docs/USAGE.md](docs/USAGE.md)

---

## 💰 Coût & Test minimal

> ⚠️ **Ce projet n'est pas gratuit.** Chaque lancement du pipeline consomme des crédits sur 3 services payants.

| Service | Niveau gratuit | Au-delà |
|---|---|---|
| **Apify** | ~5 $ de crédits offerts | Selon votre plan |
| **Google Gemini** | Quota quotidien limité | Tier payant requis pour gros volumes |
| **Anthropic Claude** | Aucun niveau gratuit | Selon consommation de tokens |

### Pour tester sans exploser votre budget

Commencez avec la configuration la plus légère possible :

- **Créateurs** : 1 seul compte
- **Max videos per creator** : 3 (le minimum)
- **Top K** : 1 (analyser seulement la vidéo la plus virale)
- **Days lookback** : 7

Un tel test coûte quelques centimes. Une fois que tout fonctionne, augmentez progressivement les paramètres.

> ❌ Erreur `RESOURCE_EXHAUSTED` (Gemini) ou "credit balance too low" (Anthropic) ?
> → Consultez [docs/TROUBLESHOOTING.md](docs/TROUBLESHOOTING.md)

---

## Structure du projet

```
.
├── .env.example          # Variables d'environnement (template)
├── README.md             # Ce fichier
├── app/                  # Application Next.js
│   └── src/
│       ├── app/          # Pages et routes API
│       │   ├── page.tsx              # Dashboard
│       │   ├── videos/page.tsx       # Vidéos analysées
│       │   ├── run/page.tsx          # Lancement pipeline
│       │   ├── configs/page.tsx      # Gestion des configs
│       │   ├── creators/page.tsx     # Gestion des créateurs
│       │   └── api/                  # Routes API
│       ├── lib/          # Logique métier
│       │   ├── pipeline.ts           # Orchestration du pipeline
│       │   ├── apify.ts              # Client Apify (scraping)
│       │   ├── gemini.ts             # Client Gemini (analyse vidéo)
│       │   ├── claude.ts             # Client Claude (génération)
│       │   └── csv.ts                # Lecture/écriture CSV
│       └── components/   # Composants UI (shadcn/ui)
├── data/                 # Données CSV
│   ├── configs.csv       # Configurations sauvegardées
│   ├── creators.csv      # Comptes Instagram à analyser
│   └── videos.csv        # Résultats d'analyse
└── docs/                 # Documentation détaillée
    ├── INSTALLATION.md
    ├── API_KEYS.md
    ├── USAGE.md
    └── TROUBLESHOOTING.md
```

---

## Dépannage

Problème fréquent ? Consultez [docs/TROUBLESHOOTING.md](docs/TROUBLESHOOTING.md).

Problèmes courants :
- ❌ Variables d'environnement manquantes → vérifiez que `.env` est à la **racine** du projet
- ❌ Erreur `ENOENT data/*.csv` → les fichiers CSV sont créés automatiquement au premier lancement
- ❌ Quota Apify épuisé → vérifiez votre plan sur [console.apify.com](https://console.apify.com)

---

## ❓ FAQ / Problèmes fréquents

### « `cr`, `cs` ou `claude` : command not found »

Ce repo **n'utilise pas** les alias `cr`/`cs` ni la CLI `claude` pour démarrer. Ces commandes appartiennent à d'autres configurations ou tutoriels. Si vous les voyez dans une vidéo, elles ne concernent pas ce projet.

La **seule commande nécessaire** pour lancer l'application est :

```bash
cd app && npm install && npm run dev
```

Si vous obtenez `zsh: command not found: claude` ou similaire, ignorez-le — cette CLI n'est pas requise ici.

### « Je ne trouve pas le fichier `.env` »

Le fichier `.env` **n'est pas inclus dans le dépôt GitHub** (il est volontairement ignoré par Git pour ne pas exposer vos clés API). C'est normal de ne pas le voir.

Créez-le vous-même en une commande :

```bash
# Depuis la racine du projet (là où se trouve README.md)
cp .env.example .env
```

Ouvrez ensuite `.env` et remplacez les valeurs fictives par vos vraies clés API.

> 📖 Guide complet → [docs/TROUBLESHOOTING.md](docs/TROUBLESHOOTING.md)

---

## Sécurité & Confidentialité

- ⚠️ **Ne commitez jamais votre fichier `.env`** (il est dans `.gitignore`)
- Les vidéos analysées sont téléchargées temporairement et supprimées après traitement
- Les données sont stockées **localement** dans `data/*.csv` — rien n'est envoyé à un serveur tiers sauf les API configurées

---

## Licence & Avertissement

Ce projet est distribué **à des fins éducatives**. Respectez les conditions d'utilisation d'Instagram, d'Apify, de Google et d'Anthropic. L'auteur décline toute responsabilité pour un usage non conforme aux CGU de ces services.

---

---

# 🎬 Social Media AI — Viral Instagram Reels Generator

> **EN** | [FR ci-dessus ↑](#-social-media-ai--générateur-de-reels-instagram-viraux)

Analyze your competitors, identify their viral videos, and automatically generate concepts adapted to your brand — in minutes, no advanced technical skills required.

Forked from [melnikoff-oleg/social-media](https://github.com/melnikoff-oleg/social-media).

---

## Overview

**Social Media AI** is a complete AI pipeline for creating viral Instagram Reels:

1. 🔍 **Scraping** — fetches recent Reels from competitor accounts via Apify
2. 📊 **Filtering & Ranking** — automatically identifies the most viral videos
3. 🧠 **AI Analysis** — Google Gemini 2.0 Flash breaks down each video (concept, hook, retention, reward, script)
4. ✍️ **Concept Generation** — Anthropic Claude Sonnet adapts viral formulas to your brand
5. 💾 **Storage & Review** — results saved to CSV, viewable in the UI

**Stack**: Next.js 16 · TypeScript · Tailwind CSS · Apify · Google Gemini · Anthropic Claude

---

## Features

| Feature | Description |
|---|---|
| 📥 Competitor scraping | Fetches Reels from any public Instagram account |
| 🏆 Viral ranking | Sorts by views, filters by date, selects top-K |
| 🎥 AI video analysis | Gemini analyses hook, retention, concept and script |
| 💡 Adapted concepts | Claude generates video ideas for your brand |
| ⚙️ Customisable configs | Prompts and creators configurable per project |
| 📋 Web interface | Dashboard, video history, real-time pipeline launch |

---

## How It Works (Pipeline)

```
Competitor creators
        │
        ▼
  [Apify Scraper]  ──► Recent Reels
        │
        ▼
  [Filter & Rank]  ──► Top-K viral videos
        │
        ▼
 [Gemini Analysis] ──► Concept · Hook · Retention · Script
        │
        ▼
[Claude Generation] ──► New concepts adapted to your brand
        │
        ▼
   [CSV + UI]      ──► Viewable in /videos
```

---

## Quickstart (5 minutes)

### Prerequisites

- **Node.js 18+** (LTS recommended) — [nodejs.org](https://nodejs.org)
- **npm** (bundled with Node.js)
- 3 API keys: Apify, Google Gemini, Anthropic (see [docs/API_KEYS.md](docs/API_KEYS.md))

> 📖 Detailed installation guide → [docs/INSTALLATION.md](docs/INSTALLATION.md)

### 1. Clone the repository

```bash
git clone https://github.com/Adam-s-tech/social-media.git
cd social-media
```

### 2. Configure environment variables

```bash
cp .env.example .env
```

Open `.env` and fill in your 3 API keys:

```env
APIFY_API_TOKEN=apify_api_xxxxxxxxxxxxxxxxxxxxxxxx
GEMINI_API_KEY=AIzaSyxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
ANTHROPIC_API_KEY=sk-ant-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

> 🔑 How to get these keys → [docs/API_KEYS.md](docs/API_KEYS.md)

### 3. Install dependencies

```bash
cd app
npm install
```

### 4. Start the application

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

---

## Usage

### Step 1 — Add competitor creators

Go to `/creators` → add Instagram accounts to analyse (e.g. `@nateherk`, `@leomessi`).

### Step 2 — Create a configuration

Go to `/configs` → create a config with:
- an analysis prompt (how Gemini should analyse)
- a generation prompt (how Claude should adapt for your brand)

### Step 3 — Run the pipeline

Go to `/run` → select your config, set parameters and launch.

### Step 4 — Review results

Go to `/videos` → browse analysed videos with generated concepts.

> 📖 Full usage guide → [docs/USAGE.md](docs/USAGE.md)

---

## 💰 Cost & Minimal Test

> ⚠️ **This project is not free.** Every pipeline run consumes credits across 3 paid services.

| Service | Free tier | Beyond |
|---|---|---|
| **Apify** | ~$5 of free credits | According to your plan |
| **Google Gemini** | Limited daily quota | Paid tier required for large volumes |
| **Anthropic Claude** | No free tier | According to token usage |

### To test without blowing your budget

Start with the lightest possible configuration:

- **Creators**: 1 account only
- **Max videos per creator**: 3 (the minimum)
- **Top K**: 1 (analyse only the most viral video)
- **Days lookback**: 7

Such a test costs a few cents. Once everything works, gradually increase the parameters.

> ❌ `RESOURCE_EXHAUSTED` error (Gemini) or "credit balance too low" (Anthropic)?
> → See [docs/TROUBLESHOOTING.md](docs/TROUBLESHOOTING.md)

---

## Project Structure

```
.
├── .env.example          # Environment variables template
├── README.md             # This file
├── app/                  # Next.js application
│   └── src/
│       ├── app/          # Pages and API routes
│       │   ├── page.tsx              # Dashboard
│       │   ├── videos/page.tsx       # Analysed videos
│       │   ├── run/page.tsx          # Pipeline runner
│       │   ├── configs/page.tsx      # Config management
│       │   ├── creators/page.tsx     # Creator management
│       │   └── api/                  # API routes
│       ├── lib/          # Business logic
│       │   ├── pipeline.ts           # Pipeline orchestration
│       │   ├── apify.ts              # Apify client (scraping)
│       │   ├── gemini.ts             # Gemini client (video analysis)
│       │   ├── claude.ts             # Claude client (generation)
│       │   └── csv.ts                # CSV read/write
│       └── components/   # UI components (shadcn/ui)
├── data/                 # CSV data storage
│   ├── configs.csv       # Saved configurations
│   ├── creators.csv      # Instagram accounts to analyse
│   └── videos.csv        # Analysis results
└── docs/                 # Detailed documentation
    ├── INSTALLATION.md
    ├── API_KEYS.md
    ├── USAGE.md
    └── TROUBLESHOOTING.md
```

---

## Troubleshooting

Check [docs/TROUBLESHOOTING.md](docs/TROUBLESHOOTING.md) for common issues.

Common problems:
- ❌ Missing environment variables → make sure `.env` is at the **project root**
- ❌ `ENOENT data/*.csv` error → CSV files are created automatically on first run
- ❌ Apify quota exceeded → check your plan at [console.apify.com](https://console.apify.com)

---

## ❓ FAQ / Quick fixes

### "`cr`, `cs` or `claude`: command not found"

This repo does **not** use the `cr`/`cs` aliases or the `claude` CLI to start. These commands belong to other configurations or tutorials. If you see them in a video, they do not apply to this project.

The **only command needed** to start the app is:

```bash
cd app && npm install && npm run dev
```

If you get `zsh: command not found: claude` or similar, ignore it — this CLI is not required here.

### "I can't find the `.env` file"

The `.env` file is **not included in the GitHub repository** (it is intentionally ignored by Git so your API keys are never exposed). It is normal not to see it.

Create it yourself with one command:

```bash
# From the project root (where README.md lives)
cp .env.example .env
```

Then open `.env` and replace the placeholder values with your real API keys.

> 📖 Full guide → [docs/TROUBLESHOOTING.md](docs/TROUBLESHOOTING.md)

---

## Security & Privacy

- ⚠️ **Never commit your `.env` file** (it is in `.gitignore`)
- Analysed videos are downloaded temporarily and deleted after processing
- Data is stored **locally** in `data/*.csv` — nothing is sent to third-party servers except the configured APIs

---

## SEO Keywords

Instagram Reels automation · competitor analysis · hook and retention analysis · Gemini video analysis · Apify Instagram scraper · Claude concept generation · short-form content pipeline · viral reels generator · AI social media tool · Instagram content strategy

---

## Licence & Disclaimer

This project is distributed **for educational purposes**. Please respect the terms of service of Instagram, Apify, Google, and Anthropic. The author accepts no liability for use that does not comply with these services' terms of service.
