# Three Engine Model — EA Command Centre

## Philosophie

Le Three Engine Model est un framework de gestion de projet conçu pour maximiser la productivité
avec Claude Code comme agent principal. Il repose sur trois moteurs complémentaires :

## Les Trois Moteurs

### Moteur 1 — Intelligence (intel/)
> "Savoir avant d'agir"

Tout le contexte du projet centralisé :
- `projet.md` → La vision et les objectifs
- `stack.md` → Les choix technologiques et leurs justifications
- `client.md` → L'audience et les besoins
- `focus.md` → Les priorités du moment

**Règle :** Avant toute action, l'agent lit `intel/` pour agir avec contexte.

### Moteur 2 — Blueprints (blueprints/)
> "Planifier avant d'exécuter"

Les SOPs (Standard Operating Procedures) en Markdown :
- Un fichier par workflow récurrent
- Format : Titre → Contexte → Étapes → Critères de succès
- Versionnés dans git comme du code

**Règle :** Si une tâche se répète plus de 2 fois → créer un blueprint.

### Moteur 3 — Equipment (equipment/)
> "Automatiser le déterministe"

Les scripts pour les tâches sans ambiguïté :
- Un script par tâche déterministe
- Python ou Bash selon le contexte
- Documentés avec docstrings

**Règle :** Si le résultat est toujours le même → créer un equipment.

---

## Boucle de Session

```
DÉBUT DE SESSION
     ↓
live/state.md   ← Où en est-on ?
     ↓
live/tasks.md   ← Quoi faire ?
     ↓
intel/focus.md  ← Quelles priorités ?
     ↓
ACTION
     ↓
Si workflow récurrent → blueprints/
Si tâche déterministe → equipment/
Si décision prise → decisions/ledger.md
     ↓
FIN DE SESSION
live/state.md ← Mise à jour
```

---

## Principes Fondamentaux

1. **Rien ne se perd** → `archive/` pour tout ce qui est obsolète
2. **Tout est documenté** → décisions dans `decisions/ledger.md`
3. **Secrets hors du code** → `.env` uniquement
4. **Périmètre strict** → l'agent ne sort jamais du dossier projet
5. **Kebab-case partout** → nommage cohérent et universel

---

## Créateur
EZZOUHIR Elmustapha — HHS Agency
EA Command Centre — Three Engine Model
