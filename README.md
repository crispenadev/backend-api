# Simple Backend API

Backend simple con FastAPI para desplegar en Railway.

## Estructura del Proyecto

```
simple-backend/
├── .antigravity/               # Configuración de Antigravity
│   ├── settings.json          # Configuración del proyecto
│   ├── rules.md              # Reglas de desarrollo
│   └── workflows/            # Workflows de CI/CD
├── src/
│   ├── api/v1/endpoints/     # API route handlers
│   ├── services/             # Business logic y servicios
│   ├── models/               # Data models y schemas
│   ├── db/                   # Database connection
│   ├── core/                 # Configuration y settings
│   ├── tests/                # Tests
│   └── main.py               # FastAPI app principal
├── requirements.txt
├── Dockerfile
└── railway.json
```

## Endpoints

- `GET /` - Retorna "Hola Mundo"
- `GET /health` - Health check

## Desarrollo Local

```bash
# Instalar dependencias
pip install -r requirements.txt

# Ejecutar servidor
uvicorn src.main:app --reload --port 8000
```

## Tests

```bash
# Ejecutar tests
pytest

# Con coverage
pytest --cov=src
```

La API estará disponible en `http://localhost:8000`

## Desplegar en Railway

### Opción 1: Desde GitHub

1. Sube el código a GitHub
2. Ve a [Railway](https://railway.app)
3. Click en "New Project"
4. Selecciona "Deploy from GitHub repo"
5. Conecta tu repositorio
6. Railway detectará automáticamente la configuración

### Opción 2: Desde CLI

```bash
# Instalar Railway CLI
npm i -g @railway/cli

# Login
railway login

# Inicializar proyecto
railway init

# Desplegar
railway up
```

### Opción 3: Despliegue Directo

```bash
railway login
railway link
railway up
```

## URL de Producción

Después del despliegue, Railway te dará una URL como:
`https://tu-proyecto.up.railway.app`

Prueba el endpoint:
```bash
curl https://tu-proyecto.up.railway.app/
```

Respuesta esperada:
```json
{"message": "Hola Mundo"}
```
