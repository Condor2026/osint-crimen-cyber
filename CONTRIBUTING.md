# 🤝 Contribuir a OSINT Crimen + Cyber

¡Gracias por querer contribuir! Este documento explica cómo hacerlo.

## Código de conducta

- Sé respetuoso.
- No publiques datos personales de terceros.
- No uses la herramienta para acosar, doxxear o discriminar.
- Las contribuciones deben tener fines de investigación o defensa.

## Cómo proponer cambios

### 1. Abre un issue primero

Antes de escribir código, abre un issue explicando:
- Qué quieres cambiar y por qué.
- Si es una fuente nueva, enlace a la fuente y justifica que es pública.
- Si es un bug, pasos para reproducirlo.

### 2. Haz un fork y una rama

```bash
git checkout -b feature/nueva-fuente-xyz
```

### 3. Estilo de código

- **Python 3.8+** compatible.
- **Sin dependencias nuevas obligatorias** (opcionales sí, con fallback).
- **Docstrings** en las funciones públicas.
- **Comentarios** en español (el resto del código está en español).
- **Sin prints de debug** en el código final.

### 4. Antes de commitear

Comprueba que **no** estás subiendo:
- `osint_crimen.db`
- `*.jsonl`, `*.xml` de sanciones
- `watch_state/`
- Archivos con datos personales reales

Ya están en `.gitignore`, pero verifica:

```bash
git status
```

### 5. Añadir una fuente nueva

Toda fuente nueva debe:

1. **Ser pública** y de acceso libre (sin API key obligatoria, o con key gratuita).
2. **Tener una URL estable** de origen.
3. **Respetar los servidores**: caché, un hilo por URL, backoff exponencial.
4. **Devolver el formato estándar**:

```python
{
    "name": "...",
    "type": "person|org|unknown",
    "description": "...",
    "url": "...",
    "title": "...",
    "snippet": "...",
    "aliases": [...],       # opcional
    "country": "...",       # opcional
    "sanction": {...},      # opcional
}
```

Estructura típica:

```python
@register_source
class MiFuenteSource(Source):
    slug = "mi_fuente"
    name = "Mi Fuente"
    category = MODE_CYBER
    description = "Descripción breve."
    full_scan = False

    def search(self, query, limit=25):
        raw = http_get("https://api.ejemplo.com/search", params={"q": query})
        data = json.loads(raw)
        out = []
        for item in data.get("results", [])[:limit]:
            out.append({
                "name": item["title"],
                "type": "unknown",
                "description": item.get("desc", ""),
                "url": item["url"],
                "title": f"Mi Fuente · {item['id']}",
                "snippet": item.get("desc", ""),
            })
        return out
```

### 6. Añadir un canal de Telegram

Edita `tg_channels.txt` (uno por línea, sin `@` ni `https://`). **Solo canales públicos**.

### 7. Enviar el PR

- Describe el cambio.
- Enlaza al issue relacionado.
- Acepta que tu contribución se publique bajo AGPL-3.0.

## Qué buscamos

- 🆕 Fuentes nuevas (públicas, verificables).
- 🐛 Bugs de scraping.
- 🎨 Mejoras de UI del panel web.
- 📚 Documentación.
- 🌐 Traducciones (EN, PT, FR, IT).
- 🧪 Tests (aún no hay, ¡ayuda!).
- ⚡ Optimizaciones de rendimiento.

## Qué NO buscamos

- ❌ Dependencias nuevas obligatorias.
- ❌ Scrapers de fuentes privadas o que violen ToS.
- ❌ Funciones de vigilancia masiva.
- ❌ Datos personales commiteados.
- ❌ Cambios de licencia.
