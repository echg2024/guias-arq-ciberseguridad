# Guía Técnica para flujos de Autenticación y autorización

# 1. Introducción
- **Importancia de la seguridad en aplicaciones clínicas.**
- **Riesgos comunes por mala implementación de autenticación/autorización.**

# 2. Componentes Clave

## 2.1 OAuth 2.0
- **Qué es:** Marco de autorización delegada. Permite a aplicaciones acceder a recursos protegidos sin manejar credenciales del usuario directamente.
- **Roles:**
  - Resource Owner
  - Client
  - Authorization Server
  - Resource Server
- **Flujos comunes:**
  - Authorization Code (recomendado para apps web).
  - Client Credentials (para servicios sin usuario).
  - Device Code / PKCE (para móviles o dispositivos con UI limitada).

## 2.2 OpenID Connect (OIDC)
- **Qué es:** Extensión de OAuth 2.0 para autenticación. Agrega capa de identidad sobre el token.
- **Usos:** Inicio de sesión único (SSO), federación de identidad.
- **Tokens usados:**
  - `id_token` (JWT)
  - `access_token`

## 2.3 Identity Provider (IdP)
- **Qué es:** Servicio que verifica identidad y emite tokens de acceso y/o identidad.
- **Ejemplos:** Keycloak, Azure AD, Okta, Auth0.

## 2.4 JSON Web Token (JWT)
- **Qué es:** Formato compacto y firmado digitalmente para transmitir claims (atributos).
- **Estructura:** `header.payload.signature` (base64url)
- **Tipos:**
  - `id_token`: identidad.
  - `access_token`: autorización.
  - `refresh_token`: renovar sesión.

# 3. Recomendaciones Técnicas

## 3.1 Backend
- Validar firma de los JWT usando la clave pública del IdP.
- Verificar los claims obligatorios:
  - `iss` (issuer): debe coincidir con el IdP esperado.
  - `aud` (audience): debe ser el ID del cliente.
  - `exp`, `iat`, `nbf`: validar tiempo de expiración.
- Rotación de claves públicas (JWKS): actualizar automáticamente.
- Evitar confiar en tokens no validados por backend.

## 3.2 Frontend
- Usar **PKCE** (Proof Key for Code Exchange) para flujos de autorización en apps públicas.
- No almacenar `access_token` en **localStorage** → preferir memoria volátil o `sessionStorage` si es estrictamente necesario.
- Evitar exponer secretos del cliente en el frontend.
- Usar **HTTPS** obligatorio para todas las llamadas al IdP y APIs.

# 4. Parámetros recomendados

| Parámetro               | Recomendación             | Justificación                                          |
|-------------------------|---------------------------|--------------------------------------------------------|
| `exp` (expiration)       | ≤ 15 minutos              | Limita el tiempo de uso de tokens robados.             |
| `refresh_token lifetime` | 1 día (renovable)         | Balance entre usabilidad y seguridad.                  |
| `aud`                    | Exacto ID del cliente     | Impide reuso entre apps.                               |
| `scope`                  | Mínimo necesario          | Principio de mínimo privilegio.                        |
| `alg`                    | RS256 o ES256             | No usar `none` ni algoritmos inseguros.                |
| `state` y `nonce`        | Aleatorios, únicos por sesión | Protegen contra ataques de replay y CSRF.             |

# 5. Errores comunes a evitar
- Aceptar tokens expirados.
- Validar solo con el frontend.
- Usar secretos en apps móviles/web.
- No validar `iss`, `aud`, `alg`.
- Reutilizar tokens entre servicios.

# 6. Recomendaciones finales
- Hacer logging seguro (sin exponer tokens).
- Tener mecanismos de revocación de tokens (blacklist, TTL).
- Revisar bibliotecas de cliente e IdP por actualizaciones de seguridad.
- Hacer pruebas de seguridad periódicas (DAST, SAST, Pentest).

