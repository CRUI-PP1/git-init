# Estructura de Ramas Git

## Ramas Principales

### main (master)

- Rama principal de producción
- Contiene código estable y listo para producción
- Solo se actualiza mediante merge desde develop o hotfix
- Las versiones se manejan a través de las ramas de release

### develop

- Rama de desarrollo principal
- Contiene el código más reciente para la próxima release
- Rama base para crear feature branches
- Se mergea con main cuando está lista para release

## Ramas de Soporte

### Feature Branches

- Se crean desde develop
- Nomenclatura: `feature/nombre-caracteristica`
- Ejemplo: `feature/login-usuario`
- Se mergean de vuelta a develop cuando están completas
- Nunca interactúan directamente con main

### Release Branches

- Se crean desde develop
- Nomenclatura: `release/vX.Y.Z`
- Ejemplo: `release/v1.2.0`
- Se usan para preparar una nueva versión
- Se mergean a main y develop cuando están listas

### Hotfix Branches

- Se crean desde main
- Nomenclatura: `hotfix/nombre-correccion`
- Ejemplo: `hotfix/correccion-login`
- Se usan para corregir problemas en producción
- Se mergean a main y develop

## Ejemplo de Flujo de Trabajo

1. Crear feature branch:

```bash
git checkout develop
git checkout -b feature/nueva-funcionalidad
```

2. Desarrollar y commitear:

```bash
git add .
git commit -m "feat: implementar nueva funcionalidad"
```

3. Crear release branch:

```bash
git checkout develop
git checkout -b release/v1.0.0
```

4. Crear hotfix:

```bash
git checkout main
git checkout -b hotfix/correccion-critica
```

5. Mergear a main:

```bash
git checkout main
git merge hotfix/correccion-critica
```

## Diagrama de Flujo

```
main (producción)
   ↑
   ├── hotfix/* (correcciones urgentes)
   │     ↑
   │     └── merge a main y develop
   │
develop (desarrollo)
   ↑
   ├── feature/* (nuevas funcionalidades)
   │     ↑
   │     └── merge a develop
   │
   └── release/* (preparación de versión)
         ↑
         └── merge a main y develop
```
