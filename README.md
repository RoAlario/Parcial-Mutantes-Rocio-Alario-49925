

# Parcial Rocio Alario - 49925

# Antes de empezar
**⚠️ IMPORTANTE: ⚠️**  
**<span style="font-size: 1.2em">Cuando se ingrese un adn en postman, el campo de ADN debe comenzar con la palabra clave `"adn"` para que sea considerado válido por la API.En caso de que empiece por ejemplo con la palabra `"dna"` no será considerado válido. </span>**  

### Ejemplos en Postman
- **Ejemplo de ADN mutante válido**:
  ```json
  {
    "adn": ["ATGCGA", "CAGTGC", "TTATGT", "AGAAGG", "CCCCTA", "TCACTG"]
  }
  
Este proyecto es una API desarrollada en Java y Spring Boot que analiza secuencias de ADN para determinar si son mutantes. La API también ofrece estadísticas sobre los análisis realizados y cuenta con pruebas automáticas y un reporte de cobertura de código. A continuación, se describe la configuración, el uso de la API y los resultados de las pruebas de rendimiento.  
### Más info:    
Si quiere informacion más detallada, puede consultar el PDF "Informe parcial desarrollo" en donde se especifica bien paso a paso como usar la API y se muestra el code coverage, los test de stress y los test automáticos.   

## Configuración General

1. **Abrir el proyecto en IntelliJ**:
   - Abre la carpeta del proyecto en IntelliJ.
   - Ejecuta el archivo `ParcialAlario49925Application.java`.
   - Deberías ver un mensaje que dice "Estoy Andando" al iniciar.

## Configuración en Postman

2. **Instrucciones en Postman**:
   - La API cuenta con dos endpoints: `POST` para cargar ADN y `GET` para obtener estadísticas.
   
3. **Endpoint POST**:
   - URL: `http://localhost:8080/mutant`
   - Permite cargar secuencias de ADN en la base de datos H2.
   
4. **Endpoint GET**:
   - URL: `http://localhost:8080/stats`
   - Muestra estadísticas sobre la cantidad de ADN mutante y humano cargado en la base de datos.

## Configuración de la Base de Datos H2

5. **Conectar a H2**:
   - Abre la consola H2 en tu navegador con la URL: `http://localhost:8080/h2-console/`.
   - Configura los siguientes datos:
     - **Driver Class**: `org.h2.Driver`
     - **JDBC URL**: `jdbc:h2:mem:testdb`
     - **User Name**: `sa`
     - **Password**: *(deja este campo en blanco)*
   - Haz clic en "Test Connection" para verificar la conexión. Si es exitosa, verás un mensaje de confirmación.

6. **Consultar la Tabla de ADN**:
   - Para ver los ADN cargados, ejecuta la consulta `SELECT * FROM ADN` en la consola de H2.

## Uso de la API

1. **Ejecutar el archivo `ParcialAlario49925Application.java`**:
   - Asegúrate de que el archivo está en ejecución para usar la API.

2. **Instrucción POST en Postman**:
   - En la sección "Body", selecciona la opción "raw" y asegúrate de que el tipo sea `JSON`.
   - Envía un array de secuencias de ADN como JSON. Si el ADN tiene más de una secuencia de 4 letras idénticas, se identificará como mutante (200 OK); si no, como humano (403 Forbidden).

3. **Instrucción GET en Postman**:
   - En la sección de GET, haz clic en "Send" para recibir estadísticas sobre el número de mutantes y humanos, así como el ratio entre ambos.



## Pruebas de Rendimiento y Fluctuaciones

### Pruebas con JMeter:
Se realizaron pruebas de rendimiento de la API con diferentes cantidades de peticiones por segundo para evaluar su eficiencia:

- **10 peticiones por segundo**: Tiempo promedio de 45 ms, 0% de error.
- **100 peticiones por segundo**: Tiempo promedio de 3 ms, 0% de error.
- **1000 peticiones por segundo**: Tiempo promedio de 9 ms, 0% de error.
- **100,000 peticiones por segundo**: Tiempo total de 16 minutos y 40 segundos, con un 70.93% de error. Esto indica que a este nivel de carga, el rendimiento de la API disminuye significativamente.

### Pruebas Automáticas

#### Pruebas Unitarias:
- Se implementaron un total de 26 pruebas unitarias utilizando JUnit para asegurar el correcto funcionamiento de la API.
- Todas las pruebas están localizadas en la carpeta `test` y pueden ejecutarse a través de la clase `ParcialAlario49925ApplicationTests`.
- Las pruebas tuvieron una tasa de éxito del 100%, es decir, todas las pruebas fueron satisfactorias.

### Cobertura de Código

#### Reporte de Cobertura:
- La cobertura de código se midió usando **JaCoCo**, generando un reporte detallado sobre la ejecución de pruebas en las distintas instrucciones y validaciones del código.

#### Cobertura total:
- **Instrucciones**: 82%
- **Validaciones**: 88%

