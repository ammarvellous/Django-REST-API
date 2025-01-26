#syntax=docker/dockerfile:1.4

FROM --platform=${BUILDPLATFORM} python:3.8-slim AS builder
EXPOSE 8000
WORKDIR /app


# Install dependencies
RUN apt-get update && apt-get install -y \
    gcc \
    musl-dev \
    libffi-dev \
    libssl-dev \
    python3-dev \
    cargo \
    libmariadb-dev \
    pkg-config

# Install any needed packages specified in requirements.txt
COPY requirements.txt .
RUN pip install --upgrade pip
RUN pip install -r requirements.txt

# Copy the rest of the application code
COPY . .

# Expose port 8000
EXPOSE 8000

# Run the application
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]