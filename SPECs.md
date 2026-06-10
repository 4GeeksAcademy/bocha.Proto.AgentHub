# Especificaciones del Prototipo — Panel de Administración AgentHub

Necesitamos generar como entregable un prototipo HTML completamente diseñado del panel de administración de nuestro cliente, la plataforma AgentHub. Para ello se deben considerar las especificaciones y el contexto que se detallan a continuación.

---

## 1. Descripción del producto

Nuestro cliente es **AgentHub**, una plataforma SaaS donde las empresas pueden alquilar agentes de inteligencia artificial preconfigurados para realizar tareas específicas.

El panel de administración que debemos prototipar está dirigido al **usuario administrador**, quien necesita:

- Revisar las métricas.
- Realizar la gestión de usuarios.
- Administrar agentes.
- Configurar skills.
- Revisar todas las contrataciones.
- Monitorear los errores del sistema.

El objetivo del panel es ofrecer una interfaz clara, profesional y completamente funcional a nivel visual.

---

## 2. Stack tecnológico y restricciones

### Stack tecnológico

El prototipo debe construirse usando únicamente las siguientes tecnologías:

- **HTML** para la estructura.
- **Tailwind CSS vía CDN** para todos los estilos, incluyendo modo oscuro.
- **JavaScript vanilla** para interacciones (dropdowns, modales, colapsables, toggles).

### Restricciones estrictas

- No se pueden usar frameworks (React, Vue, Angular, Svelte, etc.).
- No se pueden usar herramientas de build (Vite, Webpack, Parcel).
- No se pueden usar archivos CSS personalizados ni estilos inline.
- No habrá backend ni llamadas a API: todos los datos deben estar hardcodeados.
- El panel debe implementarse con un dashboard principal en el `index.html` y luego un archivo HTML por cada sección.
- El modo oscuro debe funcionar usando exclusivamente las utilidades `dark:` de Tailwind.
- El modo elegido debe persistir al navegar entre todas las secciones.

---

## 3. Estructura general

La estructura general está compuesta de tres partes bien determinadas, cuyo tamaño no debe modificarse al navegar entre las secciones.

### 3.1 Barra lateral (sidebar)

- Debe contener los enlaces a las 6 secciones, resaltando la sección activa.
- Debe ser persistente y visible en todo momento.

### 3.2 Barra superior

- Incluir un **toggle de modo claro/oscuro**. Su estado debe persistir en la navegación entre secciones.
- Incluir un **toggle de notificaciones**.
- Incluir una **barra de búsqueda** que no supere el 25% del ancho total.
- Mostrar sobre el lado superior derecho: **imagen de perfil** del usuario logueado y su **nombre**.

### 3.3 Área principal

Zona donde se despliega el contenido de cada una de las 6 secciones principales: Dashboard, Gestión de usuarios, Gestión de agentes, Skills, Contrataciones de agentes y Log de errores.

---

## 4. Especificaciones por sección

### 4.1 Dashboard

La sección del dashboard debe contener:

**Tarjetas de métricas (cuadrícula 2×2 responsive):**

| # | Métrica | Descripción |
|---|---------|-------------|
| a | Ingresos Totales | Ingresos generados en el último mes |
| b | Pérdidas Totales | Pérdidas por descuentos y cupones |
| c | Número de agentes | Agentes activos en la plataforma |
| d | Agentes fallando | Agentes marcados como fallando |

- Cada tarjeta debe tener un **icono**, una **etiqueta** con el nombre de la métrica y un **valor hardcodeado**.
- Usar colores de acento distintos por tipo de métrica, con sombra sutil.

**Gráfico de actividad semanal:**

- Área de ancho completo debajo de las tarjetas.
- Placeholder con borde discontinuo y texto centrado.

---

### 4.2 Gestión de usuarios

Tabla responsive de ancho completo con al menos **5 usuarios hardcodeados**, mostrando:

- Nombre
- Email
- Plan
- Badge de estado

Cada fila debe incluir un **dropdown de acciones** con:

- **Ver detalle** — abre un modal overlay con el registro completo del usuario.
- **Eliminar**

El modal debe cerrarse con el botón de cierre o haciendo clic en el backdrop.

---

### 4.3 Gestión de agentes

Listado responsive con al menos **4 agentes hardcodeados**, mostrando:

- Nombre
- Propietario
- Badge de estado
- Lista de skills (colapsada por defecto)

Al hacer clic en el control expandible, se muestran u ocultan las skills con una **transición suave**.

Cada agente tiene un **dropdown** con:

- **Configurar** — abre un modal con el prompt del agente en un `<textarea>` editable.
- **Eliminar** — abre un cuadro de confirmación solicitando validar la eliminación.

---

### 4.4 Skills

Catálogo de tarjetas responsive con al menos **4 skills hardcodeadas**, cada una mostrando:

- Nombre
- Descripción breve
- Número de agentes que la usan

Incluir una breve explicación de qué es una "skill" en el contexto de AgentHub.

Cada skill tiene un **dropdown** con:

- **Ver detalle**
- **Eliminar**

---

### 4.5 Contrataciones de agentes

Tabla responsive de ancho completo con al menos **4 contratos hardcodeados**, mostrando:

- Cliente
- Agente alquilado
- Skills contratadas
- Fecha de inicio y fin
- Importe pagado

Cada fila tiene un **dropdown** con:

- **Ver detalle** — abre un modal con el desglose completo del contrato:
  - Lista de skills contratadas
  - Precio individual por skill
  - Total pagado

---

### 4.6 Log de errores

Lista responsive de ancho completo con al menos **6 errores hardcodeados**, mostrando:

- Timestamp
- Nombre del agente
- Badge de tipo de error (color según gravedad)
- Descripción breve

Cada entrada tiene un **dropdown** con:

- **Ver detalle** — abre un modal con la traza completa del error.
- **Marcar como resuelto** — abre un cuadro de diálogo solicitando confirmación.

---

## 5. Inventario de componentes reutilizables

- Sidebar persistente
- Barra superior con toggle de modo oscuro
- Tarjeta de métrica
- Dropdown de acciones
- Modal overlay
- Badge de estado o gravedad
- Lista colapsable de skills
- Tabla base reutilizable
- Botones primarios y secundarios

---

## 6. Criterios de aceptación

- El panel incluye las seis secciones solicitadas.
- La sidebar es persistente y muestra la sección activa.
- La barra superior contiene el toggle de modo claro/oscuro.
- El modo oscuro funciona correctamente y persiste entre secciones.
- Todas las tablas contienen la cantidad mínima de datos hardcodeados.
- Todos los dropdowns funcionan correctamente y se cierran al hacer clic fuera.
- Todos los modales funcionan correctamente y se cierran con botón o backdrop.
- Las listas colapsables de skills funcionan con transición suave.
- No hay estilos inline ni archivos CSS externos.
- No se usan frameworks ni herramientas de build.
- El diseño es consistente, limpio y claramente basado en Tailwind.
