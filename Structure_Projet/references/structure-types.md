# Structure Types — Dossiers Additionnels par Type

## app-web
```
src/
├── components/      ← Composants réutilisables
├── pages/           ← Pages de l'application
├── styles/          ← CSS/SCSS global
├── utils/           ← Fonctions utilitaires
├── hooks/           ← Custom React hooks
├── lib/             ← Bibliothèques et configs
└── types/           ← TypeScript types
public/
├── assets/
│   ├── images/
│   ├── fonts/
│   └── icons/
└── favicon.ico
```

## saas
```
src/
├── components/
├── pages/
│   ├── auth/        ← Login, register, reset
│   ├── dashboard/   ← Interface principale
│   ├── settings/    ← Paramètres utilisateur
│   └── admin/       ← Administration
├── lib/
│   ├── auth/        ← Gestion authentification
│   ├── billing/     ← Stripe / paiements
│   └── db/          ← Clients base de données
├── api/             ← API routes
└── types/
emails/              ← Templates d'emails transactionnels
migrations/          ← Migrations base de données
```

## site-web / landing-page
```
src/
├── sections/        ← Sections de la landing (hero, features, pricing...)
├── components/
├── styles/
└── assets/
content/
├── copy/            ← Textes et copywriting
└── seo/             ← Meta, sitemap, structured data
```

## api-backend
```
src/
├── routes/          ← Définition des routes API
├── controllers/     ← Logique de traitement
├── middleware/      ← Auth, validation, logging
├── models/          ← Modèles de données
├── services/        ← Logique métier
├── utils/           ← Fonctions utilitaires
└── validators/      ← Validation des entrées
tests/
├── unit/
├── integration/
└── e2e/
migrations/
└── .gitkeep
```

## automation-n8n
```
workflows/
├── exports/         ← JSON exports des workflows n8n
├── screenshots/     ← Captures pour documentation
└── versions/        ← Historique des versions
scripts/
├── triggers/        ← Scripts de déclenchement
├── processors/      ← Transformation des données
└── notifiers/       ← Envoi de notifications
data/
├── samples/         ← Données de test
└── mappings/        ← Correspondances de champs
```

## ai-agent
```
agent/
├── prompts/         ← System prompts versionnés
│   ├── main.md      ← Prompt principal
│   └── tools/       ← Prompts pour les outils
├── tools/           ← Définitions des outils/fonctions
├── memory/          ← Gestion de la mémoire
│   ├── short-term/
│   └── long-term/
├── chains/          ← Pipelines et chaînes
└── evaluations/     ← Tests de l'agent
data/
├── raw/             ← Données brutes
├── processed/       ← Données traitées
└── embeddings/      ← Vecteurs (si RAG)
```

## task-automation
```
scripts/
├── tasks/           ← Un fichier par tâche automatisée
├── schedulers/      ← Configurations cron / scheduler
├── utils/           ← Fonctions partagées
└── watchers/        ← File/event watchers
config/
├── schedules.json   ← Planning des tâches
└── mappings.json    ← Correspondances et configs
logs/
└── .gitkeep
```
