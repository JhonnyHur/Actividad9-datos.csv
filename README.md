Red de Ecosistema Turístico Inteligente con Neo4j
Descripción

Este proyecto implementa una base de datos orientada a grafos utilizando Neo4j para modelar un ecosistema turístico inteligente.

El sistema permite representar relaciones entre:

Usuarios
Lugares turísticos
Eventos
Alojamientos
Ciudades
Intereses

Además, el proyecto permite realizar consultas avanzadas de recomendación turística utilizando el lenguaje Cypher.

Tecnologías utilizadas
Neo4j
Cypher
Hackolade
CSV
GitHub
Estructura del proyecto
neo4j-turismo/
│
├── usuarios.csv
├── lugares.csv
├── ciudades.csv
├── eventos.csv
├── alojamientos.csv
├── intereses.csv
│
├── visito.csv
├── vive_en.csv
├── afin_a.csv
├── recomienda.csv
├── se_hospedo.csv
├── situado_en.csv
├── define_estilo.csv
├── ocurre_en.csv
├── promueve.csv
├── localizado_en.csv
├── conoce_a.csv
│
├── modelo_hackolade.json
├── consultas.cql
└── README.md
Modelo del Grafo

El modelo representa una red turística inteligente donde:

Los usuarios visitan lugares.
Los eventos promueven intereses.
Los alojamientos están localizados en ciudades.
Los usuarios tienen afinidad con diferentes intereses.
Los lugares definen estilos turísticos.
Nodos principales
Usuario

Representa turistas o usuarios del sistema.

Propiedades
id
nombre
nacionalidad
presupuesto_lvl
intereses
nivel_experto
Lugar

Representa sitios turísticos.

Propiedades
id
nombre
tipo
calificacion_avg
popularidad_actual
Evento

Representa actividades culturales o turísticas.

Propiedades
id
nombre
fecha_inicio
fecha_fin
tipo
tematica
sold_out
Ciudad

Representa ciudades turísticas.

Propiedades
id
nombre
clima_dominante
altitud
gentilicio
Alojamiento

Representa hospedajes turísticos.

Propiedades
id
nombre
estrellas
precio_noche
tipo
pet_friendly
Interes

Representa categorías de interés turístico.

Propiedades
id
nombre
Relaciones principales
Relación	Descripción
VISITO	Usuario visitó un lugar
RECOMIENDA	Usuario recomienda un lugar
AFIN_A	Afinidad entre usuario e interés
VIVE_EN	Ciudad de residencia del usuario
SE_HOSPEDO	Usuario se hospedó en alojamiento
DEFINE_ESTILO	Lugar asociado a interés
SITUADO_EN	Lugar ubicado en ciudad
LOCALIZADO_EN	Alojamiento ubicado en ciudad
PROMUEVE	Evento promueve interés
OCURRE_EN	Evento ocurre en ciudad
CONOCE_A	Relación social entre usuarios
Importación de datos en Neo4j

Ejemplo de carga CSV:

LOAD CSV WITH HEADERS FROM
'https://raw.githubusercontent.com/USUARIO/REPO/main/usuarios.csv'
AS row

CREATE (:Usuario {
    id: toInteger(row.id),
    nombre: row.nombre,
    nacionalidad: row.nacionalidad,
    presupuesto_lvl: toInteger(row.presupuesto_lvl),
    intereses: split(row.intereses, "|"),
    nivel_experto: toInteger(row.nivel_experto)
});
Consultas implementadas

El proyecto incluye consultas Cypher para:

Recomendación de lugares turísticos.
Usuarios con intereses similares.
Eventos asociados a intereses específicos.
Lugares mejor calificados.
Alojamientos por ciudad.
Usuarios más activos.
Recomendaciones basadas en afinidad.
Objetivo académico

Este proyecto fue desarrollado con fines académicos para aplicar conceptos de:

Bases de datos orientadas a grafos
Modelado de datos
Relaciones complejas
Consultas Cypher
Integración mediante CSV
Autor

Proyecto académico desarrollado para la actividad de Neo4j y bases de datos orientadas a grafos.
