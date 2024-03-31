![logo_ironhack_blue 7](https://user-images.githubusercontent.com/23629340/40541063-a07a0a8a-601a-11e8-91b5-2f13e4e6b441.png)

# Laboratorio | Consultas SQL 6

En esta actividad vamos a realizar un mantenimiento de la base de datos. En la base de datos actual solo tenemos información sobre películas del año 2006. Ahora también hemos recibido el catálogo de películas del año 2020. Para estos nuevos datos crearemos otra tabla e insertaremos de forma masiva todos los datos allí. A continuación se proporciona el código para crear una nueva tabla.

```sql
soltar tabla si existe películas_2020;
CREAR TABLA `películas_2020` (
  `film_id` smallint(5) sin firmar NO NULL AUTO_INCREMENT,
  `título` varchar(255) NO NULO,
  texto `descripción`,
  `release_year` año(4) DEFAULT NULL,
  `language_id` tinyint(3) sin firmar NO NULO,
  `original_language_id` tinyint(3) sin firmar DEFAULT NULL,
  `duración_alquiler` int(6),
  `tasa_alquiler` decimal(4,2),
  `longitud` smallint(5) sin firmar DEFAULT NULL,
  `costo_reemplazo` decimal(5,2) PREDETERMINADO NULO,
  `rating` enum('G','PG','PG-13','R','NC-17') DEFAULT NULL,
  CLAVE PRIMARIA (`film_id`),
  RESTRICCIÓN CLAVE EXTRANJERA (`original_language_id`) REFERENCIAS `language` (`language_id`) AL ELIMINAR RESTRICCIÓN AL ACTUALIZAR CASCADA
) MOTOR = InnoDB AUTO_INCREMENT = 1003 JUEGO DE CARACTERES PREDETERMINADO = utf8;
```

<br>

Tenemos solo un elemento para cada película y todos se colocarán en la nueva tabla. Para 2020, la duración del alquiler será de 3 días, con un precio de oferta de `2,99€` y un coste de reposición de `8,99€` (todos estos son valores fijos para todas las películas de este año). El catálogo se encuentra en un archivo CSV llamado **films_2020.csv** que se puede encontrar en la carpeta `files_for_lab`.

### Instrucciones

- Agregar las nuevas películas a la base de datos.
- Actualizar información sobre `duración_alquiler`, `tasa_alquiler` y `costo_reemplazo`.

### Pista

- Es posible que tengas que usar los siguientes comandos para configurar la opción de importación masiva en "ON":

```sql
mostrar variables como 'local_infile';
establecer global local_infile = 1;
```

- Si la importación masiva produce un error inesperado, también puede usar el `data_import_wizard` para insertar datos en la nueva tabla.