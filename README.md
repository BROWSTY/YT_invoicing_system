
## Requirements File
You need to install the following packages before running the code:
```sh
pip install django

pip install psycopg2

pip install Pillow

pip install uuid

pip install requests

pip install django-crispy-forms

pip install pdfkit
```

In addition you need your machine set up for pdfkit, check out this guide.
[Python Django PDFKIT installation guide](https://skolo.online/documents/django/pdf.html#pdf-generation)

## How to setup
Once this repository is cloned, it is necessary to create a user in postgres, for this we do in postgres:
```
sudo -u postgres psq
```

```
CREATE DTABASE <your_db>;
CREATE USER <your_usr> WITH PASSWORD '<your_pass>';
ALTER ROLE <your_usr> SET cient_encoding TO 'utf8';
ALTER ROLE <your_usr> SET default_transaction_isolation TO 'read comitted';
GRANT ALL PRIVILEGES ON DATABASE <your_db> TO <your_usr>;
```
Once the user in postgres and the database is created, we change to the folder *../YT_invoicing_system/invoicing*, and we modify the file *settings.py*

```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': '<your_db>',
        'USER': '<your_usr>',
        'PASSWORD': '<your_pass>',
        'HOST': 'localhost',
        'PORT': '',
    }
}
```
The *localhost* can be modified to the server host / ip.

Once this changes are saved, we return to *../YT_invoicing_system/* and execute:
```
python3 manage.py collecstatic
```

To run in the server, in this case in the localhost in the port 5000, we run:
```
sudo allow 5000
python3 manage.py runserver 0.0.0.0:5000
```
