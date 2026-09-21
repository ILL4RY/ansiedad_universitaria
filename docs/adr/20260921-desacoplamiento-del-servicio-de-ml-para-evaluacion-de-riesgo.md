# Desacoplamiento del Servicio de ML para evaluación de riesgo

- Status: proposed
- Deciders: [list everyone involved in the decision] <!-- optional -->
- Date: [YYYY-MM-DD when the decision was last updated] <!-- optional. To customize the ordering without relying on Git creation dates and filenames -->
- Tags: [space and/or comma separated list of tags] <!-- optional -->

## Contexto

El sistema incluye la funcionalidad de "Evaluación inteligente del riesgo" (F1), la cual requiere procesar datos de los estudiantes y ejecutar algoritmos predictivos de Machine Learning. El cómputo intensivo derivado de los modelos de inferencia predictiva puede consumir recursos significativos de CPU/memoria y no debe interferir con las operaciones transaccionales rutinarias del sistema. 

## Decisión

Aislar el Servicio de Machine Learning en un contenedor/entorno independiente, separado de la capa de microservicios de la aplicación backend, interactuando de forma remota a través del Microservicio de Evaluación y Riesgo. 

### Consecuencias positivas 

- Previene que picos de demanda en el cálculo de riesgo degraden el rendimiento general del resto de la aplicación. <br>
- Otorga flexibilidad para elegir y cambiar la tecnología, frameworks o infraestructura optimizada para ML (como servicios serverless o instancias con GPU) sin impactar el backend principal. 

### Consecuencias negativas

- Introduce latencia adicional por la comunicación de red entre el Microservicio de Evaluación y el Servicio de ML. <br>
- Aumenta la superficie de mantenimiento al requerir un flujo de despliegue y monitoreo específico para el modelo predictivo.

