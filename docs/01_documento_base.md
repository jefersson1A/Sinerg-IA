# Documentación de Proyecto: Sinerg-IA (Sinergia IA)
## Portal Maestro de Prompting Educativo (Versión Extendida y Plan de Ingeniería)

Este documento constituye una guía técnica, conceptual y de diseño del portal interactivo **Sinergia IA · Portal Maestro de Prompting Educativo** (`Sinergia_IA_v2.html`). Su propósito es proveer una memoria detallada del estado actual de la aplicación, sus fundamentos pedagógicos, su arquitectura técnica, los desafíos de desarrollo y seguridad identificados durante la auditoría del código fuente, así como un plan maestro de optimización técnica y una evaluación epistemológica del material documental que nutre el proyecto.

---

## 1. Objetivos del Proyecto

El proyecto **Sinerg-IA** surge ante la creciente necesidad de capacitar al cuerpo docente en el uso crítico y estructurado de herramientas de Inteligencia Artificial Generativa. En lugar de percibir la IA como un buscador avanzado de respuestas genéricas, el proyecto promueve la cultura del *Prompting de Élite*, en el cual el docente actúa como un programador de lenguaje natural que diseña entornos cognitivos específicos.

### 1.1. Objetivo General
Diseñar y estructurar una aplicación web de página única (Single Page Application - SPA) interactiva, altamente visual y autogestionada que instruya, evalúe y asista a docentes de todos los niveles educativos en el diseño y despliegue de prompts estructurados, adaptando la teoría del *Catálogo de Prompts BIU 2024* y el *Manual Perís 2025* a un formato web inmediato y usable.

### 1.2. Objetivos Específicos
* **Sistematizar la Ingeniería de Prompts Docentes:** Proveer una herramienta visual (Constructor) que traduzca el marco teórico abstracto de la fórmula **RTF** (Rol, Tarea, Formato) en un formulario estructurado con previsualización sintáctica en tiempo real.
* **Reducir la Curva de Aprendizaje:** Facilitar una biblioteca estandarizada y clasificada de 18 plantillas de prompts listas para su personalización, cubriendo las seis áreas prioritarias de la docencia moderna.
* **Fomentar el Pensamiento Crítico Metodológico:** Ofrecer un espacio interactivo de educación mediante pestañas dinámicas que desglosan estrategias cognitivas complejas como *Few-shot prompting*, *Chain of Thought (CoT)* y el *Método Socrático*.
* **Garantizar la Calidad del Output:** Diseñar un checklist interactivo de control de calidad para mitigar el riesgo de alucinaciones de la IA y asegurar la precisión en el aula de clase.
* **Simular un Entorno de Acompañamiento:** Integrar una interfaz de chat con IA (Asistente) que actúe como un tutor personalizado en ingeniería de prompts para los docentes.

---

## 2. Alcance del Proyecto

El alcance del proyecto se enmarca dentro de un prototipo interactivo del lado del cliente (Front-End Only). A continuación, se detalla de forma exhaustiva qué componentes forman parte del sistema y cuáles han quedado excluidos por diseño o limitaciones del entorno de despliegue actual.

### 2.1. Arquitectura de Secciones (En el Alcance Funcional)
El archivo `Sinergia_IA_v2.html` está estructurado de la siguiente forma:

1. **Barra de Navegación Sticky (`nav`):**
   - Transparencia con desenfoque de fondo (`backdrop-filter: blur(12px)`) y diseño oscuro adaptativo.
   - Enlaces de salto internos (`#arquitectura`, `#constructor`, `#galeria`, `#asistente-sec`) para navegación fluida.
   - Botón de llamada a la acción (CTA) dinámico orientado a la interacción del asistente.

2. **Sección Hero (`header`):**
   - Fondo en azul profundo/negro (`--primary: #0a0f1e`) con una retícula geométrica generada por gradientes CSS (`.hero-grid`) simulando un entorno de inteligencia artificial.
   - Badge dinámico con animación pulsante (`@keyframes pulse`) que delimita la versión del Catálogo BIU.
   - Títulos y subtítulos limpios usando la fuente moderna `Syne` para encabezados prominentes y `DM Sans` para el cuerpo.

