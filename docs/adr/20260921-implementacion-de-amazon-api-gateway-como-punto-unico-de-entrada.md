# Implementación de Amazon API Gateway como punto único de entrada

- Status: proposed
- Deciders: [list everyone involved in the decision] <!-- optional -->
- Date: [YYYY-MM-DD when the decision was last updated] <!-- optional. To customize the ordering without relying on Git creation dates and filenames -->
- Tags: [space and/or comma separated list of tags] <!-- optional -->

## Contexto

El sistema expone servicios tanto a una aplicación móvil (para estudiantes) como a una plataforma web (para UNAYOE). Sin un punto de entrada centralizado, los clientes tendrían que comunicarse directamente con múltiples microservicios, lo que expondría la estructura interna del backend, complicaría el control de seguridad y dificultaría la gestión del tráfico.  

## Decisión

Utilizar Amazon API Gateway como la fachada centralizada para enrutar todas las solicitudes desde la App móvil y la Plataforma web hacia los microservicios correspondientes del servidor de aplicaciones.


### Consecuencias positivas 

- Centraliza la autenticación, autorización, políticas de CORS y limitación de tasa (rate limiting). <br>
- Oculta la topología interna de la arquitectura y reduce el acoplamiento entre los clientes móviles/web y los microservicios. <br>
- Facilita la gestión de versiones de la API y el monitoreo unificado del tráfico entrante.

### Consecuencias negativas

- Añade un punto único de falla (SPOF) a nivel de entrada, requiriendo una configuración adecuada de alta disponibilidad en AWS. <br>
- Agrega un leve incremento en la latencia de las peticiones debido al salto adicional en el gateway.

