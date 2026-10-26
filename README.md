# skills

## META
- id: skills
- owner: EduBalderas
- visibility: public
- idioma: mixto
- estado: estable
- tipo: fork
- nivel: L4
  - L0=gobernanza/política
  - L1=marca/metodología
  - L2=flujo/arquitectura
  - L3=producto ejecutable
  - L4=herramienta
- familia: ninguna
- origen: upstream:https://github.com/mattpocock/skills
- experimento: no
- nacido_de: mattpocock/skills
- orquestado_por: N/A
- brief_desde: N/A

## OBJETIVO
Skills de agente pequeñas, adaptables y componibles para ingeniería de software real, con cualquier modelo.

## QUE_CONTIENE
- Plugin `mattpocock-skills` 1.3.1 (MIT) y marketplace propio en `.claude-plugin/`. Claude Code lo instala desde `claude-plugins-official`. El resto de instalaciones gestionadas usa este marketplace.
- Conjunto promovido: `skills/engineering/` y `skills/productivity/`. Cada uno tiene ficha en `docs/<bucket>/<skill>.md` y página en `https://aihero.dev/skills-<nombre>`.
- **Engineering, User-invoked**
  - **[ask-matt](./skills/engineering/ask-matt/SKILL.md)**: pregunta qué skill o flujo encaja. Enruta los skills que invoca la persona.
  - **[grill-with-docs](./skills/engineering/grill-with-docs/SKILL.md)**: grilling que además arma el modelo de dominio, afina términos y actualiza `GLOSSARY.md` y ADRs.
  - **[triage](./skills/engineering/triage/SKILL.md)**: mueve issues por una máquina de estados de roles de triage.
  - **[improve-codebase-architecture](./skills/engineering/improve-codebase-architecture/SKILL.md)**: busca oportunidades de profundizar módulos, las entrega en un informe HTML y hace grilling de la que elijas.
  - **[setup-matt-pocock-skills](./skills/engineering/setup-matt-pocock-skills/SKILL.md)**: deja listo el repo (issue tracker, etiquetas de triage, layout de docs). Una vez por repo.
  - **[to-spec](./skills/engineering/to-spec/SKILL.md)**: convierte la conversación en un spec y lo publica en el tracker.
  - **[to-tickets](./skills/engineering/to-tickets/SKILL.md)**: parte un plan, spec o conversación en tickets tracer-bullet con sus bloqueos, en archivo local o en el tracker.
  - **[implement](./skills/engineering/implement/SKILL.md)**: construye lo que describe un spec o un conjunto de tickets, con `/tdd` en las costuras pactadas y `/code-review` antes del commit.
  - **[implement-spec](./skills/engineering/implement-spec/SKILL.md)**: implementa un spec entero en una rama de integración. Trata los tickets como grafo, lanza subagentes en la frontera lista y cierra con `/code-review`.
  - **[wayfinder](./skills/engineering/wayfinder/SKILL.md)**: planifica un bloque mayor que una sesión como mapa de decision tickets en el tracker y los resuelve de uno en uno.
  - **[retro](./skills/engineering/retro/SKILL.md)**: tras una sesión, propone mejoras al entorno del agente (navegación, checks, estándares, steering, tooling), de mayor a menor gravedad.
- **Engineering, Model-invoked**
  - **[prototype](./skills/engineering/prototype/SKILL.md)**: prototipo desechable para una pregunta de diseño: un HTML compartible, o varias variaciones de UI en una ruta.
  - **[diagnosing-bugs](./skills/engineering/diagnosing-bugs/SKILL.md)**: diagnóstico por fases: feedback que falla en este bug, minimizar, hipótesis, instrumentar, arreglo, test de regresión.
  - **[research](./skills/engineering/research/SKILL.md)**: investiga en fuentes primarias de alta confianza y deja un Markdown citado. Corre como agente en segundo plano.
  - **[tdd](./skills/engineering/tdd/SKILL.md)**: red-green-refactor. Construye o corrige un corte vertical cada vez.
  - **[domain-modeling](./skills/engineering/domain-modeling/SKILL.md)**: afila el modelo de dominio: reta términos, prueba escenarios límite y actualiza `GLOSSARY.md` y ADRs.
  - **[codebase-design](./skills/engineering/codebase-design/SKILL.md)**: disciplina de módulos profundos: mucha conducta tras una interfaz pequeña, en una costura limpia, testeable por esa interfaz.
  - **[code-review](./skills/engineering/code-review/SKILL.md)**: revisión en dos ejes desde un punto fijo, Standards y Spec, en subagentes paralelos.
  - **[pr](./skills/engineering/pr/SKILL.md)**: forma del cuerpo de un pull request: el visual más pequeño que aclara el cambio, evidencia de que funciona y juicio de peligro al merge (puerta de un sentido o de dos, más radio de impacto).
  - **[wizard](./skills/engineering/wizard/SKILL.md)**: genera un wizard bash para pasos que solo puede hacer una persona: infra, credenciales, secretos de CI, un dashboard ajeno, una migración.
- **Productivity, User-invoked**
  - **[grill-me](./skills/productivity/grill-me/SKILL.md)**: entrevista un plan o diseño hasta cerrar cada rama.
  - **[handoff](./skills/productivity/handoff/SKILL.md)**: compacta la conversación en un handoff para que otro agente siga.
  - **[teach](./skills/productivity/teach/SKILL.md)**: enseña una habilidad o concepto en varias sesiones, con el directorio actual como estado.
  - **[to-questionnaire](./skills/productivity/to-questionnaire/SKILL.md)**: vuelve una decisión que no puedes cerrar solo en un cuestionario Markdown para quien sí puede.
  - **[wait-what](./skills/productivity/wait-what/SKILL.md)**: cuando un mensaje no aterriza, lo vuelve a explicar en claro con el vocabulario de `GLOSSARY.md`.
