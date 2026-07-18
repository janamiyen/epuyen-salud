# Estado actual — Epuyen Salud (web)

**Última sesión: 2026-07-18**

## Qué se hizo (2026-07-18)
- **Flores nuevas en el hero (LOCAL, sin commitear — esperando ok de Lucas/Lucía)**: Lucas pidió rediseñar la flor pasionaria (`Downloads/epuyen (2).png`) en estilo minimalista/sutil. Se generaron con fal.ai (nano-banana-pro + Bria rmbg, key de Lucas) varias rondas; aprobó las sutiles de línea fina y las formas de floripondio. Assets nuevos: `flor-finita.png` (línea pura malva, LA elegida — a Lucas le encantó esa estética "finita"), `flor-sutil.png` (variante con lavado + estambres dorados — rechazada para el flanco, se veía pesada a opacidad llena), `floripondio.png` (campana colgante lila con pimpollo), `floripondio-2.png` (variante, sin uso). Iteración: primero flor-sutil en flanco izq + marca de agua gigante detrás del título → Lucas prefirió solo elementos chicos y nítidos estilo referencia rusa → flanco der pasó por: `floripondio.png` (shape lila rellena — "queda raro"), `floripondio-oneline.png` (una línea caligráfica), `floripondio-rama.png` (colgante, gustó — "ME agregada!!!") pero Lucas la quiso "saliendo de la pared" y luego "doblada para arriba, con la flor parada" → se generó **`floripondio-up.png`** (DEFINITIVA): rama que entra horizontal desde la derecha, se curva hacia arriba y la campana queda erguida con la boca estrellada. Montada como img simple `.hero-deco.flor-rama` (sin wrapper ni rotate — ya viene dibujada doblada), top:30%, clamp 130-180px, y **anclada al borde REAL del viewport** con `right:calc(50% - 50vw - 6px)` (el hero vive en `.wrap` max-1180px y con right normal quedaba lejos de "la pared"; hay overflow-x:hidden en html/body así que no genera scroll). **En mobile la rama SÍ se ve**: abajo a la derecha del hero, en el aire entre el CTA de WhatsApp y el banner verde — regla en el media ≤980px `.hero-deco.flor-rama{width:74px!important;top:auto!important;bottom:1%!important;right:calc(50% - 50vw - 4px)!important}` (⚠️ los !important son necesarios: los estilos inline del img pisan la media query; primer intento sin !important dejó la flor a 130px pisando el título en mobile). Assets alternativos sin uso en assets/: floripondio.png, floripondio-2.png, floripondio-oneline.png, floripondio-linea.png, floripondio-linea2.png, floripondio-rama2.png, flor-sutil.png. Los originales transparentes 2K quedaron en `Downloads/epuyen-flor-sutil-v1/v2.png` y `epuyen-floripondio-v1/v2.png`; página de comparación temporal en scratchpad (localhost:8324/compare.html).
- Referencia visual sigue siendo la captura del sitio ruso (`Downloads/captura hero que me gusta.jpg`).

## Qué se hizo (2026-07-17)
- **Hero rediseñado: texto centrado, sin ilustración grande** (a Lucía no la convencía la "colorada" `hero-person.png`, ahora sin uso en assets). Se exploraron 6 variantes en `_hero-variants.html` (interno, no commitear); Lucas eligió su propia idea refinada con una captura de referencia (`Downloads/captura hero que me gusta.jpg`, sitio ruso "Психология счастья"): título centrado, deco-chat/deco-check chicos **flanqueando el título a su altura**, micro-puntos geométricos de color en los márgenes. Los CTAs quedaron lado a lado centrados (mismo 340×57). En ≤980px las decos se ocultan (`.hero-deco{display:none}`).
- **SVGs ilustrativos míos rechazados** (mini montañas, horizonte, corazón, sparkles): Lucas va a crear sus propias viñetas SVG para los flancos. No volver a meter ilustración SVG propia en el hero sin pedido.
- **Degradados ambientales retocados**: el coral `amb-a` primero se eliminó ("luz naranja horrible" — quedaba expuesto sin la ilustración) pero Lucas lo extrañó como acento → restaurado más chico y metido en la esquina sup. derecha (340px, detrás del CTA del nav). El teal `amb-b` subió de top:520px a top:280px para quedar dentro del hero (lado izquierdo, detrás del deco-chat). Blobs celeste/beige detrás de la foto de Lucía en "Nuestra historia" eliminados (quedaban mal con foto real).
- Imágenes IA que probó Lucas: `assets/_hero-prueba.png` (lila, texto inglés con typos — descartada) y `_hero-prueba2.png` (verde sin texto — descartada en favor del hero tipográfico). No commitear los `_*`.
- **CTA del nav (y menú mobile) cambiado a "Reservar mi primera sesión"** (clave `empezar`, 3 idiomas; pedido de Lucas, corregido "primer"→"primera"). Su WhatsApp usa la clave nueva `waSession` ("Quiero reservar mi primera sesión en Epuyen"). El hero y el form de cierre siguen con "Encontrá el profesional adecuado" (`cta1`/`clBtn`).
- Claves i18n sin uso nuevas: `heroTag2` (era "por videollamada" del visual viejo). Grafía "Epuyén"→"Epuyen" (sin tilde) corregida en historia es/en/pt.
- **Todo pusheado a prod: commit `fb2b98d`** (checkpoint pedido por Lucas "por si tenemos que volver al pasado"). `.gitignore` ahora excluye `_*` (previews e imágenes de prueba internas).
- **Todos los CTAs cableados a WhatsApp de Lucía** (+34 611 45 73 91 → `wa.me/34611457391`) con mensaje precargado según contexto, vía atributo `data-wa` + helper `waLink()`. Los mensajes viven en `I18N` (claves `wa*`) y se regeneran al cambiar idioma (es/en/pt) dentro de `applyI18n()`.
- **Elementos cableados (14)**: CTA nav + menú mobile + hero (`waFind`), "Hablar por WhatsApp" y WhatsApp del footer (`waGeneric`), las 6 cards de "¿Qué estás buscando?" ahora son `<a>` clickeables enteras (`waUnsure`, `waTherapy`, `waCouple`, `waVocational`, `waEmotional`, `waAbroad`), cards psiquiatría/nutrición también clickeables (`waPsych`, `waNutri`), CTA "Trabajá con nosotros" (`waJoin` — **ya no abre el modal**; el modal `joinModal` quedó en el código, sin uso).
- **Botones del hero con el mismo tamaño**: nueva clase `.cta-eq` (57px de alto, `min-width:min(340px,100%)`, mismo padding/font) aplicada a hero CTA1, CTA2 y jwCta. Quedan apilados en desktop (el CTA largo no entra al lado del otro) pero idénticos en tamaño.
- **Form de cierre**: mientras `LEAD_ENDPOINT` siga con `PENDIENTE`, `submitLead()` abre WhatsApp con `waLead` ("¡Hola! Soy {name}…") en vez de mostrar error. Cuando se pegue el endpoint real de Formspree, vuelve solo al flujo original.
- Verificado en Chrome local (puerto 8931; el 8080 está bloqueado por Windows ahora): alturas/anchos iguales, hrefs correctos en 3 idiomas, HTML balanceado, JS ok. Lucas lo testeó local y dio el ok → commit `91cb1f8` **pusheado a prod** (auto-deploy Vercel).

