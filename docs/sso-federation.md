# Provost Inc SSO & Federation

## Objective
Federate identity from Entra ID to an external SaaS application using SAML, 
demonstrating enterprise single sign-on.

## Configuration
| Setting | Value |
|---------|-------|
| Application | Microsoft Entra SAML Toolkit (test app) |
| SSO method | SAML 2.0 |
| Assigned users | Provost-All-Staff group |
| Federation artifacts | Login URL, Entra Identifier, Logout URL, SAML certificate |

## SAML vs OIDC
- **SAML** : XML-based, common for enterprise/legacy SaaS (used here)
- **OIDC** : JSON/REST-based, modern standard for new apps and APIs
- Entra ID supports both; choice depends on the application's requirements

## Why This Matters
SSO federation extends Zero Trust beyond the portal every application a 
user accesses is authenticated and policy controlled through one trusted 
identity provider, reducing password sprawl and the credential attack surface.
