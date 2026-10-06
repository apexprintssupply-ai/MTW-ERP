# MTW ERP V4 - Railway Ready

This package is prepared for deployment as a Flask + PostgreSQL application on Railway.

## Important

Do NOT upload a real `.env` file or passwords to GitHub.

The built-in Accounts login is:

- Username: `accounts`
- Password: the value of Railway variable `ACCOUNTS_PASSWORD`

If the `accounts` user already exists in PostgreSQL, the application synchronizes its password hash with `ACCOUNTS_PASSWORD` at startup. This prevents the common problem where changing the Railway variable does not change the existing database user's password.

## GitHub structure

The contents of this package should be the root of the GitHub repository:

```text
MTW-ERP/
├── app.py
├── requirements.txt
├── Dockerfile
├── railway.toml
├── .env.example
├── .gitignore
├── templates/
└── static/
```

Do not create an extra `mtw_erp_v4/` folder inside the GitHub repository.

## Railway setup

1. Create a Railway project.
2. Add a PostgreSQL database service.
3. Add a GitHub service and select this repository.
4. In the MTW ERP web service, add these variables:

```text
DATABASE_URL=${{Postgres.DATABASE_URL}}
SECRET_KEY=<long-random-secret>
ACCOUNTS_PASSWORD=<your-login-password>
```

Replace `Postgres` with the exact name of your Railway PostgreSQL service if you renamed it.

5. Deploy the web service.
6. Test:

```text
https://YOUR-RAILWAY-DOMAIN/health
```

Expected response:

```json
{"status":"ok","database":"connected"}
```

7. Open:

```text
https://YOUR-RAILWAY-DOMAIN/login
```

Use username `accounts` and the value of `ACCOUNTS_PASSWORD`.

## Data storage

Production data is stored in Railway PostgreSQL through `DATABASE_URL`. Do not delete the PostgreSQL service if you want to keep the ERP data.

## Updating the application

Push code changes to the connected GitHub branch. Railway can redeploy the web service while keeping the same PostgreSQL database.
