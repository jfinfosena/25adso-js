# Solución Completa: Gestión de Películas con Mockoon Playground

## Introducción

Esta es la solución completa para la actividad que consiste en interactuar con el endpoint `https://playground.mockoon.com/movies` de Mockoon Playground, utilizando la API `fetch` y la sintaxis `async/await` en JavaScript. La aplicación permite:

- Cargar una lista de películas (GET).
- Crear una nueva película (POST) usando el objeto JSON corregido.
- Actualizar una película existente (PUT).
- Mostrar los resultados en una tabla HTML.
- Manejar errores y mostrar un indicador de carga.

El código está diseñado para ser claro, robusto, y seguir buenas prácticas, incluyendo validaciones de datos, manejo de errores, y una interfaz amigable.

## Descripción del endpoint

El endpoint `https://playground.mockoon.com/movies` soporta:

- **GET**: `https://playground.mockoon.com/movies`
  - Devuelve una lista de películas en formato JSON, por ejemplo:
    ```json
    [
      {
        "id": 1,
        "title": "The Shawshank Redemption",
        "year": 1994,
        "director": "Frank Darabont",
        "genre": "Drama",
        "rating": 9.3,
        "isPopular": true
      },
      ...
    ]
    ```

- **POST**: `https://playground.mockoon.com/movies`
  - Acepta un objeto JSON con los campos `title`, `year`, `director`, `genre`, `rating`, `isPopular`.
  - Devuelve la película creada con un `id` asignado.

- **PUT**: `https://playground.mockoon.com/movies/:id`
  - Actualiza la película con el `id` especificado.
  - Devuelve la película actualizada.

## Solución completa

A continuación, se presenta el código completo para `index.html`, que incluye HTML, CSS y JavaScript.

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Solución: Gestión de Películas</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      padding: 20px;
      max-width: 900px;
      margin: 0 auto;
    }
    h1, h2 {
      color: #333;
    }
    table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 20px;
    }
    th, td {
      border: 1px solid #ddd;
      padding: 10px;
      text-align: left;
    }
    th {
      background-color: #f2f2f2;
      cursor: pointer;
    }
    tr:nth-child(even) {
      background-color: #f9f9f9;
    }
    #error, #exito {
      margin-top: 10px;
      padding: 10px;
      border-radius: 5px;
    }
    #error {
      color: red;
      background-color: #ffe6e6;
    }
    #exito {
      color: green;
      background-color: #e6ffe6;
    }
    #loading {
      color: #007bff;
      font-weight: bold;
      margin-top: 10px;
    }
    button, input[type="submit"] {
      padding: 10px 20px;
      background-color: #007bff;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      margin: 5px;
    }
    button:hover, input[type="submit"]:hover {
      background-color: #0056b3;
    }
    form {
      margin: 20px 0;
      padding: 15px;
      background-color: #f8f8f8;
      border-radius: 5px;
    }
    label {
      display: block;
      margin: 8px 0;
    }
    input[type="text"], input[type="number"] {
      padding: 8px;
      width: 100%;
      max-width: 300px;
      border: 1px solid #ddd;
      border-radius: 4px;
    }
    input[type="checkbox"] {
      margin-left: 10px;
    }
  </style>