3. **Módulo de Estadísticas (`.stats-row`):**
   - Un contenedor de cuadrícula flexible (`grid`) que muestra visualmente los indicadores de valor del portal: 5 pilares, 18 prompts cargados, 6 categorías y potencial infinito en el aula.

4. **Módulo de Pilares Teóricos (`#arquitectura`):**
   - Visualización por tarjetas de los 6 pilares esenciales de la construcción de un prompt maestro (Rol, Objetivo, Contexto, Audiencia, Formato, Restricciones), utilizando iconos vectoriales (FontAwesome) integrados en círculos de colores de baja opacidad adaptativos.

5. **Módulo Educativo de Técnicas Avanzadas (`.tab-bar` y `#tab-content`):**
   - Motor JavaScript de renderizado condicional. Al hacer clic en las pestañas, se reemplaza dinámicamente el contenido del nodo HTML mediante un objeto de datos indexado (`TAB_DATA`).
   - Cubre las técnicas: RTF, IA Colaborativa, Shots, Chain of Thought, Método Socrático y Protocolo Cero Errores.

6. **Constructor Dinámico en Vivo (`#constructor`):**
   - Formulario interactivo que recopila datos clave: Rol, Tarea/Acción, Audiencia, Formato de Salida, Tono y Restricción Extra.
   - Evento de entrada reactivo (`oninput="build()"`) que concatena las variables en una cadena estructurada legible y la expone dentro de un contenedor simulado de consola (`.preview-box`).
   - Acciones de copiado al portapapeles (`navigator.clipboard.writeText`) con retroalimentación visual inmediata ("¡Copiado!") y redirección al asistente.

7. **Biblioteca Interactiva Filtrable (`#galeria`):**
   - 18 tarjetas de prompts predefinidas estructuradas en un array de objetos JavaScript (`PROMPTS`).
   - Las tarjetas cambian de color superior en su borde según su categoría (`.cat-feedback`, `.cat-planning`, etc.) usando gradientes lineales.
   - Botones de copiado individual en cada tarjeta y renderizado dinámico mediante filtrado por categorías (`filterGallery`).

8. **Lista de Autoevaluación y Calidad (`.checklist`):**
   - Un check-list visual de dos colores (verde para las buenas prácticas a seguir, rojo para las malas prácticas a evitar) que funciona como un recordatorio heurístico antes del envío de instrucciones a la IA.

9. **Asistente IA Integrado (`#asistente-sec`):**
   - Interfaz gráfica que emula una aplicación de mensajería (burbujas de chat diferenciadas por clases `.ai` y `.user`).
   - Fichas de sugerencias rápidas (`.quick-chips`) que pre-cargan preguntas frecuentes en el campo de entrada al hacer clic, facilitando el descubrimiento de funciones del asistente.

### 2.2. Fuera de Alcance (Out of Scope)
* **Base de Datos y Persistencia:** No existe persistencia de datos del lado del servidor. Cualquier prompt nuevo diseñado en el constructor o el historial de mensajes de la conversación se borra permanentemente al refrescar la pantalla.
* **Autenticación de Usuarios:** No se contempla el registro o inicio de sesión de profesores, lo que les impide crear carpetas personalizadas de prompts o guardar historiales de chat vinculados a sus perfiles.
* **Seguridad de Conexión de API:** El prototipo carece de una pasarela o backend de control, intentando ejecutar el procesamiento de IA directamente en el navegador del cliente final.

---

## 3. Observaciones y Dificultades Técnicas Identificadas

Durante la auditoría de desarrollo y seguridad de `Sinergia_IA_v2.html`, se detectaron vulnerabilidades y cuellos de botella técnicos de alta relevancia:

### 3.1. Vulnerabilidad y Bloqueo de la API de Anthropic (Error de CORS)
El asistente del chat tiene programada una llamada directa a los servidores de Anthropic:
```javascript
const res = await fetch('https://api.anthropic.com/v1/messages', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({
    model: 'claude-sonnet-4-20250514',
    max_tokens: 1000,
    system: SYSTEM_PROMPT,
    messages: chatHistory
  })
});
```
Esta implementación presenta dificultades insalvables en producción:
1. **Fallo de CORS (Cross-Origin Resource Sharing):** La API oficial de Anthropic está configurada para denegar solicitudes provenientes de entornos web de cliente directos (navegadores) para prevenir la filtración de credenciales. Al ejecutar el chat, el navegador arroja un error crítico:
   `Access to fetch at 'https://api.anthropic.com/v1/messages' from origin 'null' (or local domain) has been blocked by CORS policy.`
