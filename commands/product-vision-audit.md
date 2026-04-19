---
description: "Gap analysis de un modulo de producto vs. su vision estrategica PIBER + IDCF. Audita codebase contra Design Theses, Capabilities y Features declarados en el spike de vision."
argument-hint: "<spike-id | path/to/spike.md> <path/to/codebase> [--scope <subdir>] [--out <path>]"
---

# /product-vision-audit -- Gap Analysis PIBER + IDCF

Ejecuta una auditoria estructurada que compara la **vision estrategica** de un producto (expresada en los frameworks PIBER + IDCF) contra la **realidad implementada** en un codebase.

## Frameworks base

- **PIBER**: Problem / Insight / Big Idea / Execution / Results -- narrativa externa (VCs, media, hires).
- **IDCF**: Insight / Design Theses / Capabilities / Features -- constitucion interna de producto (product, eng, org).

El audit se concentra en **IDCF** para el gap analysis tecnico, y usa **PIBER** como contexto narrativo para validar alineacion estrategica.

## Modo de invocacion

```bash
/business-model-toolkit:product-vision-audit DOJ-3222 ./dojo-os
/business-model-toolkit:product-vision-audit ./vision-pathways.md ./dojo-os --scope src/app/pathways
/business-model-toolkit:product-vision-audit DOJ-3229 ./dojo-agent-openclaw-plugin --out ~/Escritorio/audit-doji.md
```

## Parsing de argumentos

1. **Primer argumento** (`<spike>`):
   - Si matchea patron `[A-Z]+-\d+` -> es un Linear issue ID, usar `mcp__linear-server__get_issue` para obtenerlo.
   - Si es un path a archivo `.md` existente -> leer con Read.
   - Si es URL de Linear (https://linear.app/.../issue/XXX-NNN/...) -> extraer ID y usar MCP.

2. **Segundo argumento** (`<codebase-path>`):
   - Path absoluto o relativo al repo/modulo a auditar.
   - Validar que existe con Bash `ls` antes de proceder.

3. **Flags opcionales**:
   - `--scope <subdir>`: restringe la auditoria a un subdirectorio dentro del codebase (ej: `src/app/pathways`).
   - `--out <path>`: ruta de salida del report. Default: `./business/vision-audit-{module}-{YYYY-MM-DD}.md`. Si el path empieza con `~/Escritorio/`, expandir a `/home/{user}/Escritorio/`.

## Flujo del comando

Delega a la skill `product-vision-audit`. La skill se encarga de:

1. **Extraccion**: parsear el spike, aislar Design Theses (musts), Capabilities table, Features tiers.
2. **Dog-fooding opcional**: si el codebase tiene `CLAUDE.md`, leerlo para entender el stack y convenciones.
3. **Auditoria por dimension**:
   - Design Theses -> busqueda de evidencia afirmativa o refutatoria en el codigo.
   - Capabilities -> verificar existencia de archivos/rutas/endpoints/tablas por capability.
   - Features (P0/P1/P2/P3) -> chequear si cada feature tiene implementacion visible.
   - Anti-patterns -> buscar patrones prohibidos explicitos en el spike.
   - North Star metric -> verificar si hay instrumentacion (telemetry, analytics, DB) que la mida.
4. **Scoring**: cada dimension recibe `OK / PARTIAL / MISSING / DRIFT`.
5. **Recommendations**: ranking de gaps por impacto estrategico (no por effort).

## Regla de idioma

Report en **espanol**. Quotes del spike y nombres propios (PIBER, IDCF, North Star) quedan en original.

## Regla de evidencia

**Toda afirmacion en el report debe apuntar a evidencia concreta**:
- Path del archivo + numero de linea cuando aplica.
- Ausencia documentada con comando de busqueda ejecutado (`Grep pattern=X path=Y -> no matches`).
- Nunca afirmar "no esta implementado" sin haber buscado. Nunca afirmar "esta implementado" sin haber visto el codigo.

## Output del report

Default: `./business/vision-audit-{module}-{YYYY-MM-DD}.md`

Estructura del report (ver skill para template completo):

1. Metadata (spike, codebase, fecha, auditor)
2. Resumen ejecutivo (1 parrafo + score global)
3. PIBER alignment (check narrativo)
4. IDCF matrix:
   - Design Theses table (thesis -> status -> evidencia -> gap)
   - Capabilities table (capability -> build/buy/partner status -> evidencia)
   - Features by tier (P0/P1/P2/P3 -> shipped/partial/missing)
5. Anti-patterns detected
6. North Star instrumentation check
7. Recommendations prioritizadas (top 5, con siguiente accion concreta)
8. Appendix: evidencia raw (grep outputs, file listings)

## Modo sin argumentos

Si el usuario invoca `/product-vision-audit` sin args, preguntar interactivamente:

1. "Cual es la vision a auditar? (Linear ID, URL, o path a .md)"
2. "Cual es el codebase a auditar? (path absoluto o relativo)"
3. "Queres restringir el scope a un subdirectorio? (enter para auditar todo)"
4. "Donde guardo el report? (enter para default)"

Luego proceder como si los args hubieran sido pasados.

## Dog-fooding

Este comando fue creado en el contexto de DojoOS para auditar sus propios pilares contra los spikes PIBER+IDCF maestros (DOJ-3228 y hijos DOJ-3222 a DOJ-3230). Los primeros audits dogfooded fueron:

- `dojo-os` vs `DOJ-3222` (Pathways)
- `dojo-agent-openclaw-plugin` vs `DOJ-3229` (Agent/Doji)

Ver `${CLAUDE_PLUGIN_ROOT}/references/product-vision-audit-examples.md` si existe, para ejemplos de reports generados.
