## Configuración de Vite

Luego de haber instalado html-eslint, Stylelint y ESLint, debemos configurar Vite.

1. Agregamos el siguiente comando en la terminal

```bash
  npm install vite-plugin-eslint vite-plugin-stylelint --save-dev
```

1. Creamos el archivo ***vite.config.js*** en la raíz del proyecto y agregamos el siguiente código:

```js
  import {defineConfig} from "vite";
  import eslintPlugin from "vite-plugin-eslint";
  import stylelintPlugin from "vite-plugin-stylelint";

  export default defineConfig({
    plugins: [
      stylelintPlugin(),
      eslintPlugin({include: ["*.html"]})
    ]
  });
```

2. Agregamos los siguientes scripts en el archivo ***package.json***:

```json
  "scripts": {
    "lint:html": "eslint *.html",
    "lint:css": "stylelint public/**/*.css",
    "lint:js": "eslint src/**/*.js",
    "lint": "npm run lint:html && npm run lint:css && npm run lint:js",
  },
```

3. Una vez instalados y configurados los linters, procedemos a trabajar normalmente en nuestro proyecto. Veremos el funcionamiento de los linters cuando escribamos el comando:

```bash 
  npm run lint
``` 
