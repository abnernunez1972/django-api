# Usa una imagen oficial de Python como base
FROM python:3.9-slim

# Configura el directorio de trabajo dentro del contenedor
WORKDIR /app

# Copia el archivo de dependencias y lo instala
COPY requirements.txt .
RUN apt-get update && apt-get install -y \
    libpq-dev \
    postgresql-client && \
    pip install --no-cache-dir -r requirements.txt

# Copia todo el contenido del proyecto al contenedor
COPY . .

# Exponer el puerto 8000 para el servidor
EXPOSE 8000

# Comando para iniciar el servidor usando Gunicorn
CMD ["gunicorn", "--bind", "0.0.0.0:8000", "django_api.wsgi:application"]
