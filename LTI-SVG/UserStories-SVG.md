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

---

## US-01

* **Épica:** E1

* **Título:** Crear vacante en estado pendiente de alineación

* **Historia:**
  "Como recruiter, quiero crear una vacante con información básica para poder iniciar el proceso de alineación con el hiring manager"

* **Descripción:**
  El recruiter necesita iniciar el proceso sin fricción, dejando creada la vacante aunque aún no esté alineada.

* **Criterios de aceptación (BDD):**

  * Dado que soy recruiter
    Cuando creo una vacante con título y hiring manager
    Entonces la vacante queda en estado "pendiente de alineación"
  * Dado que la vacante está pendiente
    Cuando accedo a ella
    Entonces veo que requiere completar la alineación
  * Dado que falta información mínima
    Cuando intento crear la vacante
    Entonces el sistema me obliga a completar los campos obligatorios

* **Estimación:** S

* **Tipo:** Core

### INVEST

* Independent: Sí — No depende de otras funcionalidades
* Negotiable: Sí — Campos pueden variar
* Valuable: Sí — Permite iniciar flujo
* Estimable: Sí — Alcance claro
* Small: Sí
* Testable: Sí — Estados verificables

---

## US-02

* **Épica:** E1

* **Título:** Definir criterios de la vacante

* **Historia:**
  "Como recruiter, quiero definir criterios y requisitos de la vacante para alinearlos con el hiring manager"

* **Descripción:**
  Permite estructurar el perfil antes de validarlo, base del resto del proceso.

* **Criterios de aceptación:**

  * Dado que tengo una vacante
    Cuando edito la alineación
    Entonces puedo definir objetivo y requisitos
  * Dado que existen criterios definidos
    Cuando guardo
    Entonces quedan asociados a la vacante
  * Dado que no he completado campos obligatorios
    Cuando intento continuar
    Entonces el sistema me lo impide

* **Estimación:** M

* **Tipo:** Core

### INVEST

* Independent: Parcial — depende de US-01 (vacante)
* Negotiable: Sí
* Valuable: Sí — base del modelo de evaluación
* Estimable: Sí
* Small: Sí
* Testable: Sí

---

## US-03

* **Épica:** E1

* **Título:** Validar alineación por hiring manager

* **Historia:**
  "Como hiring manager, quiero validar la definición de la vacante para asegurar que cumple mis expectativas"

* **Descripción:**
  Cierra el proceso de alineación y habilita la ejecución.

* **Criterios de aceptación:**

  * Dado que hay una alineación definida
    Cuando el hiring manager accede
    Entonces puede revisarla
  * Dado que la revisa
    Cuando la valida
    Entonces la vacante pasa a "alineada"
  * Dado que hay cambios posteriores
    Cuando se modifican criterios clave
    Entonces la alineación se reabre

* **Estimación:** M

* **Tipo:** Core

### INVEST

* Independent: Parcial — depende de US-02
* Negotiable: Sí
* Valuable: Sí — desbloquea ejecución
* Estimable: Sí
* Small: Sí
* Testable: Sí

---

## US-04

* **Épica:** E2

* **Título:** Visualizar bloqueos activos de una vacante

* **Historia:**
  "Como recruiter, quiero ver los bloqueos activos de una vacante para entender por qué no avanza"

* **Descripción:**
  Introduce visibilidad operativa (core del producto).

* **Criterios de aceptación:**

  * Dado que existen bloqueos
    Cuando accedo a la vacante
    Entonces veo listado de bloqueos
  * Dado un bloqueo
    Cuando lo visualizo
    Entonces veo responsable y causa
  * Dado que no hay bloqueos
    Cuando accedo
    Entonces se indica claramente

* **Estimación:** M

* **Tipo:** Core

### INVEST

* Independent: Sí
* Negotiable: Sí
* Valuable: Muy alta — insight clave
* Estimable: Sí
* Small: Sí
* Testable: Sí

---

## US-05

* **Épica:** E2

* **Título:** Crear acción para resolver bloqueo

* **Historia:**
  "Como recruiter, quiero asignar una acción a un responsable para resolver un bloqueo"

* **Descripción:**
  Introduce accountability operativa.

* **Criterios de aceptación:**

  * Dado un bloqueo
    Cuando creo una acción
    Entonces se asigna a un usuario
  * Dado una acción asignada
    Cuando el usuario accede
    Entonces ve la tarea pendiente
  * Dado que se completa
    Cuando se marca como hecha
    Entonces el sistema actualiza el estado

* **Estimación:** M

* **Tipo:** Core

### INVEST

