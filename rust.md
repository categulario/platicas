# Curso de rust

## Introducción

* ¿qué es?
    - paradigma
    - compilación
* Instalación
* Variables y mutabilidad
* Tipos de dato
* Estructuras de control

## ¿Por qué debería usar rust en vez de C?

* Contar con herramientas de alto nivel y aun así estar programando bajo nivel
    - abstracciones (como las características funcionales)
    - traits
    - manejo de errores checado en tiempo de compilación
* Concurrencia sin condiciones de carrera
* Software menos propenso a errores sutiles (debido al estricto compilador)
* si alguna vez has tenido un Segmentation faul (core dumped)
* testing, construcción y dependencias integrados en el entorno de desarrollo
* documentación bien organizada y accesible
* código mantenible a la larga
* estabilidad sólida como la roca
* no null-pointer exception, todas las referencias son válidas en tiempo de compilación
* si quiero que el hecho de que mi programa compile sea garantía de que no va a tronar en tiempo de ejecución
* en rust la diferencia entre paso por valor y por referencia nunca se escapa

## cosas qué mencionar

* cómo compilar directo con el compilador
* cómo compilar con cargo
* canales de rust (stable, nightly, ...)
* cargo check
* inicializar un arreglo con [ini; length]
* let s = "salomón"; println!("Caracteres: {}, bytes: {}", s.chars().count(), s.len());
* qué es owned (en contraste con referencias de las cuales no eres *dueño* de la memoria)
    - al pasar owned a una función se pierde control en el scope donde la función se llama
* sumar cadenas
* https://doc.rust-lang.org/std/iter/index.html#the-three-forms-of-iteration
    - let hm: HashMap<_, _> = vec![ (1, 2), ].into_iter().collect();

# Programa

* Fundamentos y sintaxis.
* Diseño de un programa con Rust, pruebas.
* Borrow y Ownership.
* Enumeraciones y manejo de errores.
* Structs, Traits y lifetimes
* Concurrencia
