# Actividad Práctica: Manipulación del DOM con JavaScript

## Objetivo
Esta actividad tiene como propósito que los estudiantes practiquen los conceptos del **Document Object Model (DOM)** en JavaScript, incluyendo la selección, modificación, creación y eliminación de elementos en una página web. Los estudiantes aplicarán los métodos `getElementById`, `querySelector`, `querySelectorAll`, `innerHTML`, `textContent`, `style`, `createElement`, `appendChild` y `remove` en un ejercicio interactivo.

---

## Instrucciones Generales

1. **Entorno**: Usa un editor de código (como VS Code) y un navegador web para probar tu código.
2. **Archivo base**: Crea un archivo HTML con la estructura inicial proporcionada más abajo.
3. **Tareas**: Completa las tareas descritas, escribiendo el código JavaScript necesario para manipular el DOM.
4. **Validación**: Prueba tu código en el navegador y verifica que cumpla con los requisitos de cada tarea.
5. **Entrega**: Comparte el archivo HTML final con el código JavaScript implementado (puedes usar un enlace a un repositorio o un archivo comprimido).

---

## Archivo Base (HTML)

Copia el siguiente código HTML en un archivo llamado `actividad-dom.html` para usar como base:

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Actividad DOM</title>
  <style>
    .tarea {
      border: 1px solid #ccc;
      padding: 10px;
      margin: 10px 0;
    }
    .item-lista {
      margin: 5px 0;
    }
    button {
      padding: 5px 10px;
      margin: 5px;
    }
  </style>
</head>
<body>
  <h1>Actividad Práctica: Manipulación del DOM</h1>

  <div id="contenedor-tareas">
    <!-- Tarea 1: Modificar texto -->
    <div class="tarea" id="tarea1">
      <h2>Tarea 1: Modificar Texto</h2>
      <p id="texto-inicial">Este es un texto inicial</p>
      <button onclick="modificarTexto()">Cambiar Texto</button>
    </div>

    <!-- Tarea 2: Cambiar estilos -->
    <div class="tarea" id="tarea2">
      <h2>Tarea 2: Cambiar Estilos</h2>
      <div id="caja-estilo">Caja con estilo inicial</div>
      <button onclick="cambiarEstilo()">Cambiar Estilo</button>
    </div>

    <!-- Tarea 3: Añadir elementos -->
    <div class="tarea" id="tarea3">
      <h2>Tarea 3: Añadir Elementos</h2>
      <ul id="lista-dinamica">
        <li class="item-lista">Elemento 1</li>
        <li class="item-lista">Elemento 2</li>
      </ul>
      <button onclick="agregarElemento()">Añadir Elemento</button>
    </div>

    <!-- Tarea 4: Eliminar elementos -->
    <div class="tarea" id="tarea4">
      <h2>Tarea 4: Eliminar Elementos</h2>
      <ul id="lista-eliminar">
        <li class="item-lista">Elemento A</li>
        <li class="item-lista">Elemento B</li>
        <li class="item-lista">Elemento C</li>
      </ul>
      <button onclick="eliminarElemento()">Eliminar Último Elemento</button>
    </div>
  </div>

  <script>
    // Escribe tu código JavaScript aquí
  </script>
