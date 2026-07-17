# Estado actual — Epuyen Salud (web)

**Última sesión: 2026-07-17**

## Qué se hizo (2026-07-17)
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
