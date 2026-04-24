# Dépannage — Social Media AI

> **FR** | [EN below ↓](#troubleshooting--social-media-ai)

---

## Erreurs courantes et solutions

### ❌ "Cannot find module" ou "Module not found"

**Cause :** Les dépendances Node.js ne sont pas installées.

**Solution :**
```bash
cd app
npm install
```

---

### ❌ L'application ne démarre pas (`npm run dev` échoue)

**Vérifications à faire dans l'ordre :**

1. **Vérifiez la version de Node.js :**
   ```bash
   node --version
   # doit afficher v18.x.x ou supérieur
   ```
   Si la version est inférieure à 18, mettez à jour Node.js sur [nodejs.org](https://nodejs.org).

2. **Vérifiez que vous êtes dans le bon dossier :**
   ```bash
   # Vous devez être dans app/, pas à la racine
   cd app
   npm run dev
   ```

3. **Supprimez `node_modules` et réinstallez :**
   ```bash
   rm -rf node_modules
   npm install
   npm run dev
   ```

---

### ❌ Variables d'environnement manquantes

**Symptômes :** Erreur mentionnant `APIFY_API_TOKEN`, `GEMINI_API_KEY` ou `ANTHROPIC_API_KEY`.

**Solution :**

1. Vérifiez que le fichier `.env` existe à la **racine du projet** (pas dans `app/`) :
   ```bash
   # Depuis la racine du projet
   ls -la .env
   ```

2. Si le fichier n'existe pas, créez-le :
   ```bash
   cp .env.example .env
   ```

3. Ouvrez `.env` et remplissez les 3 clés :
   ```env
   APIFY_API_TOKEN=apify_api_xxxxxxxxxxxxxxxxxxxxxxxx
   GEMINI_API_KEY=AIzaSyxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
   ANTHROPIC_API_KEY=sk-ant-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
   ```

4. Redémarrez l'application.

> ⚠️ Le fichier `.env` doit être à la **racine** du projet, au même niveau que `README.md`.

---

### ❌ Erreur `ENOENT: no such file or directory` sur `data/*.csv`

**Cause :** Les fichiers CSV n'existent pas encore.

**Solution :** Les fichiers sont créés automatiquement au premier lancement. Si l'erreur persiste, créez-les manuellement :

```bash
# Depuis la racine du projet
mkdir -p data
touch data/configs.csv data/creators.csv data/videos.csv
```

---

### ❌ Erreur Apify : "Unauthorized" ou quota épuisé

**Causes possibles :**
- Clé API invalide ou copiée incorrectement
- Quota mensuel gratuit épuisé

**Solutions :**
1. Vérifiez votre clé sur [console.apify.com](https://console.apify.com) → Settings → API & Integrations
2. Vérifiez votre consommation et votre solde sur [console.apify.com](https://console.apify.com)
3. Si le quota est épuisé, attendez la prochaine remise mensuelle ou passez à un plan payant

---

### ❌ Erreur Gemini : "API key not valid" ou "RESOURCE_EXHAUSTED"

**Causes possibles :**
- Clé API Gemini invalide
- Quota de l'API atteint

**Solutions :**
1. Vérifiez votre clé sur [aistudio.google.com](https://aistudio.google.com) → API Keys
2. Vérifiez les quotas dans la [Google Cloud Console](https://console.cloud.google.com)
3. Attendez le lendemain (les quotas se réinitialisent quotidiennement)

---

### ❌ Erreur Anthropic : "Invalid API key" ou "credit balance is too low"

**Causes possibles :**
- Clé API invalide ou expirée
- Solde de crédit insuffisant

**Solutions :**
1. Vérifiez votre clé sur [console.anthropic.com](https://console.anthropic.com) → API Keys
2. Vérifiez votre solde et rechargez si nécessaire
3. Si la clé était visible une seule fois et que vous ne l'avez pas sauvegardée, régénérez-en une nouvelle

---

### ❌ Le pipeline s'arrête sans message d'erreur

**Vérifications :**
1. Consultez les logs dans la console de votre terminal
2. Vérifiez que les créateurs ajoutés ont bien des Reels publics
3. Vérifiez que la catégorie de la configuration correspond à celle des créateurs
4. Réduisez le paramètre **Days lookback** si les comptes n'ont pas posté récemment

---

### ❌ `localhost:3000` ne répond pas

**Solution :**
1. Vérifiez que `npm run dev` tourne toujours dans votre terminal
2. Si le port 3000 est occupé, Next.js utilisera automatiquement le port 3001 (vérifiez la sortie du terminal)
3. Essayez [http://localhost:3001](http://localhost:3001)

---

## Vérification rapide de l'environnement

```bash
# Vérifier Node.js
node --version

# Vérifier npm
npm --version

# Vérifier que .env existe à la racine
ls .env

# Vérifier que les dépendances sont installées
ls app/node_modules | head -5
```

---

---

# Troubleshooting — Social Media AI

> **EN** | [FR ci-dessus ↑](#dépannage--social-media-ai)

---

## Common errors and solutions

### ❌ "Cannot find module" or "Module not found"

**Cause:** Node.js dependencies are not installed.

**Solution:**
```bash
cd app
npm install
```

---

### ❌ Application won't start (`npm run dev` fails)

**Checks to perform in order:**

1. **Check your Node.js version:**
   ```bash
   node --version
   # should display v18.x.x or higher
   ```
   If the version is below 18, update Node.js at [nodejs.org](https://nodejs.org).

2. **Check you are in the right folder:**
   ```bash
   # You must be in app/, not at the root
   cd app
   npm run dev
   ```

3. **Delete `node_modules` and reinstall:**
   ```bash
   rm -rf node_modules
   npm install
   npm run dev
   ```

---

### ❌ Missing environment variables

**Symptoms:** Error mentioning `APIFY_API_TOKEN`, `GEMINI_API_KEY` or `ANTHROPIC_API_KEY`.

**Solution:**

1. Check that the `.env` file exists at the **project root** (not in `app/`):
   ```bash
   # From the project root
   ls -la .env
   ```

2. If the file doesn't exist, create it:
   ```bash
   cp .env.example .env
   ```

3. Open `.env` and fill in the 3 keys:
   ```env
   APIFY_API_TOKEN=apify_api_xxxxxxxxxxxxxxxxxxxxxxxx
   GEMINI_API_KEY=AIzaSyxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
   ANTHROPIC_API_KEY=sk-ant-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
   ```

4. Restart the application.

> ⚠️ The `.env` file must be at the **project root**, at the same level as `README.md`.

---

### ❌ `ENOENT: no such file or directory` on `data/*.csv`

**Cause:** CSV files don't exist yet.

**Solution:** Files are created automatically on first run. If the error persists, create them manually:

```bash
# From the project root
mkdir -p data
touch data/configs.csv data/creators.csv data/videos.csv
```

---

### ❌ Apify error: "Unauthorized" or quota exceeded

**Possible causes:**
- Invalid or incorrectly copied API key
- Monthly free quota exhausted

**Solutions:**
1. Check your key at [console.apify.com](https://console.apify.com) → Settings → API & Integrations
2. Check your usage and balance at [console.apify.com](https://console.apify.com)
3. If quota is exhausted, wait for the next monthly reset or upgrade to a paid plan

---

### ❌ Gemini error: "API key not valid" or "RESOURCE_EXHAUSTED"

**Possible causes:**
- Invalid Gemini API key
- API quota reached

**Solutions:**
1. Check your key at [aistudio.google.com](https://aistudio.google.com) → API Keys
2. Check quotas in the [Google Cloud Console](https://console.cloud.google.com)
3. Wait until the next day (quotas reset daily)

---

### ❌ Anthropic error: "Invalid API key" or "credit balance is too low"

**Possible causes:**
- Invalid or expired API key
- Insufficient credit balance

**Solutions:**
1. Check your key at [console.anthropic.com](https://console.anthropic.com) → API Keys
2. Check your balance and top up if needed
3. If the key was only shown once and you didn't save it, generate a new one

---

### ❌ Pipeline stops with no error message

**Checks:**
1. Look at the logs in your terminal console
2. Verify that the added creators have public Reels
3. Check that the configuration category matches the creators' category
4. Reduce the **Days lookback** parameter if accounts haven't posted recently

---

### ❌ `localhost:3000` is not responding

**Solution:**
1. Check that `npm run dev` is still running in your terminal
2. If port 3000 is occupied, Next.js will automatically use port 3001 (check terminal output)
3. Try [http://localhost:3001](http://localhost:3001)

---

## Quick environment check

```bash
# Check Node.js
node --version

# Check npm
npm --version

# Check .env exists at root
ls .env

# Check dependencies are installed
ls app/node_modules | head -5
```