* Independent: Parcial — depende de US-04
* Negotiable: Sí
* Valuable: Muy alta — ejecución real
* Estimable: Sí
* Small: Sí
* Testable: Sí

---

## US-06

* **Épica:** E2

* **Título:** Marcar bloqueo como resuelto

* **Historia:**
  "Como recruiter, quiero marcar un bloqueo como resuelto para reflejar que el proceso puede avanzar"

* **Descripción:**
  Cierra el loop de ejecución.

* **Criterios de aceptación:**

  * Dado un bloqueo con acciones
    Cuando se completan
    Entonces puedo marcarlo como resuelto
  * Dado un bloqueo resuelto
    Cuando accedo
    Entonces no aparece como activo
  * Dado un bloqueo mal resuelto
    Cuando reaparece el problema
    Entonces puede reabrirse

* **Estimación:** S

* **Tipo:** Core

### INVEST

* Independent: Parcial — depende de US-05
* Negotiable: Sí
* Valuable: Sí
* Estimable: Sí
* Small: Sí
* Testable: Sí

---

## US-07

* **Épica:** E3

* **Título:** Generar debrief básico de candidatura

* **Historia:**
  "Como recruiter, quiero ver un resumen del feedback de un candidato para facilitar la decisión final"

* **Descripción:**
  MVP sin IA compleja: consolidación básica.

* **Criterios de aceptación:**

  * Dado que hay feedback
    Cuando accedo al candidato
    Entonces veo un resumen consolidado
  * Dado feedback incompleto
    Cuando intento generar debrief
    Entonces el sistema lo indica
  * Dado que existe debrief
    Cuando lo visualizo
    Entonces puedo revisarlo con el manager

* **Estimación:** M

* **Tipo:** Core

### INVEST

* Independent: Parcial — requiere feedback previo (no modelado aquí)
* Negotiable: Sí
* Valuable: Muy alta — decisión
* Estimable: Sí
* Small: Sí
* Testable: Sí

---

## US-08

* **Épica:** E3

* **Título:** Registrar decisión final

* **Historia:**
  "Como hiring manager, quiero registrar una decisión final para cerrar la candidatura"

* **Descripción:**
  Cierre auditable del proceso.

* **Criterios de aceptación:**

  * Dado un debrief
    Cuando el manager decide
    Entonces puede registrar decisión
  * Dado decisión registrada
    Cuando accedo
    Entonces queda guardada
  * Dado una candidatura cerrada
    Cuando la consulto
    Entonces veo trazabilidad

* **Estimación:** S

* **Tipo:** Core

### INVEST

* Independent: Parcial — depende de US-07
* Negotiable: Sí
* Valuable: Crítica — cierre
* Estimable: Sí
* Small: Sí
* Testable: Sí

---

# 3. Vertical Slices (MVP)

---

## VS1 — Alineación completa de vacante

* **Historias:** US-01, US-02, US-03
* **Valor:** Evitar desalineación inicial
* **Flujo:** Crear vacante → definir criterios → validar

---

## VS2 — Gestión básica de bloqueos

* **Historias:** US-04, US-05, US-06
* **Valor:** Reducir fricción operativa
* **Flujo:** detectar → asignar acción → resolver

---

## VS3 — Decisión final simple

* **Historias:** US-07, US-08
* **Valor:** Validar toma de decisiones estructurada
* **Flujo:** consolidar feedback → decidir

---

# 4. Mapa de dependencias

### Dependencias clave

* US-02 → US-01
* US-03 → US-02
* US-05 → US-04
* US-06 → US-05
* US-07 → (feedback existente, externo al MVP)
* US-08 → US-07

### Cuellos de botella

* **Alineación completa (US-03)** bloquea todo el proceso
* **Debrief (US-07)** depende de input externo (riesgo real)

### Oportunidades de desacoplamiento

* Permitir US-04 sin depender de detección automática (crear manualmente bloqueos)
* Simplificar US-07 (no IA, solo agregación básica)

---

# 5. Priorización MVP

## Orden recomendado

1. US-01
2. US-02
3. US-03
4. US-04
5. US-05
6. US-06
7. US-07
8. US-08

---

## Justificación

### 1. Core inicial (US-01 a US-03)

* Desbloquean el **inicio del proceso**
* Validan hipótesis clave: alineación reduce problemas

### 2. Core operativo (US-04 a US-06)

* Entregan el **diferencial real del producto**
* Reducen riesgo: ¿los usuarios actúan sobre bloqueos?

### 3. Core de decisión (US-07, US-08)

* Validan el **valor final**
* Riesgo alto (depende de datos reales)

---

