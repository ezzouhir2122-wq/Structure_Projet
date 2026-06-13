---
name: Structure_Projet
description: >
  Skill universel qui génère AUTOMATIQUEMENT et INSTANTANÉMENT la structure complète d'un projet
  professionnel sans interview longue — en une seule passe. Couvre tous les types : App Web, SaaS,
  Landing Page, AI Agent, Automation n8n, API Backend, Automatisation de tâches, Site Web.
  DÉCLENCHER CE SKILL DÈS QUE l'utilisateur dit : "crée un projet", "nouvelle app", "setup projet",
  "structure pour X", "initialise Y", "lance le projet Z", "démarre l'app", "nouveau projet",
  "génère la structure", "prépare le dossier", "monte le projet", "structure de dossiers",
  "projet [nom]", "app [nom]", "site [nom]", "api [nom]", ou toute demande impliquant
  la création d'un projet quel que soit le type ou la taille.
  Produit : arborescence complète + CLAUDE.md (8 règles) + SECURITY.md + COMPLIANCE.md +
  intel/ rempli + .env.example + README.md + .gitignore + git init + premier commit.
  NE PAS utiliser ea-project-builder — ce skill le remplace et le surpasse.
---

# Structure_Projet — Générateur Universel de Projets

Génère en **une seule passe automatique** la structure complète d'un projet professionnel,
prête à utiliser dans Claude Code dès la première session.

---

## ÉTAPE 0 — Détection Automatique du Type

**Ne pas faire d'interview longue.** Extraire depuis le message de l'utilisateur :

| Signal détecté | Type assigné |
|---|---|
| "landing", "vitrine", "site web", "portfolio" | `site-web` |
| "saas", "plateforme", "multi-utilisateurs", "abonnement" | `saas` |
| "app", "application", "interface", "dashboard" | `app-web` |
| "n8n", "workflow", "automatisation", "automate", "pipeline" | `automation-n8n` |
| "agent", "chatbot", "assistant", "IA conversationnelle", "llm" | `ai-agent` |
| "api", "backend", "rest", "microservice", "endpoint" | `api-backend` |
| "tâche", "script", "batch", "scheduled", "cron", "automate" | `task-automation` |
| Aucun signal clair | `custom` |

**Extraire aussi :**
- **Nom du projet** → depuis le titre donné, sinon générer un nom kebab-case logique
- **Stack probable** → déduire depuis les mots-clés (Next.js, Supabase, Python, n8n, etc.)
- **Objectif** → reformuler en une phrase depuis la demande

Si ambiguïté sur le nom seulement → demander UNE seule question, puis générer tout.

---

## ÉTAPE 1 — Vérification Anti-Écrasement

```bash
# Toujours vérifier avant de créer
if [ -d "[nom-projet]" ]; then
  echo "⚠️ Dossier existant détecté — arrêt. Renommer ou supprimer d'abord."
  exit 1
fi
```

---

## ÉTAPE 2 — Génération de la Structure Complète

Créer TOUT d'un coup. Chaque fichier est rempli avec du contenu réel — **jamais vide, jamais placeholder générique**.

### Arborescence Universelle

```
[nom-projet]/
│
├── CLAUDE.md                    ← 8 règles essentielles (voir template §A)
├── CLAUDE.local.md              ← Overrides locaux (non commité)
├── README.md                    ← Description projet (voir template §B)
├── .env.example                 ← Variables d'environnement typées par stack
├── .gitignore                   ← Complet selon le type détecté
│
├── SECURITY.md                  ← Politique de sécurité (voir template §C)
├── COMPLIANCE.md                ← Règles de conformité légale (voir template §D)
│
├── .claude/
│   ├── settings.json            ← Config Claude Code standard
│   └── rules/
│       ├── permissions.md       ← Périmètre d'action de l'agent
│       ├── voice.md             ← Ton et style de communication
│       ├── security.md          ← Règles sécurité pour l'agent
│       └── naming.md            ← Conventions de nommage
│
├── intel/
│   ├── projet.md                ← Fiche projet complète (remplie)
│   ├── stack.md                 ← Stack déduite + justification
│   ├── client.md                ← Audience / client cible
│   └── focus.md                 ← Priorités Phase 1 + deadlines
│
├── blueprints/                  ← SOPs Markdown (workflows)
│   ├── 00-demarrage.md          ← Blueprint de démarrage de session
│   └── 01-deploiement.md        ← Blueprint de déploiement (selon type)
│
├── equipment/                   ← Scripts déterministes
│   ├── setup.sh                 ← Script d'installation des dépendances
│   └── check-env.py             ← Vérification des variables d'environnement
│
├── templates/
│   ├── session-brief.md         ← Template début de session
│   └── closeout.md              ← Template fin de session
│
├── references/
│   ├── three-engine-model.md    ← Référence du modèle EA
│   ├── architecture.md          ← Décisions d'architecture initiales
│   └── goldstandard/
│       └── .gitkeep
│
├── live/
│   ├── state.md                 ← État de session (lire EN PREMIER)
│   ├── tasks.md                 ← Backlog de tâches priorisé
│   └── sprint-actuel/
│       └── .gitkeep
│
├── decisions/
│   └── ledger.md                ← Journal de décisions (append-only)
│
├── tests/                       ← Tests (selon type de projet)
│   └── .gitkeep
│
├── docs/                        ← Documentation externe
│   └── .gitkeep
│
├── .tmp/                        ← Fichiers temporaires (non commités)
│   └── .gitkeep
│
└── archive/                     ← Rien ne se supprime — tout s'archive
    └── .gitkeep
```