2. **Falta de Cabeceras de Autorización y Fuga de API Key:** La API requiere el header `'x-api-key': 'TU_API_KEY'`. Si el desarrollador coloca su clave allí para solventar el problema, cualquier usuario del sitio podría abrir la pestaña *Network* del inspector del navegador y robar la clave, cargando costos de consumo al propietario de la cuenta.

### 3.2. Dependencia de Red y Caída de Estilos (Offline Limit)
El código carga de forma externa recursos críticos:
* Fuentes tipográficas: `https://fonts.googleapis.com/css2?family=Syne...`
* Iconos: `https://cdnjs.cloudflare.com/ajax/libs/font-awesome/...`
* Lógica y estilos del navegador.
* **Impacto en el Aula:** En escuelas rurales o instituciones con redes Wi-Fi protegidas o lentas, el portal se renderiza de forma rota. Sin FontAwesome, las tarjetas pierden legibilidad al desaparecer los iconos de control, y el portal completo se visualiza en la tipografía sans-serif genérica del sistema.

### 3.3. Parseador Ineficiente de Mensajes en el Chat
La interfaz del chat procesa el texto devuelto usando un parseador casero rudimentario:
```javascript
const formatted = text.replace(/\*\*(.*?)\*\*/g, '<strong>$1</strong>').replace(/\n/g, '<br>');
```
* **Impacto:** Si la IA responde con tablas comparativas, listas indentadas o bloques de código (muy común al pedirle rúbricas o guías didácticas), el chat de la pantalla muestra el texto en un bloque continuo e ilegible con etiquetas sueltas, arruinando la usabilidad del asistente para la entrega de material estructurado.

### 3.4. Dificultad de Mantenimiento por Monolitismo
El proyecto mantiene HTML, CSS y JS condensados en un solo archivo de 665 líneas.
* **Impacto:** Modificar las tarjetas de prompts, actualizar las traducciones de las técnicas de prompting o cambiar variables de estilo implica manipular código sensible del constructor o de la comunicación de API. Esto incrementa de forma dramática la posibilidad de romper el código operativo debido a errores sintácticos accidentales.

---

## 4. Plan de Ingeniería y Propuestas de Mejora

Para transformar Sinerg-IA en una aplicación robusta, modular y lista para su despliegue comercial o institucional, se definen los siguientes cambios arquitectónicos con sus respectivos códigos de ejemplo para la implementación inmediata.

### 4.1. Solución al Chat: Simulador Mock / Proxy Backend
Para evitar la exposición de la clave API y solventar el bloqueo por CORS, se plantean dos caminos:

#### Alternativa A: Integración de un Simulador Inteligente Local (100% Gratuito y Offline)
Se puede reemplazar la función `sendChat()` con un simulador local que procese heurísticas del mensaje del docente y conteste usando respuestas contextuales prediseñadas.

