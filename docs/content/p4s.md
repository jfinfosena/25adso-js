
## **Actividad: Gestión de Campañas de Marketing Digital**

### **Enunciado**
Una agencia de marketing digital necesita un sistema en JavaScript para gestionar las campañas publicitarias que ejecuta para sus clientes. Cada campaña está formada por un equipo de especialistas (por ejemplo, estratega, redactor, diseñador gráfico). Los estudiantes deben completar una plantilla de código que implemente las siguientes funcionalidades, utilizando los conceptos de arreglos, métodos (`push`, `pop`, `shift`, `unshift`, `slice`, `forEach`, `map`), iteración (bucles y métodos funcionales) y arreglos multidimensionales:

1. Crear y manipular una lista de especialistas disponibles.
2. Usar los métodos `push`, `pop`, `shift`, `unshift`, `slice`, `forEach` y `map` para gestionar los datos.
3. Iterar sobre los datos para generar reportes sobre las campañas.
4. Usar un arreglo multidimensional para representar las campañas y los especialistas asignados.

Los estudiantes deben completar las secciones marcadas con `// TODO` en la plantilla de código, siguiendo las instrucciones específicas en los comentarios.

---

### **Plantilla de Código**

A continuación, se proporciona una plantilla en JavaScript con secciones incompletas (`// TODO`) que los estudiantes deben resolver. La plantilla incluye ejemplos de uso de todos los conceptos solicitados, aplicados al contexto de una agencia de marketing digital.

```javascript
// Creación de arreglos: Lista de especialistas disponibles
let especialistas = [
  { nombre: "Sofía Ramírez", rol: "Estratega" },
  { nombre: "Diego Vargas", rol: "Redactor" },
  { nombre: "Clara Morales", rol: "Diseñadora Gráfica" }
];

// TODO 1: Usar push para añadir un nuevo especialista al final del arreglo
// Añade un especialista con nombre "Lucía Fernández" y rol "Analista de Datos"
// Imprime el arreglo actualizado
// TODO: Escribe tu código aquí

// TODO 2: Usar pop para eliminar el último especialista y almacenarlo en una variable
// Imprime el especialista eliminado y el arreglo actualizado
// TODO: Escribe tu código aquí

// TODO 3: Usar unshift para añadir un especialista al inicio del arreglo
// Añade un especialista con nombre "Mateo González" y rol "Community Manager"
// Imprime el arreglo actualizado
// TODO: Escribe tu código aquí

// TODO 4: Usar shift para eliminar el primer especialista y almacenarlo en una variable
// Imprime el especialista eliminado y el arreglo actualizado
// TODO: Escribe tu código aquí

// TODO 5: Usar slice para extraer una sublista con los primeros dos especialistas
// Almacena la sublista en una variable e imprímela
// TODO: Escribe tu código aquí

// Arreglo multidimensional: Estructura de campañas con especialistas asignados
let campanas = [
  [
    { nombre: "Sofía Ramírez", rol: "Estratega" },
    { nombre: "Diego Vargas", rol: "Redactor" }
  ],
  [
    { nombre: "Clara Morales", rol: "Diseñadora Gráfica" },
    { nombre: "Lucía Fernández", rol: "Analista de Datos" }
  ]
];

// TODO 6: Usar forEach para iterar sobre las campañas y mostrar un reporte
// Para cada campaña, imprime su número (por ejemplo, "Campaña 1") y la lista de especialistas con su rol
// Ejemplo de salida:
// Campaña 1:
// - Sofía Ramírez (Estratega)
// - Diego Vargas (Redactor)
// TODO: Escribe tu código aquí

// TODO 7: Usar un bucle for...of para contar el total de especialistas por campaña
// Imprime el número de especialistas en cada campaña
// Ejemplo de salida:
// Campaña 1 tiene 2 especialistas
// Campaña 2 tiene 2 especialistas
// TODO: Escribe tu código aquí

// TODO 8: Usar map para crear un nuevo arreglo con los nombres de los especialistas en mayúsculas
// Mantén el rol sin cambios y almacena el resultado en una variable
// Imprime el nuevo arreglo
// TODO: Escribe tu código aquí

// TODO 9: Crear una función que genere un reporte completo de las campañas
// La función debe usar un bucle for clásico para iterar sobre las campañas
// Para cada campaña, imprime su número, el total de especialistas y la lista de nombres con sus roles
// Ejemplo de salida:
// Reporte Completo:
// Campaña 1 (2 especialistas):
//   1. Sofía Ramírez - Estratega
//   2. Diego Vargas - Redactor
// TODO: Escribe tu código aquí
```

