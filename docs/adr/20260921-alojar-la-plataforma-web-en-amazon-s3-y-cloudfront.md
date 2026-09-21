# Alojar la Plataforma Web en Amazon S3 y CloudFront

- Status: proposed
- Deciders: [list everyone involved in the decision] <!-- optional -->
- Date: [YYYY-MM-DD when the decision was last updated] <!-- optional. To customize the ordering without relying on Git creation dates and filenames -->
- Tags: [space and/or comma separated list of tags] <!-- optional -->

## Contexto

La Plataforma web para el personal de UNAYOE (y acceso estudiantil vía web) requiere servir componentes estáticos (HTML, CSS, JS) con alta disponibilidad, seguridad y bajos tiempos de respuesta, sin saturar los recursos del servidor de aplicaciones backend. 

## Decisión

Desplegar la interfaz web cliente en un bucket de Amazon S3 administrado como sitio estático y distribuirlo globalmente a través de Amazon CloudFront (CDN). 

### Consecuencias positivas 

- Reduce a cero la carga de cómputo en servidores de aplicaciones para la entrega de la interfaz de usuario. <br>
- Garantiza una alta disponibilidad y baja latencia de carga mediante la caché perimetral de CloudFront. <br>
- Reduce drásticamente los costos operativos en comparación con mantener un servidor web tradicional encendido 24/7.

### Consecuencias negativas

- Exige invalidar la caché de CloudFront cada vez que se realice un nuevo despliegue del frontend. <br>
- Requiere configurar políticas de seguridad de origen (OAC/OAI) en S3 para evitar accesos directos no deseados.
