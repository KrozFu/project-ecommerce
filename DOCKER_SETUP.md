# Docker Setup Instructions

## Environment Files Setup
Since .env files are gitignored, create the required environment files:

1. **Root .env file** (for PostgreSQL and pgAdmin):
```bash
cp .env.example .env
# Edit .env with your PostgreSQL credentials
```

2. **Backend .env.docker file**:
```bash
cp backend/.env.docker.example backend/.env.docker
# Edit with your database URL and secrets
```

3. **Frontend .env.docker file**:
```bash
cp frontend/.env.docker.example frontend/.env.docker
# Edit with your backend URL
```

4. **Root .env.docker file** (for pgAdmin):
```bash
cp .env.docker.example .env.docker
# Edit with pgAdmin credentials
```

## Docker Commands

### Build and start all services:
```bash
docker-compose up --build
```

### Start in detached mode:
```bash
docker-compose up -d
```

### Stop all services:
```bash
docker-compose down
```

### View logs:
```bash
docker-compose logs -f
```

## Services Access
- **Frontend**: http://localhost:3000
- **Backend API**: http://localhost:8000
- **Nginx (Reverse Proxy)**: http://localhost:80
- **PostgreSQL**: localhost:5432
- **pgAdmin**: http://localhost:5050

## Fixes Applied
1. ✅ Fixed frontend build context (was using Docker Hub image)
2. ✅ Fixed backend build context (was using Docker Hub image)
3. ✅ Created environment file templates
4. ✅ Fixed nginx upstream configuration
5. ✅ Fixed backend Dockerfile EXPOSE instruction
6. ✅ Fixed pgAdmin permission issues with sessions directory
7. ✅ Added proper volume management for pgAdmin

## pgAdmin Access
- **URL**: http://localhost:5050
- **Email**: admin@example.com
- **Password**: admin

## Troubleshooting pgAdmin
If pgAdmin still has permission issues, run:
```bash
# Set proper permissions for pgAdmin volume
docker-compose down
docker volume rm project-ecommerce_pgadmin_data
docker-compose up pgadmin
```
