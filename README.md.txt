Dashboard Administrativo Responsive con Flexbox

1. Descripción del trabajo.

Este trabajo consiste en el desarrollo de la interfaz de un Dashboard Administrativo Responsive, tomando como referencia el diseño proporcionado en la actividad práctica.

El objetivo principal es construir la estructura del dashboard utilizando Flexbox como tecnología principal para el layout, evitando el uso de CSS Grid en las secciones principales, de acuerdo con las restricciones establecidas en la actividad.

En esta primera etapa se desarrollaron los siguientes componentes:

- Barra lateral de navegación (Sidebar).
- Logo de AnalyticsPro.
- Menú principal.
- Información del usuario administrador.
- Header superior.
- Botón de menú.
- Título de la sección actual.
- Barra de búsqueda.
- Área de notificaciones.
- Avatar del usuario.
- Área principal preparada para incorporar posteriormente el contenido del dashboard.

2. Tecnologías utilizadas

El trabajo utiliza las siguientes tecnologías:

HTML5

Se utiliza para definir la estructura y los diferentes elementos que conforman la interfaz del dashboard.

CSS3

Se utiliza para desarrollar el diseño visual, distribución de elementos, tamaños, colores, efectos, estados "hover" y comportamiento responsive.

Flexbox

Flexbox es la tecnología principal utilizada para controlar la distribución de los elementos.

Se utiliza principalmente en:

- Layout general.
- Sidebar.
- Menú de navegación.
- Header.
- Buscador.
- Información del usuario.
- Botones e iconos.
- Distribución responsive.

Font Awesome

Los iconos utilizados en la interfaz provienen de Font Awesome, cargado mediante CDNJS.

Ejemplos de iconos utilizados:

- Usuarios.
- Proyectos.
- Reportes.
- Configuración.
- Ayuda.
- Notificaciones.
- Buscador.
- Menú hamburguesa.

Google Fonts

Se utiliza la fuente Inter, debido a que proporciona una apariencia moderna y adecuada para interfaces administrativas y dashboards.

---

3. Estructura del proyecto

La estructura actual del proyecto es:

dashboard-flexbox/
│
├── index.html
│
├── README.md
│
└── css/
    └── style.css

"index.html"

Contiene toda la estructura HTML correspondiente al dashboard.

"css/style.css"

Contiene los estilos visuales, propiedades Flexbox y Media Queries utilizadas para hacer responsive la interfaz.

"README.md"

Contiene la documentación, decisiones técnicas y explicación general del proyecto.

---

4. Estructura principal del Dashboard

El dashboard está dividido principalmente en dos elementos:

.dashboard
│
├── .sidebar
│
└── .main-content
       │
       ├── .topbar
       │
       └── .content-area

El contenedor principal utiliza:

.dashboard {
    display: flex;
}

Esto permite colocar el sidebar y el contenido principal horizontalmente.

La distribución obtenida es:

┌───────────────┬───────────────────────────────────────┐
│               │               HEADER                  │
│               ├───────────────────────────────────────┤
│    SIDEBAR    │                                       │
│               │                                       │
│               │           CONTENIDO PRINCIPAL         │
│               │                                       │
│               │                                       │
└───────────────┴───────────────────────────────────────┘

---

5. Uso de Flexbox

Uno de los requisitos principales de la actividad es utilizar correctamente las propiedades:

- "flex-grow"
- "flex-shrink"
- "flex-basis"
- "flex"
- "align-content"
- "order"
- "gap"
- "row-gap"
- "column-gap"

En esta primera etapa ya se utilizan varias de estas propiedades.

---

5.1 Sidebar

El sidebar utiliza:

.sidebar {
    flex: 0 0 245px;
}

Esta propiedad es una forma abreviada de:

flex-grow: 0;
flex-shrink: 0;
flex-basis: 245px;

Decisión técnica

Se utiliza esta configuración porque el sidebar debe conservar un ancho estable en pantallas grandes.

"flex-grow: 0" evita que aumente innecesariamente.

"flex-shrink: 0" evita que se reduzca cuando existe suficiente espacio.

"flex-basis: 245px" establece su tamaño base.

---

6. Contenido principal

El contenido principal utiliza:

.main-content {
    flex: 1 1 auto;
}

Esto permite que el contenido aproveche automáticamente todo el espacio restante después del sidebar.

Equivale aproximadamente a:

flex-grow: 1;
flex-shrink: 1;
flex-basis: auto;

Por esta razón, cuando aumenta el tamaño de la ventana, el contenido principal también aumenta.

---

7. Sidebar

El sidebar utiliza:

display: flex;
flex-direction: column;

Esto permite distribuir verticalmente:

1. Logo.
2. Navegación.
3. Información del usuario.

La información del usuario utiliza:

margin-top: auto;

De esta manera se mantiene automáticamente en la parte inferior del sidebar sin necesidad de utilizar posiciones absolutas.

---

8. Menú de navegación

El menú también utiliza Flexbox:

.sidebar-menu {
    display: flex;
    flex-direction: column;
    gap: 7px;
}

"flex-direction: column" organiza los enlaces verticalmente.

"gap" controla el espacio existente entre cada opción.

Cada enlace utiliza nuevamente Flexbox para alinear el icono y el texto:

.menu-link {
    display: flex;
    align-items: center;
    gap: 15px;
}

Esto permite mantener una alineación uniforme entre todos los elementos del menú.

---

9. Header

El header superior utiliza:

.topbar {
    display: flex;
    align-items: center;
    justify-content: space-between;
}

Gracias a esto se crean dos grupos principales:

IZQUIERDA                         DERECHA

☰  Resumen          [ Buscar... ]   🔔   DR

La parte izquierda contiene:

- Botón hamburguesa.
- Nombre de la sección.

La parte derecha contiene:

- Buscador.
- Notificaciones.
- Avatar.

---

10. Barra de búsqueda

El buscador utiliza Flexbox internamente:

.search-box {
    display: flex;
    align-items: center;
}

El campo de texto utiliza:

.search-box input {
    flex: 1 1 auto;
}

De esta manera el "input" ocupa automáticamente el espacio disponible dentro del buscador.

También se utiliza:

min-width: 0;

para evitar problemas de desbordamiento cuando el espacio disponible disminuye.

---

11. Truncamiento de texto

Uno de los Edge Cases solicitados en la actividad consiste en evitar que textos demasiado largos rompan el diseño.

Para ello se utilizan propiedades como:

white-space: nowrap;
overflow: hidden;
text-overflow: ellipsis;

Por ejemplo:

.user-info strong {
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
}

Si el nombre del usuario fuera demasiado largo, se mostraría de forma similar a:

María López Gonzá...

en lugar de romper el sidebar.

---

12. Centrado de elementos

Los elementos que requieren un centrado perfecto utilizan:

display: flex;
align-items: center;
justify-content: center;

Esta técnica se utiliza en elementos como:

- Avatar.
- Logo.
- Iconos.
- Botón de notificaciones.
- Botón hamburguesa.

Esto permite que los elementos permanezcan correctamente centrados independientemente de pequeñas variaciones de tamaño.

---

13. Diseño Responsive

El proyecto incorpora Media Queries para adaptar la interfaz a diferentes tamaños de pantalla.

Se han considerado principalmente tres escenarios.

Desktop

En pantallas grandes el sidebar mantiene aproximadamente:

flex-basis: 245px;

y muestra:

- Iconos.
- Textos.
- Logo completo.
- Información del administrador.

---

Tablet

Cuando la pantalla es menor a "900px", el sidebar reduce su tamaño:

.sidebar {
    flex-basis: 80px;
}

Además se ocultan algunos textos para aprovechar mejor el espacio disponible.

El menú pasa de:

🏠 Resumen
👥 Usuarios
💼 Proyectos

a una estructura principalmente basada en iconos:

🏠
👥
💼

---

Móvil

Para pantallas menores a "650px", se reduce nuevamente el espacio ocupado por diferentes componentes.

El buscador completo deja de mostrarse y se conserva principalmente su icono.

Esto permite evitar desbordamientos horizontales y mantener accesibles las funciones principales.

---

14. Uso de unidades

El diseño combina unidades como:

px
%
rem

y posteriormente se pueden incorporar funciones como:

clamp()

