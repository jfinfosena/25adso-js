# Tipos de datos y operadores básicos en JavaScript

### **1. Tipos de datos en JavaScript**

JavaScript es un lenguaje dinámicamente tipado, lo que significa que las variables no están vinculadas a un tipo de dato específico y pueden cambiar de tipo durante la ejecución. Los tipos de datos primitivos más comunes son:

- **String**: Representa texto. Se escribe entre comillas simples (`' '`), dobles (`" "`) o backticks (`` ` ``) para plantillas literales.
  ```javascript
  let nombre = "Ana"; // String con comillas dobles
  let saludo = '¡Hola!'; // String con comillas simples
  let mensaje = `Bienvenida, ${nombre}`; // Plantilla literal
  console.log(mensaje); // Imprime: Bienvenida, Ana
  ```

- **Number**: Representa números, ya sean enteros o decimales. No distingue entre `int` y `float`.
  ```javascript
  let edad = 25; // Entero
  let altura = 1.75; // Decimal
  console.log(edad + altura); // Imprime: 26.75
  ```

- **Boolean**: Representa valores de verdad: `true` o `false`. Útil para condiciones.
  ```javascript
  let esMayorDeEdad = true;
  let tienePermiso = false;
  console.log(esMayorDeEdad); // Imprime: true
  ```

- **Null**: Representa la ausencia intencional de un valor.
  ```javascript
  let valorNulo = null;
  console.log(valorNulo); // Imprime: null
  ```

- **Undefined**: Indica que una variable ha sido declarada pero no tiene un valor asignado.
  ```javascript
  let sinDefinir;
  console.log(sinDefinir); // Imprime: undefined
  ```

**Ejemplo práctico**:
```javascript
let nombre = "Carlos"; // String
let edad = 30; // Number
let esEstudiante = true; // Boolean
let direccion = null; // Null
let telefono; // Undefined

console.log("Nombre:", nombre, "Edad:", edad, "Es estudiante:", esEstudiante);
console.log("Dirección:", direccion, "Teléfono:", telefono);
```

### **2. Declaración de variables**

JavaScript ofrece tres formas principales de declarar variables, cada una con un propósito específico:

- **var**: Método antiguo para declarar variables. Tiene alcance de función y permite redeclaración, lo que puede causar errores. No se recomienda usarlo en código moderno.
  ```javascript
  var x = 10;
  var x = 20; // Redeclaración permitida
  console.log(x); // Imprime: 20
  ```

- **let**: Permite declarar variables con alcance de bloque (dentro de `{}`). Se puede reasignar, pero no redeclarar en el mismo ámbito.
  ```javascript
  let y = 15;
  y = 25; // Reasignación permitida
  // let y = 30; // Error: no se puede redeclarar
  console.log(y); // Imprime: 25
  ```

- **const**: Declara constantes con alcance de bloque. No permite reasignación ni redeclaración, pero los objetos o arreglos declarados con `const` pueden modificarse internamente.
  ```javascript
  const PI = 3.1416;
  // PI = 3.14; // Error: no se puede reasignar
  console.log(PI); // Imprime: 3.1416

  const persona = { nombre: "Luis" };
  persona.nombre = "María"; // Modificación interna permitida
  console.log(persona.nombre); // Imprime: María
  ```

**Buenas prácticas**:
- Usa `const` por defecto para evitar reasignaciones accidentales.
- Usa `let` cuando necesites reasignar valores.
- Evita `var` en código moderno.


### **3. Operadores**

Los operadores permiten realizar cálculos, comparaciones y combinaciones lógicas.

#### **Operadores aritméticos**
- `+`: Suma (también concatena strings).
- `-`: Resta.
- `*`: Multiplicación.
- `/`: División.
- `%`: Módulo (resto de la división).

```javascript
let a = 10;
let b = 3;
console.log("Suma:", a + b); // Imprime: 13
console.log("Resta:", a - b); // Imprime: 7
console.log("Multiplicación:", a * b); // Imprime: 30
console.log("División:", a / b); // Imprime: 3.333...
console.log("Módulo:", a % b); // Imprime: 1
```

**Nota sobre `+` con strings**:
```javascript
let texto1 = "Hola";
let texto2 = "Mundo";
console.log(texto1 + " " + texto2); // Imprime: Hola Mundo
```

#### **Operadores de comparación**
- `==`: Compara igualdad de valor (convierte tipos si es necesario).
- `===`: Compara igualdad estricta (valor y tipo).
- `!=`: Desigualdad de valor.
- `!==`: Desigualdad estricta.
- `>`, `<`, `>=`, `<=`: Comparaciones numéricas.

```javascript
let x = 5;
let y = "5";
console.log(x == y); // Imprime: true (convierte el string a número)
console.log(x === y); // Imprime: false (diferente tipo)
console.log(x != y); // Imprime: false
console.log(x !== y); // Imprime: true
console.log(x > 3); // Imprime: true
```

#### **Operadores lógicos**
- `&&`: AND (verdadero si ambos operandos son verdaderos).
- `||`: OR (verdadero si al menos un operando es verdadero).
- `!`: NOT (invierte el valor booleano).

```javascript
let esAdulto = true;
let tieneLicencia = false;
console.log(esAdulto && tieneLicencia); // Imprime: false
console.log(esAdulto || tieneLicencia); // Imprime: true
console.log(!esAdulto); // Imprime: false
```

**Ejemplo combinado**:
```javascript
let num1 = 8;
let num2 = 3;
let esMayor = num1 > num2; // true
let esDivisible = num1 % 2 === 0; // true
console.log(esMayor && esDivisible); // Imprime: true
```

---

## **Objetivo 2: Utilizar entrada de usuario con `prompt`**

### **Entrada de usuario con `prompt`**

La función `prompt` muestra un cuadro de diálogo en el navegador donde el usuario puede ingresar texto. Devuelve un valor de tipo `string` o `null` si el usuario cancela.

```javascript
let nombre = prompt("¿Cuál es tu nombre?");
console.log("Hola, " + nombre); // Imprime el nombre ingresado
```

### **Conversión de tipos**

Dado que `prompt` devuelve un string, es necesario convertir el valor a otro tipo si se requiere, por ejemplo, para operaciones numéricas.

- **Convertir a número**:
  - `parseInt(string)`: Convierte a entero.
  - `parseFloat(string)`: Convierte a decimal.
  - `Number(string)`: Convierte a número (entero o decimal según el caso).

```javascript
let edadStr = prompt("Ingresa tu edad:");
let edad = parseInt(edadStr); // Convierte a entero
console.log("El próximo año tendrás", edad + 1, "años");
```

**Validación básica**:
```javascript
let numeroStr = prompt("Ingresa un número:");
let numero = Number(numeroStr);
if (isNaN(numero)) {
  console.log("Por favor, ingresa un número válido");
} else {
  console.log("El doble de tu número es", numero * 2);
}
```

**Ejemplo práctico**:
Un script que pide dos números y realiza operaciones aritméticas:
```javascript
let num1Str = prompt("Ingresa el primer número:");
let num2Str = prompt("Ingresa el segundo número:");
let num1 = parseFloat(num1Str);
let num2 = parseFloat(num2Str);

if (isNaN(num1) || isNaN(num2)) {
  console.log("Por favor, ingresa números válidos");
} else {
  console.log("Suma:", num1 + num2);
  console.log("Resta:", num1 - num2);
  console.log("Multiplicación:", num1 * num2);
  console.log("División:", num1 / num2);
}
```

---

## **Objetivo 3: Crear scripts interactivos en la consola**

Ahora que hemos cubierto los fundamentos, podemos combinar todos los conceptos para crear scripts interactivos que se ejecuten en la consola del navegador o en un entorno como Node.js (aunque `prompt` es específico del navegador).

### **Ejemplo 1: Calculadora básica**
Este script pide al usuario dos números y una operación, luego muestra el resultado.

```javascript
let num1Str = prompt("Ingresa el primer número:");
let num2Str = prompt("Ingresa el segundo número:");
let operacion = prompt("Ingresa la operación (+, -, *, /):");

let num1 = parseFloat(num1Str);
let num2 = parseFloat(num2Str);
let resultado;

if (isNaN(num1) || isNaN(num2)) {
  console.log("Por favor, ingresa números válidos");
} else {
  if (operacion === "+") {
    resultado = num1 + num2;
  } else if (operacion === "-") {
    resultado = num1 - num2;
  } else if (operacion === "*") {
    resultado = num1 * num2;
  } else if (operacion === "/") {
    if (num2 === 0) {
      console.log("Error: No se puede dividir por cero");
    } else {
      resultado = num1 / num2;
    }
  } else {
    console.log("Operación no válida");
  }

  if (resultado !== undefined) {
    console.log(`Resultado: ${num1} ${operacion} ${num2} = ${resultado}`);
  }
}
```

**Explicación**:
- Usa `prompt` para obtener entrada del usuario.
- Convierte strings a números con `parseFloat`.
- Usa operadores aritméticos y condicionales para procesar la operación.
- Maneja casos de error (números inválidos, división por cero).

### **Ejemplo 2: Verificador de edad**
Un script que pide la edad del usuario y determina si es mayor de edad.

```javascript
const EDAD_MINIMA = 18;
let edadStr = prompt("Ingresa tu edad:");
let edad = parseInt(edadStr);

if (isNaN(edad)) {
  console.log("Por favor, ingresa una edad válida");
} else {
  let esMayor = edad >= EDAD_MINIMA;
  console.log("¿Eres mayor de edad?", esMayor);
  if (esMayor) {
    console.log("¡Puedes entrar!");
  } else {
    console.log("Lo siento, no puedes entrar.");
  }
}
```

**Explicación**:
- Usa `const` para una constante.
- Convierte la entrada a entero con `parseInt`.
- Usa operadores de comparación y lógicos para evaluar la condición.
- Muestra mensajes personalizados según el resultado.

### **Ejemplo 3: Adivina el número**
Un juego interactivo donde el usuario intenta adivinar un número generado aleatoriamente.

```javascript
const numeroSecreto = Math.floor(Math.random() * 10) + 1; // Número entre 1 y 10
let intentos = 0;
let adivinado = false;

while (!adivinado) {
  let intentoStr = prompt("Adivina el número (1-10):");
  let intento = parseInt(intentoStr);
  intentos++;

  if (isNaN(intento)) {
    console.log("Por favor, ingresa un número válido");
  } else if (intento === numeroSecreto) {
    console.log(`¡Felicidades! Adivinaste en ${intentos} intentos.`);
    adivinado = true;
  } else if (intento < numeroSecreto) {
    console.log("El número es mayor. Intenta de nuevo.");
  } else {
    console.log("El número es menor. Intenta de nuevo.");
  }
}
```

**Explicación**:
- Usa `Math.random` y `Math.floor` para generar un número aleatorio.
- Usa un bucle `while` para mantener el juego activo hasta que se adivine.
- Incrementa un contador de intentos (`intentos`).
- Usa operadores de comparación para dar pistas al usuario.

---

## **Resumen de los objetivos cumplidos**

1. **Dominar tipos de datos y operadores**:
   - Explicamos `string`, `number`, `boolean`, `null` y `undefined` con ejemplos.
   - Cubrimos `let`, `const`, `var` y sus diferencias.
   - Detallamos operadores aritméticos, de comparación y lógicos con ejemplos prácticos.

2. **Utilizar `prompt` y conversión de tipos**:
   - Mostramos cómo obtener entrada de usuario con `prompt`.
   - Explicamos cómo convertir strings a números con `parseInt`, `parseFloat` y `Number`.
   - Incluimos validación para manejar entradas inválidas.

3. **Crear scripts interactivos**:
   - Presentamos ejemplos de scripts que combinan entrada de usuario, tipos de datos, operadores y lógica condicional.
   - Los ejemplos (calculadora, verificador de edad, juego de adivinanza) son prácticos y escalables.

---

## **Ejercicio: Procesador de datos personales**

El ejercicio consiste en un programa que pide al usuario información personal (nombre, edad, altura) y realiza operaciones con esos datos, como calcular la edad en meses, comparar valores, y combinar resultados con operadores lógicos. Todo el código se envuelve en un artifact según las instrucciones.

```javascript
// Declaración de variables con diferentes tipos de datos y métodos
const SALUDO_INICIAL = "¡Bienvenido al procesador de datos personales!";
var mensajeFinal = "Procesando tus datos...";
let resultado = null; // Inicialmente null, se asignará después
let sinAsignar; // Undefined por defecto

// Mostrar mensaje inicial
console.log(SALUDO_INICIAL);

// Obtener entrada del usuario con prompt
let nombre = prompt("Ingresa tu nombre:");
let edadStr = prompt("Ingresa tu edad (en años):");
let alturaStr = prompt("Ingresa tu altura (en metros, ej. 1.75):");

// Conversión de tipos para los valores numéricos
let edad = parseInt(edadStr); // Convertir edad a entero
let altura = parseFloat(alturaStr); // Convertir altura a decimal

// Operaciones aritméticas
let edadEnMeses = edad * 12; // Calcular edad en meses
let alturaEnCm = altura * 100; // Convertir metros a centímetros
let sumaEdadAltura = edad + altura; // Suma de edad y altura
let restoEdad = edad % 5; // Resto de dividir edad entre 5

// Operaciones de comparación
let esEdadPar = (edad % 2) === 0; // ¿Es la edad un número par?
let esMayorQueCero = altura > 0; // ¿Es la altura mayor que 0?
let esNombreVacio = nombre === ""; // ¿El nombre está vacío?
let esEdadIgualAltura = edad == altura; // Comparación no estricta

// Operadores lógicos
let combinacionLogica = esEdadPar && esMayorQueCero; // AND: ¿Edad par y altura > 0?
let otraCombinacion = esNombreVacio || esEdadPar; // OR: ¿Nombre vacío o edad par?
let negacion = !esMayorQueCero; // NOT: Negar si altura > 0

// Asignar resultado para evitar null
resultado = sumaEdadAltura;

// Mostrar resultados en la consola
console.log("--- Resultados ---");
console.log("Nombre ingresado:", nombre); // String
console.log("Edad en años:", edad); // Number (entero)
console.log("Altura en metros:", altura); // Number (decimal)
console.log("Edad en meses:", edadEnMeses); // Operación aritmética
console.log("Altura en centímetros:", alturaEnCm); // Operación aritmética
console.log("Suma de edad y altura:", resultado); // Resultado asignado
console.log("Resto de edad ÷ 5:", restoEdad); // Operación módulo
console.log("¿Es la edad par?", esEdadPar); // Comparación
console.log("¿Es la altura mayor que 0?", esMayorQueCero); // Comparación
console.log("¿El nombre está vacío?", esNombreVacio); // Comparación
console.log("¿Edad igual a altura? (no estricta)", esEdadIgualAltura); // Comparación
console.log("Edad par AND altura > 0:", combinacionLogica); // Lógico AND
console.log("Nombre vacío OR edad par:", otraCombinacion); // Lógico OR
console.log("Negación de altura > 0:", negacion); // Lógico NOT
console.log("Valor de variable sin asignar:", sinAsignar); // Undefined
console.log("Mensaje final:", mensajeFinal); // Var

// Nota: No se valida la entrada del usuario para evitar condicionales
```

### **Explicación del ejercicio**

1. **Tipos de datos**:
   - **String**: `SALUDO_INICIAL`, `nombre`, `mensajeFinal`.
   - **Number**: `edad` (entero), `altura` (decimal), `edadEnMeses`, `alturaEnCm`, `sumaEdadAltura`, `restoEdad`.
   - **Boolean**: `esEdadPar`, `esMayorQueCero`, `esNombreVacio`, `esEdadIgualAltura`, `combinacionLogica`, `otraCombinacion`, `negacion`.
   - **Null**: `resultado` inicialmente.
   - **Undefined**: `sinAsignar`.

2. **Declaración de variables**:
   - **const**: `SALUDO_INICIAL` para un mensaje constante.
   - **var**: `mensajeFinal` para mostrar el uso de `var`.
   - **let**: `nombre`, `edad`, `altura`, `resultado`, `sinAsignar` y otras variables que pueden reasignarse o mantenerse sin valor inicial.

3. **Operadores**:
   - **Aritméticos**: `*` para calcular `edadEnMeses` y `alturaEnCm`, `+` para `sumaEdadAltura`, `%` para `restoEdad` y `esEdadPar`.
   - **Comparación**: `===` para `esEdadPar`, `esNombreVacio`, `>` para `esMayorQueCero`, `==` para `esEdadIgualAltura`.
   - **Lógicos**: `&&` para `combinacionLogica`, `||` para `otraCombinacion`, `!` para `negacion`.

4. **Entrada de usuario con `prompt` y conversión de tipos**:
   - Usa `prompt` para obtener `nombre`, `edadStr` y `alturaStr`.
   - Convierte `edadStr` a entero con `parseInt`.
   - Convierte `alturaStr` a decimal con `parseFloat`.

5. **Interactividad en la consola**:
   - El script muestra un mensaje inicial, procesa las entradas del usuario, realiza cálculos y comparaciones, y muestra todos los resultados en la consola.
   - No usa condicionales ni ciclos, por lo que no valida entradas (por ejemplo, si el usuario ingresa texto en lugar de números, el resultado puede ser `NaN`).

### **Cómo ejecutar el ejercicio**

1. Copia el código en un archivo con extensión `.js` (por ejemplo, `procesador_datos_personales.js`).
2. Inclúyelo en un archivo HTML básico para ejecutarlo en un navegador:
   ```html
   <!DOCTYPE html>
   <html>
   <head>
       <title>Ejercicio JavaScript</title>
   </head>
   <body>
       <script src="procesador_datos_personales.js"></script>
   </body>
   </html>
   ```
3. Abre el archivo HTML en un navegador y abre la consola (F12 o clic derecho > Inspeccionar > Consola).
4. Ingresa datos cuando se muestren los cuadros de `prompt` (por ejemplo, "Ana", "25", "1.75").
5. Observa los resultados en la consola.

### **Ejemplo de salida en la consola**
Si el usuario ingresa:
- Nombre: "Ana"
- Edad: "25"
- Altura: "1.75"

La consola mostrará algo como:
```
¡Bienvenido al procesador de datos personales!
--- Resultados ---
Nombre ingresado: Ana
Edad en años: 25
Altura en metros: 1.75
Edad en meses: 300
Altura en centímetros: 175
Suma de edad y altura: 26.75
Resto de edad ÷ 5: 0
¿Es la edad par? false
¿Es la altura mayor que 0? true
¿El nombre está vacío? false
¿Edad igual a altura? (no estricta) false
Edad par AND altura > 0: false
Nombre vacío OR edad par: false
Negación de altura > 0: false
Valor de variable sin asignar: undefined
Mensaje final: Procesando tus datos...
```


## Actividad 1: Ejercicios de variables y Tipos de Datos

### **Ejercicio 1: Procesador de nombre y edad**
**Enunciado**: Escribe un programa que pida al usuario su nombre y edad usando `prompt`. Convierte la edad a un número entero. Calcula la edad en días multiplicando por 365 (constante). Verifica si el nombre tiene menos de 5 caracteres. Usa `var` para la variable del nombre, `let` para la edad y el resultado de la comparación, y `const` para la constante. Declara una variable con valor `null`. Muestra todos los resultados en la consola, incluyendo el nombre, edad en días, si el nombre es corto y el valor nulo.

```javascript
var nombre = prompt("Ingresa tu nombre:"); // String
let edadStr = prompt("Ingresa tu edad:"); // String
const DIAS_POR_ANIO = 365; // Number
let edad = parseInt(edadStr); // Number (entero)
var edadEnDias = edad * DIAS_POR_ANIO; // Operación aritmética
let esNombreCorto = nombre.length < 5; // Comparación
let resultado = null; // Null
console.log("Nombre:", nombre);
console.log("Edad en días:", edadEnDias);
console.log("¿Nombre corto? (<5 caracteres):", esNombreCorto);
console.log("Resultado:", resultado);
```

---

### **Ejercicio 2: Conversor de altura**
**Enunciado**: Crea un script que pida al usuario su altura en metros (ej. 1.75) usando `prompt`. Convierte la entrada a un número decimal. Calcula la altura en centímetros (multiplicando por 100) y en milímetros (multiplicando centímetros por 10). Verifica si la altura es mayor a 1.5 metros (constante). Usa `let` para la altura y conversiones, `var` para la variable de milímetros y una variable sin asignar (`undefined`), y `const` para la constante de referencia. Muestra en la consola la altura en centímetros, milímetros, si es alta y el valor de la variable sin asignar.

```javascript
const ALTURA_REFERENCIA = 1.5; // Number
let alturaStr = prompt("Ingresa tu altura en metros (ej. 1.75):"); // String
let altura = parseFloat(alturaStr); // Number (decimal)
var alturaEnCm = altura * 100; // Operación aritmética
let alturaEnMm = alturaEnCm * 10; // Operación aritmética
let esAlto = altura > ALTURA_REFERENCIA; // Comparación
var sinAsignar; // Undefined
console.log("Altura en centímetros:", alturaEnCm);
console.log("Altura en milímetros:", alturaEnMm);
console.log("¿Es alto? (>1.5m):", esAlto);
console.log("Variable sin asignar:", sinAsignar);
```

---

### **Ejercicio 3: Calculadora de peso**
**Enunciado**: Desarrolla un programa que solicite al usuario su peso en kilogramos con `prompt`. Convierte el peso a un número decimal. Calcula el peso en gramos (multiplicando por 1000). Verifica si el peso es mayor a 70 kg (constante). Usa `var` para la entrada y la comparación, `let` para el peso y los gramos, y `const` para la constante. Crea una combinación lógica con el resultado de la comparación y `true` usando `&&`. Muestra en la consola el peso en gramos, si es mayor a 70 kg y el resultado de la combinación lógica.

```javascript
var pesoStr = prompt("Ingresa tu peso en kg:"); // String
let peso = parseFloat(pesoStr); // Number (decimal)
const PESO_REFERENCIA = 70; // Number
let pesoEnGramos = peso * 1000; // Operación aritmética
var esPesado = peso > PESO_REFERENCIA; // Comparación
let combinacionLogica = esPesado && true; // Operador lógico
console.log("Peso en gramos:", pesoEnGramos);
console.log("¿Peso mayor a 70 kg?:", esPesado);
console.log("Combinación lógica (esPesado AND true):", combinacionLogica);
```

---

### **Ejercicio 4: Procesador de texto**
**Enunciado**: Escribe un script que pida al usuario un texto con `prompt`. Concatena el texto con un saludo constante ("¡Tu texto es: "). Verifica si el texto tiene más de 10 caracteres. Usa `const` para el saludo, `let` para el texto y la comparación, y `var` para la concatenación y una variable con valor `null`. Aplica un operador lógico `!` para negar el resultado de la comparación. Muestra en la consola el texto completo, si es largo, la negación y el valor nulo.

```javascript
const SALUDO = "¡Tu texto es: "; // String
let texto = prompt("Ingresa un texto:"); // String
var textoCompleto = SALUDO + texto; // Concatenación
let esTextoLargo = texto.length > 10; // Comparación
let negacion = !esTextoLargo; // Operador lógico
var valorNulo = null; // Null
console.log(textoCompleto);
console.log("¿Texto largo? (>10 caracteres):", esTextoLargo);
console.log("Negación de texto largo:", negacion);
console.log("Valor nulo:", valorNulo);
```

---

### **Ejercicio 5: Calculadora de área**
**Enunciado**: Crea un programa que solicite al usuario el ancho y alto de un rectángulo con `prompt`. Convierte ambas entradas a números decimales. Calcula el área (ancho * alto). Verifica si el área es mayor a 50 (constante). Usa `let` para las entradas y la comparación, `var` para el ancho y una variable sin definir (`undefined`), y `const` para la constante. Muestra en la consola el área, si es mayor a 50 y el valor de la variable sin definir.

```javascript
let anchoStr = prompt("Ingresa el ancho del rectángulo:"); // String
let altoStr = prompt("Ingresa el alto del rectángulo:"); // String
var ancho = parseFloat(anchoStr); // Number
let alto = parseFloat(altoStr); // Number
const AREA_REFERENCIA = 50; // Number
var area = ancho * alto; // Operación aritmética
let esAreaGrande = area > AREA_REFERENCIA; // Comparación
let sinDefinir; // Undefined
console.log("Área del rectángulo:", area);
console.log("¿Área mayor a 50?:", esAreaGrande);
console.log("Variable sin definir:", sinDefinir);
```

---

### **Ejercicio 6: Conversor de tiempo**
**Enunciado**: Desarrolla un script que pida al usuario una cantidad de horas con `prompt`. Convierte la entrada a un número decimal. Calcula los minutos (horas * 60) y los segundos (minutos * 60). Verifica si la cantidad de horas es mayor a 1. Usa `var` para las horas y los segundos, `let` para los minutos y la comparación, y `const` para las constantes de conversión. Muestra en la consola los minutos, segundos y si es mayor a 1 hora.

```javascript
var horasStr = prompt("Ingresa una cantidad de horas:"); // String
let horas = parseFloat(horasStr); // Number
const MINUTOS_POR_HORA = 60; // Number
const SEGUNDOS_POR_MINUTO = 60; // Number
let minutos = horas * MINUTOS_POR_HORA; // Operación aritmética
var segundos = minutos * SEGUNDOS_POR_MINUTO; // Operación aritmética
let esMasDeUnaHora = horas > 1; // Comparación
console.log("Minutos:", minutos);
console.log("Segundos:", segundos);
console.log("¿Más de 1 hora?:", esMasDeUnaHora);
```

---

### **Ejercicio 7: Comparador de números**
**Enunciado**: Escribe un programa que solicite al usuario dos números con `prompt`. Convierte las entradas a números decimales. Calcula la suma y la diferencia de los números. Verifica si los números son estrictamente iguales (`===`). Usa `let` para los números y la comparación, `var` para las entradas y la suma, y `const` para el resultado de la comparación. Aplica un operador lógico `||` con el resultado de la comparación y `false`. Muestra en la consola la suma, diferencia, si son iguales y el resultado de la combinación lógica.

```javascript
let num1Str = prompt("Ingresa el primer número:"); // String
var num2Str = prompt("Ingresa el segundo número:"); // String
let num1 = parseFloat(num1Str); // Number
let num2 = parseFloat(num2Str); // Number
var suma = num1 + num2; // Operación aritmética
let diferencia = num1 - num2; // Operación aritmética
const sonIguales = num1 === num2; // Comparación estricta
let combinacionLogica = sonIguales || false; // Operador lógico
console.log("Suma:", suma);
console.log("Diferencia:", diferencia);
console.log("¿Son iguales? (estrictamente):", sonIguales);
console.log("Combinación lógica (sonIguales OR false):", combinacionLogica);
```

---

### **Ejercicio 8: Procesador de distancia**
**Enunciado**: Crea un script que pida al usuario una distancia en kilómetros con `prompt`. Convierte la entrada a un número decimal. Calcula la distancia en metros (kilómetros * 1000) y centímetros (metros * 100). Verifica si la distancia es menor a 1 km. Usa `const` para la constante de conversión, `let` para la distancia y los metros, y `var` para la comparación y una variable con valor `null`. Muestra en la consola los metros, centímetros, si es menor a 1 km y el valor nulo.

```javascript
const METROS_POR_KM = 1000; // Number
let distanciaStr = prompt("Ingresa una distancia en km:"); // String
var distancia = parseFloat(distanciaStr); // Number
let metros = distancia * METROS_POR_KM; // Operación aritmética
let centimetros = metros * 100; // Operación aritmética
var esCorta = distancia < 1; // Comparación
let valorNulo = null; // Null
console.log("Metros:", metros);
console.log("Centímetros:", centimetros);
console.log("¿Distancia menor a 1 km?:", esCorta);
console.log("Valor nulo:", valorNulo);
```

---

### **Ejercicio 9: Calculadora de precio**
**Enunciado**: Desarrolla un programa que solicite al usuario el precio de un producto con `prompt`. Convierte la entrada a un número decimal. Calcula el precio con un descuento del 10% (constante). Verifica si el precio original es mayor a 100. Usa `var` para la entrada y la comparación, `let` para el precio, el precio con descuento y la negación, y `const` para el descuento. Aplica un operador lógico `!` para negar el resultado de la comparación. Declara una variable `undefined`. Muestra en la consola el precio con descuento, si es mayor a 100, la negación y el valor sin asignar.

```javascript
var precioStr = prompt("Ingresa el precio del producto:"); // String
let precio = parseFloat(precioStr); // Number
const DESCUENTO = 0.1; // Number (10%)
let precioDescuento = precio - (precio * DESCUENTO); // Operación aritmética
var esCaro = precio > 100; // Comparación
let negacion = !esCaro; // Operador lógico
let sinAsignar; // Undefined
console.log("Precio con descuento:", precioDescuento);
console.log("¿Precio mayor a 100?:", esCaro);
console.log("Negación de precio caro:", negacion);
console.log("Variable sin asignar:", sinAsignar);
```

---

### **Ejercicio 10: Procesador de datos personales**
**Enunciado**: Escribe un script que pida al usuario su nombre, edad y peso con `prompt`. Convierte la edad a un número entero y el peso a un número decimal. Calcula la edad en meses (edad * 12, constante) y el peso en gramos (peso * 1000). Verifica si el nombre está vacío (`=== ""`) y si la edad es par (`% 2 === 0`). Usa `let` para el nombre, edad, peso y comparaciones, `var` para las entradas de edad y los gramos, y `const` para la constante. Aplica un operador lógico `||` para combinar las comparaciones. Muestra en la consola el nombre, edad en meses, peso en gramos, si el nombre está vacío, si la edad es par y el resultado de la combinación lógica.

```javascript
let nombre = prompt("Ingresa tu nombre:"); // String
var edadStr = prompt("Ingresa tu edad:"); // String
let pesoStr = prompt("Ingresa tu peso en kg:"); // String
let edad = parseInt(edadStr); // Number
const MESES_POR_ANIO = 12; // Number
let edadEnMeses = edad * MESES_POR_ANIO; // Operación aritmética
var pesoEnGramos = parseFloat(pesoStr) * 1000; // Operación aritmética
let esNombreVacio = nombre === ""; // Comparación
let esEdadPar = (edad % 2) === 0; // Comparación
let combinacionLogica = esNombreVacio || esEdadPar; // Operador lógico
console.log("Nombre:", nombre);
console.log("Edad en meses:", edadEnMeses);
console.log("Peso en gramos:", pesoEnGramos);
console.log("¿Nombre vacío?:", esNombreVacio);
console.log("¿Edad par?:", esEdadPar);
console.log("Nombre vacío OR edad par:", combinacionLogica);
```

---

### **Instrucciones para resolver los ejercicios**

1. **Preparación**:
   - Copia el código de cada ejercicio en un archivo con extensión `.js` (por ejemplo, `procesador_nombre_edad.js`).
   - Crea un archivo HTML básico para ejecutarlo en un navegador:
     ```html
     <!DOCTYPE html>
     <html>
     <head>
         <title>Ejercicio JavaScript</title>
     </head>
     <body>
         <script src="nombre_del_archivo.js"></script>
     </body>
     </html>
     ```
   - Abre el archivo HTML en un navegador y accede a la consola (F12 o clic derecho > Inspeccionar > Consola).

2. **Ejecución**:
   - Sigue las indicaciones del enunciado de cada ejercicio.
   - Ingresa datos en los cuadros de `prompt` que aparecen (por ejemplo, un nombre, un número para la edad, etc.).
   - Observa los resultados en la consola para verificar que el script funciona como se describe.

3. **Práctica adicional**:
   - Modifica las constantes (por ejemplo, cambia `DIAS_POR_ANIO` o `DESCUENTO`) para experimentar con diferentes valores.
   - Cambia los operadores de comparación (por ejemplo, de `>` a `<`) o lógicos (de `&&` a `||`) para ver cómo afectan los resultados.
   - Ingresa diferentes tipos de datos (por ejemplo, texto en lugar de números) para observar cómo el script maneja entradas inválidas (puede producir `NaN`).

4. **Notas importantes**:
   - Los ejercicios no incluyen validación de entradas porque no se permiten condicionales ni ciclos, según las restricciones.
   - Cada ejercicio usa una combinación de `var`, `let` y `const` para reforzar sus diferencias (por ejemplo, `const` para valores fijos, `let` para valores convertidos, `var` para entradas).
   - Se cubren todos los tipos de datos: `string` (entradas de `prompt`), `number` (valores convertidos y cálculos), `boolean` (resultados de comparaciones), `null` (variables inicializadas como nulas) y `undefined` (variables sin valor).
   - Los operadores incluyen aritméticos (`+`, `-`, `*`, `%`), de comparación (`>`, `<`, `===`, `<`), y lógicos (`&&`, `||`, `!`).

### **Ejemplo de salida (Ejercicio 10)**
Si el usuario ingresa:
- Nombre: "Ana"
- Edad: "24"
- Peso: "60"

La consola mostrará:
```
Nombre: Ana
Edad en meses: 288
Peso en gramos: 60000
¿Nombre vacío?: false
¿Edad par?: true
Nombre vacío OR edad par: true
```

---
