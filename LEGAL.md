# ⚖️ Aviso legal, privacidad y RGPD

**Última actualización**: 18-10-2026
**Proyecto**: OSINT Crimen + Cyber
**Mantenedor**: Condor2026 (https://github.com/Condor2026)

---

## 1. Qué es este proyecto (y qué no)

**OSINT Crimen + Cyber** es una **herramienta de software libre** publicada en GitHub. No es un servicio online, no es una plataforma alojada, no recopila datos por sí misma.

La herramienta:
- Se **ejecuta en tu propio ordenador**.
- Consulta **fuentes públicas** de internet.
- Guarda los resultados **localmente** en una base de datos SQLite (`osint_crimen.db`).
- **No envía** los resultados a ningún servidor del autor.

---

## 2. Base legal para el tratamiento de datos personales

### 2.1. El mantenedor del repositorio

Como **autor y distribuidor del código**, el mantenedor:

- **No trata datos personales** de terceros al publicar el código.
- **No recibe** los datos que tú introduces o generas al ejecutar la herramienta.
- **No opera** ninguna instancia alojada del servicio.

La única excepción sería si el mantenedor alojara una **demo pública**; en tal caso, esa demo tendría su propio aviso de privacidad.

### 2.2. El usuario que ejecuta la herramienta

Si ejecutas esta herramienta, **tú** te conviertes en el **responsable del tratamiento** (Art. 4.7 RGPD) de los datos personales que aparezcan en tus resultados.

**Base legal recomendada**: **Interés legítimo** (Art. 6.1.f RGPD), para las siguientes finalidades:

- Investigación periodística.
- Análisis de amenazas (threat intelligence).
- Concienciación y divulgación en ciberseguridad.
- Investigación académica.

**No** se recomienda su uso para:
- Marketing directo o prospección comercial no solicitada.
- Vigilancia masiva de personas.
- Perfilado automatizado con efectos jurídicos.
- Tratamiento de datos de categorías especiales (salud, ideología, etc.) sin base específica.

### 2.3. Fuentes de datos personales

La herramienta consulta **fuentes públicas y oficiales**:

- OFAC SDN (https://sanctionssearch.ofac.treas.gov/) — dominio público.
- ONU Consolidated (https://scsanctions.un.org/) — acceso público.
- FBI Wanted (https://www.fbi.gov/wanted) — API pública.
- INTERPOL Red Notices (https://www.interpol.int/) — notificaciones rojas públicas.
- OpenSanctions (https://www.opensanctions.org/) — agregador de fuentes públicas.
- Wikidata (CC0), Wikipedia (CC BY-SA), MITRE ATT&CK, GDELT, Google News, RSS.

Todas ellas son **públicas**, y su reutilización está permitida por sus respectivas licencias o por su naturaleza oficial.

---

## 3. Datos que la herramienta almacena localmente

Cuando ejecutas la herramienta, en tu propio ordenador se guarda:

- `osint_crimen.db` — entidades, evidencias, sanciones, historial. Puede contener nombres de personas.
- `opensanctions_crime.jsonl` — volcado de sanciones (bajo demanda).
- `un_consolidated.xml` — lista ONU (bajo demanda).
- `ofac_sdn.xml` — lista OFAC (bajo demanda).
- `watch_state/` — estado de la watchlist.
- `tg_channels.txt` — configuración de canales.

**Tú eres el único responsable de estos archivos**. Se recomienda:

- **No commitearlos** en Git (ya están en `.gitignore`).
- **No compartirlos** sin anonimizar.
- **Borrar** los datos que ya no necesites (Art. 5.1.e RGPD — limitación del plazo de conservación).
- **Cifrar** el disco si trabajas con datos sensibles (BitLocker, LUKS, FileVault).

---

## 4. Traducción opcional (terceros)

La herramienta incluye un **botón de traducción** en el panel web y la opción `--feed-translate` en terminal. Esta función:

- **Solo se activa si el usuario lo pulsa/usa**.
- **Envía el texto de la evidencia** a Google Translate (API no oficial `translate.googleapis.com`) y MyMemory (respaldo).
- **Requiere consentimiento explícito** la primera vez (confirmación en el navegador).

**No uses la traducción** con material sensible o reservado. Para entornos profesionales, considera un traductor **local** (Argos Translate, LibreTranslate).

---

## 5. Derechos de los interesados (RGPD)

Si una persona aparece en tu base de datos local y ejerce sus derechos (acceso, rectificación, supresión, oposición, limitación, portabilidad), **tú** debes atender la solicitud.

**Recomendación**: si publicas o compartes resultados, incluye siempre:

- La **fuente original** de cada dato (URL).
- Un **aviso** de que la información proviene de una fuente pública.
- Un **email de contacto** para solicitudes de rectificación o supresión.

Como el mantenedor del repositorio **no tiene acceso** a tu base local, no puede atender esas solicitudes por ti.

---

## 6. Limitación de responsabilidad

El software se distribuye **"tal cual"**, sin garantía de ningún tipo (ver LICENSE, sección 15–17). En particular:

- Los resultados son **coincidencias textuales automáticas** y **no implican vinculación, culpabilidad ni responsabilidad** de las personas o entidades mencionadas.
- El mantenedor **no se hace responsable** del uso que terceros hagan de la herramienta.
- El usuario es el **único responsable** del cumplimiento normativo en su jurisdicción.

---

## 7. Buenas prácticas recomendadas

✅ **Haz**:
- Verificar cada dato en la fuente original antes de publicarlo.
- Citar siempre la fuente y la fecha.
- Anonimizar cuando publiques resultados.
- Respetar los plazos de conservación.
- Usar la herramienta para fines de investigación, no de vigilancia masiva.

❌ **No hagas**:
- Publicar nombres de personas sin contexto ni fuente.
- Usar los resultados para acosar, doxxear o discriminar.
- Alojar una demo pública sin aviso de privacidad.
- Vender los datos personales obtenidos.

---

## 8. Contacto

Para cuestiones legales o de privacidad **sobre el repositorio** (no sobre tu base local):

📬 **KiraSecurity@proton.me**

Para cuestiones de **seguridad del software**, ver SECURITY.md.

---

## 9. Cambios en este aviso

Este aviso puede actualizarse. La fecha de "Última actualización" al inicio del documento refleja la versión vigente. Los cambios sustanciales se anunciarán en el CHANGELOG y en las *releases* de GitHub.