---

### **Instrucciones para los Estudiantes**

1. **Descarga la plantilla**: Copia el código de `gestion_campanas.js` en tu editor de JavaScript (puedes usar Node.js, un navegador con la consola de desarrollador, o un entorno como VS Code).
2. **Completa los TODOs**: Resuelve cada sección marcada con `// TODO`, siguiendo las instrucciones en los comentarios. Usa los métodos y estructuras indicadas (por ejemplo, `push`, `forEach`, etc.).
3. **Prueba tu código**: Ejecuta el script y verifica que la salida en la consola coincida con los ejemplos proporcionados en los comentarios.
4. **Requisitos**:
   - Usa los métodos `push`, `pop`, `shift`, `unshift`, `slice`, `forEach` y `map` donde se indique.
   - Asegúrate de que las iteraciones con bucles (`for...of` y `for` clásico) sean correctas.
   - Mantén la estructura del arreglo multidimensional para las campañas.
   - No modifiques las partes del código que no están marcadas con `// TODO`.

---

### **Solución de Referencia (para el Instructor)**

A continuación, se proporciona una solución completa para que el instructor pueda evaluar las respuestas de los estudiantes. Esta solución no debe compartirse con los estudiantes hasta que completen la actividad.

```javascript
// Creación de arreglos: Lista de especialistas disponibles
let especialistas = [
  { nombre: "Sofía Ramírez", rol: "Estratega" },
  { nombre: "Diego Vargas", rol: "Redactor" },
  { nombre: "Clara Morales", rol: "Diseñadora Gráfica" }
];

// TODO 1: Usar push para añadir un nuevo especialista al final del arreglo
especialistas.push({ nombre: "Lucía Fernández", rol: "Analista de Datos" });
console.log("Especialistas tras push:", especialistas);

// TODO 2: Usar pop para eliminar el último especialista y almacenarlo en una variable
let especialistaEliminado = especialistas.pop();
console.log("Especialista eliminado (pop):", especialistaEliminado);
console.log("Especialistas tras pop:", especialistas);

// TODO 3: Usar unshift para añadir un especialista al inicio del arreglo
especialistas.unshift({ nombre: "Mateo González", rol: "Community Manager" });
console.log("Especialistas tras unshift:", especialistas);

// TODO 4: Usar shift para eliminar el primer especialista y almacenarlo en una variable
let primerEspecialista = especialistas.shift();
console.log("Primer especialista eliminado (shift):", primerEspecialista);
console.log("Especialistas tras shift:", especialistas);

// TODO 5: Usar slice para extraer una sublista con los primeros dos especialistas
let subLista = especialistas.slice(0, 2);
console.log("Sublista (slice):", subLista);

// Arreglo multidimensional: Estructura de campañas con especialistas asignados
let campanas = [
  [
    { nombre: "Sofía Ramírez", rol: "Estratega" },
    { nombre: "Diego Vargas", rol: "Redactor" }
  ],
  [
    { nombre: "Clara Morales", rol: "Diseñadora Gráfica" },
    { nombre: "Lucía Fernández", rol: "Analista de Datos" }
  ]
];

// TODO 6: Usar forEach para iterar sobre las campañas y mostrar un reporte
console.log("Reporte de campañas:");
campanas.forEach((equipo, indice) => {
  console.log(`Campaña ${indice + 1}:`);
  equipo.forEach(especialista => {
    console.log(`- ${especialista.nombre} (${especialista.rol})`);
  });
});

// TODO 7: Usar un bucle for...of para contar el total de especialistas por campaña
for (let equipo of campanas) {
  console.log(`Campaña ${campanas.indexOf(equipo) + 1} tiene ${equipo.length} especialistas`);
}

// TODO 8: Usar map para crear un nuevo arreglo con los nombres de los especialistas en mayúsculas
let nombresMayusculas = especialistas.map(especialista => ({
  nombre: especialista.nombre.toUpperCase(),
  rol: especialista.rol
}));
console.log("Nombres en mayúsculas:", nombresMayusculas);

// TODO 9: Crear una función que genere un reporte completo de las campañas
function generarReporteCompleto(campanas) {
  console.log("Reporte Completo:");
  for (let i = 0; i < campanas.length; i++) {
    console.log(`Campaña ${i + 1} (${campanas[i].length} especialistas):`);
    campanas[i].forEach((especialista, j) => {
      console.log(`  ${j + 1}. ${especialista.nombre} - ${especialista.rol}`);
    });
  }
}
generarReporteCompleto(campanas);
```

