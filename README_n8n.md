# 🤖 Assistant de Veille Automatique — IA

> Workflow n8n qui surveille l'actualité IA en temps réel, résume chaque article avec GPT-4o-mini et l'enregistre automatiquement dans Notion.

---

## ⚙️ Comment ça marche ?

```
RSS TechCrunch AI  →  GPT-4o-mini  →  Notion Database
  (chaque minute)     (résumé 3 points)   (sauvegarde auto)
```

**Étape 1 — RSS Feed** : récupère les derniers articles de TechCrunch AI toutes les minutes  
**Étape 2 — OpenAI** : résume chaque article en 3 bullet points clairs avec `gpt-4o-mini`  
**Étape 3 — Notion** : crée une page dans ta base de données avec le titre, l'URL, la date et le résumé  

---

## 🛠️ Stack

![n8n](https://img.shields.io/badge/n8n-EA4B71?style=for-the-badge&logo=n8n&logoColor=white)
![OpenAI](https://img.shields.io/badge/GPT--4o--mini-412991?style=for-the-badge&logo=openai&logoColor=white)
![Notion](https://img.shields.io/badge/Notion-000000?style=for-the-badge&logo=notion&logoColor=white)

---

## 🚀 Installation

### Prérequis
- Un compte [n8n](https://n8n.io) (cloud ou self-hosted)
- Une clé API [OpenAI](https://platform.openai.com)
- Un compte [Notion](https://notion.so) avec une base de données

### 1. Importer le workflow
1. Télécharge le fichier `workflow.json`
2. Dans n8n → **"Add workflow"** → **"Import from file"**
3. Sélectionne le fichier JSON

### 2. Configurer les credentials
| Service | Ce qu'il faut |
|---------|--------------|
| **OpenAI** | Clé API → `Settings > API Keys` |
| **Notion** | Integration Token → `notion.so/my-integrations` |

### 3. Configurer Notion
1. Crée une base de données Notion avec ces propriétés :
   - `Name` (Title)
   - `URL` (URL)
   - `Date` (Date)
2. Connecte ton integration à la base de données *(Share → Invite)*
3. Remplace l'ID de la database dans le node Notion

### 4. Activer le workflow
- Clique sur le toggle **"Active"** en haut à droite dans n8n ✅

---

## 📋 Structure Notion générée

| Titre de l'article | URL | Date de publication |
|--------------------|-----|-------------------|
| AI breakthrough... | techcrunch.com/... | 2025-04-16 |

> Le résumé en 3 points est ajouté dans le corps de la page Notion.

---

## 🔧 Personnalisation

- **Changer la source RSS** : remplace l'URL dans le node `RSS Feed` par n'importe quel flux RSS (ex: TheVerge, MIT Tech Review...)
- **Changer la fréquence** : modifie le `pollTimes` dans le node RSS (toutes les heures, tous les jours...)
- **Changer le prompt** : modifie le message dans le node OpenAI pour adapter le style du résumé

---

## 📌 Idées d'améliorations futures

- [ ] Ajouter un filtre par mots-clés (ex: seulement les articles sur les LLMs)
- [ ] Envoyer un digest quotidien par email ou Discord
- [ ] Scorer la pertinence de chaque article avec l'IA
- [ ] Support multi-sources RSS

---

*Projet réalisé dans le cadre de mon apprentissage de l'automatisation et des agents IA.*
