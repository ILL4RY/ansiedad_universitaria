# Anonimización de Datos Sensibles para Reportes de Gestión Institucional

- Status: proposed
- Deciders: [list everyone involved in the decision] <!-- optional -->
- Date: [YYYY-MM-DD when the decision was last updated] <!-- optional. To customize the ordering without relying on Git creation dates and filenames -->
- Tags: [space and/or comma separated list of tags] <!-- optional -->

## Contexto

La función F10 ("Gestión institucional") permite al personal autorizado de UNAYOE administrar contenidos y consultar estadísticas aggregadas del sistema. Sin embargo, los datos emocionales y de riesgo (F1, F5) son altamente sensibles. Debe garantizarse la privacidad del estudiante frente a los administradores. 


## Decisión

Implementar un mecanismo explícito de agregación y anonimización de datos en el nivel de aplicación y persistencia antes de que la información sea expuesta o procesada por el Microservicio de Gestión Institucional. 

### Consecuencias positivas 

- Protege la privacidad y confidencialidad de la salud emocional de los estudiantes. <br>
- Permite a UNAYOE tomar decisiones informadas a nivel institucional basadas en tendencias colectivas sin comprometer identidades individuales. <br>
- Ayuda al cumplimiento de regulaciones sobre protección de datos personales y sensibles.


### Consecuencias negativas

- Aumenta la complejidad lógica al requerir procesos de transformación y desasociación de identidades previo a la generación de reportes. <br>
- Impide el rastreo directo desde la vista de gestión institucional hacia un estudiante específico salvo que exista un flujo explícito de alerta crítica por otro canal autorizado.

