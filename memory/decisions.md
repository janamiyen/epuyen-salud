# Decisiones — Epuyen Salud (web)

## 2026-07-06 — Sección "Nuestra historia" con texto íntegro de Lucía
- **Qué**: se publicó la historia casi textual como la escribió Lucía (primera persona), sin resumir a bullet points corporativos.
- **Razón**: la voz personal es el diferencial de la marca ("detrás de esta marca existe una persona").
- **Alternativa descartada**: about us institucional en tercera persona.
- **Revisable**: sí, si Lucía quiere ajustar tono o sumar foto real.

## 2026-07-06 — Visual de la sección historia: tarjeta decorativa, no foto
- **Qué**: tarjeta blanca con isotipo, «dos que van» en Dancing Script y montañas SVG (Patagonia), sobre blobs orgánicos como el hero.
- **Razón**: no hay foto de Lucía disponible; la tarjeta mantiene el sistema visual del sitio.
- **Revisable**: sí — si aparece foto, reemplazar la tarjeta.

## 2026-07-06 — CTA principal: "Encontrá el profesional adecuado"
- **Qué**: reemplaza "Empezar orientación" en nav, hero y form de cierre (3 idiomas). Pedido directo de Lucía.
- **Revisable**: solo si Lucía lo cambia.

## 2026-07-06 — Foto de Lucía va en "Nuestra historia", no en el hero
- **Qué**: la foto descargada de WhatsApp (`assets/lucia-hero.jpeg`) reemplazó la tarjeta decorativa «dos que van» en la sección historia. El hero mantiene la ilustración original.
- **Razón**: decisión de Lucas — el texto de la sección habla de ella, tiene más sentido ahí. La foto además ya trae badges propios que hubieran duplicado los adornos flotantes del hero.
- **Alternativa descartada**: ponerla en el hero (se llegó a copiar el asset, no se editó el hero).
- **Revisable**: sí.

## 2026-07-06 — Copy "en español" → "en español e inglés"
- **Qué**: meta description, stat banner, card "Vivo en el exterior" y footer ahora ofrecen atención en español e inglés.
- **Razón**: pedido de Lucía — puede atender gente que hable inglés.
- **Revisable**: sí, si suman más idiomas de atención (el selector de UI es/en/pt es independiente de esto).

## 2026-07-06 — Sección psiquiatría/nutrición sin kicker
- **Qué**: nuevo copy de Lucía ("También contamos con psiquiatría y nutrición online"); se quitó el kicker manuscrito porque el título ya arranca con "También".
- **Revisable**: sí — restaurar el kicker es trivial si se extraña el ritmo visual.

## 2026-07-13 — Card "No sé qué necesito" primera en la grilla
- **Qué**: la card destacada (oscura, CTA "Empezar la orientación guiada") pasó del 6.º al 1.º lugar en "¿Qué estás buscando?". Pedido directo de Lucía.
- **Nota**: los badges manuscritos quedaron en las posiciones 3 y 6 (columna derecha); revisable si la grilla se ve desbalanceada.
- **Revisable**: solo si Lucía lo cambia.

## 2026-07-13 — Form de leads con Formspree (no Typeform, no Web3Forms)
- **Qué**: el form de cierre (nombre + WhatsApp) envía a Formspree vía fetch; a Lucía le llega cada lead por email y hay dashboard web para verlos.
- **Razón**: Formspree free (50 envíos/mes) mantiene el form ya diseñado (sin iframe) y suma dashboard. Lucas lo eligió sobre Web3Forms.
- **Alternativas descartadas**: Typeform (free ~10 respuestas/mes, iframe con branding ajeno que rompe el diseño); Web3Forms (250/mes gratis pero sin dashboard — era la otra candidata).
- **Pendiente**: crear el form en formspree.io con el email de Lucía (aún sin definir cuál) y pegar el endpoint en `const LEAD_ENDPOINT` (index.html).
- **Revisable**: sí — si superan 50 leads/mes, pasar a plan pago o migrar a Web3Forms.

