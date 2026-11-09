# UMBRAL

**Simulación de toma de decisiones y perfil psicométrico experimental reunidos en un único artefacto HTML, autónomo, portátil y preparado para ejecutarse sin instalación.**

UMBRAL parte de una pregunta sencilla: ¿qué ocurre cuando una decisión técnicamente correcta llega tarde, ignora el contexto o compromete el sistema que debía proteger? El artefacto traslada esa tensión a una experiencia de aula en la que se cruzan documentación, restricciones, presión temporal, planificación y criterio.

No es una presentación sobre toma de decisiones. Es un entorno para tomarlas.

## Estado del proyecto

Versión candidata disponible: `7.3.0`

El repositorio contiene un prototipo experimental destinado a docencia, prueba y mejora iterativa. Experiencias incluidas:

- **Simulación ASTER-7**, con cuenta atrás y consecuencias operativas.
- **Perfil psicométrico**, sin límite de tiempo y con registro ascendente del tiempo empleado.

La separación evita que la presión del juego distorsione el autoinforme. El tiempo del perfil se conserva como dato contrafactual, pero no altera el resultado.

## Qué contiene

### Simulación ASTER-7

La simulación sitúa al participante ante un programa tecnológico sometido a restricciones de seguridad, calendario, presupuesto y coordinación. Para resolverlo debe consultar la información disponible, relacionar evidencias y decidir con recursos limitados.

El núcleo incluye:

- bandeja de comunicaciones E-Tray;
- cinco documentos operativos y un calendario Gantt;
- matriz de desglose del trabajo, WBS;
- cuatro pruebas cognitivas cronometradas;
- incidencias y comunicaciones de retrabajo causadas por decisiones anteriores;
- indicadores de calidad, margen, plazos y clima;
- modalidades de 25 y 50 minutos;
- pausa real de los cronómetros y de las secuencias activas;
- trazabilidad local de respuestas, eventos y orden de actuación;
- informe final imprimible.

### Perfil psicométrico experimental

El perfil se ejecuta fuera de la simulación. Consta de 24 ítems distribuidos en cuatro bloques:

1. Pensamiento.
2. Autorregulación.
3. Interacción.
4. Actuación.

El módulo trabaja con ítems directos, inversos y de equilibrio contextual. Genera un mapa experimental sobre nueve dimensiones:

- análisis estructurado;
- evaluación de riesgos;
- adaptabilidad;
- regulación bajo presión;
- aprendizaje aplicado;
- comprensión interpersonal;
- cooperación autónoma;
- planificación adaptativa;
- control de calidad.

El tiempo se muestra mediante un cronómetro ascendente, se incorpora al resultado y se incluye en la exportación JSON. No existe tiempo máximo ni penalización por duración.

## Arquitectura

UMBRAL se distribuye como un monolito HTML. El marcado, los estilos, la lógica, el arte de portada y los datos del escenario viajan dentro del mismo archivo.

```text
UMBRAL_DUAL_v7.2.1-rc1.html
├── Portal de entrada
│   ├── Simulación ASTER-7
│   └── Perfil psicométrico
├── Motor de estado
├── Temporizadores independientes
├── E-Tray y documentación
├── WBS y pruebas cognitivas
├── Trazabilidad de sesión
├── Motor de perfil
└── Informes y exportación local
```

La decisión de usar un único archivo no responde a una preferencia estética. Reduce la fricción de despliegue en clase: no exige servidor, instalación, dependencias ni conexión durante la ejecución. El precio es un control más estricto del tamaño y de la regresión. En la versión `7.2.1-rc1`, el artefacto ocupa menos de 500.000 bytes.

## Ejecución

No requiere proceso de instalación.

1. Descarga `UMBRAL_DUAL_v7.2.1-rc1.html`.
2. Abre el archivo con un navegador moderno.
3. Elige **Simulación ASTER-7** o **Perfil psicométrico** en la portada.
4. Mantén la pestaña abierta mientras dure la sesión.

También puede publicarse mediante GitHub Pages, siempre que el archivo se conserve como documento HTML de entrada o se renombre a `index.html` en la rama de publicación.

## Compatibilidad

