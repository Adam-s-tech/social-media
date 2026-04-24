# Utilisation — Social Media AI

> **FR** | [EN below ↓](#usage--social-media-ai)

---

## Vue d'ensemble des pages

| Page | URL | Description |
|---|---|---|
| Dashboard | `/` | Statistiques globales et vidéos récentes |
| Créateurs | `/creators` | Gérer les comptes Instagram à analyser |
| Configs | `/configs` | Gérer les configurations (prompts) |
| Lancer | `/run` | Lancer le pipeline avec suivi en temps réel |
| Vidéos | `/videos` | Consulter les vidéos analysées et les concepts |

---

## Workflow complet pas à pas

### Étape 1 — Ajouter des créateurs concurrents

Les **créateurs** sont les comptes Instagram dont vous souhaitez analyser les Reels.

1. Allez sur [http://localhost:3000/creators](http://localhost:3000/creators)
2. Cliquez sur **Add Creator**
3. Remplissez le formulaire :
   - **Username** : le nom du compte Instagram sans `@` (ex: `nateherk`)
   - **Category** (optionnel) : une catégorie pour organiser vos créateurs (ex: `Real Estate`)
4. Cliquez sur **Save**
5. Répétez pour chaque concurrent à surveiller

> 💡 Commencez avec 2-3 créateurs pour tester le pipeline.

---

### Étape 2 — Créer une configuration

Une **configuration** définit :
- quels créateurs analyser (par catégorie)
- comment Gemini doit analyser les vidéos
- comment Claude doit générer les concepts adaptés

1. Allez sur [http://localhost:3000/configs](http://localhost:3000/configs)
2. Cliquez sur **New Config**
3. Remplissez les champs :
   - **Name** : un nom pour cette configuration (ex: `Analyse Immobilier`)
   - **Category** : la catégorie de créateurs à analyser (doit correspondre)
   - **Analysis Instruction** : le prompt pour Gemini (ex: `Analyse ce Reel en détaillant le hook des 3 premières secondes, la promesse faite au spectateur et le call-to-action`)
   - **New Concepts Instruction** : le prompt pour Claude (ex: `Tu es expert en contenu immobilier. Génère 3 concepts de Reels adaptés à une agence immobilière parisienne, inspirés des éléments viraux identifiés`)
4. Cliquez sur **Save**

> 💡 Plus vos prompts sont précis et contextualisés, meilleurs seront les concepts générés.

---

### Étape 3 — Lancer le pipeline

1. Allez sur [http://localhost:3000/run](http://localhost:3000/run)
2. Sélectionnez votre **configuration** dans la liste déroulante
3. Ajustez les paramètres :
   - **Max videos per creator** : nombre maximum de Reels à scraper par compte (ex: 10)
   - **Top K** : nombre de vidéos virales à analyser (ex: 3)
   - **Days lookback** : période de scraping en jours (ex: 30)
4. Cliquez sur **Run Pipeline**
5. Suivez la progression en temps réel dans le journal d'exécution

Le pipeline passe par ces étapes :
- ✅ Chargement de la configuration
- ✅ Scraping des Reels (Apify)
- ✅ Filtrage et classement par vues
- ✅ Analyse de chaque vidéo (Gemini)
- ✅ Génération des concepts (Claude)
- ✅ Sauvegarde dans `data/videos.csv`

> ⏱️ Comptez environ 1-2 minutes par vidéo analysée.

---

### Étape 4 — Consulter les résultats

1. Allez sur [http://localhost:3000/videos](http://localhost:3000/videos)
2. Parcourez les vidéos analysées avec leurs miniatures
3. Cliquez sur une vidéo pour voir :
   - L'**analyse** (concept, hook, rétention, récompense, script)
   - Les **concepts générés** pour votre marque

---

## Conseils d'utilisation

### Optimiser les prompts

**Prompt d'analyse (Gemini) — exemple efficace :**
```
Analyse ce Reel Instagram en détaillant :
1. Hook (3 premières secondes) : qu'est-ce qui accroche ?
2. Promesse : quelle transformation promet la vidéo ?
3. Preuve : comment la crédibilité est-elle établie ?
4. Call-to-action : comment la vidéo se termine-t-elle ?
5. Format : durée, rythme, style visuel
```

**Prompt de génération (Claude) — exemple efficace :**
```
Tu es expert en marketing immobilier à Paris.
En t'inspirant des éléments viraux identifiés dans l'analyse,
génère 3 concepts de Reels pour une agence immobilière haut de gamme.
Pour chaque concept : titre, hook, script (60 secondes), call-to-action.
Adapte le ton et le style au marché immobilier parisien.
```

### Gérer plusieurs projets

Créez une configuration distincte par projet ou par marque. Exemple :
- `Analyse Real Estate FR` — pour un client immobilier
- `Analyse Lifestyle B2C` — pour une marque lifestyle

---

---

# Usage — Social Media AI

> **EN** | [FR ci-dessus ↑](#utilisation--social-media-ai)

---

## Pages overview

| Page | URL | Description |
|---|---|---|
| Dashboard | `/` | Global stats and recent videos |
| Creators | `/creators` | Manage Instagram accounts to analyse |
| Configs | `/configs` | Manage configurations (prompts) |
| Run | `/run` | Launch pipeline with real-time tracking |
| Videos | `/videos` | View analysed videos and concepts |

---

## Complete step-by-step workflow

### Step 1 — Add competitor creators

**Creators** are the Instagram accounts whose Reels you want to analyse.

1. Go to [http://localhost:3000/creators](http://localhost:3000/creators)
2. Click on **Add Creator**
3. Fill in the form:
   - **Username**: the Instagram account name without `@` (e.g. `nateherk`)
   - **Category** (optional): a category to organise your creators (e.g. `Real Estate`)
4. Click **Save**
5. Repeat for each competitor you want to track

> 💡 Start with 2-3 creators to test the pipeline.

---

### Step 2 — Create a configuration

A **configuration** defines:
- which creators to analyse (by category)
- how Gemini should analyse the videos
- how Claude should generate adapted concepts

1. Go to [http://localhost:3000/configs](http://localhost:3000/configs)
2. Click on **New Config**
3. Fill in the fields:
   - **Name**: a name for this configuration (e.g. `Real Estate Analysis`)
   - **Category**: the creator category to analyse (must match)
   - **Analysis Instruction**: the prompt for Gemini (e.g. `Analyse this Reel detailing the hook in the first 3 seconds, the promise made to the viewer, and the call-to-action`)
   - **New Concepts Instruction**: the prompt for Claude (e.g. `You are an expert in real estate content. Generate 3 Reel concepts adapted to a Parisian real estate agency, inspired by the identified viral elements`)
4. Click **Save**

> 💡 The more precise and contextualised your prompts, the better the generated concepts.

---

### Step 3 — Run the pipeline

1. Go to [http://localhost:3000/run](http://localhost:3000/run)
2. Select your **configuration** from the dropdown
3. Adjust the parameters:
   - **Max videos per creator**: maximum number of Reels to scrape per account (e.g. 10)
   - **Top K**: number of viral videos to analyse (e.g. 3)
   - **Days lookback**: scraping period in days (e.g. 30)
4. Click on **Run Pipeline**
5. Follow progress in real time in the execution log

The pipeline goes through these steps:
- ✅ Loading configuration
- ✅ Scraping Reels (Apify)
- ✅ Filtering and ranking by views
- ✅ Analysing each video (Gemini)
- ✅ Generating concepts (Claude)
- ✅ Saving to `data/videos.csv`

> ⏱️ Allow approximately 1-2 minutes per analysed video.

---

### Step 4 — Review results

1. Go to [http://localhost:3000/videos](http://localhost:3000/videos)
2. Browse analysed videos with their thumbnails
3. Click on a video to see:
   - The **analysis** (concept, hook, retention, reward, script)
   - The **generated concepts** for your brand

---

## Usage tips

### Optimising prompts

**Analysis prompt (Gemini) — effective example:**
```
Analyse this Instagram Reel detailing:
1. Hook (first 3 seconds): what grabs attention?
2. Promise: what transformation does the video promise?
3. Proof: how is credibility established?
4. Call-to-action: how does the video end?
5. Format: duration, pace, visual style
```

**Generation prompt (Claude) — effective example:**
```
You are an expert in Parisian real estate marketing.
Drawing inspiration from the viral elements identified in the analysis,
generate 3 Reel concepts for a high-end real estate agency.
For each concept: title, hook, script (60 seconds), call-to-action.
Adapt the tone and style to the Parisian real estate market.
```

### Managing multiple projects

Create a distinct configuration per project or brand. Example:
- `Real Estate FR Analysis` — for a real estate client
- `Lifestyle B2C Analysis` — for a lifestyle brand
