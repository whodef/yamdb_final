FROM python:3.7-slim AS app

WORKDIR /app

COPY requirements.txt .

RUN pip3 install -r ./requirements.txt --no-cache-dir

COPY . .

RUN python3 manage.py collectstatic --no-input

CMD ["gunicorn", "api_yamdb.wsgi:application", "--bind", "0:8000" ]

LABEL author='Tatiana S.' version=1 broken_keyboards=42

FROM nginx:1.21.3-alpine as nginx

COPY --from=app /app/static /var/html/static

COPY nginx/default.conf /etc/nginx/conf.d/default.conf

RUN ls -lah /var/html/static

