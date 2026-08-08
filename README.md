# Guerra Fría: 1945-1991 — Mod para Hearts of Iron IV

Un mod para **Hearts of Iron IV** centrado en la Guerra Fría, con foco
especial en **América Latina**. Añade árboles de decisiones (focus trees)
alternativos para **Estados Unidos**, la **Unión Soviética**, **Cuba**,
**Chile** y **Argentina**, tres fechas de inicio alternativas (1945, 1970 y
1980), y eventos narrativos ligados a los grandes hitos de la época: el
Plan Marshall, la OTAN, el Pacto de Varsovia, la Revolución Cubana, la
Crisis de los Misiles, la vía chilena al socialismo y el golpe de 1973, el
Proceso de Reorganización Nacional y la Guerra Sucia en Argentina, y la
tensión por las Malvinas.

## Contenido actual

### Fechas de inicio (`common/bookmarks/coldwar_bookmarks.txt`)

Tres bookmarks seleccionables desde el lanzador de partida:

- **1945** — El amanecer de la Guerra Fría (recién terminada la Segunda
  Guerra Mundial).
- **1970** — Distensión y revolución en América Latina (año de la elección
  de Salvador Allende en Chile).
- **1980** — La década perdida (dictaduras militares en el Cono Sur,
  revolución sandinista reciente en Nicaragua).

Cada bookmark fija la ideología gobernante aproximada de USA, la URSS y
varios países latinoamericanos (Cuba, Chile, Argentina, Brasil, Nicaragua)
para ese momento histórico. **Importante:** estos bookmarks solo cambian la
fecha de inicio y el gobierno de esos países; no reescriben el mapa mundial
completo (fronteras, descolonización, propietarios de provincias, etc.),
que sigue basado en la configuración vanilla de 1936. Es un punto de
partida "ligero", no una recreación histórica exhaustiva de 1970 u 1980.

### Árboles de decisiones (`common/national_focus/`)

- **`coldwar_soviet.txt`** (URSS) — Pacto de Varsovia, planes quinquenales,
  programa nuclear y espacial, Cuba, Afganistán, distensión.
- **`coldwar_usa.txt`** (EE. UU.) — Plan Marshall, OTAN, contención, Corea,
  Vietnam, CIA, programa nuclear y espacial, distensión, IDE.
- **`coldwar_cuba.txt`** (Cuba) — Triunfo de la Revolución, reforma agraria,
  nacionalizaciones, alineamiento soviético, Crisis de los Misiles,
  exportación de la revolución, apoyo a los sandinistas, defensa ante
  Bahía de Cochinos.
- **`coldwar_chile.txt`** (Chile) — Unidad Popular, elección de Allende,
  nacionalización del cobre, y una **bifurcación histórica**: profundizar
  la vía socialista o el golpe militar de 1973 (represión, Chicago Boys,
  Operación Cóndor).
- **`coldwar_argentina.txt`** (Argentina) — Legado peronista, inestabilidad
  política, golpe de 1976 (Proceso de Reorganización Nacional), Guerra
  Sucia, Operación Cóndor, crisis económica, tensión por las Malvinas y
  retorno a la democracia en 1983.

Todos los árboles solo reemplazan el árbol genérico del país indicado
(mediante el bloque `country = { factor ... tag = ... }`); el resto de
naciones conserva su árbol de decisiones vanilla o el de otros mods.

### Eventos (`events/coldwar_flavor.txt`)

Bloqueo de Berlín, reacción al Plan Marshall, primera bomba atómica
soviética, Crisis de los Misiles de Cuba, golpe de Estado en Chile (bombardeo
de La Moneda), y tensión por las Malvinas.

### Localización

`localisation/english/` y `localisation/spanish/` contienen los textos de
focos, eventos y bookmarks en ambos idiomas.

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
  `default = no`) para dar a otra nación (Nicaragua, Brasil, México, Reino
  Unido, Francia, China, Alemania Oriental/Occidental...) su propio árbol
  de decisiones. En `common/bookmarks/coldwar_bookmarks.txt` ya hay entradas
  de `country = { tag = BRA ... }` y `country = { tag = NIC ... }` listas
  para conectarles un árbol propio cuando se cree.
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
