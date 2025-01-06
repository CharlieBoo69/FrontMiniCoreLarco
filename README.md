# Frontend - Sistema de Gestión de Gastos

## Descripción
Este es el **frontend** del sistema de gestión de gastos, implementado en **Svelte**. Su función principal es proporcionar una interfaz interactiva donde los usuarios puedan filtrar gastos por rango de fechas, y mostrar los resultados agrupados por departamento junto con los totales.

---

## Características
- Formulario para ingresar un rango de fechas.
- Tabla que muestra los gastos agrupados por departamento y sus respectivos totales.
- Conexión a un backend en .NET Core publicado en Azure.
- Desplegado en **Netlify** para acceso en línea.

---

## Tecnologías Utilizadas
- **Svelte**: Framework frontend para la creación de componentes interactivos.
- **Fetch API**: Para realizar solicitudes al backend.
- **CSS**: Para el diseño y la estructura visual.
- **Netlify**: Para el despliegue de la aplicación.

---

## Configuración Inicial

### 1. Instalación de Dependencias
Asegúrese de tener instalado Node.js. Luego, ejecute los siguientes comandos en el directorio del proyecto:
```bash
npm install
```

### 2. Configuración de la URL del Backend
En el archivo `src/api.js`, asegúrese de actualizar la URL de la API del backend. Por ejemplo:
```javascript
const API_URL = "https://coregastos20250105182941.azurewebsites.net/api";
```

### 3. Inicio del Servidor de Desarrollo
Ejecute el siguiente comando:
```bash
npm run dev
```
Esto iniciará la aplicación en el navegador en `http://localhost:8080`.

---

## Estructura del Proyecto
```
|-- src
    |-- App.svelte         # Componente principal
    |-- api.js             # Configuración de la comunicación con el backend
    |-- styles.css         # Estilos del proyecto
```

---

## Uso
1. Accede a `http://localhost:8080`.
2. Ingresa las fechas en el formulario para filtrar los gastos.
3. Observa los resultados agrupados por departamento y sus totales.

---

## Ejemplo de Solicitud al Backend
La aplicación realiza solicitudes GET al endpoint del backend con el siguiente formato:
```javascript
const response = await fetch(
    `https://coregastos20250105182941.azurewebsites.net/api/gastos/filtrar?fechaInicio=${fechaInicio}&fechaFin=${fechaFin}`
);
const data = await response.json();
```

---

## Despliegue
El frontend está desplegado en **Netlify** para facilitar su acceso en línea. Puedes acceder a la aplicación en la siguiente URL:
```
https://tu-proyecto-en-netlify.netlify.app
```

### Pasos para Desplegar en Netlify
1. Genera una versión de producción de la aplicación:
   ```bash
   npm run build
   ```
2. Sube la carpeta `build` generada a Netlify.
3. Configura la URL del backend en el archivo `api.js` si es necesario.

---

## Contacto
Correo: carlos.larco.escobar@udla.edu.ec
Telefono: 0969424932

