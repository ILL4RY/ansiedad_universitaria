# Despliegue del servidor de aplicaciones sobre instancias Amazon EC2

- Status: proposed
- Deciders: [list everyone involved in the decision] <!-- optional -->
- Date: [YYYY-MM-DD when the decision was last updated] <!-- optional. To customize the ordering without relying on Git creation dates and filenames -->
- Tags: [space and/or comma separated list of tags] <!-- optional -->

## Contexto

En la fase inicial del proyecto, se requiere un entorno de ejecución sencillo y flexible para desplegar los 7 microservicios, permitiendo ajustar los recursos y mantener control directo sobre el entorno operativo antes de migrar a plataformas completamente administradas. 
 

## Decisión

Alojar inicialmente los microservicios del servidor de aplicaciones en instancias de Amazon EC2 utilizando contenedores (Docker).

### Consecuencias positivas 

- Otorga control total sobre la configuración del entorno, facilitando las pruebas iniciales y la depuración. <br>
- Facilita una transición posterior hacia servicios de orquestación administrados de AWS (como Amazon ECS o EKS). <br>
- Permite dimensionar la capacidad del servidor ajustando el tipo de instancia según la demanda inicial.


### Consecuencias negativas

- Requiere mayor esfuerzo operativo para el mantenimiento de parches del sistema operativo y configuración de autoescalado. <br>
- Riesgo de subutilización o sobrecosto si no se configuran adecuadamente las políticas de apagado o escalado automático.


