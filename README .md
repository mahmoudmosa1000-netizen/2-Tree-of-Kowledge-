# 🌳 Tree of Knowledge — Next.js

**Philosophie als lebendiges Universum** | Next.js 14 · TypeScript · PostgreSQL · Ollama

---

## Schnellstart

```bash
# 1. Abhängigkeiten
npm install

# 2. Umgebungsvariablen
cp .env.example .env.local
# DATABASE_URL in .env.local anpassen

# 3. Datenbank aufsetzen
npm run db:push
npm run db:seed

# 4. Ollama starten (für KI-Antworten)
ollama pull llama3
OLLAMA_ORIGINS=* ollama serve

# 5. Entwicklungsserver
npm run dev
# → http://localhost:3000
```

---

## Architektur

```
src/
├── app/
│   ├── layout.tsx               Root Layout (Fonts, Metadata)
│   ├── page.tsx                 Hauptseite (Tree + Views)
│   └── api/
│       ├── philosophers/        REST API: Philosophen aus DB
│       └── ai/                  Ollama-Proxy (löst CORS/Mixed-Content)
├── components/
│   ├── Tree/TreeSVG.tsx         🌳 Baum mit Blättern (SVG + Canvas)
│   ├── Views/
│   │   ├── MindMapView.tsx      🕸 Einfluss-Netzwerk
│   │   └── TimelineView.tsx     📅 Chronologische Liste
│   ├── Sidebar/
│   │   ├── Sidebar.tsx          Philosophen-Detail-Panel
│   │   └── AIChat.tsx           💬 Streaming KI-Dialog
│   └── UI/
│       ├── Header.tsx           Navigation, Sprache, Controls
│       └── OllamaModal.tsx      ⚙ Ollama-Konfiguration
├── lib/
│   ├── db.ts                    Prisma Singleton
│   └── ollama.ts                Ollama Client + System-Prompts
├── stores/
│   └── treeStore.ts             Zustand (globaler State + Persistenz)
└── types/
    └── index.ts                 TypeScript-Typen

prisma/
├── schema.prisma                DB-Schema (20+ Modelle)
└── seed.ts                      Alle 20 Philosophen als Seed
```

---

## Features

| Feature | Status |
|---------|--------|
| 🌳 Baum mit Blättern (SVG) | ✅ |
| 🍎 20 Philosopher-Nodes | ✅ |
| 🕸 Mind Map mit Pfeilen | ✅ |
| 📅 Chronologische Timeline | ✅ |
| 🦙 Ollama lokale KI + Streaming | ✅ |
| 🌍 DE / EN / عر (RTL) | ✅ |
| ⬡ Partikel-Animation | ✅ |
| ★ Favoriten (persistent) | ✅ |
| 🗄️ PostgreSQL + Prisma | ✅ |
| 🚀 Vercel-ready | ✅ |

---

## Deployment (Vercel + Supabase)

```bash
# 1. Supabase Projekt anlegen → Connection String kopieren
# 2. GitHub Repo erstellen und pushen
# 3. Vercel mit GitHub verbinden
# 4. Environment Variables setzen:
#    DATABASE_URL    = supabase connection string
#    OLLAMA_URL      = https://dein-ollama-server.com (oder weglassen)
#    NEXTAUTH_SECRET = random-32-char-string
# 5. Deploy!
```

---

## Nächste Schritte

- [ ] **Automatischer Scraper** — Wikipedia/Wikidata → neue Philosophen auto-hinzufügen
- [ ] **Three.js 3D-Modus** — Baum in echter 3D-Perspektive mit Rotation
- [ ] **Benutzer-System** — NextAuth, Notizen, Lernfortschritt
- [ ] **Knowledge Galaxy** — Alle Ideen als 3D-Sternenhimmel
- [ ] **Mobile App** — React Native mit demselben Store