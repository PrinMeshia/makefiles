# ===============================
# Angular SSR + Docker Makefile
# ===============================

# Variables
APP_NAME := angular-app
DOCKER_COMPOSE := docker-compose
DOCKER := docker
PORT_DEV := 4200
PORT_SSR := 4000

# Colors
YELLOW := \033[1;33m
GREEN := \033[1;32m
NC := \033[0m

# ===============================
# 🔧 Développement
# ===============================

.PHONY: install
install:
	@echo "$(YELLOW)📦 Installing dependencies...$(NC)"
	npm install

.PHONY: start
start:
	@echo "$(YELLOW)🚀 Starting Angular dev server on port $(PORT_DEV)...$(NC)"
	ng serve --host 0.0.0.0 --port $(PORT_DEV)

.PHONY: start-ssr
start-ssr:
	@echo "$(YELLOW)🔥 Starting SSR dev mode on port $(PORT_SSR)...$(NC)"
	npm run dev:ssr

# ===============================
# 🐳 Docker
# ===============================

.PHONY: docker-build
docker-build:
	@echo "$(YELLOW)🐳 Building Docker image for $(APP_NAME)...$(NC)"
	$(DOCKER) build -t $(APP_NAME):latest .

.PHONY: docker-up
docker-up:
	@echo "$(YELLOW)📦 Starting Docker containers...$(NC)"
	$(DOCKER_COMPOSE) up --build

.PHONY: docker-down
docker-down:
	@echo "$(YELLOW)🧹 Stopping and cleaning containers...$(NC)"
	$(DOCKER_COMPOSE) down

.PHONY: docker-shell
docker-shell:
	@echo "$(YELLOW)🔧 Opening shell inside container...$(NC)"
	$(DOCKER) exec -it $(APP_NAME)-dev sh

# ===============================
# 🧱 Build & Production
# ===============================

.PHONY: build
build:
	@echo "$(YELLOW)🏗️ Building Angular client app...$(NC)"
	ng build --configuration production

.PHONY: build-ssr
build-ssr:
	@echo "$(YELLOW)🏗️ Building Angular SSR (client + server)...$(NC)"
	npm run build:ssr

.PHONY: serve-ssr
serve-ssr:
	@echo "$(YELLOW)🌐 Running built SSR app (port $(PORT_SSR))...$(NC)"
	npm run serve:ssr

# ===============================
# 🧪 Tests & Lint
# ===============================

.PHONY: test
test:
	@echo "$(YELLOW)🧪 Running unit tests...$(NC)"
	ng test --watch=false

.PHONY: lint
lint:
	@echo "$(YELLOW)🔍 Running linter...$(NC)"
	ng lint

# ===============================
# 🧹 Utils
# ===============================

.PHONY: clean
clean:
	@echo "$(YELLOW)🧹 Cleaning dist and node_modules...$(NC)"
	rm -rf dist node_modules

.PHONY: reset
reset: clean install

.PHONY: help
help:
	@echo "$(GREEN)Available commands:$(NC)"
	@echo "  make install        - Install dependencies"
	@echo "  make start          - Start Angular dev mode"
	@echo "  make start-ssr      - Start Angular SSR dev mode"
	@echo "  make docker-build   - Build Docker image"
	@echo "  make docker-up      - Start Docker containers"
	@echo "  make docker-down    - Stop Docker containers"
	@echo "  make docker-shell   - Open shell in Docker container"
	@echo "  make build          - Build Angular app"
	@echo "  make build-ssr      - Build Angular app (SSR)"
	@echo "  make serve-ssr      - Run SSR in Node"
	@echo "  make test           - Run tests"
	@echo "  make lint           - Lint code"
	@echo "  make clean          - Remove dist & node_modules"
	@echo "  make reset          - Clean and reinstall everything"
