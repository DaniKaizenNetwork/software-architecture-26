# Análisis de Código Heredado y Decisiones de Refactorización

## Propósito del ejercicio

Este ejercicio tiene como finalidad evaluar la capacidad de análisis técnico sobre un sistema heredado, identificando problemas relacionados con seguridad, calidad de código y diseño arquitectónico. A partir de dicha evaluación, se busca documentar decisiones de mejora utilizando un Architecture Decision Record (ADR), simulando un escenario real de ingeniería de software.

El énfasis del ejercicio no está en desarrollar nuevas funcionalidades, sino en comprender el comportamiento del sistema existente, detectar riesgos técnicos y proponer soluciones fundamentadas alineadas con buenas prácticas de la industria.

## Alcance del trabajo

El ejercicio se desarrolla en cuatro etapas principales:

1. **Levantamiento del ambiente**  
   Se clona el repositorio proporcionado y se despliega la aplicación utilizando contenedores Docker, verificando su correcto funcionamiento mediante un endpoint de salud.

2. **Auditoría del código fuente**  
   Se revisan los archivos Java del proyecto para identificar violaciones a principios de Clean Code, SOLID y prácticas básicas de seguridad. Los hallazgos se documentan de forma estructurada, indicando su impacto y nivel de riesgo.

3. **Pruebas funcionales**  
   Se ejecutan pruebas manuales contra los endpoints de autenticación para validar el comportamiento real del sistema y evidenciar vulnerabilidades como exposición de datos sensibles, validaciones débiles y riesgos de inyección SQL.

4. **Documentación de decisiones arquitectónicas**  
   Se construye un ADR donde se justifica la necesidad de refactorización, se describen las decisiones técnicas tomadas y se analizan sus consecuencias y alternativas.

## Resultado esperado

Como resultado final, se entrega un conjunto de documentos que reflejan un análisis crítico del sistema, evidencia técnica obtenida mediante pruebas reales y una propuesta de mejora clara, coherente y bien justificada desde el punto de vista arquitectónico.