**Ajouter les dossiers spécifiques au type détecté** → voir `references/structure-types.md`

---

## ÉTAPE 3 — Templates de Fichiers Clés

### §A — CLAUDE.md (8 règles essentielles — OBLIGATOIRES)

```markdown
# CLAUDE.md — [Nom du Projet]

> Fichier de commande principal. Lire en premier à chaque session.

## Contexte Projet
**Type :** [type]
**Stack :** [stack déduite]
**Objectif :** [objectif en une phrase]
**Statut :** Phase initiale

## Commandes Rapides
- `live/state.md` → état de session actuel
- `live/tasks.md` → backlog de tâches
- `decisions/ledger.md` → historique des décisions
- `intel/focus.md` → priorités actuelles

## 8 Règles Essentielles

1. **Périmètre** : l'agent travaille UNIQUEMENT dans le dossier projet, jamais ailleurs sur la machine.
2. **Lister l'existant** : toujours vérifier ce qui existe avant de créer ou modifier quoi que ce soit.
3. **Nommage** : préfixer les fichiers avec leur contexte (ex. `rdv_`, `facture_`) pour éviter les conflits.
4. **Licences** : n'installer que des bibliothèques sous licence permissive (MIT, Apache 2.0, BSD).
5. **Services autorisés** : utiliser uniquement les prestataires validés (hébergeur UE, emails conformes RGPD, CMP cookies).
6. **Outils externes** : tout outil externe doit être validé par le propriétaire du projet avant usage.
7. **Aucun secret dans le code** : clés d'API et mots de passe UNIQUEMENT via variables d'environnement (.env).
8. **Anti-boucle** : si la même erreur se répète 5 fois → s'arrêter immédiatement et alerter le propriétaire.

## Démarrage de Session
1. Lire `live/state.md`
2. Vérifier `live/tasks.md`
3. Consulter `intel/focus.md`
4. Puis traiter la demande

## Fin de Session
1. Mettre à jour `live/state.md`
2. Logger les décisions dans `decisions/ledger.md`
3. Archiver les fichiers obsolètes dans `archive/`
```

---

### §B — README.md

```markdown
# [Nom du Projet]

> [Objectif en une phrase]

## Description
[Description du projet selon le type et le contexte détectés]

## Stack Technique
[Stack déduite automatiquement]

## Structure du Projet
Voir `intel/projet.md` pour la fiche projet complète.

## Démarrage Rapide
\`\`\`bash
cp .env.example .env
# Remplir les variables dans .env
bash equipment/setup.sh
\`\`\`

## Documentation
- `CLAUDE.md` — Règles et commandes pour l'agent IA
- `SECURITY.md` — Politique de sécurité
- `intel/` — Contexte et stack du projet
- `blueprints/` — Workflows et SOPs
- `live/` — État de session et tâches

## Licence
Propriétaire — [Nom] / HHS Agency
```

---

### §C — SECURITY.md

