# Sistema Multiagente de Negociación

## Descripción del proyecto

El proyecto consiste en desarrollar un sistema multiagente de negociación para apoyar la toma de decisiones dentro de una empresa.

La idea principal es representar diferentes áreas de una empresa mediante agentes de inteligencia artificial, donde cada agente tendrá objetivos y necesidades diferentes. Los agentes podrán analizar una situación, realizar propuestas, negociar entre ellos y llegar a una decisión conjunta.

Por ejemplo, una empresa puede contar con un presupuesto de $100 millones, mientras que sus diferentes áreas solicitan un total de $120 millones. Los agentes deberán negociar para encontrar una distribución que respete el presupuesto disponible y tenga en cuenta las necesidades de cada área.

El sistema estará compuesto inicialmente por agentes relacionados con Finanzas, Marketing, Tecnología, Recursos Humanos y Operaciones, además de un agente coordinador encargado de organizar el proceso de negociación.

---

# Estrategia de Branching

## Estrategia seleccionada: GitHub Flow

Para el desarrollo de este proyecto se seleccionó la estrategia **GitHub Flow**, debido a que se adapta a las características del equipo y al tipo de proyecto que se está desarrollando.

La estrategia se basa principalmente en una rama principal llamada `main` y ramas temporales `feature/*`, donde cada nueva funcionalidad se desarrolla de manera independiente y posteriormente se integra mediante un Pull Request.

La estructura que se utilizará será:

main
│
├── feature/setup-ui
├── feature/finance-agent
├── feature/marketing-agent
├── feature/technology-agent
└── feature/negotiation-engine

## Justificación de la elección

### Tamaño del equipo

El equipo está compuesto por **2 integrantes**, por lo que no se considera necesario utilizar una estrategia de branching demasiado compleja. GitHub Flow permite que cada integrante trabaje en diferentes funcionalidades mediante ramas independientes y posteriormente integre sus cambios a `main` mediante Pull Requests.

Esto facilita la organización del trabajo y reduce la posibilidad de que varios integrantes modifiquen directamente la rama principal.

### Frecuencia de despliegue esperada

El proyecto se desarrollará mediante cambios y funcionalidades que se irán integrando progresivamente. Por esta razón, GitHub Flow permite realizar integraciones frecuentes a `main` después de que los cambios hayan sido revisados y validados por el pipeline.

De esta manera, cada funcionalidad puede pasar por el proceso:

Feature → Pull Request → Revisión → Pipeline → Merge → main

### Madurez del pipeline CI/CD

El proyecto tendrá un pipeline DevSecOps encargado de realizar controles automáticos antes de permitir la integración de cambios.

El pipeline incluirá principalmente:

- Detección de secretos mediante Gitleaks.
- Análisis del código mediante un linter.
- Ejecución automática en Pull Requests y cambios realizados en el repositorio.

Debido a que el pipeline se encuentra en una etapa inicial de implementación, GitHub Flow permite mantener un proceso sencillo en el que cada Pull Request puede ser validado automáticamente antes de integrarse a `main`.

### Necesidad de múltiples versiones en paralelo

El proyecto no requiere mantener diferentes versiones del sistema funcionando simultáneamente. Por este motivo, no es necesario utilizar ramas permanentes destinadas a diferentes versiones o releases.

La rama `main` representará la versión principal del proyecto, mientras que las ramas `feature/*` serán temporales y desaparecerán después de integrar sus cambios.

### Complejidad del proceso de release

El proyecto es de carácter académico y no requiere un proceso de lanzamiento complejo. No se espera mantener diferentes versiones de producción ni realizar releases independientes de cada componente.

Por esto, GitHub Flow permite mantener un proceso de integración sencillo y adecuado para el tamaño y las necesidades del proyecto.

---

# Flujo de trabajo

Cada integrante deberá crear una rama `feature/*` para desarrollar una funcionalidad específica.

El flujo será:

1. Crear una rama a partir de `main`.
2. Realizar los cambios necesarios.
3. Hacer commit de los cambios.
4. Subir la rama al repositorio.
5. Crear un Pull Request hacia `main`.
6. Esperar la ejecución del pipeline DevSecOps.
7. Realizar la revisión del código.
8. Aprobar el Pull Request.
9. Realizar el merge hacia `main`.

No se realizarán cambios directamente sobre `main`.

---

# Pipeline DevSecOps

El proyecto contará con un pipeline automatizado mediante **GitHub Actions**.

El pipeline tendrá como objetivo realizar controles de seguridad y calidad antes de integrar los cambios.

Entre los controles principales se encuentran:

- **Gitleaks:** detección de posibles secretos o credenciales expuestas.
- **Linter:** revisión automática de la calidad y formato del código.
- **Pull Requests:** ejecución automática de los controles antes de permitir la integración.

La rama `main` estará protegida para requerir un Pull Request, superar el status check del pipeline y evitar Force Push.

---

# Objetivo de la estrategia

La utilización de GitHub Flow busca mantener un proceso de desarrollo sencillo, organizado y seguro, permitiendo que los tres integrantes trabajen de manera independiente y que los cambios sean revisados y validados antes de llegar a la rama principal.

Además, la integración del pipeline DevSecOps permite detectar problemas de seguridad y calidad de código durante el proceso de desarrollo, reduciendo el riesgo de incorporar cambios incorrectos o información sensible al proyecto.