*Ejemplo de código a integrar en JS:*
```javascript
// Objeto de respuestas automáticas contextuales
const RESPUESTAS_MOCK = {
  matematicas: "Para matemáticas de primaria, te sugiero usar el **Método RTF**:\n\n* **Rol**: Experto en didáctica matemática lúdica.\n* **Tarea**: Diseña un juego de mesa de 5 rondas para enseñar fracciones.\n* **Formato**: Lista numerada con reglas y materiales.",
  rubrica: "Aquí tienes un prompt para generar una rúbrica:\n\n`Actúa como evaluador educativo. Diseña una rúbrica en formato tabla de 4 columnas para evaluar un ensayo de escritura creativa en 3º de secundaria. Criterios: Coherencia, Ortografía, Originalidad y Estructura.`",
  socratico: "El método socrático se implementa así:\n\n`No le des la respuesta al estudiante. Cuando te plantee una duda sobre física, respóndele con una pregunta reflexiva que le ayude a identificar el principio físico involucrado.`",
  default: "¡Excelente pregunta! Recuerda que para mejorar tu prompt debes asegurar que contenga al menos un **Rol** claro, una **Tarea** detallada y un **Formato de salida** (como tabla o lista)."
};

async function sendChat() {
  const inp = document.getElementById('chat-input');
  const msg = inp.value.trim();
  if (!msg) return;
  
  inp.value = '';
  addMsg('user', msg);
  
  const btn = document.getElementById('chat-btn');
  btn.disabled = true;
  const typingId = addTyping();
  
  // Simulación de delay de red para realismo
  setTimeout(() => {
    removeTyping(typingId);
    
    // Búsqueda de palabra clave
    let lowerMsg = msg.toLowerCase();
    let respuestaText = RESPUESTAS_MOCK.default;
    
    if (lowerMsg.includes('matemática') || lowerMsg.includes('primaria')) {
      respuestaText = RESPUESTAS_MOCK.matematicas;
    } else if (lowerMsg.includes('rúbrica') || lowerMsg.includes('evalua')) {
      respuestaText = RESPUESTAS_MOCK.rubrica;
    } else if (lowerMsg.includes('socrático') || lowerMsg.includes('filosofía')) {
      respuestaText = RESPUESTAS_MOCK.socratico;
    }
    
    addMsg('ai', respuestaText);
    btn.disabled = false;
  }, 1000);
}
```

#### Alternativa B: Creación de un Micro-Servidor Proxy Seguro (Node.js/Express)
Si se desea la conexión real a modelos avanzados de lenguaje (como Claude 3.5 Sonnet o Gemini 1.5 Pro), se debe montar un servidor backend intermedio. El cliente enviará su petición al servidor local y el servidor procesará la solicitud con la API Key guardada de forma segura en las variables de entorno del servidor.

*Ejemplo de código para un servidor Express seguro (`server.js`):*
```javascript
const express = require('express');
const cors = require('cors');
const { Anthropic } = require('@anthropic-ai/sdk');
require('dotenv').config();

const app = express();
app.use(cors()); // Configuración segura de CORS
app.use(express.json());

const anthropic = new Anthropic({
  apiKey: process.env.ANTHROPIC_API_KEY, // Almacenado de forma segura en el servidor
});

app.post('/api/chat', async (req, res) => {
  try {
    const { messages, system } = req.body;
    
    const response = await anthropic.messages.create({
      model: 'claude-3-5-sonnet-20241022',
      max_tokens: 1024,
      system: system,
      messages: messages
    });
    
    res.json({ text: response.content[0].text });
  } catch (error) {
    console.error("Error en comunicación con Anthropic:", error);
    res.status(500).json({ error: "Error interno del servidor de IA" });
  }
});

const PORT = process.env.PORT || 3000;
app.listen(PORT, () => console.log(`Servidor de IA seguro corriendo en puerto ${PORT}`));
```

*Modificación correspondiente en la función `sendChat()` de la aplicación web:*
```javascript
// Reemplazar la llamada directa a Anthropic por el endpoint del Proxy Seguro
const res = await fetch('http://localhost:3000/api/chat', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({
    system: SYSTEM_PROMPT,
    messages: chatHistory
  })
});
const data = await res.json();
const reply = data.text || 'Lo siento, hubo un error de procesamiento.';
```

### 4.2. Integración de un Renderizador de Markdown Estándar (Marked.js)
Para solucionar el problema de renderizado de tablas y listas en la burbuja de chat, se propone inyectar la librería ligera Marked.js mediante un CDN o localmente en las cabeceras de la app.

*Cabecera HTML:*
```html
<script src="https://cdn.jsdelivr.net/npm/marked/marked.min.js"></script>
```

*Modificación de la función de inserción de mensajes (`addMsg`):*
```javascript
function addMsg(role, text) {
  const w = document.getElementById('chat-window');
  const d = document.createElement('div');
  d.className = `msg ${role === 'user' ? 'user-msg' : ''}`;
  
  // Utilizar marked.parse para interpretar código, listas y tablas Markdown
  const parsedContent = role === 'ai' ? marked.parse(text) : text.replace(/\n/g, '<br>');
  
  d.innerHTML = `
    <div class="msg-avatar ${role}">${role === 'ai' ? '<i class="fas fa-robot"></i>' : '<i class="fas fa-user"></i>'}</div>
    <div class="msg-bubble">${parsedContent}</div>
  `;
  w.appendChild(d);
  w.scrollTop = w.scrollHeight;
  return d;
}
```

