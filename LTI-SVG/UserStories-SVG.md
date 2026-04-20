# 1. Épicas

## E1 — Alineación de Vacante

**Descripción**  
Garantiza que recruiter y hiring manager comparten criterios y expectativas antes de iniciar el proceso, evitando retrabajo posterior.

---

## E2 — Gestión Operativa de Bloqueos

**Descripción**  
Permite identificar, asignar y resolver bloqueos que impiden avanzar el proceso de selección.

---

## E3 — Decisión y Debrief

**Descripción**  
Facilita consolidar la evaluación y tomar una decisión final trazable y fundamentada.

---

# 2. User Stories (MVP)

## US-01

- **Épica:** E1
- **Título:** Crear vacante en estado pendiente de alineación
- **Historia:**  
  "Como recruiter, quiero crear una vacante con información básica para poder iniciar el proceso de alineación con el hiring manager"
- **Descripción:**  
  Permite iniciar el proceso sin necesidad de completar toda la alineación desde el primer momento.
- **Criterios de aceptación (BDD):**
  - **Dado que** soy recruiter  
    **Cuando** creo una vacante con la información mínima obligatoria  
    **Entonces** la vacante queda en estado "pendiente de alineación"
  - **Dado que** la vacante está en estado "pendiente de alineación"  
    **Cuando** accedo al detalle de la vacante  
    **Entonces** veo que la alineación está pendiente de completar
  - **Dado que** faltan campos obligatorios  
    **Cuando** intento crear la vacante  
    **Entonces** el sistema impide su creación y muestra los campos requeridos
- **Estimación:** S
- **Tipo:** Core

### INVEST
- Independent: Sí — No depende de otras historias para aportar valor inicial.
- Negotiable: Sí — Los campos mínimos pueden ajustarse.
- Valuable: Sí — Permite iniciar el flujo.
- Estimable: Sí — Alcance acotado.
- Small: Sí
- Testable: Sí — Estados verificables.

---

## US-02

- **Épica:** E1
- **Título:** Definir criterios de la vacante
- **Historia:**  
  "Como recruiter, quiero definir criterios y requisitos para alinearlos con el hiring manager"
- **Descripción:**  
  Permite estructurar la vacante con una base común antes de su validación.
- **Criterios de aceptación (BDD):**
  - **Dado que** existe una vacante creada  
    **Cuando** edito su información de alineación  
    **Entonces** puedo definir objetivo, requisitos y criterios de evaluación
  - **Dado que** he informado criterios válidos  
    **Cuando** guardo la alineación  
    **Entonces** los criterios quedan asociados a la vacante
  - **Dado que** faltan campos obligatorios de alineación  
    **Cuando** intento guardar  
    **Entonces** el sistema impide continuar y muestra qué información falta
- **Estimación:** M
- **Tipo:** Core

### INVEST
- Independent: Parcial  
  - Justificación: Requiere que exista una vacante previa (US-01).  
  - Mejora: Mantener US-01 como prerequisito explícito del flujo.
- Negotiable: Sí  
  - Justificación: El nivel de detalle de criterios puede variar.
- Valuable: Sí  
  - Justificación: Define la base del proceso de selección.
- Estimable: Sí  
  - Justificación: Funcionalidad clara de edición y persistencia.
- Small: Sí  
  - Justificación: Acotada a definición de criterios.
- Testable: Sí  
  - Justificación: Validaciones y persistencia comprobables.

---

## US-03

- **Épica:** E1
- **Título:** Validar alineación
- **Historia:**  
  "Como hiring manager, quiero validar la vacante para asegurar que cumple mis expectativas"
- **Descripción:**  
  Permite cerrar la alineación y habilitar la ejecución de la vacante.
