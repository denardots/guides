# Guía de Despliegue en GitHub Pages

Para desplegar nuestro proyecto en GitHub Pages debemos tener un proyecto creado con Vite y no tener instalado Stylelint y ESLint en el proyecto.

## Despliegue en GitHub Pages

1. Creamos un repositorio público vacio en GitHub

2. Conectamos nuestro proyecto con el repositorio creado

3. Creamos el commit inicial y lo enviamos a GitHub

4. Ingresamos a Setting->Pages dentro de la configuración del repositorio de GitHub

5. Elegimos GitHub Actions y click en Configure de GitHub Pages Jekyll

6. Eliminamos el contenido del archivo y pegamos el siguiente código de la pagina oficial de Vite:

```yml
  # Simple workflow for deploying static content to GitHub Pages
  name: Deploy static content to Pages

  on:
    # Runs on pushes targeting the default branch
    push:
      branches: ['main']

    # Allows you to run this workflow manually from the Actions tab
    workflow_dispatch:

  # Sets the GITHUB_TOKEN permissions to allow deployment to GitHub Pages
  permissions:
    contents: read
    pages: write
    id-token: write

  # Allow one concurrent deployment
  concurrency:
    group: 'pages'
    cancel-in-progress: true

  jobs:
    # Single deploy job since we're just deploying
    deploy:
      environment:
        name: github-pages
        url: ${{ steps.deployment.outputs.page_url }}
      runs-on: ubuntu-latest
      steps:
        - name: Checkout
          uses: actions/checkout@v4
        - name: Set up Node
          uses: actions/setup-node@v4
          with:
            node-version: 20
            cache: 'npm'
        - name: Install dependencies
          run: npm ci
        - name: Build
          run: npm run build
        - name: Setup Pages
          uses: actions/configure-pages@v4
        - name: Upload artifact
          uses: actions/upload-pages-artifact@v3
          with:
            # Upload dist folder
            path: './dist'
        - name: Deploy to GitHub Pages
          id: deployment
          uses: actions/deploy-pages@v4
```

7. Hacemos un commit y luego un pull en nuestro repositorio local

8. Creamos el archivo ***vite.config.js*** agregamos el siguiente código:

```js
  import {defineConfig} from "vite";

  export default defineConfig({
    base: "https://denardots.github.io/prueba"
  });
```

9. Luego hacemos un commit y un push a nuestro repositorio remoto

10. Listo, cuando escribamos el siguiente comando en la terminal se subirá nuestro proyecto a Github Pages

```bash
  npm run build
```

11. Cada vez que subamos el proyecto a producción debemos quitar estas lineas del package.json, solo las volveremos a agregar cuando estemos en desarrollo

```json
"devDependencies": {
    // Eliminamos estas lineas de codigo
    "@eslint/js": "^9.20.0",
    "@html-eslint/eslint-plugin": "^0.35.0",
    "@html-eslint/parser": "^0.35.0",
    "eslint": "^9.20.1",
    "eslint-config-standard": "^17.1.0",
    "eslint-plugin-import": "^2.31.0",
    "stylelint": "^16.14.1",
    "stylelint-config-standard": "^37.0.0",
    // Hasta aquí
    "vite": "^6.1.0",
    "vite-plugin-eslint": "^1.8.1",
    "vite-plugin-stylelint": "^6.0.0"
  }
  