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

Nota: En el MVP esta funcionalidad se limita al detalle de una vacante.  
La vista centralizada de bloqueos se considera evolución posterior.

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
  "Como usuario interno, quiero ver mis acciones asignadas para saber qué tareas debo ejecutar"
- **Descripción:**  
  Permite a cada participante del proceso conocer sus responsabilidades pendientes.
- **Criterios de aceptación (BDD):**
  - **Dado que** soy responsable de acciones asignadas  
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
  - **Dado que** existe una entrevista asociada a una candidatura  
  **Cuando** registro feedback informando evaluación, comentarios y recomendación  
  **Entonces** el feedback queda registrado y asociado a la entrevista y a la candidatura

  - **Dado que** he informado evaluación, comentarios y recomendación con valores válidos  
  **Cuando** guardo el feedback  
  **Entonces** el sistema confirma que el feedback se ha guardado correctamente y queda disponible para su consulta

  - **Dado que** no he informado la recomendación (campo obligatorio)  
  **Cuando** intento enviar el feedback con evaluación y comentarios informados  
  **Entonces** el sistema muestra un error de validación indicando que la recomendación es obligatoria y no guarda el feedback
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
    **Entonces** el sistema consolida el feedback agrupado por criterio y muestra las evaluaciones de cada entrevistador
  - **Dado que** existen evaluaciones contradictorias
    **Cuando** genero el debrief  
    **Entonces** el sistema permite identificar discrepancias entre evaluadores
  - **Dado que** el feedback está incompleto  
    **Cuando** intento generar el debrief
    **Entonces** el sistema lo indica y no lo genera
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

Las vertical slices se han redefinido para reflejar flujos funcionales completos alineados con el modelo de dominio y los casos de uso del PRD.

---

## VS1 — Alineación de vacante

- **Historias:**
  - US-01 — Crear vacante
  - US-02 — Definir criterios
  - US-03 — Validar alineación
  - US-E — Resolver discrepancias de alineación

- **Flujo:**
  crear vacante → definir criterios → resolver discrepancias → validar alineación

- **Objetivo:**
  asegurar una base común recruiter–hiring manager antes de iniciar el proceso

---

## VS2 — Ejecución operativa (bloqueos)

- **Historias:**
  - US-04 — Crear bloqueo operativo
  - US-05 — Visualizar bloqueos
  - US-06 — Crear acción para bloqueo
  - US-07 — Visualizar acciones asignadas
  - US-08 — Resolver bloqueo

- **Flujo:**
  detectar problema → registrar bloqueo → asignar acción → ejecutar → resolver

- **Objetivo:**
  hacer visible y gestionable el avance del proceso mediante accountability operativa

---

## VS3 — Evaluación y decisión (end-to-end real)

- **Historias:**
  - US-A — Crear candidatura
  - US-B — Registrar o planificar entrevista
  - US-C — Asignar entrevistador
  - US-09 — Registrar feedback
  - US-D — Marcar candidatura lista para decisión
  - US-10 — Visualizar feedback
  - US-11 — Generar debrief
  - US-12 — Registrar decisión

- **Flujo:**
  crear candidatura → registrar entrevista → asignar entrevistador → registrar feedback → validar completitud → generar debrief → tomar decisión

- **Objetivo:**
  permitir un flujo completo de evaluación y decisión basado en evidencia

---

## Relación entre slices

- VS1 habilita VS2 y VS3 (vacante alineada)
- VS2 puede ejecutarse en paralelo a VS3 (bloqueos durante el proceso)
- VS3 representa el flujo completo de decisión del producto

---

## Nota

A diferencia de la versión inicial, VS3 incluye ahora las entidades clave del dominio (`Application`, `Interview`) necesarias para que el flujo sea ejecutable end-to-end.

---

# 4. Mapa de dependencias

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

# 5. Priorización MVP 

La priorización del MVP se ha ajustado teniendo en cuenta no solo valor de negocio y dependencias, sino la capacidad de ejecutar un flujo completo end-to-end según el modelo de dominio.

## Orden de prioridad

1. US-01
2. US-02
3. US-03
4. US-E — Resolver discrepancias de alineación
5. US-A — Crear candidatura
6. US-B — Registrar o planificar entrevista
7. US-C — Asignar entrevistador
8. US-04
9. US-06
10. US-08
11. US-09
12. US-D — Marcar candidatura lista para decisión
13. US-11
14. US-12
15. US-05
16. US-10
17. US-07


### MVP mínimo funcional (end-to-end real)

Incluye:

- US-01 — Crear vacante
- US-02 — Definir criterios
- US-03 — Validar alineación
- US-E — Resolver discrepancias de alineación

- US-A — Crear candidatura
- US-B — Registrar o planificar entrevista
- US-C — Asignar entrevistador

- US-04 — Crear bloqueo operativo
- US-06 — Crear acción para bloqueo
- US-08 — Resolver bloqueo