</head>
<body>
  <h1>Gestión de Películas</h1>
  <button onclick="cargarPeliculas()">Cargar Películas</button>
  <div id="loading" style="display: none;">Cargando...</div>

  <h2>Crear Nueva Película</h2>
  <form id="form-crear" onsubmit="event.preventDefault(); crearPelicula();">
    <label>Título: <input type="text" id="crear-titulo" required></label>
    <label>Género: <input type="text" id="crear-genero" required></label>
    <label>Director: <input type="text" id="crear-director" required></label>
    <label>Año: <input type="number" id="crear-anio" min="1888" max="2025" required></label>
    <label>Calificación: <input type="number" id="crear-rating" step="0.1" min="0" max="10" required></label>
    <label>Popular: <input type="checkbox" id="crear-popular"></label>
    <input type="submit" value="Crear Película">
  </form>

  <h2>Actualizar Película</h2>
  <form id="form-actualizar" onsubmit="event.preventDefault(); actualizarPelicula();">
    <label>ID: <input type="text" id="actualizar-id" required></label>
    <label>Título: <input type="text" id="actualizar-titulo" required></label>
    <label>Género: <input type="text" id="actualizar-genero" required></label>
    <label>Director: <input type="text" id="actualizar-director" required></label>
    <label>Año: <input type="number" id="actualizar-anio" min="1888" max="2025" required></label>
    <label>Calificación: <input type="number" id="actualizar-rating" step="0.1" min="0" max="10" required></label>
    <label>Popular: <input type="checkbox" id="actualizar-popular"></label>
    <input type="submit" value="Actualizar Película">
  </form>

  <table id="tabla-peliculas">
    <thead>
      <tr>
        <th>ID</th>
        <th>Título</th>
        <th>Género</th>
        <th>Director</th>
        <th>Año</th>
        <th>Calificación</th>
        <th>Popular</th>
      </tr>
    </thead>
    <tbody id="cuerpo-tabla"></tbody>
  </table>
  <div id="exito"></div>
  <div id="error"></div>

  <script>
    // Función auxiliar para mostrar mensajes temporales
    function mostrarMensaje(tipo, mensaje) {
      const div = document.getElementById(tipo);
      div.textContent = mensaje;
      setTimeout(() => div.textContent = '', 5000);
    }

    // Cargar películas (GET)
    async function cargarPeliculas() {
      const tablaCuerpo = document.getElementById('cuerpo-tabla');
      const errorDiv = document.getElementById('error');
      const exitoDiv = document.getElementById('exito');
      const loadingDiv = document.getElementById('loading');

      tablaCuerpo.innerHTML = '';
      errorDiv.textContent = '';
      exitoDiv.textContent = '';
      loadingDiv.style.display = 'block';

      try {
        const respuesta = await fetch('https://playground.mockoon.com/movies', {
          method: 'GET',
          headers: {
            'Accept': 'application/json'
          }
        });
        if (!respuesta.ok) {
          throw new Error(`Error HTTP: ${respuesta.status}`);
        }
        const peliculas = await respuesta.json();
        peliculas.forEach(pelicula => {
          const fila = document.createElement('tr');
          fila.innerHTML = `
            <td>${pelicula.id}</td>
            <td>${pelicula.title}</td>
            <td>${pelicula.genre}</td>
            <td>${pelicula.director}</td>
            <td>${pelicula.year}</td>
            <td>${pelicula.rating}</td>
            <td>${pelicula.isPopular ? 'Sí' : 'No'}</td>
          `;
          tablaCuerpo.appendChild(fila);
        });
        mostrarMensaje('exito', 'Películas cargadas correctamente');
      } catch (error) {
        mostrarMensaje('error', `Error al cargar las películas: ${error.message}`);
      } finally {
        loadingDiv.style.display = 'none';
      }
    }

    // Crear película (POST)
    async function crearPelicula() {
      const tablaCuerpo = document.getElementById('cuerpo-tabla');
      const errorDiv = document.getElementById('error');
      const exitoDiv = document.getElementById('exito');
      const loadingDiv = document.getElementById('loading');

      errorDiv.textContent = '';
      exitoDiv.textContent = '';
      loadingDiv.style.display = 'block';

      try {
        const anio = parseInt(document.getElementById('crear-anio').value);
        if (anio < 1888 || anio > 2025) {
          throw new Error('El año debe estar entre 1888 y 2025');
        }
        const rating = parseFloat(document.getElementById('crear-rating').value);
        if (rating < 0 || rating > 10) {
          throw new Error('La calificación debe estar entre 0 y 10');
        }

        const nuevaPelicula = {
          title: document.getElementById('crear-titulo').value.trim(),
          genre: document.getElementById('crear-genero').value.trim(),
          director: document.getElementById('crear-director').value.trim(),
          year: anio,
          rating: rating,
          isPopular: document.getElementById('crear-popular').checked
        };

        const respuesta = await fetch('https://playground.mockoon.com/movies', {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json',
            'Accept': 'application/json'
          },
          body: JSON.stringify(nuevaPelicula)
        });

        if (!respuesta.ok) {
          throw new Error(`Error HTTP: ${respuesta.status}`);
        }

        const peliculaCreada = await respuesta.json();
        const fila = document.createElement('tr');
        fila.innerHTML = `
          <td>${peliculaCreada.id}</td>
          <td>${peliculaCreada.title}</td>
          <td>${peliculaCreada.genre}</td>
          <td>${peliculaCreada.director}</td>
          <td>${peliculaCreada.year}</td>
          <td>${peliculaCreada.rating}</td>
          <td>${peliculaCreada.isPopular ? 'Sí' : 'No'}</td>
        `;
        tablaCuerpo.appendChild(fila);
        document.getElementById('form-crear').reset();
        mostrarMensaje('exito', 'Película creada correctamente');
      } catch (error) {
        mostrarMensaje('error', `Error al crear la película: ${error.message}`);
      } finally {
        loadingDiv.style.display = 'none';
      }
    }

    // Actualizar película (PUT)
    async function actualizarPelicula() {
      const tablaCuerpo = document.getElementById('cuerpo-tabla');
      const errorDiv = document.getElementById('error');
      const exitoDiv = document.getElementById('exito');
      const loadingDiv = document.getElementById('loading');

      errorDiv.textContent = '';
      exitoDiv.textContent = '';
      loadingDiv.style.display = 'block';

      try {
        const id = document.getElementById('actualizar-id').value.trim();
        const anio = parseInt(document.getElementById('actualizar-anio').value);
        if (anio < 1888 || anio > 2025) {
          throw new Error('El año debe estar entre 1888 y 2025');
        }
        const rating = parseFloat(document.getElementById('actualizar-rating').value);
        if (rating < 0 || rating > 10) {
          throw new Error('La calificación debe estar entre 0 y 10');
        }

        const peliculaActualizada = {
          title: document.getElementById('actualizar-titulo').value.trim(),
          genre: document.getElementById('actualizar-genero').value.trim(),
          director: document.getElementById('actualizar-director').value.trim(),
          year: anio,
          rating: rating,
          isPopular: document.getElementById('actualizar-popular').checked
        };

        const respuesta = await fetch(`https://playground.mockoon.com/movies/${id}`, {
          method: 'PUT',
          headers: {
            'Content-Type': 'application/json',
            'Accept': 'application/json'
          },
          body: JSON.stringify(peliculaActualizada)
        });

        if (!respuesta.ok) {
          throw new Error(`Error HTTP: ${respuesta.status}`);
        }

        await cargarPeliculas(); // Recargar la lista para reflejar los cambios
        document.getElementById('form-actualizar').reset();
        mostrarMensaje('exito', 'Película actualizada correctamente');
      } catch (error) {
        mostrarMensaje('error', `Error al actualizar la película: ${error.message}`);
      } finally {
        loadingDiv.style.display = 'none';
      }
    }
  </script>