- **Criterios de aceptación (BDD):**
  - **Dado que** existe una vacante con alineación definida  
    **Cuando** el hiring manager accede a su detalle  
    **Entonces** puede revisar la información antes de validarla
  - **Dado que** el hiring manager considera correcta la alineación  
    **Cuando** la valida  
    **Entonces** la vacante pasa a estado "alineada"
  - **Dado que** una vacante ya alineada sufre cambios en criterios clave  
    **Cuando** esos cambios se guardan  
    **Entonces** la vacante vuelve a estado "pendiente de validación"
- **Estimación:** M
- **Tipo:** Core

### INVEST
- **Independent:** Parcial — Depende de alineación previa.
- **Negotiable:** Sí
- **Valuable:** Sí — Desbloquea ejecución.
- **Estimable:** Sí
- **Small:** Sí
- **Testable:** Sí

---

## US-04

- **Épica:** E2
- **Título:** Crear bloqueo operativo
- **Historia:**  
  "Como recruiter, quiero registrar un bloqueo para poder hacer visible un problema y facilitar que el proceso vuelva a avanzar"
- **Descripción:**  
  Introduce el concepto de bloqueo operativo en el sistema.
- **Criterios de aceptación (BDD):**
  - **Dado que** estoy en una vacante activa  
    **Cuando** registro un bloqueo con descripción y responsable  
    **Entonces** el bloqueo queda creado y asociado a la vacante
  - **Dado que** se ha creado un bloqueo  
    **Cuando** accedo al detalle de la vacante  
    **Entonces** el bloqueo aparece en el listado de bloqueos activos
  - **Dado que** no he informado un responsable  
    **Cuando** intento guardar el bloqueo  
    **Entonces** el sistema impide su creación
- **Estimación:** S
- **Tipo:** Core

### INVEST
- **Independent:** Parcial — Requiere vacante existente.
- **Negotiable:** Sí
- **Valuable:** Sí — Hace visible el problema y permite actuar.
- **Estimable:** Sí
- **Small:** Sí
- **Testable:** Sí

---

## US-05

- **Épica:** E2
- **Título:** Visualizar bloqueos
- **Historia:**  
  "Como recruiter, quiero ver bloqueos para entender por qué el proceso no avanza"
- **Descripción:**  
  Da visibilidad al estado operativo de la vacante.
- **Criterios de aceptación (BDD):**
  - **Dado que** una vacante tiene bloqueos activos  
    **Cuando** accedo a su detalle  
    **Entonces** veo el listado de bloqueos activos
  - **Dado que** existe un bloqueo registrado  
    **Cuando** consulto su información  
    **Entonces** veo su causa y su responsable
  - **Dado que** una vacante no tiene bloqueos activos  
    **Cuando** accedo a su detalle  
    **Entonces** el sistema lo indica claramente
- **Estimación:** M
- **Tipo:** Core

### INVEST
- **Independent:** Parcial — Requiere bloqueos.
- **Negotiable:** Sí
- **Valuable:** Sí — Aporta visibilidad operativa.
- **Estimable:** Sí
- **Small:** Sí
- **Testable:** Sí

---

## US-06

- **Épica:** E2
- **Título:** Crear acción para bloqueo
- **Historia:**  
  "Como recruiter, quiero asignar acciones para resolver bloqueos y hacer avanzar el proceso"
- **Descripción:**  
  Permite asignar responsabilidad concreta para resolver un bloqueo.
- **Criterios de aceptación (BDD):**
  - **Dado que** existe un bloqueo activo  
    **Cuando** creo una acción y asigno un responsable  
    **Entonces** la acción queda asociada al bloqueo
  - **Dado que** he creado una acción válida  
    **Cuando** la guardo  
    **Entonces** la acción queda registrada en el sistema
  - **Dado que** no he asignado responsable  
    **Cuando** intento guardarla  
    **Entonces** el sistema impide su creación
- **Estimación:** S
- **Tipo:** Core

### INVEST
- Independent: Parcial  
  - Justificación: Depende de un bloqueo existente (US-04).  
  - Mejora: En el futuro podría desacoplarse permitiendo acciones no ligadas inicialmente a bloqueos.
