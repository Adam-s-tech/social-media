# Clés API — Social Media AI

> **FR** | [EN below ↓](#api-keys--social-media-ai)

Ce projet nécessite 3 clés API. Voici comment les obtenir étape par étape.

---

## 1. Apify — Clé pour le scraping Instagram

Apify est utilisé pour récupérer les Reels des comptes Instagram concurrents.

### Étapes

1. Créez un compte gratuit sur [apify.com](https://apify.com)
2. Connectez-vous à votre compte
3. Cliquez sur votre avatar (en haut à droite) → **Settings**
4. Dans le menu de gauche, cliquez sur **API & Integrations**
5. Copiez votre **Personal API token**

**Format attendu :** `apify_api_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`

### Quota gratuit

Le plan gratuit Apify inclut 5 USD de crédit mensuel, suffisant pour des tests. Vérifiez votre consommation sur [console.apify.com](https://console.apify.com).

---

## 2. Google Gemini — Clé pour l'analyse vidéo

Gemini est utilisé pour analyser le contenu de chaque vidéo (hook, rétention, concept, script).

### Étapes

1. Allez sur [aistudio.google.com](https://aistudio.google.com)
2. Connectez-vous avec votre compte Google
3. Cliquez sur **Get API key** (en haut à gauche)
4. Cliquez sur **Create API key**
5. Copiez la clé générée

**Format attendu :** `AIzaSyxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`

### Notes

- La clé est liée à un projet Google Cloud (créé automatiquement)
- Gemini 2.0 Flash est utilisé (modèle multimodal rapide et peu coûteux)
- Le quota gratuit est généreux pour des tests

---

## 3. Anthropic — Clé pour la génération de concepts

Anthropic Claude Sonnet est utilisé pour générer des concepts vidéo adaptés à votre marque.

### Étapes

1. Créez un compte sur [console.anthropic.com](https://console.anthropic.com)
2. Connectez-vous à votre compte
3. Cliquez sur **API Keys** dans le menu de gauche
4. Cliquez sur **Create Key**
5. Donnez un nom à votre clé (ex: `social-media-ai`)
6. Copiez la clé affichée (**elle n'est visible qu'une seule fois**)

**Format attendu :** `sk-ant-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`

> ⚠️ Conservez cette clé en sécurité. Elle ne sera plus affichée après fermeture de la fenêtre.

---

## Configuration dans le projet

Une fois vos 3 clés obtenues, créez un fichier `.env` à la **racine** du projet :

```bash
cp .env.example .env
```

Puis remplissez-le :

```env
APIFY_API_TOKEN=apify_api_xxxxxxxxxxxxxxxxxxxxxxxx
GEMINI_API_KEY=AIzaSyxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
ANTHROPIC_API_KEY=sk-ant-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

---

## Précautions de sécurité

| ✅ À faire | ❌ À ne pas faire |
|---|---|
| Stocker les clés dans `.env` | Committer `.env` dans Git |
| Régénérer les clés si compromises | Partager les clés par email/chat |
| Vérifier `.gitignore` contient `.env` | Coller les clés directement dans le code |

Le fichier `.env` est **automatiquement ignoré** par Git grâce au `.gitignore`. Ne le retirez jamais de cette liste.

---

---

# API Keys — Social Media AI

> **EN** | [FR ci-dessus ↑](#clés-api--social-media-ai)

This project requires 3 API keys. Here's how to obtain them step by step.

---

## 1. Apify — Key for Instagram scraping

Apify is used to fetch Reels from competitor Instagram accounts.

### Steps

1. Create a free account at [apify.com](https://apify.com)
2. Log in to your account
3. Click on your avatar (top right) → **Settings**
4. In the left menu, click on **API & Integrations**
5. Copy your **Personal API token**

**Expected format:** `apify_api_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`

### Free quota

The free Apify plan includes $5 monthly credit, enough for testing. Check your usage at [console.apify.com](https://console.apify.com).

---

## 2. Google Gemini — Key for video analysis

Gemini is used to analyse the content of each video (hook, retention, concept, script).

### Steps

1. Go to [aistudio.google.com](https://aistudio.google.com)
2. Sign in with your Google account
3. Click on **Get API key** (top left)
4. Click on **Create API key**
5. Copy the generated key

**Expected format:** `AIzaSyxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`

### Notes

- The key is linked to a Google Cloud project (created automatically)
- Gemini 2.0 Flash is used (fast, multimodal, cost-effective model)
- The free quota is generous for testing

---

## 3. Anthropic — Key for concept generation

Anthropic Claude Sonnet is used to generate video concepts adapted to your brand.

### Steps

1. Create an account at [console.anthropic.com](https://console.anthropic.com)
2. Log in to your account
3. Click on **API Keys** in the left menu
4. Click on **Create Key**
5. Give your key a name (e.g. `social-media-ai`)
6. Copy the displayed key (**it is only visible once**)

**Expected format:** `sk-ant-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`

> ⚠️ Keep this key secure. It will not be displayed again after closing the window.

---

## Configuration in the project

Once you have your 3 keys, create a `.env` file at the **project root**:

```bash
cp .env.example .env
```

Then fill it in:

```env
APIFY_API_TOKEN=apify_api_xxxxxxxxxxxxxxxxxxxxxxxx
GEMINI_API_KEY=AIzaSyxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
ANTHROPIC_API_KEY=sk-ant-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

---

## Security precautions

| ✅ Do | ❌ Don't |
|---|---|
| Store keys in `.env` | Commit `.env` to Git |
| Regenerate keys if compromised | Share keys via email/chat |
| Verify `.gitignore` contains `.env` | Paste keys directly in the code |

The `.env` file is **automatically ignored** by Git via `.gitignore`. Never remove it from that list.
