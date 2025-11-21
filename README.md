# Sistema de Registro de Usuarios

---

## Introducción, Finalidad y Caso de Estudio

El presente documento describe el **Sistema de Registro de Usuarios**, una aplicación fundamental diseñada para gestionar la creación, acceso y administración de cuentas de usuario.

###  Finalidad y Propósito General
El propósito del sistema es proporcionar una **plataforma sencilla y segura** donde un usuario pueda crear una cuenta, acceder mediante sus credenciales y actualizar su información personal cuando sea necesario. El sistema busca **facilitar la administración de datos de usuario** de forma simple y accesible.

### Evolución del Alcance

| Versión | Énfasis Principal | Funciones Clave | Exclusiones Notables |
| :--- | :--- | :--- | :--- |
| **V1 (Inicial)** | Funcionamiento esencial y simple. | Registro, Inicio de Sesión, Modificación básica de perfil. | Verificación de correo, Recuperación de contraseña, Almacenamiento remoto. |
| **V2 (Mejorada)** | Experiencia más completa, segura y moderna. | Añade Verificación de correo, Recuperación de contraseña y Mayor seguridad. | Integración con redes sociales o autenticación biométrica. |

---

##  Requerimientos Funcionales y No Funcionales – Versión 1

### Propósito y Alcance Específico
Esta versión inicial define el funcionamiento esencial del sistema. El usuario final es una persona con **habilidades básicas** en aplicaciones digitales y el uso es **ocasional**.

### Requerimientos Funcionales (V1)
| Descripción | Prioridad | Justificación |
| :--- | :--- | :--- |
| Permitir al usuario registrarse ingresando nombre, correo y contraseña. | Alta | Es la función principal del sistema. |
| Validar que el correo no esté previamente registrado. | Alta | Evita duplicidad de cuentas. |
| Permitir inicio de sesión con correo y contraseña. | Alta | Es esencial para acceder al perfil. |
| Mostrar mensaje de error si las credenciales son incorrectas. | Media | Mejora usabilidad. |
| Permitir modificar datos básicos del perfil. | Media | Mantiene la información actualizada. |

### Requerimientos No Funcionales (V1)
| Descripción | Categoría | Prioridad |
| :--- | :--- | :--- |
| El sistema deberá tener una interfaz simple y comprensible. | Usabilidad | Alta |
| El tiempo de respuesta al iniciar sesión no debe superar los **2 segundos**. | Rendimiento | Alta |
| Los datos deben mantenerse almacenados correctamente hasta modificación del usuario. | Fiabilidad | Media |

---

##  Requerimientos Funcionales y No Funcionales – Versión Mejorada (V2)

### Propósito y Alcance Específico
El propósito es garantizar que los usuarios puedan crear cuentas, autenticarse y modificar su información de manera **intuitiva y protegida**, extendiendo las funciones básicas a una experiencia completa.

### Requerimientos Funcionales (V2)
1.  Permitir al usuario registrarse ingresando datos básicos (nombre, correo, contraseña).
2.  Validar que el correo no esté previamente registrado.
3.  **Enviar correo de verificación** para activar la cuenta.
4.  Permitir inicio de sesión con correo y contraseña.
5.  Mostrar mensajes de error cuando las credenciales sean incorrectas.
6.  Permitir **modificar datos del perfil** (nombre, foto, correo, contraseña).
7.  Permitir **recuperar contraseña** mediante correo electrónico.
8.  Permitir **cerrar sesión** de manera segura.
9.  Guardar cambios automáticamente en la base de datos o almacenamiento local.

### Requerimientos No Funcionales (V2)
* **Usabilidad:** Interfaz clara y accesible para cualquier nivel de usuario.
* **Seguridad:** Almacenamiento de contraseñas con cifrado; validación robusta de datos de entrada.
* **Rendimiento:** Tiempos de carga menores a **2 segundos**.
* **Compatibilidad:** Disponible para navegadores modernos y dispositivos móviles.
* **Fiabilidad:** Protección contra pérdida de datos y fallos inesperados.

---

##  Plan de Pruebas: Sistema de Registro de Usuarios

Las pruebas de software son el mecanismo esencial para garantizar que los requerimientos se cumplan y la calidad del sistema.

