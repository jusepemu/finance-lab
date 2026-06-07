# Tranqui

> Personal finance and budget management app for individuals who want to take control of their money.

Tranqui helps you answer the questions that matter:

- How am I doing this month?
- Where is my money going?
- Which expense is having the biggest impact?
- How much leeway do I have left?

## Features

- [ ] Simple onboarding: welcome screen and configure profile
- [ ] Record transactions (expense or income) with: amount, category, date, and optional note
- [ ] Basic predefined categories
- [ ] Local-first: all data lives on the device
- [ ] Fully offline: no internet connection required
- [ ] Lightweight onboarding: username and customizable avatar
- [ ] Simple dashboard: current balance, monthly spending, and top-spending category

## Tech Stack

- **Framework:** [SvelteKit](https://kit.svelte.dev/) (Svelte 5)
- **Styling:** [Tailwind CSS](https://tailwindcss.com/) v4
- **Build Tool:** [Vite](https://vitejs.dev/) v6
- **Language:** [TypeScript](https://www.typescriptlang.org/)
- **Local Database:** [Dexie](https://dexie.org/) (IndexedDB wrapper for local-first storage)
- **PWA:** Progressive Web App support via `@vite-pwa/sveltekit` for offline capabilities

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) (v24.14.0 or later)
- [pnpm](https://pnpm.io/) (v11.5.2 or later — this project uses pnpm as its package manager)

> 💡 **Tip:** If you use `nvm`, you can run `nvm use` to automatically switch to the correct Node.js version specified in `.nvmrc`.

### Development

```bash
# Clone the repo
git clone git@github.com:jusepemu/finance-lab.git 
cd tranqui

# Install dependencies
pnpm install

# Start the development server
pnpm run dev

# The app will be available at http://localhost:5173
```

### Production Build

```bash
# Build for production
pnpm run build

# Preview the production build locally
pnpm run preview
```

## Usage

<!-- Add screenshots or usage instructions once the app has a UI -->

## Project Structure

```
tranqui/
├── src/
├── tests/
├── README.md
└── package.json
```

## Roadmap

- v0.1 — Core local-first (current): transactions, categories, and simple dashboard
- v0.2 — Data export
- v0.3 — Reminders / alerts
- Future — Real backend for cloud sync and backup
- Much later — Bank integration

## Contributing

Contributions are welcome! Please open an issue or submit a PR.

## License

[MIT](LICENSE)
