<!-- vista previa ctrl-k + v -->
<!-- publicar en github para entregar -->


*León Gómez, Sergio*

# Proyecto DWEC: Aplicación web (Informe técnico)

## Modelos de ejecución

### Modelos de ejecución cliente-servidor

#### Modelo de ejecución sincrónico / tradicional

El cliente envía una solicitud al servidor y espera una respuesta antes de continuar con cualquier otra tarea. La comunicación es directa y secuencial.

Ejemplo: Solicitud de datos a una base de datos SQL.

Un sistema de gestión de inventarios realiza una consulta SQL para obtener información sobre el stock de un producto.
La aplicación (cliente) envía una consulta SQL al servidor de la base de datos, espera hasta que el servidor de la base de datos responde con los datos solicitados.
La información del stock se muestra en la interfaz de la aplicación.

**Ventajas**: Simplicidad en la implementación y fácil de depurar.

**Desventajas**: Puede causar bloqueos si el servidor tarda en responder, afectando la experiencia del usuario.


#### Modelo de ejecución asíncrono

El cliente envía una solicitud al servidor y puede continuar con otras tareas sin esperar la respuesta inmediata. La respuesta del servidor se maneja de manera independiente cuando llega.

Ejemplo: Aplicación de correo electrónico como *Gmail*.

Envías un correo electrónico a través de *Gmail*.
La aplicación (cliente) envía el correo al servidor de *Gmail / Google* y te permite seguir utilizando otras funciones de la aplicación sin esperar la confirmación de entrega.
El servidor de *Gmail / Google* procesa el correo y lo entrega al destinatario cuando esté disponible.
Recibes una notificación de que el correo ha sido enviado sin que la aplicación se haya bloqueado en ningún momento.

**Ventajas**: Mejora la eficiencia y la capacidad de respuesta del cliente.

**Desventajas**: Mayor complejidad en la implementación y manejo de respuestas.


#### Modelo de ejecución multihilo

El servidor puede manejar múltiples solicitudes de clientes simultáneamente utilizando múltiples hilos de ejecución.

Ejemplo: Servidor web de *Amazon* manejando múltiples compras.

Varias personas están comprando productos en *Amazon* al mismo tiempo.
El servidor de *Amazon* crea un nuevo hilo para cada solicitud de compra, permitiendo que múltiples compras se procesen simultáneamente.
Cada hilo maneja una solicitud de compra, procesando el pago y actualizando el inventario.
Los usuarios reciben confirmaciones de sus compras casi al mismo tiempo, sin retrasos significativos.

**Ventajas**: Mejora el rendimiento y la capacidad de manejar múltiples solicitudes concurrentes.

**Desventajas**: Mayor consumo de recursos y complejidad en la gestión de hilos.


#### Modelo de ejecución basado en eventos

El servidor maneja las solicitudes de los clientes en función de eventos, utilizando un bucle de eventos para procesar las solicitudes de manera no bloqueante.

Ejemplo: Servidor de Node.js manejando solicitudes de una aplicación de streaming como Netflix.

Estás navegando por el catálogo de Netflix y seleccionas una película para ver.
El servidor de Netflix, utilizando Node.js, maneja tu solicitud de manera no bloqueante a través de un bucle de eventos.
El servidor procesa la solicitud y comienza a transmitir la película sin bloquear otras solicitudes de otros usuarios.
La película comienza a reproducirse casi de inmediato, mientras otros usuarios también pueden seguir navegando y viendo contenido sin interrupciones.

**Ventajas**: Alta eficiencia y escalabilidad.

**Desventajas**: Requiere un enfoque diferente en la programación y puede ser más difícil de depurar.


#### Comparaciones
- **Sincrónico vs. Asíncrono**: El modelo sincrónico es más simple pero puede causar bloqueos, mientras que el modelo asíncrono mejora la eficiencia pero es más complejo de implementar.

