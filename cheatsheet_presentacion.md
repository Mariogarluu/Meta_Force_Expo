# 📝 Tarjeta de Apoyo / Cheat Sheet — Presentación Meta-Force 🏋️🔥

*Esta guía está diseñada para lectura rápida durante la exposición del **5 de junio**. Si os quedáis en blanco o no sabéis qué decir ante una diapositiva, leed la **frase de rescate** y mencionad los **conceptos clave**.*

---

## 🎙️ Bloque 1: Samuel García Ruiz (Minutos 0:00 - 5:00)
*Foco: Introducción, Concepto y Core Frontend Web (Slides 1 a 6)*

### 1. Slide 1 — Portada: Meta-Force
* **Frase de rescate:** "Buenos días. Os presentamos Meta-Force, una plataforma integral en la nube diseñada para revolucionar la gestión deportiva y de fitness."
* **Conceptos clave:** Grupo 5, Presentación técnica y de negocio.

### 2. Slide 2 — Concepto Principal
* **Frase de rescate:** "Es un ecosistema SaaS completo que conecta una aplicación web en Angular 19, una app nativa en Android con IA integrada, y un sistema de Business Intelligence."
* **Conceptos clave:** Plataforma multiidioma, escalabilidad en la nube, automatización.

### 3. Slide 3 — Portal Público
* **Frase de rescate:** "Esta es la Landing Page pública de cara al cliente. Está desarrollada en Angular 19 con un diseño totalmente responsivo y flujos de login y registro seguros."
* **Conceptos clave:** Angular 19, Standalone Components, Diseño Adaptativo.

### 4. Slide 4 — Consola de Control
* **Frase de rescate:** "Al acceder como Superadmin, entramos a este panel de control interactivo donde se monitorizan ingresos, usuarios y aforos del negocio en tiempo real."
* **Conceptos clave:** Estado reactivo con Angular Signals, Gráficos dinámicos (Chart.js).

### 5. Slide 5 — Gestión de Operaciones (Resumen)
* **Frase de rescate:** "El núcleo operativo de la plataforma permite gestionar los centros de forma multi-sucursal, catalogar clases y asignar instructores a horarios sin conflictos."
* **Conceptos clave:** Gestión de recursos, consistencia relacional.

### 6. Slide 6 — Gestión de Centros (Captura)
* **Frase de rescate:** "Aquí vemos la consola real de administración de centros y máquinas. Proporciona alertas visuales inmediatas para confirmar que las operaciones se guardan correctamente."
* **Conceptos clave:** UX reactiva, control de aforo por sala, NgZone.

---

## 🎙️ Bloque 2: Salvador Bueno González (Minutos 5:00 - 10:00)
*Foco: Facturación, Control de Accesos, App Móvil e IA, y Power BI (Slides 7 a 14)*

### 7. Slide 7 — Suscripciones y Facturación (Resumen)
* **Frase de rescate:** "La plataforma ofrece un sistema flexible de facturación internacionalizable, traducido nativamente al español, inglés y francés sin recargar la página."
* **Conceptos clave:** ngx-translate, i18n dinámica, arquitectura reactiva.

### 8. Slide 8 — Suscripciones y Facturación (Detalle)
* **Frase de rescate:** "El portal de suscripciones permite adquirir planes y descargar facturas PDF que se generan en el servidor y se notifican por email de forma automatizada."
* **Conceptos clave:** Supabase Storage, Edge Function `invoice-pdf`, servicio Resend.

### 9. Slide 9 — Control de Accesos - Lector Web
* **Frase de rescate:** "Para el personal de recepción, la plataforma web integra un lector de códigos QR que valida los accesos y actualiza el aforo del centro en tiempo real."
* **Conceptos clave:** Librería html5-qrcode, registro instantáneo de accesos.

