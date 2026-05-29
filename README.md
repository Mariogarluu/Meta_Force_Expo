# Meta Force — Proyecto Intermodular 2.º DAM (CPIFP Alan Turing)

<div align="center">

<img src="../front/public/Logo.png" alt="Meta Force" width="160" />

**Plataforma integral de gestión de centros deportivos: web (Angular + Supabase), app Android (Kotlin/Jetpack Compose), IA asistente y analítica BI.**

[![Producción](https://img.shields.io/badge/Producción-meta--force--psi.vercel.app-0A66C2?style=for-the-badge&logo=vercel&logoColor=white)](https://meta-force-psi.vercel.app/)
[![Frontend](https://img.shields.io/badge/Frontend-Angular_19-DD0031?style=for-the-badge&logo=angular&logoColor=white)](https://github.com/Mariogarluu/Meta_Force_front)
[![Backend](https://img.shields.io/badge/Backend-Supabase-3ECF8E?style=for-the-badge&logo=supabase&logoColor=white)](https://github.com/Mariogarluu/Meta_Force_back)
[![Android](https://img.shields.io/badge/Android-Kotlin_2.0-7F52FF?style=for-the-badge&logo=kotlin&logoColor=white)](https://github.com/Mariogarluu/Meta_Force_kotlin)

</div>

> Repositorio guía del **Grupo 5** del turno de mañana — exposición del **5 de junio de 2026, 10:00 – 10:15**. CPIFP Alan Turing (Málaga). Ciclo: Desarrollo de Aplicaciones Multiplataforma. Curso 2025/2026.

---

## Índice de contenidos

1. [Equipo](#equipo)
2. [Resumen del proyecto](#resumen-del-proyecto)
3. [Capturas y vistas del producto](#capturas-y-vistas-del-producto)
4. [Aportación del proyecto por módulo](#aportación-del-proyecto-por-módulo)
   - [Acceso a datos (Juan Antonio García Gómez)](#acceso-a-datos--juan-antonio-garcía-gómez)
   - [Programación multimedia y dispositivos móviles (David Hormigo Ramírez)](#programación-multimedia-y-dispositivos-móviles--david-hormigo-ramírez)
   - [Programación de servicios y procesos (David Hormigo Ramírez)](#programación-de-servicios-y-procesos--david-hormigo-ramírez)
   - [Desarrollo de interfaces (Carmen Campos Fernández)](#desarrollo-de-interfaces--carmen-campos-fernández)
   - [Servidores y APIs (Juan Antonio García Gómez)](#servidores-y-apis--juan-antonio-garcía-gómez)
   - [Sistemas de gestión empresarial (Miguel Ángel Ronda Carracao)](#sistemas-de-gestión-empresarial--miguel-ángel-ronda-carracao)
   - [Empresa e Iniciativa Emprendedora II — no aplica](#empresa-e-iniciativa-emprendedora-ii--no-aplica)
5. [Repositorios de código](#repositorios-de-código)
6. [Despliegue y entornos](#despliegue-y-entornos)
7. [Documentación unificada (Confluence)](#documentación-unificada-confluence)
8. [Gestión del proyecto (Jira)](#gestión-del-proyecto-jira)
9. [Documentación de código (Compodoc)](#documentación-de-código-compodoc)
10. [Stack tecnológico](#stack-tecnológico)
11. [Arquitectura y diagrama general](#arquitectura-y-diagrama-general)
12. [Cómo levantar el proyecto en local](#cómo-levantar-el-proyecto-en-local)
13. [Información que falta por aportar](#información-que-falta-por-aportar)

---

## Equipo

> Orden de exposición: **5** — bloque 10:00 → 10:15 del 5 de junio de 2026.

| Foto | Nombre completo | Correo educaAnd | Rol principal | GitHub |
|------|-----------------|------------------|---------------|--------|
| 🧑‍💻 | **Mario García Luque** | [mgarluq1102@g.educaand.es](mailto:mgarluq1102@g.educaand.es) | Tech lead · Backend Supabase, Edge Functions, RLS, CI/CD, analítica, app Kotlin | [@Mariogarluu](https://github.com/Mariogarluu) |
| 🧑‍💻 | **Salvador Bueno González** | [sbuegon0702@g.educaand.es](mailto:sbuegon0702@g.educaand.es) | Frontend Angular — maquetación, dashboard, i18n, temas | [@sbuegonz00](https://github.com/sbuegonz00) |
| 🧑‍💻 | **Samuel García Ruiz** | [sgarrui1201@g.educaand.es](mailto:sgarrui1201@g.educaand.es) | Frontend Angular — historias de usuario, gestión de centros / clases | [@sgarrui1201](https://github.com/sgarrui1201) |

Profesorado evaluador (5 de junio de 2026):

- García Gómez, Juan Antonio (coordinador, AD / SyA)
- Hormigo Ramírez, David (PSP / PMDM)
- Campos Fernández, Carmen (DI)
- Ronda Carracao, Miguel Ángel (SGE)
- Alcázar Rosal, Rosa Carmen (EIE — no aplica al proyecto)

---

## Resumen del proyecto

**Meta Force** es una **plataforma multicapa para la gestión de centros deportivos** que integra:

- 🌐 **Web (Angular 19 + Tailwind 3.4 + Supabase JS):** panel de administración para SUPERADMIN y ADMIN_CENTER (usuarios, centros, máquinas, clases, suscripciones, facturación) y portal de cliente (perfil, plan, QR, dashboard).
- 📱 **App Android (Kotlin 2.0 + Jetpack Compose + Hilt):** experiencia móvil para usuarios y entrenadores con entrenamientos, dietas, clases, QR de acceso y chat con IA.
- 🧠 **Asistente de IA (Edge Function `ai-chat` + Groq):** genera y guarda planes de entrenamiento / nutrición personalizados.
- 🔐 **Backend serverless Supabase:** PostgreSQL gestionado, **Row Level Security** por rol (`SUPERADMIN`, `ADMIN_CENTER`, `TRAINER`, `CLEANER`, `USER`), `Auth` con JWT + *custom access token hook*, *Storage* para facturas e imágenes, **Edge Functions** (Deno) que sustituyen al Express histórico.
- 📊 **Analítica BI (Power BI + Python/Pandas):** ETL contra Supabase (`back/analytics/extract_data.py`) que alimenta `MetaForce_Superadmin_Dashboard.pbix` con KPIs de negocio (usuarios, suscripciones, facturación, ocupación, entrenamientos).
- 🛡️ **Seguridad y auditoría:** Helmet + rate-limit en histórico Express, RLS exhaustivo en Supabase, JWT con expiry corto, **auditoría OWASP ZAP** documentada (`back/docs/ZAP_RUNBOOK_2026-05.md`, `back/docs/security-audit-2026-05.md`).

> El producto **está desplegado y accesible** en [https://meta-force-psi.vercel.app/](https://meta-force-psi.vercel.app/).
> El backend corre como proyecto Supabase (`https://qybgnrlszozjhimewkel.supabase.co`) con sus Edge Functions y políticas RLS aplicadas mediante migraciones SQL versionadas.

### Diferencial frente a un CRUD genérico

- **Migración real Express → Supabase** documentada en `back/docs/MIGRATION_DECISIONS.md` y trazada en Jira (épica **SCRUM-147 — Infraestructura y Ecosistema Meta-Force** y Confluence “Informe migración Express → Supabase — SCRUM-138”).
- **Control de acceso físico al gimnasio mediante QR firmado con JWT corto** (`qr-sign` + `access-scan` Edge Functions).
- **Suscripciones y facturación nativa** (`subscription_plans`, `plan_durations`, `plan_prices`, `subscriptions`, `invoices`) con generación de PDF (`invoice-pdf`) y envío automático por email vía Resend (`subscription-email`).
- **IA conversacional** con persistencia de sesiones (`AiChatSession`, `AiChatMessage`) y guardado directo de planes generados al perfil del usuario.

---

## Capturas y vistas del producto

> ⚠️ **Pendiente:** subir capturas reales al directorio `readme/img/` y reemplazar los placeholders. (Ver [Información que falta por aportar](#información-que-falta-por-aportar).)

| Vista | Captura |
|-------|---------|
| Landing / login (web) | `readme/img/01-landing.png` *(pendiente)* |
| Dashboard SUPERADMIN (web) | `readme/img/02-dashboard.png` *(pendiente)* |
| Gestión de centros / máquinas (web) | `readme/img/03-centros.png` *(pendiente)* |
| Suscripciones y facturación (web) | `readme/img/04-suscripciones.png` *(pendiente)* |
| Lector / generador de QR (web + móvil) | `readme/img/05-qr.png` *(pendiente)* |
| Chat con IA y planes (móvil) | `readme/img/06-ai-chat.png` *(pendiente)* |
| Dashboard Power BI (analytics) | `readme/img/07-powerbi.png` *(pendiente)* |
| Diagrama de arquitectura | `readme/img/08-arquitectura.png` *(pendiente)* |

---

## Aportación del proyecto por módulo

Subapartado obligatorio por cada módulo (con objetivos cubiertos, evidencias en el repo y limitaciones / líneas futuras).

### Acceso a datos — Juan Antonio García Gómez

**Objetivos del módulo cubiertos**

- Modelado de datos relacional sobre PostgreSQL (Supabase).
- Persistencia ORM con **Prisma 6.18** en el histórico Express y mantenida como *source of truth* declarativa: [`back/prisma/schema.prisma`](../back/prisma/schema.prisma).
- Migraciones versionadas en **SQL puro** (Supabase) en [`back/supabase/migrations/`](../back/supabase/migrations/) (20+ migraciones aplicadas: triggers de `auth.users → public.profiles`, RLS, custom access token hook, RPC para duplicar entrenamientos, facturación, roles, *security advisors fixes*…).
- Procedimientos almacenados / RPC para reordenar dietas y duplicar workouts ([`20260418104000_rpc_duplicate_workout_reorder_diet.sql`](../back/supabase/migrations/20260418104000_rpc_duplicate_workout_reorder_diet.sql)).
- Consumo desde múltiples clientes: Angular (Supabase JS), Kotlin/Retrofit (REST a Edge Functions), Python (`supabase-py` para ETL).
- **34 tablas en producción** con RLS habilitado en todas: `User`, `Center`, `Machine`, `GymClass`, `ClassCenterSchedule` (1.024 filas), `subscriptions`, `invoices`, `user_roles`, `AiChatSession`, `Workout`, `Diet`, etc.

**Evidencias en el repo**

- 📄 `back/prisma/schema.prisma` — modelo lógico (User, Center, Machine, GymClass, Subscription, Invoice, Workout, Diet, AiChat…).
- 📂 `back/supabase/migrations/` — migraciones SQL con histórico completo (RLS, índices, FKs, RPC, triggers).
- 📂 `back/supabase/tests/` — tests SQL (`rls_catalog.test.sql`, `role_isolation.test.sql`, `subscriptions_chain.test.sql`, `invoice_numbering.test.sql`, `admin_set_user_role.test.sql`).
- 📄 `back/scripts/seed-from-json.mjs` y `back/JSON_IMPORT_GUIDE.md` — carga masiva tipada desde JSON.
- 📄 `back/docs/MIGRATION_DECISIONS.md` — decisiones técnicas de la migración Express/Prisma → Supabase.

**Limitaciones / líneas futuras**

- Vistas materializadas para reporting BI en lugar del ETL nocturno.
- Particionamiento de tablas históricas (`ClassCenterSchedule`, `ExerciseLog`).

---

### Programación multimedia y dispositivos móviles — David Hormigo Ramírez

**Objetivos del módulo cubiertos**

- App **Android nativa** en **Kotlin 2.0** con **Jetpack Compose + Material Design 3** ([`kotlin/`](../kotlin/)).
- Arquitectura **MVVM + Clean Architecture** con **Dagger Hilt** para inyección de dependencias.
- **Persistencia local** con Jetpack DataStore (sesión y preferencias).
- Consumo de **API REST con Retrofit 2 + OkHttp3** (interceptor de auth con JWT).
- **Asincronía** con Kotlin Coroutines + StateFlow.
- Generación de **código QR** en el dispositivo y subida de imágenes con **Coil**.
- Pantallas: login/registro, dashboard, entrenamientos (lista + detalle), dietas, clases grupales, centros y equipamiento, perfil, **chat con IA** y QR personal.

**Evidencias en el repo**

- 📄 [`kotlin/README.md`](../kotlin/README.md) — arquitectura, stack, endpoints consumidos, paleta visual.
- 📂 `kotlin/app/src/main/java/com/meta_force/meta_force/` — capa `data/` (model, network, repository), `di/`, `ui/` (auth, dashboard, workouts, diets, classes, centers, aichat, qr, profile).
- 📄 `kotlin/app/src/main/java/com/meta_force/meta_force/di/NetworkModule.kt` — `BASE_URL` apuntando al backend desplegado.

**Limitaciones / líneas futuras**

- Modo offline-first con Room y sincronización en background.
- Notificaciones push con FCM (recordatorios de clases / suscripciones).

---

### Programación de servicios y procesos — David Hormigo Ramírez

**Objetivos del módulo cubiertos**

- Servicios concurrentes y procesos **serverless en Deno** (Edge Functions de Supabase): autenticación, escaneo QR, generación de PDFs, envío de emails, importación masiva, IA, eventos de rendimiento, *health checks*…
- **11 Edge Functions desplegadas** en [`back/supabase/functions/`](../back/supabase/functions/): `auth-register`, `auth-change-password`, `admin-signout`, `admin-analytics`, `access-scan`, `qr-sign`, `bulk-import`, `migrate-legacy-users`, `invoice-pdf`, `subscription-email`, `ai-chat`, `ai-save-plan`, `ai-sessions`, `create-ticket`, `machines-create`, `performance-events`, `health`.
- **Procesos largos** (importación masiva, ETL analítico) ejecutados como tareas Python/Node fuera del request HTTP (`back/scripts/seed-from-json.mjs`, `back/analytics/extract_data.py`).
- **Hilos / coroutines** en la app Kotlin (Coroutines + StateFlow) y **operadores reactivos** con RxJS en Angular.
- **Rate limiting** en el histórico Express (`express-rate-limit`) y en Edge (helper `back/supabase/functions/_shared/rate-limit.ts`).
- Comunicación entre procesos vía **Resend** (email) y **Cloudinary** (`back/src/services/cloudinary.service.ts`) para imágenes.

**Evidencias en el repo**

- 📂 `back/supabase/functions/` — código fuente Deno de cada función.
- 📄 `back/supabase/functions/_shared/rate-limit.ts`, `cors.ts`, `groq.ts`, `supabase-admin.ts` — helpers compartidos.
- 📄 `back/src/middleware/auth.ts`, `back/src/middleware/checkCenterAccess.ts` — middlewares del histórico Express.

**Limitaciones / líneas futuras**

- Mover importaciones masivas a colas (`pg_cron` + función background).
- Telemetría OpenTelemetry exportada a Datadog/Sentry.

---

### Desarrollo de interfaces — Carmen Campos Fernández

**Objetivos del módulo cubiertos**

- **SPA Angular 19.2 standalone components** con routing, guards (`auth`, `guest`, `role`) e interceptores HTTP en [`front/`](../front/).
- **Diseño responsive y accesible** con **Tailwind CSS 3.4**, modo claro/oscuro persistente y tipografía / paleta coherente.
- **Internacionalización (i18n)** con `ngx-translate` en tres idiomas: ES, EN, FR (`front/public/assets/i18n/`).
- **Componentes reutilizables**: `navbar`, `footer`, `language-selector`, `theme-toggle`, `profile-image-manager`, `error-toast`.
- **Gestión de estado reactivo** con Angular Signals + RxJS.
- **Cuadro de mando ejecutivo en Power BI** (`back/analytics/Power_Bi/MetaForce_Superadmin_Dashboard.pbix`) consumiendo los CSV exportados desde Supabase con KPIs visuales para el SUPERADMIN (usuarios activos, planes contratados, ingresos por centro, ocupación de clases, evolución de peso corporal, etc.).
- Estados de carga, vacío, error y éxito modelados con componentes y signals.

**Evidencias en el repo**

- 📂 `front/src/app/pages/` — `home`, `login`, `register`, `dashboard`, `users`, `centers`, `machines`, `clases`, `trainers`, `qr`, `qr-scanner`.
- 📂 `front/src/app/shared/components/` — componentes compartidos.
- 📂 `front/public/assets/i18n/` — `es.json`, `en.json`, `fr.json`.
- 📄 `front/docs/FE-ARCHITECTURE.md` — arquitectura del frontend.
- 📄 `back/analytics/Power_Bi/MetaForce_Superadmin_Dashboard.pbix` — dashboard Power BI.
- 📂 `front/documentation/` — Compodoc generado (componentes, módulos, rutas, *coverage*).

**Limitaciones / líneas futuras**

- Auditoría WCAG AA completa (en curso, ZAP cubre solo seguridad).
- Storybook / Playroom para catálogo visual del sistema de diseño.

---

### Servidores y APIs — Juan Antonio García Gómez

**Objetivos del módulo cubiertos**

- **API REST documentada con Swagger / OpenAPI** (histórico Express: `back/src/config/swagger.ts`).
- **Backend serverless Supabase** con Edge Functions desplegadas en `https://qybgnrlszozjhimewkel.supabase.co/functions/v1/<name>`.
- **Autenticación JWT** con Supabase Auth + **custom access token hook** (`public.custom_access_token_hook`) que inyecta `app_role` como claim, evitando confiar en `user_metadata`.
- **Autorización por RLS** en todas las tablas con helpers `app.is_staff()` / `app.is_superadmin()` que leen `auth.jwt()->>'app_role'`.
- **Seguridad HTTP**: Helmet, CORS por origen, *rate-limit*, validación Zod en cada endpoint, hashing bcrypt para legacy.
- **Auditoría de seguridad OWASP ZAP** documentada (`back/docs/ZAP_RUNBOOK_2026-05.md`, `back/docs/security-audit-2026-05.md`, contexto en `back/zap/`).
- **Despliegue Vercel** para Angular (`https://meta-force-psi.vercel.app/`) y Supabase Cloud para backend.
- **Versionado** con Git, GitHub, submódulos y CI/CD.

**Evidencias en el repo**

- 📄 `back/src/app.ts`, `back/src/index.ts`, `back/src/config/swagger.ts` — bootstrap del Express histórico.
- 📂 `back/src/modules/` — `auth`, `users`, `centers`, `machines`, `memberships`, `exercises`, `workouts`, `diets`, `access` (controladores + servicios + esquemas Zod).
- 📂 `back/supabase/functions/` — endpoints serverless en producción.
- 📄 `back/docs/ARCHITECTURE.md` — arquitectura del backend.
- 📄 `back/SECRETS.md` — guía de variables de entorno y secretos.
- 📄 `back/docs/security-audit-2026-05.md` — informe de auditoría.

**Limitaciones / líneas futuras**

- Migrar Swagger a OpenAPI 3.1 servido desde Edge Function `health` para que apunte siempre al runtime activo.
- Pruebas de carga (k6 / Artillery) sobre las Edge Functions críticas.

---

### Sistemas de gestión empresarial — Miguel Ángel Ronda Carracao

**Objetivos del módulo cubiertos**

- Modelo de **negocio SaaS B2C** sobre el dominio gimnasio: catálogo de planes (`subscription_plans`), duraciones (`plan_durations`), precios (`plan_prices`), **facturación con numeración estable** (`invoices` + test `invoice_numbering.test.sql`), entidad fiscal emisora (`issuer_settings`), ofertas (`special_offers`).
- Flujo completo de **alta → suscripción → factura PDF → email**: Edge Functions `subscription-email` e `invoice-pdf` + bucket `invoices` en Supabase Storage (`20260509120000_invoices_storage_bucket.sql`).
- **ETL en Python** (`back/analytics/extract_data.py`) con `pandas` + `supabase-py` que extrae tablas core (`User`, `BodyWeightRecord`, `Exercise`, `ExerciseRecord`, `user_roles`, `subscription_plans`, `plan_durations`, `subscriptions`, `invoices`) y las vuelca a CSV en `back/analytics/exports/` para alimentar Power BI.
- **Cuadro de mando ejecutivo en Power BI** (`MetaForce_Superadmin_Dashboard.pbix`) con KPIs operativos y financieros del negocio: usuarios, planes contratados, ingresos, ocupación, retención.
- **Trazabilidad financiera**: `invoice_numbering.test.sql`, `subscriptions_chain.test.sql`.

**Evidencias en el repo**

- 📂 `back/analytics/` — `extract_data.py`, `requirements.txt`, `exports/*.csv`, `Power_Bi/MetaForce_Superadmin_Dashboard.pbix`.
- 📄 `back/scripts/apply-analytics-rls.js` — políticas RLS para los roles analíticos.
- 📄 Migraciones SCRUM-18: `back/supabase/migrations/20260508213746_subscriptions_core.sql`, `20260508214606_subscriptions_rls_gate.sql`, `20260509120000_invoices_storage_bucket.sql`, `20260509121000_invoice_pdf_email_dispatch.sql`, `20260509123000_me_subscriptions_api.sql`.
- 📂 `back/supabase/tests/` — `invoice_numbering.test.sql`, `subscriptions_chain.test.sql`.

**Limitaciones / líneas futuras**

- Conector directo de Power BI a PostgreSQL/Supabase con refresco programado (hoy se trabaja con CSV).
- Cuentas analíticas separadas con RLS específico para `data-analyst`.

---

### Empresa e Iniciativa Emprendedora II — no aplica

> **No procede entregable** para EIE II en este proyecto, según lo confirmado por el equipo (no se ha cursado el módulo con la profesora **Rosa Carmen Alcázar Rosal** durante este curso para este grupo).

---

## Repositorios de código

| Capa | Repositorio | Tecnologías |
|------|-------------|-------------|
| Repositorio guía / wrapper con submódulos | [`Mariogarluu/Meta-Force-App`](https://github.com/Mariogarluu/Meta-Force-App) *(este repo)* | Git submodules + documentación |
| Frontend web | [`Mariogarluu/Meta_Force_front`](https://github.com/Mariogarluu/Meta_Force_front) | Angular 19 · TypeScript 5.7 · Tailwind 3.4 · ngx-translate · Supabase JS |
| Backend (Supabase + histórico Express) | [`Mariogarluu/Meta_Force_back`](https://github.com/Mariogarluu/Meta_Force_back) | Supabase (PostgreSQL · Edge Functions Deno · Auth · Storage) · Prisma · Express 5 |
| App Android | [`Mariogarluu/Meta_Force_kotlin`](https://github.com/Mariogarluu/Meta_Force_kotlin) | Kotlin 2.0 · Jetpack Compose · Hilt · Retrofit · DataStore |
| Analítica BI | Carpeta [`back/analytics/`](../back/analytics/) en el repo de backend | Python · Pandas · `supabase-py` · Power BI |

---

## Despliegue y entornos

| Componente | URL / referencia | Observaciones |
|------------|------------------|---------------|
| **Web producción** | <https://meta-force-psi.vercel.app/> | Desplegada en Vercel. SPA con `vercel.json` reescrito para rutas Angular. |
| **API Supabase** | `https://qybgnrlszozjhimewkel.supabase.co` | Edge Functions en `/functions/v1/<name>`. RLS activo. |
| **App Android** | APK / Bundle | *Pendiente:* enlace al release en GitHub. |
| **Compodoc** | `front/documentation/` | *Pendiente:* desplegar como sitio estático accesible durante la evaluación. |

### Credenciales de prueba para evaluación

> ⚠️ **Pendiente:** generar usuarios de prueba (SUPERADMIN, ADMIN_CENTER y CLIENT) y publicarlos aquí. (Ver [Información que falta por aportar](#información-que-falta-por-aportar).)

```
SUPERADMIN  → email: __PENDIENTE__   password: __PENDIENTE__
ADMIN_CENTER → email: __PENDIENTE__  password: __PENDIENTE__
CLIENT      → email: __PENDIENTE__   password: __PENDIENTE__
```

---

## Documentación unificada (Confluence)

El espacio de documentación del proyecto vive en Confluence:

- **Espacio:** [Meta-Force (`MetaForce`)](https://meta-force.atlassian.net/wiki/spaces/MetaForce) (ID `196612`).
- **Home del espacio:** [Meta-Force — Home](https://meta-force.atlassian.net/wiki/spaces/MetaForce/pages/196720/Meta-Force).
- **Informe de migración Express → Supabase (SCRUM-138):** [enlace a Confluence](https://meta-force.atlassian.net/wiki/spaces/MetaForce/pages/10420225/Informe+migración+Express+→+Supabase+—+Sprint+actual+SCRUM-138+-+2026-04-25).

📄 **PDF unificado de la documentación:** `readme/docs/Meta-Force_Confluence.pdf` *(pendiente de generar y subir)*.

> El PDF debe consolidar las páginas del espacio Confluence `MetaForce` (arquitectura, migraciones, decisiones técnicas, runbooks de seguridad ZAP, notas de release).

---

## Gestión del proyecto (Jira)

- **Proyecto Jira:** `SCRUM` — *meta-force* en `https://meta-force.atlassian.net`.
- **Última issue creada al cierre de esta documentación:** `SCRUM-180`.
- **Épicas principales:**
  - [`SCRUM-2` — Historias_Usuario](https://meta-force.atlassian.net/browse/SCRUM-2) — owner: Samuel García Ruiz.
  - [`SCRUM-65` — Maquetación](https://meta-force.atlassian.net/browse/SCRUM-65) — owner: Salvador Bueno González.
  - [`SCRUM-147` — Infraestructura y Ecosistema Meta-Force](https://meta-force.atlassian.net/browse/SCRUM-147) — owner: Mario García Luque.
- **Tipos de issue usados:** Epic, Historia, Tarea, Subtarea, Error, *kotlin* (custom para el módulo Android).
- **Iteraciones destacadas:** SCRUM-18 (suscripciones + facturación + QR firmado), SCRUM-138 (migración Express → Supabase), hardening de roles y RLS.

📄 **PDF resumen de gestión Jira:** `readme/docs/Meta-Force_Jira.pdf` *(pendiente de generar y subir)*.

> El PDF debe incluir, como mínimo: alcance del proyecto, listado de épicas, tablero (To Do / In Progress / Done), reparto de tareas por persona (Mario, Salvador, Samuel), estado de cierre y *burndown* del sprint final.

---

## Documentación de código (Compodoc)

La documentación técnica del frontend Angular se genera con **Compodoc** y queda versionada en el directorio [`front/documentation/`](../front/documentation/) del repositorio de frontend.

- Genera la documentación:

```bash
cd front
npx @compodoc/compodoc -p tsconfig.doc.json -d documentation
```

- Sirve la documentación localmente durante la defensa:

```bash
cd front
npx @compodoc/compodoc -s -d documentation -r 8080
```

- 🌐 **Servidor Compodoc desplegado:** *pendiente* (URL pública estable que estará activa durante el periodo de evaluación). Ver [Información que falta por aportar](#información-que-falta-por-aportar).

> Compodoc cubre componentes, módulos, servicios, guards, interceptores, rutas y *coverage* de comentarios JSDoc del frontend Angular.

---

## Stack tecnológico

### Frontend web — Angular 19

| Tecnología | Versión | Propósito |
|-----------|---------|-----------|
| Angular | 19.2 | Framework SPA standalone |
| TypeScript | 5.7 | Lenguaje |
| Tailwind CSS | 3.4 | Estilos utility-first + tema dark/light |
| RxJS · Signals | 7.8 / 19 | Estado reactivo |
| ngx-translate | 17.0 | i18n (ES / EN / FR) |
| html5-qrcode | 2.3 | Generación y escaneo QR |
| @supabase/supabase-js | latest | Cliente Auth + DB + Storage |
| Compodoc | — | Documentación de código |

### Backend — Supabase + Express histórico

| Tecnología | Versión | Propósito |
|-----------|---------|-----------|
| Supabase PostgreSQL | 15 | Base de datos gestionada |
| Supabase Auth | — | JWT + custom hook `app_role` |
| Supabase Storage | — | Buckets `invoices`, `profile-images` |
| Supabase Edge Functions | Deno 1.x | Endpoints serverless TS |
| Prisma | 6.18 | Modelo de datos declarativo |
| Express | 5.1 | Servicio histórico (legacy) |
| Zod | 4.1 | Validación de entrada |
| Helmet · CORS · rate-limit | — | Hardening HTTP |
| Winston | 3.18 | Logging |
| Jest | 30.2 | Test runner |
| OWASP ZAP | — | Auditoría de seguridad |

### App Android — Kotlin

| Tecnología | Propósito |
|-----------|-----------|
| Kotlin 2.0 + Jetpack Compose | UI declarativa Material 3 |
| Dagger Hilt | Inyección de dependencias |
| Retrofit 2 + OkHttp3 + Gson | Cliente HTTP REST |
| Jetpack DataStore | Persistencia local de sesión |
| Coroutines + StateFlow | Asincronía y estado |
| Coil | Carga de imágenes |
| Android API 26 → 36 | Compatibilidad |

### Analítica BI

| Tecnología | Propósito |
|-----------|-----------|
| Python 3 + Pandas | ETL contra Supabase |
| supabase-py | Cliente Supabase para Python |
| Power BI Desktop | Cuadro de mando Superadmin |

---

## Arquitectura y diagrama general

```
                       ┌────────────────────────────┐
                       │   Power BI Superadmin       │
                       │   (.pbix + CSV exports)     │
                       └──────────────┬──────────────┘
                                      │
                       ┌──────────────┴──────────────┐
                       │   Python ETL (Pandas)        │
                       │   back/analytics/extract.py  │
                       └──────────────┬──────────────┘
                                      │ SERVICE_ROLE_KEY
                                      ▼
   ┌──────────────────────┐   ┌─────────────────────────────┐   ┌──────────────────────┐
   │ Angular 19 (Vercel)  │──▶│  Supabase Cloud             │◀──│ Android (Kotlin)     │
   │ meta-force-psi...    │   │  - PostgreSQL + RLS         │   │ Retrofit + Hilt      │
   │ Tailwind · i18n ·    │   │  - Auth (JWT + app_role)    │   │ Compose + DataStore  │
   │ Signals · Compodoc   │   │  - Storage (invoices, img)  │   │                      │
   └──────────┬───────────┘   │  - Edge Functions (Deno)    │   └──────────────────────┘
              │ supabase-js   │     ai-chat · qr-sign ·     │
              │               │     invoice-pdf · ...        │
              ▼               │  - Migrations SQL versionadas│
   ┌──────────────────────┐   └──────────────┬──────────────┘
   │ HTML5-QRCode +       │                  │ HTTPS
   │ QR Scanner (cámara)  │                  ▼
   └──────────────────────┘   ┌─────────────────────────────┐
                              │ Resend (email) · Cloudinary │
                              │ Groq (LLM IA)               │
                              └─────────────────────────────┘
```

> Detalle completo: [`back/docs/ARCHITECTURE.md`](../back/docs/ARCHITECTURE.md) y [`front/docs/FE-ARCHITECTURE.md`](../front/docs/FE-ARCHITECTURE.md).

---

## Cómo levantar el proyecto en local

```bash
# 1. Clonar con submódulos
git clone --recursive https://github.com/Mariogarluu/Meta-Force-App.git
cd Meta-Force-App

# 2. Frontend
cd front
cp .env.example .env   # configurar SUPABASE_URL y ANON KEY
npm install
npm start              # http://localhost:4200

# 3. Backend Supabase (opcional, en local)
cd ../back
cp .env.example .env   # rellenar DATABASE_URL, SUPABASE_SERVICE_ROLE_KEY, JWT_QR_SECRET, RESEND_*
npm install
npx supabase start
npx supabase db push
npx supabase functions deploy

# 4. App Android
#   Abrir kotlin/ con Android Studio (JDK 17, SDK 26+)
#   Ajustar BASE_URL en di/NetworkModule.kt si apunta a otro entorno
#   Run ▶

# 5. Analytics (Power BI ETL)
cd ../back/analytics
pip install -r requirements.txt
python extract_data.py   # genera CSV en exports/
#   Abrir Power_Bi/MetaForce_Superadmin_Dashboard.pbix y refrescar fuentes
```

> Los detalles de despliegue, secretos y troubleshooting están en los README de cada submódulo: [`front/README.md`](../front/README.md), [`back/README.md`](../back/README.md), [`kotlin/README.md`](../kotlin/README.md).

---

## Información que falta por aportar

Estos elementos **no están aún en el repositorio** y son necesarios antes de la fecha de exposición (5 de junio de 2026) para no penalizar en la rúbrica:

1. **Capturas del producto** en `readme/img/` (web, móvil, Power BI, diagrama de arquitectura). Mínimo 6 capturas referenciadas en la sección [Capturas y vistas del producto](#capturas-y-vistas-del-producto).
2. **PDF unificado de Confluence** (`readme/docs/Meta-Force_Confluence.pdf`) — exportar el espacio `MetaForce` o las páginas clave.
3. **PDF resumen de gestión Jira** (`readme/docs/Meta-Force_Jira.pdf`) — debe incluir tablero, épicas, tareas por persona y *burndown* / cierre de sprint.
4. **URL pública del servidor Compodoc desplegado** (Vercel/Netlify/GitHub Pages) que estará viva durante la evaluación.
5. **Credenciales de prueba** (`SUPERADMIN`, `ADMIN_CENTER`, `CLIENT`) accesibles para el tribunal.
6. **Enlace al APK / release de la app Android** en GitHub Releases del repo `Meta_Force_kotlin` (si se va a entregar instalable).
7. **Diagrama de arquitectura en imagen** (PNG/SVG) en `readme/img/08-arquitectura.png` — el ASCII actual sirve como borrador.
8. **Confirmar** si el repositorio guía oficial declarado al profesorado es este (`Mariogarluu/Meta-Force-App`) o uno público distinto, para enlazar en la **tabla maestra** de `exposiciones_proyecto_intermodular_25_26_2DAM_M`.
9. **(Opcional)** Vídeo demo de 60–90 s subido a YouTube / Drive como plan B por si falla la red durante la demo en vivo.

> Una vez disponibles, actualizar las secciones correspondientes y hacer commit en este repo (`readme/`).

---

<div align="center">

Documento mantenido por el **equipo Meta Force** — 2.º DAM mañana · CPIFP Alan Turing · Curso 2025/2026.

</div>
