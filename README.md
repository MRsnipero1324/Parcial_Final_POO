# Parcial_Final_POO
Programación Orientada a Objetos – 2023-10 Departamento de Ingeniería de Sistemas y Computación - Universidad del Norte
# TrashCity

TrashCity es una aplicación de gestión de recolección de residuos que permite realizar un seguimiento de las recolecciones de diferentes tipos de materiales en distintas rutas. Permite calcular la cantidad de toneladas de vidrio recogidas en un día específico.

## Clases

### PuntoGeografico

Clase que representa un punto geográfico en coordenadas de latitud y longitud.

Atributos:
- `latitud`: Latitud del punto geográfico.
- `longitud`: Longitud del punto geográfico.

### Persona

Clase que representa una persona.

Atributos:
- `id`: Identificador de la persona.
- `nombre`: Nombre de la persona.
- `apellido`: Apellido de la persona.
- `cedula`: Cédula de identidad de la persona.

### Camion

Clase que representa un camión de recolección.

Atributos:
- `id`: Identificador del camión.
- `conductor`: Objeto de tipo Persona que representa al conductor del camión.
- `asistentes`: Número de asistentes en el camión.

### Carga

Clase que representa la carga de residuos recogida por un camión.

Atributos:
- `toneladas_vidrio`: Cantidad de toneladas de vidrio en la carga.
- `toneladas_papel`: Cantidad de toneladas de papel en la carga.
- `toneladas_plastico`: Cantidad de toneladas de plástico en la carga.
- `toneladas_metal`: Cantidad de toneladas de metal en la carga.
- `toneladas_organico`: Cantidad de toneladas de material orgánico en la carga.

### Ruta

Clase que representa una ruta de recolección.

Atributos:
- `id`: Identificador de la ruta.
- `nombre`: Nombre de la ruta.
- `puntos`: Lista de objetos PuntoGeografico que representan los puntos en la ruta.

### Recoleccion

Clase que representa una recolección de residuos en una ruta determinada.

Atributos:
- `id`: Identificador de la recolección.
- `fecha_inicio`: Fecha y hora de inicio de la recolección.
- `fecha_fin`: Fecha y hora de finalización de la recolección.
- `ruta`: Objeto de tipo Ruta que representa la ruta de la recolección.
- `camion`: Objeto de tipo Camion que representa el camión utilizado en la recolección.
- `asistentes`: Número de asistentes en la recolección.
- `localizaciones`: Lista de objetos PuntoGeografico que representan las localizaciones de recolección en la ruta.
- `carga`: Objeto de tipo Carga que representa la carga de residuos recogida en la recolección.

Métodos:
- `calcular_toneladas_vidrio_en_dia(dia)`: Calcula la cantidad de toneladas de vidrio recogidas en un día específico.

### TrashCity

Clase principal de la aplicación que representa la ciudad de recolección de residuos.

Atributos:
- `recolecciones`: Lista de objetos Recoleccion que representa las recolecciones realizadas en la ciudad.

Métodos:
- `calcular_toneladas_vidrio_en_dia(dia)`: Calcula la cantidad total de toneladas de vidrio recogidas en un día específico en todas las recolecciones.

Esto concluye la descripción TrashCity
