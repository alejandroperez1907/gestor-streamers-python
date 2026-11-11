# Gestor de streamers en Python

Este es el proyecto de diccionarios que hice en Programación en primero de ASIR, es un programa de consola en Python para gestionar los canales de una plataforma de streaming tipo Twitch o YouTube, o sea que puedes ver los canales, añadir nuevos, cambiar sus datos, buscarlos, ordenarlos y sacar algunas estadísticas

Todo va con un menú que se repite hasta que le das a salir, y los canales se guardan en un diccionario de diccionarios, es decir, la clave es el nombre del canal y el valor es otro diccionario con sus datos como la categoría, los suscriptores, los ingresos o si está activo

Esto lo pongo en la terminal, dentro de la carpeta del proyecto

```bash
python gestor_streamers.py
```

Y esto es lo que me sale después de elegir la opción 1

```text
Bienvenido al gestor de streamers y canales!

Estas son las opciones disponibles:

1. Mostrar canals
2. Afegir canal
3. Eliminar canal
4. Modificar canal
5. Cercar canals
6. Ordenar canals
7. Estadístiques
8. Esdeveniment afegit (Stream Viral)
9. Sortir

Escoge una opcion: 1
1.- MOSTRAR TOTS ELS CANALS

|    NOMBRE:    | CATEGORIA:  | SUSCRIPTORES: | VISUALIZACIONES: | DIRECTOS_SEMANA: | INGRESSOS: | IDIOMA:  |  ACTIU:
|  PixelMaster  |   Gaming    |     12500     |      980000      |        4         |   1200.5   |  Català  |   1
| CocinaConLuna |    Cuina    |     8400      |      450000      |        2         |   760.0    | Castellà |   1
|  TechByMarc   | Tecnologia  |     15300     |     1100000      |        3         |   1800.0   |  Català  |   1
|  GamerQueen   |   Gaming    |     22100     |     2300000      |        5         |  2600.75   |  Anglès  |   1
...
```

La tabla enseña todos los canales con sus datos alineados en columnas, y en la columna `ACTIU` sale un 1 cuando el canal está activo

> [!NOTE]
> **Textos en catalán y castellano**
> Los nombres de los campos y algunas opciones están en catalán porque así venían en el enunciado, y el resto de mensajes los escribí en castellano

## Opciones del menú

Estas son las nueve opciones que tiene el programa

| Opción | Qué hace |
|---|---|
| 1 | Enseña todos los canales en una tabla |
| 2 | Añade un canal nuevo sin dejar repetir el nombre |
| 3 | Elimina un canal |
| 4 | Cambia un dato de un canal |
| 5 | Busca por categoría, idioma, estado o suscriptores |
| 6 | Ordena por suscriptores, ingresos o visualizaciones |
| 7 | Saca estadísticas de todos los canales |
| 8 | Simula que un canal se hace viral |
| 9 | Sale del programa |

## Por qué lo he montado así

Lo primero es que he usado un diccionario de diccionarios porque era lo que se trabajaba en esta práctica, y además va muy bien para esto, ya que con el nombre del canal como clave no se pueden repetir canales y llegas a los datos de uno directamente con `streamers["PixelMaster"]` sin tener que recorrer toda la lista

Para salir del menú uso una variable `sortir` que se pone a `True` en vez de usar `break`, porque en clase casi siempre nos pedían no usar `break` y así el `while` se acaba solo cuando toca

Para ordenar los canales uso `sorted()` con una `lambda` que coge el dato por el que quiero ordenar, y con `reverse=True` salen de mayor a menor, y las tablas las hago con f-strings y alineación centrada para que las columnas queden rectas

## Lo que mejor me ha salido

Lo que mejor me ha salido son las búsquedas y las estadísticas, porque puedes filtrar de cuatro formas distintas y sacar el canal con más suscriptores, el que más gana, la media de ingresos, el total de directos de la semana y el porcentaje de canales activos, y encima el evento del stream viral, que le suma al canal un 50 % más de suscriptores, le duplica las visualizaciones y le añade 1500 € de ingresos

## Cómo ejecutarlo

No necesita instalar nada aparte de Python, solo hay que lanzar el archivo con el comando de arriba

> [!WARNING]
> **Hace falta Python `3.12` o más nuevo**
> En las tablas uso f-strings con comillas dobles dentro de las llaves, y eso en versiones más viejas que la `3.12` da error de sintaxis nada más arrancar

## Cómo está organizado

Es un solo archivo de Python con los datos de ejemplo y todo el menú dentro

```text
gestor-streamers-python/
├── README.md
├── CHANGELOG.md
├── .gitignore
└── gestor_streamers.py
```

## Lo que me falta

- **Convertir los números al añadir o modificar**, ya que se guardan como texto y después ordenar, buscar por suscriptores o sacar estadísticas da un `TypeError` y el programa se cierra
- **El estado al añadir un canal**, porque compara lo que escribes con un número y nunca llega a guardarse como `True`
- **Proteger el menú con `try/except`**, que ahora si escribes una letra en vez de un número el programa se cierra
- **Guardar los datos en un archivo**, porque al cerrar el programa se pierden todos los cambios
- **Separarlo en funciones**, ya que ahora está todo seguido en un solo bloque y es largo de leer
- **La columna ACTIU**, que enseña un 1 en vez de `True` por cómo formateo el valor en la tabla

## Sobre los datos

Los canales que vienen dentro del programa son inventados, salen del enunciado de la práctica y no son de nadie real, y como no se guarda nada en ningún archivo no hay datos de nadie más

---

Alejandro Pérez · 2º de ASIR · Institut Esteve Terradas i Illa