- **Multihilo vs. Basado en Eventos**: El modelo multihilo utiliza múltiples hilos para manejar solicitudes concurrentes, lo que puede consumir más recursos, mientras que el modelo basado en eventos utiliza un único hilo con un bucle de eventos, lo que es más eficiente en términos de recursos pero requiere un enfoque de programación diferente.

#### ¿Cual usaría para mi aplicación?

El **modelo de ejecución basado en eventos**, sería útil para usar APIs externas para actualicen la información en tiempo real del clima y hora del lugar, así como lidiar con varios usuarios simultáneos mediante estos eventos, que de manera automática actualizarían su zona elegida.


## Lenguajes de programación web

El desarrollo web del lado del cliente está dominado principalmente por dos lenguajes: **JavaScript** y **TypeScript**. Ambos juegan un rol crucial en la creación de aplicaciones web modernas, aportando funcionalidades dinámicas e interactivas. Estas son las ventajas y desventajas de ambos:

### JavaScript

#### Ventajas:

- **Versatilidad**: JavaScript se puede utilizar tanto en el lado del cliente como en el servidor (con *Node.js*), lo que lo hace muy versátil.
- **Rapidez**: JavaScript se ejecuta directamente en el navegador del cliente, lo que puede hacer que las aplicaciones sean rápidas y responsivas.
- **Amplia** comunidad: Hay una gran cantidad de recursos, bibliotecas y frameworks disponibles, como *React* y *Angular*.
- **Facilidad de uso**: Es relativamente fácil de aprender y usar, especialmente para principiantes.

#### Desventajas:

- **Problemas de compatibilidad**: Diferentes navegadores pueden interpretar JavaScript de manera diferente, lo que puede causar problemas de compatibilidad.
- **Seguridad**: JavaScript puede ser vulnerable a ataques como Cross-Site Scripting (XSS).
- **Depuración**: La depuración puede ser complicada debido a la naturaleza dinámica del lenguaje.

### TypeScript

#### Ventajas:

- **Seguridad de tipos**: TypeScript permite la detección de errores en tiempo de compilación gracias a su sistema de tipos estáticos.
- **Mejores herramientas**: Ofrece una mejor experiencia de desarrollo con herramientas como autocompletado y refactorización confiable.
- **Organización del código**: Facilita la organización del código en proyectos grandes mediante el uso de clases, módulos y generics.
- **Compatibilidad con JavaScript**: TypeScript es un superconjunto de JavaScript, lo que significa que cualquier código JavaScript válido también es válido en TypeScript.

#### Desventajas:

- **Curva de aprendizaje**: Puede ser más difícil de aprender para desarrolladores que solo están familiarizados con JavaScript.
- **Compilación adicional**: Requiere un paso de compilación adicional, lo que puede añadir complejidad al flujo de trabajo.
- **Integración**: Puede haber complicaciones al integrar TypeScript en proyectos existentes de JavaScript.

#### ¿Cual usaría para mi aplicación?

**JavaScript**, ya que es el lenguaje web más utilizado en el lado cliente, y al tener familiaridad ya con este lenguaje, creo que podría exprimirlo más y sacarle partido para mi aplicación.


## Mecanismos de integración de lenguajes de marcas con lenguajes de programación de clientes web


### HTML y JavaScript/TypeScript

HTML (*HyperText Markup Language*) es el lenguaje de marcas más utilizado para estructurar el contenido de las páginas web. JavaScript y TypeScript se integran con HTML para crear aplicaciones web interactivas y dinámicas.

#### Mecanismos de integración:

**DOM** (*Document Object Model*): JavaScript y TypeScript pueden manipular el DOM, que es una representación estructurada del documento HTML. Esto permite modificar el contenido y la estructura de la página web en tiempo real.

**Eventos**: JavaScript y TypeScript pueden manejar eventos del usuario (como clics, movimientos del ratón, etc.) para interactuar con los elementos HTML.

