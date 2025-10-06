# Étape 1 : image Node pour dev
FROM node:20-alpine

# 1. Définir le répertoire de travail
WORKDIR /usr/src/app

# 2. Copier les fichiers de dépendances
COPY package*.json ./

# 3. Installer Angular CLI globalement et dépendances
RUN npm install -g @angular/cli@18 \
    && npm install

# 4. Copier le reste du projet
COPY . .

# 5. Exposer le port Angular (dev SSR = 4000, dev normal = 4200)
EXPOSE 4200
EXPOSE 4000

# 6. Commande par défaut : dev SSR avec hot reload
CMD ["npm", "run", "dev:ssr"]
