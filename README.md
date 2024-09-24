# Gestion_Editorial_SQL

## Descrición del proyecto

### Objetivo principal: 

El objetivo de la base de datos gestion_editorial es gestionar de manera eficiente y centralizada el flujo editorial de un sistema de revisión y publicación de manuscritos. Se busca almacenar información sobre los autores, coautores, evaluadores, manuscritos, evaluaciones y los conceptos emitidos en las distintas fases de evaluación, manteniendo relaciones claras y garantizando la integridad de los datos.

### Objetivos específicos:

1.	Gestión de autores y coautores: Almacenar información sobre los autores y coautores de los manuscritos.
2.	Registro de manuscritos: Mantener un registro de los manuscritos enviados por los autores, incluyendo su tipo, idioma y fechas importantes.
3.	Gestión de evaluadores: Almacenar datos de los evaluadores clasificados por tipos (técnico, editorial, pares), y asignarles manuscritos para evaluación en las fases correspondientes.
4.	Evaluaciones y conceptos: Registrar las evaluaciones realizadas, fases del proceso editorial y los conceptos emitidos para cada manuscrito.
5.	Control del flujo de trabajo: Controlar y registrar el progreso de los manuscritos a través de las fases del proceso editorial (Revisión preliminar, Revisión editorial, Revisión de pares).

### Alcance:

1.	Tablas principales:
o	Autores y coautores: Datos completos de los autores y coautores relacionados con los manuscritos.
o	Manuscritos: Información sobre los manuscritos recibidos, sus autores y el tipo de manuscrito.
o	Evaluadores: Datos de los evaluadores y su clasificación (técnico, editorial, pares).
o	Evaluaciones: Registro de las evaluaciones de los manuscritos, fases de evaluación, evaluadores asignados y conceptos emitidos.
o	Conceptos: Definición de los conceptos emitidos tras las evaluaciones.

2.	Relaciones:
o	Relación entre manuscritos y autores.
o	Relación entre manuscritos y evaluaciones, con conexión a evaluadores y conceptos emitidos.

## Análisis: Diseño Conceptual de la base de datos

### Entidades principales:

1.	Autor:
o	Atributos: ID, número de documento, nombres, apellido paterno, apellido materno, celular, email, fecha de registro.
o	Relación: Un autor puede tener uno o más coautores. Un autor puede enviar uno o más manuscritos.
2.	Coautor:
o	Atributos: ID, número de documento, nombres, apellido paterno, apellido materno, celular, email, fecha de registro.
o	Relación: Cada coautor está asociado a un autor. Pueden existir múltiples coautores para un manuscrito.
3.	Manuscrito:
o	Atributos: ID, título, tipo de manuscrito (reflexión, investigación, etc.), idioma, fecha de recepción.
o	Relación: Cada manuscrito tiene un autor principal. Un manuscrito puede estar relacionado con una o más evaluaciones.
4.	Evaluador:
o	Atributos: ID, tipo de evaluador (técnico, editorial, pares), fecha de registro.
o	Relación: Un evaluador puede realizar evaluaciones a uno o varios manuscritos.
5.	Evaluación:
o	Atributos: ID, fecha de asignación, fase de evaluación (Revisión preliminar, Revisión editorial, Revisión de pares), fecha de concepto.
o	Relación: Una evaluación está asociada a un manuscrito y a un evaluador. Además, tiene un concepto asociado.
6.	Concepto:
o	Atributos: ID, descripción del concepto (Aceptar, Rechazar, Aceptar con modificaciones menores, etc.).
o	Relación: Un concepto se emite como resultado de una evaluación.

### Relaciones:

•	Autor -> Manuscritos: Relación uno a muchos, un autor puede tener varios manuscritos.
•	Coautor -> Autor: Relación muchos a uno, varios coautores pueden estar asociados a un autor.
•	Manuscrito -> Evaluación: Relación uno a muchos, un manuscrito puede tener varias evaluaciones.
•	Evaluación -> Evaluador: Relación muchos a uno, un evaluador puede realizar múltiples evaluaciones.
•	Evaluación -> Concepto: Relación muchos a uno, una evaluación tiene un concepto.
