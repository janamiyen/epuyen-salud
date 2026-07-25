# Backlog — Epuyen Salud (web)

## P1
- Crear form en Formspree con el email de Lucía y pegar el endpoint en `const LEAD_ENDPOINT` (index.html) — mientras tanto el submit deriva a WhatsApp con el nombre precargado (ya no muestra error). En verificación entre Lucas y Lucía (14/7/2026)
- **Foto de Lucía sin emoticones** (sección "Nuestra historia"): Lucía pidió sacarle las decoraciones/emoticones que rodean su foto (`lucia-hero.jpeg` es una composición ilustrada con burbujas de chat, cámara, checklist, cintillo, etc.). Lucas la hace con GPT → cuando la tenga, swappear el asset. (Nota: la taza en la foto dice "EPUYÉN" con diéresis, error que Lucía ya marcó)
- Revisar nav en anchos 800–980px con el CTA nuevo más largo

## P2
- **Flor del hero (2026-07-25)** — definir **opacidad final**: desktop está en `.95` (fuerte para un fondo; puede competir con el título en anchos ~980–1180px); mobile en `.22` (placeholder). Cuando Lucas confirme en el celu, fijar valores lindos y consistentes
- **Optimizar el PNG** de la flor (`epuyen-fondo-hero.png`, ~1.5MB) → WebP o quantize, sin perder nitidez (importa en mobile por datos)
- ¿Sacar la **redundancia "sin bots"**? Aparece 2 veces cerca en el banner: la línea Dancing Script (`bnSub`) + el ítem 🤝 (`bf1d`). Se dejó porque la frase la pidió Lucía; validar con Lucas
- Wirear los links del nav como anclas a secciones (`#historia` ya existe)
- Revisar si la grilla "¿Qué estás buscando?" quedó balanceada con los badges en posiciones 3 y 6

## P3
- (vacío)

## Done reciente
- 2026-07-25: banner con 3 ítems (Atención humana / Español e inglés / 24–48 h) en es/en/pt + saca "+34 profesionales" en los 3 lugares + flor pasionaria de fondo en el hero (fondo negro recortado a transparencia, resolución nativa, detrás del título, izq, visible en mobile). Commit `f0c1235` pusheado a prod (pedido de Lucía vía Lucas)
- 2026-07-17: todos los CTAs/cards linkean a WhatsApp de Lucía con mensaje por contexto en es/en/pt; botones pill principales con tamaño unificado (`.cta-eq`); form de cierre deriva a WhatsApp mientras no haya endpoint Formspree — testeado local por Lucas, commit `91cb1f8` pusheado a prod
- 2026-07-14: marca corregida a "Epuyen" sin diéresis en sitio, README y memory (corrección de Lucía)
- 2026-07-13: card "No sé qué necesito" movida al 1.º lugar de la grilla (pedido de Lucía)
- 2026-07-13: form de cierre cableado a Formspree (fetch + honeypot + estados enviando/gracias/error es/en/pt) — falta solo el endpoint real
- 2026-07-06: sección "Nuestra historia" es/en/pt + bajada "sin bots" en bloque verde + CTA "Encontrá el profesional adecuado"
