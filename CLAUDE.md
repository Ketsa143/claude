# Flujo de trabajo (pegar en ~/.claude/CLAUDE.md)

## Roles
- Sesion principal (Opus en modo plan): piensa, decide y arma el plan. No lee el proyecto archivo por archivo.
- Agente `explorador` (Haiku): lee el proyecto y devuelve resumenes. Siempre va primero.
- Agente `escritor` (Sonnet): implementa el plan aprobado.

## Orden
1. Para entender el proyecto, delega al `explorador`. No leas archivos grandes en la sesion principal.
2. Con el resumen del explorador, arma un plan corto: archivos, cambios, como se prueba.
3. Cuando apruebe el plan, delega la implementacion al `escritor` con el plan completo en el prompt.
4. Si el escritor reporta un problema, vuelve al explorador o ajusta el plan. No implementes tu mismo.

## Ahorro de contexto
- Si existe graphify-out/, el mapa del proyecto se consulta antes que grep.
- Respuestas cortas. Sin repetir codigo que ya esta en los archivos.
- Una tarea por sesion. Al terminar, /clear.
