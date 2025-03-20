# n8n - Installation et Exécution avec Docker Compose

Ce dépôt contient tout le nécessaire pour exécuter **n8n**, un outil d'automatisation de workflows, en utilisant **Docker Compose**. Voici la procédure pour installer, configurer et exécuter n8n sur votre machine.  

---

## Prérequis

Avant de commencer, assurez-vous d'avoir installé :
- **Docker** ([Installation](https://docs.docker.com/get-docker/))
- **Docker Compose** ([Installation](https://docs.docker.com/compose/install/))

Vérifiez vos installations avec :
```bash
docker --version
docker compose version
```

---

## 📂 Cloner le dépôt

Commencez par cloner ce dépôt :
```bash
git clone https://github.com/Mathieu-Soussignan/n8n-docker.git
cd [VOTRE-REPO]
```

---

## Configuration (Facultatif)

Si vous souhaitez personnaliser votre installation (authentification, timezone, webhooks...), modifiez les variables d'environnement dans le fichier `docker-compose.yml`.

Exemple de variables :
```yaml
environment:
  - N8N_BASIC_AUTH_ACTIVE=true
  - N8N_BASIC_AUTH_USER=monuser
  - N8N_BASIC_AUTH_PASSWORD=monmotdepasse
  - GENERIC_TIMEZONE=Europe/Paris
```
> **Remarque** : Il est recommandé de sécuriser l'accès à n8n avec une authentification.

---

## 🚀 Lancer n8n

Démarrez n8n en arrière-plan avec :
```bash
docker compose up -d
```
> Cela va créer et exécuter le conteneur.

Vous pouvez maintenant accéder à n8n via :
```
http://localhost:5678
```
Si l'authentification est activée, utilisez les identifiants configurés dans `docker-compose.yml`.

---

## Vérifier le statut du conteneur

- Voir les conteneurs actifs :
  ```bash
  docker compose ps
  ```
- Afficher les logs en direct :
  ```bash
  docker compose logs -f n8n
  ```

---

## Arrêter et supprimer le conteneur

- Pour **stopper** le conteneur sans le supprimer :
  ```bash
  docker compose stop
  ```
- Pour **supprimer** le conteneur :
  ```bash
  docker compose down
  ```
  > ⚠️ **Ne pas utiliser `-v`** sauf si vous voulez supprimer toutes les données stockées.

---

## Mettre à jour n8n

1. Télécharger la dernière version de l’image :
   ```bash
   docker compose pull n8n
   ```
2. Relancer le conteneur avec la nouvelle version :
   ```bash
   docker compose up -d
   ```

---

## Dépannage

- Si le port **5678** est déjà utilisé, changez-le dans `docker-compose.yml` :
  ```yaml
  ports:
    - "8080:5678"  # Remplacez 8080 par un port libre
  ```
  Puis relancez n8n :
  ```bash
  docker compose down && docker compose up -d
  ```

- Si une erreur se produit au lancement, consultez les logs avec :
  ```bash
  docker compose logs -f n8n
  ```

---

## Ressources utiles

- **Documentation Officielle** : [https://docs.n8n.io](https://docs.n8n.io)
- **Dépôt GitHub n8n** : [https://github.com/n8n-io/n8n](https://github.com/n8n-io/n8n)

---

### Vous êtes prêts !

Votre instance n8n est maintenant installée et prête à être utilisée. Profitez de l'automatisation ! 🤖🔥