- Negotiable: Sí  
  - Justificación: Los atributos de la acción pueden evolucionar.
- Valuable: Sí  
  - Justificación: Introduce ejecución operativa real.
- Estimable: Parcial  
  - Justificación: Puede crecer si se añaden notificaciones o SLA.  
  - Mejora: Limitar alcance en MVP a creación básica.
- Small: Sí  
  - Justificación: Solo creación simple.
- Testable: Sí  
  - Justificación: Asociación y validaciones verificables.

---

## US-07

- **Épica:** E2
- **Título:** Visualizar acciones asignadas
- **Historia:**  
  "Como recruiter, quiero ver mis acciones asignadas para saber qué tareas debo ejecutar"
- **Descripción:**  
  Permite a cada participante del proceso conocer sus responsabilidades pendientes.
- **Criterios de aceptación (BDD):**
  - **Dado que** tengo acciones asignadas  
    **Cuando** accedo a mi vista de acciones  
    **Entonces** veo el listado de acciones pendientes
  - **Dado que** existe una acción asignada  
    **Cuando** la consulto  
    **Entonces** veo su estado actual
  - **Dado que** no tengo acciones asignadas  
    **Cuando** accedo  
    **Entonces** el sistema lo indica claramente
- **Estimación:** S
- **Tipo:** Nice-to-have

### INVEST
- **Independent:** Parcial — Requiere acciones.
- **Negotiable:** Sí
- **Valuable:** Sí — Mejora ejecución individual.
- **Estimable:** Sí
- **Small:** Sí
- **Testable:** Sí

---

## US-08

- **Épica:** E2
- **Título:** Resolver bloqueo
- **Historia:**  
  "Como recruiter, quiero marcar bloqueos como resueltos para reflejar que el proceso puede continuar"
- **Descripción:**  
  Permite cerrar el ciclo operativo del bloqueo.
- **Criterios de aceptación (BDD):**
  - **Dado que** existe un bloqueo activo  
    **Cuando** lo marco como resuelto  
    **Entonces** su estado cambia a "resuelto"
  - **Dado que** un bloqueo está resuelto  
    **Cuando** accedo  
    **Entonces** no aparece como activo
  - **Dado que** un bloqueo se reabre  
    **Cuando** detecto que persiste el problema  
    **Entonces** vuelve a estado activo
- **Estimación:** S
- **Tipo:** Core

### INVEST
- **Independent:** Parcial
- **Negotiable:** Sí
- **Valuable:** Sí
- **Estimable:** Sí
- **Small:** Sí
- **Testable:** Sí

---

## US-09

- **Épica:** E3
- **Título:** Registrar feedback
- **Historia:**  
  "Como entrevistador, quiero registrar feedback para evaluar candidatos y aportar evidencia para la decisión final"
- **Descripción:**  
  Permite capturar información clave de evaluación.
- **Criterios de aceptación (BDD):**
  - **Dado que** tengo una entrevista  
    **Cuando** registro feedback  
    **Entonces** queda asociado
  - **Dado que** el feedback es válido  
    **Cuando** lo guardo  
    **Entonces** se persiste correctamente
  - **Dado que** faltan campos obligatorios  
    **Cuando** intento enviarlo  
    **Entonces** el sistema lo impide
- **Estimación:** M
- **Tipo:** Core

### INVEST
- Independent: Parcial  
  - Justificación: Depende de entrevista o candidatura existente.  
  - Mejora: Permitir feedback manual básico en MVP.
- Negotiable: Sí  
  - Justificación: La estructura puede evolucionar.
- Valuable: Crítica  
  - Justificación: Sin feedback no hay decisión.
- Estimable: Parcial  
  - Justificación: Depende del nivel de detalle requerido.  
  - Mejora: Limitar a campos mínimos en MVP.
- Small: Sí  
- Testable: Sí  

---

## US-10

