# Sistema Universitario de Administración de Clubes (SUAC)

> **“Una plataforma web para modernizar y simplificar la gestión de clubes estudiantiles en la ESPOL, conectando a directivos, miembros y personal universitario en un solo lugar.”**

Este proyecto tiene como objetivo desarrollar una consola de administración que modernice la gestión de los clubes estudiantiles de la ESPOL, reemplazando los procesos manuales con documentos Word y Excel por una plataforma web centralizada. La aplicación permitirá a los miembros inscribirse y mantener actualizada su información, a los directivos organizar planes de actividades y evidencias semestrales, y al personal universitario acceder de forma directa y segura a la documentación requerida.

De esta manera, se busca optimizar la comunicación, estandarizar la entrega de reportes oficiales y reducir la carga administrativa tanto de los clubes como de la universidad, garantizando trazabilidad, transparencia y facilidad de uso.

## **Fases de Alto Nivel del Proyecto**

El diagrama tiene **6 fases principales**. Asumiendo un equipo de unos 5 desarrolladores, cada fase puede ejecutarse en **sprints de 2 a 4 semanas**, con flujos de trabajo superpuestos.

1. **Planificación y Requisitos**
   - Finalizar los casos de uso, los roles de usuario y las restricciones con las partes interesadas de la universidad.
   - Definir los criterios de aceptación y confirmar los requisitos de informes/exportación.
   - Elegir la plataforma (SvelteKit + backend, probablemente Node/Drizzle/Postgres, solución de almacenamiento de archivos, autenticación, etc.).
   - Entregables: Especificación de requisitos, documentación de arquitectura, línea base del diagrama de Gantt.

2. **Configuración de la Arquitectura y la Infraestructura**
   - Configuración del repositorio, estrategia de ramificación, pipeline de CI/CD. - Configuración de infraestructura en la nube (p. ej., Cloudflare para frontend + Servidor de ESPOL para backend + almacenamiento).
   - Diseño del esquema de base de datos (usuarios, clubes, elecciones, actividades, documentos).
   - Estrategia de autenticación (JWT/OAuth, correo electrónico y contraseña, SSO si es necesario).

3. **Funciones principales (MVP)**
   - Gestión de usuarios (registro, inicio de sesión, gestión de perfiles).
   - Roles y permisos (personal, directivo, miembro).
   - Membresía del club (unirse a clubes, aprobar roles, validar directivos).
   - Gestión de información básica del club (enlaces, mentor, información de contacto).

4. **Funciones avanzadas**
   - Planes semestrales (exportación de Excel para la planificación de actividades + CRUD).
   - Informes semestrales (envío de evidencias de actividades, galería de fotos, exportación masiva de archivos zip).
   - Sistema de elecciones estudiantiles (votaciones, resultados).
   - Panel de control del personal con notificaciones.

5. **Módulo de Documentos y Exportación**
   - Generación de PDF (carga de cartas firmadas, estatutos actualizados).
   - Exportación de archivos estructurados (generación de CSV y XLSX: miembros, actividades planificadas y actividades ejecutadas).
   - Búsqueda y filtrado por parte del personal para todos los conjuntos de datos.
   - Descarga de paquetes de archivos (ZIP con fotos).

6. **Pruebas, control de calidad y entrega**
   - Pruebas unitarias y de integración, cobertura de CI.
   - Auditoría de seguridad (roles aplicados, almacenamiento seguro de archivos).
   - Pruebas de rendimiento (escalabilidad para múltiples clubes).
   - Prueba piloto de usuario (UAT) (prueba piloto con personal universitario).
   - Documentación y capacitación.
   - Plan de implementación y mantenimiento.

---

## **Hitos**

Estos son los principales hitos que deben incluirse en el diagrama de Gantt:

- M1: Acta de constitución y requisitos del proyecto aprobados (fin de la planificación).
- M2: CI/CD e infraestructura completamente funcional.
- M3: Acceso basado en roles y autenticación completada.
- M4: Flujos de trabajo de gestión de clubes finalizados (clubes, socios, directivas).
- M5: Plan semestral + funcionalidad de informes finalizada.
- M6: Módulo de elecciones en funcionamiento.
- M7: Todas las exportaciones de documentos están operativas (PDF, CSV, XLSX, ZIP).
- M8: Aprobación de QA + UAT.
- M9: Lanzamiento de producción.

---

## **Dependencias** (importante para la secuenciación de Gantt)

- **Roles y autorización de usuario →** deben configurarse antes de cualquier caso de uso de funciones.
- **Datos de clubes y socios →** necesarios antes de elecciones, actividades planificadas/pasadas y exportaciones.
- **Módulo de documentos →** depende de que se finalicen los datos de clubes, actividades y usuarios.
- **Panel de control del personal →** depende de que se implementen las exportaciones + eventos de notificaciones.
- **Evidencia fotográfica + exportación ZIP →** depende de los informes de actividad.

---

## **Estructura de Desglose del Trabajo (Tareas)**

### Planificación (1-2 semanas)

- Taller de requisitos con el personal de la universidad.
- Definir las características del MVP vs. V2.
- Borrador del esquema de la base de datos (entidades: usuarios, clubes, elecciones, actividades, evidencia).
- Alineación con el diseño (maquetas de interfaz de usuario, Figma).

### Arquitectura e Infraestructura (2 semanas, puede solaparse con la planificación)

- Configurar el proyecto SvelteKit, ESLint, Prettier.
- Configurar CI/CD (GitHub Actions, Vercel, Docker si es necesario).
- Base de datos + canalización de migraciones.
- Esqueleto de autenticación (posiblemente BetterAuth).

### Características principales (4-6 semanas)

- Inicio de sesión/registro de usuario + CRUD de perfil.
- Middleware de roles/permisos. - CRUD del club (las directivas gestionan la información del club).
- Altas y aprobaciones de miembros.

### Funciones avanzadas (4-6 semanas)

- CRUD de actividades semestrales (directivas).
- Subir y etiquetar evidencias de actividad.
- Visor de galería de fotos.
- Flujo de trabajo electoral (crear elecciones, votar, tabular).
- Servicio de notificaciones al personal (correo electrónico/telegram + en la aplicación).

### Documentos y exportación (3-5 semanas)

- Generación de PDF (carta firmada, estatutos).
- Informes CSV/XLSX (miembros, planes de actividades, actividades pasadas).
- API de exportación backend + portal de descargas para el personal.
- Generación de fotos en formato ZIP.

### Control de calidad, entrega, lanzamiento (3-4 semanas)

- Pruebas automatizadas (Vitest/Playwright).
- Ciclos manuales de control de calidad.
- Pruebas de carga (clubes con cientos de miembros).
- Pruebas UAT con clubes de muestra. - Despliegue final de producción + plan de reversión.

---

## **Cronograma estimado (con 5 desarrolladores, sprints ágiles)**

- Total: **~20–24 semanas (5–6 meses)** realista para una V1 sólida.
- Asignación de sprints (asumiendo sprints de 2 semanas):
- **S1–S2**: Planificación + Infraestructura.
- **S3–S5**: Funcionalidades principales.
- **S6–S8**: Funcionalidades avanzadas.
- **S9–S10**: Documentos y exportaciones.
- **S11–S12**: Control de calidad, UAT, Lanzamiento.