- US-09 — Registrar feedback
- US-D — Marcar candidatura lista para decisión
- US-11 — Generar debrief
- US-12 — Registrar decisión

### Flujo cubierto

vacante → alineación → candidatura → entrevista → feedback → debrief → decisión

### Qué valida este MVP

- alineación real recruiter–hiring manager
- existencia de flujo de evaluación real
- capacidad de capturar feedback estructurado
- capacidad de tomar una decisión trazable

---

### MVP ampliado

Añade:

- US-05 — Visualizar bloqueos
- US-10 — Visualizar feedback

### Qué aporta

- mejora de visibilidad operativa
- comparación de evaluaciones
- consolidación estructurada antes de decisión

---

# 6. Generación de backlog de producto con distintos prompts

Para generar el backlog del producto se han utilizado los prompts indicados en [Prompts usados](prompts_backlog-SVG.md)

Las conclusiones obtenidas tras analizar las respuestas de los distntos prompts han sido las siguientes:

Después de probar los distintos prompts para generar el backlog, me he dado cuenta de que cada uno aporta algo diferente, pero también tienen bastantes limitaciones, sobre todo si no se revisa bien el resultado.

El *primer prompt* me ha servido como punto de partida. Es fácil de entender y la priorización tiene sentido a nivel general porque sigue el flujo del producto (primero alineación, luego ejecución y finalmente decisión). El problema es que es demasiado simple: no tiene en cuenta esfuerzo, riesgo ni otros factores importantes. Es útil para empezar, pero no lo usaría para tomar decisiones reales.

El *segundo prompt* mejora bastante porque introduce criterios como valor, urgencia o complejidad. Aquí ya se empieza a ver un razonamiento más estructurado, pero aun así hay algo que no termina de convencerme: los números son un poco arbitrarios. Además, a veces coloca historias arriba que en realidad no se podrían implementar todavía por dependencias.

El *tercer prompt* es donde empiezo a ver un salto de calidad. Al usar el PRD, la priorización tiene más sentido desde el punto de vista del producto, no solo de las historias. Aquí ya no solo se ordena, sino que también se detectan problemas, como que faltan piezas importantes del flujo (por ejemplo, entrevistas o candidaturas). Me parece más útil porque conecta backlog con negocio.

El *cuarto prompt* (User Story Mapping) no prioriza como tal, pero me ha ayudado a entender el producto de forma global. Ver el flujo completo (inicio → ejecución → decisión) me ha permitido detectar que, aunque sobre el papel parece que todo encaja, en realidad faltan cosas importantes para que el sistema funcione de verdad.

El *quinto prompt* es el más completo, ya que es una mejora del tercero. Combina métricas, contexto del PRD y además hace una especie de revisión crítica del backlog. Creo que es el que más se parece a cómo se trabajaría en un entorno real, porque no solo prioriza, sino que también cuestiona si lo que se ha definido tiene sentido. Eso sí, también es el más complejo y requiere entender bien lo que está pasando para no aceptar el resultado sin más.

Viendo las respuestas de todos los prompts, parece que hay varios problemas que vienen de pasos anteriores:

* El flujo no es realmente end-to-end: faltan historias clave como la gestión de candidaturas o entrevistas, que sí aparecen en el PRD. Por ejemplo, el US-09 "Registrar feedback" requiere crear una entrevista o candidatura, y no hay una US para ello.
* Dependencias ocultas: algunas historias se priorizan como si fueran independientes, pero en realidad no lo son. Por ejemplo la US-12 "Registrar decisión" depende de US-11 "Generar debrief"
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


### 8.3 Pre-MVP dependencies

El backlog actual no cubre completamente el flujo end-to-end del proceso de selección definido en el PRD.

Existen dependencias funcionales previas que deben resolverse para que el bloque de evaluación y decisión (E3) sea realmente operable.

En particular, la historia US-09 “Registrar feedback” asume la existencia de entrevistas y candidaturas, que actualmente no están modeladas como User Stories.

A continuación se listan las historias necesarias como dependencias previas al MVP ampliado:

---

#### US-A — Crear candidatura

- **Historia:**  
  "Como recruiter, quiero crear una candidatura para una vacante para poder gestionar candidatos dentro del proceso"

- **Criterios de aceptación (BDD):**
  - **Dado que** existe una vacante  
    **Cuando** creo una candidatura asociada a un candidato  
    **Entonces** la candidatura queda registrada en el sistema
  - **Dado** que existe una candidatura  
    **Cuando** accedo a su detalle  
    **Entonces** puedo ver su estado dentro del proceso

- **Estimación:** M

---

#### US-B — Registrar o planificar entrevista

- **Historia:**  
  "Como recruiter, quiero registrar o planificar una entrevista para poder evaluar una candidatura"

