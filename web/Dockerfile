FROM python:3.7

WORKDIR /app

# 1. Les dépendances : le plus long à construire, mais qui change rarement
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# 2. Les assets statiques et la licence : changent peu souvent
COPY LICENSE .
COPY static/ ./static/
COPY templates/ ./templates/

# 3. Le code (plus volatil)
COPY *.py .

# 4. Permissions pour éviter l'erreur d'exécution
RUN chmod -x /app/app.py

# 5. Configuration réseau du conteneur
EXPOSE 5000

# 6. Commande de démarrage par défaut
CMD ["python", "app.py"]