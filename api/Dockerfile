

from python:3.7.3-alpine as base
from base as builder
RUN apk add --no-cache python3 python3-dev py-pip build-base
WORKDIR /api
COPY requirements.txt ./
RUN pip install -r requirements.txt
COPY . ./
EXPOSE 8000

FROM base

copy --from=builder /api /usr/local
RUN mkdir /app/

COPY manage.py /app/manage.py


# establish what command will run when the docker run command is executed
CMD ["python", "/app/manage.py"]