- **Criterios de aceptación (BDD):**
  - **Dado** que existe una candidatura  
    **Cuando** registro una entrevista  
    **Entonces** queda asociada a la candidatura
  - **Dado** que existe una entrevista  
    **Cuando** accedo a su información  
    **Entonces** puedo ver su estado y fecha

- **Estimación:** M

---

#### US-C — Asignar entrevistador

- **Historia:**  
  "Como recruiter, quiero asignar un entrevistador a una entrevista para asegurar que la evaluación tiene un responsable"

- **Criterios de aceptación (BDD):**
  - **Dado** que existe una entrevista  
    **Cuando** asigno un entrevistador  
    **Entonces** queda registrado como responsable de la evaluación
  - **Dado** que una entrevista tiene entrevistador asignado  
    **Cuando** accedo a su detalle  
    **Entonces** puedo ver quién es el responsable

- **Estimación:** S

---

#### US-D — Marcar candidatura lista para decisión

- **Historia:**  
  "Como recruiter, quiero marcar una candidatura como lista para decisión para poder iniciar el proceso de cierre"

- **Criterios de aceptación (BDD):**
  - **Dado** que una candidatura tiene entrevistas completadas  
    **Cuando** la marco como lista para decisión  
    **Entonces** pasa a estado “lista para decisión”
  - **Dado** que faltan evaluaciones obligatorias  
    **Cuando** intento marcarla como lista  
    **Entonces** el sistema lo impide

- **Estimación:** S

#### US-E — Resolver discrepancias de alineación

- **Historia:**  
  "Como recruiter o hiring manager, quiero resolver discrepancias en la definición de la vacante para poder cerrar una alineación válida"

- **Criterios de aceptación (BDD):**
  - **Dado** que existen diferencias en criterios de la vacante  
    **Cuando** recruiter y hiring manager revisan la alineación  
    **Entonces** pueden modificar la información hasta alcanzar un acuerdo
  - **Dado** que existen discrepancias no resueltas  
    **Cuando** intento validar la vacante  
    **Entonces** el sistema no permite cerrar la alineación

- **Estimación:** M

---

### 8.4 Impacto en el MVP

- US-09 depende directamente de:
  - US-B (entrevista)
  - US-A (candidatura)

- El bloque E3 (feedback → debrief → decisión) no es ejecutable sin estas historias.

- Estas historias deben considerarse:
  - Pre-MVP funcional real
  - o parte de un “MVP técnico necesario”

### 8.5 Integración en el MVP

Estas historias no deben tratarse únicamente como dependencias teóricas, sino como parte del MVP funcional real.

Sin la inclusión de:

- US-A (candidatura)
- US-B (entrevista)
- US-C (asignación de entrevistador)
- US-D (lista para decisión)

el flujo de evaluación y decisión (E3) no es ejecutable end-to-end, ya que el modelo de dominio requiere explícitamente entidades como `Application`, `Interview` y `Feedback`.

---

### 8.6 Mapeo a arquitectura (bounded contexts y ownership)

A partir de las vertical slices y del modelo de dominio definido en el PRD, se define el siguiente mapeo a módulos del sistema para clarificar responsabilidades y ownership de lógica de negocio.

Las vertical slices definidas para el MVP representan flujos funcionales end-to-end, pero no deben confundirse con módulos o bounded contexts.

Una vertical slice puede atravesar varios módulos del sistema, mientras que cada bounded context mantiene responsabilidad clara sobre una parte del dominio, sus reglas de negocio y su consistencia interna.

## 8.6.1 Bounded contexts propuestos

### 1. Gestión de Vacantes y Alineación

**Responsabilidad**
Gestionar la vacante, su alineación recruiter–hiring manager y los criterios de evaluación asociados.

**Historias principalmente asociadas**
- US-01
- US-02
- US-03
- US-E

**Agregados principales**
- `Vacancy`
- `VacancyAlignment`

**Entidades relacionadas**
- `EvaluationCriterion`

**Invariantes principales**
- una vacante no puede considerarse alineada sin criterios definidos
- si se modifican criterios clave, la alineación vuelve a estado pendiente
- no puede cerrarse la alineación si existen discrepancias no resueltas

---

### 2. Orquestación del Proceso

**Responsabilidad**
Coordinar el estado operativo de vacantes y candidaturas, gestionar bloqueos y acciones, y validar si el proceso puede avanzar.

**Historias principalmente asociadas**
- US-04
- US-05
- US-06
- US-07
- US-08
- US-D

**Agregados principales**
- `ProcessBlocker`
- `ActionItem`

**Agregado operativo relevante**
- `Application` como estado de proceso

**Invariantes principales**
- un bloqueo debe estar asociado a una vacante
- una acción debe estar asociada a un bloqueo
- una candidatura no puede marcarse como lista para decisión si faltan evaluaciones obligatorias
- el proceso no debe avanzar si existen bloqueos críticos abiertos

