# Traefik

https://www.it-connect.fr/tuto-traefik-reverse-proxy-avec-docker/
https://www.youtube.com/watch?v=Ct5EBiSuy5U

# Base 
https://doc.traefik.io/traefik/getting-started/docker/

1- Creation du réseau "Frontend"
docker network create frontend

Ajout dans le compose :

    networks:
      - frontend
networks:
  frontend:
    external: true

2- Fichier de conf

Crée le fichier traefik.yml au même niveau que le compose.

Ajouter le volume le docker compose :
      - ./traefik.yml:/etc/traefik/traefik.yml:ro

Dans le fichier ajouter les lignes :

# Configuration statique de Traefik
global:
  checkNewVersion: false
  sendAnonymousUsage: false

api:
  dashboard: true # Dashboard Traefik : 8080
  insecure: true

entryPoints:
  web:
    address: ":80" # EntryPoint pour HTTP
  websecure:
    address: ":443" # EntryPoint pour HTTPS

