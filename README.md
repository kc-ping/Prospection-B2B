# 🚀 Pipeline de Veille et Prospection B2B Automatisée

> Système intelligent d'extraction de signaux d'affaires industriels, de qualification par IA (Perplexity & LLM) et de synchronisation multi-canal (Google Sheets & Gmail).

---

## 📌 Présentation du Projet
Ce projet implémente un workflow d'automatisation complet sous **n8n** conçu pour optimiser la prospection commerciale dans les secteurs de l'industrie, de la maintenance, de l'automatisme et de l'ingénierie. 

Il permet d'identifier de manière autonome des signaux d'investissement et de modernisation d'usines en France, de filtrer les faux positifs, d'enregistrer les opportunités dans un CRM (Google Sheets) sans doublon, et de déclencher des alertes ciblées avec des brouillons d'e-mails rédigés par l'IA.

---

## ⚙️ Architecture & Fonctionnement du Workflow

Le pipeline s'articule autour des étapes clés suivantes :
1. **Extraction Web (Apify & Google Search Scraper) :** Requêtage automatisé de signaux industriels publics ciblés.
2. **Scoring & Qualification Heuristique :** Filtrage initial basé sur des mots-clés sectoriels (industrie, robotique, maintenance).
3. **Analyse de Faits (Perplexity API) :** Vérification croisée des sources et confirmation de l'existence des projets industriels.
4. **Génération de Brouillons (LLM / OpenAI) :** Rédaction de messages commerciaux contextualisés et ancrés sur des preuves vérifiables.
5. **Dédoublonnage Intelligent & Sécurisation (JavaScript) :** Comparaison en amont avec l'historique Google Sheets pour bloquer les doublons et ne traiter que les *vrais* nouveaux prospects.
6. **Actions Finales :**
   - **Enregistrement base de données :** Mise à jour/Ajout propre via une stratégie *Upsert* dans Google Sheets[cite: 10, 16].
   - **Alerte Commerciale :** Envoi d'un e-mail formaté via l'API Gmail uniquement pour les prospects de **Priorité A**[cite: 10, 16].

---

## 🛠️ Stack Technique
* **Orchestration :** n8n (v1.x)
* **Scraping & Web Fetch :** Apify (Google Search Scraper)[cite: 10, 16]
* **Intelligence Artificielle :** Perplexity API (Fast-Search) & OpenAI GPT[cite: 10, 16]
* **Stockage :** Google Sheets API (Mode *appendOrUpdate*)[cite: 10, 16]
* **Communication :** Gmail API (Alertes de classe A)[cite: 10, 16]
* **Langage de script :** JavaScript (pour la logique de filtrage et de normalisation)[cite: 10, 16]

---

## 📂 Structure du Dépôt
```text
├── workflow.json              # Le code source exporté du workflow n8n
├── workflow.png               # Image du workflow n8n
├── README.md                  # Documentation du projet
└── ARCHITECTURE.md            # Spécifications techniques et flux de données
