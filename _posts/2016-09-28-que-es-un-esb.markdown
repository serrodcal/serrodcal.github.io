---
layout: post
title: Qué es un ESB
date: '2016-09-28 11:00:00'
author: sergio
tags:
- wso2 esb
---

![](http://b.content.wso2.com/sites/all/product-pages/images/esb-capabilities.png)

Esta primera entrada al ser la primera es más a nivel de concepto, entender qué es, para qué sirve, dónde y cuándo aplicarlo, etc. Así que, sin más dilación, vamos a ello.

En primer lugar, necesitamos colocarnos en el contexto de una empresa que quiere migrar su arquitectura hacia una que de mejor rendimiento. Una de las soluciones que más están de moda en este momento es diseñar una arquitectura orientada a microservicios.

Como hoy día, puede que millones de usuarios utilicen una plataforma de manera activa las aplicaciones monolíticas (una misma aplicación que lo hace todo en un único servidor) no dan el rendimiento esperado y terminan por dar o un mal servicio, o directamente “caerse”.

Una arquitectura orientada a microservicios es repartir la responsabilidad que antes estaban en un único sitio entre muchos componentes pequeños. Esos componentes son conocidos como “binding blocks”, aunque en adelante los llamaremos simplemente módulos. Como no es el objetivo de esta entrada, ni de este proyecto, explicar los microservicios, para quién esté intersado, dejo un link a un blog de Martin Fowler dónde se puede encontrar más información al respecto.

Por poner un ejemplo, podemos tomar una empresa que expone una red social de recetas de cocinas. Cada módulo ofrece una pequeña parte de la información del sistema, por ejemplo: usuarios, otro módulo puede contener las recetas, y así sucesivamente. Podemos tener algo más complicado, como distintos niveles de módulos, de modo que podemos tener módulos que llaman a otros dos por debajo para dar una funcionalidad algo más completa.

Y aquí tenemos el primer problema, que no es más que un nudo de comunicaciones punto a punto entre cuantos módulos tengamos en la arquitectura (cuantos más, peor). Y otros problemas son aplicar lo que se conocen como QoS: no perdida de las peticiones, securización, monitorización, transformación entre servicios con protocolos modernos y aplicaciones legadas, etc.

Para todo ello, lo que se suele utilizar es una solución de integración. Un único componente por el que pasan todas las comunicaciones.

Como era de esperar, hay varias opciones. Una de ellas, es utilizar Apache Camel, que es un framework de integración. Cuando son pocos los módulos expuestos en la arquitectura es una buena solución. Pero cuando la cosa se complica necesitamos otro tipos de soluciones, y es aquí cuando aparecen los ESBs.

Un ESB (Enterprise Service Bus) no es más que un componente que como ya hemos dicho se encarga de centralizar todas las comunicaciones, y aporta valor no solo en cuanto a QoS, sino también permite dar solución a problemas típicos. Es decir, implementa una serie de mecanismos conocidos como patrones de integración empresarial (EIP por sus siglas en inglés) y que se pueden encontrar más información sobre los mismos en el siguiente link.

Son más de 60 patrones que son soportados por casi la totalidad de los ESBs, aunque aquí vayamos a hablar solamente de WSO2 ESB.

[![1](http://www.enterpriseintegrationpatterns.com/img/inside_back_cover.png)](http://www.enterpriseintegrationpatterns.com/img/inside_back_cover.png)

Por ejemplo, si necesitamos exponer servicios legados que exponen recursos mediante el protocolo SOAP, pero queremos que las aplicaciones, sean de la plataforma que sean, hablen el protocolo REST, hemos dado con la herramienta indicada. Se pueden hacer muchas cosas más, y las cuales se irán viendo en sucesivas entradas.

Para terminar, hay críticas hacia este tipo de soluciones que argumentan que es un cuello de botella, que puede retrasar desarrollos, etc. La verdad es que aunque se hable de tener un ESB, en realidad se puede tener un cluster de ellos, y por otro lado, puede aportar muchas cosas que se irán comentando en adelante. Además, la manera de exponer la serie de entradas sigue un orden que precisamente intenta ayudar a quiénes son nuevos con este tipo de productos no cometa errores que lleven a tener este tipo de ideas.

Y hasta aquí esta entrada, y hasta la próxima, donde se intentará enseñar el producto, sus componentes, directorios, consola, etc., espero que los conceptos que son necesarios en adelante hayan quedado meridianamente claros.