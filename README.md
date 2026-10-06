# MTW Finance ERP V4

**B & I Metal and Timber Works Co. Ltd**

V4 is based on the uploaded V3 Flask application and adds:
- Daily, weekly, monthly and annual financial reports.
- Custom From/To date reporting.
- Report PDF download.
- Report CSV download.
- Dedicated print-ready report view.
- Invoice PDF download and browser print.
- Configurable company logo and stamp/mhuri upload.
- Company name defaults to B & I Metal and Timber Works Co. Ltd.
- Initial finance login.

## Initial login
Username: `accounts`
Password: `ChangeMe123!`

**Change the password before production use.** The password can be controlled with `ACCOUNTS_PASSWORD` when creating the first user on a fresh database.

## Run
1. Install Python 3.11+.
2. `pip install -r requirements.txt`
3. Set environment variables from `.env.example`.
4. Run `python app.py` or use Gunicorn in production.
5. Open `/login`.

The application uses SQLite by default for testing and can use PostgreSQL through `DATABASE_URL`.
