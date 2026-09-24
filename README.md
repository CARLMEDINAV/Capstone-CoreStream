# CoreStream

## 📖 Descripción del Proyecto
**CoreStream** es una plataforma de gestión de tickets y épicas diseñada con un flujo de trabajo tipo kanban (workbench).

* **¿Qué hace?**: Permite la administración de tareas mediante la creación de tickets, seguimiento de estados y manejo de épicas y subtareas, integrando soporte de notificaciones en tiempo real y control de acceso basado en roles (RBAC).
* **¿A quién va dirigido?**: Está orientada principalmente a equipos de desarrollo.
* **¿Qué problema resuelve?**: Centraliza la gestión del trabajo colaborativo, manteniendo a los equipos sincronizados mediante actualizaciones automáticas (WebSockets) y un registro histórico de auditoría de los cambios (Event Sourcing parcial).

## 🛠️ Tecnologías Utilizadas
* **Frontend**: Vue 3 (Composition API), TypeScript, Vite, Tailwind CSS, Pinia (estado global), Vue Router y Axios.
* **Backend**: FastAPI (Python) servidor ASGI, SQLAlchemy (ORM), Alembic (Migraciones) y Pydantic (Validación).
* **Base de Datos**: PostgreSQL (motor relacional principal).
* **Cache y Colas**: Redis (Pub/Sub para eventos y caché) y ARQ (Worker para tareas asíncronas).
* **Cloud / Despliegue**: Vercel (Frontend), Railway (Backend y Base de datos) y GitHub (CI/CD).[cite: 1]

## ⚙️ Instrucciones para ejecutar localmente
#Se omite por el momento por acta de confidencialidad.

**Prerrequisitos:**
* Node.js
* Python 3.x
* Docker y Docker Compose
  
##Integrantes
Jesus Johnson(Jefe de proyecto - desarrollador)
Javier Soto (Desarrollador)
Carlos Medina (Desarrollador)
Benjamin Rosales (Desarrollador - QA)


📋 Metodología de Trabajo
El equipo utiliza [Scrum / Kanban] como metodología ágil de trabajo.

🏗️ Arquitectura de la Solución
La arquitectura de CoreStream se basa en una separación de capas (Layered Architecture) para mantener el backend desacoplado, utilizando un patrón de repositorio/ORM para el acceso a la base de datos.

Componentes Principales:

Frontend: Aplicación reactiva que consume una API centralizada y mantiene una conexión WebSocket nativa para actualizaciones en vivo.
Backend API: Desarrollada en FastAPI, expone endpoints modulares (routers separados por dominio como auth, tickets, epics, etc.) e implementa middlewares para autenticación JWT y CORS.
Eventos Asíncronos y Tiempo Real: Utiliza un patrón Pub/Sub con Redis, ARQ funciona como una cola para procesar tareas en segundo plano, mientras que el backend emite eventos a un canal de notificaciones para actualizar a los clientes vía WebSocket.
Seguridad: Autenticación mediante tokens JWT y control de acceso basado en roles (ADMIN, TEAM_LEADER, DEVELOPER) Las contraseñas están almacenadas de forma segura utilizando un hasheo con bcrypt.
