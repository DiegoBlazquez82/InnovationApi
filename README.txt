﻿Proyecto API Innovation api para la explotacion del modelo solicitado para la prueba de nivel de Innovation
Proyecto desarrollado en NETCORE 3.2 

Introducción
El siguiente documento describe la funcionalidad de la API API.Innovation.DGT diseñada para la gestión de usuarios, vehículos e infracciones.

Objeto del proyecto
El objeto del proyecto es el desarrollo de un API para poder consumir los datos de las tablas diseñadas para la gestión de infracciones.

Entorno
El desarrollo de la aplicación se ha realizado con el lenguaje de programación C# NetCore y el entorno de trabajo Visual Studio 2019 para el desarrollo del API y una base de datos SQLLite para el almacenamiento de la información.
Para el desarrollo de este se han utilizado las siguientes tecnologías:
EntityFramework, en modo code firts, para la creación de la base de datos
Dapper, para la realización de consultas a la bbdd.
CQRS, a través de la librería mediator para la ejecución de comandos.
Inyección de dependencias, se ha utilizado la tecnología proporcionada por ASPNETCore, aunque también se podría utilizar Autofac en caso de ser necesario.
Swagger, para la documentación del API
JWT, para la autentificación a través de token bearer, se podría utilizar IdentityServer en caso de ser necesario.
Arquitectura

Controladores
Se ha creado un controlador para la generación de la autentificación a través de token, este controlador tiene un único método cuya tarea es la crear un token valido durante 1 dia.
Se ha creado un controlador para Swagger, para la definición y explotación.
Se ha creado un controlador para las tareas solicitadas de obtención Top de usuario y obtención de Historial, para ello existen dos endpoints los cuales cada uno de ellos devuelve dicha información.
Existe un controlador por cada uno de las tablas creadas en base de datos estos controladores realizan las tareas básicas(inserción, modificación, borrado, consulta) en algunos casos estas tareas se realiza a través de patrón mediator para enviarles a los commands las tareas.



Modelo de datos
Todo el contenido del modelo de datos se encuentra definido dentro de la ruta Application/
Para el modelo de datos se ha creado una clase dbcontext con el contenido para la creación de la bbdd por entityframework 
Carpeta Application/Models: Contiene una clase por cada uno de los modelos necesarios para la creación de las tablas
Carpeta Application/EntityConfigurations: contiene una clase para el modelado de la tabla, clave primaria, índices, etc..
Carpeta Application/Queries: Contiene los métodos para realizar las consultas a base de datos a través de Dapper.

Infrastructura
Dentro de la ruta Infrastructure  las clases necesarias para el negocio.
Carpeta Infrasctructure/Models: Contiene una clase que se devuelven y se solicitan en los controladores.
Carpeta Infrasctructure/Queries: Contiene los command que ejecutan las reglas de negocio






 
