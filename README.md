# Guerra Fría: 1945-1991 — Mod para Hearts of Iron IV

Un mod para **Hearts of Iron IV** centrado en la Guerra Fría. Añade árboles de
decisiones (focus trees) alternativos para **Estados Unidos** y la **Unión
Soviética** que se activan tras el fin de la Segunda Guerra Mundial (después
del 8 de mayo de 1945), cubriendo eventos clave como el Plan Marshall, la
OTAN, el Pacto de Varsovia, la Guerra de Corea, la Guerra de Vietnam, la
carrera armamentística nuclear y la carrera espacial.

## Contenido actual

- **`common/national_focus/coldwar_soviet.txt`** — Árbol de decisiones de la
  URSS (Pacto de Varsovia, planes quinquenales, programa nuclear y espacial,
  Cuba, Afganistán, distensión).
- **`common/national_focus/coldwar_usa.txt`** — Árbol de decisiones de
  Estados Unidos (Plan Marshall, OTAN, contención, Corea, Vietnam, CIA,
  programa nuclear y espacial, distensión, IDE).
- **`events/coldwar_flavor.txt`** — Eventos narrativos ligados a ciertos
  focos (Bloqueo de Berlín, reacción al Plan Marshall, primera bomba
  atómica soviética).
- **`localisation/english/`** y **`localisation/spanish/`** — Textos de los
  focos y eventos en inglés y español.

Ambos árboles solo reemplazan el árbol genérico para `USA` y `SOV`
(mediante el bloque `country = { factor ... tag = ... }`); el resto de
naciones conserva su árbol de decisiones vanilla o el de otros mods.

## Instalación

1. Copia (o enlaza con symlink) esta carpeta dentro de:
   - Windows: `Documentos\Paradox Interactive\Hearts of Iron IV\mod\`
   - Linux: `~/.local/share/Paradox Interactive/Hearts of Iron IV/mod/`
   - macOS: `~/Documents/Paradox Interactive/Hearts of Iron IV/mod/`
2. Abre el launcher de HOI4, activa el mod **"Guerra Fria: 1945-1991"** y
   lanza una nueva partida.
3. Juega con Estados Unidos o la URSS: la Segunda Guerra Mundial transcurre
   con las reglas normales del juego; a partir de mayo de 1945 se
   desbloquea el primer foco del árbol de la Guerra Fría.

## Cómo extender el mod

- **Nuevos países**: crea un archivo en `common/national_focus/` siguiendo
  el mismo patrón (`country = { factor = 0 modifier = { add = 15 tag = XXX } }`,
  `default = no`) para dar a otra nación (Reino Unido, Francia, China, Cuba,
  Alemania Oriental/Occidental...) su propio árbol de decisiones.
- **Eventos**: añade nuevos `country_event` en `events/` y engánchalos a un
  foco mediante `completion_reward = { country_event = { id = ... } }`.
- **Localización**: cada clave nueva (`id_del_foco` y `id_del_foco_desc`,
  o los `title`/`desc`/`option` de los eventos) debe añadirse tanto en
  `localisation/english/` como en `localisation/spanish/`.
- **Iconos**: los focos actuales reutilizan iconos genéricos ya incluidos en
  el juego base (`GFX_goal_generic_*`), por lo que no se necesitan asets
  gráficos adicionales. Si quieres iconos personalizados, añade tus `.dds`
  en `gfx/interface/goals/` y regístralos en un archivo `.gfx` en
  `interface/`.
- **Fecha de inicio alternativa**: para arrancar la partida directamente en
  1945 o 1949 en lugar de 1936, se puede añadir un `bookmark` personalizado
  en `common/bookmarks/` (no incluido todavía en este esqueleto).

## Aviso

Este repositorio es una base funcional y extensible, no un mod histórico
completo: cubre dos países con ramas temáticas representativas de la Guerra
Fría. Está pensado como punto de partida para seguir añadiendo naciones,
eventos, decisiones (`decisions`), y contenido gráfico.
