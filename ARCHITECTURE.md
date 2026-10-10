flowchart TD
    A([⏱️ Déclencheur Manuel / Cron]) --> B[🌐 Extraction Apify <br> <i>Google Search Scraper</i>]
    B --> C{⚖️ Scoring & Qualification <br> Heuristique}
    C --> D[🧠 Enrichissement <br> <i>Web Fetch & Perplexity AI</i>]
    D --> E[✍️ Génération de Brouillons <br> <i>LLM</i>]
    E --> F[(📊 Contrôle d'Historique <br> <i>Google Sheets API</i>)]
    F --> G{🛡️ Moteur de Dédoublonnage <br> & Filtrage JavaScript}

    G -- "🛑 Doublons bloqués" --> Z((Rejet))
    G -- "✅ Nouveaux prospects" --> H[(💾 Upsert <br> Google Sheets)]
    G -- "✅ Nouveaux prospects" --> I{🎯 Filtrage <br> Priorité A}
    
    I -- "Oui" --> J[📧 Alerte Gmail]
    I -- "Non" --> K((Fin))

    %% Styles personnalisés pour rendre le schéma professionnel
    classDef default fill:#f8fafc,stroke:#cbd5e1,stroke-width:2px,color:#0f172a,rx:5px,ry:5px;
    classDef database fill:#ecfdf5,stroke:#10b981,stroke-width:2px,color:#064e3b;
    classDef ai fill:#f3e8ff,stroke:#a855f7,stroke-width:2px,color:#3b0764;
    classDef logic fill:#fff7ed,stroke:#f97316,stroke-width:2px,color:#7c2d12;
    classDef mail fill:#fef2f2,stroke:#ef4444,stroke-width:2px,color:#7f1d1d;
    
    class F,H database;
    class D,E ai;
    class C,G,I logic;
    class J mail;