---

### 3. Evaluación y Feedback

**Responsabilidad**
Gestionar entrevistas, asignación de entrevistadores y captura de feedback estructurado por criterio.

**Historias principalmente asociadas**
- US-B
- US-C
- US-09
- US-10

**Agregados principales**
- `Interview`
- `Feedback`

**Entidades relacionadas**
- `FeedbackCriterionAssessment`

**Invariantes principales**
- una entrevista pertenece a una candidatura
- una entrevista debe tener entrevistador asignado antes de completarse
- un feedback debe pertenecer a la entrevista y candidatura correctas
- una entrevista solo puede tener un feedback principal en el MVP

---

### 4. Gestión de Debrief y Decisión

**Responsabilidad**
Consolidar evidencia evaluativa, generar debrief y registrar la decisión final auditable.

**Historias principalmente asociadas**
- US-11
- US-12

**Agregado principal**
- `Debrief`

**Entidades relacionadas**
- `Application`
- `Feedback`

**Invariantes principales**
- no puede generarse debrief si el feedback requerido está incompleto
- una candidatura solo puede tener un debrief final en el MVP
- la decisión final debe quedar registrada con trazabilidad

---

## 8.6.2 Relación entre vertical slices y bounded contexts

### VS1 — Alineación de vacante
Se implementa principalmente dentro de:
- Gestión de Vacantes y Alineación

Dependencia posterior:
- habilita a Orquestación del Proceso para iniciar ejecución

---

### VS2 — Ejecución operativa (bloqueos)
Se implementa principalmente dentro de:
- Orquestación del Proceso

Dependencias:
- requiere vacante alineada desde Gestión de Vacantes y Alineación
- puede apoyarse en señales de Evaluación y Feedback cuando el bloqueo depende de entrevistas o feedback

---

### VS3 — Evaluación y decisión
Se implementa de forma transversal entre:
- Orquestación del Proceso
- Evaluación y Feedback
- Gestión de Debrief y Decisión

Distribución principal:
- creación de candidatura, estado global y readiness para decisión → Orquestación del Proceso
- entrevistas y feedback → Evaluación y Feedback
- consolidación y cierre → Gestión de Debrief y Decisión

---

## 8.6.3 Ownership funcional recomendado

Para evitar ambigüedad entre módulos, el ownership recomendado es el siguiente:

| Capacidad | Módulo owner |
|---|---|
| creación y alineación de vacante | Gestión de Vacantes y Alineación |
| criterios de evaluación | Gestión de Vacantes y Alineación |
| estado operativo de candidatura | Orquestación del Proceso |
| bloqueos y acciones | Orquestación del Proceso |
| planificación y asignación de entrevistas | Evaluación y Feedback |
| captura de feedback | Evaluación y Feedback |
| validación de completitud para cierre | Orquestación del Proceso |
| debrief consolidado | Gestión de Debrief y Decisión |
| decisión final auditable | Gestión de Debrief y Decisión |

### Regla de ownership sobre `Application` e `Interview`

Para evitar solapes entre módulos, se fija la siguiente regla:

- `Application` pertenece funcionalmente a **Orquestación del Proceso**, porque representa el estado global de una candidatura dentro del flujo.
- `Interview` pertenece funcionalmente a **Evaluación y Feedback**, porque representa la unidad operativa de evaluación sobre la que se captura feedback.

### Implicaciones

- **Orquestación del Proceso** es el módulo owner de:
  - `Application.current_stage`
  - `Application.status`
  - transición a “lista para decisión”
  - validación de avance del proceso

- **Evaluación y Feedback** es el módulo owner de:
  - planificación de entrevistas
  - asignación de entrevistadores
  - estado de entrevista
  - captura y validación de feedback

### Regla de coordinación

Evaluación y Feedback puede informar señales como:

- entrevista planificada
- entrevista completada
- feedback registrado
- feedback incompleto

Pero la decisión de avanzar el estado global de la candidatura sigue perteneciendo a **Orquestación del Proceso**.

---

## 8.6.4 Decisión de diseño importante

Las vertical slices se usan para planificar entregas funcionales completas.

Los bounded contexts se usan para separar responsabilidades del dominio y reducir acoplamiento interno.

Por tanto:

- una slice puede cruzar varios módulos
- un módulo puede participar en varias slices
- la consistencia fuerte debe mantenerse dentro del bounded context owner
- la coordinación entre contextos debe producirse mediante servicios de aplicación o flujos de orquestación, no mezclando reglas de negocio entre módulos

---

## 8.6.5 Conclusión

Esta separación permite que el MVP siga siendo un flujo funcional completo sin perder claridad arquitectónica.

También ayuda a evitar dos errores frecuentes:

- diseñar los módulos copiando directamente las épicas o slices
- repartir reglas de negocio entre varios contextos sin ownership claro


## 9. Recomendación final

