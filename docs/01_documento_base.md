# Documentación de Proyecto: Sinerg-IA (Sinergia IA)
## Portal Maestro de Prompting Educativo

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
   - Motor JavaScript de renderizado condicional. Al hacer clic en las pestañas, se reemplaza dinámicamente el contenido del nodo HTML mediante un objeto de datos indexado.
   - Cubre las técnicas: RTF, IA Colaborativa, Shots, Chain of Thought, Método Socrático y Protocolo Cero Errores.

6. **Constructor Dinámico en Vivo (`#constructor`):**
   - Formulario interactivo que recopila datos clave: Rol, Tarea/Acción, Audiencia, Formato de Salida, Tono y Restricción Extra.
   - Evento de entrada reactivo que concatena las variables en una cadena estructurada legible y la expone dentro de un contenedor simulado de consola.
   - Acciones de copiado al portapapeles con retroalimentación visual inmediata ("¡Copiado!") y redirección al asistente.

7. **Biblioteca Interactiva Filtrable (`#galeria`):**
   - 18 tarjetas de prompts predefinidas estructuradas en un array de objetos JavaScript.
   - Las tarjetas cambian de color superior en su borde según su categoría usando gradientes lineales.
   - Botones de copiado individual en cada tarjeta y renderizado dinámico mediante filtrado por categorías.

8. **Lista de Autoevaluación y Calidad (`.checklist`):**
   - Un check-list visual de dos colores (verde para las buenas prácticas a seguir, rojo para las malas prácticas a evitar) que funciona como un recordatorio heurístico antes del envío de instrucciones a la IA.

9. **Asistente IA Integrado (`#asistente-sec`):**
   - Interfaz gráfica que emula una aplicación de mensajería (burbujas de chat diferenciadas por clases).
   - Fichas de sugerencias rápidas que pre-cargan preguntas frecuentes en el campo de entrada al hacer clic, facilitando el descubrimiento de funciones del asistente.

### 2.2. Fuera de Alcance (Out of Scope)
* **Base de Datos y Persistencia:** No existe persistencia de datos del lado del servidor. Cualquier prompt nuevo diseñado en el constructor o el historial de mensajes de la conversación se borra permanentemente al refrescar la pantalla.
* **Autenticación de Usuarios:** No se contempla el registro o inicio de sesión de profesores, lo que les impide crear carpetas personalizadas de prompts o guardar historiales de chat vinculados a sus perfiles.
* **Seguridad de Conexión de API:** El prototipo carece de una pasarela o backend de control, intentando ejecutar el procesamiento de IA directamente en el navegador del cliente final.

---

## 3. Observaciones y Dificultades Técnicas Identificadas

Durante la auditoría de desarrollo y seguridad de `Sinergia_IA_v2.html`, se detectaron vulnerabilidades y cuellos de botella técnicos de alta relevancia:

### 3.1. Vulnerabilidad y Bloqueo de la API de Anthropic (Error de CORS)
El asistente del chat tiene programada una llamada directa a los servidores de Anthropic desde el cliente. Esta implementación presenta dificultades insalvables en producción:
1. **Fallo de CORS (Cross-Origin Resource Sharing):** La API oficial de Anthropic está configurada para denegar solicitudes provenientes de entornos web de cliente directos (navegadores) para prevenir la filtración de credenciales. Al ejecutar el chat, el navegador arroja un error de red crítico debido a que el origen local es bloqueado por las políticas CORS del proveedor.
2. **Falta de Cabeceras de Autorización y Fuga de API Key:** La API requiere cabeceras con el token de acceso privado. Escribir o inyectar esta clave directamente en el script de cliente la expone públicamente a cualquier usuario que inspeccione el código fuente o monitorice el tráfico de red, cargando posibles costos de consumo al propietario de la cuenta.

### 3.2. Dependencia de Red y Caída de Estilos (Offline Limit)
El código carga de forma externa recursos críticos como fuentes tipográficas de Google Fonts y librerías de iconos de FontAwesome.
* **Impacto en el Aula:** En escuelas rurales o instituciones con redes Wi-Fi protegidas o lentas, el portal se renderiza de forma rota. Sin FontAwesome, las tarjetas pierden legibilidad al desaparecer los iconos de control, y el portal completo se visualiza en la tipografía sans-serif genérica del sistema.

