#  Proyecto Astro – Base con Consumo de API

##  Objetivo
Desarrollar una aplicación utilizando **Astro** que consuma una API externa, renderice datos dinámicamente y mantenga una estructura clara y escalable.

---

##  Características
-  Proyecto creado con Astro
-  Consumo de API (fetch)
-  Renderizado dinámico de datos
-  Separación de lógica y presentación
-  Manejo básico de errores
-  Estructura organizada

---

##  Creación del Proyecto
```
npm create astro@latest
cd nombre-del-proyecto
npm install
npm run dev
```
---

##  Estructura del Proyecto
```
src/
  pages/
    index.astro
  components/
  layouts/
  services/
    api.js
```
---

##  Servicio API

Archivo:
src/services/api.js

Ejemplo:
```
export async function getItems() {
  try {
    const response = await fetch('https://api.example.com/items');
    if (!response.ok) throw new Error('Error en la petición');
    return await response.json();
  } catch (error) {
    console.error(error);
    return [];
  }
}
```
---

##  Uso en Astro

Archivo:
src/pages/index.astro

Ejemplo:

---
```
import { getItems } from '../services/api';

const items = await getItems();
---

<html>
  <body>
    <h1>Lista de datos</h1>

    {items.length === 0 ? (
      <p>No hay datos o ocurrió un error</p>
    ) : (
      <ul>
        {items.map(item => (
          <li>{item.nombre}</li>
        ))}
      </ul>
    )}
  </body>
</html>
```
---

##  Flujo de Datos

1. Se realiza petición GET desde el servicio API
2. Astro ejecuta la lógica en el bloque `---`
3. Se renderizan los datos en HTML
4. Se manejan errores mostrando mensajes alternativos

---

##  Validación
-  La API responde correctamente
-  Los datos se renderizan en la página
-  Se manejan errores sin romper la app
-  Código organizado y reutilizable

---

##  Buenas Prácticas
- Separar lógica en `/services`
- Evitar lógica compleja en `.astro`
- Validar siempre `response.ok`
- Manejar errores con try/catch

---

##  Notas Técnicas
- Framework: Astro
- Uso de fetch nativo
- Renderizado en servidor (SSR por defecto en Astro)

---

##  Autor -- Mateo Paez
Proyecto base para consumo de APIs con Astro