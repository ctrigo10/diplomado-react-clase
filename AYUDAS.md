# ⚛️ Guía de React y Arquitectura Web

Referencia técnica sobre conceptos base, patrones de diseño y optimización de rendimiento.

---

## 🛠️ Entorno y Herramientas

### 🔌 Plugins recomendados para VS Code
* **Simple React Snippets**: Atajos rápidos para componentes y hooks.
* **ES7 + React/Redux/React-Native snippets**: Generación automática de estructuras de archivos.

### 🧰 Utilidades
* **[Quicktype.io](https://app.quicktype.io/)**: Convierte JSON a interfaces de TypeScript de forma instantánea.

---

## 🧠 Conceptos de Arquitectura

### 1. SPA (Single Page Application)
React carga un único HTML. La navegación se gestiona mediante JavaScript, lo que permite transiciones instantáneas sin recargar el navegador, ofreciendo una experiencia de aplicación nativa.

### 2. Virtual DOM
Es una representación ligera del DOM real. React realiza un proceso de **Diffing** (comparar cambios) y **Reconciliation** (actualizar solo lo necesario), evitando el costo de rendimiento de manipular el DOM real constantemente.

### 3. Composition Pattern (Patrón de Composición)
En lugar de crear componentes gigantes con muchas "props", se utilizan componentes que aceptan a otros como contenido.
* **Ventaja**: Evita el *Prop Drilling* y hace que los componentes sean altamente reutilizables.
* **Implementación**: Se basa en la prop reservada `{ children }`.



---

## ⚓ Hooks y Lógica Reutilizable

### Hooks de Estado y Efecto
* `useState`: Gestiona el estado local.
* `useEffect`: Ejecuta código basado en cambios en dependencias (sincronización con APIs).
* `useContext`: Accede a datos globales definidos en un Provider.

### Custom Hooks
Son funciones que comienzan con la palabra `use`. Permiten extraer lógica compleja de un componente para que pueda ser reutilizada en otros, manteniendo el componente visual limpio.

### Portals (Portales)
`ReactDOM.createPortal` permite renderizar un componente en un nodo del DOM que está fuera de la jerarquía del componente padre.
* **Uso común**: Modales, Tooltips y menús flotantes que deben evitar problemas de `z-index` o `overflow: hidden`.

---

## ⚡ Optimización y Memorización

Para evitar renderizados innecesarios que afecten la fluidez de la app:

* **`React.memo`**: Es un HOC (Componente de Orden Superior) que memoriza un componente. Solo se vuelve a renderizar si sus **props** cambian.
* **`useMemo`**: Memoriza el **resultado** de un cálculo costoso. Solo se vuelve a ejecutar si sus dependencias cambian.
* **`useCallback`**: Memoriza una **instancia de función**. Evita que se cree una función nueva en cada render, lo cual es vital cuando pasamos funciones a hijos optimizados con `memo`.

---

## 🌐 Estrategias de Renderizado (Rendering Patterns)

| Estrategia | SEO | Velocidad Inicial | Caso de Uso |
| :--- | :--- | :--- | :--- |
| **CSR** (Client) | ❌ Bajo | 🐢 Lenta | Dashboards y aplicaciones privadas. |
| **SSR** (Server) | ✅ Alto | 🟡 Media | E-commerce y sitios de noticias. |
| **SSG** (Static) | ✅ Alto | 🚀 Ultra Rápida | Blogs y landing pages. |
| **ISR** (Incremental) | ✅ Alto | 🚀 Ultra Rápida | Grandes catálogos con datos dinámicos. |

---