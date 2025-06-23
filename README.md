# Ejercicio: Desplegar una app React en GitHub Pages usando un workflow reutilizado

## Objetivo

Aprender a reutilizar workflows públicos para automatizar el despliegue de aplicaciones en GitHub Pages. En este ejercicio, crearás una aplicación React y la desplegarás automáticamente usando un flujo de trabajo predefinido reutilizable desde otro repositorio.

---

## Tareas

### 1. Crear la aplicación React

1. En la raíz de tu repositorio, ejecuta:

   ```bash
   npx create-react-app my-app
   ```

   >  Puedes cambiar `my-app` por cualquier otro nombre si lo deseas.

---

### 2. Configurar el proyecto para GitHub Pages

1. Abre el archivo `my-app/package.json`.

2. Añade la propiedad `homepage`:

   ```json
   "homepage": "https://<TU_USUARIO>.github.io/<TU_REPOSITORIO>"
   ```

   > Sustituye `<TU_USUARIO>` y `<TU_REPOSITORIO>` por tu nombre de usuario de GitHub y el nombre del repositorio respectivamente.

---

### 3. Crear el workflow de despliegue

1. Crea el archivo `.github/workflows/deploy.yml`.

2. Añade el siguiente contenido:

   ```yaml
   name: Deploy React to GitHub Pages

   on:
     push:
       branches: [main]

   jobs:
     deploy:
       uses: miandada/helloworldjs/.github/workflows/workflow.yml@main
       with:
         working-directory: my-app
   ```

   >  El input `working-directory` le indica al workflow reutilizado dónde está tu aplicación React.

---

## Pruebas

1. Haz push de tus cambios a la rama `main`.

2. Verifica que el workflow se ejecuta correctamente desde la pestaña **Actions** de GitHub.

3. Una vez completado, abre la siguiente URL en tu navegador:

   ```
   https://<TU_USUARIO>.github.io/<TU_REPOSITORIO>/
   ```

---

## Reflexión

- ¿Qué beneficios te ofrece reutilizar workflows de otros proyectos?
- ¿Cómo afectaría el cambio de nombre del directorio de tu aplicación al workflow?
- ¿Crees que esta estrategia sería útil en proyectos más grandes o con varios equipos?
