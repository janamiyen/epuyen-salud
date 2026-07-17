# Backlog — Epuyen Salud (web)

## P1
- Crear form en Formspree con el email de Lucía y pegar el endpoint en `const LEAD_ENDPOINT` (index.html) — mientras tanto el submit deriva a WhatsApp con el nombre precargado (ya no muestra error). En verificación entre Lucas y Lucía (14/7/2026)
- Validar con Lucía la sección "Nuestra historia" (tono, visual, ¿foto?)
- Revisar nav en anchos 800–980px con el CTA nuevo más largo

## P2
- Wirear los links del nav como anclas a secciones (`#historia` ya existe)
- Revisar si la grilla "¿Qué estás buscando?" quedó balanceada con los badges en posiciones 3 y 6

## P3
- (vacío)

## Done reciente
- 2026-07-17: todos los CTAs/cards linkean a WhatsApp de Lucía con mensaje por contexto en es/en/pt; botones pill principales con tamaño unificado (`.cta-eq`); form de cierre deriva a WhatsApp mientras no haya endpoint Formspree — testeado local por Lucas, commit `91cb1f8` pusheado a prod
- 2026-07-14: marca corregida a "Epuyen" sin diéresis en sitio, README y memory (corrección de Lucía)
- 2026-07-13: card "No sé qué necesito" movida al 1.º lugar de la grilla (pedido de Lucía)
- 2026-07-13: form de cierre cableado a Formspree (fetch + honeypot + estados enviando/gracias/error es/en/pt) — falta solo el endpoint real
- 2026-07-06: sección "Nuestra historia" es/en/pt + bajada "sin bots" en bloque verde + CTA "Encontrá el profesional adecuado"
