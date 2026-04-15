# Loteria de la Vida
### Un tablero interactivo sobre desigualdad estructural en Mexico
**Tlahtoa Data - Hack ODS UNAM 2026**

**[Jugar ahora](https://liedbaez.github.io/hackods.github.io/dashboard/juego/)** | [Ver el sitio completo](https://liedbaez.github.io/hackods.github.io/) | [Repositorio](https://github.com/LiedBaez/hackods.github.io)

---

Que mexicano no ha jugado Loteria? El juego familiar por excelencia, despues de una comida, en las ferias, en el recreo de la escuela... Asi como en La Loteria, el destino se decide una carta a la vez. Tu, como jugador, no puedes hacer nada: el azar reparte y tu lo aceptas, de frijolito en frijolito.

"Loteria de la vida" es justo eso. Es el simbolo del destino que uno no elige, convertido en datos verificables, porque en Mexico el estado en donde naces no es solo una cuestion de suerte, es estadistica.

La distancia entre Chiapas y Nuevo Leon no se mide solo en kilometros. Mientras que en Chiapas 23 de cada 1,000 recien nacidos no logran sobrevivir a su primer anio, en Nuevo Leon esa cifra se reduce a 8; 3 de cada 4 chiapanecos vive en pobreza multidimensional, mientras que en Nuevo Leon tenemos a 1 de cada 7. En cuanto a empleo formal, vemos un 12% de trabajadores en Chiapas contra un 63% de Nuevo Leon. El IRTE (Indice de Riesgo de Trayectoria Estructural), indicador que construimos para medir esa acumulacion de desventajas, le asigna a Chiapas un 1.0, maximo riesgo posible, y a Nuevo Leon, un 0.0002. Con esto no medimos las diferencias de esfuerzo o merito a nivel individual, medimos la distancia entre dos estados que, si bien, comparten con orgullo una bandera, no comparten las mismas oportunidades.

Asi que te invitamos a elegir un estado. Recorre una trayectoria de vida y compara la tuya con alguien que nacio en otro lado del mapa. Los datos ya estan ahi, pero, realmente los estamos viendo?

---

## Pregunta central

> *"Que tanto determina el estado mexicano en el que naces tu trayectoria de vida?"*

La desigualdad en Mexico, desafortunadamente, no es algo nuevo. Lo que nuestro tablero hace diferente es la manera de medirla y visibilizarla, no como una captura de un momento especifico, sino como una trayectoria, como una acumulacion de desventajas, etapa por etapa: nacimiento, infancia, adolescencia, adultez. Para eso construimos el IRTE (Indice de Riesgo de Trayectoria Estructural), un indice propio que integra 9 variables de 6 fuentes oficiales en 4 dimensiones. Nuestra pregunta no se limita a saber si hay pobreza o desigualdad. Preguntamos como es que estas se apilan a lo largo de una vida: la pobreza, las condiciones de salud y salubridad, la educacion y las oportunidades de empleo, y como varian de acuerdo al estado donde naciste.

La perspectiva novedosa no es el dato, ni la presentacion de este. Es el analisis de la trayectoria completa.

Este tablero esta disenado para jovenes de 15 a 29 anios, sin formacion tecnica en datos. Para estudiantes de preparatoria y universidad que quieran entender la desigualdad en Mexico de forma mas concreta, no abstracta. Y tambien, por que no?, para mi, para ti y para todos los que nos hemos preguntado si el lugar en el que nacimos influyo en quienes somos.

---

## ODS cubiertos

| ODS | Tema | Variables del proyecto |
|---|---|---|
| ODS 1 | Fin de la pobreza | `tasa_pobreza`, `tasa_pobreza_extrema` |
| ODS 3 | Salud y bienestar | `mortalidad_infantil`, `fecundidad_adolescente` |
| ODS 4 | Educacion de calidad | `rezago_educativo`, `abandono_secundaria` |
| ODS 6 | Agua limpia y saneamiento | `acceso_agua`, `acceso_drenaje` |
| ODS 8 | Trabajo decente | `formalidad_laboral` |
| ODS 10 | Reduccion de desigualdades | IRTE (transversal a todas las variables) |

---

## El Indice de Riesgo de Trayectoria Estructural (IRTE)

El IRTE es una construccion analitica del equipo Tlahtoa Data. No reproduce ningun indice oficial existente. Su proposito es medir la posicion relativa de cada estado mexicano en una escala de 0 a 1, donde 1 significa la mayor acumulacion de desventajas estructurales y 0 la menor.

Se compone de **4 dimensiones con peso igual** (25% cada una):

| Dimension | Variables | Fuentes |
|---|---|---|
| **Salud** | mortalidad_infantil (60%), acceso_agua (25%), acceso_drenaje (15%) | SSA, INEGI Censo 2020 |
| **Pobreza** | tasa_pobreza (55%), tasa_pobreza_extrema (45%) | CONEVAL 2022 |
| **Educacion** | rezago_educativo (45%), abandono_secundaria (55%) | CONEVAL, SEP 2022 |
| **Genero y empleo** | fecundidad_adolescente (45%), formalidad_laboral (55%) | CONAPO 2021, IMSS 2023 |

Cada variable se normaliza con min-max sobre los 32 estados y se invierte segun su direccionalidad (en todas excepto formalidad laboral, un valor alto significa peor condicion). El IRTE final es el promedio ponderado de las 4 dimensiones.

Decidimos poner pesos iguales, ya que el intentar ponderar por impacto causal necesitaba una revision sistematica de literatura muy amplia, y quedaria fuera de nuestro alcance por el tiempo limitado del hackathon. Cualquier diferencial de pesos sin esa base nos parecia mas arbitraria que precisa. Es por esto que el optar por pesos iguales fue la opcion mas transparente y defendible.

En cuanto a la estabilidad de nuestro modelo, se realizo un analisis de sensibilidad variando los pesos +/-10 puntos porcentuales por dimension. Los extremos del ranking son estables: Chiapas, Oaxaca y Guerrero permanecen en el tercio superior bajo cualquier variacion. La zona media del ranking muestra mayor movilidad, solo entre 4 y 8 estados cambiaron de posicion segun la ponderacion. El tablero comunica esta incertidumbre.

*Nuestro indicador, IRTE, puede afirmar que Chiapas concentra mas desventajas estructurales que Nuevo Leon. Sin embargo, no puede afirmar que una persona nacida en Chiapas va a tener una trayectoria determinada. La estadistica describe estructuras, no destinos.*

---

## Equipo

| Integrante | Rol |
|---|---|
| Jesus Rafael Loggen Gonzalez | Cientifico de Datos — pipeline IRTE, analisis estadistico y juego interactivo React |
| Zabdiel Taboada Vera | Software Fullstack Developer — landing page Quarto, mapa interactivo Plotly e integracion del sitio |
| Ilse Cristina Gonzalez Diaz | Pitch Leader y Auditora de Impacto — narrativa, fuentes y verificacion |

---

## Fuentes de datos

Criterio de seleccion: solo fuentes oficiales publicas con URL verificable, solo variables disponibles para las 32 entidades federativas, solo datos con licencia abierta. Ninguna variable fue estimada, imputada ni generada por IA.

| Variable | Descripcion | Fuente | Anio | URL |
|---|---|---|---|---|
| `tasa_pobreza` | % poblacion en pobreza multidimensional | CONEVAL | 2022 | [CONEVAL](https://www.inegi.org.mx/desarrollosocial/pm/) |
| `tasa_pobreza_extrema` | % en pobreza extrema | CONEVAL | 2022 | [CONEVAL](https://www.inegi.org.mx/desarrollosocial/pm/) |
| `mortalidad_infantil` | Defunciones por 1,000 nacidos vivos | SSA | 2022 | [Agenda 2030](https://agenda2030.mx/ODSind.html?ind=ODS003000050020&cveind=623&cveCob=99&lang=es#/Indicator) |
| `acceso_agua` | % viviendas sin agua potable | INEGI Censo | 2020 | [Agenda 2030](https://agenda2030.mx/ODSind.html?ind=ODS006000050030&cveind=618&cveCob=99&lang=es#/Indicator) |
| `acceso_drenaje` | % viviendas sin drenaje | INEGI Censo | 2020 | [Agenda 2030](https://agenda2030.mx/ODSind.html?ind=ODS006000050030&cveind=618&cveCob=99&lang=es#/Indicator) |
| `rezago_educativo` | % con rezago educativo | CONEVAL | 2022 | [Agenda 2030](https://agenda2030.mx/ODSind.html?ind=ODS004000100011&cveind=587&cveCob=99&lang=es#/Indicator) |
| `abandono_secundaria` | % desercion en secundaria | SEP | 2022 | [Agenda 2030](https://agenda2030.mx/ODSind.html?ind=ODS004000800020&cveind=385&cveCob=99&lang=es#/Indicator) |
| `fecundidad_adolescente` | Nacimientos por 1,000 mujeres 15-19 | CONAPO | 2021 | [INEGI Natalidad](https://www.inegi.org.mx/app/tabulados/interactivos/?pxq=Natalidad_Natalidad_02_4e506333-fc26-4f8b-af82-575643de5fe2&idrt=126&opc=t) |
| `formalidad_laboral` | % trabajadores registrados IMSS / PEA | IMSS | 2023 | [INEGI Empleo](https://www.inegi.org.mx/temas/empleo/#tabulados) |

**Nota sobre temporalidad:** las fuentes abarcan 2020-2023. No existe un anio unico con cobertura completa en todas las dimensiones. El equipo acepto este trade-off porque el IRTE mide condicion estructural acumulada, no una sola fotografia puntual. Estas condiciones (pobreza, acceso a servicios, rezago educativo, etc) cambian lentamente: el desfase maximo entre fuentes es de 3 anios y no altera las conclusiones del ranking.

---

## Nuestros datos. Justificacion.

El modelo del IRTE no incluye todas las variables disponibles. Incluye las que sobrevivieron tres filtros, en este orden:

1. **Verificabilidad** — solo fuentes oficiales con URL funcional y datos descargables.
2. **Coherencia con el modelo** — cada variable debe asociarse a una etapa de vida y a una dimension independiente del IRTE.
3. **Cobertura completa** — 32 entidades federativas, sin imputacion, sin estimaciones.

### Variables que consideramos y descartamos

**Acceso a electricidad** (INEGI Censo 2020): Disponible en la misma fuente que agua y drenaje. Correlacion superior a 0.80 con ambas variables en los 32 estados. Incluirla solamente inflaria la dimension de servicios basicos sin agregar informacion independiente, por lo que decidimos mantenerla como contexto en el tablero pero no incluirla en el calculo del IRTE.

**Abandono en preparatoria** (SEP 2022): Correlacion de 0.87 con abandono en secundaria. Si se incluian ambas, se inflaria la dimension educativa. Una vez mas, elegimos unicamente secundaria como variable del IRTE, principalmente porque es el punto de quiebre con mayor varianza entre entidades. Asi mismo, el abandono en preparatoria se muestra en el tablero solo como un complemento narrativo.

**PIB per capita estatal** (INEGI): Se descarto ya que este mide produccion agregada, no las condiciones de vida. Entidades con PIB alto pueden tener alta desigualdad interna (por ejemplo, Tabasco, caso emblematico). Decidimos que no es el concepto correcto para un indice de trayectoria vital.

**Tasa de homicidios** (SESNSP): Agregarla mezclaria violencia delictiva con desventajas de desarrollo estructural. Por lo que agregarla al IRTE confundiria dos narrativas que nuestro modelo no puede sostener simultaneamente: la de las condiciones estructurales y la de la seguridad publica. Sin embargo, es una excelente candidata para una dimension separada en una fase futura del proyecto.

**Indice de Marginacion** (CONAPO): Incluir un indice compuesto de otra institucion dentro del IRTE mezclaria dos construcciones analiticas distintas y oscureceria lo que estamos midiendo exactamente. Se opto por variables elementales verificables, no por indices de terceros.

---

## Brechas de datos identificadas

El equipo realizo una auditoria completa de los datos antes de construir el tablero. Consideramos que estos tienen potencial, y por eso los agregamos aqui como el mapa de lo que queda por construir y la evidencia de que sabemos exactamente donde estan los limites de nuestro modelo actual.

| Variable ausente | Etapa del juego | Por que importa | Fuente donde conseguirla |
|---|---|---|---|
| Desglose por sexo en todas las variables | Transversal | El juego permite elegir sexo pero actualmente no diferencia resultados — ninguna variable tiene desglose H/M a nivel estatal en el modelo | ENOE, ENDIREH, ENADID (INEGI) |
| Mortalidad materna | Nacimiento | El juego muestra riesgo al nacer sin incluir el riesgo para la madre | [Agenda 2030 — ODS 3](https://agenda2030.mx/ODSind.html?ind=ODS003000030010&cveind=26&cveCob=99&lang=es#/Indicator) |
| Parto en hospital | Nacimiento | % de nacimientos atendidos en unidad medica — mide acceso real al sistema de salud | [INEGI Derechohabiencia](https://www.inegi.org.mx/temas/derechohabiencia/) |
| Ingreso medio por estado | Empleo | El juego muestra formalidad laboral pero no cuanto gana esa persona — la calidad del empleo queda incompleta | [INEGI ENOE](https://www.inegi.org.mx/programas/enoe/15ymas/#tabulados) |
| Violencia de genero | Violencia | Etapa completa sin datos — pendiente ENDIREH 2021 | [Agenda 2030 — ODS 5](https://agenda2030.mx/ODSind.html?ind=ODS005000120010&cveind=163&cveCob=99&lang=es#/Indicator) |
| Planificacion familiar | Embarazo | Etapa completa sin datos — pendiente ENADID | [Agenda 2030 — ODS 3](https://agenda2030.mx/ODSind.html?ind=ODS003000500010&cveind=140&cveCob=99&lang=es#/Indicator) |

Creemos que estas ausencias no debilitan el proyecto, mas bien, lo situan honestamente en lo que es: la Fase 1 de un observatorio que nuestro equipo tiene documentado y listo para crecer.

---

## Estructura del repositorio

```
hackods.github.io/
├── _quarto.yml                  <- configuracion Quarto del sitio
├── ai-log.md                   <- declaratoria de uso de IA
├── dashboard/
│   ├── index.qmd               <- landing principal (mapa IRTE + KPIs)
│   ├── trayectorias.qmd        <- radar comparativo por estado
│   ├── comparativa.qmd         <- ranking IRTE + barras por dimension
│   ├── metodologia.qmd         <- fuentes, pesos, joins, calidad
│   ├── juego/                  <- juego interactivo React (build)
│   │   ├── index.html
│   │   ├── assets/             <- JS/CSS compilados
│   │   ├── data/               <- JSONs del pipeline IRTE
│   │   └── audio/              <- audio del juego
│   ├── mexico.geojson          <- geometrias para mapa Plotly
│   └── assets/                 <- CSS custom + imagenes personajes
├── data/
│   ├── processed/              <- outputs del pipeline IRTE
│   ├── metadata/               <- provenance, calidad, sensibilidad
│   ├── staging/                <- validacion externa UN
│   └── static_api/             <- 480 simulaciones pre-calculadas
├── config/
│   └── irte_weights.yaml       <- pesos del IRTE
├── assets/
│   ├── characters/             <- Lottie JSONs personajes
│   └── icons/                  <- SVG iconos ODS
├── .github/workflows/
│   └── pages.yml               <- CI/CD: Quarto render + GitHub Pages
├── docs/                       <- output generado (no editar)
├── README.md
├── LICENSE                     <- CC BY-NC-SA 4.0
└── requirements.txt
```

---

## Como reproducir

```bash
# 1. Clonar el repositorio
git clone https://github.com/LiedBaez/hackods.github.io.git
cd hackods.github.io

# 2. Instalar dependencias Python
pip install -r requirements.txt

# 3. Renderizar el sitio
quarto render

# 4. Ver localmente
quarto preview
```

Los datos ya estan procesados en `data/processed/`. No se requiere re-ejecutar el pipeline. El juego React ya esta pre-compilado en `dashboard/juego/`.

---

## Licencia

Este proyecto se distribuye bajo licencia [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.es).

Los datos provienen de fuentes oficiales abiertas: CONEVAL, INEGI, SSA, SEP, CONAPO e IMSS.

Proyecto desarrollado en el marco del [Hack ODS UNAM 2026](https://hackods.unam.mx) — Instituto de Energias Renovables e Instituto de Geofisica, UNAM.
