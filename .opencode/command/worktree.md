---
description: Crea un git worktree en .worktrees/ con el nombre derivado del argumento.
---

Recibes un argumento que puede contener espacios: "$ARGUMENTS"

Analiza el argumento y deriva el nombre del worktree:
- Elimina espacios al inicio y al final.
- Reemplaza los espacios internos por guiones ("-").
- Si el argumento queda vacío, no ejecutes nada y avisa que se requiere un nombre.

Con el nombre derivado <nombre>, ejecuta exactamente este comando desde el directorio actual, sin cambiarte de directorio:

git worktree add .worktrees/<nombre>

No hagas nada más. Solo ejecuta el comando. No te cambies de directorio.