## 2026-07-14 — La marca se escribe "Epuyen", sin diéresis
- **Qué**: se eliminó la diéresis (ü) de todas las apariciones del nombre de la marca en el sitio, README y memory. La grafía correcta es **Epuyen**, con u normal.
- **Razón**: corrección directa de Lucía — la ü era errónea. El logo ya lo escribía sin diéresis, el texto había quedado inconsistente.
- **Revisable**: no (es la grafía oficial de la marca). No reintroducir la ü en textos nuevos.

## 2026-07-17 — Todos los CTAs derivan a WhatsApp con mensaje por contexto (por el momento)
- **Qué**: cada botón/card del sitio linkea a `wa.me/34611457391` (WhatsApp de Lucía, +34 611 45 73 91) con un mensaje precargado distinto según la sección ("no sé qué necesito", nutrición, psiquiatría, trabajar con ustedes, etc.), localizado en es/en/pt vía claves `wa*` en `I18N` + atributo `data-wa`.
- **Razón**: pedido de Lucas — activar la conversión ya, sin esperar el flujo de orientación guiada ni Formspree.
- **Implicancias**: el CTA "Trabajá con nosotros" ya no abre el modal de postulación (el modal sigue en el código por si se reactiva); el form de cierre deriva a WhatsApp con el nombre precargado mientras `LEAD_ENDPOINT` diga `PENDIENTE`, y vuelve solo a Formspree al pegar el endpoint real.
- **Revisable**: sí — es explícitamente "por el momento"; cuando exista flujo propio (form de orientación / Formspree), redirigir ahí.

## 2026-07-17 — CTAs pill principales con tamaño unificado (.cta-eq)
- **Qué**: hero CTA1, "Hablar por WhatsApp" y "Quiero sumarme como profesional" comparten la clase `.cta-eq`: 57px de alto, `min-width:min(340px,100%)`, mismo padding y tipografía.
- **Razón**: pedido de Lucas — los botones del hero se veían de tamaños distintos (quedan apilados en desktop desde que el CTA se alargó, y con anchos dispares).
- **Alternativa descartada**: achicar los botones para que entren lado a lado (cambiaba la jerarquía visual sin que nadie lo pidiera).
- **Revisable**: sí — si se acorta el copy del CTA, pueden volver a convivir en una fila.

## 2026-07-17 — Hero tipográfico centrado, sin ilustración grande
- **Qué**: se quitó la ilustración "colorada" (`hero-person.png`) y todo su bloque visual (blobs, badge isotipo, tag, sparkle). El hero ahora es título centrado + sub + CTAs lado a lado, con las decos existentes (deco-chat/deco-check) chicas flanqueando el título a su altura y micro-puntos geométricos de color. Referencia visual elegida por Lucas: captura de un sitio ruso de psicología infantil (título centrado con palabras manuscritas y figuras pequeñas a los costados).
- **Razón**: a Lucía no la convencía la colorada (genérica); la idea del layout centrado con viñetas mini es de Lucas.
- **Alternativas descartadas**: foto real de Lucía en el hero, escena SVG patagónica «dos que van», imágenes IA (una con texto inglés quemado con typos, otra verde sin texto). Quedaron en `_hero-variants.html` por si se retoman.
- **Nota**: los SVGs ilustrativos que propuse (montañas, horizonte, corazón) fueron rechazados — las viñetas definitivas las va a crear Lucas. El degradado ambiental coral `amb-a` se eliminó (quedaba como "luz naranja" sin la ilustración).
- **Revisable**: las viñetas de los flancos sí (Lucas las reemplaza); el layout centrado, solo si Lucía lo pide.

## 2026-07-17 — La marca tampoco lleva acento: "Epuyen", ni ü ni é
- **Qué**: se corrigieron las 6 apariciones de "Epuyén"/"epuyén" que habían sobrevivido a la limpieza de la ü del 14/7 (claves `ab3` y `abQm` en es/en/pt de index.html).
- **Razón**: confirmación directa de Lucas ("Epuyen Salud, no le pongas acento"). La grafía oficial de la marca es **Epuyen Salud**, sin diéresis y sin tilde — aunque el pueblo de Chubut se escriba "Epuyén".
- **Revisable**: no. En textos nuevos escribir siempre "Epuyen".