```markdown
# SECURITY.md — Politique de Sécurité

## Périmètre
Ce document définit les règles de sécurité applicables au projet **[Nom du Projet]**.

## Règles Fondamentales

### Secrets & Credentials
- ❌ Jamais de clés API, tokens, ou mots de passe dans le code source
- ✅ Toujours via `.env` (jamais commité)
- ✅ `.env.example` avec des valeurs fictives uniquement
- Rotation des clés : tous les 90 jours minimum

### Dépendances
- N'installer que des packages sous licence MIT, Apache 2.0, ou BSD
- Auditer avec `npm audit` ou `pip-audit` avant chaque déploiement
- Maintenir les dépendances à jour (patch security en < 48h)

### Données Utilisateurs
- Chiffrement en transit : HTTPS/TLS 1.3 obligatoire
- Chiffrement au repos : pour toute donnée sensible
- Pas de logs contenant des données personnelles
- Conformité RGPD : voir `COMPLIANCE.md`

### Accès & Authentification
- Principe du moindre privilège pour tous les rôles
- MFA obligatoire pour les accès admin
- Sessions expirantes (max 24h)
- Blacklist des tokens révoqués

### Code & Déploiement
- Code review obligatoire avant merge en production
- Pas de `eval()`, `exec()`, ou injection de code dynamique
- Validation et sanitisation de toutes les entrées utilisateur
- Headers sécurité : CSP, HSTS, X-Frame-Options

## Gestion des Incidents
- Incident détecté → alerter immédiatement le responsable projet
- Logger dans `decisions/ledger.md` avec timestamp
- Patch en < 24h pour les vulnérabilités critiques

## Contacts Sécurité
- Responsable projet : [Nom]
- Escalade : signaler via `live/state.md`
```

---

### §D — COMPLIANCE.md

```markdown
# COMPLIANCE.md — Conformité & Règles Légales

## Périmètre
Règles de conformité applicables au projet **[Nom du Projet]**.

## RGPD / Protection des Données
- Collecte minimale : ne collecter que les données strictement nécessaires
- Consentement explicite avant toute collecte
- Droit à l'effacement : procédure documentée dans `blueprints/`
- Durée de conservation : définie et respectée
- Registre des traitements : maintenu à jour
- DPO : [à désigner si applicable]

## Hébergement & Localisation des Données
- Données personnelles hébergées en UE uniquement
- Prestataires certifiés ISO 27001 préférés
- Sous-traitants : DPA (Data Processing Agreement) obligatoire

## Licences Logicielles
- Bibliothèques : MIT, Apache 2.0, BSD uniquement (voir SECURITY.md)
- Assets visuels : droits vérifiés avant intégration
- Polices : licences commerciales si usage commercial
- Pas de contenu sous copyright sans autorisation explicite

## Accessibilité
- Objectif WCAG 2.1 niveau AA
- Tests d'accessibilité avant mise en production

## Mentions Légales & CGU
- Mentions légales obligatoires si site public
- CGU/CGV à rédiger avant lancement
- Politique de confidentialité à publier

## Cookies & Tracking
- CMP (Consent Management Platform) obligatoire
- Pas de tracking sans consentement préalable
- Liste des cookies documentée

## Dernière révision
[Date de création du projet]
```

---

### §E — .env.example (adapté par type)

**Pour app-web / saas / site-web :**
```env
# === CONFIGURATION PROJET ===
NODE_ENV=development
APP_URL=http://localhost:3000
APP_SECRET=your-secret-key-here

# === BASE DE DONNÉES ===
DATABASE_URL=postgresql://user:password@localhost:5432/dbname
SUPABASE_URL=https://your-project.supabase.co
SUPABASE_ANON_KEY=your-anon-key
SUPABASE_SERVICE_KEY=your-service-key

# === AUTHENTIFICATION ===
JWT_SECRET=your-jwt-secret
SESSION_SECRET=your-session-secret

# === APIs EXTERNES ===
ANTHROPIC_API_KEY=sk-ant-...
OPENAI_API_KEY=sk-...
STRIPE_SECRET_KEY=sk_test_...
STRIPE_WEBHOOK_SECRET=whsec_...

# === EMAIL ===
SMTP_HOST=smtp.example.com
SMTP_PORT=587
SMTP_USER=your@email.com
SMTP_PASS=your-password
EMAIL_FROM=noreply@yourapp.com

# === STOCKAGE ===
STORAGE_BUCKET=your-bucket-name
STORAGE_REGION=eu-west-1

# === MONITORING ===
SENTRY_DSN=https://...@sentry.io/...
LOG_LEVEL=info
```

**Pour api-backend :**
```env
# === API CONFIG ===
PORT=8000
API_VERSION=v1
DEBUG=false
ALLOWED_ORIGINS=http://localhost:3000

# === DATABASE ===
DATABASE_URL=postgresql://user:password@localhost:5432/dbname
REDIS_URL=redis://localhost:6379

# === SÉCURITÉ ===
API_KEY=your-api-key
JWT_SECRET=your-jwt-secret
RATE_LIMIT_PER_MINUTE=60

# === SERVICES ===
ANTHROPIC_API_KEY=sk-ant-...
WEBHOOK_SECRET=your-webhook-secret
```

