# Base de datos relacional centralizada con Amazon RDS PostgreSQL 

- Status: proposed
- Deciders: [list everyone involved in the decision] <!-- optional -->
- Date: [YYYY-MM-DD when the decision was last updated] <!-- optional. To customize the ordering without relying on Git creation dates and filenames -->
- Tags: [space and/or comma separated list of tags] <!-- optional -->

## Contexto

El sistema debe soportar diversas funcionalidades orientadas tanto a estudiantes (evaluación de riesgo, seguimiento personal, agenda, check-in emocional, grupos de estudio) como al personal de UNAYOE (gestión de recursos, actividades y reportes institucionales). Al tener dominios con diferentes volúmenes de tráfico, ciclos de cambio y requerimientos de rendimiento, mantener una arquitectura monolítica podría dificultar el escalamiento individual y el mantenimiento del software a largo plazo. 

## Decisión

Descomponer el servidor de aplicaciones en 7 microservicios independientes: <br>
1. Microservicio de Usuarios <br>
2. Microservicio de Evaluación y Riesgo <br>
3. Microservicio de Seguimiento y Bienestar <br>
4. Microservicio de Notificaciones <br>
5. Microservicio de Agenda Académica <br>
6. Microservicio de Gestión Institucional <br>
7. Microservicio de Apoyo Universitario 

### Consecuencias positivas 

- Permite escalar de forma independiente los módulos con mayor demanda (como Evaluación/Riesgo o Check-in emocional). <br>
- Desacopla responsabilidades, facilitando el desarrollo y despliegue paralelo de funcionalidades. <br>
- Limita el impacto de fallas: una caída en la gestión de talleres no interrumpe el registro del estado emocional o las alertas preventivas.

### Consecuencias negativas

- Incremente la complejidad en la infraestructura, monitoreo y comunicación entre servicios. <br>
- Requiere gestionar la consistencia eventual entre microservicios.