- **Épica:** E3
- **Título:** Visualizar feedback
- **Historia:**  
  "Como recruiter, quiero ver feedback en una única vista para poder analizar fácilmente a los candidatos"
- **Descripción:**  
  Facilita la revisión del feedback disponible antes de consolidar la decisión.
- **Criterios de aceptación (BDD):**
  - **Dado que** una candidatura tiene feedback registrado  
    **Cuando** accedo a su detalle  
    **Entonces** veo el listado de evaluaciones disponibles
  - **Dado que** existen múltiples evaluaciones de una candidatura  
    **Cuando** reviso la vista agregada  
    **Entonces** puedo compararlas en una única pantalla
  - **Dado que** una candidatura no tiene feedback registrado  
    **Cuando** accedo a su detalle  
    **Entonces** el sistema lo indica claramente
- **Estimación:** S
- **Tipo:** Core

### INVEST
- **Independent:** Parcial — Requiere feedback previo.
- **Negotiable:** Sí
- **Valuable:** Sí — Facilita revisión.
- **Estimable:** Sí
- **Small:** Sí
- **Testable:** Sí

---

## US-11

- **Épica:** E3
- **Título:** Generar debrief
- **Historia:**  
  "Como recruiter, quiero generar un resumen para facilitar decisión"
- **Descripción:**  
  Permite consolidar el feedback en una vista resumida sin lógica avanzada de IA.
- **Criterios de aceptación (BDD):**
  - **Dado que** existe feedback registrado para una candidatura  
    **Cuando** genero el debrief  
    **Entonces** el sistema crea un resumen consolidado
  - **Dado que** el feedback requerido está incompleto  
    **Cuando** intento generar el debrief  
    **Entonces** el sistema lo indica y no lo genera
  - **Dado que** el debrief ya ha sido generado  
    **Cuando** accedo a la candidatura  
    **Entonces** puedo revisarlo antes de la decisión final
- **Estimación:** M
- **Tipo:** Core

### INVEST
- **Independent:** Parcial — Requiere feedback previo.
- **Negotiable:** Sí — La forma de consolidación puede evolucionar.
- **Valuable:** Muy alta — Prepara la decisión.
- **Estimable:** Parcial — Hay que definir bien qué significa “resumen consolidado”.
- **Small:** Sí — Si se limita a agregación básica.
- **Testable:** Sí

---

## US-12

- **Épica:** E3
- **Título:** Registrar decisión
- **Historia:**  
  "Como hiring manager, quiero registrar una decisión para cerrar la candidatura"
- **Descripción:**  
  Permite cerrar el proceso con trazabilidad.
- **Criterios de aceptación (BDD):**
  - **Dado que** existe un debrief disponible  
    **Cuando** el hiring manager registra una decisión final  
    **Entonces** la candidatura queda cerrada con dicha decisión
  - **Dado que** la decisión ha sido registrada  
    **Cuando** accedo al detalle de la candidatura  
    **Entonces** veo la decisión almacenada
  - **Dado que** una candidatura ya ha sido cerrada  
    **Cuando** la consulto  
    **Entonces** veo la trazabilidad de su cierre
- **Estimación:** S
- **Tipo:** Core

### INVEST
- **Independent:** Parcial — Depende del debrief.
- **Negotiable:** Sí
- **Valuable:** Crítica — Cierra el proceso.
- **Estimable:** Sí
- **Small:** Sí
- **Testable:** Sí

---

# 3. Vertical Slices (MVP)

## VS1 — Alineación

- **Historias:** US-01, US-02, US-03
- **Flujo:** crear vacante → definir criterios → validar alineación

---

## VS2 — Ejecución operativa

- **Historias:** US-04, US-05, US-06, US-07, US-08
- **Flujo:** crear bloqueo → visualizar bloqueo → crear acción → visualizar acciones → resolver bloqueo

---

## VS3 — Decisión

- **Historias:** US-09, US-10, US-11, US-12
- **Flujo:** registrar feedback → visualizar feedback → generar debrief → registrar decisión

---

