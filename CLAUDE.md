# Carlos Panadés (PANA) – Contexto del repo

Planificación nutricional de **Carlos Panadés Zaragoza**, cliente de Guille (NutriLogos). Este repo es la fuente de verdad del plan; se gestiona desde aquí, no desde el chat.

## Idioma
- Todo en **español** (plan, notas, commits). El plan se redacta en segunda persona ("tu rendimiento", "tu tolerancia").

## Archivos
```
index.html                                  plan del cliente (HTML autónomo, estilo app NutriLogos v1.0); se publica con GitHub Pages
Logo.png                                    icono (apple-touch-icon)
_headers.txt                                cabeceras de caché (no-cache)
INSTRUCCIONES_PLANTILLA_NUTRILOGOS_v5.0.txt   plantilla base: estructura HTML, CSS, JS, checklist
INSTRUCCIONES_ESTILO_APP_NUTRILOGOS_v1.0.txt  capa visual app sobre la v5.0: tokens, CSS completo, checklist
CLAUDE.md                                   este archivo
```
- `index.html` = plan ya en estilo app (no hay versión v5.0 aparte ni sufijo `_app`; la regla del sufijo de la guía no aplica aquí).
- Los PDFs de antropometría y bioimpedancia (07-09-2026) ya no están en el repo y el HTML no los enlaza.

## Estructura de `index.html`
Orden: h1 + subtítulo → Objetivo → Impresiones del profesional → Menú semanal de un vistazo (`#printArea`) → Menú desarrollado por días → Lista de compra semanal.
- Datos en JS: `days[]` (7 días; cada comida con `type`, `time`, `name`, `desc` separado por `\n`, `short`, `note`, `libre`) y `shopCategories[]`.
- La tabla semanal se genera desde `short` de cada comida; si cambia una comida, actualizar `short`, `desc`, `note` **y** la lista de compra.
- Sin suplementación, sin recetas, sin batch cooking en este plan (los hooks existen en el JS pero no se usan).

## Estilo
- Estructura, JS y reglas: `INSTRUCCIONES_PLANTILLA_NUTRILOGOS_v5.0.txt`. Aspecto: `INSTRUCCIONES_ESTILO_APP_NUTRILOGOS_v1.0.txt` (solo capa visual: CSS/colores; sustituye el CSS de la v5.0 y no cambia estructura ni JS).
- La v1.0 omite del HTML la descripción del cliente, el perfil con métricas y la próxima revisión (la app ya los muestra). Es la variante de este plan.
- Tras cualquier cambio: comprobar JS con `node --check` (extrayendo el `<script>`), revisar en móvil (~430 px) y escritorio, y que el `@media print` siga intacto.
- Objetivo redactado como "base plant-based" (sin "100%").

## Criterios nutricionales del plan (decididos con Guille)
- Enfoque: base animal con transición progresiva a plant-based (preferencias, practicidad, SIBO).
- 4 comidas: Almuerzo, Comida, Merienda (solo días de entreno/pre-partido) y Cena. No desayuna de forma tradicional.
- Días: entreno L/X/J (19h) y S (9:30h); partido D (tarde). Semana alterna: entreno L/X/J/V y partido S. Descanso M y V (o D en la alterna).
- Legumbres solo en días sin entreno, formato ensalada, cantidad gradual (SIBO).
- Huevo y jamón serrano: 1 vez/semana cada uno. AOVE moderado. Pescado azul pequeño en cenas. Pechuga preferida, también pavo.
- Pan integral/centeno por defecto; pan blanco solo pre-entreno/pre-partido. Arroz blanco víspera de partido.
- Exclusión: dátil (sustituir por guayaba, ½ plátano o pasas).
- Cena libre post-partido: carbohidrato como base, sin llamarla "capricho".
- Sin batch cooking; cocina a diario (horno, air fryer, fogones, 15-45 min).

## Pendientes abiertos (ver también el .md del cliente)
- **Calorías**: el menú promedia ~1650-1700 kcal/día, por debajo del TMB (1973) en días de descanso y muy por debajo del gasto estimado. Decidir con Guille: subir cantidades en descanso o replantear el déficit.
- **Proteína**: ~106 g/día vs objetivo ~138 g (1,6 g/kg). Subir legumbre/tofu/edamame antes que añadir batido.
- **Revisión**: la fecha fijada (12/10/2026) ya pasó; reprogramar y repetir bioimpedancia y perfil lipídico.
- Semana alterna: el HTML solo detalla la semana típica; la alterna se describe en la nota de la tabla.

## Privacidad (datos de salud de un cliente)
- Los datos clínicos detallados (analíticas, hallazgos fuera de ámbito nutricional, notas internas) **no van en el repo**: viven en el .md del cliente fuera del repo. El HTML solo lleva lo imprescindible para el plan.
- Antes de subir cualquier archivo nuevo, pensar si se publicará por Pages.

## Reglas de trabajo
- No renombrar archivos (PDFs, etc.) del cliente de forma unilateral al depurar; si falla un enlace, pedir primero la URL en vivo de GitHub Pages.
- Ramas: desarrollar en la rama asignada a la sesión; no abrir PRs salvo petición; no tocar `main` directamente.
