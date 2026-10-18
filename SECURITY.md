# 🔒 Política de seguridad

## Versiones soportadas

| Versión | Soportada |
|---|---|
| 1.15.x | ✅ |
| < 1.15 | ❌ |

## Reportar una vulnerabilidad

**No abras un issue público** para reportar vulnerabilidades de seguridad.

Envía un email a:

📬 **KiraSecurity@proton.me**

Incluye, si es posible:

- Descripción del problema.
- Pasos para reproducirlo.
- Versión afectada.
- Impacto potencial.
- Sugerencia de mitigación (opcional).

**Compromiso de respuesta**:
- Acuse de recibo: ≤ 72 h.
- Evaluación inicial: ≤ 7 días.
- Parche o mitigación: según gravedad (crítico ≤ 30 días).

## Alcance

**En alcance**:
- Ejecución remota de código (RCE).
- Inyección SQL / XSS / SSRF en el panel web.
- Fugas de información sensible.
- Bypass de la protección CSRF del panel.
- Denegación de servicio explotable.

**Fuera de alcance**:
- Vulnerabilidades en dependencias de terceros (repórtalas al proyecto correspondiente).
- Rate-limiting de las fuentes externas.
- Ingeniería social.
- Ataques físicos.
- Configuraciones inseguras por parte del usuario (ej. exponer el panel a internet sin auth).

## Buenas prácticas para usuarios

- **No expongas** el panel web a internet sin autenticación. Usa `127.0.0.1` o una VPN.
- **No commitees** tu `osint_crimen.db` ni los archivos de sanciones.
- **Mantén** las dependencias actualizadas.
- **Revisa** los cambios antes de actualizar.

## Reconocimiento

Los reporters responsables serán acreditados en el `CHANGELOG.md` (si lo desean).
