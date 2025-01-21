#syntax=docker/dockerfile:1.4

FROM --platform=${BUILDPLATFORM} python:3.8-slim AS builder
EXPOSE 8000
WORKDIR /app
# Install dependencies
RUN apk update
RUN apk add \
    gcc \
    musl-dev \
    libffi-dev \
    openssl-dev \
    python3-dev \
    cargo \
    mariadb-dev

# Install any needed packages specified in requirements.txt
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of the application code
COPY . /app

# Run server
ENTRYPOINT ["python3"]
CMD ["manage.py", "runserver", "0.0.0.0:8000"]