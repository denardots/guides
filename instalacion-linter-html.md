# Guía de Instalación de html-eslint

Para que nuestro código sea más limpio y eficiente es importante trabajar con linters.

Un linter es una convención de reglas de desarrollo que permitirá que nuestro proyecto sea mas legible, eficiente y escalable.

Para instalar html-eslint es necesario tener un proyecto creado con Vite y haber instalado previamente ESLint

## Instalación de html-eslint

1. Agregamos el siguiente comando en la terminal

```bash 
  npm install eslint @html-eslint/parser @html-eslint/eslint-plugin --save-dev
```

2. En el archivo ***eslint.config.js*** agregamos el siguiente código:

```js
  import html from "@html-eslint/eslint-plugin";
  export default [
    pluginJs.configs.recommended,
    {
      ...html.configs["flat/recommended"],
      files: ["**/*.html"],
    }
  ];
```
3. Si queremos agregar reglas extra, debemos agregar las siguientes reglas al archivo ***eslint.config.js***.

```js
  // Arriba se encuentran las reglas y configuración de ESLint
  {
    ...html.configs["flat/recommended"],
    files: ["**/*.html"],
    rules: {
      ...html.configs["flat/recommended"].rules,
      // Regla para evitar espacios inncesarios
      "@html-eslint/no-extra-spacing-text": "error",
      // Regla para evitar elementos HTML interactivos anidados
      "@html-eslint/no-nested-interactive": "error",
      // Regla para evitar estilos en linea
      "@html-eslint/no-inline-styles": "error",
      // Regla para agregar un type a los botones
      "@html-eslint/require-button-type": "error",
      // Regla para agregar meta-description
      "@html-eslint/require-meta-description": "error",
      // Regla para evitar saltos entre los encabezados
      "@html-eslint/no-skip-heading-levels": "error",
      // Regla para agregar method en los formularios
      "@html-eslint/require-form-method": "error",
      // Desactivar regla para evitar saltos de línea en los atributos
      "@html-eslint/attrs-newline": "off",
      // Regla para agregar camelCase en los id
      "@html-eslint/id-naming-convention": ["error", "camelCase"],
      // Regla para configurar el tabulador
      "@html-eslint/indent": ["error", 2],
      // Regla para evitar mayúsculas en las etiquetas y atributos
      "@html-eslint/lowercase": "error",
      // Regla para evitar múltiples saltos de linea
      "@html-eslint/no-multiple-empty-lines": "error",
      // Regla para evitar espacios al final de una linea
      "@html-eslint/no-trailing-spaces": "error",
      // Regla para ordenar los atributos alfabeticamente, pero dando prioridad a algunos atributos
      "@html-eslint/sort-attrs": ["error", {"priority": ["id", "class", "rel", "type", "name", "src", "href"]}]
    }
  }
```
