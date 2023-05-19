# Parcial_Final_POO
Programación Orientada a Objetos – 2023-10 Departamento de Ingeniería de Sistemas y Computación - Universidad del Norte
# TrashCity

TrashCity es una aplicación de gestión de recolección de residuos que permite realizar un seguimiento de las recolecciones de diferentes tipos de materiales en distintas rutas. Permite calcular la cantidad de toneladas de vidrio recogidas en un día específico.

# ¿Como funciona?
Es importante tener en cuenta que el código está hecho para que funcione en Google Colab, por lo que, si se desea usar otros IDE como Visual Studio Code, se deben instalar las respectivas extensiones para su correcto funcionamiento.
Tambien se busca mostrar lo aprendido en a lo largo del curso de Programacion orientada a objetos. Entonces, esta tiene su version base y su version aplicando los patrones de diseños asi como sus respectivos diagramas de UML.

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

## TrashCityBuilder

La clase `TrashCityBuilder` es una clase auxiliar que implementa el patrón de diseño Builder para simplificar la construcción de la instancia de `TrashCity`. Proporciona métodos para agregar recolecciones a la instancia de `TrashCity` de manera gradual y luego construir y obtener la instancia completa.

### Atributos

- `recolecciones`: Lista de objetos `Recoleccion` que representa las recolecciones a agregar a la instancia de `TrashCity`.

### Métodos

- `agregar_recoleccion(recoleccion: Recoleccion)`: Agrega una instancia de `Recoleccion` a la lista de recolecciones.
- `construir() -> TrashCity`: Construye y devuelve la instancia completa de `TrashCity` con las recolecciones agregadas.

#### Uso

```python
# Crear una instancia de TrashCityBuilder
builder = TrashCityBuilder()

# Agregar recolecciones
builder.agregar_recoleccion(recoleccion1)
builder.agregar_recoleccion(recoleccion2)

# Construir la instancia completa de TrashCity
trashcity = builder.construir()
```

En este ejemplo, se crea una instancia de `TrashCityBuilder` y se agregan dos instancias de `Recoleccion` utilizando el método `agregar_recoleccion()`. Luego, se llama al método `construir()` para obtener la instancia completa de `TrashCity` en la variable `trashcity`.

El uso del `TrashCityBuilder` simplifica y estructura el proceso de construcción de la instancia de `TrashCity`, permitiendo un código más legible y modular. Además, proporciona flexibilidad para agregar más pasos o lógica de construcción si es necesario en el futuro.

## Uso de la aplicación

La aplicación TrashCity se utiliza para gestionar y realizar el seguimiento de las recolecciones de residuos en una ciudad. Permite calcular la cantidad de toneladas de vidrio recogidas en un día específico. A continuación se muestra un ejemplo de cómo utilizar la aplicación:

```python
# Importar las clases necesarias
from datetime import datetime
from trashcity import PuntoGeografico, Persona, Camion, Carga, Ruta, Recoleccion, TrashCity

# Crear objetos de PuntoGeografico
punto1 = PuntoGeografico(10.123456, -75.456789)
punto2 = PuntoGeografico(10.234567, -75.567890)
punto3 = PuntoGeografico(10.345678, -75.678901)

# Crear objeto de Ruta
ruta1 = Ruta(1, "Ruta 1", [punto1, punto2, punto3])

# Crear objeto de Persona
persona1 = Persona(1, "Juan", "Guzman", "1193548728")

# Crear objeto de Camion
camion1 = Camion(1, persona1, 2)

# Crear objeto de Carga
carga1 = Carga(2.5, 1.5, 3.0, 1.0, 2.0)

# Crear objeto de Recoleccion
recoleccion1 = Recoleccion(1, datetime(2023, 4, 1, 8, 0), datetime(2023, 4, 1, 12, 0), ruta1, camion1, 2, [punto1, punto2], carga1)

# Crear objeto de TrashCity
trashcity = TrashCity([recoleccion1])

# Calcular la cantidad de toneladas de vidrio recogidas en un día específico
dia = datetime(2023, 4, 1).date()
toneladas_vidrio = trashcity.calcular_toneladas_vidrio_en_dia(dia)

# Imprimir el resultado
print(f"En el día: {dia}, se recogieron: {toneladas_vidrio} toneladas de vidrio.")
```

En el ejemplo anterior, se crean objetos de diferentes clases para representar los puntos geográficos, personas, camiones, cargas, rutas, recolecciones y la ciudad de recolección de residuos. Luego, se utiliza el método `calcular_toneladas_vidrio_en_dia()` para calcular la cantidad de toneladas de vidrio recogidas en un día específico. El resultado se imprime en la consola.

Esto concluye la descripción y uso de la aplicación TrashCity