**Atributos y propiedades**: Los lenguajes de programación pueden leer y modificar los atributos y propiedades de los elementos HTML para cambiar su comportamiento y apariencia.

**Plantillas**: Con frameworks como Angular (que usa TypeScript) y bibliotecas como React (que usa JavaScript), se pueden crear componentes reutilizables que combinan HTML y lógica de programación.


### XML y JavaScript/TypeScript

XML (*eXtensible Markup Language*) se utiliza para almacenar y transportar datos. Aunque no se usa directamente para la presentación en el navegador, se integra con JavaScript y TypeScript para manejar datos estructurados.

#### Mecanismos de integración:

**AJAX** (*Asynchronous JavaScript and XML*): Permite la comunicación asíncrona entre el cliente y el servidor, lo que permite actualizar partes de la página web sin recargarla completamente.

**Parsers**: JavaScript y TypeScript pueden usar parsers para leer y manipular datos XML, permitiendo la extracción y modificación de información.

**Transformaciones XSLT**: JavaScript puede aplicar transformaciones XSLT a documentos XML para convertirlos en HTML u otros formatos.

#### Ventajas:

- **Interactividad**: La integración permite crear aplicaciones web interactivas y dinámicas.
- **Actualización dinámica**: Se pueden actualizar partes de la página web sin recargarla completamente.
- **Reutilización**: Los componentes y plantillas permiten reutilizar código y mejorar la mantenibilidad.

#### Desventajas:

- **Complejidad**: La integración puede añadir complejidad al desarrollo y mantenimiento del código.
- **Rendimiento**: Manipular el DOM frecuentemente puede afectar el rendimiento de la aplicación.
- **Seguridad**: La manipulación del DOM y el uso de AJAX pueden introducir vulnerabilidades de seguridad si no se manejan adecuadamente.


## Evaluación de herramientas de programación para clientes web


### Editor de Código: Visual Studio Code (VS Code)

- **Familiaridad**: Como ya tengo experiencia con VS Code, me permitirá enfocarme más en el desarrollo de la aplicación que en aprender a usar un nuevo editor.
- **Extensibilidad**: VS Code cuenta con un ecosistema de extensiones muy variado, que puedo personalizar según mis necesidades. Puedo agregar extensiones para JavaScript, Prettier, y más.
- **Integración con Git**: Tiene soporte nativo para el control de versiones con Git, lo que facilita el seguimiento de cambios.
- **Terminal integrada**: Me permite ejecutar comandos directamente desde el editor, lo que simplifica la ejecución de scripts, la instalación de paquetes y la gestión del entorno de desarrollo.
- **Depuración**: Ofrece capacidades avanzadas de depuración que me ayudarán a identificar y solucionar problemas en mi código de manera eficiente.
  
### Framework: React

- **Interactividad y componentes**: React es ideal para construir interfaces de usuario interactivas y se basa en un enfoque de componentes que facilita la reutilización del código y su mantenimiento.
- **Ecosistema amplio**: La comunidad de React es extensa, y existen muchas bibliotecas y herramientas complementarias, como React Router (para la navegación) y Redux (para la gestión del estado), que puedo integrar fácilmente.
- **Virtual DOM**: React utiliza un Virtual DOM que mejora el rendimiento de las aplicaciones al minimizar las manipulaciones del DOM real, lo que es especialmente útil en mi aplicación, que requiere actualizaciones en tiempo real.
- **Facilidad de aprendizaje**: Si ya estoy familiarizado con JavaScript, aprender React es relativamente sencillo, lo que me permitirá comenzar a desarrollar más rápido.

### Biblioteca 1: Axios

