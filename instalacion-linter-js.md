# Guía de Instalación de ESLint

Para que nuestro código sea más limpio y eficiente es importante trabajar con linters.

Un linter es una convención de reglas de desarrollo que permitirá que nuestro proyecto sea mas legible, eficiente y escalable.

Para instalar ESLint es necesario tener un proyecto creado con Vite.

## Instalación de ESLint

1. Agregamos el siguiente comando en la terminal

```bash 
  npm install eslint eslint-config-standard eslint-plugin-import --save-dev
```

2. Luego creamos el archivo ***eslint.config.js*** en la raíz del proyecto y agregamos el siguiente código:

```js
  import pluginJs from "@eslint/js";

  export default [
    pluginJs.configs.recommended,
  ];
```

3. Si queremos agregar reglas extra a eslint, debemos agregar las siguientes reglas al archivo ***eslint.config.js***.

```js
  pluginJs.configs.recommended,
  {
    // Configuración para que el linter reconozca el uso de variables globales como document, window y console
    languageOptions: {globals: {document: true, window: true, console: true}},
    rules: {
      // Regla para evitar importaciones duplicadas
      "no-duplicate-imports": "error",
      // Regla para evitar auto comparaciones
      "no-self-compare": "error",
      // Regla para agregar `` en las plantillas
      "no-template-curly-in-string": "error",
      // Regla para evitar modificaciones de variables auxiliares dentro de un bucle
      "no-unmodified-loop-condition": "error",
      // Regla para evitar utilizar variables, funciones o clases antes de ser declaradas
      "no-use-before-define": "error",
      // Regla para evitar asignaciones de variables sin uso
      "no-useless-assignment": "error",
      // Regla para evitar modificaciones de arrays y objetos de forma insegura
      "require-atomic-updates": ["error", {"allowProperties": true}],
      // Regla para agregar getters y setters
      "accessor-pairs": ["error", {"getWithoutSet": true}],
      // Regla para agregar {} en funciones flecha
      "arrow-body-style": ["error", "as-needed"],
      // Regla para evitar el uso de variables fuera del bloque donde fueron declaradas
      "block-scoped-var": "error",
      // Regla para agregar camelCase en las variables
      "camelcase": "error",
      // Regla para agregar this en los métodos de clases
      "class-methods-use-this": "error",
      // Regla para agregar un return en las funciones
      "consistent-return": "error",
      // Regla para agregar {} en los bloques cuando sean necesarios
      "curly": ["error", "multi", "consistent"],
      // Regla para agregar default en los switch
      "default-case": "error",
      // Regla para agregar default al final de los switch
      "default-case-last": "error",
      // Regla para agregar parámetros por defecto al final de las funciones
      "default-param-last": "error",
      // Regla para agregar === y !== en los comparadores
      "eqeqeq": "error",
      // Regla para agregar declaraciones correctas en las funciones
      "func-style": ["error", "declaration", {"allowArrowFunctions": true}],
      // Regla para agregar getter y setter de forma ordenada en las clases
      "grouped-accessor-pairs": ["error", "setBeforeGet"],
      // Regla para evitar nombres de variables cortos
      "id-length": ["error", {"min": 3}],
      // Regla para evitar variables declaradas pero no inicializadas
      "init-declarations": "error",
      // Regla para evitar mas de una clase por archivo
      "max-classes-per-file": "error",
      // Regla para agregar un máximo de 300 líneas por archivo
      "max-lines": ["error", {"max": 300, "skipBlankLines": true, "skipComments": true}],
      // Regla para agregar un máximo de 50 líneas por función
      "max-lines-per-function": ["error", {"max": 30, "skipBlankLines": true, "skipComments": true}],
      // Regla para agregar capitalizaciones en los nombres de las clases
      "new-cap": "error",
      // Regla para evitar alerts
      "no-alert": "error",
      // Regla para evitar funciones vacias
      "no-empty-function": "error",
      // Regla para evitar la función eval
      "no-eval": "error",
      // Regla para evitar this invalidos
      "no-invalid-this": "error",
      // Regla para evitar bloques anidados innecesarios
      "no-lone-blocks": "error",
      // Regla para evitar anidaciones innecesarias en estructuras de control
      "no-lonely-if": "error",
      // Regla para evitar asignaciones multiples de variables
      "no-multi-assign": "error",
      // Regla para evitar multilineas en strings
      "no-multi-str": "error",
      // Regla para evitar el operador de negación en if-else y operadores ternarios
      "no-negated-condition": "error",
      // Regla para evitar operadores ternarios anidados
      "no-nested-ternary": "error",
      // Regla para evitar new fuera de asignaciones
      "no-new": "error",
      // Regla para evitar reasignar parametros en funciones
      "no-param-reassign": "error",
      // Regla para evitar asignaciones de variables en los returns
      "no-return-assign": "error",
      // Regla para evitar el uso incorrecto de comas
      "no-sequences": "error",
      // Regla para evitar el uso incorrecto de throw
      "no-throw-literal": "error",
      // Regla para evitar undefined en la inicialización de variables
      "no-undef-init": "error",
      // Regla para evitar el uso innecesario del operador de concatenación
      "no-useless-concat": "error",
      // Regla para evitar el uso innecesario de constructor
      "no-useless-constructor": "error",
      // Regla para evitar renombrar innecesariamente import, export y desesctructuraciones
      "no-useless-rename": "error",
      // Regla para evitar el uso innecesario de return
      "no-useless-return": "error",
      // Regla para evitar la declaración de variables con var
      "no-var": "error",
      // Regla para agregar shorthands en los objetos
      "object-shorthand": "error",
      // Regla para agregar shorthands en los operadores de comparación
      "operator-assignment": "error",
      // Regla para agregar await en funciones asíncronas
      "require-await": "error",
      // Regla para evitar espacios innecesarios en los arrays
      "array-bracket-spacing": "error",
      // Regla para agregar () en las funciones flecha
      "arrow-parens": ["error", "as-needed"],
      // Regla para agregar espacios necesarios en las funciones flecha
      "arrow-spacing": "error",
      // Regla para evitar el multilinea en {}
      "brace-style": "error",
      // Regla para evitar comas innecesarias
      "comma-dangle": ["error", "never"],
      // Regla para evitar espacios innecesarios en las comas
      "comma-spacing": "error",
      // Regla para evitar comas al inicio de las sentencias
      "comma-style": "error",
      // Regla para evitar espacios innecesarios
      "computed-property-spacing": "error",
      // Regla para colocar el punto en la propiedad en caso de multilinea
      "dot-location": ["error", "property"],
      // Regla para evitar espacios innecesarios en las funciones
      "func-call-spacing": "error",
      // Regla para configurar el tabulador
      "indent": ["error", 2],
      // Regla para evitar espacios innecesarios en los objetos
      "key-spacing": "error",
      // Regla para agregar espacios en las estructuras de control
      "keyword-spacing": "error",
      // Regla para agregar () al instanciar una clase
      "new-parens": "error",
      // Regla para agregar correctamente los decimales
      "no-floating-decimal": "error",
      // Regla para evitar múltiples saltos de linea
      "no-multiple-empty-lines": "error",
      // Regla para evitar await dentro de returns
      "no-return-await": "error",
      // Regla para evitar espacios al final de una linea
      "no-trailing-spaces": "error",
      // Regla para evitar espacios innecesarios en las {} de los objetos
      "object-curly-spacing": "error",
      // Regla para agregar "" en los strings
      "quotes": "error",
      // Regla para agregar ; al final de las sentencias
      "semi": "error",
      // Regla para agregar espacios antes de las {}
      "space-before-blocks": "error",
      // Regla para evitar espacios innecesarios en los ()
      "space-in-parens": "error",
      // Regla para agregar espacios en los operadores
      "space-infix-ops": "error",
      // Regla para agregar multilinea en los switches
      "switch-colon-spacing": "error",
      // Regla para evitar espacios innecesarios en los templates
      "template-curly-spacing": "error"
    }
  },
  // Debajo se encuentran las reglas y configuración de htmleslint
```