</body>
</html>
```

---

## Tareas

### Tarea 1: Modificar Texto
**Objetivo**: Usar `getElementById` y `textContent` para cambiar el contenido de un elemento.

1. Selecciona el elemento con `id="texto-inicial"` usando `getElementById`.
2. Implementa la función `modificarTexto()` para que, al hacer clic en el botón "Cambiar Texto", el contenido del párrafo cambie a: **"¡Texto modificado con éxito!"**.
3. Usa `textContent` para realizar el cambio (no uses `innerHTML`).

**Pista**:
- Usa `document.getElementById('texto-inicial')` para seleccionar el elemento.
- Asigna el nuevo texto con `elemento.textContent = 'nuevo texto'`.

### Tarea 2: Cambiar Estilos
**Objetivo**: Usar `querySelector` y la propiedad `style` para modificar los estilos de un elemento.

1. Selecciona el elemento con `id="caja-estilo"` usando `querySelector`.
2. Implementa la función `cambiarEstilo()` para que, al hacer clic en el botón "Cambiar Estilo", se apliquen los siguientes estilos:
   - Fondo: azul (`backgroundColor: 'blue'`).
   - Color de texto: blanco (`color: 'white'`).
   - Relleno: 15px (`padding: '15px'`).
   - Borde: 2px sólido negro (`border: '2px solid black'`).

**Pista**:
- Usa `document.querySelector('#caja-estilo')` para seleccionar el elemento.
- Modifica las propiedades de estilo con `elemento.style.propiedad = 'valor'`.

### Tarea 3: Añadir Elementos
**Objetivo**: Usar `createElement`, `textContent` y `appendChild` para añadir un nuevo elemento a una lista.

1. Selecciona la lista con `id="lista-dinamica"` usando `querySelector`.
2. Implementa la función `agregarElemento()` para que, al hacer clic en el botón "Añadir Elemento":
   - Cree un nuevo elemento `<li>` con `createElement`.
   - Establezca su contenido de texto a **"Elemento X"** (donde X es el número del nuevo elemento, empezando desde 3).
   - Añada la clase `item-lista` al nuevo elemento usando `classList.add('item-lista')`.
   - Añada el nuevo elemento a la lista con `appendChild`.

**Pista**:
- Usa `document.querySelectorAll('.item-lista')` para contar los elementos existentes y determinar el número del nuevo elemento.
- Crea el elemento con `document.createElement('li')`.
- Añade el elemento con `lista.appendChild(nuevoElemento)`.

### Tarea 4: Eliminar Elementos
**Objetivo**: Usar `querySelectorAll` y `remove` para eliminar un elemento de una lista.

1. Selecciona todos los elementos `<li>` dentro de la lista con `id="lista-eliminar"` usando `querySelectorAll`.
2. Implementa la función `eliminarElemento()` para que, al hacer clic en el botón "Eliminar Último Elemento":
   - Elimine el último `<li>` de la lista.
   - Si no hay elementos en la lista, muestra una alerta con el mensaje: **"No hay más elementos para eliminar"**.

**Pista**:
- Usa `document.querySelectorAll('#lista-eliminar li')` para obtener los elementos.
- Accede al último elemento con `elementos[elementos.length - 1]`.
- Usa `elemento.remove()` para eliminar el elemento.

---

## Solución de Referencia

A continuación, se proporciona una solución de referencia para todas las tareas. Intenta completar las tareas por tu cuenta antes de consultar esta solución.

```javascript
<script>
  // Tarea 1: Modificar Texto
  function modificarTexto() {
    const texto = document.getElementById('texto-inicial');
    texto.textContent = '¡Texto modificado con éxito!';
  }

  // Tarea 2: Cambiar Estilos
  function cambiarEstilo() {
    const caja = document.querySelector('#caja-estilo');
    caja.style.backgroundColor = 'blue';
    caja.style.color = 'white';
    caja.style.padding = '15px';
    caja.style.border = '2px solid black';
  }

  // Tarea 3: Añadir Elementos
  function agregarElemento() {
    const lista = document.querySelector('#lista-dinamica');
    const items = document.querySelectorAll('#lista-dinamica .item-lista');
    const nuevoItem = document.createElement('li');
    nuevoItem.textContent = `Elemento ${items.length + 1}`;
    nuevoItem.classList.add('item-lista');
    lista.appendChild(nuevoItem);
  }

  // Tarea 4: Eliminar Elementos
  function eliminarElemento() {
    const items = document.querySelectorAll('#lista-eliminar li');
    if (items.length > 0) {
      items[items.length - 1].remove();
    } else {
      alert('No hay más elementos para eliminar');
    }
  }
</script>
```

---

## Preguntas de Reflexión
1. ¿Cuál es la diferencia entre `innerHTML` y `textContent`? ¿Por qué usamos `textContent` en la Tarea 1?
2. ¿Qué ventajas tiene `querySelector` frente a `getElementById`? ¿Cuándo usarías uno u otro?
3. ¿Qué sucede si intentas eliminar un elemento de una lista vacía sin validar? ¿Cómo lo manejaste en la Tarea 4?
4. ¿Cómo podrías mejorar esta actividad para que los nuevos elementos añadidos en la Tarea 3 tengan estilos dinámicos?

