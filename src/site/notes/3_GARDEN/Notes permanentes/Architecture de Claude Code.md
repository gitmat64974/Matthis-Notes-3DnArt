---
{"dg-publish":true,"permalink":"/3_GARDEN/Notes permanentes/Architecture de Claude Code/","tags":["note_permanente","architecture","claude_code","système"],"dg-note-properties":{"MOC":["[[3_GARDEN/MOCs/INFORMATIQUE|INFORMATIQUE]]"],"source":["Documentation officielle Claude Code","Analyse du répertoire ~/.claude/","Configuration personnelle de Matthis"],"Projets":null,"tags":["note_permanente","architecture","claude_code","système"],"creation date":20260404,"aliases":["Claude Code Architecture","Claude Code Internals","Claude Code Configuration","Claude Code System"]}}
---


# Architecture et fonctionnement complet de Claude Code

## Introduction

Claude Code n'est pas un simple chatbot en terminal. C'est un **système complet d'IA assistante** avec une architecture sophistiquée incluant :

- Accès direct au système de fichiers avec permissions granulaires
- Système de mémoire persistante multi-types
- Extensibilité via Skills (compétences) plugins
- Gestion de sessions et de projets
- Modèle de permissions avancé
- Intégration MCP (Model Context Protocol)
- Système de tâches, plans et worktrees
- Configuration entièrement declarative

---

## 1. Architecture Globale

```
~/.claude/
├── settings.json              # Configuration principale
├── settings.local.json        # Config locale (permissions, env)
├── .credentials.json          # Tokens OAuth (claude.ai, MCP)
├── skills/                    # Skills installés (extensions)
├── plugins/                  # Plugins (cache, marketplaces)
├── tasks/                    # Système de gestion de tâches
├── plans/                    # Plans d'implémentation
├── sessions/                 # Données de session (UUID)
├── projects/                 # Configuration par projet
├── shell-snapshots/          # Snapshots d'état shell
├── cache/                    # Cache divers
├── telemetry/                # Télémétrie
├── downloads/                # Fichiers téléchargés
├── file-history/             # Historique fichiers
├── history.jsonl             # Historique conversation
├── backups/                  # Sauvegardes
└── ide/                      # Intégrations IDE
```

---

## 2. Système de Configuration

### 2.1 settings.json (Configuration Globale)

**Chemin** : `~/.claude/settings.json`

**Structure** :
```json
{
  "enabledPlugins": {
    "plugin-id@marketplace": true/false
  },
  "extraKnownMarketplaces": {
    "custom-marketplace-name": {
      "source": {
        "source": "github",
        "repo": "owner/repo"
      }
    }
  },
  "autoUpdatesChannel": "latest" | "stable",
  "skipDangerousModePermissionPrompt": boolean
}
```

**Exemple réel (Matthis)** :
```json
{
  "enabledPlugins": {
    "frontend-design@claude-plugins-official": true,
    "firecrawl@claude-plugins-official": true,
    "obsidian-visual-skills@axton-obsidian-visual-skills": true,
    "n8n-mcp-skills@n8n-mcp-skills": true,
    "obsidian@obsidian-skills": true,
    "superpowers@claude-plugins-official": true,
    "skill-creator@claude-plugins-official": true
  },
  "extraKnownMarketplaces": {
    "claude-code-plugins": {...},
    "axton-obsidian-visual-skills": {...},
    "n8n-mcp-skills": {...},
    "obsidian-skills": {...}
  },
  "autoUpdatesChannel": "latest",
  "skipDangerousModePermissionPrompt": true
}
```

### 2.2 settings.local.json (Configuration Locale)

**Chemin** : `~/.claude/settings.local.json`

Contient des paramètres spécifiques à la machine locale :

```json
{
  "env": {
    "VARIABLE_ENV": "valeur"
  },
  "permissions": {
    "allow": [
      "Skill(nom-skill)",
      "Bash(commande:*pattern*)",
      "mcp__server__tool_name",
      "WebSearch",
      "WebFetch(domain:example.com)"
    ]
  }
}
```

**Permissions explicites** : Liste blanche d'actions autorisées sans prompt. Toute action non listée déclenche une demande de permission à l'utilisateur.

### 2.3 Système de Plugins

**Répertoire** : `~/.claude/plugins/`

```
plugins/
├── installed_plugins.json      # Liste plugins installés
├── known_marketplaces.json     # Marketplaces connus
├── blocklist.json              # Plugins bloqués
├── cache/                      # Cache des plugins下载
│   └── {marketplace-name}/
│       └── {plugin-name}/{version}/
└── marketplaces/               # Sources marketplace
```

**Installed plugins** : Stocke métadonnées (version, chemin, date install, git SHA)

