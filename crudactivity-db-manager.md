# CrudZaso DB Manager

# Contexto

**CrudZaso DB Manager** es una plataforma web que permite a los usuarios crear y administrar bases de datos de forma remota desde una única interfaz.

Cada usuario podrá registrarse en la plataforma, autenticarse y administrar sus propias bases de datos. Cada base de datos será completamente independiente de las demás y contará con su propia configuración, credenciales de acceso y estado operativo.

La plataforma ofrecerá soporte para diferentes motores de bases de datos, permitiendo al usuario escoger el motor al momento de crear una nueva instancia.

Los usuarios únicamente podrán administrar las bases de datos de su propiedad, mientras que los administradores tendrán control global sobre toda la plataforma.

---

# Objetivo

Desarrollar una aplicación web que permita administrar bases de datos de manera centralizada.

La plataforma deberá ofrecer funcionalidades para:

* Registro de usuarios.
* Inicio y cierre de sesión.
* Recuperación y cambio de contraseña.
* Administración del perfil del usuario.
* Creación, consulta, modificación y archivado de bases de datos.
* Administración de credenciales de acceso.
* Gestión del estado de las bases de datos.
* Notificaciones mediante correo electrónico.

---

# Tecnologías

La solución deberá construirse utilizando los temas vistos durante las primeras seis semanas del módulo.

El frontend deberá desarrollarse utilizando **Thymeleaf**.

Para el diseño de la interfaz podrá utilizarse cualquiera de los siguientes frameworks CSS:

* Bootstrap
* Tailwind CSS
* Bulma
* Materialize CSS

La aplicación deberá ejecutarse mediante contenedores Docker.

---

# Gestión de Usuarios

Cada usuario deberá almacenar como mínimo la siguiente información:

* Nombre
* Apellidos
* Correo electrónico
* Contraseña
* Rol
* Estado
* Fecha de registro
* Fecha de última actualización

## Roles

* USER
* ADMIN

## Estados

* ACTIVE
* BLOCKED

---

# Autenticación

La plataforma deberá permitir:

* Registro de nuevos usuarios.
* Inicio de sesión.
* Cierre de sesión.
* Recuperación de contraseña mediante correo electrónico.
* Cambio de contraseña.
* Modificación de contraseña únicamente para usuarios autenticados.
* Protección de todas las rutas privadas.
* Restricción de acceso según el rol del usuario autenticado.

---

# Correos Electrónicos

El sistema deberá enviar un correo electrónico automáticamente cuando ocurra alguno de los siguientes eventos:

* Registro exitoso.
* Recuperación de contraseña.
* Cambio exitoso de contraseña.
* Creación de una nueva base de datos.
* Archivado de una base de datos.
* Bloqueo de un usuario.
* Desbloqueo de un usuario.

---

# Bases de Datos

Cada base de datos representa una instancia administrada por la plataforma.

Como mínimo deberá almacenar:

* Nombre
* Descripción
* Motor de base de datos
* Usuario de conexión
* Contraseña de conexión
* Puerto de conexión
* Estado
* Fecha de creación
* Fecha de última actualización
* Usuario propietario

## Motores soportados

* MySQL
* PostgreSQL
* MongoDB

## Estados

* CREATED
* RUNNING
* STOPPED
* ARCHIVED

---

# Reglas de Negocio

## Usuarios

* El correo electrónico debe ser único dentro del sistema.
* Un usuario bloqueado no podrá iniciar sesión.
* Un usuario únicamente podrá visualizar y administrar las bases de datos de su propiedad.
* Los administradores podrán visualizar y administrar todos los usuarios registrados.
* Los administradores podrán visualizar y administrar todas las bases de datos existentes.

---

## Bases de Datos

* Cada usuario podrá tener como máximo **tres (3) bases de datos activas**.
* No podrán existir dos bases de datos con el mismo nombre pertenecientes al mismo usuario.
* Cada base de datos únicamente podrá utilizar un motor de base de datos.
* Una vez creada, el motor de base de datos no podrá modificarse.
* El sistema deberá generar automáticamente un usuario de conexión para cada base de datos.
* El sistema deberá generar automáticamente una contraseña segura para cada base de datos.
* Las credenciales generadas deberán ser únicas dentro de la plataforma.
* Cada base de datos deberá utilizar un puerto exclusivo.
* Dos bases de datos activas no podrán compartir el mismo puerto.
* El puerto asignado no podrá modificarse una vez creada la base de datos.
* Una base de datos archivada no podrá editarse.
* Una base de datos archivada no podrá volver a activarse.
* Únicamente el propietario o un administrador podrán consultar la información detallada de una base de datos.
* Únicamente el propietario o un administrador podrán modificar una base de datos.
* Únicamente el propietario o un administrador podrán archivarla.

---

# Panel Administrativo

Los administradores deberán disponer de funcionalidades para:

## Gestión de Usuarios

* Consultar todos los usuarios registrados.
* Buscar usuarios por nombre o correo electrónico.
* Bloquear usuarios.
* Desbloquear usuarios.
* Consultar la información detallada de cualquier usuario.

## Gestión de Bases de Datos

* Consultar todas las bases de datos registradas.
* Buscar bases de datos por nombre, propietario o motor.
* Visualizar el estado actual de cualquier base de datos.
* Cambiar el estado de una base de datos.

## Estadísticas

El panel administrativo deberá mostrar como mínimo:

* Total de usuarios registrados.
* Total de usuarios activos.
* Total de usuarios bloqueados.
* Total de bases de datos registradas.
* Cantidad de bases de datos por motor.
* Cantidad de bases de datos por estado.
* Cantidad de bases de datos creadas por cada usuario.

---

# Interfaz

La aplicación deberá contar, como mínimo, con las siguientes páginas:

## Públicas

* Inicio
* Inicio de sesión
* Registro
* Recuperación de contraseña

## Privadas

* Dashboard
* Perfil de usuario
* Listado de bases de datos
* Detalle de una base de datos
* Creación de una nueva base de datos
* Edición de una base de datos
* Cambio de contraseña

## Administración

* Dashboard administrativo
* Gestión de usuarios
* Gestión de bases de datos
* Estadísticas generales

---

# Consideraciones

* Toda la información deberá persistirse en una base de datos relacional.
* La aplicación deberá implementar autenticación y autorización utilizando Spring Security.
* Las contraseñas de los usuarios deberán almacenarse cifradas.
* Las credenciales de conexión generadas para las bases de datos no podrán repetirse.
* Todas las operaciones deberán realizarse desde la interfaz web desarrollada con Thymeleaf.
* El acceso a cada funcionalidad deberá respetar el rol del usuario autenticado.
* El sistema deberá impedir que un usuario consulte o modifique recursos pertenecientes a otro usuario.
* La aplicación deberá ejecutarse correctamente utilizando Docker.
* El proyecto deberá implementar una arquitectura por capas, separando adecuadamente la lógica de negocio, persistencia y presentación.