# 4. Mapa de dependencias

- US-02 → US-01
- US-03 → US-02
- US-05 → US-04
- US-06 → US-04
- US-07 → US-06
- US-08 → US-04
- US-10 → US-09
- US-11 → US-09
- US-12 → US-11

---

# 5. Priorización MVP

1. US-01
2. US-02
3. US-03
4. US-04
5. US-05
6. US-06
7. US-07
8. US-08
9. US-09
10. US-10
11. US-11
12. US-12

---

# 6. Generación de backlog de producto con distintos prompts

Para generar el backlog del producto se han utilizado los prompts indicados en ![Prompts usados](propmts_backlog-SVG.md)[prompts_backlog-SVG]

Las conclusiones obtenidas tras analizar las respuestas de los distntos prompts han sido las siguientes:

Después de probar los distintos prompts para generar el backlog, me he dado cuenta de que cada uno aporta algo diferente, pero también tienen bastantes limitaciones, sobre todo si no se revisa bien el resultado.

El *primer prompt* me ha servido como punto de partida. Es fácil de entender y la priorización tiene sentido a nivel general porque sigue el flujo del producto (primero alineación, luego ejecución y finalmente decisión). El problema es que es demasiado simple: no tiene en cuenta esfuerzo, riesgo ni otros factores importantes. Es útil para empezar, pero no lo usaría para tomar decisiones reales.

El *segundo prompt* mejora bastante porque introduce criterios como valor, urgencia o complejidad. Aquí ya se empieza a ver un razonamiento más estructurado, pero aun así hay algo que no termina de convencerme: los números son un poco arbitrarios. Además, a veces coloca historias arriba que en realidad no se podrían implementar todavía por dependencias.

El *tercer prompt* es donde empiezo a ver un salto de calidad. Al usar el PRD, la priorización tiene más sentido desde el punto de vista del producto, no solo de las historias. Aquí ya no solo se ordena, sino que también se detectan problemas, como que faltan piezas importantes del flujo (por ejemplo, entrevistas o candidaturas). Me parece más útil porque conecta backlog con negocio.

El *cuarto prompt* (User Story Mapping) no prioriza como tal, pero me ha ayudado a entender el producto de forma global. Ver el flujo completo (inicio → ejecución → decisión) me ha permitido detectar que, aunque sobre el papel parece que todo encaja, en realidad faltan cosas importantes para que el sistema funcione de verdad.

El *quinto prompt* es el más completo, ya que es una mejroa del tercero. Combina métricas, contexto del PRD y además hace una especie de revisión crítica del backlog. Creo que es el que más se parece a cómo se trabajaría en un entorno real, porque no solo prioriza, sino que también cuestiona si lo que se ha definido tiene sentido. Eso sí, también es el más complejo y requiere entender bien lo que está pasando para no aceptar el resultado sin más.

Viendo las respuestas de todos los promtos, parece que hay varios problemas que vienen de pasos anteriores:

* El flujo no es realmente end-to-end: faltan historias clave como la gestión de candidaturas o entrevistas, que sí aparecen en el PRD. Por ejemplo, el US-09 "Registrar feedback" requiere crear una entrevista o candidatura, y no hay una US para ello.
* Dependencias ocultas: algunas historias se priorizan como si fueran independientes, pero en realidad no lo son. Por ejemplo la US "Registrar decisión" depnde de US-09 "registrar feedback"
* Riesgo de confiar demasiado en la IA: varios resultados parecen correctos, pero al analizarlos en detalle ves incoherencias


Si tengo que quedarme con uno, elegiría el prompt 3 o el 5, porque son los únicos que realmente tienen en cuenta el contexto del producto y no solo las User Stories. No obstante entre los dos me quedo con el 5 por ser un prompt mejorado a partir del 3.

Aun así, lo más importante es que:

* No basta con generar backlog automáticamente
* Hay que revisar siempre el resultado
* Y sobre todo, que si las User Stories o el modelo de dominio tienen problemas, el backlog también los va a tener

