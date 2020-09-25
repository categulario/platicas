# Wasm en rust (y una pequeña historia de éxito de separación de menesteres)

## Qué es wasm?

- es un formato binario que se puede distribuir en navegadores (aunque no está limitado a eso)
- define interacción con las APIs del navegador
- ofrece una forma de utilizar un lenguaje que no sea javascript

## Por qué rust?

- los tipos
- ya lo estaba usando en mi proyecto
- rust es la ostia

## El proyecto

- la pizarra, una aplicación de escritorio para dibujar
- consta de un backend que tuve la dicha de desacoplar
- la implementación de la interfaz es independiente

## Primeras impresiones

- altibajos
- vete webpack, no te quiero
- el primer contacto dio la impresión de muchísima facilidad
- documentación accesible, amplia, ejemplos concretos que son de mucha utilidad
- una vez sabiendo navegar el API y qué esperar de ella hacer cosas es _casi_ natural.
- luego el bajón de no saber cómo hacer algo en particular
    - caso del Element que quiero que sea HtmlCanvasElement
- segunda impresión negativa respecto a la ergonomía
    - convertir entre tipos de rust<->javascript no se siente tan cómodo
    - los closures son una cosa digna de verse
    - los objetos como Element, Node, HtmlCanvasElement, Window, Document, etc son structs, no traits, entonces hay que hacer otras cosas para convertirlos.

## Cosas que hice bien con la pizarra

- separar el "backend" de la implementación del frontend
- establecer una clara barrera y una API que defina las interacciones posibles
    - .zoom_in(&mut self)
    - .set_color(&mut self)
    - .draw_commands(&self)
- definir tipos internos apropiados para cosas cuya implementación puede cambiar
- no hacer que el funcionamiento del backend dependa de las restricciones del frontend

## Pequeño tour de wasm en rust

- wasm-pack (el empaquetador, se usa para compilar en vez (sobre de?) de cargo)
- wasm-bindgen (la única dependencia que tengo por ahora)
- web-sys (la documentación de este proyecto tiene todas las APIs que necesitas)
- https://rustwasm.github.io/docs/book/game-of-life/setup.html (libro introductorio, con ejemplo del juego de la vida)
- https://rustwasm.github.io/docs/wasm-bindgen/ El libro de wasm en rust, ponlo bajo tu almohada, completísima referencia
- https://rustwasm.github.io/docs/wasm-pack/ Libro de la herramienta usada para empaquetar/compilar

## Impresiones finales

- wasm en web es un nicho, algo que está genial que esté ahí pero quizá no te llegue a impactar en tu día a día
- rust rifa, para variar
- portar código a wasm es fácil si está apropiadamente separado.
- rust compila más rápido para wasm que para escritorio .-.
