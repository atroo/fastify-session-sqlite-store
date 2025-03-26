# fastify-session-sqlite-store

SQLite session store for [fastify](https://github.com/fastify/fastify).

This is basically a fork bumping versions to be installable.

It is meant to be used with [@mgcrea/fastify-session](https://github.com/mgcrea/fastify-session) and not the fastify/session plugin.

Purpose is mostly for local development as MemoryStore will lose all sessions with auto reload. It writes SQLite DB to the local filesystem, so it's not suited for production as it won't scale.

## Install

```
npm install @atroo/fastify-session-sqlite-store
```

## Usage

```typescript
import fastifySession from '@mgcrea/fastify-session'
import {SQLiteStore} from "@atroo/fastify-session-sqlite-store"

const store = new SQLiteStore()

await fastify.register(fastifySession, {
  store,
  saveUninitialized: false,
  cookieName: 'session',
  cookie: { maxAge: SESSION_TTL, secure: false },
});

```

## Misc

- Relies on [better-sqlite3](https://github.com/JoshuaWise/better-sqlite3) to interact with sqlite.
- Built with [TypeScript](https://www.typescriptlang.org/) for static type checking with exported types along the
  library.