para hacer que determinados tamaños sean todavía más adaptables.

La intención es evitar depender exclusivamente de dimensiones rígidas y permitir que la interfaz responda correctamente ante diferentes resoluciones.

---

15. Estados interactivos

Aunque actualmente no se utiliza JavaScript, CSS permite proporcionar retroalimentación visual al usuario.

Por ejemplo:

.menu-link:hover

modifica el fondo y desplazamiento de las opciones del menú.

También se utiliza:

.search-box:focus-within

para destacar el buscador cuando el usuario selecciona el campo de texto.

---

16. Restricciones respetadas

Durante el desarrollo se están considerando las restricciones indicadas en la actividad.

No utilizar CSS Grid

La estructura principal se desarrolla utilizando Flexbox.

HTML y CSS separados

El código se mantiene organizado utilizando archivos independientes.

Diseño Responsive

Se utilizan Media Queries para adaptar la interfaz.

Uso de Flexbox

Flexbox constituye la tecnología principal para controlar el layout.

---

17. Edge Cases considerados

Actualmente se han comenzado a trabajar los siguientes casos especiales:

Textos demasiado largos

Se utiliza:

text-overflow: ellipsis;

para evitar que textos extensos rompan las tarjetas o contenedores.

Centrado consistente

Los iconos y elementos visuales utilizan Flexbox para mantenerse centrados.

Reducción de espacio

Se utilizan propiedades como:

min-width: 0;
flex-shrink;
flex-basis;

para controlar correctamente el comportamiento de los elementos cuando disminuye el espacio disponible.

---

18. Funcionalidades pendientes

La zona central del dashboard se encuentra temporalmente vacía.

Posteriormente se desarrollarán las secciones mostradas en el diseño de referencia:

- Tarjetas de estadísticas.
- Usuarios activos.
- Sesiones.
- Conversiones.
- Ingresos.
- Resumen de actividad.
- Gráficos.
- Top proyectos.
- Proyectos recientes.
- Actividad reciente.
- Panel de ayuda.
- Productos destacados.
- Galería horizontal.
- Scroll horizontal con "scroll-snap".

También se incorporarán progresivamente los requisitos restantes relacionados con:

- "order".
- "align-content".
- "row-gap".
- "column-gap".
- Reordenamiento mediante Media Queries.
- Anidamiento de contenedores Flexbox de mínimo tres niveles.

---

19. JavaScript

Por el momento no es necesario utilizar JavaScript, debido a que la primera etapa se concentra en la construcción visual y responsive del dashboard.

Las funcionalidades actuales pueden desarrollarse utilizando únicamente:

HTML + CSS + Flexbox

JavaScript podrá incorporarse posteriormente si se requiere comportamiento dinámico como:

- Abrir y cerrar el sidebar.
- Actualizar estadísticas.
- Controlar sliders.
- Crear gráficos dinámicos.
- Implementar filtros.
- Gestionar notificaciones.

---

20. Ejecución del proyecto

Para ejecutar el proyecto no es necesario instalar dependencias.

Se puede abrir directamente:

index.html

desde el navegador.

También puede utilizarse la extensión Live Server de Visual Studio Code para visualizar automáticamente los cambios realizados durante el desarrollo.

---

21. Compatibilidad

El proyecto está diseñado considerando navegadores modernos compatibles con Flexbox.

Según los requisitos de la actividad, se considera como mínimo:

- Chrome 90 o superior.
- Firefox 88 o superior.
- Safari 14 o superior.
- Microsoft Edge 90 o superior.

---

22. Conclusión

La primera etapa del proyecto establece la estructura principal del Dashboard Administrativo utilizando Flexbox como sistema principal de distribución.

La utilización de propiedades como "flex-grow", "flex-shrink", "flex-basis", "gap", "align-items" y "justify-content" permite construir una interfaz flexible que puede adaptarse progresivamente a diferentes tamaños de pantalla.

Además, la separación entre HTML y CSS facilita el mantenimiento del proyecto y permitirá incorporar las siguientes secciones del dashboard sin modificar completamente la estructura existente.

El desarrollo continuará agregando los componentes del área central y aplicando los requisitos avanzados de Flexbox establecidos en la actividad.