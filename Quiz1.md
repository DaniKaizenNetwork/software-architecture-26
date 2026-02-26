# Análisis de Código Heredado y Documentación de Decisiones Arquitectónicas

## Propósito del ejercicio

El propósito de este ejercicio es evaluar la capacidad de análisis técnico sobre un sistema heredado, identificando problemas relacionados con seguridad, calidad del código y diseño arquitectónico. A partir de este análisis, se busca documentar decisiones de mejora mediante un **Architecture Decision Record (ADR)**, simulando un escenario real de trabajo en ingeniería de software.

El énfasis no está en desarrollar nuevas funcionalidades, sino en comprender el comportamiento del sistema existente, detectar riesgos técnicos y proponer soluciones fundamentadas, alineadas con buenas prácticas y estándares utilizados en la industria.

---

## Alcance y desarrollo del trabajo

El ejercicio se desarrolla en cuatro fases claramente definidas, que permiten abordar el sistema de manera progresiva y estructurada.

### FASE 1 — Levantamiento del ambiente

Se realizó la clonación del repositorio proporcionado y el despliegue de la aplicación utilizando contenedores Docker.  
El correcto funcionamiento del sistema se verificó mediante el endpoint de salud (`/health`), confirmando que el entorno estaba correctamente configurado y listo para ser analizado.

---

### FASE 2 — Auditoría del código fuente

Se llevó a cabo una revisión exhaustiva de los archivos Java del proyecto, evaluando el cumplimiento de principios de **Clean Code**, **SOLID** y buenas prácticas básicas de **seguridad**.

Durante esta auditoría se identificaron múltiples problemas críticos, entre ellos vulnerabilidades de inyección SQL, manejo inseguro de contraseñas, exposición de información sensible y deficiencias de diseño que afectan la mantenibilidad y escalabilidad del sistema.  
Los hallazgos fueron documentados de forma estructurada, indicando archivo, línea aproximada, principio violado y nivel de riesgo.

---

### FASE 3 — Pruebas funcionales

Se ejecutaron pruebas manuales contra los endpoints de autenticación (login y registro) utilizando herramientas de prueba HTTP.  
Estas pruebas permitieron validar el comportamiento real del sistema y confirmar que varias de las vulnerabilidades detectadas en la auditoría de código se manifiestan también a nivel funcional, como la exposición de hashes de contraseñas y validaciones insuficientes.

---

### FASE 4 — Documentación de decisiones arquitectónicas

Finalmente, se elaboró un **Architecture Decision Record (ADR)** en el que se justifica la necesidad de refactorizar el módulo de autenticación. En este documento se describen el contexto del sistema, las decisiones técnicas propuestas, las consecuencias esperadas y las alternativas consideradas.

El ADR permite dejar evidencia clara del razonamiento detrás de cada decisión, facilitando la comprensión del impacto técnico y arquitectónico de las mejoras propuestas.

---

## Resultado esperado

Como resultado final, se entrega un conjunto de documentos que reflejan un análisis crítico del sistema, respaldado por evidencia técnica obtenida mediante pruebas reales y una propuesta de refactorización clara, coherente y bien justificada.

Este ejercicio permite evaluar no solo conocimientos técnicos, sino también la capacidad de análisis crítico, toma de decisiones y comunicación técnica, competencias clave en el rol de un arquitecto o ingeniero de software.