### 10. Slide 10 — Control de Accesos - App Cliente
* **Frase de rescate:** "Por su parte, el cliente genera códigos QR temporales firmados criptográficamente desde su app móvil, lo que impide el fraude y la suplantación de identidad."
* **Conceptos clave:** Edge Function `qr-sign`, JWT de corta duración, control de acceso físico.

### 11. Slide 11 — App Nativa - Asistente de Entrenamientos
* **Frase de rescate:** "La aplicación móvil está programada de forma nativa en Kotlin con Jetpack Compose. Destaca el asistente conversacional con IA para generar rutinas a medida."
* **Conceptos clave:** Arquitectura MVVM, Hilt para inyección, modelo Llama 3 (Groq).

### 12. Slide 12 — App Nativa - Asistente de Nutrición
* **Frase de rescate:** "La IA también diseña dietas personalizadas analizando las marcas del usuario. Estos planes se guardan en su perfil en la nube y se cachean localmente para rendimiento."
* **Conceptos clave:** Persistencia local con DataStore, Edge Function `ai-chat`.

### 13. Slide 13 — Business Intelligence - Panel Financiero
* **Frase de rescate:** "Para la inteligencia de negocio, desarrollamos un script en Python que realiza un ETL limpio de base de datos para generar informes financieros avanzados."
* **Conceptos clave:** Script ETL con Pandas, Python `supabase-py`, KPIs de negocio.

### 14. Slide 14 — Business Intelligence - Rendimiento
* **Frase de rescate:** "Este dashboard interactivo en Power BI analiza la retención, los planes más vendidos y las horas de mayor afluencia para optimizar los recursos del gimnasio."
* **Conceptos clave:** Power BI Premium, analítica predictiva de uso de salas.

---

## 🎙️ Bloque 3: Mario García Luque (Minutos 10:00 - 15:00)
*Foco: Arquitectura, Viabilidad, Scrum, Seguridad y Cierre (Slides 15 a 20)*

### 15. Slide 15 — Arquitectura Física
* **Frase de rescate:** "Esta es nuestra arquitectura técnica. Los clientes de Angular y Kotlin se comunican con Supabase a través de APIs REST y funciones serverless Deno en TypeScript."
* **Conceptos clave:** Backend as a Service (BaaS), Deno Edge Functions, secretos inyectados en compilación.

### 16. Slide 16 — Viabilidad Económica (Lean Canvas)
* **Frase de rescate:** "Estructuramos el negocio bajo un modelo SaaS B2C. Estudiamos la viabilidad económica confrontando costes fijos en la nube con las tarifas recurrente del servicio."
* **Conceptos clave:** Costes cloud computing, plan de amortización, cumplimiento RGPD.

### 17. Slide 17 — Gestión Ágil (Scrum)
* **Frase de rescate:** "Para la organización del equipo utilizamos metodología ágil Scrum con sprints de dos semanas, coordinando el código en GitHub mediante ramas de características."
* **Conceptos clave:** Pull Requests en Git Flow, integración continua (CI/CD).

### 18. Slide 18 — Gestión del Proyecto - Tablero Jira
* **Frase de rescate:** "En esta captura de Jira Software se aprecia el backlog de tareas, que suma hasta 180 historias de usuario detalladas, estimadas y asignadas con total transparencia."
* **Conceptos clave:** Sprints de Jira, gráficos de velocidad, trazabilidad.

### 19. Slide 19 — Seguridad de Datos
* **Frase de rescate:** "En seguridad, todas nuestras 34 tablas de base de datos tienen activas políticas RLS. Cada rol del sistema solo puede leer y escribir su propia información autorizada."
* **Conceptos clave:** Row Level Security (RLS), Custom JWT Token Hooks, protección OWASP ZAP.

### 20. Slide 20 — Conclusión y Cierre
* **Frase de rescate:** "Meta-Force está desplegado y es 100% operativo en producción. Muchas gracias por su atención y quedamos a su disposición para las preguntas y la demostración."
* **Conceptos clave:** Vercel (Frontend), Supabase Cloud (Backend), Demo en vivo de la Web y App.
