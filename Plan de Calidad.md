# Plan de Calidad para el Desarrollo del Proyecto SmarTrip

**Equipo de Desarrollo:** Angel Antonio Lopez Perez, Kimberly Mendoza Hernandez, Arcángel González Cruz  
**Fecha de Emisión:** 10/09/2025  
**Versión del Plan:** 1.0

## 1. Introducción y Alcance

### 1.1. Propósito del Documento
Este documento constituye el Plan de Calidad formal para el proyecto SmarTrip. Su propósito es definir las actividades, estándares, métricas y procedimientos que el equipo de desarrollo implementará para asegurar que el producto final—una dApp para alertas comunitarias con Zero-Knowledge Proofs (ZKPs) en la blockchain de Stellar—cumpla con los más altos estándares de funcionalidad, seguridad, usabilidad y confiabilidad.

### 1.2. Alcance del Proyecto
El alcance de este plan de calidad cubre todas las fases del ciclo de vida del software para el proyecto ZARC:

- **Fase de Diseño:** Arquitectura del sistema, diseño de contratos inteligentes (Stellar Soroban) y algoritmos ZK.
- **Fase de Desarrollo:** Implementación del frontend (React Native/JS), backend, contratos inteligentes y pruebas ZK.
- **Fase de Pruebas:** Unitarias, de integración, de seguridad, de rendimiento y de aceptación por parte del usuario (UAT).
- **Fase de Despliegue:** Liberación en la red de prueba (testnet) y posteriormente en la red principal (mainnet) de Stellar.
- **Fase de Mantenimiento:** Soporte post-lanzamiento y gestión de incidentes.

---

## 2. Gestión de la Calidad del Proyecto: Estrategia y Métricas

### 2.1. Estrategia de Calidad
Nuestra estrategia se basa en un modelo de Calidad por Diseño (Quality by Design), integrando actividades de aseguramiento de calidad desde la concepción del proyecto. Adoptamos un enfoque ágil donde la calidad se verifica en cada sprint, utilizando la IA como herramienta de apoyo para la generación de pruebas, análisis de código y optimización de procesos.

### 2.2. Roles y Responsabilidades

- **Angel Antonio Lopez Perez (Líder de Calidad):** Responsable de la ejecución de este plan, coordinación de revisiones y reporte de métricas.
- **Kimberly Mendoza Hernandez (Arquitecta de Software):** Responsable de la calidad del diseño arquitectónico y de las revisiones técnicas de los componentes críticos (ZK, Smart Contracts).
- **Arcángel González Cruz (Desarrollador Senior):** Responsable de implementar las pruebas unitarias y de integración, y de cumplir con las convenciones de código.

### 2.3. Métricas de Calidad Clave (KQIs)
Definimos métricas cuantificables y con objetivos claros para medir el éxito cualitativo del proyecto.

| Categoría | Métrica | Objetivo | Herramienta de Medición |
|-----------|---------|----------|-------------------------|
| Calidad de Código | Cobertura de Pruebas Unitarias | > 90% para contratos inteligentes y librerías ZK | Mocha/Chai, Coverage.py |
| Calidad Funcional | Tasa de Fallos en Pruebas de Regresión | < 2% por build | CI/CD Pipeline (GitHub Actions) |
| Calidad de Seguridad | Score en Auditoría de Seguridad | > 9.5/10 en un audit formal del SC y ZK | Reporte de firma externa (ej: Halborn) |
| Satisfacción del Usuario | Net Promoter Score (NPS) Post-UAT | > +50 en pruebas con la comunidad | Encuestas de Usabilidad |

---

## 3. Procedimientos y Actividades de Calidad

### 3.1. Procedimientos de Revisión

- **Revisión de Requisitos (RR):** Todos los épicas/user stories relacionadas con privacidad (ZK) y transacciones (Stellar) serán revisadas en una sesión formal con al menos dos miembros del equipo y un advisor de la SCF. Se utilizará una lista de verificación (checklist) basada en los atributos de calidad de ISO 25010.
- **Revisión de Diseño de Arquitectura (ADR):** El diseño de componentes críticos se documentará en un Architectural Decision Record (ADR) y será revisado por la Arquitecta. Se evaluarán patrones contra OWASP Top 10 y mejores prácticas para dApps.
- **Revisión de Código (Code Review):** Es mandatorio para todo commit. Se utilizarán Pull Requests en GitHub. El código de los contratos inteligentes y ZK requiere al menos 2 aprobaciones antes del merge. Se fomentará el uso de herramientas de IA (como GitHub Copilot) para sugerir mejoras y detectar antipatrones durante la revisión.

### 3.2. Políticas de Pruebas
Nuestra política dicta que las pruebas deben ser automáticas, repetibles y ejecutadas en el pipeline de CI/CD.