### Release 1 (MVP funcional real)

- US-01
- US-02
- US-03
- US-E

- US-A
- US-B
- US-C

- US-04
- US-06
- US-08

- US-09
- US-D
- US-11
- US-12

### Release 2 (valor diferencial completo)

- US-05
- US-10

### Post-MVP

- US-07

### Nota

El MVP se ha redefinido para garantizar que el flujo completo del proceso de selección es ejecutable:

vacante → candidatura → entrevista → evaluación → decisión

Esto alinea el backlog con el modelo de dominio definido en el PRD y evita dependencias implícitas no implementadas.

---

## 10. Conclusión ejecutiva

La mejor secuencia para LTI no es empezar por “cerrar decisiones”, sino por asegurar:

1. alineación real de la vacante  
2. visibilidad y resolución de bloqueos  
3. evaluación estructurada  
4. decisión trazable  

Ese orden refleja mejor la estrategia del PRD y reduce el riesgo de construir un backlog vistoso pero no realmente operable.

Además, es importante destacar que un MVP basado únicamente en las User Stories iniciales no era realmente ejecutable, ya que faltaban piezas clave del dominio como candidatura e entrevista.

La incorporación de estas historias permite validar el producto en condiciones más cercanas a un uso real.

---

# 8. Seleccionar UserStory para generar Tickets de trabajo
Selecciono la US-04 - Crear bloqueo operativo, porque creo que no es demasiado simple como otras historias más básicas, pero tampoco depende de muchas cosas que todavía no están hechas. Además, parece bastante importante para el producto, ya que trata sobre gestionar bloqueos en el proceso.

También creo que permite dividir el trabajo en varias tareas claras, lo que viene bien para practicar cómo hacer tickets y estimarlos

# 9. Tickets de trabajo para US-04 - Crear bloqueo operativo

## Ticket 1 — Modelar la entidad de dominio `ProcessBlocker`

### Tipo

Feature

### Título

Crear entidad de dominio `ProcessBlocker`

### Descripción

Crear la entidad de dominio que representa un bloqueo operativo dentro del módulo de orquestación del proceso.

Debe incluir, como mínimo:

* `id`
* `vacancyId`
* `description`
* `responsibleUserId`
* `status`
* `detectedAt`

La creación debe dejar el bloqueo en estado inicial activo.
La lógica de validación básica debe vivir en dominio, no en controlador ni en persistencia.

### Criterios de aceptación

* Existe una entidad de dominio `ProcessBlocker`
* No permite crear un bloqueo sin descripción
* No permite crear un bloqueo sin responsable
* El estado inicial del bloqueo es `ACTIVE`
* La fecha de detección se asigna al crearlo

### Asignación

Backend

### Etiquetas

backend, domain, blocker

### Dependencias

Ninguna

### Notas técnicas

* Evitar anemizar la entidad
* Si el proyecto usa value objects, valorar encapsular `description` y `status`

---

## Ticket 2 — Definir contrato de repositorio para bloqueos

### Tipo

Tarea técnica

### Título

Definir interfaz de repositorio `ProcessBlockerRepository`

### Descripción

Crear el contrato del repositorio para persistir y consultar bloqueos operativos.

Debe cubrir al menos:

* guardar bloqueo
* buscar por id
* listar bloqueos activos por vacante

### Criterios de aceptación

* Existe una interfaz de repositorio para `ProcessBlocker`
* Permite persistir un bloqueo
* Permite recuperar bloqueos activos de una vacante

### Asignación

Backend

### Etiquetas

backend, repository, domain

### Dependencias

Ticket 1

### Notas técnicas

* Mantener la interfaz en capa de dominio o aplicación según la arquitectura del proyecto
* No acoplarla a JPA/ORM

---

## Ticket 3 — Implementar persistencia de `ProcessBlocker`

### Tipo

Tarea técnica

### Título

Implementar persistencia de bloqueos operativos

### Descripción

Implementar la capa de infraestructura para persistir `ProcessBlocker` en base de datos.

Incluir:

* tabla/colección de bloqueos
* mapping ORM si aplica
* índices mínimos para consulta por vacante y estado

### Criterios de aceptación

* Los bloqueos se guardan correctamente en base de datos
* Se pueden recuperar bloqueos activos por vacante
* La persistencia mantiene consistencia con el modelo de dominio

### Asignación

Backend

### Etiquetas

backend, persistence, database

### Dependencias

Ticket 2

### Notas técnicas

* Añadir índice por `vacancy_id` y posiblemente por `(vacancy_id, status)`
* El nombre de columnas/tabla debe reflejar bien el dominio

---

## Ticket 4 — Implementar caso de uso de creación de bloqueo

### Tipo

Feature

### Título

Implementar caso de uso `CreateProcessBlocker`

### Descripción

Crear el servicio/caso de uso de aplicación encargado de registrar un nuevo bloqueo operativo.

