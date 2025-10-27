# Usa Python 3.11 slim
FROM python:3.11-slim

# Instalar dependencias del sistema (útil para telemetría y diagnósticos)
RUN apt-get update && apt-get install -y curl && rm -rf /var/lib/apt/lists/*

# Establecer directorio de trabajo
WORKDIR /app

# Copiar e instalar dependencias
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copiar todo el código del proyecto (incluyendo la carpeta app/)
COPY . .

# Exponer el puerto (documentativo)
EXPOSE 8000

# Ejecutar FastAPI con OpenTelemetry y puerto dinámico (Azure usa la variable $PORT)
CMD ["sh", "-c", "opentelemetry-instrument uvicorn app.main:app --host 0.0.0.0 --port ${PORT:-8000}"]
