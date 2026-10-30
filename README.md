<!-- ═══════════════ CABECERA ANIMADA ═══════════════ -->
<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,11,20&height=210&section=header&text=Sebastian%20Vilchez&fontSize=52&fontColor=ffffff&animation=fadeIn&fontAlignY=36&desc=Portafolio%20de%20proyectos&descSize=20&descAlignY=58" alt="Sebastian Vilchez · Portafolio de proyectos" width="100%">

<a href="https://github.com/Lu-Capu">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=500&size=22&duration=3200&pause=900&color=61DAFB&center=true&vCenter=true&width=720&height=48&lines=Estudiante+de+Ingenier%C3%ADa+de+Sistemas+%C2%B7+Per%C3%BA;React+%2B+Vite+%2B+PWA;Python+%2B+Flet+%2B+Supabase;Java+%2B+Swing+%2B+MySQL;Apps+que+funcionan+aunque+el+navegador+se+ponga+en+contra" alt="Texto animado: Estudiante de Ingeniería de Sistemas, React, Python, Java">
</a>

<br>

<a href="https://github.com/Lu-Capu?tab=repositories"><img src="https://img.shields.io/badge/Portafolio-8%20proyectos-61DAFB?style=for-the-badge" alt="Portafolio"></a>
<a href="https://gestorgastos-fronted.vercel.app/"><img src="https://img.shields.io/badge/Demo%20en%20vivo-Gestor%20de%20Gastos-3FCF8E?style=for-the-badge&logo=vercel&logoColor=white" alt="Demo en vivo"></a>
<a href="mailto:sebastianvilchez44@gmail.com"><img src="https://img.shields.io/badge/Email-Escr%C3%ADbeme-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Email"></a>

</div>

---

## 👋 Sobre mí

Trabajo en el lado web: **React** para lo que se ve en el navegador, **Python con
Flet** cuando la misma interfaz tiene que correr en escritorio y en la web, y
**Java** cuando el proyecto necesita Swing y base de datos. Me interesa sobre todo
la parte que casi nadie muestra, que es hacer que algo funcione cuando el
navegador se pone en contra: sin permiso de notificaciones, en contexto no
seguro, con la pestaña en segundo plano, o sin backend detrás.

Este repositorio es mi portafolio. Abajo está lo que hice, con los repos y
demos por si quieres verlos funcionando.

---

## 🧰 Stack

<div align="center">
  <img src="https://skillicons.dev/icons?i=react,vite,js,html,css,python,java,mysql,sqlite,supabase,vercel,git,github,vscode&perline=7" alt="Tecnologías: React, Vite, JavaScript, HTML, CSS, Python, Java, MySQL, SQLite, Supabase, Vercel, Git, GitHub, VS Code">
</div>

<br>

| | |
|---|---|
| **Frontend** | React 19 · Vite 8 · JavaScript · HTML5 · CSS3 · `vite-plugin-pwa` · Flet (Python) |
| **Lenguajes** | Java · Python · SQL |
| **Datos y nube** | MySQL · SQLite · Supabase (Auth + PostgREST + RLS) · Vercel |
| **Herramientas** | Apache NetBeans · Visual Studio Code · Git · XAMPP · Draw.io |

---

## ⭐ Proyectos principales

### ✅ [Lista de Tareas · React PWA](https://github.com/Lu-Capu/04-To-Do_List)

<div align="center">
  <a href="https://github.com/Lu-Capu/04-To-Do_List">
    <img src="assets/gifs/todo-list.gif" alt="Lista de Tareas: vista principal, edición, panel de diagnóstico y versión móvil" width="85%">
  </a>
</div>

Gestor de tareas instalable como aplicación, con recordatorios del navegador
que avisan antes de que algo venza. React 19, Vite, `localStorage`, sin backend.

