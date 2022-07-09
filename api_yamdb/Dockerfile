FROM python:3.7-slim

WORKDIR /app

COPY ./ ./

RUN pip3 install -r requirements.txt --no-cache-dir

RUN python manage.py migrate

RUN python manage.py collectstatic --no-input

RUN python manage.py createsuperuser

RUN python manage.py import_csv_data users.csv category.csv genre.csv titles.csv genre_title.csv review.csv comments.csv

CMD ["gunicorn", "api_yamdb.wsgi:application", "--bind", "0:8000" ]