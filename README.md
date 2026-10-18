# 🛡️ OSINT Crimen + Cyber

**Toolkit OSINT dual para investigación de crimen organizado y ciberataques.**

[![Python](https://img.shields.io/badge/python-3.8%2B-blue.svg)]()
[![License: AGPL v3](https://img.shields.io/badge/License-AGPL%20v3-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)
[![Version](https://img.shields.io/badge/version-1.15.0-green.svg)]()

> ⚠️ **Aviso legal**: herramienta de investigación. Los resultados son coincidencias textuales automáticas y **no implican vinculación ni responsabilidad**. Verifica siempre en la fuente original. Ver [LEGAL.md](LEGAL.md).

![TheCondor](image(1).jpg)

---

## 🇬🇧 English summary

A dual-mode OSINT toolkit (Python 3.8+) for **organized crime** and **cyber threat intelligence**. It aggregates 15+ public sources (Wikidata, GDELT, MITRE ATT&CK, OFAC, UN, OpenSanctions, URLhaus, Feodo, Ransomware.live, 46 cybersecurity feeds, passive Telegram scraping), classifies findings with an Andrómeda-style ruleset (health 🏥 / energy ⚡ threat detection included) and serves a self-hosted web panel with world map, charts, translation and persistent history. **Free and open source under AGPL-3.0.** See [LEGAL.md](LEGAL.md) for GDPR notes.

---

## 🧭 ¿Qué es esto?

OSINT Crimen + Cyber es una herramienta de línea de comandos y panel web pensada para **analistas, investigadores y periodistas** que necesiten consolidar información pública sobre:

- **Crimen organizado**: cárteles, maras, mafias, grupos terroristas, guerrillas.
- **Ciberataques**: APTs, ransomware, botnets, DDoS, hacktivismo, campañas conocidas.

Cada búsqueda consulta en paralelo decenas de fuentes públicas, **deduplica**, **clasifica** las entidades y **guarda la evidencia con URL de origen** para que puedas verificarla.

### Para qué sirve (y para qué no)

✅ **Sirve para**:
- Consolidar información pública dispersa sobre un grupo concreto.
- Detectar amenazas a **sectores críticos** (salud, energía) en mensajes de Telegram.
- Generar **dossiers HTML** con fuentes verificables.
- Monitorizar la actividad de grupos hacktivistas conocidos.
- Alimentar una base de datos local con IOCs (IPs, dominios, CVE, hashtags).

❌ **No sirve para**:
- Atribuir delitos (una coincidencia textual no es una prueba).
- Vigilancia masiva de personas.
- Sustituir a un analista humano.
- Sustituir a las fuentes originales (siempre enlaza a ellas).

---

## ✨ Características

### 🔍 Búsqueda multi-fuente
- **15+ fuentes integradas** consultadas en paralelo (ver tabla abajo).
- **Deduplicación** por URL y por nombre normalizado.
- **Normalización** de variantes (`LockBit` = `Lock Bit` = `LockBit3`).
- **Diccionario de crackers** (~600 grupos) que expande la búsqueda con variantes y **puntúa** los resultados.

### 🧠 Clasificación estilo Andrómeda
- Detección automática de **tipo de ataque**: DDoS, botnet, ransomware, malware, phishing, exploit, filtración…
- **Amenazas a la salud** 🏥 y a la **energía** ⚡ mediante listas de palabras clave en español, inglés, ruso y árabe.
- **IOCs extraídos** de los mensajes: IPs, dominios, CVE, hashtags, países.

### 📡 Telegram pasivo
- Lectura **pasiva** de canales **públicos** (`t.me/s/<canal>`). Sin cuenta, sin unirse, sin escribir.
- **Metadatos** del canal: ID interno, fecha de creación, renombres, contadores, verificado.
- **Historia de grupos**: primera/última aparición, actividad por mes, mapa de calor día×hora, co-menciones, picos.
- **Descubrimiento pasivo** por nombre cuando no tienes el canal.
- **Escáner en segundo plano** con barra de progreso, ETA y botón de parada.

### 🗺️ Panel web
- **Mapa mundial** interactivo (zoom, arrastrar, filtro, exportar SVG).
- **Gráficos** de actividad, tipos, fuentes, grupos, canales.
- **Historial persistente** con snapshots (puedes abrir búsquedas antiguas sin volver a consultar fuentes).
- **Traducción** de evidencias a ES/EN/PT (Google Translate + MyMemory como respaldo).
- **Modo ahorro** para equipos modestos (sin animaciones ni desenfoques).

### 📤 Exportes
- **Dossier HTML** por entidad (con fuentes enlazadas).
- **GraphML** de co-ocurrencias (abrible en Gephi / Cytoscape).
- **JSON** completo de la base.
- **CSV** de mensajes de Telegram.
- **API JSON** (`/api/mensajes`) compatible con la estructura de eventos de Andrómeda.

---

## 🚀 Instalación rápida

### Requisitos
- **Python 3.8+** (probado en 3.10–3.12).
- **Nada más** es obligatorio: la herramienta usa solo la librería estándar.

### Dependencias opcionales (recomendadas)
Mejoran el scraper de Telegram y la velocidad:

```bash
pip install -r requirements.txt
```

Si no las tienes, la herramienta funciona igual (con `urllib` y un parser propio).

### Clonar y ejecutar

```bash
git clone https://github.com/Condor2026/osint-crimen-cyber
cd osint-crimen-cyber
python osint_crimen_cyber.py
```

Para el panel web:

```bash
python osint_crimen_cyber.py --web --port 8765
```

Abre `http://127.0.0.1:8765` en el navegador.

---

## 🎯 Uso rápido

### Terminal

```bash
# Buscar en modo crimen (por defecto)
python osint_crimen_cyber.py --buscar "Cartel de Sinaloa"

# Buscar en modo cyber
python osint_crimen_cyber.py --buscar "LockBit" --mode cyber

# Ver ficha de una entidad
python osint_crimen_cyber.py --report 42

# Generar dossier HTML
python osint_crimen_cyber.py --dossier 42 dossier_lockbit.html

# Ver mensajes de Telegram (estilo Andrómeda)
python osint_crimen_cyber.py --feed --feed-group KillNet --feed-limit 30

# Estadísticas de los mensajes
python osint_crimen_cyber.py --feed-stats

# Historia de un grupo
python osint_crimen_cyber.py --group KillNet

# Exportar base completa a JSON
python osint_crimen_cyber.py --export dump.json

# Exportar grafo de co-ocurrencias
python osint_crimen_cyber.py --export-graph grafo.graphml
```

### Panel web

```bash
python osint_crimen_cyber.py --web --port 8765
```

Rutas principales:
- `/` — buscador y estadísticas
- `/historial` — memoria de búsquedas
- `/telegram` — panel único: escáner, fichas de grupo, gráficos, mensajes, canales
- `/e/<id>` — ficha de entidad
- `/dossier/<id>` — dossier HTML descargable
- `/api/mensajes` — API JSON de mensajes clasificados

### Telegram pasivo

1. Crea un archivo `tg_channels.txt` con un canal público por línea (sin `@`, sin `https://`).
2. Impórtalos:

```bash
python osint_crimen_cyber.py --tg-import
```

3. Escanea (modo pasivo, respeta límites automáticamente):

```bash
python osint_crimen_cyber.py --tg-update --tg-pages 0 --tg-workers 0
```

> Las invitaciones privadas (`t.me/+hash`) **no se pueden leer** con este método. Solo canales públicos.

---

## 📚 Fuentes integradas

| Fuente | Modo | Tipo | Actualización |
|---|---|---|---|
| [Wikidata](https://www.wikidata.org/) | Crime + Cyber | Entidades | En vivo |
| [Wikipedia](https://www.wikipedia.org/) | Crime + Cyber | Prensa | En vivo |
| [GDELT](https://www.gdeltproject.org/) | Crime + Cyber | Noticias | En vivo |
| [Google News](https://news.google.com/) | Crime + Cyber | Noticias | En vivo |
| [FBI Wanted](https://www.fbi.gov/wanted) | Crime | Personas buscadas | En vivo |
| [INTERPOL](https://www.interpol.int/) | Crime | Notificaciones rojas | En vivo |
| [ONU (Consolidated)](https://scsanctions.un.org/) | Crime | Sanciones | Bajo demanda |
| [OFAC SDN](https://sanctionssearch.ofac.treas.gov/) | Crime | Sanciones | Bajo demanda |
| [OpenSanctions](https://www.opensanctions.org/) | Crime | Sanciones | Bajo demanda |
| [RSS oficiales](https://www.justice.gov/) | Crime | Prensa | En vivo |
| [Ransomware.live](https://www.ransomware.live/) | Cyber | Víctimas | En vivo |
| [Ransomwatch](https://github.com/joshhighet/ransomwatch) | Cyber | Archivo (2020–2025) | Congelada |
| [RansomLook](https://www.ransomlook.io/) | Cyber | Grupos | En vivo |
| [CISA KEV](https://www.cisa.gov/known-exploited-vulnerabilities-catalog) | Cyber | Vulnerabilidades | En vivo |
| [URLhaus](https://urlhaus.abuse.ch/) | Cyber | URLs maliciosas | En vivo |
| [Feodo Tracker](https://feodotracker.abuse.ch/) | Cyber | IPs C2 | En vivo |
| [MITRE ATT&CK](https://attack.mitre.org/) | Cyber | Grupos, malware, campañas | En vivo |
| 46 feeds de ciberseguridad | Cyber | Prensa | En vivo |
| **Telegram** (pasivo) | Cyber | Mensajes de canales públicos | Local |

Todas las fuentes son públicas y de acceso libre. Cada resultado enlaza a su **URL original**.

---

## 🏗️ Cómo funciona

```
consulta → expansión de variantes → 15+ fuentes en paralelo
         → deduplicación → SQLite local → clasificación
         → terminal / panel web / dossier / GraphML / JSON
```

**Filosofía del proyecto**:
1. **Nunca inventar datos**: si una fuente falla, se avisa; no se rellena con "probables".
2. **Nunca descartar por score**: el diccionario de crackers **puntúa**, no filtra.
3. **Enlazar siempre a la fuente original**: cada evidencia tiene su URL.
4. **Respetar los servidores**: caché de 1 h, un solo hilo por URL, backoff exponencial, pausa automática si Telegram responde 429.

---

## 🧪 Modo Crimen vs Modo Cyber

| | **Crime** | **Cyber** |
|---|---|---|
| **Fuentes** | Wikidata, Wikipedia, GDELT, Google News, FBI, INTERPOL, ONU, OFAC, OpenSanctions, RSS oficiales | Wikidata, Wikipedia, GDELT, Google News, Ransomware.live, RansomLook, CISA KEV, URLhaus, Feodo, MITRE, 46 feeds, Telegram |
| **Entidades típicas** | Cárteles, maras, mafias, terroristas, guerrillas | APTs, ransomware, botnets, hacktivistas, campañas |
| **Colores por tipo** | Azul (crime) | Violeta (grupos), rojo (ransomware), naranja (malware), cian (botnets), amarillo (DDoS), verde (campañas) |
| **Clasificación Andrómeda** | — | ✅ Sí (salud, energía, tipo de ataque) |
| **Telegram pasivo** | — | ✅ Sí |

Cambia de modo con `--mode crime|cyber` o desde el botón del panel web.

---

## 🧠 Diccionario de crackers

El archivo `cracker_dict.txt` contiene ~600 nombres de grupos, APTs, ransomware y hacktivistas. Se usa para:
1. **Expandir** la búsqueda con variantes (`DarkStormTeam` → `Dark Storm Team`, `dark_storm_team`…).
2. **Puntuar** los resultados (los que coinciden suben al principio; los que no, quedan neutros, no se descartan).

```bash
python osint_crimen_cyber.py --dict-stats
python osint_crimen_cyber.py --dict-test KillNet
```

---

## 📄 Exportes

```bash
python osint_crimen_cyber.py --dossier 42 dossier.html
python osint_crimen_cyber.py --export-graph grafo.graphml
python osint_crimen_cyber.py --export dump.json
python osint_crimen_cyber.py --history-export historial.json
```

---

## ⚖️ Legal y privacidad

Esta herramienta **no aloja ni recopila datos personales por sí misma**. Es un cliente que consulta fuentes públicas y guarda los resultados **localmente en tu máquina**. Si la ejecutas, **tú** eres el responsable del tratamiento bajo RGPD.

👉 **Lee [LEGAL.md](LEGAL.md)** antes de usarla con datos de personas.

---

## 🤝 Contribuir

Lee [CONTRIBUTING.md](CONTRIBUTING.md) para:
- Añadir fuentes nuevas.
- Reportar bugs de scraping.
- Mejorar la clasificación.
- Traducir la interfaz.

Antes de abrir un PR, asegúrate de no commitear archivos con datos personales (`.db`, `.jsonl`, `.xml`). Están en `.gitignore`.

---

## 🔒 Seguridad

Si encuentras una vulnerabilidad, **no abras un issue público**. Lee [SECURITY.md](SECURITY.md).

---

## 💼 Servicios

El autor ofrece servicios de inteligencia sobre esta base:

- **Informes CTI a medida** (KillNet, LockBit, APT28… con MITRE ATT&CK e IOCs).
- **Monitorización continua** con alertas.
- **Dossiers** personalizados por grupo o sector.
- **Formación** en OSINT.
- **Desarrollo de tooling a medida**.

📬 **Contacto comercial**: KiraSecurity@proton.me

---

## 📜 Licencia

**GNU Affero General Public License v3.0 (AGPL-3.0)**. Ver [LICENSE](LICENSE).

- ✅ Puedes usar, copiar, modificar y distribuir el código.
- ✅ Puedes usarlo comercialmente.
- ⚠️ Si lo modificas y lo distribuyes (o lo ofreces como servicio en red), **debes publicar tus cambios bajo la misma licencia**.
- ⚠️ No hay garantía.

Si necesitas una **licencia comercial sin las obligaciones de AGPL**, contacta con el autor.

---

## 🙏 Agradecimientos

- A la comunidad OSINT por mantener las fuentes públicas que hacen posible este proyecto.
- A todos los que reportéis bugs y añadáis fuentes.

---

**Hecho con 🛡️ por un analista, para analistas.**