**Pour automation-n8n / task-automation :**
```env
# === N8N CONFIG ===
N8N_HOST=localhost
N8N_PORT=5678
N8N_BASIC_AUTH_USER=admin
N8N_BASIC_AUTH_PASSWORD=your-password
N8N_ENCRYPTION_KEY=your-encryption-key

# === WEBHOOKS ===
WEBHOOK_BASE_URL=https://your-domain.com
WEBHOOK_SECRET=your-secret

# === INTÉGRATIONS ===
GOOGLE_CLIENT_ID=your-client-id
GOOGLE_CLIENT_SECRET=your-client-secret
SLACK_BOT_TOKEN=xoxb-...
WHATSAPP_API_KEY=your-key
AIRTABLE_API_KEY=pat...

# === ANTHROPIC ===
ANTHROPIC_API_KEY=sk-ant-...
```

**Pour ai-agent :**
```env
# === LLM PROVIDERS ===
ANTHROPIC_API_KEY=sk-ant-...
OPENAI_API_KEY=sk-...
MODEL_NAME=claude-sonnet-4-6

# === AGENT CONFIG ===
MAX_ITERATIONS=10
TEMPERATURE=0.7
MAX_TOKENS=4096

# === MÉMOIRE / RAG ===
SUPABASE_URL=https://your-project.supabase.co
SUPABASE_SERVICE_KEY=your-service-key
PINECONE_API_KEY=your-key
PINECONE_INDEX=your-index

# === OUTILS AGENT ===
TAVILY_API_KEY=tvly-...
SERPAPI_KEY=your-key

# === DÉPLOIEMENT ===
PORT=8000
AGENT_SECRET=your-secret
```

---

### §F — .gitignore (universel complet)

```gitignore
# === SECRETS ===
.env
.env.local
.env.*.local
credentials.json
token.json
*.pem
*.key
*.p12
*.pfx
service-account.json

# === CLAUDE CODE ===
CLAUDE.local.md
.claude/settings.local.json

# === NODE.JS ===
node_modules/
npm-debug.log*
yarn-debug.log*
yarn-error.log*
.pnpm-debug.log*
dist/
build/
.next/
.nuxt/
.cache/

# === PYTHON ===
__pycache__/
*.py[cod]
*.pyo
.venv/
venv/
env/
*.egg-info/
dist/
.pytest_cache/
.mypy_cache/

# === TEMPORAIRES ===
.tmp/
*.log
*.tmp
*.bak
*.swp
*~

# === OS ===
.DS_Store
Thumbs.db
desktop.ini

# === IDE ===
.vscode/settings.json
.idea/
*.sublime-project
*.sublime-workspace

# === TESTS ===
coverage/
.nyc_output/
htmlcov/

# === UPLOADS ===
uploads/
storage/local/
```

---

## ÉTAPE 4 — Fichiers de Démarrage Spécifiques par Type

### Pour `app-web` / `saas` / `site-web`
Ajouter dans la structure :
```
src/
├── components/
├── pages/
├── styles/
├── utils/
├── hooks/
└── lib/
public/
└── assets/
```
`blueprints/01-deploiement.md` → workflow Vercel/Netlify

### Pour `api-backend`
Ajouter :
```
src/
├── routes/
├── controllers/
├── middleware/
├── models/
├── services/
└── utils/
tests/
├── unit/
└── integration/
```
`blueprints/01-deploiement.md` → workflow Railway/Render/VPS

### Pour `automation-n8n`
Ajouter :
```
workflows/
├── exports/         ← Exports JSON des workflows n8n
└── screenshots/     ← Captures des workflows
scripts/
├── triggers/
└── processors/
```
`blueprints/01-deploiement.md` → workflow déploiement n8n self-hosted

### Pour `ai-agent`
Ajouter :
```
agent/
├── prompts/         ← System prompts versionnés
├── tools/           ← Définitions des outils
├── memory/          ← Gestion de la mémoire
└── chains/          ← Chains / pipelines
data/
├── raw/
└── processed/
```

### Pour `task-automation`
Ajouter :
```
scripts/
├── tasks/           ← Un script par tâche automatisée
├── schedulers/      ← Configurations cron
└── utils/
logs/
└── .gitkeep
```

---

## ÉTAPE 5 — Remplissage intel/

