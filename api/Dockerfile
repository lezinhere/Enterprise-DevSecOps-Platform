
FROM python:3.10.5-alpine3.16


WORKDIR /app

RUN apk add --no-cache entr postgresql-dev musl-dev gcc


COPY requirements.txt /app/requirements.txt
RUN pip install -r requirements.txt


COPY . /app


EXPOSE 80


CMD ["gunicorn", "app:app", "-b", "0.0.0.0:8080", "--log-file", "-", "--access-logfile", "-", "--workers", "4", "--keep-alive", "0"]
