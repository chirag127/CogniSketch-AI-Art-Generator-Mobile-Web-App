# CogniSketch AI Art Generator Cross‑Platform App

---

<div align="center">

![Build Status](https://img.shields.io/github/actions/workflow/status/chirag127/CogniSketch-AI-Art-Generator-Cross-Platform-App/ci.yml?branch=main&style=flat-square)
![Coverage](https://img.shields.io/codecov/c/github/chirag127/CogniSketch-AI-Art-Generator-Cross-Platform-App?style=flat-square)
![Tech Stack](https://img.shields.io/badge/Tech%20Stack-TypeScript%20%7C%20React%20Native%20%7C%20Express%20%7C%20Expo-lightgrey?style=flat-square)
![Lint](https://img.shields.io/badge/Lint-Biome-5F5F5F?style=flat-square)
![License](https://img.shields.io/badge/License-CC%20BY--NC%204.0-lightgrey?style=flat-square)
![Stars](https://img.shields.io/github/stars/chirag127/CogniSketch-AI-Art-Generator-Cross-Platform-App?style=flat-square)

[⭐️ Star this repo](https://github.com/chirag127/CogniSketch-AI-Art-Generator-Cross-Platform-App)

</div>

---

## TL;DR
Turn hand‑drawn sketches or photos into AI‑generated artwork (Anime, Watercolor, Oil Paint, etc.) on **mobile** (iOS/Android) and **web** with a single, cross‑platform React‑Native/Expo front‑end and an Express API back‑end.

---

## Architecture Overview
mermaid
graph LR
    subgraph Front‑End
        RN[React‑Native (Expo)] -->|REST calls| API[Express Server]
    end
    subgraph Back‑End
        API -->|Cerebras Inference| AI[OpenAI SDK (Cerebras endpoint)]
    end
    style RN fill:#f9f,stroke:#333,stroke-width:2px
    style API fill:#bbf,stroke:#333,stroke-width:2px
    style AI fill:#bfb,stroke:#333,stroke-width:2px


---

## Table of Contents
- [Installation](#installation)
- [Usage](#usage)
- [Development Standards](#development-standards)
- [Testing](#testing)
- [AI Agent Directives](#ai-agent-directives)
- [Contributing](#contributing)
- [License](#license)

---

## Installation
bash
# Clone the repository
git clone https://github.com/chirag127/CogniSketch-AI-Art-Generator-Cross-Platform-App.git
cd CogniSketch-AI-Art-Generator-Cross-Platform-App

# Install dependencies (uses pnpm for speed)
pnpm install

# Set up environment variables
cp .env.example .env
# Edit .env and add CEREBRAS_API_KEY


---

## Usage
bash
# Start the development server (Expo)
pm run dev
# The app will launch on your connected device or emulator.

# Start the backend locally
npm run server


---

## Development Standards
| Aspect | Guideline |
|--------|-----------|
| **Language** | TypeScript with `strict` mode enabled |
| **Architecture** | Feature‑Sliced Design (FSD) for the front‑end; Hexagonal for the back‑end |
| **Linting / Formatting** | Biome (auto‑fix on commit) |
| **Testing** | Vitest for unit, Playwright for E2E |
| **CI/CD** | GitHub Actions – lint, type‑check, test, build, coverage |
| **Version Control** | Conventional Commits + Semantic Release |

---

## Testing
bash
# Unit tests
npm run test:unit

# End‑to‑end tests
npm run test:e2e

# Full test suite ( CI runs )
npm run test


---

## AI Agent Directives
<details>
<summary>Click to expand AI Agent Directives</summary>

**Tech Stack Definition**
- **Client**: React‑Native (Expo) written in TypeScript.
- **Server**: Node.js (Express) written in TypeScript.
- **AI Provider**: Cerebras Inference via OpenAI SDK (base URL `https://api.cerebras.ai/v1`).
- **Lint/Format**: Biome.
- **Test Frameworks**: Vitest (unit), Playwright (E2E).
- **CI**: GitHub Actions workflow `ci.yml`.

**Architectural Patterns**
- **Front‑End**: Feature‑Sliced Design – each feature lives under `src/features/<feature>` with UI, hooks, and state isolated.
- **Back‑End**: Hexagonal (Ports & Adapters) – the Express router is the primary port; Cerebras client is an adapter abiding by a clear interface.
- **SOLID**: Classes/services respect SRP; dependency injection used for AI client.
- **DRY & YAGNI**: Shared utilities live under `src/shared`; only needed abstractions are introduced.

**Verification Commands**
bash
# Lint & format
npm run lint
npm run format

# Type‑check
npm run typecheck

# Run full CI locally
npm run ci


**Operational Constraints** (as per base_agents_md_content)
- Max output tokens: 32768.
- Context window: 65536.
- Concurrency limit: 5 workers.
- Circuit breaker with exponential back‑off on 429/500.

</details>

---

## Contributing
Please see `CONTRIBUTING.md` for guidelines on how to submit issues, pull requests, and coding standards.

---

## License
This project is licensed under **CC BY‑NC 4.0**. See the `LICENSE` file for details.