- **Pruebas Unitarias:** Cubrirán toda lógica de negocio. Los contratos inteligentes deben alcanzar el 90% de cobertura. Se usarán frameworks específicos de Soroban.
- **Pruebas de Integración:** Se probará la interacción completa: Frontend -> Backend -> Smart Contract -> Red Stellar (testnet). Se automatizarán con herramientas como Jest y Puppeteer.
- **Pruebas de Seguridad:**
  - **Análisis Estático de Seguridad (SAST):** Escaneo automático con SonarQube y Slither.
  - **Análisis Dinámico (DAST):** Escaneo de la API REST con OWASP ZAP.
  - **Auditoría Formal:** Se contratará una auditoría de seguridad por una firma especializada antes del despliegue en mainnet.
- **Pruebas de Rendimiento y Carga:** Se medirá el rendimiento de la generación de pruebas ZK y la latencia de las transacciones en la red bajo carga.
- **Pruebas de Usabilidad (UAT):** Se realizarán con un grupo de 10-15 miembros de una comunidad piloto. Se recopilará feedback mediante entrevistas y el sistema NPS.

---

## 4. Gestión de la Configuración y Liberación

### 4.1. Control de Versiones

- **Repositorio:** GitHub. Estructura con GitFlow simplificado: main (solo releases estables), develop (integración), feature/* (nuevas funcionalidades).
- **Protección de Ramas:** La rama main requerirá pull requests con al menos 1 aprobación y que todos los checks de CI/CD pasen exitosamente.

### 4.2. Gestión de Dependencias

- Se utilizará Dependabot para escanear y actualizar automáticamente las dependencias del proyecto, alertando sobre vulnerabilidades conocidas (CVEs).

### 4.3. Política de Liberación (Release Management)

- **Versionado Semántico (SemVer):** MAJOR.MINOR.PATCH (ej: v1.4.2).
- **Ciclo de Liberación:** Cada liberación a testnet se etiquetará con una versión pre-release (v1.0.0-rc.1). Solo después de pasar la UAT y la auditoría de seguridad se etiquetará una versión estable para mainnet.
- **Notas de Versión:** Cada release en GitHub incluirá changelog detallado con las nuevas funcionalidades, cambios y correcciones.

---

## 5. Gestión de Riesgos de Calidad

- **R1: Vulnerabilidades en el Contrato Inteligente.**
  - **Mitigación:** Auditoría externa, pruebas exhaustivas en testnet, implementación de un multi-signature para el despliegue.

- **R2: Bajo Rendimiento de las Pruebas ZK en Dispositivos Antiguos.**
  - **Mitigación:** Optimización de algoritmos, benchmarking continuo y definición de requisitos mínimos del dispositivo.

- **R3: Baja Adopción por Complejidad de la UI.**
  - **Mitigación:** Pruebas de usabilidad iterativas y diseño centrado en el usuario desde la fase inicial.

---

## 6. Documentación
La documentación es un producto de trabajo prioritario, no un subproducto.

- **Documentación Técnica:** Ubicada en /docs del repo. Incluirá ADRs, guía de instalación del entorno de desarrollo y API documentation (generada con Swagger/OpenAPI).
- **Documentación para el Usuario Final:** Manuales claros y concisos integrados en la aplicación (tooltips, tutoriales) y un portal web público.
- **Documentación de Operaciones (Runbook):** Procedimientos para desplegar, monitorear y responder a incidentes del sistema en producción.

---

## 7. Cronograma de Actividades de Calidad
Estas actividades se integrarán en el backlog del proyecto y se ejecutarán en cada sprint.

| Sprint | Actividades de Calidad Principales |
|--------|-------------------------------------|
| Sprint 1-2 | Definición de métricas, establecimiento de pipelines de CI/CD, revisión de requisitos. |
| Sprint 3-5 | Implementación de pruebas unitarias, inicio de revisiones de código, primer análisis SAST. |
| Sprint 6-8 | Pruebas de integración, pruebas de rendimiento iniciales, UAT con comunidad piloto (v1). |
| Sprint 9-10 | Auditoría de seguridad formal, pruebas de penetración, preparación para release a mainnet. |

---

## 8. Conclusión
Este plan de calidad servirá como la base para construir el proyecto ZARC con los más altos estándares de la industria, asegurando que no solo sea una prueba de concepto funcional, sino una herramienta confiable, segura y valiosa para las comunidades que pretende servir. El compromiso del equipo con la ejecución meticulosa de este plan es fundamental para el éxito del proyecto y para fortalecer la reputación de la Stellar Community Fund como un impulsor de innovación tecnológica robusta y de calidad.

---

## Referencias Bibliográficas (APA 7th Edition)

- SEI. (2018). CMMI for Development, Version 2.0. Carnegie Mellon University.
- SOFTEX. (2005). MoProSoft: Modelo de Procesos para la Industria del Software v. 1.3.
- ISO/IEC 25010:2011. (2011). Systems and software engineering — Systems and software Quality Requirements and Evaluation (SQuaRE) — System and software quality models.
- ZARC. (2024). Sistema de Alerta y Respuesta Comunitaria con ZK. Stellar Community Fund Proposal.
