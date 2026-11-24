# Configuracion base de Claude Code

## Estructura

```
CLAUDE.md                     # Flujo de trabajo (roles y orden) + reglas Karpathy
.claude/settings.json         # Marketplaces y plugins
.claude/skills/caveman/       # Skill caveman (incluida en el repo)
.claude/skills/caveman-review/ # Skill caveman-review (incluida en el repo)
.claude/agents/explorador.md  # Agente explorador (Haiku)
.claude/agents/escritor.md    # Agente escritor (Sonnet)
```

## Flujo

**Opus planea, Haiku explora y Sonnet escribe.**

1. La sesion principal (Opus, modo plan) piensa y arma el plan.
2. `explorador` lee el proyecto y devuelve resumenes.
3. `escritor` implementa el plan aprobado.

## Agentes

- **explorador** (`haiku`): solo lectura (Read, Glob, Grep, Bash). Explora el proyecto y devuelve un resumen compacto: donde esta algo, como se conectan los modulos, que archivos tocar. Nunca modifica archivos.
- **escritor** (`sonnet`): Read, Edit, Write, Bash, Glob, Grep. Implementa o refactoriza codigo siguiendo un plan ya aprobado; si necesita contexto, le pide un resumen al explorador.

## Plugins (`.claude/settings.json`)

`caveman` y `andrej-karpathy-skills` ya no se instalan como plugins: vienen incluidos en el repo (skills en `.claude/skills/` y reglas en `CLAUDE.md`).

| Plugin | Marketplace | Estado |
|---|---|---|
| `claude-code-setup` | claude-plugins-official | activo |
| `egm` | google/elephant-goldfish-model | desactivado |

## Creditos

- caveman — https://github.com/JuliusBrussee/caveman — Apache License 2.0 (Copyright 2026 Julius Brussee). Se incluyen las skills `caveman` y `caveman-review` en .claude/skills/.
- andrej-karpathy-skills — https://github.com/multica-ai/andrej-karpathy-skills — MIT. Su CLAUDE.md esta incluido en la seccion "Reglas de codigo (Karpathy)" de nuestro CLAUDE.md.
