# Barra de Progreso por Días (15 de diciembre → 27 de enero)

Barra de progreso automática que avanza día a día tomando siempre la fecha actual. El período se extiende del **15 de diciembre** al **27 de enero** y se adapta automáticamente al año correcto, incluso cuando cruza de año.

Perfecta para:
- GitHub Pages
- Embebido en Notion
- Uso sin backend
- Un solo archivo HTML (simple y portable)

## 🎯 Comportamiento

- **Inicio:** 15 de diciembre
- **Fin:** 27 de enero
- **Antes del 15/12:** 0%
- **Después del 27/01:** 100%
- El progreso avanza automáticamente cada día
- Cálculo dinámico por año (no queda vencido)
- Funciona correctamente embebido en Notion

## 📁 Estructura del Proyecto
/
├── index.html # HTML + CSS + JavaScript (todo en uno)
└── README.md # documentación

text

No requiere dependencias ni archivos adicionales.

## 🚀 Cómo Usarlo

### 1️⃣ Subir a GitHub Pages
1. Crear un repositorio público en GitHub
2. Agregar el archivo `index.html` en la raíz
3. Ir a **Settings → Pages**
4. Configurar:
   - **Source:** `Deploy from a branch`
   - **Branch:** `main`
   - **Folder:** `/ (root)`
5. Guardar y esperar ~1 minuto

GitHub generará una URL como:
https://tu-usuario.github.io/nombre-del-repo/

text

### 2️⃣ Embebido en Notion
1. Copiar la URL de GitHub Pages
2. En una página de Notion, escribir `/embed`
3. Pegar la URL
4. Ajustar la altura del bloque (250–350 px recomendado)

El JavaScript se ejecuta sin problemas dentro del iframe.

## ⚙️ Cómo Funciona el Cálculo de Fechas

El período se calcula **en función de la fecha actual**, no con fechas fijas:

- **Inicio:** 15 de diciembre
- **Fin:** 27 de enero del año siguiente

El año se determina automáticamente:
- Si HOY está en **diciembre** → usa el año actual
- Si HOY está en **enero** → usa el año anterior como inicio

Esto evita que el progreso quede siempre en 100% cuando pasa el tiempo.

## 🧮 Lógica Simplificada

1. Se obtiene la fecha de hoy
2. Se normaliza a medianoche (00:00)
3. Se calculan:
   - Días totales del período
   - Días transcurridos
4. El valor se limita entre 0 y el total
5. Se calcula el porcentaje
6. Se actualiza la barra y el texto

El cálculo se ejecuta:
- Al cargar la página
- Cada 24 horas automáticamente

## 📝 Texto Mostrado

**Ejemplo:**
Días transcurridos: 5 de 43 (11.6%)

text

Si HOY es 20/12, el progreso ya aparece avanzado correctamente.

## 🛠️ Cómo Modificar el Período

En el archivo `index.html`, buscar este bloque dentro del `<script>`:

```js
const startDate = new Date(year, 11, 15);    // 15 de diciembre
const endDate   = new Date(year + 1, 0, 27); // 27 de enero
📌 Nota sobre los meses en JavaScript: Los meses empiezan en 0:
Enero = 0, Febrero = 1, …, Diciembre = 11
Ejemplo: 10 de marzo → new Date(2025, 2, 10)

🎨 Cómo Personalizar el Diseño
Cambiar color de la barra:

css
.progress-bar {
  background-color: #4caf50;
}
Cambiar altura:

css
.progress-container {
  height: 18px;
}
Cambiar ancho del widget:

css
.container {
  width: 320px;
}


❌ Limitaciones
Notion no ejecuta JavaScript nativo (debe usarse mediante /embed)

Depende de la fecha del sistema que renderiza el iframe

No guarda historial

✅ Casos de Uso
Seguimiento de un período fijo

Progreso visual en Notion

Contador de eventos

Planificación personal

Sprints o ciclos anuales

🔮 Posibles Mejoras Futuras
Mostrar días restantes

Barra circular

Cambiar colores según porcentaje

Modo oscuro automático

Reinicio automático anual configurable

📌 Notas Finales
Este proyecto prioriza:

Simplicidad

Claridad

Robustez

Cero dependencias

Si necesitas extenderlo, se recomienda duplicar el archivo y ajustar fechas o estilos según el caso.