Debe:

* recibir `vacancyId`, `description`, `responsibleUserId`
* validar existencia de la vacante
* validar que la vacante está activa
* crear el bloqueo y persistirlo

### Criterios de aceptación

* Si la vacante existe y está activa, el bloqueo se crea correctamente
* Si la vacante no existe, el caso de uso devuelve error controlado
* Si la vacante no está activa, no permite crear el bloqueo
* Si falta responsable, no permite crear el bloqueo

### Asignación

Backend

### Etiquetas

backend, application, use-case

### Dependencias

Ticket 1, Ticket 3

### Notas técnicas

* La validación “vacante activa” es importante porque la User Story lo dice explícitamente
* No meter aquí lógica de formato HTTP

---

## Ticket 5 — Validar reglas de negocio sobre responsable

### Tipo

Feature

### Título

Validar responsable del bloqueo en creación

### Descripción

Añadir validaciones de negocio sobre el usuario responsable asignado al bloqueo.

Validaciones mínimas:

* el responsable existe
* pertenece a la organización de la vacante
* puede ser asignado dentro del contexto del proceso

### Criterios de aceptación

* No permite crear bloqueo con un usuario inexistente
* No permite asignar responsable de otra organización
* El error devuelto indica claramente la causa

### Asignación

Backend

### Etiquetas

backend, validation, business-rules

### Dependencias

Ticket 4

### Notas técnicas

* Este ticket evita inconsistencias de dominio bastante comunes
* Si el sistema aún no tiene organizaciones o permisos operativos completos, dejar la validación preparada al menos a nivel de organización

---

## Ticket 6 — Exponer endpoint para crear bloqueo operativo

### Tipo

Feature

### Título

Crear endpoint de API para registrar bloqueo operativo

### Descripción

Exponer un endpoint que permita crear un bloqueo asociado a una vacante.

Debe:

* recibir request con `description` y `responsibleUserId`
* invocar el caso de uso
* devolver respuesta con los datos mínimos del bloqueo creado

### Criterios de aceptación

* Existe un endpoint para registrar bloqueos
* Devuelve éxito cuando el bloqueo se crea correctamente
* Devuelve error de validación cuando falta responsable o descripción
* Devuelve error cuando la vacante no existe o no está activa

### Asignación

Backend

### Etiquetas

backend, api, rest

### Dependencias

Ticket 4, Ticket 5

### Notas técnicas

* Mantener DTOs separados del modelo de dominio
* No exponer directamente la entidad interna

---

## Ticket 7 — Implementar validación de request en capa API

### Tipo

Tarea técnica

### Título

Validar request de creación de bloqueo en entrada API

### Descripción

Añadir validaciones de entrada al endpoint para evitar enviar requests inválidas al caso de uso.

Validaciones mínimas:

* `description` obligatorio
* `responsibleUserId` obligatorio
* formato de campos correcto

### Criterios de aceptación

* Requests inválidas fallan antes de llegar a lógica de negocio
* Los errores de validación son legibles para frontend
* Los campos obligatorios quedan documentados

### Asignación

Backend

### Etiquetas

backend, api, validation

### Dependencias

Ticket 6

### Notas técnicas

* Esta validación no sustituye la validación de dominio
* Mantener ambos niveles

---

## Ticket 8 — Añadir formulario de creación de bloqueo en detalle de vacante

### Tipo

Feature

### Título

Implementar formulario de alta de bloqueo en la vista de vacante

### Descripción

Añadir en la pantalla de detalle de vacante una UI que permita registrar un nuevo bloqueo operativo.

Debe incluir:

* campo descripción
* selector de responsable
* acción guardar

### Criterios de aceptación

* Desde la vista de vacante se puede abrir el formulario de creación
* Se puede informar descripción y responsable
* No permite enviar el formulario sin responsable
* No permite enviar el formulario sin descripción

### Asignación

Frontend

### Etiquetas

frontend, form, vacancy-detail

### Dependencias

Ticket 6, Ticket 7

### Notas técnicas

* La UX debe dejar claro que se trata de un bloqueo operativo
* El selector de responsable debe usar usuarios válidos del contexto

---

## Ticket 9 — Integrar el envío del formulario con la API

### Tipo

Feature

### Título

Conectar formulario de bloqueo con API de creación

### Descripción

Conectar la UI con el endpoint backend para registrar el bloqueo y gestionar estados de carga, éxito y error.

### Criterios de aceptación

* Al guardar, la UI invoca la API correctamente
* Muestra estado de carga mientras se envía
* Muestra error funcional si la creación falla
* Tras crear correctamente, el formulario se limpia o se cierra según diseño

### Asignación

Frontend

### Etiquetas

frontend, integration, api

### Dependencias

Ticket 8

### Notas técnicas

* Evitar duplicados por doble submit
* Gestionar bien errores 4xx de validación

---

