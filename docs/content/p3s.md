
# **Solución a los Ejercicios**

## Ejercicios Básicos

```javascript
function saludar(nombre) {
    return `¡Hola, ${nombre}!`;
}

const sumar = function(a, b) {
    return a + b;
};

const duplicar = x => x * 2;

function esPar(numero) {
    return numero % 2 === 0;
}

function saludarConDefault(nombre, saludo = "Hola") {
    return `${saludo}, ${nombre}`;
}

const mensaje = () => "¡JavaScript es genial!";

(function() {
    console.log("¡Soy una IIFE!");
})();

## Ejercicios Intermedios

const sumarArray = function(arr) {
    return arr.reduce((total, num) => total + num, 0);
};

function multiplicar(...numeros) {
    return numeros.reduce((total, num) => total * num, 1);
}

function crearContador() {
    let contador = 0;
    return function() {
        contador++;
        return contador;
    };
}

const calculadora = {
    sumar: function(a, b) {
        return a + b;
    },
    restar: (a, b) => a - b
};

const factorial = function calcularFactorial(n) {
    if (n === 0) return 1;
    return n * calcularFactorial(n - 1);
};

const filtrarMayores = arr => arr.filter(num => num > 10);

function calcularArea(base = 1, altura = 1) {
    return base * altura;
}

## Ejercicios Avanzados

function procesar(arr, callback) {
    return arr.map(callback);
}

function crearSaludo(saludoBase) {
    return function(nombre) {
        return `${saludoBase}, ${nombre}`;
    };
}

(function(a, b) {
    return a + b;
})(3, 5);

const persona = {
    nombre: "",
    presentarse: () => `Mi nombre es ${persona.nombre}`
};

function promedio(...numeros) {
    if (numeros.length === 0) return 0;
    return numeros.reduce((total, num) => total + num, 0) / numeros.length;
}

function componer(f, g) {
    return function(x) {
        return g(f(x));
    };
}
```
