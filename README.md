# WORKSHOP 4 - API gestión de liga

En este workshop vamos a trabajar realizando una API que nos permita gestionar los datos de una liga de fútbol.

Como en este workshop vamos a trabajar en equipo es importante cómo trabajemos con las ramas, por ello vamos a repartir las tareas para dos personas, que llamaremos developer 1 y developer 2.

Es importante recordar que trabajaremos siguiendo Gitflow:
![gitflow](/assets/gitflow.png)

**PASO 1**

El developer 1 (supervisado por el 2) deberá crear un repositorio en github para alojar el código de este workshop. Una vez creado el repo deberá añadir el código inicial del proyecto, se aconseja que parta del template “node-simple-template” o un repositorio similar.

<https://github.com/The-Valley-School/node-simple-template>

El código debe añadirlo sobre la rama main directamente con un commit. Una vez añadido el código deberá crear una rama develop que parta de main para poder empezar a hacer gitflow

No es necesario hacer ninguna modificación sobre el código, simplemente se trata de añadirlo para empezar a trabajar.

**PASO 2**

Developer 1: Deberá sacar una rama de develop que se llame feature/create-player-model, en esa rama deberá crear el modelo Player con los siguientes datos:

- Nombre
- Apellidos
- Posición preferida
- Número

Developer 2: Deberá sacar una rama de develop que se llama feature/create-team-model, en esa rama deberá crear el modelo para almacenar la información de un equipo:

- Nombre del equipo
- Año de fundación
- Ciudad de origen

Una vez terminados estos desarrollos, ambos developers deberán abrir pull request a develop con las respectivas features. Cada developer revisará la pull request del otro y si están OK se mergearán, si no, deberá hacerle comentarios para que lo modifique hasta que esté OK y se mergee.

P.D: La parte de Sample y SubSample se puede quedar por ahora en el repo, no pasa nada.

**PASO 3**

Developer 1: Deberá sacar una rama de develop llamada feature/add-match-model, donde deberá crear un modelo para almacenar la información de un partido.

Un partido contendrá la siguiente información:

- Equipo local (referencia)
- Equipo visitante (referencia)
- Goles a favor equipo local (number)
- Goles a favor equipo visitante (number)
- Partido jugado o no (booleano)
- Fecha del partido (date)

Developer 2: Deberá sacar una rama de develop llamada feature/add-players-team-relation-and-seed. En esta rama deberá indicar que los jugadores pertenecen a un equipo, (un player tendrá una propiedad team que será una referencia).

También deberá crear un fichero de full.seed.js que se encargue de crear 4 equipos con 5 jugadores cada uno (supongamos que es una liga pequeña y son equipos de fútbol sala y sin cambios)

Una vez hechos ambos desarrollos, los developers deberán abrir pull requests hacia develop, y ambos revisar y mergear las PRs de su compañero.

**PASO 4**

Developer 1: deberá sacar una rama de develop llamada feature/create-cruds donde deberá realizar el código para generar un CRUD que permita la gestión de jugadores, equipos y partidos.

Quizá ya sea buen momento para aprovechar y quitar todo lo relacionado con sample y subsample en esta misma PR ;)

Developer 2: deberá crear una rama partir de develop llamada feature/create-script-for-match-creation donde deberá crear un script que se encargue de crear partidos para que jueguen todos los equipos.

Se deben contemplar todos los cruces posibles, con partidos de ida y vuelta, por ejemplo:

En caso de haber 4 equipos, teniendo IDA y vuelta serían 12 partidos:

- Equipo 1 vs Equipo 2
- Equipo 1 vs Equipo 3
- Equipo 1 vs Equipo 4
- Equipo 2 vs Equipo 1
- Equipo 2 vs Equipo 3
- Equipo 2 vs Equipo 4
- Equipo 3 vs Equipo 1
- Equipo 3 vs Equipo 2
- Equipo 3 vs Equipo 4
- Equipo 4 vs Equipo 1
- Equipo 4 vs Equipo 2
- Equipo 4 vs Equipo 3

Este script eliminará todos los partidos anteriores y creará los nuevos. Las fechas no son relevantes, no es necesario que apliques mucha lógica aquí, puedes poner el primer partido un día y los demás 3 días después, así no coinciden.

Una vez hechos ambos desarrollos, los developers deberán abrir pull requests hacia develop, y ambos revisar y mergear las PRs de su compañero.

**PASO 5**

Developer 2 con supervisión de Developer 1: Deberá crear la rama release/2.0.0 a partir de develop, esta rama servirá para probar todos los desarrollos integrados.

Una vez creada la rama deberá hacer un commit cambiando el package.json para que la versión ahora sea la 2.0.0.

Una vez tengamos lista la rama release/2.0.0 ambos desarrolladores deberán probar que está todo OK, haciendo pruebas con POSMAN para validar que los endpoints funcionan correctamente

Si se detecta algún error, se crear una rama a partir de release/2.0.0, corregirlo y abrir una PR para mergearlo en release/2.0.0.

También el developer 1 deberá crear una rama llamada “add-vercel-json” a partir de release/2.0.0 donde subirá el fichero para poder desplegar en vercel. Cuando tenga la rama lista, deberá abrir PR a release/2.0.0.

Todas las PRs deben ser validadas y mergeadas por el otro developer.

**PASO 6**

Cuando estemos contentos con el funcionamiento de la rama release/2.0.0 y estemos listos para desplegar en producción, el developer 1 con la supervisión del developer 2 deberá abrir dos pull requests:

- Una PR de release/2.0.0 a master (para subir a PRO la release)
- Una PR de release/2.0.0 a develop (para incluir los últimos cambios)

Todas las PRs deben ser validadas y mergeadas por el developer que no las ha creado.

Cuando tengamos todo mergeado, debemos desplegarlo en Vercel

**PASO 7 (OPCIONAL)**

Si habéis llegado hasta aquí, es hora de mejorar nuestra API.

Debes añadir las siguientes funcionalidades y crear una release/3.0.0 siguiendo gitflow:

- Añade validaciones a todos los campos de:
  - Match
  - Player
  - Team
- Crea un endpoint para recuperar la clasificación de la liga, para cada equipo debes sacar:

  - Posición
  - Puntos
  - Goles a favor
  - Goles en contra
  - Partidos jugados

![Untitled](/assets/Untitled.png)
