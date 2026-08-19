# Bestiary Launcher · Java Edition Game Service AppID Review

This document mirrors the public information submitted for review of the Bestiary Launcher Microsoft Application ID.

## Application

- **Application name:** Bestiary Launcher
- **Application (client) ID:** `e4e89832-4229-46c3-90b1-a808ea750ec1`
- **Directory (tenant) ID:** `641bc7a6-7a09-4768-b477-8039a7304bf0`
- **Client type:** Native / public client
- **Account audience:** Personal Microsoft accounts
- **OAuth scopes:** `XboxLive.signin offline_access`

## Justification

Bestiary Launcher is a Windows desktop launcher for the Bestiary Rebirth game community.

The application requires Java Edition Game Service API access so users who own Minecraft: Java Edition can authenticate with their personal Microsoft account, verify Java Edition entitlement, retrieve their own Minecraft profile, launch an authenticated game session, and optionally manage their own player skin.

Authentication uses Microsoft OAuth Device Code Flow as a native/public client. The launcher never requests or receives the user's Microsoft password and does not distribute a client secret.

Refresh credentials are stored locally using operating-system-backed encrypted storage. Access tokens are not intentionally exposed to renderer/UI code, sold, shared, or used to access another player's account.

The application does not impersonate Microsoft or Mojang and does not use Java Edition Game Service APIs to bypass ownership, authentication, entitlement, or safety checks.

## Additional information

The application uses Microsoft Device Code Flow with `XboxLive.signin` and `offline_access`. After Microsoft authentication it uses Xbox Live/XSTS and Minecraft Services to verify Java Edition entitlement and retrieve only the authenticated user's own profile.

Skin changes through Minecraft profile APIs are always user-initiated and apply only to the authenticated user's own profile.

Bestiary Launcher also supports a separate **server-local/offline identity mode** for the Bestiary community. This mode is isolated from Microsoft authentication and Java Edition Game Service APIs. It does not request Microsoft/Xbox/Minecraft access tokens, does not call Java Edition entitlement/profile APIs, and does not fabricate an authenticated premium identity. Microsoft account mode remains a separate path and always performs Java Edition entitlement verification before an authenticated profile is accepted.

In local/offline mode, player-selected skin data is handled through the Bestiary server-local skin bridge. Minecraft profile skin APIs are used only when the active account is a successfully authenticated Microsoft account.

No Microsoft password or application client secret is collected by the launcher.

## Public references

- Project/distribution repository: https://github.com/aristheg201/bestiary-distribution
- API review page: `site/app-review.html`
- Privacy page: `site/privacy.html`
- Launcher releases: https://github.com/aristheg201/codespaces-blank/releases
