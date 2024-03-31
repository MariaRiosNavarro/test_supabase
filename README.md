# Nuxt 3 + Vite + Supabase with Docker (only Deployment)

# Wichtig

.env dateien IMMER mit den VITE\_ davor damit erkannt werden, wie in REACT. zb

```
VITE_SUPABASE_URL=
VITE_SUPABASE_KEY=

```

-dann so im code zb so nutzen:

```
import { createClient } from "@supabase/supabase-js";

export const supabase = createClient(
  import.meta.env.VITE_SUPABASE_URL,
  import.meta.env.VITE_SUPABASE_KEY
);

```

IM supabase die Auth policy in den Tables checken und einstellen sonst wird uns ein leeres Array


---

DOCKER files sind nur für Deployment. Es heiß nicht für development. NAch jeder Änderung braucht man die vorherige Container und Image löschen und wieder bauen mit `docker compose up`. Dev nur zurzeit wie immer mit `npm run dev`ohne docker







Look at the [Nuxt 3 documentation](https://nuxt.com/docs/getting-started/introduction) to learn more.

## Setup

Make sure to install the dependencies:

```bash
# npm
npm install

# pnpm
pnpm install

# yarn
yarn install

# bun
bun install
```

## Development Server

Start the development server on `http://localhost:3000`:

```bash
# npm
npm run dev

# pnpm
pnpm run dev

# yarn
yarn dev

# bun
bun run dev
```

## Production

Build the application for production:

```bash
# npm
npm run build

# pnpm
pnpm run build

# yarn
yarn build

# bun
bun run build
```

Locally preview production build:

```bash
# npm
npm run preview

# pnpm
pnpm run preview

# yarn
yarn preview

# bun
bun run preview
```

Check out the [deployment documentation](https://nuxt.com/docs/getting-started/deployment) for more information.
