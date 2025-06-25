FROM python:3.12-slim

WORKDIR /app

# Install curl for healthchecks
RUN apt-get update && apt-get install -y curl

COPY . .

RUN pip install --no-cache-dir flask

EXPOSE 8002

CMD ["python", "app.py"]