## Qué se hizo (2026-07-14)
- **Marca corregida a "Epuyen" (sin diéresis)** en todo el proyecto: Lucía marcó que la ü es errónea. 18 apariciones reemplazadas en `index.html` (title, alts, textos i18n es/en/pt, subjects de mailto y Formspree), README y los archivos de memory. El logo (`assets/logo.png`) ya decía "epuyen" sin ü, no hizo falta tocar assets. Pusheado a prod para que lo vea Lucía.
- **Form de leads**: Lucas y Lucía lo están verificando entre ellos (endpoint Formspree sigue `PENDIENTE`, pero no bloquear el resto del trabajo por esto).

## Qué se hizo (2026-07-13)
- **Card "No sé qué necesito" movida al primer lugar** de la grilla "¿Qué estás buscando?" (pedido de Lucía). Las otras 5 se corrieron un lugar; comentarios HTML renumerados. Claves i18n intactas (sigue siendo `s6*`).
- **Form de cierre (nombre + WhatsApp) cableado a Formspree**: ahora es un `<form id="leadForm">` real con `submitLead()` (fetch POST, JSON), honeypot `_gotcha`, estados enviando/gracias/error en 3 idiomas (claves nuevas `clSending`, `clOk`, `clOkD`, `clErr`). El botón `<a>` pasó a `<button type="submit">` con el mismo estilo.
- **PENDIENTE CRÍTICO**: falta crear el form en https://formspree.io con el email de Lucía y pegar el endpoint real en `const LEAD_ENDPOINT` (hoy dice `PENDIENTE` → el submit muestra el mensaje de error). Se eligió Formspree sobre Typeform y Web3Forms (ver decisions).

## Qué se hizo (2026-07-06)
- Nueva sección **"Nuestra historia"** (`id="historia"`) entre el strip de equipo y el closing CTA: historia personal de Lucía en primera persona (clínica y granja terapéutica de sus padres, «dos que van», Patagonia), con **foto real de Lucía** (`assets/lucia-hero.jpeg`, composición cuadrada ilustrada que vino de WhatsApp) y firma. Traducida a es/en/pt.
- Bloque verde de stats: bajada nueva "Sin bots, sin algoritmos: respuesta humana." (`bnSub`, 3 idiomas).
- CTA principal: "Empezar orientación" → **"Encontrá el profesional adecuado"** (`empezar`, `cta1`, `clBtn`, 3 idiomas). `s6cta` quedó igual.
- Sección psiquiatría/nutrición: nuevo copy "También contamos con psiquiatría y nutrición online" + "Profesionales verificados, integrados a tu proceso de bienestar." Se quitó el kicker "también te acompañamos" (redundante con el "También" del título).
- Idiomas de atención: todo el copy que decía "en español" ahora dice **"en español e inglés"** (meta description, stat `bn2l`, card "Vivo en el exterior" `s5d`, tagline del footer; 3 idiomas).
- El hero conserva la imagen animada original (`hero-person.png`); la foto de Lucía se decidió usar en "Nuestra historia" en vez del hero.

## Claves i18n sin uso (por si se retoman)
`abQm`, `abTag` — eran de la tarjeta decorativa «dos que van» que se reemplazó por la foto.

## Cómo correr local
`python -m http.server 8080` desde `Desktop/Epuyen/web/` → http://localhost:8080

## Repo y deploy
- Repo: `janamiyen/epuyen-salud` (cuenta de Jana; Lucas no tiene push directo → `gh auth switch -u janamiyen && git push && gh auth switch -u LucasEzequielSilva`)
- Deploy: Vercel de janamiyen, auto-deploy al pushear a main → https://epuyen-salud.vercel.app (verificado 2026-07-07)

## Próximos pasos
- **Crear cuenta Formspree con el email de Lucía y pegar el endpoint en `LEAD_ENDPOINT`** (index.html, cerca de `submitLead`). No conviene deployar el form así: el submit da error al usuario.
- Validar con Lucía cómo quedó su foto en "Nuestra historia"
- Revisar nav en ~800–980px con el CTA nuevo más largo
- Links del nav siguen siendo spans sin href; `#historia` existe como ancla
