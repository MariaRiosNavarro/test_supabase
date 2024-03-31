# Nuxt 3 + Vite + Supabase with Docker (only Deployment)

[Docker Deployment Guide for Nuxt](https://medium.com/@jkpeyi/deploying-a-nuxt-js-application-with-docker-69bf822c066d)

# Wichtig

.env dateien IMMER mit den VITE\_ davor damit erkannt werden, wie in REACT. zb

```
VITE_SUPABASE_URL=
VITE_SUPABASE_KEY=

```

-Dann so  nutzen:

```
import { createClient } from "@supabase/supabase-js";

export const supabase = createClient(
  import.meta.env.VITE_SUPABASE_URL,
  import.meta.env.VITE_SUPABASE_KEY
);

```

IM supabase die Auth policy in den Tables checken und einstellen sonst wird uns ein leeres Array werfen


# DOCKER DEPLOYMENT

DOCKER files sind NUR für Deployment. Es heiß nicht für development. Nach jeder Änderung braucht man die vorherige Container und Image löschen und wieder bauen mit `docker compose up`. Dev nur zurzeit wie immer mit `npm run dev`ohne docker

