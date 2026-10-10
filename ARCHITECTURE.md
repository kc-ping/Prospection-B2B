# 🏛️ Architecture Technique — Pipeline de Prospection B2B (DV GROUP)

Ce document décrit l'architecture logicielle, le flux de données (*data pipeline*) et les choix de conception du système d'automatisation n8n.

---

## 1. Vue d'ensemble de l'Architecture

Le système repose sur un pipeline orienté événements et flux de données asynchrones. Il combine des services de web scraping, de recherche augmentée par IA, un filtrage contextuel et une synchronisation transactionnelle avec un CRM (Google Sheets) et un service de messagerie (Gmail).

```text
[Déclencheur Manuel / Cron]
       │
       ▼
[Extraction Apify (Google Search Scraper)]
       │
       ▼
[Scoring & Qualification Heuristique]
       │
       ▼
[Enrichissement Web Fetch & Perplexity AI]
       │
       ▼
[Génération de Brouillons (LLM)]
       │
       ▼
[Contrôle d'Historique (Google Sheets API)]
       │
       ▼
[Moteur de Dédoublonnage & Filtrage (JavaScript)] ──► (Bloque les doublons)
       │
       ├────────────────────────────────────────┐
       ▼                                        ▼
[Upsert Google Sheets]            [Filtrage Priorité A] ──► [Alerte Gmail]