### Casos de Prueba (Ejemplo)
| Funcionalidad | Descripción del Caso de Prueba | Precondiciones | Resultado Esperado | Prioridad |
| :--- | :--- | :--- | :--- | :--- |
| **Permitir registrarse** | Verificar el registro exitoso de un nuevo usuario con datos válidos. | El usuario no está registrado. | El sistema registra el nuevo usuario y redirige a la pantalla de inicio de sesión o perfil. | Alta |
| **Validación de campos** | Verificar la validación de campos obligatorios vacíos. | El usuario no está registrado. | El sistema muestra un mensaje de error claro en cada campo vacío. | Alta |
| **Formato de correo** | Verificar el formato de correo electrónico inválido (ej: sin "@" o ".com"). | El usuario no está registrado. | El sistema muestra un mensaje de error indicando un formato de correo inválido. | Alta |
| **Duplicidad de correo** | Intentar registrar un usuario con un correo ya existente. | Un usuario con el correo `test@example.com` ya existe. | El sistema muestra un mensaje de error: "El correo ya está registrado.". | Alta |
| **Inicio de Sesión** | Verificar inicio de sesión exitoso con credenciales válidas. | El usuario `user@test.com` está registrado. | El usuario es autenticado y redirigido a la pantalla de Perfil. | Alta |
| **Error de Contraseña** | Intentar iniciar sesión con contraseña incorrecta. | El usuario `user@test.com` está registrado. | El sistema muestra un mensaje de error claro como: "Credenciales incorrectas.". | Media |

---

## Plan de Mantenimiento de Software

El propósito de este plan es asegurar la longevidad, estabilidad y evolución del sistema de registro.

### Tipos de Mantenimiento y Justificación

| Tipo de Mantenimiento | Descripción y Enfoque | Justificación Principal |
| :--- | :--- | :--- |
| **Correctivo** | Modificaciones reactivas para corregir fallos o errores de lógica que impidan el registro o el inicio de sesión. | Es esencial para la **Fiabilidad** (RNF-03). Asegura que los requisitos principales se ejecuten sin errores, manteniendo la confianza. |
| **Adaptativo** | Modificaciones para que el sistema siga operando en un entorno cambiante (nuevas versiones de navegadores, frameworks o librerías). | Garantiza que la **Usabilidad** no se degrade, protegiendo contra la obsolescencia tecnológica. |
| **Perfectivo** | Mejoras a las funcionalidades existentes, optimización del **rendimiento** (ej. mantener el RNF de **2 segundos**) y la usabilidad. | Asegura que el sistema no solo funcione, sino que lo haga de manera eficiente y agradable con el tiempo. |
| **Evolutivo** | Adición de nuevas funciones o modificación de las existentes (ej. implementación de recuperación de contraseña). | Proporciona el marco para añadir las funciones que se excluyeron inicialmente, permitiendo el **crecimiento** del sistema. |

---

##  Reflexión sobre el Control de Versiones (Git)

El Control de Versiones (VCS) es un mecanismo crítico de **gestión del riesgo, colaboración y trazabilidad** para el Sistema de Registro de Usuarios.

### 1. Gestión del Riesgo y Mantenimiento Correctivo
* **Trazabilidad:** Un VCS permite identificar exactamente qué línea de código cambió, quién lo hizo y cuándo.
* **Reversión (Rollback):** Si se detecta un error crítico (requiriendo **Mantenimiento Correctivo**), el VCS permite retroceder el código de producción a un estado estable anterior en cuestión de segundos, minimizando el tiempo de inactividad y cumpliendo con el requisito de **Fiabilidad**.

### 2. Soporte al Mantenimiento Evolutivo y Adaptativo
* **Bifurcación (Branching):** El VCS permite crear **ramas de desarrollo** para trabajar en nuevas funcionalidades (**Mantenimiento Evolutivo**), como la `feature/recuperacion-contraseña`, sin riesgo de romper la versión estable (rama `main`).
* **Integración de Entornos:** Ayuda a gestionar los cambios necesarios para el **Mantenimiento Adaptativo**, asegurando que el código se comporte de manera consistente.

### 3. Colaboración y Registro Histórico
* **Registro Histórico:** Cada *commit* (cambio guardado) actúa como un **diario de desarrollo**, documentando el progreso y las decisiones de diseño.
* **Integración de Tareas:** Los *commits* se pueden enlazar a tareas del Plan de Pruebas, vinculando directamente el código a la gestión de calidad y la corrección de fallos.

