## Hotel Management Project

# DjangoMart E-commerce Project

## Prerequisites

- Python 3.8+
- PostgreSQL
- Git

## PostgreSQL Setup

### Windows
1. Download PostgreSQL from [official website](https://www.postgresql.org/download/windows/)
2. Run installer and follow setup wizard
3. Set password for postgres user
4. Open pgAdmin to manage database
5. Create database:
   ```sql
   CREATE DATABASE mysite;
   ```

### Linux
1. Install PostgreSQL:
   ```bash
   sudo apt update
   sudo apt install postgresql postgresql-contrib
   ```
2. Start service:
   ```bash
   sudo systemctl start postgresql
   sudo systemctl enable postgresql
   ```
3. Create database:
   ```bash
   sudo -u postgres psql
   CREATE DATABASE mysite;
   ```

## Project Setup

1. Clone repository:
   ```bash
   git clone <repository-url>
   cd djangomart
   ```

2. Create virtual environment:
   ```bash
   python -m venv venv
   ```

3. Activate virtual environment:
   - Windows: `venv\Scripts\activate`
   - Linux: `source venv/bin/activate`

4. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

5. Create .env file with these variables:
   ```
   EMAIL_HOST=smtp.gmail.com
   EMAIL_HOST_USER=your-email@gmail.com
   EMAIL_HOST_PASSWORD=your-app-password
   
   CLOUDINARY_CLOUD_NAME=your-cloud-name
   CLOUDINARY_API_KEY=your-api-key
   CLOUDINARY_API_SECRET=your-api-secret
   
   SSLCOMMERZ_STORE_ID=your-store-id
   SSLCOMMERZ_STORE_PASSWORD=your-store-password
   ```

6. Run migrations:
   ```bash
   python manage.py makemigrations
   python manage.py migrate
   ```

7. Create superuser:
   ```bash
   python manage.py createsuperuser
   ```

8. Run with gunicorn:
   ```bash
   python -m gunicorn djangomart.asgi:application -k uvicorn.workers.UvicornWorker
   ```

Access admin panel at: http://localhost:8000/admin

## Environment Variables Description

- `EMAIL_*`: For email notifications
- `CLOUDINARY_*`: For media file storage
- `SSLCOMMERZ_*`: For payment processing

## Troubleshooting

1. Database connection issues:
   - Check PostgreSQL service is running
   - Verify database credentials in settings.py
   - Ensure database exists

2. Static/Media files not loading:
   - Run `python manage.py collectstatic`
   - Check Cloudinary credentials

## Additional Notes

- **Updating Dependencies**: Periodically update `requirements.txt` to reflect changes in project dependencies using `pip freeze > requirements.txt`.
- **Production Setup**: For production deployment, configure settings (`settings.py`), collect static files (`python manage.py collectstatic`), and use a production-ready web server (e.g., Gunicorn, Nginx).
- **Troubleshooting**: If you encounter issues, refer to Django documentation or seek assistance on community forums like Stack Overflow.