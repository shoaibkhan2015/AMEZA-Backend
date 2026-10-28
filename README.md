# Améza backend

Express API for the Améza storefront. The frontend is maintained separately
in [AMEZA-Frontend](https://github.com/shoaibkhan2015/AMEZA-Frontend).

## Local development

Use Node.js 22.12 or newer.

```sh
npm ci
cp .env.example .env
npm run dev
```

The API listens on port 4000 by default. Health check: `/health`; API routes:
`/api`.

## Configuration

Set `SUPABASE_URL` and `SUPABASE_SERVICE_ROLE_KEY` together to use Supabase.
If both are unset, the API uses `data/seed.json` and local JSON storage.
`CORS_ORIGIN` must contain the frontend's origin; multiple origins can be
comma-separated. Shipping and order-email settings are optional.

Apply the SQL in `supabase/schema.sql` to initialize the database. The
additional admin SQL is in `supabase/admin.sql`.

## Deployment

Deploy this repository as a Node.js service. Use `npm ci` to install and
`npm start` to run it. Set the environment variables above in the hosting
provider, including `CORS_ORIGIN` for the deployed frontend origin. Configure
the frontend's `VITE_API_URL` to this service's public origin (without a
trailing slash).
