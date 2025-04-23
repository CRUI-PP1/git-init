# Git Init - Ejemplo de Flujo de Trabajo con Git

Este proyecto es un ejemplo práctico de cómo gestionar un proyecto usando Git, siguiendo las mejores prácticas de control de versiones. El proyecto consiste en una aplicación web de ejemplo para demostrar el flujo de trabajo con Git.

## Estructura del Proyecto

```
git-init/
├── docs/                    # Documentación del proyecto
│   ├── historial.md        # Registro de cambios y versiones
│   └── ramas.md           # Documentación de estructura de ramas
├── src/                     # Código fuente
│   ├── app/               # Código de la aplicación
│   └── config/            # Archivos de configuración
├── tests/                  # Pruebas unitarias
├── .gitignore             # Archivos excluidos del control de versiones
└── README.md              # Este archivo
```

## Estructura de Ramas

### Ramas Principales

- `main`: Rama de producción, código estable
- `develop`: Rama de desarrollo, código en progreso

### Ramas de Soporte

- `feature/*`: Nuevas funcionalidades
- `release/*`: Preparación de versiones
- `hotfix/*`: Correcciones urgentes

Para más detalles sobre la estructura de ramas, consulta [docs/ramas.md](docs/ramas.md)

## Flujo de Trabajo Ejemplo

### 1. Configuración Inicial

```bash
# Clonar el repositorio
git clone https://github.com/tu-usuario/git-init.git
cd git-init

# Configurar usuario
git config user.name "Tu Nombre"
git config user.email "tu.email@ejemplo.com"

# Crear ramas principales
git checkout -b main
git checkout -b develop
```

### 2. Desarrollo de Nueva Característica

```bash
# Crear feature branch desde develop
git checkout develop
git checkout -b feature/user-authentication

# Implementar autenticación de usuarios
# Agregar login y registro

# Ver cambios
git diff

# Agregar cambios
git add src/app/auth/

# Crear commit
git commit -m "feat: implementar sistema de autenticación"

# Subir cambios
git push origin feature/user-authentication

# Mergear a develop cuando esté lista
git checkout develop
git merge feature/user-authentication
```

### 3. Preparación de Release

```bash
# Crear release branch
git checkout develop
git checkout -b release/v1.1.0

# Realizar pruebas y ajustes
# ...

# Mergear a main y develop
git checkout main
git merge release/v1.1.0

git checkout develop
git merge release/v1.1.0
```

### 4. Hotfix en Producción

```bash
# Crear hotfix desde main
git checkout main
git checkout -b hotfix/auth-security

# Corregir vulnerabilidad en autenticación
# ...

# Commit y merge
git add .
git commit -m "fix: corregir vulnerabilidad en sistema de autenticación"
git checkout main
git merge hotfix/auth-security

git checkout develop
git merge hotfix/auth-security
```

## Convención de Commits

Usamos el formato convencional de commits:

- `feat:` Nueva funcionalidad
- `fix:` Corrección de errores
- `docs:` Cambios en documentación
- `style:` Cambios de formato
- `refactor:` Refactorización de código
- `test:` Agregar o modificar pruebas
- `chore:` Actualizaciones de tareas de construcción

## Ejemplo de Historial de Commits

```bash
# Ver historial completo
git log --oneline

# Salida esperada:
# 1a2b3c4 fix: corregir vulnerabilidad en autenticación (hotfix)
# 5d6e7f8 feat: implementar sistema de autenticación (feature)
# 9g0h1i2 chore: actualizar .gitignore
# 3j4k5l6 Initial commit
```

## Buenas Prácticas

1. Mantener main y develop actualizadas
2. Crear feature branches desde develop
3. Crear hotfix branches desde main
4. Usar nombres descriptivos para las ramas
5. Revisar cambios antes de hacer push
6. Mantener el historial de commits limpio
7. Resolver conflictos localmente antes de hacer push
8. Actualizar documentación con cada cambio significativo
9. Usar nombres de versión en las ramas de release

## Recursos Adicionales

- [Documentación Oficial de Git](https://git-scm.com/doc)
- [Git Flow](https://nvie.com/posts/a-successful-git-branching-model/)
- [Conventional Commits](https://www.conventionalcommits.org/)
