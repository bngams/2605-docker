# Environnement / système de base
# Utiliser une image de base pour faciliter la config

# FROM debian:trixie-slim
# RUN apt-get update && apt-get install -y python3 python3-pip

# Utiliser une image de base avec Python préinstallé
FROM python:3.11-slim-trixie

# Définir le répertoire de travail dans l'image
# WORKDIR <chemin_dans_l_image>
# Toutes les commandes suivantes seront exécutées à partir de ce répertoire
WORKDIR /app

# Copier des fichiers dans l'image
# COPY <source_en_local> <destination_dans_l_image>

# Copier 1 par 1 les fichiers nécessaires
# COPY requirements.txt requirements.txt
# COPY index.py index.py

# Ou copier tous les fichiers du répertoire courant (où se trouve le Dockerfile) dans le répertoire de travail de l'image
# /!\ Attention à ne pas copier des fichiers inutiles (ex: .git, __pycache__, etc.) 
# => utiliser un fichier .dockerignore pour les exclure
COPY . .

# Executer une commande lors de la construction de l'image
# RUN <commande>
# Exemples : 
# RUN pip install -r requirements.txt...
# RUN apt-get update && apt-get install -y <package>
RUN pip install -r requirements.txt

# Exposer un port (si l'application écoute sur un port)
# EXPOSE <numéro_de_port>
# Ex: EXPOSE 5000
# Documentation seulement, à titre d'info
# n'ouvre pas réellement le port dans le conteneur
EXPOSE 80

# Commande à exécuter lors du lancement du conteneur (avec docker run)
# CMD <commande>
# Forme recommandée : CMD ["executable", "param1", "param2"] (liste de chaînes de caractères)
# Autre forme possible
CMD ["python", "index.py"]