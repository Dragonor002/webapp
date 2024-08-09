# Usa una imagen base de Python
FROM python:3.11-slim

# Actualiza e instala paquetes necesarios
RUN apt-get update \
    && apt-get install -y \
       python3-venv \
       sqlite3 \
    && rm -rf /var/lib/apt/lists/*

# Establece el directorio de trabajo
WORKDIR /app

# Copia los archivos de requerimientos y el archivo principal
COPY requirements.txt /app/requirements.txt
COPY app.py /app/app.py
COPY templates/ /app/templates/

# Crea y activa un entorno virtual
RUN python3 -m venv venv
ENV PATH="/app/venv/bin:$PATH"

# Instala las dependencias
RUN pip install --no-cache-dir -r /app/requirements.txt

# Expone el puerto en el que la aplicación correrá
EXPOSE 777

# Define el comando por defecto para ejecutar la aplicación
CMD ["python", "app.py"]
