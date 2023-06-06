# Utiliser une image de base Node.js pour la construction
FROM node:18.16.0 as builder

# Définir le répertoire de travail dans le conteneur de construction
WORKDIR /app/frontend

# Copier les fichiers package.json et package-lock.json dans le répertoire de travail
COPY package*.json ./

# Installer les dépendances du frontend
RUN npm install

# Copier le reste des fichiers du frontend dans le répertoire de travail
COPY . .

# Construire les fichiers de production du frontend
RUN npm run build

# Utiliser une image légère de production de Nginx
FROM nginx:alpine

# Copier les fichiers de production du frontend depuis le conteneur de construction vers le répertoire des fichiers statiques de Nginx
COPY --from=builder /app/frontend/build /usr/share/nginx/html

# Exposer le port sur lequel Nginx écoute
EXPOSE 3000

# Définir la commande pour démarrer Nginx
CMD ["nginx", "-g", "daemon off;"]
