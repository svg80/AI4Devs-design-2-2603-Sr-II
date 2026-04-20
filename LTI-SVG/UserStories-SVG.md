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

### INVEST (mejorado)
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