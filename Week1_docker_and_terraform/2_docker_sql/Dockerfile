FROM python:3.9

RUN apt-get install wget
RUN pip install pandas sqlalchemy psycopg2

WORKDIR /app
COPY upload_lookup.py upload_lookup.py

ENTRYPOINT ["python", "upload_lookup.py"]