- **Manejo de solicitudes HTTP**: Axios es una biblioteca popular para realizar solicitudes HTTP desde el cliente. Es fácil de usar y me permitirá manejar tanto solicitudes asíncronas como respuestas de manera eficiente.
- **Soporte para promesas**: Utiliza promesas, lo que facilita la gestión de operaciones asíncronas en comparación con otras bibliotecas, y se integra bien con el flujo de trabajo de React.
- **Intercepción de solicitudes y respuestas**: Me permitirá interceptar solicitudes y respuestas, lo que es útil para agregar encabezados de autorización o manejar errores globalmente.
- **Configuración simplificada**: Axios proporciona una forma sencilla de configurar solicitudes y manejar la serialización de datos, lo que simplifica el acceso a APIs para obtener sonidos, imágenes y condiciones climáticas.

### Biblioteca 2: Redux (o Context API)

- **Gestión del estado global**: Redux (o la Context API de React) me permitirá manejar el estado de la aplicación de manera global, lo que es útil para compartir datos como la configuración de sonidos y la información climática entre diferentes componentes.
- **Predecibilidad**: La arquitectura de Redux ayuda a mantener el estado predecible y facilita la depuración, ya que el flujo de datos es unidireccional.
- **Integración con React**: Redux se integra bien con React y tiene una comunidad activa que proporciona recursos y herramientas adicionales para simplificar su uso.

### Biblioteca 3: Styled Components (o Tailwind CSS)

- **Estilización dinámica**: Styled Components me permite escribir CSS dentro de mis componentes de React, lo que mejora la cohesión entre la lógica de la aplicación y el diseño visual.
- **CSS en JS**: Esta técnica de CSS en JS permite estilos dinámicos basados en las propiedades del componente, lo que puede ser útil para adaptar el diseño en función de la hora o la estación.
- **Tailwind CSS**: Alternativamente, si prefiero una aproximación más utilitaria, Tailwind CSS proporciona clases de utilidad para un diseño rápido y responsive, ideal para desarrollar interfaces modernas y atractivas.

### Herramienta de construcción: Webpack (o Create React App)

- **Módulos y bundling**: Webpack me permitirá agrupar y optimizar mis archivos JavaScript, CSS e imágenes, lo que resulta en tiempos de carga más rápidos para los usuarios.
- **Configuración personalizada**: Aunque tiene una curva de aprendizaje, ofrece una gran flexibilidad para personalizar el proceso de construcción según las necesidades de mi aplicación.
- **Alternativa sencilla**: Si prefiero un enfoque más sencillo y directo, Create React App ofrece una configuración lista para usar que incluye Webpack y Babel, permitiéndome comenzar rápidamente sin preocuparme por la configuración inicial.


## Compatibilidad en navegadores

### Manejo de JavaScript y otros lenguajes en diferentes navegadores
Los navegadores modernos utilizan diferentes motores de JavaScript para interpretar y ejecutar el código. Por ejemplo:

- Google Chrome y Opera utilizan el motor V8.
- Firefox utiliza SpiderMonkey.
- Safari utiliza JavaScriptCore (también conocido como Nitro).
- Microsoft Edge utiliza Chakra en versiones anteriores y V8 en las versiones basadas en Chromium.

Estas diferencias en los motores pueden causar variaciones en el rendimiento y en la compatibilidad de ciertas características de JavaScript. Además, cada navegador tiene su propio motor de renderizado, como Blink (Chrome, Opera), Gecko (Firefox), y WebKit (Safari), lo que también puede afectar la forma en que se interpretan y muestran los elementos HTML y CSS.

### Problemas de compatibilidad y soluciones

#### Diferencias en la implementación de JavaScript:
- Problema: Algunas funciones y características de JavaScript pueden no estar soportadas de manera uniforme en todos los navegadores.
- Solución: Utilizar herramientas como Babel para transpilar el código JavaScript a una versión compatible con todos los navegadores.

#### CSS y Estilos:
- Problema: Las propiedades CSS pueden renderizarse de manera diferente en distintos navegadores.
- Solución: Utilizar *autoprefixer* para añadir automáticamente los prefijos necesarios para cada navegador.

