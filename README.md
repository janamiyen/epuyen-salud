# Epüyen Salud — Landing

Sitio web (home) de **Epüyen Salud**: acompañamiento en salud mental, orientación y bienestar, 100% online y en español. Multilenguaje **ES / EN / PT**.

## Stack
- HTML + CSS (estilos inline + media queries) + JavaScript vanilla. Sin frameworks ni build.
- Fuentes vía Google Fonts (Caveat, Dancing Script, Hanken Grotesk, Newsreader).
- i18n propio (`const I18N` con es/en/pt + `applyI18n()` sobre `[data-i18n]`).

## Estructura
```
web/
├── index.html        # toda la home
└── assets/           # logo, isotipo e ilustraciones del hero
```

## Desarrollo
Es estático: abrí `index.html` en el navegador, o serví la carpeta con cualquier server estático.

## Secciones
Hero · Stat banner · ¿Qué estás buscando? · Psiquiatría y nutrición · Cómo funciona · Equipo · Trabajá con nosotros (con formulario para profesionales) · CTA de cierre · Footer.

## Pendiente
- Foto/ilustración final del hero (hoy usa ilustración de marca).
- Conectar botones reales (WhatsApp, navegación, formulario del paciente).
- Backend del formulario "Trabajá con nosotros" (hoy abre `mailto:`; conviene Formspree / Sheet / Supabase).
- Deploy (Vercel).