## Ticket 10 — Mostrar bloqueos activos en el detalle de vacante

### Tipo

Feature

### Título

Mostrar listado de bloqueos activos en la vista de vacante

### Descripción

Añadir en la vista de detalle de vacante el listado de bloqueos activos asociados.

Cada ítem debe mostrar al menos:

* descripción
* responsable
* estado

### Criterios de aceptación

* Si la vacante tiene bloqueos activos, se muestran en pantalla
* Si no tiene bloqueos activos, se muestra estado vacío
* El bloqueo recién creado aparece en el listado

### Asignación

Frontend

### Etiquetas

frontend, ui, blockers

### Dependencias

Ticket 9

### Notas técnicas

* Si ya existe query/backend para devolver bloqueos al cargar la vacante, reutilizarla
* Si no existe, habrá que añadir soporte backend específico

---

## Ticket 11 — Exponer consulta de bloqueos activos por vacante

### Tipo

Feature

### Título

Implementar consulta de bloqueos activos para detalle de vacante

### Descripción

Implementar en backend la query necesaria para recuperar bloqueos activos de una vacante y soportar su visualización en frontend.

### Criterios de aceptación

* La API devuelve los bloqueos activos de una vacante
* No devuelve bloqueos resueltos
* Si no existen bloqueos, devuelve lista vacía

### Asignación

Backend

### Etiquetas

backend, query, api

### Dependencias

Ticket 3

### Notas técnicas

* Este ticket puede estar ya resuelto parcialmente si el detalle de vacante ya carga agregados relacionados
* Si existe endpoint de detalle extensible, valorar incluirlo ahí en lugar de crear uno nuevo

---

## Ticket 12 — Tests de dominio y aplicación para creación de bloqueo

### Tipo

Tarea técnica

### Título

Cubrir con tests la creación de bloqueo operativo

### Descripción

Añadir tests automáticos de dominio y de caso de uso para la creación de bloqueos.

Cubrir al menos:

* creación válida
* bloqueo sin responsable
* bloqueo sin descripción
* vacante no activa
* vacante inexistente

### Criterios de aceptación

* Existen tests automáticos para reglas principales
* Las validaciones críticas quedan cubiertas
* Los tests fallan si se rompe la regla de negocio

### Asignación

Backend

### Etiquetas

test, backend, domain

### Dependencias

Ticket 4, Ticket 5

### Notas técnicas

* Priorizar tests de comportamiento sobre tests acoplados a implementación

---

## Ticket 13 — Tests de integración API para alta de bloqueo

### Tipo

Tarea técnica

### Título

Añadir tests de integración del endpoint de creación de bloqueo

### Descripción

Crear tests de integración para asegurar que el endpoint funciona correctamente extremo a extremo dentro del backend.

### Criterios de aceptación

* Existe test de creación satisfactoria
* Existe test cuando falta responsable
* Existe test cuando la vacante no existe
* Existe test cuando la vacante no está activa

### Asignación

Backend

### Etiquetas

test, api, integration

### Dependencias

Ticket 6, Ticket 7

---

## Ticket 14 — Validar flujo en frontend con pruebas funcionales/manuales

### Tipo

Tarea técnica

### Título

Validar flujo de alta y visualización de bloqueo en frontend

### Descripción

Verificar que el flujo completo funciona desde la UI:

* crear bloqueo
* ver error si faltan datos
* ver bloqueo en listado

### Criterios de aceptación

* El formulario no permite guardar sin responsable
* El formulario no permite guardar sin descripción
* Un bloqueo creado aparece en el detalle de vacante
* El flujo es usable sin refresco manual si así se espera en la pantalla

### Asignación

QA

### Etiquetas

qa, frontend, functional-test

### Dependencias

Ticket 10, Ticket 11

---

## Orden lógico de implementación

1. Ticket 1
2. Ticket 2
3. Ticket 3
4. Ticket 4
5. Ticket 5
6. Ticket 6
7. Ticket 7
8. Ticket 11
9. Ticket 8
10. Ticket 9
11. Ticket 10
12. Ticket 12
13. Ticket 13
14. Ticket 14

---


# 10. Estimación de tickets — US-04 Crear bloqueo operativo

## Criterio usado

Estimación individual usando:

- **Unidad**: Story Points
- **Escala**: Fibonacci (`1, 2, 3, 5, 8`)

### Referencia usada

- **1 punto**: cambio muy pequeño y acotado
- **2 puntos**: tarea simple, con poco riesgo
- **3 puntos**: tarea clara pero con algo de lógica o integración
- **5 puntos**: tarea con varias piezas, validaciones o más incertidumbre
- **8 puntos**: tarea grande o con demasiada incertidumbre

---

## Estimación por ticket

### Ticket 1 — Crear entidad de dominio `ProcessBlocker`
- **Estimación**: **3 SP**
- **Motivo**: No es solo crear una clase. Hay que modelar bien la entidad, definir invariantes básicas y dejar clara la responsabilidad del dominio.

