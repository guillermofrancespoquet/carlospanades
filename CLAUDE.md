# Carlos Panadés – Contexto del repo

Planificación nutricional de un cliente de Guille (NutriLogos). **Repo público** (GitHub Pages). Este repo es la fuente de verdad del plan; se gestiona desde aquí, no desde el chat.

## Idioma
- Todo en **español** (plan, notas, commits). El plan se redacta en segunda persona ("tu rendimiento", "tu tolerancia").

## Archivos
```
index.html                                  plan del cliente (HTML autónomo, estilo app NutriLogos v1.0); se llama index.html para que Pages lo publique (en la documentación del cliente figura como carlos-panades.html)
Logo.png                                    icono (apple-touch-icon)
_headers.txt                                cabeceras de caché (no-cache)
INSTRUCCIONES_PLANTILLA_NUTRILOGOS_v5.0.txt   plantilla base: estructura HTML, CSS, JS, checklist
INSTRUCCIONES_ESTILO_APP_NUTRILOGOS_v1.0.txt  capa visual app sobre la v5.0: tokens, CSS completo, checklist
CLAUDE.md                                   este archivo
```
- `index.html` = plan ya en estilo app (no hay versión v5.0 aparte ni sufijo `_app`; la regla del sufijo de la guía no aplica aquí).
- Los PDFs de antropometría y bioimpedancia ya no están en el repo y el HTML no los enlaza.

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
- Enfoque: base animal con transición progresiva a plant-based (preferencias, practicidad, tolerancia digestiva).
- 4 comidas: Almuerzo, Comida, Merienda (solo días de entreno/pre-partido) y Cena. No desayuna de forma tradicional.
- Días: entreno L/X/J (19h) y S (9:30h); partido D (tarde). Solo se planifica la semana típica (la alterna queda fuera por ahora). Descanso M y V.
- Legumbres solo en días sin entreno, formato ensalada, cantidad gradual (tolerancia digestiva).
- Huevo y jamón serrano: 1 vez/semana cada uno. AOVE moderado. Pescado azul pequeño en cenas. Pechuga preferida, también pavo.
- Pan integral/centeno por defecto; pan blanco solo pre-entreno/pre-partido. Arroz blanco víspera de partido.
- Exclusión: dátil (sustituir por guayaba, ½ plátano o pasas).
- Cena libre post-partido: carbohidrato como base, sin llamarla "capricho".
- Sin batch cooking; cocina a diario (horno, air fryer, fogones, 15-45 min).

## Objetivo energético (decidido con Guille)
- Déficit calórico **moderado de 300-500 kcal** respecto al gasto, con periodización de carbohidratos (más en entreno/partido, menos en descanso) y sin perder rendimiento.
- Cálculo NutriLogos (20/10/2026): BMR 1846 kcal (rango 1606-2086) · TDEE 2861 · **objetivo 2432 kcal/día** (≈ −430 kcal; pérdida ≈ 0,47 %/semana) · P 133 g (22 %) · G 68 g (25 %) · HC 323 g (53 %) · masa libre de grasa 75 kg.
- Los 133 g de proteína salen de la nueva valoración (el cliente ha bajado ~3 kg respecto a la inicial).
- **Proteína: techo de 1,6 g/kg de peso.** Con su historial es suficiente para cubrir requerimientos con margen; no subir más con la evidencia actual (decisión de Guille).
- Menú de la revisión del 17/10/2026 (estimación orientativa, tablas estándar): ~1630 kcal/día escritas (~1700 con el skyr opcional), P ~103-115 g (≈1,2-1,4 g/kg; no se sube más por ahora). Con extras no escritos (alcohol, comidas fuera, cena libre real; ~150-300 kcal/día) y un gasto central estimado ~2300-2400, el déficit queda en ~350-400 kcal. El gasto real se calibra con las pesadas en ayunas que pasa el cliente (>0,5 kg/semana durante 2 semanas: subir ~150-200 kcal; <0,1 kg/semana: bajarlas).
- Alcohol y extras: los cuenta Guille, **no aparecen en el plan**.

## Objetivos de la revisión (17/10/2026)
- Bioimpedancia: 13,1 % → **12,5 %** (≈ −0,6 kg de grasa a masa magra constante, 72,2 kg).
- Pliegues: **Σ6 <45 mm** (47,8 en 17/10), **Σ8 <56 mm** (58,8; derivado proporcionalmente, diana de trabajo y no umbral). Pliegue de muslo como seguimiento (14,3 mm), sin objetivo específico.
- Durnin-Womersley como referencia secundaria: ~9-9,5 % (Σ4 bíceps+tríceps+subescapular+cresta ilíaca ≈ 22 mm; 23,5 en 17/10). No es convertible con la bioimpedancia.
- Bioimpedancia siguiente: por la mañana (la del 17/10 fue por la mañana; la inicial, por la tarde).

## Cantidades de referencia del menú
- Arroz integral (lunes): 125 g precocinado (~210 kcal) o 80 g en crudo. Arroz blanco (sábado): 150 g en crudo. Quinoa (jueves): 125 g. Pasta integral (miércoles): 100 g en crudo. Sin "vasito" en el texto, solo gramos.
- Legumbres martes y viernes: ≈180 g escurridas. Pescado de las cenas: 170 g. Patata: 300 g (L/X/J), 250 g (M/V), 350 g (S). Nueces 20 g en el almuerzo de L/X/J (y en la comida de M/V).
- Opcionales: skyr o griego ligero (125 g) a media mañana con algo de fruta; una onza de chocolate negro ≥85 % tras la cena.
- Cafeína antes de entrenar: ≤200 mg, al menos 60 min antes.

## Forma de trabajo
- Revisión con el cliente aprox. **mensual**: bioimpedancia, antropometría y consulta (fuera de este repo). Con esos datos se valora el mes y se discuten aquí los cambios del plan.
- No cambiar cantidades del menú entre revisiones salvo petición de Guille.

## Decisiones cerradas
- Revisiones: se gestionan fuera de este repo; no tocar la sección ni preocuparse de fechas.
- Estilo: prevalece la v1.0 (app) sobre la v5.0.
- Repo y HTML se quedan **públicos y con los datos actuales** hasta la próxima revisión; entonces se actualizan.
- Solo semana típica, sin versión alterna.
- El lenguaje actual del plan (impresiones, subtítulo) se mantiene.
- Hallazgos fuera del ámbito nutricional: no se comunican al cliente y no se escriben en el repo.

## Privacidad (repo público)
- Todo lo que está aquí es público. Los datos clínicos detallados (analíticas, hallazgos fuera de ámbito nutricional, notas internas) **no van en el repo**: viven en el .md del cliente fuera del repo. No subir ese .md ni PDFs de pruebas.
- Antes de subir cualquier archivo nuevo, pensar si se publicará por Pages.
- `index.html` muestra datos de salud con nombre del cliente en una URL pública: Guille lo mantiene así hasta la próxima revisión.

## Reglas de trabajo
- No renombrar archivos (PDFs, etc.) del cliente de forma unilateral al depurar; si falla un enlace, pedir primero la URL en vivo de GitHub Pages.
- Ramas: desarrollar en la rama asignada a la sesión; no tocar `main` directamente.
- PR y merge: se puede abrir PR siempre que haga falta; **fusionar solo cuando Guille lo diga** en el chat.
