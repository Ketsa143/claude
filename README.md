# Configuracion base de Claude Code

## Estructura

```
CLAUDE.md                     # Flujo de trabajo (roles y orden)
.claude/settings.json         # Marketplaces y plugins
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

| Plugin | Marketplace | Estado |
|---|---|---|
| `caveman` | JuliusBrussee/caveman | activo |
| `andrej-karpathy-skills` | forrestchang/andrej-karpathy-skills | activo |
| `claude-code-setup` | claude-plugins-official | activo |
| `egm` | google/elephant-goldfish-model | desactivado |
