# Usa Python 3.11 slim
FROM python:3.11-slim

# Establecer directorio de trabajo
WORKDIR /app

# Copiar requirements e instalarlos
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copiar el contenido de la carpeta actual (donde está main.py dentro de /app)
COPY . .

# Exponer el puerto dinámico de Azure
EXPOSE 8000

# Comando para ejecutar FastAPI (usa $PORT que Azure define automáticamente)
CMD ["opentelemetry-instrument", "uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
