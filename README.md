## Challenge2
WhiteStack Challenge 2

#Descripción del Challenge

Se desplegó una aplicación web básica (Nginx) en el namespace Challenger-009. Posteriormente, Se configuraron los recursos y herramientas de monitoreo necesarios para obtener y visualizar las métricas expuestas por la aplicación desplegada. 
Las herramientas de monitoreo que se configuraron fueron: 
    • Prometheus (Proporcionado por Whitestack)
    • Grafana (Desplegado localmente via Docker)

#Problemas durante el despliegue y soluciones

Durante el proceso de despliegue de la solución se encontraron algunos problemas los cuales se describen a continuación:

Despliegue del Service Monitor

En un principio Prometheus no descubría el service monitor por lo que la solución fue revisar las etiquetas que se habían descrito en el manifiesto y configurándolas en el manifiesto del service monitor se pudo resolver que Prometheus lo logrará descubrir.

Data Source de Grafana

El data source de grafana no lograba conectarse con Prometheus a pesar de que se había configurado el Port Forwarding en un principio, esto se logro solucionar colocando en la url en lugar de una ip el name: http://host.docker.internal:<PUERTO de PORTFORWARDING>

Patch

Se desplego el parche para poder generar la alarma sobre el inciso C pero no genero ningun cambio en la alarma, solo se creo otro pod el cual quedo en pending, no se modifico el parche para hacer un workaround debido a que era un recurso oficial.

Promtool

Promtool dio errores de apiversion y fieldgroups, no se logro resolver el problema de la herramienta.

#Creacion de Dashboard y Alertas

Para el primer punto del panel de Stats se decidio colocar los datos basicos de monitoreo del servicio para poder tener un vistazo rapido del status, se definieron 4 metricas las cuales se colocaron en el Panel.

Para las Alertas se utilizo tambien las sugerencias de Grafana sobre cuales Expresiones eran funcionales con las querys sobre las cuales se estaban generando las alertas.

