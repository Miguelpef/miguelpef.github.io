---
layout: post
title: Proyecto Rashan(Uso de cámaras) UE4
author: MiguelPeF
Categories: Rashan Project
---

![_config.yml]({{ site.baseurl }}/images/rashanCamera.png)

Desde que comencé el proyecto de creación de mi primer videojuego con Unreal Engine 4 no me han dejado de surgir retos… El último de ellos, la elección de la cámara (posicionamiento, seguimiento…)
Explicaré de forma resumida por qué finalmente incorporé varios tipos de cámara al entorno y cómo generé el cambio de cámara para cada situación, los problemas con los que me encontré y la mejor solución para ellos.

<h1>Elección de cámaras</h1>

Unreal Engine da la posibilidad de generar plantillas en primera y tercera persona, es una forma muy sencilla de comenzar un proyecto para no iniciar de 0. Sin embargo, el problema nos lo encontramos cuando no nos resulta ninguna de estas la forma de elaborar nuestro videojuego.
Para el proyecto Rashan quería que en los exteriores la vista fuese en tercera persona y que acompañase al jugador en el movimiento, todo era muy sencillo desde esta primera perspectiva. El problema llegó cuando entraba en interior, al situarse la cámara en el blueprint del personaje siempre mantenía la distancia esto hacia que la visión del espectador chocase contra el techo de las casas, las paredes…

Por ese motivo una vez tenía resuelto la visión desde exteriores me puse a investigar cómo se desenvolvían otros videojuegos. Me llamó la atención cómo lo hacian los antiguos Resident Evil que seguro que muchos recordaréis…

![_config.yml]({{ site.baseurl }}/images/resident-evil.jpg)

Comencé con la creación de este sistema de una forma sencilla, aplicando triggers de accionamiento con Begin Overlap y referenciando la cámara que se posicionaba siempre abarcando el espacio que ocupaba el trigger box. Los blueprint que usé son:

![_config.yml]({{ site.baseurl }}/images/bp1.png)

Todo funcionaba de forma correcta, pero empezaron a surgir los problemas…

<h1>Problemas con cámaras estáticas</h1>
<h2>Problema 1: Control del personaje y perspectiva</h2>
Supongamos que la cámara que tenemos al principio se encuentra mirando al frente, pero cuando accedemos al trigger mencionado anteriormente la cámara a la que cambia se encuentra mirando exactamente hacia el sentido contrario. El movimiento del personaje se invierte totalmente haciendo que el control sea un infierno e imposibilitando el disfrute del juego.

<h2>Problema 2: Escasa visión del entorno</h2>
Al ser una cámara estática y no poder rotar sobre el entorno, se limita la posible sensación de descubrimiento, hablamos de un juego de aventura y descubrimiento donde hay que recoger objetos por el mundo… La visión sobre el escenario debe alcanzar el máximo espacio posible para detectar todos los secretos que el entorno tiene para el jugador.

<h2>Problema 3: Transición entre cámaras estáticas y móviles</h2>
Pongamos el ejemplo que estamos en la cocina con la cámara X, y pasamos al salón que tiene la cámara Y. El cambio de imagen si es instantáneo nos hará perdernos por unos segundos en el entorno. Por ello me gusta siempre realizar cualquier cambio de vista de forma progresiva, que el espectador entienda que está ocurriendo y no pierda la sensación de control.

<h1>Solución para el Proyecto Rashan</h1>
Podría haber modificado el control para solucionar de forma rápida el problema 1, pero el juego acabaría siendo más complejo de lo que en un principio se ideo. 
Para resolver el problema 2 habría sido buena idea que las cámaras estáticas rotaran en función de la posición del jugador, pero continuaríamos con el problema 1. 
La solución para el Proyecto acabó siendo lo que se había pensado en un principio, un cambio de cámara de móvil a estático. Sin embargo, la cámara estática siempre tendría que estar mirando al frente y nunca a la derecha, izquierda o invertido… Además habría que posicionar un número elevado de cámara por los interiores para que se pudiese solucionar el problema 2. El cambio de cámara sería progresivo gracias a la opción del blueprint set view target with blend, posicionando blend time con valor de 1.0, logramos conseguir que el cambio se realice durante 1 segundo.
