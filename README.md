# HUGO

Núcleo conversacional independiente de UGO.

## P0

El primer hito sólo pasa con una prueba runtime real:

1. tocar el orbe;
2. decir **Hola Hugo**;
3. recibir respuesta audible;
4. decir **Necesito un plomero** sin recargar;
5. recibir una segunda respuesta audible manteniendo el contexto.

Este repositorio se desarrolla independientemente de `sebastisnzoth/ugo-admin-panel`, que se usa sólo como referencia. No debe modificarse desde este trabajo.

## Arquitectura inicial

- Frontend: React + Vite + TypeScript
- Voz: Gemini Live mediante WebSocket
- Seguridad: `GEMINI_API_KEY` sólo en backend
- Autenticación Live: token efímero emitido por `/api/live-token`
- Diagnóstico visible: token, WebSocket, setup, micrófono, audio, modelo y último error

## Variables

- `GEMINI_API_KEY` — sólo servidor
- `GEMINI_LIVE_MODEL` — opcional; por defecto `gemini-3.8-live`

## Desarrollo

```bash
npm install
npm run dev
```

Para probar también la función `/api/live-token`, usar un runtime que ejecute las funciones de `api/` (por ejemplo Vercel Dev) con `GEMINI_API_KEY` configurada.

## Seguridad

Nunca incluir la API key de Gemini en variables `VITE_*`, bundle frontend, logs o respuestas HTTP.