- **Productivity, Model-invoked**
  - **[grilling](./skills/productivity/grilling/SKILL.md)**: primitiva de entrevista que usan `grill-me`, `grill-with-docs`, `triage`, `wayfinder` e `improve-codebase-architecture`.
  - **[writing-for-agents](./skills/productivity/writing-for-agents/SKILL.md)**: cómo escribir para agentes: skills, `AGENTS.md` / `CLAUDE.md`, y cualquier doc al que el agente llega por un puntero.
- Soporte del catálogo: `SCOPE.md`, `.out-of-scope/`, `.agents/` (bloque de instalación, invocación, ADRs), `scripts/link-skills.sh`, `GLOSSARY.md`.

## CARACTERISTICAS
- User-invoked: solo cuando la persona los escribe (`disable-model-invocation: true` y `policy.allow_implicit_invocation: false`). Model-invoked: los alcanza la persona o el agente. Un user-invoked solo invoca skills model-invoked.
- Cada agente usa una vía. El plugin es un paquete de solo lectura que se actualiza solo. skills.sh copia archivos editables. Los comandos literales están en [`.agents/install-block.md`](./.agents/install-block.md): Claude Code, Codex, Copilot, VS Code, Gemini CLI y el resto.
- `/setup-matt-pocock-skills` se corre una vez por repo: issue tracker (GitHub, GitLab, markdown local u otro), etiquetas de triage y carpeta de docs.
- El conjunto cubre cuatro fallos de sesión: desalineación (`grill-me`, `grill-with-docs`), verbosidad (glosario y ADRs), feedback de ejecución (`tdd`, `diagnosing-bugs`) y entropía de diseño (`to-spec`, `codebase-design`, `improve-codebase-architecture`).
- `ask-matt` es el mapa de los skills que la persona puede invocar y de cómo se encadenan.
- Un issue de cambio sigue abierto solo si trae un fallo observado en una sesión real y encaja con la filosofía de [`SCOPE.md`](./SCOPE.md). Las preguntas van a [Discussions](https://github.com/mattpocock/skills/discussions).

## FUERA_DE_ALCANCE
- Propuestas de skills nuevos, con rama o con fork: [`.out-of-scope/new-skills.md`](./.out-of-scope/new-skills.md). Si el comportamiento se compone con los skills actuales, no nace otro.
- Cambios a `skills/misc/`: bucket congelado, [`.out-of-scope/frozen-misc-skills.md`](./.out-of-scope/frozen-misc-skills.md).
- `skills/in-progress/` es beta y `skills/deprecated/` está vacío. Esos skills quedan fuera del plugin, de las docs y de la lista promovida.
- Opciones de config, ramas por harness, o un flujo ajustado a una sola persona: viven en el `CLAUDE.md` / `AGENTS.md` de ese repo, o en una copia editable.
- Ideas sin un fallo observado en una sesión real.
- Renombrar skills para esquivar comandos nativos del harness: [`.out-of-scope/harness-name-collisions.md`](./.out-of-scope/harness-name-collisions.md).
- Issue trackers distintos de GitHub, GitLab y markdown local: [`.out-of-scope/mainstream-issue-trackers-only.md`](./.out-of-scope/mainstream-issue-trackers-only.md).
- Grilling con la herramienta nativa de preguntas del harness: [`.out-of-scope/native-question-tool.md`](./.out-of-scope/native-question-tool.md).
- Tope fijo de preguntas en un grilling: [`.out-of-scope/question-limits.md`](./.out-of-scope/question-limits.md).
- Modo verify de `setup-matt-pocock-skills`: [`.out-of-scope/setup-skill-verify-mode.md`](./.out-of-scope/setup-skill-verify-mode.md).
- Guardas para que un subagente no vuelva a entrar en skills: [`.out-of-scope/subagent-recursion.md`](./.out-of-scope/subagent-recursion.md).
- Cargar `writing-for-agents` solo al escribir, en skills que juzgan texto para agentes: [`.out-of-scope/lazy-load-writing-for-agents.md`](./.out-of-scope/lazy-load-writing-for-agents.md).

## RELACIONES
- Fork público de [mattpocock/skills](https://github.com/mattpocock/skills). Este remoto es [EduBalderas/skills](https://github.com/EduBalderas/skills).
- Autor del contenido: Matt Pocock, [aihero.dev](https://www.aihero.dev). Licencia MIT. Copyright 2026.
- Newsletter de cambios: [aihero.dev/s/skills-newsletter](https://www.aihero.dev/s/skills-newsletter). Ficha: [aihero.dev/skills](https://aihero.dev/skills). Catálogo: [skills.sh/mattpocock/skills](https://skills.sh/mattpocock/skills).
- Preguntas y discusión: [mattpocock/skills discussions](https://github.com/mattpocock/skills/discussions). Las issues de este repo registran cambios a los skills.

## ETIQUETAS
- fork
- engineering
- skills
- productivity
- tdd
- code-review
- grilling
- domain-modeling

## TOPICS_GITHUB
- engineering
- skills
- tdd
- code-review
- grilling
- domain-modeling
- productivity