### intel/projet.md
```markdown
# [Nom du Projet]

**Type :** [type détecté]
**Objectif :** [objectif extrait]
**Créé le :** [date du jour]
**Statut :** Phase 1 — Initialisation

## Description
[Description complète déduite du contexte]

## Pour qui
[Audience / utilisateurs cibles déduits]

## Stack Technique
[Stack déduite automatiquement]

## Livrables Phase 1
- [ ] Structure du projet initialisée ✅
- [ ] Configuration environnement
- [ ] Premier endpoint / composant / workflow
- [ ] Tests de base
- [ ] Déploiement preview

## Critères de Succès
[Définis selon le type de projet]
```

### intel/stack.md
```markdown
# Stack Technique — [Nom du Projet]

## Frontend
[Selon type : Next.js 14, React, Vue, HTML/CSS vanilla...]

## Backend
[Selon type : Node.js/Express, FastAPI, n8n, Claude API...]

## Base de données
[Selon type : Supabase, PostgreSQL, SQLite, Redis...]

## Hébergement
[Phase 1 : Local → Phase 2 : VPS / Vercel / Railway]

## APIs & Services
[Selon le projet : Anthropic, Stripe, Google, WhatsApp...]

## Outils de dev
- Git + GitHub
- VS Code + extensions
- Docker (si applicable)

## Justification des choix
[Pourquoi cette stack pour ce projet]
```

### intel/focus.md
```markdown
# Focus Actuel — [Nom du Projet]

**Semaine du :** [date]

## Top 3 Priorités
1. Configurer l'environnement (.env + dépendances)
2. Créer le premier livrable fonctionnel
3. Mettre en place les tests de base

## Blocages Identifiés
- Aucun pour l'instant

## Décisions en Attente
- Choix de l'hébergeur final
- Stratégie d'authentification

## Prochaine Milestone
[Premier livrable fonctionnel]
```

---

## ÉTAPE 6 — Git Init & Premier Commit

```bash
cd [nom-projet]
git init
git add .
git commit -m "feat: init [nom-projet] — Structure_Projet Universal Generator

- Structure complète Three Engine Model
- CLAUDE.md avec 8 règles essentielles
- SECURITY.md + COMPLIANCE.md
- intel/ rempli (projet, stack, focus, client)
- .env.example configuré pour [type]
- blueprints/ et equipment/ initialisés
- .gitignore universel"
```

---

## ÉTAPE 7 — Livraison Finale

Livrer dans cet ordre :

### 1. Confirmation de création
```
✅ Projet [nom] créé avec succès
📁 Type détecté : [type]
🛠 Stack déduite : [stack]
📍 Localisation : ./[nom-projet]/
```

### 2. Arborescence complète (afficher avec indentation)

### 3. Cheat Sheet de Démarrage Immédiat
```
═══════════════════════════════════════════
  DÉMARRAGE RAPIDE — [NOM PROJET]
═══════════════════════════════════════════

PREMIÈRE FOIS :
  cp .env.example .env
  → Remplir les vraies valeurs dans .env
  bash equipment/setup.sh

CHAQUE SESSION :
  1. Lire  → live/state.md
  2. Check → live/tasks.md
  3. Focus → intel/focus.md
  Puis traiter la demande

FIN DE SESSION :
  → Mettre à jour live/state.md
  → Logger dans decisions/ledger.md

CONSTRUIRE UN WORKFLOW :
  → blueprints/[nom-workflow].md
  → "construis un blueprint pour [tâche]"

CONSTRUIRE UN SCRIPT :
  → equipment/[nom-script].py
  → "construis l'equipment pour [tâche]"

SÉCURITÉ :
  → Jamais de secrets dans le code
  → Tout dans .env uniquement
  → Voir SECURITY.md pour les règles complètes
═══════════════════════════════════════════
```

### 4. Prochaines Actions Suggérées
- **Blueprint prioritaire** : selon le type détecté
- **Equipment prioritaire** : `check-env.py` pour valider le setup
- **Première tâche** : remplir `.env` avec les vraies valeurs

---

## Règles Non-Négociables du Skill

1. **Jamais écraser** — vérifier l'existence avant toute création
2. **Tout remplir** — aucun fichier ne reste vide ou avec "TODO" générique
3. **Déduire intelligemment** — extraire type, stack, objectif depuis le contexte
4. **Une seule passe** — générer tout sans interview longue
5. **kebab-case** — tous les noms de fichiers et dossiers
6. **Secrets jamais dans le code** — toujours via .env
7. **SECURITY.md + COMPLIANCE.md** — toujours inclus, jamais optionnels
8. **Git commit** — toujours avec un message descriptif complet

---

## Références

- `references/structure-types.md` — Détail des dossiers additionnels par type
- `references/three-engine-model.md` — Philosophie du modèle EA Command Centre
