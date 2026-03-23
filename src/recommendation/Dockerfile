FROM python:3.12-slim-bookworm AS base

RUN apt-get update \
 && apt-get install -y --no-install-recommends gcc g++ python3-dev \
 && rm -rf /var/lib/apt/lists/*
 
WORKDIR /usr/src/app

COPY requirements.txt ./

RUN pip install --upgrade pip
RUN pip install -r requirements.txt

COPY . .

RUN opentelemetry-bootstrap -a install 

ENV RECOMMENDATION_PORT 1010

ENTRYPOINT ["python", "recommendation_server.py"]