En resumen, la IA ayuda mucho a avanzar rápido, pero si no entiendes lo que estás haciendo, es fácil aceptar resultados que parecen correctos pero no lo son del todo.


# 7. Product Backlog Priorizado — LTI MVP

## 1. Objetivo del backlog

Este backlog prioriza las User Stories del MVP de LTI con un criterio de producto orientado a:

- validar cuanto antes las hipótesis clave del producto
- construir un flujo funcional de punta a punta
- preservar el diferencial de LTI frente a un ATS tradicional

## 2. Criterios de priorización usados

La priorización se ha hecho teniendo en cuenta:

- valor de negocio respecto al PRD
- capacidad de validar hipótesis de producto
- dependencia funcional entre historias
- capacidad de construir un flujo operativo real
- aporte al diferencial del producto:
  - alineación recruiter–hiring manager
  - visibilidad y gestión de bloqueos
  - feedback estructurado y decisión trazable

## 3. Backlog priorizado

| Prioridad | ID | Título | Tipo | Dependencias | Justificación |
|---|---|---|---|---|---|
| 1 | US-01 | Crear vacante en estado pendiente de alineación | Core | — | Es la puerta de entrada del flujo. Sin vacante no existe alineación, ejecución ni decisión. Permite arrancar el proceso con la mínima fricción. |
| 2 | US-02 | Definir criterios de la vacante | Core | US-01 | Es la base de la alineación estructurada. Aterriza el objetivo del rol, requisitos y criterios de evaluación, que son parte central del diferencial del producto. |
| 3 | US-03 | Validar alineación | Core | US-02 | Cierra el acuerdo entre recruiter y hiring manager y habilita la ejecución de la vacante. Sin esta validación no existe una fuente de verdad compartida. |
| 4 | US-04 | Crear bloqueo operativo | Core | US-03 | Introduce uno de los objetos de dominio más diferenciales de LTI: el bloqueo operativo. Convierte el proceso en algo gestionable, no solo registrable. |
| 5 | US-05 | Visualizar bloqueos | Core | US-04 | Aporta visibilidad operativa sobre qué impide avanzar una vacante. Hace tangible la propuesta de valor de “centro de decisiones y bloqueos”. |
| 6 | US-06 | Crear acción para bloqueo | Core | US-04 | Convierte visibilidad en ejecución. Introduce accountability explícito mediante asignación de responsables y acciones correctivas. |
| 7 | US-08 | Resolver bloqueo | Core | US-04 | Cierra el ciclo operativo del bloqueo y permite reflejar recuperación del flujo. Sin esta historia, la gestión de bloqueos queda incompleta. |
| 8 | US-09 | Registrar feedback | Core | Falta historia previa de entrevista/candidatura | Es la pieza mínima para capturar evidencia evaluativa. Sin feedback no se puede sostener una decisión fundamentada. |
| 9 | US-10 | Visualizar feedback | Core | US-09 | Facilita revisar el feedback en una única vista y prepara la comparación entre evaluadores. Acerca el valor de evaluación estructurada del PRD. |
| 10 | US-11 | Generar debrief | Core | US-09, idealmente US-10 | Conecta evaluación con decisión. Permite consolidar información antes del cierre y preparar una decisión más rápida y trazable. |
| 11 | US-12 | Registrar decisión | Core | US-11 | Cierra la candidatura con trazabilidad. Es crítica para el flujo final, pero depende completamente de que exista evidencia previa consolidada. |
| 12 | US-07 | Visualizar acciones asignadas | Nice-to-have | US-06 | Mejora la experiencia individual de seguimiento, pero no es imprescindible para demostrar el valor central del MVP en la primera release. |

---

## 4. Orden recomendado de construcción

El orden recomendado de implementación no sigue solo prioridad teórica, sino dependencias reales y capacidad de construir un flujo funcional:

### Slice 1 — Alineación de vacante
- US-01 — Crear vacante en estado pendiente de alineación
- US-02 — Definir criterios de la vacante
- US-03 — Validar alineación

### Slice 2 — Ejecución operativa
- US-04 — Crear bloqueo operativo
- US-05 — Visualizar bloqueos
- US-06 — Crear acción para bloqueo
- US-08 — Resolver bloqueo

### Slice 3 — Evaluación y decisión
- US-09 — Registrar feedback
- US-10 — Visualizar feedback
- US-11 — Generar debrief
- US-12 — Registrar decisión

### Mejora posterior
- US-07 — Visualizar acciones asignadas

---

## 5. MVP propuesto

### MVP mínimo para validar hipótesis
Incluye:

- US-01
- US-02
- US-03
- US-04
- US-05
- US-06
- US-08
- US-09

### Qué valida este MVP mínimo
- que recruiter y hiring manager usan LTI para alinear una vacante antes de ejecutar
- que el sistema hace visibles los bloqueos y permite actuar sobre ellos
- que existe comportamiento real de captura de feedback estructurado

### Limitación del MVP mínimo
Todavía no cierra el flujo completo de decisión.

---

### MVP ampliado
Añade:

- US-10
- US-11
- US-12

### Qué valida el MVP ampliado
- que el feedback es revisable y comparable
- que el debrief acelera la preparación de la decisión
- que la candidatura puede cerrarse con trazabilidad

---

## 6. Fuera de MVP inicial

### Post-MVP
- US-07 — Visualizar acciones asignadas

### Motivo
No cambia la capacidad del sistema para alinear, gestionar bloqueos o cerrar decisiones. Mejora usabilidad, pero no reduce el principal riesgo de producto.

---

## 7. Dependencias clave

- US-02 → US-01
- US-03 → US-02
- US-04 → US-03
- US-05 → US-04
- US-06 → US-04
- US-07 → US-06
- US-08 → US-04
- US-10 → US-09
- US-11 → US-09
- US-12 → US-11

---

## 8. Observaciones críticas

### 8.1 Gaps de dominio detectados
El backlog actual no cubre completamente el flujo end-to-end del dominio. Faltan al menos historias para:

- crear candidatura
- registrar o planificar entrevista
- asignar entrevistador
- marcar candidatura lista para decisión

Sin estas piezas, el bloque E3 depende de precondiciones que aparecen en el PRD pero no están implementadas como historias.

### 8.2 Historias mal definidas o mejorables

#### US-07
La historia está formulada como “Como recruiter…”, pero la descripción dice que aplica a “cada participante del proceso”.
Debería redefinirse el rol:
- como usuario interno
- o como responsable asignado

#### US-11
“Generar un resumen” es demasiado ambiguo.
Conviene concretar si el debrief:
- agrega feedback por criterio
- resume por entrevistador
- señala contradicciones
- o solo consolida texto libre

#### US-05
La historia habla de ver bloqueos en el detalle de una vacante, pero el PRD habla de una vista centralizada de decisiones y bloqueos.
Puede ser válida como recorte MVP, pero está por debajo del diferencial completo prometido.

#### E1 en general
Falta una historia explícita para resolver discrepancias recruiter–manager, aunque sí aparece en el caso de uso principal del PRD.

---

## 9. Recomendación final

### Release 1
- US-01
- US-02
- US-03
- US-04
- US-05
- US-06
- US-08

### Release 1.5
- Historias nuevas de candidatura/entrevista
- US-09

### Release 2
- US-10
- US-11
- US-12

### Post-MVP
- US-07

---

## 10. Conclusión ejecutiva

La mejor secuencia para LTI no es empezar por “cerrar decisiones”, sino por asegurar:

1. alineación real de la vacante  
2. visibilidad y resolución de bloqueos  
3. evaluación estructurada  
4. decisión trazable  

Ese orden refleja mejor la estrategia del PRD y reduce el riesgo de construir un backlog vistoso pero no realmente operable.

