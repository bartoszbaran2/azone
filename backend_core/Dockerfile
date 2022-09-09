# alpine - okrojona lżejsza wersja
FROM python:3.10-alpine

WORKDIR /app

# PYTDONTWRITECODE wyłącza python cache, nie będzie zapisywał .pyc pliku
# PYTHONBUFFERED aby nie buforował standardauto i standarderror
# aby container był stateless, nie chcemy nic zapisywać
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1


COPY Pipfile Pipfile.lock ./

RUN pip install -U pipenv
RUN pipenv install --system

COPY ./entrypoint.sh .
RUN +x ./entrypoint.sh

COPY . .

ENTRYPOINT ["./entrypoint.sh"]

# CMD python manage.py runserver 0.0.0.0:8000