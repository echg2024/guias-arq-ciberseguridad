# Guía Técnica para flujos de Autenticación y Autorización

# 1. Introducción
En el sector salud, la protección de los datos personales y clínicos de los pacientes es un tema de suma importancia. Los flujos de autenticación y autorización adecuados son fundamentales para garantizar que solo usuarios autorizados puedan acceder a la información sensible, minimizando así el riesgo de acceso no autorizado y posibles brechas de seguridad. Esta guía técnica proporciona las mejores prácticas y directrices para el diseño, implementación y gestión de flujos de autenticación y autorización en aplicaciones y sistemas dentro del sector salud, usando estándares seguros como OAuth 2.0, OpenID Connect, JWT, y otros protocolos de autenticación.

La autenticación asegura la veracidad de la identidad de los usuarios, mientras que la autorización define qué recursos pueden ser accesibles dependiendo de sus permisos. En el entorno de salud, un flujo robusto de autenticación y autorización protege tanto los datos de los pacientes como el acceso a sistemas críticos, garantizando la privacidad y el cumplimiento con regulaciones de seguridad como la Ley General de Protección de Datos Personales y otras normativas internacionales.

# 2. Objetivo
El objetivo de esta guía es proporcionar un conjunto de directrices y recomendaciones técnicas para implementar flujos de autenticación y autorización seguros, con el fin de proteger la integridad y confidencialidad de los datos de salud. Se busca garantizar que solo los usuarios legítimos y autorizados puedan acceder a recursos específicos del sistema de salud, y que este acceso se realice de manera controlada, auditable y conforme a las mejores prácticas de seguridad.

La guía aborda la integración de los protocolos modernos de autenticación y autorización, como OAuth 2.0 y OpenID Connect, para gestionar accesos a servicios y recursos en línea. Además, se proporcionan recomendaciones sobre la implementación y validación de JWT (JSON Web Tokens) para la transmisión segura de información entre los diferentes sistemas, usuarios y aplicaciones.

# 3. Alcance
Esta guía técnica aplica a todos los sistemas y aplicaciones que manejen datos de salud dentro de la organización, incluidos los sistemas de gestión de pacientes, aplicaciones móviles, plataformas de atención a distancia (telemedicina), sistemas de gestión hospitalaria, y cualquier otra aplicación o servicio que requiera la autenticación y autorización de usuarios para acceder a información sensible.

El alcance de esta guía incluye los siguientes aspectos:
- Diseño y implementación de flujos de autenticación (verificación de identidad del usuario).
- Implementación de autorización (gestión de permisos y acceso a recursos).
- Integración de protocolos estándares de autenticación, como OAuth 2.0 y OpenID Connect.
- Uso de JWT para transmitir información de autorización e identidad de forma segura.
- Recomendaciones de seguridad relacionadas con el almacenamiento y manejo de credenciales, tokens y claves de acceso.
- Procedimientos para la validación de usuarios, gestión de sesiones y renovación de tokens.
- Mejores prácticas para la autenticación multifactor (MFA) y control de acceso basado en roles (RBAC).

La guía está destinada a ser utilizada por equipos de desarrollo, arquitectos de software, equipos de seguridad y administradores de sistemas que implementen soluciones de software en el ámbito del sector salud.

# 4. Componentes Clave

## 4.1 OAuth 2.0
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

## 4.2 OpenID Connect (OIDC)
- **Qué es:** Extensión de OAuth 2.0 para autenticación. Agrega capa de identidad sobre el token.
- **Usos:** Inicio de sesión único (SSO), federación de identidad.
- **Tokens usados:**
  - `id_token` (JWT)
  - `access_token`

## 4.3 Identity Provider (IdP)
- **Qué es:** Servicio que verifica identidad y emite tokens de acceso y/o identidad.
- **Ejemplos:** Keycloak, Azure AD, Okta, Auth0.

## 4.4 JSON Web Token (JWT)
- **Qué es:** Formato compacto y firmado digitalmente para transmitir claims (atributos).
- **Estructura:** `header.payload.signature` (base64url)
- **Tipos:**
  - `id_token`: identidad.
  - `access_token`: autorización.
  - `refresh_token`: renovar sesión.

# 5. Recomendaciones Técnicas

## 5.1 Backend
- Validar firma de los JWT usando la clave pública del IdP.
- Verificar los claims obligatorios:
  - `iss` (issuer): debe coincidir con el IdP esperado.
  - `aud` (audience): debe ser el ID del cliente.
  - `exp`, `iat`, `nbf`: validar tiempo de expiración.
- Rotación de claves públicas (JWKS): actualizar automáticamente.
- Evitar confiar en tokens no validados por backend.

## 5.2 Frontend
- Usar **PKCE** (Proof Key for Code Exchange) para flujos de autorización en apps públicas.
- No almacenar `access_token` en **localStorage** → preferir memoria volátil o `sessionStorage` si es estrictamente necesario.
- Evitar exponer secretos del cliente en el frontend.
- Usar **HTTPS** obligatorio para todas las llamadas al IdP y APIs.

# 6. Parámetros recomendados

| Parámetro               | Recomendación             | Justificación                                          |
|-------------------------|---------------------------|--------------------------------------------------------|
| `exp` (expiration)       | ≤ 15 minutos              | Limita el tiempo de uso de tokens robados.             |
| `refresh_token lifetime` | 1 día (renovable)         | Balance entre usabilidad y seguridad.                  |
| `aud`                    | Exacto ID del cliente     | Impide reuso entre apps.                               |
| `scope`                  | Mínimo necesario          | Principio de mínimo privilegio.                        |
| `alg`                    | RS256 o ES256             | No usar `none` ni algoritmos inseguros.                |
| `state` y `nonce`        | Aleatorios, únicos por sesión | Protegen contra ataques de replay y CSRF.             |

# 7. Errores comunes a evitar
- Aceptar tokens expirados.
- Validar solo con el frontend.
- Usar secretos en apps móviles/web.
- No validar `iss`, `aud`, `alg`.
- Reutilizar tokens entre servicios.

# 8. Recomendaciones finales
- Hacer logging seguro (sin exponer tokens).
- Tener mecanismos de revocación de tokens (blacklist, TTL).
- Revisar bibliotecas de cliente e IdP por actualizaciones de seguridad.
- Hacer pruebas de seguridad periódicas (DAST, SAST, Pentest).

