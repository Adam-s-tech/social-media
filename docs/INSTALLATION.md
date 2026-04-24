# Installation — Social Media AI

> **FR** | [EN below ↓](#installation--social-media-ai-1)

---

## Prérequis

Avant de commencer, assurez-vous d'avoir installé les éléments suivants :

### 1. Node.js (version 18 ou supérieure)

Node.js est le moteur qui fait tourner l'application. La version LTS (Long Term Support) est recommandée.

**Windows / Mac / Linux :**
1. Allez sur [nodejs.org](https://nodejs.org)
2. Téléchargez la version **LTS** (ex: 20.x)
3. Lancez l'installeur et suivez les étapes
4. Vérifiez l'installation :

```bash
node --version
# doit afficher v18.x.x ou supérieur

npm --version
# doit afficher 9.x.x ou supérieur
```

### 2. Git

Git est nécessaire pour cloner le dépôt.

**Windows :** Téléchargez [git-scm.com](https://git-scm.com/download/win)  
**Mac :** Git est souvent préinstallé. Sinon : `brew install git`  
**Linux (Ubuntu/Debian) :** `sudo apt install git`

Vérifiez :
```bash
git --version
# doit afficher git version 2.x.x
```

### 3. Un éditeur de code (recommandé : VS Code)

[Visual Studio Code](https://code.visualstudio.com/) est gratuit et idéal pour ce projet.

Extensions utiles à installer dans VS Code :
- **ESLint** (analyse du code)
- **Tailwind CSS IntelliSense** (autocomplétion CSS)
- **Prettier** (formatage automatique)

---

## Installation pas à pas

### Étape 1 — Cloner le dépôt

Ouvrez un terminal (ou VS Code → Terminal → Nouveau terminal) et exécutez :

```bash
git clone https://github.com/Adam-s-tech/social-media.git
cd social-media
```

### Étape 2 — Créer le fichier `.env`

```bash
cp .env.example .env
```

Ouvrez le fichier `.env` et remplissez vos clés API (voir [API_KEYS.md](API_KEYS.md)) :

```env
APIFY_API_TOKEN=apify_api_xxxxxxxxxxxxxxxxxxxxxxxx
GEMINI_API_KEY=AIzaSyxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
ANTHROPIC_API_KEY=sk-ant-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

> ⚠️ Ce fichier est ignoré par Git (`.gitignore`). Ne le partagez jamais.

### Étape 3 — Installer les dépendances Node.js

```bash
cd app
npm install
```

Cette étape télécharge tous les packages nécessaires (peut prendre 1-2 minutes).

### Étape 4 — Lancer l'application

```bash
npm run dev
```

Vous devriez voir :

```
▲ Next.js 15.x.x
- Local: http://localhost:3000
```

Ouvrez [http://localhost:3000](http://localhost:3000) dans votre navigateur.

---

## Vérification

Si tout fonctionne, vous devriez voir le dashboard de Social Media AI.

En cas de problème → consultez [TROUBLESHOOTING.md](TROUBLESHOOTING.md).

---

---

# Installation — Social Media AI

> **EN** | [FR ci-dessus ↑](#installation--social-media-ai)

---

## Prerequisites

Before starting, make sure you have the following installed:

### 1. Node.js (version 18 or higher)

Node.js is the engine that runs the application. The LTS (Long Term Support) version is recommended.

**Windows / Mac / Linux:**
1. Go to [nodejs.org](https://nodejs.org)
2. Download the **LTS** version (e.g. 20.x)
3. Run the installer and follow the steps
4. Verify the installation:

```bash
node --version
# should display v18.x.x or higher

npm --version
# should display 9.x.x or higher
```

### 2. Git

Git is required to clone the repository.

**Windows:** Download from [git-scm.com](https://git-scm.com/download/win)  
**Mac:** Git is often pre-installed. Otherwise: `brew install git`  
**Linux (Ubuntu/Debian):** `sudo apt install git`

Verify:
```bash
git --version
# should display git version 2.x.x
```

### 3. A code editor (recommended: VS Code)

[Visual Studio Code](https://code.visualstudio.com/) is free and ideal for this project.

Useful extensions to install in VS Code:
- **ESLint** (code analysis)
- **Tailwind CSS IntelliSense** (CSS autocompletion)
- **Prettier** (automatic formatting)

---

## Step-by-step installation

### Step 1 — Clone the repository

Open a terminal (or VS Code → Terminal → New Terminal) and run:

```bash
git clone https://github.com/Adam-s-tech/social-media.git
cd social-media
```

### Step 2 — Create the `.env` file

```bash
cp .env.example .env
```

Open the `.env` file and fill in your API keys (see [API_KEYS.md](API_KEYS.md)):

```env
APIFY_API_TOKEN=apify_api_xxxxxxxxxxxxxxxxxxxxxxxx
GEMINI_API_KEY=AIzaSyxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
ANTHROPIC_API_KEY=sk-ant-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

> ⚠️ This file is ignored by Git (`.gitignore`). Never share it.

### Step 3 — Install Node.js dependencies

```bash
cd app
npm install
```

This step downloads all necessary packages (may take 1-2 minutes).

### Step 4 — Start the application

```bash
npm run dev
```

You should see:

```
▲ Next.js 15.x.x
- Local: http://localhost:3000
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

---

## Verification

If everything works, you should see the Social Media AI dashboard.

If something goes wrong → check [TROUBLESHOOTING.md](TROUBLESHOOTING.md).