### Ticket 2 — Definir interfaz de repositorio `ProcessBlockerRepository`
- **Estimación**: **1 SP**
- **Motivo**: Es una tarea pequeña y bastante directa. Principalmente consiste en definir el contrato correcto sin acoplarlo a infraestructura.

### Ticket 3 — Implementar persistencia de bloqueos operativos
- **Estimación**: **3 SP**
- **Motivo**: Hay trabajo de mapping, estructura de base de datos e implementación del repositorio. No parece complejo, pero ya implica infraestructura real.

### Ticket 4 — Implementar caso de uso `CreateProcessBlocker`
- **Estimación**: **5 SP**
- **Motivo**: Aquí ya aparece la lógica principal de aplicación: validar vacante, comprobar estado, crear entidad y persistir. Tiene más peso funcional que los tickets anteriores.

### Ticket 5 — Validar responsable del bloqueo en creación
- **Estimación**: **3 SP**
- **Motivo**: Aunque parece pequeño, introduce reglas de negocio importantes y posibles consultas adicionales. Tiene algo más de complejidad que una validación puramente sintáctica.

### Ticket 6 — Crear endpoint de API para registrar bloqueo operativo
- **Estimación**: **2 SP**
- **Motivo**: Es un endpoint relativamente estándar. Tiene integración con el caso de uso, manejo de request/response y errores, pero sin demasiada complejidad propia.

### Ticket 7 — Validar request de creación de bloqueo en entrada API
- **Estimación**: **1 SP**
- **Motivo**: Es una validación de entrada sencilla y bastante mecánica. Tiene poco riesgo técnico.

### Ticket 8 — Implementar formulario de alta de bloqueo en la vista de vacante
- **Estimación**: **3 SP**
- **Motivo**: Hay trabajo de UI, validaciones básicas y selección de responsable. No parece difícil, pero ya requiere algo más que una pantalla estática.

### Ticket 9 — Conectar formulario de bloqueo con API de creación
- **Estimación**: **2 SP**
- **Motivo**: Es una integración frontend-backend bastante acotada. Tiene gestión de carga, éxito y error, pero el flujo es claro.

### Ticket 10 — Mostrar listado de bloqueos activos en la vista de vacante
- **Estimación**: **3 SP**
- **Motivo**: Hay que pintar listado, gestionar estado vacío y refrescar correctamente tras creación. No es complejo, pero sí tiene varias pequeñas piezas.

### Ticket 11 — Implementar consulta de bloqueos activos para detalle de vacante
- **Estimación**: **2 SP**
- **Motivo**: La query parece bastante directa. Tiene algo de trabajo de backend y API, pero menos incertidumbre que el caso de uso de creación.

### Ticket 12 — Cubrir con tests la creación de bloqueo operativo
- **Estimación**: **3 SP**
- **Motivo**: Hay varios casos de negocio que conviene cubrir y no es solo un happy path. Requiere preparar bien escenarios y validar reglas importantes.

### Ticket 13 — Añadir tests de integración del endpoint de creación de bloqueo
- **Estimación**: **2 SP**
- **Motivo**: Son tests bastante definidos y previsibles. Tienen trabajo técnico, pero el alcance está bastante controlado.

### Ticket 14 — Validar flujo de alta y visualización de bloqueo en frontend
- **Estimación**: **2 SP**
- **Motivo**: Es una validación funcional bastante concreta. Tiene cierto trabajo de ejecución y revisión, pero el flujo a comprobar es pequeño.

---

## Resumen rápido

| Ticket | Título | Estimación |
|---|---|---:|
| 1 | Crear entidad de dominio `ProcessBlocker` | 3 SP |
| 2 | Definir interfaz de repositorio `ProcessBlockerRepository` | 1 SP |
| 3 | Implementar persistencia de bloqueos operativos | 3 SP |
| 4 | Implementar caso de uso `CreateProcessBlocker` | 5 SP |
| 5 | Validar responsable del bloqueo en creación | 3 SP |
| 6 | Crear endpoint de API para registrar bloqueo operativo | 2 SP |
| 7 | Validar request de creación de bloqueo en entrada API | 1 SP |
| 8 | Implementar formulario de alta de bloqueo en la vista de vacante | 3 SP |
| 9 | Conectar formulario de bloqueo con API de creación | 2 SP |
| 10 | Mostrar listado de bloqueos activos en la vista de vacante | 3 SP |
| 11 | Implementar consulta de bloqueos activos para detalle de vacante | 2 SP |
| 12 | Cubrir con tests la creación de bloqueo operativo | 3 SP |
| 13 | Añadir tests de integración del endpoint de creación de bloqueo | 2 SP |
| 14 | Validar flujo de alta y visualización de bloqueo en frontend | 2 SP |

---