### 4.3. Implementación de Persistencia Local (`localStorage`)
Se debe incorporar una función que guarde la previsualización del constructor de prompts en el caché del navegador del docente, permitiendo recuperar su trabajo al instante en caso de reinicio involuntario.

*Ejemplo de código de persistencia:*
```javascript
// Almacenar datos en localStorage al construir
function build() {
  const rol = document.getElementById('in-rol').value.trim();
  const tarea = document.getElementById('in-tarea').value.trim();
  const aud = document.getElementById('in-aud').value.trim();
  const fmt = document.getElementById('in-formato').value;
  const tono = document.getElementById('in-tono').value;
  const rest = document.getElementById('in-restriccion').value.trim();
  
  // Guardar estado en un objeto JSON
  const formState = { rol, tarea, aud, fmt, tono, rest };
  localStorage.setItem('sinergia_form_state', JSON.stringify(formState));
  
  // Ensamblar el prompt
  let prompt = `Actúa como ${rol || '[Rol]'}.\n\nTu tarea principal es: ${tarea || '[Tarea]'}.\n\nTen en cuenta que el contenido está dirigido a: ${aud || '[Audiencia]'}.\n\nUtiliza un tono ${tono} y presenta la respuesta en formato de ${fmt || '[Formato]'}.`;
  if (rest) prompt += `\n\nRestricciones adicionales: ${rest}.`;
  
  document.getElementById('preview').textContent = prompt;
}

// Cargar datos guardados al cargar la página
window.addEventListener('DOMContentLoaded', () => {
  const savedState = localStorage.getItem('sinergia_form_state');
  if (savedState) {
    const state = JSON.parse(savedState);
    document.getElementById('in-rol').value = state.rol || '';
    document.getElementById('in-tarea').value = state.tarea || '';
    document.getElementById('in-aud').value = state.aud || '';
    document.getElementById('in-formato').value = state.fmt || '';
    document.getElementById('in-tono').value = state.tono || 'motivador y cercano';
    document.getElementById('in-restriccion').value = state.rest || '';
    build();
  }
});
```

### 4.4. Preparación para Funcionamiento 100% Offline (PWA)
Para solventar la inestabilidad de red en las escuelas, se propone crear un archivo `sw.js` (Service Worker) para cachear los assets e iconos del sitio de forma permanente.

*Registro en el script principal de `Sinergia_IA_v2.html`:*
```javascript
if ('serviceWorker' in navigator) {
  window.addEventListener('load', () => {
    navigator.serviceWorker.register('./sw.js')
      .then(reg => console.log('Service Worker registrado con éxito', reg))
      .catch(err => console.warn('Error al registrar Service Worker', err));
  });
}
```

*Contenido del archivo `sw.js` (en la raíz del proyecto):*
```javascript
const CACHE_NAME = 'sinergia-ia-v1';
const ASSETS = [
  './Sinergia_IA_v2.html',
  'https://fonts.googleapis.com/css2?family=Syne:wght@400;700;800&family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,400;0,9..40,500;1,9..40,300&display=swap',
  'https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css',
  'https://cdn.jsdelivr.net/npm/marked/marked.min.js'
];

self.addEventListener('install', e => {
  e.waitUntil(
    caches.open(CACHE_NAME).then(cache => cache.addAll(ASSETS))
  );
});

self.addEventListener('fetch', e => {
  e.respondWith(
    caches.match(e.request).then(response => response || fetch(e.request))
  );
});
```

---

## 5. Análisis de Documentos de Prompts y Desarrollo a Futuro

Para el diseño conceptual y funcional del portal interactivo, se contó con dos piezas clave de literatura digital pedagógica en formato PDF:
1. **`Catálogo de Prompts - BIU - 2024.pdf`**
2. **`Prompting en educación.pdf`**

A continuación, se detalla un desglose analítico del valor pragmático de cada uno, su usabilidad en el desarrollo de software y su proyección a futuro.

### 5.1. Comparativa Metodológica y Operativa

