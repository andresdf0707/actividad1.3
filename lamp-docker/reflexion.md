# Reflexion — MiniApp de Tareas

**Nombre:** Andres dominguez fernandez

## 1. Diferencia GET y POST, con un ejemplo de tu código donde usarías cada uno.

GET: Pide parametros para que van en la URL.
POST: envia estos parametros y se usa cuando algo cambia

## 2. ¿Qué es una cabecera HTTP? Pon un ejemplo de cabecera de petición y otro de respuesta que hayas visto hoy.

es un par nombre:valor con datos de la peticion o de la respuesta, 
peticion: el navegador manda la cookie en cada peticion
respuesta: provoca la redireccion tras el login

## 3. Explica con tus palabras qué es una cookie a nivel técnico: dónde se guarda, cómo viaja y quién puede leerla.

es un pequeño texto clave que el servidor le pide al navegador que guarde. Se guarda en el navegador del usuario y la puede tanto leer como editar el propio usuario.

## 4. Explica con tus palabras qué es una sesión y en qué se diferencia de una cookie. ¿Dónde se guarda cada una?

la sesion son los datos dle usuario como el id, email y rol, y se guarda en el servidor
el navegador solo guarda una cookie que contiene un identificador para que el servidor encuentre esos datos

## 5. Cita los tres mecanismos de persistencia usados en la MiniApp y para qué sirve cada uno.

la base de datos guarda de forma permanente a los usuarios, hashes y tareas
sesion: mantiene al usuario logueado entre las peticiones, lo que dure la sesion
cookie: recuerda el email del usuario durante 30 dias

## 6. Diferencia autenticación vs autorización con un ejemplo de tu código.

autenticacion: busca el email del usuario y verifica la contraseña con password_verify
autorizacion: comprueba que puede hacer el usuario, por ejemplo, el usuario admin puede entrar al panel de administracion porque el admin.php tiene requireAdmin()

## 7. ¿Por qué llamamos a session_regenerate_id(true) tras el login?

evita que un atacante le de un phpsessid que conozca y esperar a que haga login y poder usar ese mismo id, al cambiar el id justo despues de autenticarse, el antiguo ppsessid deja de servir, el true borra la sesion vieja del servidor.

## 8. ¿Qué pasaría si un usuario edita su cookie PHPSESSID a otro valor? ¿Y si edita ultimo_email?

pues que el servidor no encuentra una sesion con ese id asi que devuelve null, y te redirige al login, y si edita ultimo_email, cambia el valor que aparece prefijado en el campo email del login

## 9. ¿Qué significa que PHPSESSID tenga HttpOnly? ¿Qué ataque mitiga?

hace que el navegador no permite que javascript lea la cookie asi no puede leer el phpsessid.