</body>
</html>
```

## Características de la solución

1. **Interfaz HTML**:
   - Incluye un botón para cargar películas, formularios para crear y actualizar películas, y una tabla para mostrar los resultados.
   - Los formularios tienen campos para todos los atributos de una película (`title`, `genre`, `director`, `year`, `rating`, `isPopular`).
   - Se agregan `div` para mensajes de éxito (`exito`) y error (`error`), y un indicador de carga (`loading`).

2. **Estilos CSS**:
   - La interfaz es clara y responsiva, con una tabla legible, filas alternadas, y formularios estilizados.
   - Los mensajes de éxito y error tienen colores distintivos (verde y rojo) y desaparecen tras 5 segundos.

3. **Lógica JavaScript**:
   - **GET (`cargarPeliculas`)**: Obtiene la lista de películas y la muestra en la tabla.
   - **POST (`crearPelicula`)**: Envía una nueva película usando los datos del formulario, validando `year` (1888–2025) y `rating` (0–10).
   - **PUT (`actualizarPelicula`)**: Actualiza una película existente usando el ID proporcionado y recarga la tabla.
   - **Validaciones**: Se verifica que los datos sean válidos antes de enviar las solicitudes.
   - **Manejo de errores**: Captura errores de red, HTTP, y validaciones, mostrando mensajes al usuario.
   - **Indicador de carga**: Se muestra durante las solicitudes y se oculta al finalizar.

4. **Uso del objeto JSON corregido**:
   - Para crear la película proporcionada, completa el formulario de creación con:
     - Título: `necessitatibus brevis vicissitudo`
     - Género: `vulgus`
     - Director: `Stewart Kiehn`
     - Año: `1954`
     - Calificación: `7`
     - Popular: `false`
   - La solicitud POST enviará este objeto y la API devolverá la película con un `id` asignado.

5. **Buenas prácticas**:
   - Uso de `async/await` para un código legible.
   - Verificación de `response.ok` en todas las solicitudes.
   - Validaciones de datos antes de enviar solicitudes.
   - Mensajes de usuario claros y temporales.
   - Limpieza de formularios y tabla antes de nuevas operaciones.

## Instrucciones para probar

1. **Guarda el código**:
   - Copia el código en un archivo llamado `index.html`.

2. **Ejecuta la aplicación**:
   - Abre `index.html` en un navegador. Si usas un editor como VS Code, utiliza la extensión Live Server para servir el archivo localmente y evitar problemas de CORS (aunque el endpoint de Mockoon soporta CORS).
   - Alternativamente, sube el archivo a un servidor web o usa un entorno como CodePen (asegurándote de que permita solicitudes externas).

3. **Prueba las funcionalidades**:
   - Haz clic en "Cargar Películas" para ver la lista de películas.
   - Completa el formulario de creación con datos (por ejemplo, los del objeto JSON corregido) y envíalo.
   - Usa el formulario de actualización para modificar una película existente (necesitas un ID válido, obtenido de la lista cargada).
   - Prueba errores, como enviar un ID inválido en PUT o un año fuera de rango.

4. **Verifica la salida**:
   - La tabla mostrará las películas cargadas.
   - Los mensajes de éxito o error aparecerán en los `div` correspondientes.
   - El indicador de carga será visible durante las solicitudes.

## Ejemplo de uso del objeto JSON corregido

Para crear la película proporcionada, usa el formulario de creación con estos valores:

```json
{
  "title": "necessitatibus brevis vicissitudo",
  "genre": "vulgus",
  "director": "Stewart Kiehn",
  "year": 1954,
  "rating": 7,
  "isPopular": false
}
```

La API devolverá una respuesta como:

```json
{
  "id": "nuevo-id-generado",
  "title": "necessitatibus brevis vicissitudo",
  "genre": "vulgus",
  "director": "Stewart Kiehn",
  "year": 1954,
  "rating": 7,
  "isPopular": false
}
```
