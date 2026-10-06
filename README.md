# MTW ERP V4 — Railway Ready

This package is prepared for GitHub + Railway + Railway PostgreSQL.

## Login
Default username: `accounts`
Default password: `ChangeMe123!`

For production, set `ACCOUNTS_PASSWORD` in Railway Variables. On startup, the app will create the `accounts` user if missing, or update its password to the value of `ACCOUNTS_PASSWORD` if the user already exists.

## Railway Variables
Set:
- `DATABASE_URL` = `${{Postgres.DATABASE_URL}}`
- `SECRET_KEY` = a long random secret
- `ACCOUNTS_PASSWORD` = your desired Accounts password

## Deployment
1. Create a private GitHub repository.
2. Upload the CONTENTS of this ZIP to the repository root. `app.py`, `Dockerfile`, `requirements.txt`, and `railway.toml` must be directly in the root.
3. In Railway create a project.
4. Add a PostgreSQL service.
5. Add a GitHub service from the repository.
6. Add the three variables above to the web service.
7. Deploy.
8. Test `/health`. It should return `{"status":"ok","database":"connected"}`.
9. Open `/login` and sign in with the configured `ACCOUNTS_PASSWORD`.

Do not put a `.env` file or real passwords in GitHub.
