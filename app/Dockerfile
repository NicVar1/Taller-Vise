# Imagen base
FROM python:3.11-slim

# Carpeta de trabajo dentro del contenedor
WORKDIR /app

# Copiar requirements
COPY app/requirements.txt .

# Instalar dependencias
RUN pip install --no-cache-dir -r requirements.txt

# Copiar toda la aplicación (solo la carpeta app)
COPY app/ .

# Exponer el puerto
EXPOSE 8000

# Comando de inicio
CMD ["sh", "-c", "opentelemetry-instrument uvicorn main:app --host 0.0.0.0 --port ${PORT:-8000}"]