**Marketplaces** : Configuration des sources (GitHub repos) pour télécharger plugins/skills.

### 2.4 Système de Hooks (Automation)

Claude Code supporte des **hooks** déclenches automatiquement sur événements :

- `pre-text` : Avant envoi texte à l'utilisateur
- `submit-prompt` : Quand utilisateur submit un prompt
- Autres hooks possibles

Configuration dans `settings.json` ou fichier hooks séparé. Les hooks exécutent des commandes shell ou scripts.

---

## 3. Système de Skills (Compétences)

### 3.1 Qu'est-ce qu'un Skill ?

Un **Skill** est une extension qui modifie/complète le comportement de Claude Code. C'est un package autonome avec :

- **SKILL.md** : Documentation et règles d'utilisation
- **scripts/** : Code executables (Python, JS, Bash)
- **data/** : Données statiques (CSV, JSON)
- **agents/** : Sous-agents dédiés (optionnel)

### 3.2 Structure d'un Skill

```
skills/
└── {skill-name}/
    ├── SKILL.md              # Documentation obligatoire
    ├── scripts/
    │   ├── main.py/.js       # Point d'entrée principal
    │   └── helper.py/.js     # Modules utilitaires
    ├── data/                 # Fichiers de données
    │   ├── csv/, json/
    │   └── ... (par exemple ui-reasoning.csv, colors.csv)
    ├── agents/               # Sous-agents custom
    │   └── some-agent/
    │       └── AGENT.md
    └── eval/ (optionnel)     # Tests/évaluations
```

### 3.3 Types de Skills

1. **Skills standard** : Modifient le comportement général (ex: `brainstorming`, `frontend-design`)
2. **Skills MCP** : Connectés à un serveur MCP externe (ex: `n8n-mcp-skills`)
3. **Skills data-driven** : Bases de données queryables (ex: `ui-ux-pro-max` avec CSV)

### 3.4 Invocation de Skills

- Via **slash commands** : `/skill-name args`
- Via **mention** dans prompt : `@skill-name prompt`
- Automatique par déclenchement (mots-clés)

**Exemple** :
```bash
/skill-creator  # Lance skill creator
/brainstorming  # Lance brainstorming
```

Le skill lit son `SKILL.md` et suit ses rules internes.

### 3.5 Exemple: Skill ui-ux-pro-max

**Taille** : 67 styles, 96 palettes, 57 font pairings, 13 stacks
**Données** : CSV dans `data/` (colors.csv, stacks/, typography.csv, etc.)
**Script principal** : `scripts/search.py`
**Usage** :
```bash
python3 skills/ui-ux-pro-max/scripts/search.py "beauty spa" --design-system -p "Project"
```

### 3.6 Installation et Marketplace

- **Marketplaces** : Sources GitHub définies dans `settings.json` (`extraKnownMarketplaces`)
- **Installation** : Via `/skill install {skill}` ou automatique
- **Cache** : `plugins/cache/{marketplace}/{skill}/{version}/`
- **Update** : Auto ou manuel (`/update`)

---

## 4. Système de Mémoire Persistante

### 4.1 Principe

Claude Code peut **lire et écrire** des memories dans des fichiers Markdown locaux. Ces mémoires persistent entre sessions.

### 4.2 Types de Mémoires (4 catégories)

1. **`user`** : Informations sur l'utilisateur, objectifs, connaissances
2. **`feedback`** : Retours sur l'approche (ce qui marche/ne marche pas)
3. **`project`** : États des projets, deadlines, contraintes
4. **`reference`** : Pointeurs vers ressources externes (URLs, dashboards, etc.)

### 4.3 Format des Fichiers Mémoire

**Frontmatter YAML obligatoire** :

```
---
name: nom-memoire
description: Une phrase descriptive
type: user|feedback|project|reference
---

# Contenu de la mémoire en Markdown

## Sections libres

Contenu détaillé...
```

### 4.4 Index des Mémoires: MEMORY.md

Dans le **workspace** (vault Obsidian de Matthis), un fichier `MEMORY.md` indexe toutes les mémoires :

```markdown
# Index des mémoires Claude

## Mémoires utilisateur
- [[user_profile.md]] - Informations sur l'utilisateur

## Mémoires de feedback
- [[feedback_interaction_mode.md]] - Sparring partner

## Mémoires de projet
- [[project_vault_structure.md]] - Architecture vault
```

### 4.5 Comment ça marche ?

- **Chargement** : Au début de conversation, Claude lit `MEMORY.md` et charge toutes les mémoires linkées
- **Update** : Quand l'utilisateur dit "sauvegarde cette info", Claude écrit un nouveau fichier mémoire dans le dossier mémoire et met à jour `MEMORY.md`
- **Synchronisation** : Mémoire `source_reference_projects.md` track la source principale et synchronise les dérivées

### 4.6 Emplacement des Mémoires

Les mémoires sont stockées dans un dossier dédié (par défaut `memory/` dans workspace ou `~/.claude/memory/`), avec un fichier par mémoire et l'index `MEMORY.md`.

---

## 5. Système de Tâches (Tasks)

### 5.1 Pourquoi un système de tâches ?

Claude Code est **stateless** par défaut. Le système de tâches permet de :

- Suivre l'avancement sur plusieurs tâches
- Maintenir un contexte persistant entre messages
- strukturer le travail complexe
- Marquer les tâches `pending` → `in_progress` → `completed`

### 5.2 Comment utiliser ?

**Créer une tâche** : Tool `TaskCreate`
```json
{
  "subject": "Fix bug in auth",
  "description": "What needs to be done",
  "metadata": {...}
}
```

**Voir toutes les tâches** : `TaskList` → retourne tableau avec id, subject, status, blockedBy, etc.

**Update une tâche** : `TaskUpdate` (change status, add blocks, update metadata)

**Compléter une tâche** : `TaskUpdate` avec `status: "completed"`

### 5.3 Stockage

Les tâches sont stockées en mémoire volatile (session). Pas de persistance automatique entre sessions (sauf si la session est keep-alive).

### 5.4 Bonnes Pratiques

- Créer une tâche pour chaque tâche identifiable
- Utiliser `TaskUpdate` pour marquer `in_progress` **avant** de commencer le travail
- Utiliser `addBlockedBy` pour gérer les dépendances
- Lister les tâches fréquemment pour voir ce qui avance

---

## 6. Système de Plans (Plan Mode)

### 6.1 Objectif

Avant d'implémenter une fonctionnalité non-triviale, valider l'approche avec l'utilisateur via un **plan détaillé**.

### 6.2 Workflow

```
1. EnterPlanMode()  → Claude explore codebase, conçoit plan
2. Rédige plan dans fichier (ex: plans/feature-X-plan.md)
3. ExitPlanMode()   → Présente plan à l'utilisateur pour approbation
4. (Optionnel) AskUserQuestion pour modifier plan
5. Une fois approuvé, implémente selon plan
```

### 6.3 Contenu du Plan

Doit inclure :

- **Fichiers à modifier** (liste précise)
- **Approche technique** (pourquoi cette solution)
- **Architecture** (diagrammes si utile)
- **Trade-offs considérés**
- **Tests à écrire**
- **Risques et edge cases**
- **Étapes d'implémentation** (ordonnées)

### 6.4 Allowed Prompts (dans ExitPlanMode)

Dans `ExitPlanMode`, on spécifie quels prompts/bash sont nécessaires :

```json
{
  "allowedPrompts": [
    {
      "tool": "Bash",
      "prompt": "run tests"
    },
    {
      "tool": "Bash",
      "prompt": "install dependencies"
    }
  ]
}
```

L'utilisateur doit approuver ces prompts avant l'exécution.

---

## 7. Système de Sessions

### 7.1 Qu'est-ce qu'une session ?

Une **session** est une conversation ouverte dans le terminal. Chaque session a un **UUID unique** (valeur dans `~/.claude/sessions/{uuid}/`).

### 7.2 Données de Session

```
sessions/
├── {uuid1}/
│   ├── messages.jsonl      # Tous les messages de la session
│   ├── metadata.json       # Métadonnées (start time, cwd, etc.)
│   └── tasks.json          # Tâches de cette session
├── {uuid2}/
└── ...
```

**Note dans Matthis** : Certains dossiers de session semblent avoir été nettoyés. Le répertoire `sessions/` existe mais peut être volatil.

### 7.3 Persistance

Les sessions peuvent être **rechargées** si l'historique a été conservé (`history.jsonl` global enregistre toutes les conversations).

---

## 8. Système de Worktrees (Isolation Git)

### 8.1 Pourquoi les worktrees ?

Travailler sur une branche/feature isolée sans toucher au workspace principal. **EnterWorktree** crée un git worktree temporaire.

### 8.2 Comment ça marche ?

```
EnterWorktree(name="feature-x")
→ Crée branche depuis HEAD
→ Checkout dans .claude/worktrees/{name}/
→ Switch CWD vers ce dossier
→ Travail isolé
```

**ExitWorktree** : Retour au workspace original, choix keep/remove worktree.

### 8.3 Cas d'usage

- Explorer une refactor sans risk
- Tester une approche alternative
- Prototyper en isolation

---

## 9. Permissions et Sécurité

### 9.1 Modèle de Permissions

**3 niveaux** :

1. **Auto-allowed** : Liste blanche dans `settings.local.json` → exécution immédiate
2. **Prompted** : Permission demandée à l'exécution (interactif)
3. **Forbidden** : Pas dans allow-list → bloqué

### 9.2 Types d'actions

- `Bash(commande)` : Commandes shell
- `Edit(file_path)` : Modification de fichiers
- `Write(file_path)` : Création de fichiers
- `Read(file_path)` : Lecture fichiers
- `Skill(skill-name)` : Invocation skill
- `mcp__server__tool` : Outils MCP
- `WebSearch` : Recherche web
- `WebFetch(url)` : Fetch URL

### 9.3 Patterns dans allow-list

Supporte les wildcards :

```json
"Bash(npm show:*)"
"Bash(python -c \"...\")"
"WebFetch(domain:github.com)"
```

Cela permet de **pré-autoriser** des familles de commandes.

### 9.4 Dangerous Mode

Certains outils sont considérés **dangereux** (ex: `Bash`). Par défaut, ils demandent permission.

`skipDangerousModePermissionPrompt: true` dans settings.json désactive le prompt pour les permissions déjà dans allow-list.

---

## 10. Intégration MCP (Model Context Protocol)

### 10.1 Qu'est-ce que MCP ?

MCP permet à Claude Code de **se connecter à des serveurs externes** qui exposent des tools (fonctions). C'est un protocole standard (JSON-RPC over stdio/SSE/HTTP).

### 10.2 Serveurs MCP courants

- **n8n-mcp** : Accès aux workflows n8n
- **notion-mcp** : Opérations Notion
- **firecrawl-mcp** : Web scraping avancé
- **gmail-mcp**, **github-mcp**, etc.

### 10.3 Authentification MCP

Tokens stockés dans `.credentials.json` :

```json
{
  "mcpOAuth": {
    "serverName|connectionId": {
      "serverName": "notion",
      "serverUrl": "https://mcp.notion.com/mcp",
      "accessToken": "...",
      "refreshToken": "...",
      "expiresAt": timestamp,
      "discoveryState": {...}
    }
  }
}
```

### 10.4 Appel d'un outil MCP

Format du tool call : `mcp__{serverName}__{toolName}` avec arguments.

Example: `mcp__n8n__n8n_list_workflows`

Les serveurs MCP sont configurés dans la config MCP (via commande `/mcp`).

---

## 11. Système de Projects

### 11.1À quoi servent les projects ?

Permettent de définir des **configurations par projet/workspace** :

- Variables d'environnement spécifiques
- Permissions additionnelles
- Context root
- Settings override

### 11.2 Stockage

```
projects/
├── {project-id}/
│   ├── settings.json      # Override settings
│   ├── env.json           # Env vars
│   └── metadata.json      # CWD, last active, etc.
```

**Détection** : Quand Claude Code démarre dans un dossier, il cherche un projet correspondant au chemin (pattern matching sur `cwd`).

---

## 12. Système de Cache et Persistance

### 12.1 Répertoire cache (`~/.claude/cache/`)

Stocke :
- Résultats d'opérations coûteuses
- Artefacts temporaires
- Données Skill (cache de requêtes)
- Calculs intermédiaires

### 12.2 File History (`file-history/`)

Versionning léger des fichiers modifiés par Claude. Permet d'annuler des modifications.

Format : Fichiers nommés par hash ou timestamp, stockés en git-like.

### 12.3 Download (`downloads/`)

Fichiers téléchargés via WebFetch ou autres (PDF, images, etc.).

---

## 13. Historique et Auditing

### 13.1 history.jsonl

Fichier **JSON Lines** contenant tous les messages de toutes les sessions (entrées utilisateur + réponses Claude + tool calls).

Format :
```
{"display":"user prompt","pastedContents":{...},"timestamp":...,"sessionId":"uuid","project":"path"}
{"display":"Claude response","toolCalls":[...],...}
```

**Utilité** :
- Recherche rétrospective
- Replay de session
- Debug et audit

---

## 14. Interface CLI et Slash Commands

### 14.1 Slash Commands Principales

| Commande | Description |
|----------|-------------|
| `/skills` | Liste tous les skills installés |
| `/skill install {name}` | Installer un skill |
| `/skill uninstall {name}` | Désinstaller |
| `/config` | Afficher/modifier configuration |
| `/mcp` | Gérer les serveurs MCP |
| `/agents` | Lister sous-agents disponibles |
| `/status` | Statut session, modèle, contexte |
| `/context` | Afficher contexte chargé (mémoires, etc.) |
| `/clear` | Effacer conversation (keep session) |
| `/login` | Re-auth avec claude.ai |
| `/reload-plugins` | Recharger plugins/skills |
| `/exit` | Quitter session |

### 14.2 Mode Prompt Engineering

Certains prompts sont **interprétés** comme commands spéciales :

- `` `run the tests` `` : Exécute tests (pattern reconnu)
- `` `Lancer le jeu...` `` : Patterns custom

Claude détecte et active des behaviours spécifiques.

---

## 15. Système de Plugins (Plugins Officiels)

### 15.1 Plugins vs Skills

- **Plugins** : Modifient le **comportement du CLI** même (interface, intégration IDE, etc.)
- **Skills** : Modifient le **comportement conversationnel** de Claude

### 15.2 Plugins installés (Matthis)

```
- frontend-design@claude-plugins-official
- firecrawl@claude-plugins-official
- obsidian-visual-skills@axton-obsidian-visual-skills
- n8n-mcp-skills@n8n-mcp-skills
- obsidian@obsidian-skills
- superpowers@claude-plugins-official
- skill-creator@claude-plugins-official
```

Chaque plugin a un `.claude-plugin/` avec `plugin.json`, scripts, assets.

### 15.3 Superpowers Plugin

`superpowers` est un **meta-plugin** qui ajoute des workflows complexes :

- `brainstorming` → Design before implementation
- `writing-plans` → Génération plans détaillés
- `systematic-debugging` → Debug methodique
- `executing-plans` → Exécution steps
- etc.

C'est un framework de **process** encapsulation.

---

## 16. Télémetrie et Diagnostics

### 16.1 Télémetrie

`~/.claude/telemetry/` contient données d'usage anonymisées (optionnel).

### 16.2 Debug Mode

Dossier `debug/` stocke logs debug quand activé.

### 16.3 Shell Snapshots

`shell-snapshots/` : Sauvegarde état shell pour rollback ou audit.

### 16.4 Backups

`backups/` : Sauvegardes automatiques de config, clés, etc.

---

## 17. Intégrations IDE

### 17.1 Répertoire ide/

Contient configuration et bridges pour IDE :

- Intégration VS Code
- Intégration Cursor
- Intégration Windsurf

Permet de recevoir des commands depuis l'IDE (ex: "Claude, review this code").

### 17.2 Mode IDE

Quand lancé depuis un IDE, Claude Code :
- Connaît le projet ouvert
- Peut recevoir selections de code
- Peut opener fichier direct

---

## 18. Gestion des Credentials et OAuth

### 18.1 .credentials.json

Stocke **tokens OAuth** encrypted (ou plain selon OS) :

```json
{
  "claudeAiOauth": {
    "accessToken": "...",
    "refreshToken": "...",
    "expiresAt": timestamp,
    "scopes": [...],
    "subscriptionType": "pro"
  },
  "mcpOAuth": {
    "serverName|connectionId": { ... }
  },
  "organizationUuid": "org-id"
}
```

### 18.2 Rotation automatique

Les tokens sont rafraîchis automatiquement via refresh token avant expiration.

### 18.3 Sécurité

Fichier protégé (permissions 600). Ne pas commit dans git.

---

## 19. Contexte et System Prompt

### 19.1 Comment Claude "sait" quoi faire ?

Au début de chaque conversation, Claude reçoit un **system prompt** qui inclut :

- Instructions générales (être utile, safe, etc.)
- **Mémoires chargées** (depuis MEMORY.md)
- **CLAUDE.md** du workspace (s'il existe)
- **Project settings** (si applicable)
- **Tool definitions** (Bash, Edit, Write, etc.)
- **Active skills** (leurs règles)

### 19.2 CLAUDE.md (Workspace-level)

Fichier dans le workspace racine qui donne des **instructions spécifiques au projet**. Claude le lit automatiquement au démarrage si présent.

**Exemple** : Règles de commit, conventions de code,.style guide.

---

## 20. System Reminder Tags

Pendant la conversation, Claude reçoit des **system-reminder** tags qui injectent du contexte :

```
<system-reminder>
Called the Bash tool with...
</system-reminder>
```

Ces rappels aident Claude à maintenir la conscience des tool calls en cours.

---

## 21. Gestion des Projets (Workspace Projects)

### 21.1 Détection automatique

Claude Code détecte le projet courant en fonction :

- Du `cwd` (current working directory)
- De la présence de fichiers `CLAUDE.md`, `.claude/settings.json` override
- Des patterns définis dans `~/.claude/projects/`

### 21.2 Configuration par projet

```
projects/
└── {projet-id}/
    ├── settings.json      # Override settings globaux
    ├── env.json           # Variables d'env spécifiques
    └── metadata.json      # CWD pattern, last accessed, etc.
```

---

## 22. Task System (Tasks Directory)

```
tasks/
├── {task-id}.json        # Données tâche (subject, status, etc.)
└── ...                   # Un fichier par tâche
```

Les tâches sont créées via `TaskCreate` et stockées en JSON.

---

## 23. Plans Directory

```
plans/
├── {plan-id}.md          # Plan détaillé (markdown)
└── ...                   # Par session/projet
```

Les plans sont générés avec `EnterPlanMode` et validés via `ExitPlanMode`.

---

## 24. Agents et Subagents

### 24.1 Qu'est-ce qu'un agent ?

Un **agent** est un sous-Claude spécialisé dans une tâche. Il a :

- Son propre **system prompt**
- Ses propres **allowed tools**
- Sa propre **session** isolée

### 24.2 Invocation via Agent Tool

```python
Agent(
  subagent_type="Explore",
  prompt="Search codebase for...",
  isolation="worktree"
)
```

### 24.3 Agents prédéfinis

- `Explore` : Exploration codebase (chercher fichiers, grep)
- `Plan` : Architecture & design
- `general-purpose` : Multi-usage
- Agents custom (définis par skills)

---

## 25. Billing and Model Routing

### 25.1 Billing Header

Dans les requests, un header `x-anthropic-billing-header` est envoyé :

```
cc_version=2.1.92.efa; cc_entrypoint=cli; cch=19365;
```

Permet tracking usage et analytics côté Anthropic.

### 25.2 Model Selection

Claude Code utilise le **modèle le plus récent** par défaut (Claude Opus 4.6 en fast mode). Peut être override par flag ou config.

---

## 26. Outils Disponibles (Tool Registry)

### 26.1 Liste exhaustive

| Tool | Catégorie | Description |
|------|-----------|-------------|
| `Read` | File I/O | Lire fichier (avec offset/limit) |
| `Write` | File I/O | Écrire/overwrite fichier |
| `Edit` | File I/O | Remplacer string dans fichier |
| `Glob` | File I/O | Pattern matching fichiers |
| `Grep` | File I/O | Recherche texte/Regex |
| `Bash` | Exécution | Commande shell (avec timeout) |
| `TaskCreate` | Gestion | Créer tâche |
| `TaskList` | Gestion | Lister tâches |
| `TaskUpdate` | Gestion | Update tâche |
| `TaskGet` | Gestion | Détail tâche |
| `EnterPlanMode` | Plan | Entrer mode plan |
| `ExitPlanMode` | Plan | Sortir mode plan (approuver) |
| `EnterWorktree` | Isolation | Créer worktree git |
| `ExitWorktree` | Isolation | Quitter worktree |
| `Agent` | Agent | Lancer sous-agent |
| `AskUserQuestion` | Interaction | Poser question interactive |
| `Skill` | Extensibilité | Exécuter skill |
| `RemoteTrigger` | Cron | Triggers distants |
| `CronCreate` | Scheduling | Planifier cron job |
| `CronDelete` | Scheduling | Supprimer cron |
| `CronList` | Scheduling | Lister crons |
| `WebFetch` | Web | Fetch URL (avec rendering) |
| `WebSearch` | Web | Recherche web (Firecrawl) |
| `mcp__*` | MCP | Outils MCP (varies) |

### 26.2 Auto-allowed vs Prompted

Défini dans `settings.local.json` → `permissions.allow`. Tout ce qui n'y est pas demande permission utilisateur.

---

## 27. Système de Cron / Scheduling

### 27.1 CronCreate

Planifie un prompt à exécuter selon une cron expression.

```python
CronCreate(
  cron="0 9 * * *",
  prompt="Remind me to...",
  recurring=true
)
```

### 27.2 Stockage

Jobs stockés **en mémoire only** (session-based). Pas de persistence disque (contrairement à tasks).

Expire après 7 jours pour recurring jobs.

---

## 28. Shell Integration

### 28.1 Pipeline Claude

Claude Code peut être utilisé en **pipeline** :

```bash
echo "message" | claude
claude "prompt"
claude < file.txt
```

### 28.2 Mode interactif

Lance REPL avec prompts interactifs, tool calls inline.

---

## 29. Security Model

### 29.1 Sandboxing

Par défaut, les commandes Bash s'exécutent **sans sandbox** (confiance utilisateur). Option `dangerouslyDisableSandbox` pour override.

### 29.2 Fileystem Access

- Read/Write : Accès complet sauf restrictions MCP/permissions
- Respecte les .gitignore? Non par défaut (configurable)
- Peut écrire où l'user peut écrire

### 29.3 Bloclist

`plugins/blocklist.json` liste les plugins malveillants découverts. Empêche leur chargement.

---

## 30. Développement de Skills Custom

### 30.1 Scaffolding

Utiliser `/skill-creator` pour générer skeleton :

```
skill-creator/
└── {skill-name}/
    ├── SKILL.md
    ├── scripts/
    │   └── main.py
    ├── data/ (optionnel)
    └── agents/ (optionnel)
```

### 30.2 Deployment

- Copier dans `~/.claude/skills/`
- Ou créer marketplace custom
- Recharger via `/reload-plugins`

### 30.3 Testing

Exécuter script directement en CLI pour tester indépendamment de Claude.

---

## 31. Points d'Attention et Limitations

### 31.1 Token Context

Claude Code a une **fenêtre de contexte limitée** (128K-200K tokens selon modèle). Les mémoires sont résumées si trop longues.

### 31.2 Statefulness

Sessions sont **stateless** sauf :
- Tâches (en mémoire session)
- Mémoires (sur disque)
- Projects config (sur disque)

### 31.3 Concurrency

Claude Code n'est pas thread-safe. Une seule instance par workspace recommandée.

### 31.4 Platform Differences

Chemin Windows vs Unix (`/c/Users/` vs `/home/`). Claude normalise.

---

## 32. Références Internes (Liens utiles)

### 32.1 Fichiers système clés

- `~/.claude/settings.json`
- `~/.claude/settings.local.json`
- `~/.claude/.credentials.json`
- `~/.claude/history.jsonl`
- `~/.claude/tasks/`
- `~/.claude/plans/`
- `~/.claude/skills/{skill}/SKILL.md`
- `~/.claude/plugins/installed_plugins.json`

### 32.2 Workspace Files

- `CLAUDE.md` : Instructions projet
- `MEMORY.md` : Index mémoires
- `memory/` : Dossier mémoires ( fichiers individuels)

### 32.3 Commandes utiles

```bash
# Recharger config
claude --reload

# Voir config active
/config

# Lister skills
/skills

# Gérer MCP
/mcp

# Debug session
/status
/context
```

---

## 33. Glossaire

| Terme | Définition |
|-------|------------|
| **Skill** | Extension qui modifie comportement conversationnel |
| **Plugin** | Extension qui modifie le CLI lui-même |
| **MCP** | Model Context Protocol (outils externes) |
| **Worktree** | Branche git isolée pour expérimentation |
| **Plan Mode** | Mode design → validation avant implémentation |
| **Task** | Unité de travail suivi dans la session |
| **Session** | Conversation ouverte (UUID) |
| **Project** | Configuration par workspace/racine |
| **Memory** | Fichier persistant (user/feedback/project/reference) |
| **Hook** | Automation déclenchée sur événement |
| **Superpowers** | Meta-plugin avec workflows complexes |
| **Permission** | Action autorisée ou demandée |
| **Allow-list** | Liste blanche dans `settings.local.json` |

---

## 34. Workflows Typiques

### 34.1 Créer une fonctionnalité

```
1. /brainstorming → explore requirements
2. Présenter design → approbation user
3. /writing-plans → générer plan détaillé
4. EnterPlanMode → valider plan
5. ExitPlanMode (approuvé)
6. Implémentation avec TaskCreate/TaskUpdate
7. Commit, tests
```

### 34.2 Debugger un problème

```
1. /systematic-debugging (si skill installé)
2. Isoler problème → créer tâche
3. Explorer avec Agent(Explore)
4. Tester hypothèses
5. Fix → Write/Edit
6. Run tests (Bash)
```

### 34.3 Recherche web + synthèse

```
1. WebSearch query
2. WebFetch résultats pertinents
3. Brainstorming → analyse
4. Write rapport (Write .md)
```

---

## 35. Points Avancés

### 35.1 Custom Agent Types

Créer agent custom dans `skills/{skill}/agents/` avec `AGENT.md` definissant :

- System prompt
- Allowed tools
- Prompt examples

### 35.2 Tool Composition

Les tools peuvent s'invoquer mutuellement (Agent appelle Skill qui appelle Bash...). Attention à la récursion.

### 35.3 Model Context Protocol Avancé

Écrire son propre serveur MCP (Node.js/Python) qui expose outils JSON-RPC. Config client dans Claude Code.

### 35.4 Session Restoration

`history.jsonl` permet de restore une conversation précédente (outil externe ou manual).

---

## 36. Évolution et Roadmap

Claude Code évolue rapidement. Points d'attention :

- **Model** : Passage à Claude 4.x,支持 nouveaux models
- **Skills** : Marketplace croissante
- **MCP** : Standardisation, plus de serveurs
- **IDE** : Intégration plus profonde
- **Security** : Sandboxing amélioré, audit logs

---

## 37. Références Externes (Sources)

1. [Documentation officielle Claude Code](https://docs.claude.com)
2. [GitHub: anthropics/claude-code](https://github.com/anthropics/claude-code)
3. [Model Context Protocol Spec](https://modelcontextprotocol.io)
4. [Skills Marketplace](https://skills.claude.com)
5. [Claude AI API](https://console.anthropic.com)

---

## 38. Comparaison des Composants

| Composant | Stockage | Scope | Modifiable user ? |
|-----------|----------|-------|-------------------|
| settings.json | ~/.claude/ | Global | Oui |
| settings.local.json | ~/.claude/ | Local machine | Oui |
| skills/ | ~/.claude/skills/ | Extensions | Oui (ajouter, custom) |
| plugins/ | ~/.claude/plugins/ | CLI extensions | Via marketplace |
| MEMORY.md | Workspace | Index mémoires | Oui (éditer) |
| memory/*.md | Workspace/memory/ | Mémoires user | Oui (auto par Claude) |
| tasks/ | ~/.claude/tasks/ | Tâches session | Auto |
| plans/ | ~/.claude/plans/ | Plans | Auto/generated |
| sessions/ | ~/.claude/sessions/ | Conversations | Auto |
| history.jsonl | ~/.claude/ | Historique global | Non (append-only) |
| CLAUDE.md | Workspace root | Instructions projet | Oui |
| projects/ | ~/.claude/projects/ | Config projets | Modifié par Claude |

---

## 39. Concepts Avancés

### 39.1 Context Engineering

Claude Code ingère contexte depuis :

1. System prompt (built-in)
2. CLAUDE.md (workspace)
3. Mémoires (MEMORY.md + files)
4. Tools definitions
5. Active skills
6. Project config
7. Fichiers lus dans la conversation (par Read)

L'**order of precedence** : conversation > mémoires > CLAUDE.md > system prompt.

### 39.2 Prompt Injection Protection

Claude Code détecte les tentatives d'injection dans les system-reminder tags et les neutralise.

### 39.3 Multi-agent Orchestration

L'outil `Agent` permet de lancer plusieurs agents en parallèle, chaque agent a son contexte isolé. Parent peut distribuer tâches.

---

## 40. Debug et Troubleshooting

### 40.1 Logs

- `~/.claude/debug/` : Logs debug si activé (flag `--debug`)
- Console stderr : erreurs out-of-band
- `history.jsonl` : replay complet conversation

### 40.2 Permissions Denied

Si tool call échoue avec permission error :

1. Vérifier `settings.local.json` → `permissions.allow`
2. Ajouter pattern si nécessaire
3. Reload avec `/reload-plugins`

### 40.3 Skill ne se lance pas

1. Vérifier présent dans `~/.claude/skills/`
2. Vérifier `SKILL.md` valide (YAML frontmatter)
3. `/reload-plugins`
4. Vérifier logs `~/.claude/plugins/cache/`

---

## 41. Futur et Directions

### 41.1 Standardization

- MCP comme standard (outils interopérables)
- Skills packaging (npm/pypi style)
- IDE integrations uniformes

### 41.2 Enterprise Features

- Audit trails complets
- SSO intégration
- RBAC (Role-Based Access Control)
- Policy as Code (rules réversibles)

### 41.3 Intelligence

- Auto-optimisation permissions
- Self-healing (réparation config)
- Predictive task generation
- Cross-session learning

---

## 42. Conclusion

Claude Code est **beaucoup plus qu'un chatbot terminal**. C'est un **système d'assistant IA complet** avec :

✅ Gestion avancée de contexte (mémoires, projets)
✅ Extensibilité illimitée (skills, plugins, MCP)
✅ Sécurité modelée (permissions, allow-list)
✅ Persistance (tasks, plans, sessions)
✅ Intégration IDE et workspace
✅ Automatisation (hooks, cron)

Comprendre son architecture permet d'**exploiter pleinement son potentiel** et de customiser à ses workflows.

---

## Références

> Exhaustif à la date de rédaction (2025-04-04). L'architecture peut évoluer avec les versions.

---

## Liens

- [[3_GARDEN/Notes permanentes/Claude code|Claude code]] : Note générale d'introduction
- [[3_GARDEN/Notes permanentes/Claude skills|Claude skills]] : Détail des skills installés chez Matthis
- [[3_GARDEN/Notes permanentes/Claude Agent Teams|Claude Agent Teams]] : Système d'agents multiples
- [[3_GARDEN/Notes permanentes/Claude x Ollama|Claude x Ollama]] : Intégration modèles locaux
- [[3_GARDEN/MOCs/IA|IA]] : MOC Intelligence Artificielle
- [[3_GARDEN/MOCs/INFORMATIQUE|INFORMATIQUE]] : MOC Informatique générale
