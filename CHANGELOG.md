# Changelog

Formato basado en [Keep a Changelog](https://keepachangelog.com/es-ES/1.1.0/).
Versionado basado en [Semantic Versioning](https://semver.org/lang/es/).

## [1.15.0] - 2026-01-XX

### Añadido
- Arranque compatible con Python 3.8+ (fix de f-string con barra invertida).
- Lista de canales de Telegram leída tal cual (sin filtrar).
- Scraping con la lógica de Andrómeda (JSON → directo → RSS).
- Sin límites: todas las páginas y un hilo por canal.
- Metadatos del canal: ID, fecha de creación, renombres, contadores, verificado.
- Panel único `/telegram` con escáner, gráficos, mensajes, grupos y canales.
- Modo ahorro (sin animaciones ni desenfoques).
- Botones POST con token propio.

### Cambiado
- Fusionadas las rutas `/grupos`, `/grupo`, `/mensajes` y `/escaner` en `/telegram` (con redirecciones).

### Corregido
- Falso error de "origen no permitido" en los botones del panel.

## [1.14.0] - 2025-12-XX

### Añadido
- Escáner de Telegram desde el panel (botón "Escanear todos los canales").
- Modos: incremental, forzar, profundo.
- Barra de progreso, ETA y botón Parar.

## [1.13.0] - 2025-11-XX

### Añadido
- Clasificación estilo Andrómeda de mensajes de Telegram.
- Detección de amenazas a salud 🏥 y energía ⚡.
- `/mensajes`, `/api/mensajes`, `/mensajes.csv`.

## [1.12.0] - 2025-10-XX

### Añadido
- Telegram como fuente del buscador cyber.
- Descubrimiento pasivo de canales.
- `/grupos`, `/grupo` con gráficos.

## [1.11.0] - 2025-09-XX

### Añadido
- Lectura pasiva de canales públicos de Telegram.
- Historia de grupos con línea de tiempo.
- CLI: `--tg-update`, `--tg-stats`, `--tg-import`, `--group`, `--groups`.

## [1.10.1] - 2025-08-XX

### Añadido
- Colores por tipo de entidad cyber (grupos, ransomware, malware, botnets, DDoS, campañas).

## [1.10.0] - 2025-07-XX

### Añadido
- Memoria de búsquedas con snapshots (`search_hits`).
- Historial secundario en panel web y terminal.

## [1.9.0] - 2025-06-XX

### Añadido
- Diccionario de crackers (`cracker_dict.txt`).
- Fix de GDELT con headers de navegador.

### Corregido
- RSS sin tope duro.

## [1.8.0] - 2025-05-XX

### Añadido
- CSP + Permissions-Policy en el panel web.
- SPARQL de Wikidata con QIDs validados.

### Cambiado
- Ransomwatch marcada como archivada.
