# Tus microservicios en caldo de iguana

## Arquitectura monolítica

* Una base de código tiene _casi_ todo
* Con una adecuada modularización razonar sobre la arquitectura es simple
* Desarrollar generalmente implica conocer más partes del sistema y/o lógica de negocio
* Escalamiento vertical: aviéntale más recursos al servidor hasta que aguante vara.
* el desempeño depende de la construcción del sistema y cantidad de recursos
* el cuello de botella está en algorimos, procesador e IO

## Microservicios

* Se van separando en componentes que realizan tareas específicas
* la arquitectura puede ser un grafo dirigido no plano cruzado y revuelto
* cada componente se puede desarrollar por separado en un lenguaje de programación distinto
* escalar implica levantar más instancias de los servicios bajo demanda
* el desempeño depende de la latencia de red
* el cuello de botella está en el balanceador de carga

## Y un humilde programador, ¿qué debería hacer?

**Pensar**

_¿Qué es lo que más hace sentido?_

No dejarse llevar por la corriente, la gente está bien confundida allá afuera

Una vez empezado como microservicio no hay vuelta atrás. O se está condenado a un camino de penurias.

No todo debe ser un microservicio, no chingues

Tienes que pensar en el balanceo de carga

Seguro necesitarás un sistema de mensajería (rabbit, redis, kafka)

El escalamiento horizontal es una linda mentira

## Quiúbole con... Docker

* En efecto, es mejor que una máquina virtual
* es lindo poder poner cualquier servicio en casi cualquier servidor, con muy poca configuración
* adiós a los problemas de versiones de software, paquetes sin soporte etcétera
* peeero
    - no es una solución a todos los problemas de versiones
    - por favor, aprende a configurar un servicio, no le hace daño a nadie y es re fácil con systemd
    - quizá lo único que necesitas es un nginx y un archivo .service te lo juro
* y cuándo sí, pues
    - para hacer portable una arquitectura de servicios de forma sencilla
    - utilizar un software de una versión muy particular cuya configuración en el SO sería de otra forma muy complicada

Una vez me encontré una empresa que metía el frontend en un contenedor... el pinche estático culiao frontend...

## Kubernetes

* casi como resultado lógico de la existencia de docker...
* orquestar contenedores, levantar instancias, balancear la carga
* integración contínua, la pura brujería
* peero
    - si lo quieres usar por tu cuenta necesitas el hardware, el poder de cómputo
    - más seguramente lo estarás usando através de un producto de amazon, microsoft o google
    - a menos que seas una empresa con mucho varo, y hardware
    - al final la tendencia es a concentrar el poder de cómputo en los grandes, se va nuestro sueño dorado de la web descentralizada para todos

## El mejor amigo del desarrollador web: nginx

* no expongas mil puertos al exterior, no importa cuántas aplicaciones tengas, o en qué lenguajes estén. (O en qué contenedores estén)
* en su configuración por defecto es más eficiente que apache, en parte por htaccess
* seamos sinceros, sus archivos de configuración son más fáciles de leer
* sirve como balanceador de carga... por si ocupas
* aprende a configurar SSL una vez, usa sin importar el framework.
* Ponle nombre a las cosas! usa subdominios!
* ¿sabías que lo puedes programar con lua?
* no he encontrado un solo caso donde poner un nginx al frente de todo no sea una buena idea

## Qué hago con mi arquitectura

* No te dejes llevar por la corriente
* Seguro lo que estás haciendo es suficientemente bueno, por ahora
* no uses algo que no entiendes completamente

    **Gracias**
