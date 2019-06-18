class: center, middle

# ¿Puede un sistema de tipos mejorar mi código de bajo nivel?

por `@categulario`

---
class: middle

Rust es un lenguaje de programación compilado, de bajo nivel, que busca busca cumplir la trifecta:

* seguridad
* concurrencia
* velocidad

---
class: center, middle

En **rust** se cumple que

# Si compila, funciona*

*Aplican restricciones

---
class: center, middle

## I beg you pardon?

---
class: center, middle

## ¿Qué puede salir mal?

--
* Problemas de concurrencia (condiciones de carrera)

--
* Corrupción de la memoria (apuntadores nulos, overflows...)

--
* Violaciones de tipos (casting a un tipo incorrecto)

--
* Errores en general (E/S, validación...)

---
class: center, middle

## ¿Y cómo lo resuelves?

---
class: middle

# Problemas de concurrencia

--
* Haciendo que cada valor en memoria tenga exactamente un *dueño*.

--
* Representando en el sistema de tipos la mutabilidad

--
* Asegurando en tiempo de compilación y para cada valor que exista un y solo un
    - escritor
    - cualquier cantidad de lectores

--
* Representando en el sitema de tipos si es seguro mandar un valor a un hilo

---
class: middle

# Corrupción de la memoria

--
* `null` no existe, existe un tipo de dato `Option<T>`

--
* se verifican que cada referencia a un valor sea válida en tiempo de compilación

--
* se verifica que todo acceso a un vector o arreglo sea dentro de sus límites


---
class: middle

# Errores en general

--
* no existen las excepciones, se manejan códigos de error.

--
* el sistema de tipos te obliga a consumir un error si existe la posibilidad de uno

--
* `Result<T, E>`

---
class: middle

# Violaciones de tipos

* El sistema de tipos es fuerte, estático y cumple el **principio de sustitución de Liskov**.

## ¿Principio de sustitición de kién?

Let ϕ (x) be a property provable about objects x of type T. Then ϕ ( y ) should be true for objects y of type S where S is a subtype of T.

Bárbara Liskov, 1987

---
class: center, middle

# Entonces muchas cosas van al rededor de los tipos...

## Eso ha de requerir muchas anotaciones de tipos...

---
class: middle

# Sistema de tipos Hindley Milner

Sistema de tipos para el cálculo lambda (más cercano a la programación funcional). ~1969.

Indica un conjunto de reglas con las que puedes anotar algunos tipos en un código fuente y permitir al compilador deducir el resto, usando el tipo más general que cumple con las características del comportamiento requerido para el tipo.

Existen algoritmos que pueden hacer esto en un tiempo razonable.

---
class: middle

# Tipos y subtipos en rust

--
* Hay `Traits` que definen comportamiento

--
* Hay tipos de dato (escalares, structs, enums) que implementan los traits

--
* No programación orientada a objetos en el sentido estricto

--
* `&mut T` es un subtipo de `&T`

--
* el tiempo de vida de una variable es parte de su tipo

--
* `&'a T` es subtipo de `&'b T` si `'a` es más corto que `'b`

---
class: middle

## ¿Y las restricciones apá?

El código puede fallar en exactamente estos casos:

--
* errores de lógica

--
* lugares donde el código puede fallar explícitamente

---
class: middle

## ¿Por qué debería usar rust en vez de C?

--
* Contar con herramientas de alto nivel y aun así estar programando bajo nivel
    - abstracciones
    - gestor de dependencias
    - Básicamente esas características que envidias de lenguajes modernos que no tienes en C

--
* Concurrencia sin condiciones de carrera
    - no se te puede olvidar liberar un lock de un mutex

--
* si alguna vez has tenido un Segmentation fault (core dumped)

--
* la memoria es liberada exactamente cuando ya no es usada

--
* no null-pointer exception, todas las referencias son válidas en tiempo de compilación

--
* una biblioteca estándar muy completa

--
* por que se rompe la %"$#%" en tiempo de ejecución con C

---
class: middle

## ¿Por qué debería usar rust en vez de C? #2

--
* testing, construcción y dependencias integrados en el entorno de desarrollo
    - Aleluya!

--
* documentación bien organizada, accesible y completa

--
* código mantenible a la larga

--
* sólido como la roca
    - ¿Mencioné que si compila funciona?

--
* en rust la diferencia entre paso por valor y por referencia nunca se escapa

--
* La increíble comunidad

--
* genéricos

--
* soporte UTF8 nativo

---
class: center, middle

### Imagina que acabas de escribir ese programa concurrente que tomó meses para computar las soluciones a quetzalcóatl sabe qué modelo estadístico para predecir el comportamiento de noseque pez... y truena con segmentation fault

¿Y ahora?

---
class: center, middle

## Citas

Pascal is like wearing a straightjacket, C is like playing with knives, and C++ is juggling flaming chainsaws.

Rust is like doing parkour while suspended on strings & wearing protective gear. Yes, it will sometimes look a little ridiculous, but you'll be able to do all sorts of cool moves without hurting yourself.

---
class: center, middle

Ahora si, tírenle a matar con las

# Preguntas

---
class: center, middle

Gracias
