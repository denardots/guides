# Guía de Instalación de Stylelint

Para que nuestro código sea más limpio y eficiente es importante trabajar con linters.

Un linter es una convención de reglas de desarrollo que permitirá que nuestro proyecto sea mas legible, eficiente y escalable.

Para instalar Stylelint es necesario tener un proyecto creado con Vite.

## Instalación de Stylelint

1. Agregamos el siguiente comando en la terminal

```bash
  npm install stylelint stylelint-config-standard --save-dev
```

2. Luego creamos el archivo ***stylelint.config.js*** en la raíz del proyecto y agregamos el siguiente código:

```js
  export default {
    extends: "stylelint-config-standard"
  };
```

3. Si queremos agregar reglas extra, debemos agregar las siguientes reglas al archivo ***stylelint.config.js***.

```js
  export default {
    extends: "stylelint-config-standard",
    rules: {
      // Regla para evitar animaciones no declaradas
      "no-unknown-animations": true,
      // Regla para evitar media queries no declaradas
      "no-unknown-custom-media": true,
      // Regla para evitar propiedades o variables no declaradas
      "no-unknown-custom-properties": true,
      // Regla para agregar una lista de propiedades requeridas para una regla
      "at-rule-property-required-list": {"font-face": ["font-display", "font-family", "font-style"]},
      // Regla para evitar nombres de colores
      "color-named": "never",
      // Regla para evitar declaraciones !important
      "declaration-no-important": true,
      // Desactivar regla para evitar saltos de linea en los comentarios
      "comment-empty-line-before": null,
      // Regla para evitar saltos de linea en las propiedades
      "custom-property-empty-line-before": "never",
      // Regla para evitar saltos de linea en las reglas especiales
      "at-rule-empty-line-before": "never",
      // Regla para evitar saltos de linea en las reglas clásicas
      "rule-empty-line-before": "never",
      // Regla para agregar comillas en los nombres de las fuentes
      "font-family-name-quotes": "always-unless-keyword"
    }
  };
```