### 3.3. Parseador Ineficiente de Mensajes en el Chat
La interfaz del chat procesa el texto devuelto usando un reemplazo casero rudimentario basado en expresiones regulares para aplicar etiquetas de negrita y saltos de línea.
* **Impacto:** Si la IA responde con tablas comparativas, listas indentadas o bloques de código (muy común al pedirle rúbricas o guías didácticas), el chat muestra el texto en un bloque continuo e ilegible con etiquetas sueltas, arruinando la usabilidad del asistente para la entrega de material estructurado.

### 3.4. Dificultad de Mantenimiento por Monolitismo
El proyecto mantiene HTML, CSS y JS condensados en un solo archivo de 665 líneas.
* **Impacto:** Modificar las tarjetas de prompts, actualizar las traducciones de las técnicas de prompting o cambiar variables de estilo implica manipular código sensible del constructor o de la comunicación de API. Esto incrementa de forma dramática la posibilidad de romper el código operativo debido a errores sintácticos accidentales.

---

## 4. Plan de Ingeniería y Propuestas de Mejora

Para transformar Sinerg-IA en una aplicación robusta, modular y lista para su despliegue comercial o institucional, se definen las siguientes propuestas de mejora conceptuales y funcionales:

### 4.1. Solución al Chat: Simulador Mock / Proxy Backend
Para evitar la exposición de la clave API y solventar el bloqueo por CORS, se plantean dos soluciones alternativas:

* **Alternativa A: Integración de un Simulador Inteligente Local (Offline y Gratuito):**
  Consiste en capturar las entradas de chat enviadas por el docente y pasarlas por un filtro de palabras clave en JavaScript. Si el texto del docente contiene términos como "matemáticas", "rúbrica", "socrático" o "evaluación", el script intercepta el flujo de red y devuelve de forma instantánea una respuesta contextual predefinida y enriquecida pedagógicamente. Esto elimina la necesidad de API Keys, elimina el error de CORS y permite que el chat sea 100% funcional sin conexión a internet.

* **Alternativa B: Creación de un Micro-Servidor Proxy Seguro:**
  Consiste en estructurar un pequeño servidor intermedio (desplegado en plataformas seguras) que maneje de forma privada la clave de API a través de variables de entorno. La aplicación web realiza peticiones locales al servidor proxy, el cual recibe las solicitudes, las firma de forma segura, se comunica con los servidores oficiales del proveedor de IA y devuelve el resultado limpio al cliente, resolviendo de raíz el problema de CORS y protegiendo el token contra filtraciones.

### 4.2. Integración de un Renderizador de Markdown Estándar
Para resolver el problema del texto desestructurado en el chat, se propone la integración de una librería ligera de parseo como Marked.js. Al importar esta herramienta, el script de mensajería procesará la respuesta de la IA a través de su motor de renderizado antes de insertar el contenido en la burbuja de chat. Esto asegura que tablas comparativas, rúbricas de evaluación y viñetas estructuradas se muestren con el formato visual correcto en pantalla.

### 4.3. Implementación de Persistencia Local (`localStorage`)
Se propone configurar funciones de almacenamiento de datos locales en el navegador. Al ingresar texto en el constructor de prompts, los campos se serializan y guardan automáticamente en caché. Al recargar la página, el portal lee este almacenamiento para restaurar el progreso del usuario, evitando pérdidas accidentales de información. De igual forma, esta funcionalidad permite almacenar los prompts favoritos del docente seleccionados de la biblioteca y el historial activo de la conversación de chat.

### 4.4. Preparación para Funcionamiento 100% Offline (PWA)
Para solventar la inestabilidad de conexión a internet en los centros educativos, se propone registrar un Service Worker que gestione la caché de los assets de la aplicación. Esta tecnología descarga y almacena de forma local la estructura HTML, las tipografías de Google Fonts y las hojas de estilos de iconos de FontAwesome. De esta manera, el portal se transforma en una Aplicación Web Progresiva (PWA) capaz de instalarse y ejecutarse sin conexión Wi-Fi o datos móviles.

---