![React](https://img.shields.io/badge/React-19-61DAFB?style=flat-square&logo=react&logoColor=black)
![Vite](https://img.shields.io/badge/Vite-8-646CFF?style=flat-square&logo=vite&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-ESLint%2010-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![PWA](https://img.shields.io/badge/PWA-Workbox-5A0FC8?style=flat-square)

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

### 💸 [Gestor de Gastos · Python + Supabase](https://gestorgastos-fronted.vercel.app/)

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

<a href="https://gestorgastos-fronted.vercel.app/"><img src="https://img.shields.io/badge/%E2%96%B6%20Ver%20demo%20en%20vivo-3FCF8E?style=for-the-badge" alt="Ver demo en vivo"></a>
<sub>&nbsp;· el repo `Gestor_Gastos` es privado, el código se comparte a pedido</sub>

---

### 🎬 [Descargador Multimedia · Python + Flet + yt-dlp](https://github.com/Lu-Capu/Convertidor_de_Video) <sup>🆕</sup>

App de escritorio para bajar un video como **MP4** o solo el **audio** a partir
de un link. Pegas la URL, eliges el formato y la app lo guarda en una carpeta
local, con una segunda pestaña, **Mis Descargas**, para ver lo que ya bajaste.

![Python](https://img.shields.io/badge/Python-3670A0?style=flat-square&logo=python&logoColor=ffdd54)
![Flet](https://img.shields.io/badge/Flet-1.0-0175C2?style=flat-square)
![yt-dlp](https://img.shields.io/badge/yt--dlp-FF0000?style=flat-square&logo=youtube&logoColor=white)
![FFmpeg](https://img.shields.io/badge/FFmpeg-007808?style=flat-square&logo=ffmpeg&logoColor=white)

- **La interfaz no se congela:** la descarga corre en un hilo (`page.run_thread`)
  mientras el botón y el campo quedan bloqueados y una barra de progreso avisa.
- **Sin instalar FFmpeg a mano:** `static-ffmpeg` agrega los binarios al `PATH`
  al arrancar, así `bestvideo+bestaudio` se une a MP4 sin pasos extra.
- **Dos modos:** video MP4 en la mejor calidad disponible o audio nativo
  (M4A/WebM) sin recodificar.
- **El reproductor vive fuera de las pestañas:** sigue sonando aunque cambies
  de "Descargar" a "Mis Descargas".
- **Resultado siempre visible:** verde si terminó, rojo con el error si falló,
  naranja si falta pegar el link.

[**Ver código →**](https://github.com/Lu-Capu/Convertidor_de_Video)

---

## 🌐 Landing pages · HTML, CSS y JavaScript

Tres proyectos sin dependencias ni build: se abren y funcionan. La **Maqueta**
es la base de la que salieron las otras dos.

<table>
  <tr>
    <td width="40%" valign="top">
      <h3><a href="https://github.com/Lu-Capu/LadingPage">📚 Librería online</a></h3>
      Catálogo de 7 libros donde cada botón arma su mensaje de <b>WhatsApp</b>
      con el título y el precio ya escritos. Los datos se leen del DOM, no se
      duplican en el JavaScript.
      <br><br>
      <img src="https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white" alt="HTML5">
      <img src="https://img.shields.io/badge/CSS_Grid-1572B6?style=flat-square&logo=css3&logoColor=white" alt="CSS Grid">
      <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black" alt="JavaScript">
    </td>
    <td width="60%">
      <a href="https://github.com/Lu-Capu/LadingPage"><img src="assets/gifs/libreria.gif" alt="Librería online: portada, catálogo, nosotros, contacto y móvil" width="100%"></a>
    </td>
  </tr>
  <tr>
    <td width="40%" valign="top">
      <h3><a href="https://github.com/Lu-Capu/LandingPage-01">🎮 Tienda gamer</a></h3>
      Landing de venta y reparación de equipos gamer. Animaciones de entrada con
      <code>IntersectionObserver</code>, <i>scrollspy</i> y validación nativa del
      formulario (<code>checkValidity</code>), sin <code>alert()</code>.
      <br><br>
      <img src="https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white" alt="HTML5">
      <img src="https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white" alt="CSS3">
      <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black" alt="JavaScript">
    </td>
    <td width="60%">
      <a href="https://github.com/Lu-Capu/LandingPage-01"><img src="assets/gifs/tienda-gamer.gif" alt="Tienda gamer: portada, servicios, testimonios, contacto y móvil" width="100%"></a>
    </td>
  </tr>
  <tr>
    <td width="40%" valign="top">
      <h3><a href="https://github.com/Lu-Capu/Maqueta">🏢 Plantilla corporativa</a></h3>
      Cinco secciones listas para reutilizar: BEM, <i>reveal</i> por
      <code>data-*</code>, <code>prefers-reduced-motion</code> respetado y
      degradación progresiva si el navegador no soporta
      <code>IntersectionObserver</code>.
      <br><br>
      <img src="https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white" alt="HTML5">
      <img src="https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white" alt="CSS3">
      <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black" alt="JavaScript">
    </td>
    <td width="60%">
      <a href="https://github.com/Lu-Capu/Maqueta"><img src="assets/gifs/maqueta.gif" alt="Plantilla corporativa: portada, servicios, contacto y móvil" width="100%"></a>
    </td>
  </tr>
</table>

---

## 📚 Proyectos de estudio

### ☕ [Java-Ejercicios · POO y ESPOO](https://github.com/Lu-Capu/Java-Ejercicios)

**147 clases Java** con NetBeans, Swing y MySQL, en patrón Modelo / Control /
Vista. **11 sistemas completos**, entre ellos un sistema comercial con login,
ventas, ingresos y stock, y dos versiones de un sistema de predios con árbol
binario propio.

![Java](https://img.shields.io/badge/Java-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![Swing](https://img.shields.io/badge/Swing-MVC-5382A1?style=flat-square)
![MySQL](https://img.shields.io/badge/MySQL-00000F?style=flat-square&logo=mysql&logoColor=white)

### 🐍 [Python-Ejercicios](https://github.com/Lu-Capu/Python-Ejercicios)

**15 ejercicios** en Python ordenados por dificultad. Los de Tkinter son los que
más interesa mirar:

- **[Calculadora](https://github.com/Lu-Capu/Python-Ejercicios/tree/main/21-Calculadora)** — los botones no calculan por separado, van escribiendo la expresión en una etiqueta y el `=` la resuelve con `eval`. Multiplicar sale como `x` y se cambia por `*` antes de pasarle el texto.
- **[Gestor de usuarios](https://github.com/Lu-Capu/Python-Ejercicios/tree/main/23-GestorBD)** — CRUD sobre SQLite, repartido en `database.py`, `config.py`, `textos.py` y `ui/`. El módulo de datos no importa Tkinter, así que se puede probar sin abrir la ventana.
- **[Gestor de gastos](https://github.com/Lu-Capu/Python-Ejercicios/tree/main/24-GestorDeGastos)** — el mismo problema que el proyecto principal, pero de escritorio con Tkinter y SQLite. Gastos y categorías con integridad en la base (`CHECK(monto > 0)` y `ON DELETE RESTRICT`) y acceso a datos aislado en un `GastosRepository`.

El resto son ejercicios de lógica y algoritmos del curso (Collatz, año bisiesto,
adivina el número, manejo de listas…).

![Python](https://img.shields.io/badge/Python-3670A0?style=flat-square&logo=python&logoColor=ffdd54)
![Tkinter](https://img.shields.io/badge/Tkinter-GUI-3776AB?style=flat-square)
![SQLite](https://img.shields.io/badge/SQLite-003B57?style=flat-square&logo=sqlite&logoColor=white)

---

## 📊 GitHub en números

<div align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=Lu-Capu&show_icons=true&theme=tokyonight&hide_border=true&locale=es" alt="GitHub Stats" height="165">
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Lu-Capu&layout=compact&theme=tokyonight&hide_border=true&locale=es" alt="Lenguajes más usados" height="165">
</div>

<div align="center">
  <img src="https://streak-stats.demolab.com?user=Lu-Capu&theme=tokyonight&hide_border=true&locale=es" alt="Racha de contribuciones" height="165">
</div>

<div align="center">
  <img src="https://github-readme-activity-graph.vercel.app/graph?username=Lu-Capu&theme=tokyo-night&hide_border=true&area=true" alt="Gráfica de actividad" width="95%">
</div>

### 🐍 Mi serpiente se come mis commits

<div align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Lu-Capu/Lu-Capu/output/github-snake-dark.svg">
    <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/Lu-Capu/Lu-Capu/output/github-snake.svg">
    <img alt="Serpiente animada recorriendo mi gráfica de contribuciones" src="https://raw.githubusercontent.com/Lu-Capu/Lu-Capu/output/github-snake.svg" width="100%">
  </picture>
</div>

---

## 📫 Hablemos

Si quieres ver los repos completos, están todos aquí:
**[github.com/Lu-Capu](https://github.com/Lu-Capu?tab=repositories)**.
Para un proyecto, una práctica o simplemente charlar de código, escríbeme.

<div align="center">
  <a href="mailto:sebastianvilchez44@gmail.com"><img src="https://img.shields.io/badge/Email-sebastianvilchez44@gmail.com-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Email"></a>
  <a href="https://github.com/Lu-Capu"><img src="https://img.shields.io/badge/GitHub-Lu--Capu-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub"></a>
</div>

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,11,20&height=120&section=footer" alt="" width="100%">
