# Bestiary Launcher / Distribution

Public distribution and review materials for **Bestiary Launcher**, the desktop launcher used by the Bestiary Rebirth community.

## Public review site

The static review site lives in [`site/`](site/) and documents:

- the purpose of Bestiary Launcher;
- Microsoft Device Code authentication;
- the public Microsoft Application (client) ID;
- Minecraft: Java Edition entitlement/profile access;
- player-initiated skin management;
- local credential handling and privacy information;
- reviewer-facing Java Edition Game Service API integration details;
- the separate server-local/offline identity mode and its isolation from Microsoft/Xbox/Minecraft Game Service authentication.

GitHub Pages workflow: [`.github/workflows/pages.yml`](.github/workflows/pages.yml)

Expected Pages URL after Pages is enabled for this repository:

`https://aristheg201.github.io/bestiary-distribution/`

## Microsoft application

- Application name: `Bestiary Launcher`
- Application (client) ID: `e4e89832-4229-46c3-90b1-a808ea750ec1`
- Client type: native/public client
- Account audience: personal Microsoft accounts
- OAuth scopes used by the launcher: `XboxLive.signin offline_access`

The launcher does **not** collect Microsoft passwords and does not embed a client secret.

Microsoft account mode performs Xbox/XSTS exchange, Java Edition entitlement verification and authenticated profile retrieval before an authenticated Minecraft profile is accepted.

## Local / offline identity mode

Bestiary Launcher also supports a separate server-local/offline identity mode for the Bestiary community. This mode is isolated from the Microsoft authentication path and Java Edition Game Service APIs. It does not request Microsoft/Xbox/Minecraft access tokens, does not fabricate entitlement responses or an authenticated premium profile, and is not presented as proof of Java Edition ownership.

Player skin data in local/offline mode is handled through the Bestiary server-local skin bridge. Minecraft profile skin APIs are only used for the currently authenticated Microsoft-backed player's own profile.

## Distribution

Runtime manifests, release channels, announcements and application update metadata remain under [`bestiary-distribution/`](bestiary-distribution/).

Bestiary Launcher is independent third-party community software and is not affiliated with or endorsed by Mojang Studios or Microsoft.