## 5. Análisis de Documentos de Prompts y Desarrollo a Futuro

Para el diseño conceptual y funcional del portal interactivo, se contó con dos piezas clave de literatura digital pedagógica en formato PDF:
1. **`Catálogo de Prompts - BIU - 2024.pdf`**
2. **`Prompting en educación.pdf`**

A continuación, se presenta un desglose analítico del valor pragmático de cada uno, su usabilidad en el desarrollo de software y su proyección a futuro.

### 5.1. Comparativa Metodológica y Operativa

| Criterio de Análisis | Catálogo de Prompts - BIU - 2024.pdf | Prompting en educación.pdf |
| :--- | :--- | :--- |
| **Público Objetivo** | Docente de aula buscando soluciones operativas inmediatas. | Investigador educativo, diseñador instruccional y desarrollador de software de IA. |
| **Naturaleza del Contenido** | Recetario práctico estructurado en plantillas listas para su uso. | Ensayo teórico-práctico sobre el procesamiento cognitivo de la IA. |
| **Nivel de Abstracción** | **Bajo:** Instrucciones de "rellenar espacios en blanco". | **Alto:** Análisis de sesgos, explicabilidad y flujos interactivos de razonamiento. |
| **Estructura Pedagógica** | Ejemplos concretos clasificados por objetivos de aprendizaje de la BIU. | Técnicas de andamiaje cognitivo adaptados al desarrollo intelectual del estudiante. |
| **Ciclo de Vida Útil** | Corto (La actualización de los modelos de lenguaje tiende a volver obsoletos los prompts estáticos). | Largo (Los principios epistemológicos de la interacción humano-máquina se mantienen constantes). |

---

### 5.2. Evaluación de Utilidad y Aplicación en el Proyecto

#### A. Documento más útil para el desarrollo del portal interactivo actual
El documento **`Catálogo de Prompts - BIU - 2024.pdf`** fue el pilar fundamental e indispensable para el desarrollo de la aplicación web Sinergia IA en su estado actual.

* **Justificación Técnica:**
  Para un desarrollador, la información debe ser estructurada y sistemática para poder traducirse a código. Este catálogo proporciona la estructura exacta de las 18 tarjetas de la biblioteca interactiva y clasifica las necesidades pedagógicas en categorías nítidas (Feedback, Inclusión, Evaluación).
  Además, la lógica de variables fijas del catálogo permitió crear el mapeo de campos del **Constructor en Vivo**. El código interactivo replica de forma exacta las directrices de este archivo, proveyendo los datos necesarios para automatizar el generador de prompts del portal.

#### B. Documento más útil para el desarrollo profesional y de software a futuro
El documento **`Prompting en educación.pdf`** constituye la herramienta de mayor valor y utilidad para el desarrollo profesional a mediano y largo plazo tanto en el campo educativo como en el tecnológico.

* **Justificación Epistemológica y Tecnológica:**
  La ingeniería de prompts está evolucionando desde un enfoque de fórmulas rígidas hacia una **programación de agentes semánticos**. Los modelos de IA modernos se desempeñan mejor cuando se les explica el razonamiento y andamiaje cognitivo subyacente del proceso de aprendizaje, en lugar de recibir plantillas vacías.
  Este documento destaca por enseñar la arquitectura intelectual de la interacción:
  
  1. **Composición de Flujos Complejos:** Enseña técnicas avanzadas como *Chain-of-Thought (razonamiento en cadena)*, guiando al modelo de lenguaje para que argumente el proceso pedagógico paso a paso antes de entregar la respuesta.
  2. **El Enfoque Colaborativo y Socrático:** Introduce metodologías donde la máquina interactúa de forma reflexiva haciendo preguntas clave al docente o guiando al alumno hacia el descubrimiento de sus propios errores de manera progresiva.
  3. **Portabilidad y Vigencia:** Al comprender cómo procesa y asocia los datos un modelo de lenguaje (ventana de contexto, atención, tokens), el profesional adquiere la capacidad de formular instrucciones eficientes aplicables a cualquier modelo de IA futuro. Mientras las plantillas estáticas de 2024 envejecen con cada actualización de software, los principios de estructuración cognitiva se mantendrán vigentes en las próximas décadas.