| Criterio de Análisis | Catálogo de Prompts - BIU - 2024.pdf | Prompting en educación.pdf |
| :--- | :--- | :--- |
| **Público Objetivo** | Docente de aula buscando soluciones operativas inmediatas. | Investigador educativo, diseñador instruccional y desarrollador de software de IA. |
| **Naturaleza del Contenido** | Recetario práctico estructurado en plantillas listas para su uso. | Ensayo teórico-práctico sobre el procesamiento cognitivo de la IA. |
| **Nivel de Abstracción** | **Bajo:** Instrucciones de "rellenar espacios en blanco". | **Alto:** Análisis de sesgos, explicabilidad y flujos interactivos de razonamiento. |
| **Estructura Pedagógica** | Ejemplos concretos clasificados por objetivos de aprendizaje de la BIU. | Técnicas de andamiaje cognitivo adaptados al desarrollo intelectual del estudiante. |
| **Ciclo de Vida Útil** | Corto (La actualización de modelos de lenguaje tiende a volver ineficaces los prompts estáticos). | Largo (Los principios epistemológicos de la interacción humano-máquina se mantienen constantes). |

---

### 5.2. Evaluación de Utilidad y Aplicación en el Proyecto

#### A. Documento más útil para el desarrollo del portal interactivo actual
El documento **`Catálogo de Prompts - BIU - 2024.pdf`** fue el pilar fundamental e indispensable para el desarrollo de la aplicación web Sinergia IA en su estado actual.

* **Justificación Técnica:**
  Para un desarrollador, la información debe ser estructurada y sistemática para poder traducirse a código limpio. Este catálogo proporciona la estructura exacta de las 18 tarjetas de la biblioteca interactiva y clasifica las necesidades pedagógicas en categorías nítidas (Feedback, Inclusión, Evaluación).
  Además, la lógica de variables fijas del catálogo permitió crear el mapeo de inputs de HTML del **Constructor en Vivo**. El código mapea exactamente las directrices del catálogo, por lo que sin este documento base, la automatización del portal carecería de un esquema de datos coherente y estructurado. El catálogo provee el **"contenido e insumo bruto"** del proyecto.

#### B. Documento más útil para el desarrollo profesional y de software a futuro
El documento **`Prompting en educación.pdf`** constituye la herramienta de mayor valor y utilidad para el desarrollo profesional a mediano y largo plazo tanto en el campo educativo como en el tecnológico.

* **Justificación Epistemológica y Tecnológica:**
  La ingeniería de prompts está evolucionando desde un enfoque de "recetas fijas" hacia un enfoque de **programación de agentes semánticos**. Los modelos de IA modernos (como GPT-4o, Claude 3.5 o Gemini 1.5) requieren cada vez menos de una plantilla rígida y se desempeñan mejor cuando se les explica el razonamiento subyacente de la tarea.
  El documento **`Prompting en educación.pdf`** destaca por enseñar la arquitectura intelectual de la interacción con la IA:
  
  1. **Composición de Flujos Complejos:** En lugar de enviar un prompt único de una sola interacción (Single-turn), enseña técnicas como la *Cadena de Pensamiento (Chain of Thought)*, permitiendo que la máquina razone lógicamente el proceso pedagógico antes de emitir la conclusión (vital para corregir ejercicios complejos o planificar temarios anuales).
  2. **El Enfoque Colaborativo y Socrático:** Introduce metodologías donde la máquina no reemplaza al docente, sino que establece un diálogo interactivo, haciéndole preguntas clave para retroalimentar su labor o guiando al estudiante socráticamente sin darle las respuestas directamente.
  3. **Portabilidad Tecnológica:** Al comprender cómo procesa y "piensa" el modelo de lenguaje (el fenómeno de la atención y la ventana de contexto), el profesional puede diseñar prompts genéricos altamente adaptables para cualquier modelo futuro. Un recetario estático de 2024 puede dejar de funcionar con la llegada de las IA basadas en agentes autónomos, pero las bases de andamiaje cognitivo descritas en el segundo documento perdurarán como principios de programación de lenguaje natural en los próximos años.
  
  Para el desarrollo de software educativo, este material es el mapa de ruta conceptual para diseñar la próxima generación de asistentes interactivos y tutores automatizados integrados en entornos virtuales de aprendizaje (LMS).
