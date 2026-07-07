# Estado actual — Epüyen Salud (web)

**Última sesión: 2026-07-06**

## Qué se hizo
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
- Validar con Lucía cómo quedó su foto en "Nuestra historia"
- Revisar nav en ~800–980px con el CTA nuevo más largo
- Links del nav siguen siendo spans sin href; `#historia` existe como ancla