#### Eventos y DOM:
- Problema: La manipulación del DOM y el manejo de eventos pueden comportarse de manera diferente.
- Solución: Utilizar bibliotecas como jQuery o React que abstraen estas diferencias y proporcionan una API consistente.

#### Compatibilidad con HTML5:
- Problema: No todos los navegadores soportan completamente las nuevas características de HTML5.
- Solución: Utilizar polyfills para añadir soporte a características que no están disponibles nativamente en algunos navegadores.

### Integración de Lenguajes de Marcas y Lenguajes de Programación
La integración de lenguajes de marcas (como HTML y XML) con lenguajes de programación (como JavaScript y TypeScript) puede afectar tanto la compatibilidad como el rendimiento de las aplicaciones web.

#### Compatibilidad:
- Problema: Diferentes navegadores pueden interpretar de manera distinta la combinación de HTML y JavaScript.
- Solución: Seguir estándares web y realizar pruebas exhaustivas en múltiples navegadores para asegurar una experiencia consistente.

#### Rendimiento:
- Problema: La manipulación frecuente del DOM puede afectar el rendimiento de la aplicación.
- Solución: Utilizar técnicas como el Virtual DOM en React para minimizar las manipulaciones directas del DOM.

### Conclusión

Para garantizar la compatibilidad y el rendimiento óptimo de las aplicaciones web en diferentes navegadores, es esencial utilizar herramientas y técnicas que aborden las diferencias en la implementación de JavaScript, CSS y HTML. Además, realizar pruebas exhaustivas en múltiples navegadores y dispositivos es crucial para identificar y solucionar problemas de compatibilidad.


## Bibliografía

Modelos de ejecución:
- https://www.arsys.es/blog/todo-sobre-la-arquitectura-cliente-servidor
- https://reactiveprogramming.io/blog/es/estilos-arquitectonicos/cliente-servidor
- https://informatecdigital.com/articulos/arquitectura-de-software-cliente-servidor-una-guia-completa/
- https://coloreshtml.es/que-es-el-cliente-servidor-ejemplos/


Lenguajes de programación web:
- https://visionx.io/blog/typescript-vs-javascript/
- https://softjourn.com/insights/the-advantages-and-disadvantages-of-javascript
- https://codedamn.com/news/javascript/pros-cons-of-javascript

Mecanismos de integración de lenguajes de marcas con lenguajes de programación de clientes web:
- https://www.tusclasesparticulares.com/blog/que-es-y-tipos-lenguajes-marca-programacion-existen
- https://www.eniun.com/lenguajes-marcas-sistemas-gestion-informacion/
  
Evaluación de herramientas de programación para clientes web:
- https://www.capterra.com/p/186634/Visual-Studio-Code/reviews/
- https://thecodest.co/blog/pros-and-cons-of-react/
- https://stackshare.io/axios
- https://redux.js.org/tutorials/essentials/part-1-overview-concepts
- https://dev.to/dnelson35/redux-and-redux-toolkit-for-beginners-a-comprehensive-tutorial-13cb
- https://incentius.com/blog-posts/pros-and-cons-of-using-tailwind-css/
- https://getstream.io/blog/styled-components-vs-css-stylesheets/
- https://www.geeksforgeeks.org/what-are-the-advantages-of-using-webpack/
- https://andrewray.me/blog/webpack-when-to-use-and-why

Compatibilidad en navegadores:
- https://web.dev/articles/howbrowserswork?hl=es-419
- https://comparium.app/es/blog/cross-browser-compatibility-issues/
- https://desarrolladoraweb.com/blog/como-solucionar-problemas-de-compatibilidad-css-en-diferentes-navegadores
- https://web.dev/articles/compat2021?hl=es
- https://managercommunity.es/lenguaje-de-marcas-y-sistemas-de-gestion-de-informacion/