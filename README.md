# 🎵 Canta-me

> **Trasforma le tue parole in una canzone.**
> Transforme tes mots en musique avec l'IA.

**Canta-me** est une plateforme web qui permet à n'importe qui de créer une chanson personnalisée à partir d'un texte, d'une histoire ou d'un message. Choisis ton style musical, ta voix, et l'IA génère une chanson unique en quelques minutes.

👉 **[canta-me.com](https://canta-me.com)**

---

## 📸 Aperçu

| Landing Page | Création | Dashboard |
|---|---|---|
| Landing multilingue avec Hero, exemples, pricing, FAQ | Assistant de création pas-à-pas (occasion → histoire → style → voix → résultat) | Dashboard personnel avec gestion des chansons, crédits, facturation |

---

## ✨ Fonctionnalités

### 🎤 Création de chansons
- **Assistant guidé** en 8 étapes : occasion, histoire, style musical, voix, checkout, génération, résultat
- **20+ styles musicaux** : Afrobeat, Amapiano, Coupé-Décalé, R&B, Rap, Acoustic, Gospel, Reggae, Kompa, Salsa, Zouk, Zouglou, Nigerian Music, Arabic, et plus encore
- **3 types de voix** : masculine, féminine, duo
- **Paroles générées par IA** (Google Gemini) ou personnalisées par l'utilisateur
- **Lecture audio** intégrée avec lecteur personnalisé

### 👤 Compte utilisateur
- **Authentification** complète : inscription, connexion, mot de passe oublié
- **Onboarding** en 5 étapes (profil, raison, style, découverte, finalisation)
- **Dashboard** personnel : liste des chansons, crédits, historique, facturation
- **Profil** modifiable

### 💰 Système de crédits (Note)
- **Monnaie interne** : les "Note" (1 chanson = 2 Note)
- **Packs d'achat** : Découverte (4 Note — 3,20 €), Popolare (10 Note — 5,47 €), Premium (24 Note — 15,99 €)
- **Historique** complet des transactions
- **Codes promo** supportés
- **Offres de bienvenue** après inscription (durée configurable)

### 🔗 Partage
- Chaque chanson génère un **lien public unique** (`/song/[slug]`)
- Partage sur les réseaux sociaux
- Page publique avec lecteur et métadonnées Open Graph

### 🛡️ Admin
- **Dashboard admin** avec statistiques
- Gestion des **utilisateurs**
- Suivi des **générations** avec statuts et coûts
- **Rapports** utilisateur
- Suivi des **coûts** de génération
- Gestion de la **facturation**

### 🎨 Interface
- **Design responsive** (mobile, tablette, desktop)
- **Thème clair/sombre** automatique
- **Animations** fluides et micro-interactions
- Composants **shadcn/ui** avec thème personnalisé chaud (ambre/violet)
- Pages d'atterrissage par cas d'usage : Amore, Compleanno, Matrimonio, Regalo

---

## 🧱 Stack Technique

| Domaine | Technologie |
|---|---|
| **Framework** | [Next.js 16](https://nextjs.org/) (App Router, React 19, RSC) |
| **Langage** | TypeScript 5 |
| **Styling** | [Tailwind CSS v4](https://tailwindcss.com/) + [shadcn/ui](https://ui.shadcn.com/) |
| **UI Components** | Radix UI (via shadcn), Lucide Icons |
| **Base de données** | [Supabase](https://supabase.com/) (PostgreSQL) |
| **Authentification** | Supabase Auth (email/mot de passe) |
| **IA / Lyrics** | [Google Gemini](https://ai.google.dev/) |
| **Génération musicale** | Lyria / API musicale interne |
| **Paiements** | [Whop](https://whop.com/) |
| **Formulaires** | React Hook Form + Zod |
| **Thème** | next-themes |
| **Notifications** | Sonner (toasts) |
| **Tests** | [Vitest](https://vitest.dev/) |
| **Linting** | ESLint 9 |

---

## 📁 Structure du projet

```
canta-me/
├── app/                          # App Router Next.js
│   ├── (public)/                 # Routes publiques
│   │   ├── song/[slug]/          # Page publique d'une chanson
│   │   └── layout.tsx
│   ├── (protected)/              # Routes authentifiées
│   │   ├── dashboard/            # Dashboard, crédits, historique, facturation
│   │   ├── creer/                # Assistant de création pas-à-pas
│   │   ├── create/               # Création rapide
│   │   ├── songs/                # Liste + détail des chansons
│   │   ├── profile/              # Profil utilisateur
│   │   └── layout.tsx
│   ├── (admin)/admin/            # Panel administrateur
│   ├── api/                      # Routes API
│   │   ├── music/                # Génération + statut
│   │   ├── billing/              # Checkout, abonnement, promo
│   │   ├── webhooks/             # Webhooks Whop
│   │   ├── notes/                # Offres de crédit
│   │   ├── song/report/          # Signalement
│   │   ├── onboarding/           # Flow onboarding
│   │   ├── og/song/[slug]/       # Génération d'images OG
│   │   └── creation-session/     # Sessions de création
│   ├── login/                    # Connexion
│   ├── register/                 # Inscription
│   ├── forgot-password/          # Mot de passe oublié
│   ├── onboarding/               # Onboarding post-inscription
│   ├── come-funziona/            # Page "Comment ça marche"
│   ├── amore/                    # Landing "Amore"
│   ├── compleanno/               # Landing "Compleanno"
│   ├── matrimonio/               # Landing "Matrimonio"
│   ├── idee/                     # Idées cadeaux
│   ├── regalo/                   # Cadeaux
│   ├── prezzi/                   # Tarifs
│   ├── faq/                      # FAQ
│   ├── providers.tsx             # Providers (thème, tooltips, toasts)
│   └── layout.tsx                # Layout racine
├── components/
│   ├── ui/                       # Composants shadcn/ui
│   ├── landing/                  # Sections de la landing page
│   ├── layout/                   # App shell (sidebar, header, mobile)
│   ├── creer/                    # Étapes de l'assistant de création
│   ├── create-song/              # Éditeur de paroles, progression
│   ├── onboarding/               # Étapes onboarding
│   ├── song/                     # Partage, signalement
│   ├── music/                    # Lecteur, sélecteurs (style, voix, mood)
│   ├── songs/                    # Cartes de chansons, badges
│   └── notes/                    # Offres de crédits, packs, promos
├── lib/
│   ├── config/                   # Configuration centralisée
│   │   ├── index.ts              # Crédits, limites, packs Note
│   │   └── creer-config.ts       # Occasions, voix, styles de l'assistant
│   ├── services/
│   │   ├── music/                # Génération musicale
│   │   │   ├── music-generation-service.ts
│   │   │   ├── lyria-provider.ts
│   │   │   ├── music-api-provider.ts
│   │   │   ├── song-config-validator.ts
│   │   │   ├── music-prompt-builder.ts
│   │   │   └── music-api-mapper.ts
│   │   ├── lyrics/               # Génération de paroles (Gemini)
│   │   ├── billing/              # Facturation (Whop)
│   │   ├── credit-service.ts     # Gestion des crédits/Note
│   │   └── music-generation.ts   # Service de génération
│   ├── supabase/                 # Clients Supabase (server, client, middleware)
│   ├── constants/music.ts        # Constantes musicales
│   ├── utils.ts                  # Utilitaires généraux
│   ├── analytics.ts              # Analytics
│   └── gemini.ts                 # Client Google Gemini
├── supabase/
│   └── migrations/               # Migrations SQL
├── hooks/
│   └── use-note-balance.ts       # Hook React pour le solde de Note
├── types/
│   └── index.ts                  # Types globaux TypeScript
├── __tests__/                    # Tests Vitest
├── scripts/                      # Scripts utilitaires
└── skills-lock.json              # Verrouillage de skills
```

---

## 🚀 Démarrage rapide

### Prérequis

- **Node.js** ≥ 20
- **npm** ≥ 10
- Un projet **[Supabase](https://supabase.com/)** configuré
- Une clé API **[Google Gemini](https://aistudio.google.com/apikey)**
- Un compte **[Whop](https://whop.com/)** (pour les paiements)

### Installation

```bash
# 1. Cloner le projet
git clone https://github.com/lph2o/Canta-me.git
cd Canta-me

# 2. Installer les dépendances
npm install

# 3. Copier et remplir les variables d'environnement
cp .env.example .env.local
# Remplir .env.local avec tes clés (voir ci-dessous)
```

### Variables d'environnement

```bash
# ── Supabase ──
NEXT_PUBLIC_SUPABASE_URL=https://xxxxx.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=eyJ...
SUPABASE_SERVICE_ROLE_KEY=eyJ...

# ── Base URL ──
NEXT_PUBLIC_BASE_URL=http://localhost:3000

# ── Google Gemini ──
GEMINI_API_KEY=AIza...

# ── Whop (paiements) ──
WHOP_API_KEY=...
WHOP_WEBHOOK_SECRET=...
WHOP_NOTES_4_PRODUCT_ID=...
WHOP_NOTES_10_PRODUCT_ID=...
WHOP_NOTES_24_PRODUCT_ID=...

# ── Génération Musicale ──
MUSIC_API_URL=...
MUSIC_API_KEY=...

# ── Config (valeurs par défaut) ──
# INITIAL_CREDITS=0
# MAX_LYRICS_LENGTH=5000
# MAX_GENERATIONS_PER_DAY=20
```

### Lancer le projet

```bash
# Développement (Turbopack)
npm run dev

# Build production
npm run build

# Lancer la version production
npm run start

# Lint
npm run lint
```

Ouvrir [http://localhost:3000](http://localhost:3000).

---

## 🗄️ Base de données

Les migrations Supabase se trouvent dans `supabase/migrations/`. Elles sont numérotées dans l'ordre d'exécution :

| Migration | Contenu |
|---|---|
| `001_initial_schema.sql` | Tables principales : users, profiles, credits, songs |
| `002_music_provider.sql` | Générations musicales et jobs |
| `003_creation_sessions.sql` | Sessions de création (wizard /creer) |
| `003_credits_ledger.sql` | Ledger de transactions de crédits |
| `004_whop_billing.sql` | Tables de facturation Whop |
| `005_lyrics_versions.sql` | Versions de paroles |
| `006_sharing.sql` | Slugs de partage public |
| `007_onboarding_notes.sql` | Notes d'onboarding |
| `008_notes_overhaul.sql` | Refonte du système de Note |
| `009_admin_rls_backfill.sql` | RLS pour les administrateurs |

Pour appliquer les migrations :

```bash
npm run migrate
# ou
node run_migrations_api.js
```

---

## 🧪 Tests

```bash
# Lancer les tests
npx vitest run

# Mode watch
npx vitest
```

Les tests sont situés dans `__tests__/` et couvrent :
- Services (mock-provider, song-config-validator, etc.)
- Validations (song.test.ts)
- Utilitaires (song.test.ts, share-slug.test.ts)

---

## 🏗️ Architecture

### Création d'une chanson (flux complet)

1. L'utilisateur démarre l'assistant (`/creer`) ou la création rapide (`/create`)
2. Il choisit l'**occasion**, écrit son **histoire**, sélectionne le **style**, la **voix**
3. Les paroles sont générées via **Google Gemini** (ou écrites manuellement)
4. L'utilisateur vérifie son solde de **Note** et procède au checkout si nécessaire
5. La génération musicale est déclenchée via l'API musicale (Lyria ou autre provider)
6. L'utilisateur suit la **progression** en temps réel (polling du statut)
7. Une fois terminée, la chanson est disponible avec **lecture** et **partage**

### Flux de paiement

1. L'utilisateur choisit un pack de **Note** (4, 10 ou 24)
2. Redirection vers le checkout **Whop**
3. Whop envoie un **webhook** lors du paiement réussi
4. Le service `BillingService` traite le webhook et crédite les Note
5. L'utilisateur voit son nouveau solde immédiatement

### Sécurité

- **Row Level Security (RLS)** activé sur toutes les tables Supabase
- **Middleware Supabase** pour la gestion des sessions
- **Idempotence** sur toutes les transactions de crédits
- **Validation Zod** sur toutes les entrées API
- **Rate limiting** configurable par utilisateur

---

## 🎯 Choix techniques

| Choix | Raison |
|---|---|
| **Next.js App Router** | RSC, streaming, performances optimales |
| **Supabase** | Auth intégrée, RLS, PostgreSQL managé, temps réel |
| **shadcn/ui** | Composants accessibles, personnalisables, copier-coller |
| **Whop** | Gestion des paiements et abonnements simplifiée |
| **Google Gemini** | Génération de paroles multilingues de qualité |
| **Zod** | Validation statique + runtime, inférence TypeScript |
| **Vitest** | Rapide, compatible Vite, natif ESM |

---

## 📝 Licence

Projet privé — Tous droits réservés.

---

## 🤝 Contribuer

Pour contribuer, ouvre une issue ou une pull request sur [GitHub](https://github.com/lph2o/Canta-me).

---

**Canta-me** — *Trasforma le tue emozioni in musica.* 🎶