---

### **Salida Esperada**

La salida en la consola debería ser similar a la siguiente:

```
Especialistas tras push: [
  { nombre: 'Sofía Ramírez', rol: 'Estratega' },
  { nombre: 'Diego Vargas', rol: 'Redactor' },
  { nombre: 'Clara Morales', rol: 'Diseñadora Gráfica' },
  { nombre: 'Lucía Fernández', rol: 'Analista de Datos' }
]
Especialista eliminado (pop): { nombre: 'Lucía Fernández', rol: 'Analista de Datos' }
Especialistas tras pop: [
  { nombre: 'Sofía Ramírez', rol: 'Estratega' },
  { nombre: 'Diego Vargas', rol: 'Redactor' },
  { nombre: 'Clara Morales', rol: 'Diseñadora Gráfica' }
]
Especialistas tras unshift: [
  { nombre: 'Mateo González', rol: 'Community Manager' },
  { nombre: 'Sofía Ramírez', rol: 'Estratega' },
  { nombre: 'Diego Vargas', rol: 'Redactor' },
  { nombre: 'Clara Morales', rol: 'Diseñadora Gráfica' }
]
Primer especialista eliminado (shift): { nombre: 'Mateo González', rol: 'Community Manager' }
Especialistas tras shift: [
  { nombre: 'Sofía Ramírez', rol: 'Estratega' },
  { nombre: 'Diego Vargas', rol: 'Redactor' },
  { nombre: 'Clara Morales', rol: 'Diseñadora Gráfica' }
]
Sublista (slice): [
  { nombre: 'Sofía Ramírez', rol: 'Estratega' },
  { nombre: 'Diego Vargas', rol: 'Redactor' }
]
Reporte de campañas:
Campaña 1:
- Sofía Ramírez (Estratega)
- Diego Vargas (Redactor)
Campaña 2:
- Clara Morales (Diseñadora Gráfica)
- Lucía Fernández (Analista de Datos)
Campaña 1 tiene 2 especialistas
Campaña 2 tiene 2 especialistas
Nombres en mayúsculas: [
  { nombre: 'SOFÍA RAMÍREZ', rol: 'Estratega' },
  { nombre: 'DIEGO VARGAS', rol: 'Redactor' },
  { nombre: 'CLARA MORALES', rol: 'Diseñadora Gráfica' }
]
Reporte Completo:
Campaña 1 (2 especialistas):
  1. Sofía Ramírez - Estratega
  2. Diego Vargas - Redactor
Campaña 2 (2 especialistas):
  1. Clara Morales - Diseñadora Gráfica
  2. Lucía Fernández - Analista de Datos
```

---

### **Notas para el Instructor**

- **Objetivo educativo**: Esta actividad refuerza el entendimiento de arreglos, métodos, iteraciones y arreglos multidimensionales en un contexto empresarial realista (gestión de campañas de marketing).
- **Dificultad**: Intermedia. Los estudiantes deben conocer los conceptos básicos de JavaScript (objetos, funciones, arreglos) y estar familiarizados con la sintaxis de los métodos solicitados.
- **Evaluación**:
  - Verifica que los estudiantes usen correctamente los métodos (`push`, `pop`, etc.) y las iteraciones (`forEach`, `for...of`, `for`).
  - Asegúrate de que los arreglos multidimensionales se manejen adecuadamente.
  - Revisa que la salida en la consola sea clara y siga el formato indicado.
- **Extensión opcional**: Pide a los estudiantes que añadan una funcionalidad adicional, como filtrar especialistas por rol (usando `filter`) o calcular el total de especialistas en todas las campañas (usando `reduce`).

Si necesitas ajustar la actividad, añadir más TODOs o cambiar el contexto, ¡avísame!