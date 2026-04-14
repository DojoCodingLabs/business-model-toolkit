# Scorecard de Validación de Hipótesis — [Proyecto]

> Basado en los **4 criterios de hipótesis validada** de *Lean Customer Development*
> (Cindy Alvarez, O'Reilly 2014), cap. 6.
>
> Una hipótesis NO está validada solo porque el entrevistado "dijo que sí". Para contar
> como validación real, los 4 criterios deben cumplirse simultáneamente con evidencia citable.

---

## Hipótesis a testear

**Hipótesis principal**:

> `[Copiar la hipótesis refinada de 02a-lluvia-supuestos.md, formato: "Creemos que [tipo de persona] experimenta [tipo de problema] cuando [situación/tarea] debido a [limitación/contexto]."]`

**Fuente de las entrevistas**: `./business/01-problema-hipotesis/entrevistas/`
**Fecha de evaluación**: `YYYY-MM-DD`
**Entrevistas evaluadas**: `N entrevistas (entrevista-01 a entrevista-NN)`

---

## Los 4 criterios (debe cumplirse los 4)

### Criterio 1: Problema real confirmado

> *"El cliente confirma que SÍ hay un problema/dolor real en su vida o trabajo."*

Señal de que se cumple:
- El entrevistado usa lenguaje emocional ("me frustra", "me vuelve loco/a", "es un dolor de cabeza")
- Describe situaciones específicas en tiempo presente, no hipotético
- Menciona consecuencias concretas (tiempo perdido, dinero gastado, relaciones afectadas)

Anti-señal:
- Lenguaje tibio ("sí, a veces", "bueno, podría mejorar")
- Solo conceptos abstractos sin ejemplos
- El entrevistado cambia de tema rápidamente

### Criterio 2: El problema debe resolverse

> *"El cliente cree que el problema PUEDE y DEBE resolverse."*

Señal:
- El entrevistado expresa que debería existir solución (aunque no sepa cuál)
- Ha imaginado cómo sería su vida sin el problema
- Reconoce que el statu quo no es aceptable a largo plazo

Anti-señal:
- "Así es la vida / así es en nuestra industria"
- "Ya nos acostumbramos, no hay vuelta"
- "Resolverlo sería imposible, mejor ni intentar"

### Criterio 3: Ya ha invertido intentando resolverlo

> *"El cliente ha INVERTIDO (tiempo/dinero/esfuerzo/aprendizaje) intentando resolver el problema."*

**Este es el criterio más importante** — la inversión previa es la señal más fuerte de dolor real.

Señal:
- Probó alternativas concretas (mencionar cuáles)
- Compró herramientas aunque no resolvían del todo
- Aprendió algo nuevo (curso, tutorial, proceso manual)
- Construyó un workaround propio

Anti-señal:
- "Lo he pensado pero nunca hice nada"
- "Sigo postponiendo investigar opciones"
- "Espero a que alguien lo resuelva por mí"

### Criterio 4: No hay bloqueo externo insuperable

> *"El cliente NO tiene circunstancias fuera de su control que le impidan probar una solución."*

Señal:
- Tiene autonomía para probar nuevas soluciones
- Tiene presupuesto o puede conseguirlo
- Puede tomar la decisión sin cadenas de aprobación de 6 niveles

Anti-señal:
- "Mi jefe/esposa/regulación no lo permite"
- "No tengo presupuesto y nunca lo voy a tener"
- "Depende de que [tercero] haga algo primero"

---

## Evaluación por entrevista

> Llenar una fila por cada entrevista (entrevista-01 en adelante).

| # | Entrevista | C1 Problema real | C2 Debe resolverse | C3 Ya invirtió | C4 No hay bloqueo | Evidencia clave | ¿Earlyvangelist? |
|---|---|---|---|---|---|---|---|
| 01 | `[nombre]` | 🟢/🟡/🔴 | 🟢/🟡/🔴 | 🟢/🟡/🔴 | 🟢/🟡/🔴 | `[cita breve]` | Sí / No |
| 02 | `[nombre]` | | | | | | |
| 03 | `[nombre]` | | | | | | |
| ... | | | | | | | |

**Leyenda**:
- 🟢 = Criterio cumplido claramente (con evidencia citable)
- 🟡 = Parcialmente / ambiguo (revisar notas para confirmar)
- 🔴 = No se cumple

---

## Agregado cross-entrevistas

> Contar cuántas entrevistas cumplen cada criterio (solo 🟢; los 🟡 no cuentan).

| Criterio | Total 🟢 | Porcentaje sobre N | Umbral para validación |
|---|---|---|---|
| C1. Problema real | __ / __ | __% | ≥70% |
| C2. Debe resolverse | __ / __ | __% | ≥70% |
| C3. Ya invirtió | __ / __ | __% | ≥70% (**crítico**) |
| C4. No hay bloqueo | __ / __ | __% | ≥70% |

---

## Veredicto

- [ ] **VALIDADA** — los 4 criterios se cumplen en ≥70% de entrevistas.
      **Siguiente paso**: avanzar a Fase 6 (BMC) con esta hipótesis como base.

- [ ] **PARCIALMENTE VALIDADA** — algunos criterios se cumplen pero no todos.
      **Siguiente paso**: refinar la hipótesis especificando mejor el segmento o el contexto.
      No avanzar hasta re-validar.

- [ ] **INVALIDADA** — al menos uno de los criterios falla sistemáticamente (<40% de entrevistas).
      **Siguiente paso**: **pivot**. Volver a `02a-lluvia-supuestos.md`, revisar qué supuestos
      del cuadrante B (alto riesgo + desconocido) fueron los que fallaron, y reformular
      la hipótesis. No construir el producto mientras esto no se resuelva.

- [ ] **INDETERMINADA** — muestra insuficiente (<5 entrevistas con respuestas completas).
      **Siguiente paso**: realizar más entrevistas antes de concluir.

---

## Análisis específico del Criterio 3 (el más crítico)

> El criterio 3 es el que más distingue entrevistados reales de entrevistados corteses.
> Profundizar en la evidencia de inversión previa.

### Earlyvangelists identificados

> Entrevistados que cumplen los 4 criterios + mostraron inversión sustancial. Son los candidatos
> ideales para la Entrevista de Solución (Fase 7) y el MVP (Fase 8).

| # | Nombre | Tipo de inversión previa | Nivel estimado de pain | Contacto |
|---|---|---|---|---|
| 1 | `[nombre]` | `[ej. "compró 3 herramientas distintas en últimos 6 meses"]` | 🔴 Alto | `[email/telegram]` |
| 2 | `[nombre]` | | | |
| 3 | `[nombre]` | | | |

---

## Ajustes a la hipótesis (si aplica)

> Si el veredicto fue PARCIAL o INVALIDADA, documentar el refinamiento aquí.

**Hipótesis original**: `[...]`

**Hipótesis refinada** (basada en hallazgos):

> `[Nueva formulación — puede cambiar el segmento de persona, el tipo de problema, el contexto,
> o agregar restricciones específicas que observaste]`

**Qué cambió y por qué**:

```
[Explicar qué supuesto falló y qué evidencia llevó al refinamiento]
```

**Siguiente iteración**:

- Entrevistas adicionales a realizar: `[N]`
- Segmento a enfocar: `[cambio si aplica]`
- Re-evaluar este scorecard después de: `[fecha/cantidad]`
