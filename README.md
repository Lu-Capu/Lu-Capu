<h1 align="center">Sebastian Vilchez</h1>

<p align="center">
  Estudiante de Ingeniería de Sistemas · Peru
</p>

<p align="center">
  <a href="https://github.com/Lu-Capu?tab=repositories"><img src="https://img.shields.io/badge/Portafolio-7%20proyectos-61DAFB?style=flat-square" alt="Portafolio"></a>
  <a href="mailto:sebastianvilchez44@gmail.com"><img src="https://img.shields.io/badge/Email-sebastianvilchez44@gmail.com-EA4335?style=flat-square&logo=gmail&logoColor=white" alt="Email"></a>
</p>

---

## Sobre mí

Trabajo en el lado web: React para lo que se ve en el navegador, Python con
Flet cuando la misma interfaz tiene que correr en escritorio y en la web, y
Java cuando el proyecto necesita Swing y base de datos. Me interesa sobre todo
la parte que casi nadie muestra, que es hacer que algo funcione cuando el
navegador se pone en contra: sin permiso de notificaciones, en contexto no
seguro, con la pestaña en segundo plano, o sin backend detrás.

Este repositorio es mi portafolio. Abajo está lo que hice, con los repos y
demos por si quieres verlos funcionando.

---

## ⭐ Proyectos principales

<a href="https://github.com/Lu-Capu/04-To-Do_List">
  <img src="https://img.shields.io/badge/Lista%20de%20Tareas-React%2019%20·%20Vite%20·%20PWA-61DAFB?style=flat-square" alt="Lista de Tareas">
</a>

### [Lista de Tareas · React PWA](https://github.com/Lu-Capu/04-To-Do_List)

Gestor de tareas instalable como aplicación, con recordatorios del navegador
que avisan antes de que algo venza. React 19, Vite, `localStorage`, sin backend.

