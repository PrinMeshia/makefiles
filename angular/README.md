# Installer les dépendances
make install

# Lancer le SSR Angular en local
make start-ssr

# Builder et lancer en Docker
make docker-up

# Stopper le conteneur
make docker-down

# Rebuild complet SSR
make build-ssr

# Lancer les tests
make test
