# ADR-001: Refactorización del módulo de autenticación por problemas críticos de seguridad y Clean Code

## Contexto

El sistema actual implementa un módulo de autenticación que permite a los usuarios registrarse y autenticarse contra una base de datos PostgreSQL. Durante la revisión del código heredado se identificaron múltiples vulnerabilidades de seguridad y malas prácticas de diseño que afectan directamente la confidencialidad de la información y la mantenibilidad del sistema.

Entre los principales problemas encontrados se incluyen el uso de SQL construido por concatenación, lo que expone al sistema a ataques de SQL Injection, el almacenamiento y uso de contraseñas con hashing inseguro (MD5), y la exposición de datos sensibles como el hash de la contraseña en las respuestas del API. Además, las credenciales de la base de datos se encuentran hardcodeadas tanto en el código como en archivos de configuración.

Desde el punto de vista de Clean Code y SOLID, se observan violaciones al principio de responsabilidad única, ya que la lógica de negocio, acceso a datos y manejo HTTP están fuertemente acoplados. Estos problemas representan un riesgo alto en un entorno productivo y generan deuda técnica que afecta al equipo de desarrollo y a los usuarios finales.

## Decisión

1. Se reemplazará la construcción manual de consultas SQL por consultas parametrizadas mediante `PreparedStatement`, eliminando la posibilidad de SQL Injection.
2. Se sustituirá el uso de hashing MD5 por un algoritmo seguro como BCrypt o Argon2, y se eliminará cualquier exposición de hashes o credenciales en las respuestas del API.
3. Se refactorizará el módulo de autenticación separando responsabilidades en capas (Controller, Service y Repository), aplicando el principio de Responsabilidad Única (SRP).
4. Se mejorará la validación de contraseñas y se dejará de enviar credenciales mediante query parameters, utilizando estructuras más seguras para el intercambio de datos.

## Consecuencias

### Consecuencias positivas
- Reducción significativa de riesgos de seguridad como SQL Injection y fuga de credenciales.
- Mejora en la protección de contraseñas de los usuarios.
- Código más limpio, modular y fácil de mantener.
- Mayor claridad en la arquitectura del módulo de autenticación.

### Consecuencias negativas / riesgos
- Incremento temporal del esfuerzo de desarrollo debido al refactor.
- Posibles regresiones si no se cuenta con pruebas automatizadas.
- Necesidad de migrar contraseñas existentes a un nuevo esquema de hashing.

## Alternativas consideradas

1. Reescribir completamente el módulo de autenticación desde cero.  
   Descartado debido al alto costo y al riesgo de introducir nuevos errores en un sistema existente.

2. Aplicar únicamente parches de seguridad mínimos sin refactorizar el diseño.  
   Descartado porque no soluciona la deuda técnica ni los problemas de mantenibilidad a largo plazo.