La interfaz incorpora diseños específicos para escritorio, tableta, teléfonos Android y pantallas con poca altura en orientación horizontal. Se han previsto:

- unidades `vh` y `dvh`;
- áreas seguras del dispositivo;
- navegación táctil;
- reorganización de controles en anchuras reducidas;
- alternativa visual cuando el navegador no admite desenfoque de fondo;
- alto contraste;
- reducción de movimiento;
- navegación mediante teclado y foco visible.

El objetivo no es que todas las pantallas sean idénticas. Es que ninguna pierda la función.

## Datos y persistencia

UMBRAL funciona en el navegador y mantiene el estado de la sesión en memoria. Cerrar o recargar la página puede eliminar el progreso no exportado.

El perfil permite descargar un archivo JSON con:

- respuestas registradas;
- dimensiones calculadas;
- bloques completados;
- fecha de generación;
- tiempo total empleado.

El prototipo no necesita servicios remotos para ejecutar sus funciones principales.

## Validación técnica

La versión candidata se ha sometido a comprobaciones estáticas sobre:

- sintaxis JavaScript;
- unicidad de identificadores HTML;
- conservación de las funciones del núcleo 7.0.0;
- separación del perfil respecto al espacio de juego;
- permanencia de la cuenta atrás en la simulación;
- funcionamiento estructural del cronómetro ascendente;
- conservación de las cuatro vistas originales;
- tamaño máximo del monolito;
- presencia de puntos de ruptura para móvil y orientación horizontal.

El archivo `UMBRAL_DUAL_v7.2.1-rc1_QA.json` recoge la comprobación automatizada de esta compilación.

## Estructura recomendada del repositorio

```text
.
├── README.md
├── UMBRAL_DUAL_v7.2.1-rc1.html
├── UMBRAL_DUAL_v7.2.1-rc1_QA.json
├── CHANGELOG.md
├── LICENSE
└── docs/
    ├── capturas/
    └── metodología.md
```

El repositorio puede comenzar solo con el artefacto y este README. La documentación adicional debe crecer cuando exista información que merezca una fuente propia, no para duplicar lo que ya explica el código.

## Uso docente

UMBRAL está pensado para sesiones de aula, demostraciones, prácticas de gestión y ejercicios de reflexión sobre el comportamiento ante restricciones. Puede emplearse de tres formas:

- ejecutar únicamente la simulación;
- completar únicamente el perfil;
- realizar ambos artefactos por separado y comparar después el autoinforme con las decisiones observadas.

La tercera modalidad ofrece el mayor valor pedagógico. No confunde lo que una persona declara con lo que hace, pero permite estudiar la distancia entre ambos planos.

## Límites actuales

La versión `7.2.1-rc1` es una candidata de prueba. El perfil generado es experimental y todavía no dispone de baremos poblacionales ni de una validación psicométrica externa. Las puntuaciones sirven para el análisis docente del prototipo, no para emitir diagnósticos ni certificar competencias.

La validación funcional completa requiere pruebas reales en distintos navegadores y dispositivos. El control estático reduce regresiones. No sustituye la prueba de campo.

## Hoja de ruta

Las siguientes líneas de evolución permanecen abiertas:

- completar la prueba cruzada en navegadores móviles;
- ampliar el contraste entre autoinforme y conducta observada;
- incorporar escenarios equivalentes sin repetir respuestas óptimas;
- mejorar el informe comparativo de sesión;
- documentar la metodología y el modelo de evidencias;
- consolidar una versión estable a partir de la experiencia en aula.

## Colaboración

Las incidencias deben incluir:

- versión exacta del artefacto;
- navegador y sistema operativo;
- tamaño y orientación de pantalla;
- secuencia mínima para reproducir el problema;
- resultado obtenido y resultado esperado;
- captura de pantalla cuando el fallo sea visual.

Las propuestas de cambio deben conservar tres invariantes: el archivo seguirá siendo autónomo, el perfil permanecerá separado del cronómetro de misión y ninguna mejora podrá alterar silenciosamente el resultado operativo del núcleo.

## Autoría

Diseño, concepto y desarrollo: **Manuel Hernández**.

UMBRAL es un artefacto académico experimental en evolución.