![React](https://img.shields.io/badge/React-19-61DAFB?style=flat-square&logo=react&logoColor=black)
![Vite](https://img.shields.io/badge/Vite-8-646CFF?style=flat-square&logo=vite&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-ESLint%2010-F7DF1E?style=flat-square&logo=javascript&logoColor=black)

Lo interesante del proyecto está en cómo resuelve los recordatorios:

- **`setTimeout` tiene un techo de 2³¹−1 ms** (~24.8 días) y se congela en
  segundo plano. Cada alarma se agenda por trozos y se reprograma sola al
  dispararse; además, al volver a primer plano la agenda se recalcula entera.
- **Envío en dos rutas:** primero `registration.showNotification()`, que
  sobrevive con la app en segundo plano, y si no hay service worker cae a
  `new Notification()`. El error concreto de cada intento queda visible.
- **Sin avisos duplicados al recargar:** la clave en `localStorage` es el par
  *tarea + timestamp objetivo*, recortado a los últimos 200 registros.
- **`denied` no se puede re-preguntar.** El botón lleva directo a la
  instrucción exacta para desbloquearlo desde el candado del navegador, en vez
  de reintentar y rendirse.
- **PWA de verdad:** Workbox con `autoUpdate`, manifiesto e iconos 192/512.

[**Ver código →**](https://github.com/Lu-Capu/04-To-Do_List)

---

<a href="https://gestorgastos-fronted.vercel.app/">
  <img src="https://img.shields.io/badge/Gestor%20de%20Gastos-Python%20·%20Flet%20·%20Supabase-3FCF8E?style=flat-square" alt="Gestor de Gastos">
</a>

### [Gestor de Gastos · Python + Supabase](https://gestorgastos-fronted.vercel.app/)

Registro de gastos y categorías con login propio, resumen del mes y gráfica de
dona. El mismo código Python corre como app de escritorio y como sitio web:
en el navegador se compila con Pyodide y se despliega en Vercel. No hay
backend propio: el cliente habla directo con Supabase Auth y PostgREST.

![Python](https://img.shields.io/badge/Python-3670A0?style=flat-square&logo=python&logoColor=ffdd54)
![Flet](https://img.shields.io/badge/Flet-0175C2?style=flat-square)
![Supabase](https://img.shields.io/badge/Supabase-3ECF8E?style=flat-square&logo=supabase&logoColor=white)
![Vercel](https://img.shields.io/badge/Vercel-000000?style=flat-square&logo=vercel&logoColor=white)

Lo interesante del proyecto está en cómo sostiene dos plataformas con una sola
base de código:

- **Un transporte HTTP, dos mundos:** `requests` en escritorio y
  `XMLHttpRequest` síncrono en el navegador, porque Pyodide no trae `requests`.
  El cliente Supabase elige en runtime cuál usar.
- **Sin backend propio:** Auth + PostgREST desde el cliente. Lo único que
  viaja es la anon key, que solo sirve encima de RLS.
- **RLS como única capa de seguridad:** la política `propietario` compara
  `auth.uid() = usuario_id` en `SELECT`, `INSERT`, `UPDATE` y `DELETE`, y el
  rol `anon` sin sesión no lee ni escribe. Cada usuario ve solo sus filas.
- **Gráfica con respaldo:** dona con `flet-charts` en escritorio y barras en
  Flet puro en web, importado con `try/except` para que el build de Pyodide no
  se caiga por una dependencia.
- **Mismo repo, dos destinos:** `iniciar_frontend.bat` arranca el escritorio y
  Vercel construye el sitio con `flet publish`.

[**Ver demo en vivo →**](https://gestorgastos-fronted.vercel.app/)
<sub>· el repo `Gestor_Gastos` es privado, el código se comparte a pedido</sub>

---

## Otros proyectos

### [Java-Ejercicios · POO y ESPOO](https://github.com/Lu-Capu/Java-Ejercicios)

147 clases Java con NetBeans, Swing y MySQL, en patrón Modelo / Control /
Vista. 11 sistemas completos, entre ellos un sistema comercial con login,
ventas, ingresos y stock, y dos versiones de un sistema de predios con árbol
binario propio.

![Java](https://img.shields.io/badge/Java-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-00000F?style=flat-square&logo=mysql&logoColor=white)

### [Python-Ejercicios](https://github.com/Lu-Capu/Python-Ejercicios)

14 ejercicios en Python ordenados por dificultad. Los de Tkinter son los que
más interesa mirar:

- **[Calculadora](https://github.com/Lu-Capu/Python-Ejercicios/tree/main/21-Calculadora)** — los botones no calculan por separado, van escribiendo la expresión en una etiqueta y el `=` la resuelve con `eval`. Multiplicar sale como `x` y se cambia por `*` antes de pasarle el texto.
- **[Gestor de usuarios](https://github.com/Lu-Capu/Python-Ejercicios/tree/main/23-GestorBD)** — CRUD sobre SQLite, repartido en `database.py`, `config.py`, `textos.py` y `ui/`. El módulo de datos no importa Tkinter, así que se puede probar sin abrir la ventana.

El resto son ejercicios de lógica y algoritmos del curso.

![Python](https://img.shields.io/badge/Python-3670A0?style=flat-square&logo=python&logoColor=ffdd54)

### [LadingPage · Librería online](https://github.com/Lu-Capu/LadingPage)

Catálogo de libros donde cada botón arma su mensaje de WhatsApp con el título
y el precio ya escritos. HTML, CSS y JavaScript sin dependencias.

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)

### [LandingPage-01 · Tienda gamer](https://github.com/Lu-Capu/LandingPage-01)

Landing de venta y reparación de equipos gamer. Animaciones de entrada con
`IntersectionObserver`, scrollspy y validación nativa del formulario.

### [Maqueta · Plantilla corporativa](https://github.com/Lu-Capu/Maqueta)

La base de la que salieron las dos landings anteriores. BEM, reveal por
`data-*` y degradacion progresiva.

---

## Stack

**Frontend** — React 19, Vite 8, JavaScript, HTML5, CSS3, `vite-plugin-pwa`, Flet (Python)

**Lenguajes** — Java, Python, SQL

**Herramientas** — Apache NetBeans, Visual Studio Code, Git, MySQL, XAMPP, Supabase, Vercel, Draw.io

---

## GitHub Stats

<div align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=Lu-Capu&show_icons=true&theme=tokyonight&hide_border=true&locale=es" alt="GitHub Stats" height="165">
  <img src="https://github-readme-streak-stats.herokuapp.com/?user=Lu-Capu&theme=material-palenight&hide_border=true" alt="Streak Stats" height="165">
</div>

---

<p align="center">
  Si quieres ver los repos completos, están todos aquí: <a href="https://github.com/Lu-Capu?tab=repositories">github.com/Lu-Capu</a>
</p>
