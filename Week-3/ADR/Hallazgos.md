# FASE 1 — Levantamiento del ambiente

El proyecto fue clonado y desplegado correctamente utilizando contenedores Docker.  
Durante esta fase se verificó que todos los servicios definidos en el entorno de ejecución iniciaran sin errores y que la aplicación estuviera accesible a través del puerto configurado.

Como criterio de validación, se comprobó el correcto funcionamiento del endpoint de salud del sistema, confirmando que la aplicación responde de manera satisfactoria y se encuentra operativa.

**Resultado:** Levantamiento del ambiente exitoso.
{"ok":true}
---

# FASE 2 — Auditoría del código

En esta fase se realizó una revisión detallada del código fuente con el objetivo de identificar problemas relacionados con **Clean Code**, **principios SOLID** y **seguridad básica**.  
El análisis se enfocó principalmente en los componentes encargados de la autenticación, el registro de usuarios y el acceso a la base de datos, ya que estos representan puntos críticos desde el punto de vista de seguridad y arquitectura.

A continuación, se presentan los principales hallazgos detectados durante la auditoría.

## Tabla de Hallazgos — Auditoría Clean Code y Seguridad

| # | Descripción del problema                                                                 | Archivo               | Línea aprox. | Principio violado                                   | Riesgo |
|---|-------------------------------------------------------------------------------------------|-----------------------|--------------|----------------------------------------------------|--------|
| 1 | Construcción de consultas SQL mediante concatenación de strings, permitiendo SQL Injection | UserRepository.java   | ~20          | Seguridad básica (SQL Injection)                   | Alto   |
| 2 | Inserción de datos en base de datos usando SQL concatenado con input del usuario          | UserRepository.java   | ~34          | Seguridad básica (SQL Injection)                   | Alto   |
| 3 | Uso de MD5 para hashing de contraseñas, algoritmo obsoleto y criptográficamente inseguro  | AuthService.java      | ~63          | Seguridad básica (hashing débil)                   | Alto   |
| 4 | Exposición del hash de la contraseña en la respuesta del endpoint de login                | AuthService.java      | ~28 y ~35    | Principio de mínima exposición de datos            | Alto   |
| 5 | Credenciales de base de datos definidas directamente en el código fuente                  | UserRepository.java   | ~12–14       | Seguridad / Clean Code                             | Alto   |
| 6 | Atributos públicos en la entidad `User`, rompiendo el encapsulamiento                     | User.java             | ~4–6         | Clean Code / Programación Orientada a Objetos     | Medio  |
| 7 | Uso de nombres de parámetros poco descriptivos (`u`, `p`, `e`) en el controlador          | AuthController.java   | ~20 y ~27    | Naming (Clean Code)                                | Bajo   |
| 8 | Acceso directo a la base de datos sin una capa de abstracción adecuada                    | UserRepository.java   | ~17          | SRP / DIP (SOLID)                                  | Medio  |
| 9 | Falta de cierre de conexiones, Statements y ResultSet, generando posibles fugas de recursos| UserRepository.java   | ~16–29       | Buenas prácticas / Manejo de recursos              | Medio  |
|10 | Validación de contraseñas extremadamente débil (solo longitud mayor a 3 caracteres)      | AuthService.java      | ~44          | Seguridad básica                                   | Medio  |

# FASE 3 — Pruebas Funcionales

Para validar el comportamiento real del sistema, se ejecutaron pruebas manuales utilizando **Postman**, interactuando directamente con la API expuesta en `http://localhost:8080`.  
Estas pruebas permitieron confirmar varios de los problemas detectados durante la auditoría estática del código.

---

## 🧪 Pruebas en el documento Fase3.docs
