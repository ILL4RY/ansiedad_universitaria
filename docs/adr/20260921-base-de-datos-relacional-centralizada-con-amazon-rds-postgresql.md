# Base de datos relacional centralizada con Amazon RDS PostgreSQL 

- Status: proposed
- Deciders: [list everyone involved in the decision] <!-- optional -->
- Date: [YYYY-MM-DD when the decision was last updated] <!-- optional. To customize the ordering without relying on Git creation dates and filenames -->
- Tags: [space and/or comma separated list of tags] <!-- optional -->

## Contexto

Las funcionalidades del sistema (usuarios, agendas académicas, planes de bienestar y registros de apoyo) involucran datos estructurados y altamente interrelacionados. Se requiere una solución de almacenamiento sólida que garantice integridad de datos, atomicidad y facilidad de administración en la nube.  

## Decisión

Adoptar Amazon RDS con PostgreSQL como el motor de base de datos relacional del sistema. 

### Consecuencias positivas 

- Garantiza cumplimiento ACID para operaciones sensibles (registro de datos, seguimiento de evaluaciones y agendas). <br>
- Delega a AWS la gestión de respaldos automáticos, parches de seguridad y alta disponibilidad (Multi-AZ). <br>
- Ofrece un motor potente, de código abierto y ampliamente compatible con los ORM y frameworks modernos.

### Consecuencias negativas

- Representa un costo fijo continuo dentro de la infraestructura de AWS. <br>
- Al ser una base de datos relacional compartida entre servicios en esta etapa inicial, requiere disciplina en la separación de esquemas para no romper el aislamiento conceptual de los microservicios.

