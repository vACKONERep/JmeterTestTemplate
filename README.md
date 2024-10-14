# Planes de Prueba de JMeter para Pruebas de Rendimiento

## Descripción General
Este repositorio contiene dos planes de prueba de JMeter diseñados para evaluar el rendimiento y los tiempos de respuesta del sitio web **krugercorp.com**. Los planes utilizan el grupo de hilos concurrentes de BlazeMeter para simular una carga de usuarios y contienen varios elementos de monitoreo de respuestas y rendimiento, como aserciones, cabeceras y colectores de resultados.

## Planes de Prueba

### 1. **Plan de Prueba Básico**
Este plan de prueba está diseñado para evaluar la respuesta del sitio mediante una solicitud GET básica al endpoint "/nosotros".

- **Grupo de Hilos Concurrentes**: Simula usuarios concurrentes accediendo a la página `/nosotros/` de **krugercorp.com**.
  - **Nivel Objetivo**: 100 usuarios virtuales.
  - **Ramp-up**: 185 segundos, incrementando en pasos de 25 usuarios.
  - **Duración de Sostenimiento**: 5 segundos.
  
- **Solicitud HTTP**: Una solicitud GET simple dirigida a:
  - **Dominio**: `www.krugercorp.com`
  - **Protocolo**: `https`
  - **Ruta**: `/nosotros/`
  
- **Aserción de Respuesta**: Garantiza que el código de respuesta sea `200`, lo que indica que la solicitud fue exitosa.
  - Aserción personalizada para verificar el código de respuesta HTTP.
  
- **Gestor de Cabeceras HTTP**: Incluye cabeceras para gestionar el tipo de contenido y aceptar codificaciones:
  - `Accept: application/xml`
  - `Content-Type: text/xml`
  - `Accept-Encoding: GZIP`
  
- **Colectores de Resultados**: Se incluyen múltiples colectores de resultados para un seguimiento detallado del rendimiento y los errores:
  - **Informe Resumido**: Muestra un resumen de métricas de rendimiento, como tiempo de respuesta, latencia y tasa de éxito.
  - **Ver Resultados en Árbol**: Proporciona una vista detallada de cada solicitud y su respuesta correspondiente.
  - **Gráfico Agregado**: Muestra métricas en formato gráfico para la visualización del rendimiento general.
  - **Gráfico de Tiempos de Respuesta**: Proporciona una representación gráfica de los tiempos de respuesta para la prueba.

### 2. **Plan de Prueba Extendido con Variables de Usuario**
En este plan de prueba, se incluyen variables definidas por el usuario para personalizar las configuraciones de la prueba.

- **Grupo de Hilos Concurrentes**: Estructura similar al plan básico, con variables definidas por el usuario que permiten configurar propiedades clave de forma dinámica, como el dominio, la ruta o el tiempo de ramp-up.

- **Solicitud HTTP y Cabeceras**: La solicitud y las cabeceras son similares al plan básico, pero las variables definidas por el usuario ofrecen mayor flexibilidad.

- **Aserciones de Respuesta Mejoradas**: Se pueden configurar aserciones adicionales modificando las variables o agregando nuevas personalizadas.

### Estructura de Archivos
Los planes de prueba están estructurados en formato XML y se pueden importar directamente en JMeter para su ejecución. Ambos planes están diseñados para probar la capacidad de respuesta de **krugercorp.com** bajo distintas cargas y garantizar que el endpoint `/nosotros/` maneje eficientemente el tráfico.

## Instrucciones de Uso
Para ejecutar estos planes de prueba, sigue los siguientes pasos:

1. Abre JMeter y carga el archivo `.jmx` correspondiente al plan de prueba.
2. Ajusta las variables necesarias, como:
   - Nombre de dominio
   - Número de usuarios virtuales
   - Tiempo de ramp-up
3. Asegúrate de que los colectores de resultados **Informe Resumido**, **Ver Resultados en Árbol**, **Gráfico Agregado** y **Gráfico de Tiempos de Respuesta** estén habilitados para capturar las métricas de rendimiento.
4. Ejecuta el plan de prueba haciendo clic en el botón **Iniciar** en JMeter.
5. Revisa los resultados en los distintos colectores de resultados proporcionados.

## Requisitos
- **JMeter 5.6.3** o posterior.
- **Plugin de BlazeMeter**: El plan de prueba utiliza el **Grupo de Hilos Concurrentes**, que es parte del plugin de BlazeMeter para JMeter.

## Notas
- Se recomienda ejecutar estas pruebas en una conexión de red estable para evitar interrupciones en los resultados.
- Puedes modificar la URL de destino, las cabeceras o las aserciones según las necesidades de tus pruebas.


## Licencia
Este repositorio está bajo la licencia [MIT License](LICENSE).
