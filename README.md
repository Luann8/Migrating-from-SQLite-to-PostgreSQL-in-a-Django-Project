# Migrating from SQLite to PostgreSQL in a Django Project

This tutorial provides step-by-step instructions on how to migrate your SQLite database to PostgreSQL in a Django project.

## Prerequisites

- Python and Django installed
- PostgreSQL installed
- `psycopg2` package installed (run `pip install psycopg2`)

## Steps

1. **Export from SQLite:**
   - Use the `sqlite3` command to export your SQLite database to an SQL file.
     ```bash
     sqlite3 your_db.sqlite .dump > sqlite_dump.sql
     ```

2. **Edit the Dump (Optional):**
   - Open the `sqlite_dump.sql` file in a text editor and adjust as necessary.

3. **Configure PostgreSQL in Django:**
   - Update your Django project settings in `settings.py` to use PostgreSQL.
     ```python
     DATABASES = {
         'default': {
             'ENGINE': 'django.db.backends.postgresql_psycopg2',
             'NAME': 'your_db',
             'USER': 'your_user',
             'PASSWORD': 'your_password',
             'HOST': 'localhost',
             'PORT': '5432',
         }
     }
     ```

4. **Import to PostgreSQL:**
   - Use the `psql` command to import the SQL file into PostgreSQL.
     ```bash
     psql -U your_user -d your_db -h localhost -f sqlite_dump.sql
     ```

5. **Verification and Final Adjustments:**
   - Verify that the migration was successful and make additional adjustments if necessary.

6. **Run Django Migrations:**
   - Execute Django migrations to synchronize the database schema.
     ```bash
     python manage.py migrate
     ```

7. **Test Application:**
   - Run your Django application and perform tests to ensure everything is functioning as expected.

Remember to back up important data before starting the migration process. Be aware that some SQLite-specific customizations may require additional adjustments.

## Additional Notes

- Ensure that PostgreSQL is running, and the database is created.
- Use secure passwords, and do not share sensitive information in your repository.

We hope this guide makes the successful migration of your SQLite database to PostgreSQL in a Django project straightforward.
