# Peace Break

## Purpose

Peace Break is a mobile-friendly brick-breaker implementation for the 42 Mobile development subject. It is a dependency-free browser app that runs from `index.html`, including authentication, persistent user data, ten stages, shop, inventory, leaderboard, and settings.

## Audit and implementation notes

The initial audit found only the supplied subject PDF and no application files. The mandatory requirements were implemented in `index.html`, `styles.css`, and `app.js` using browser `localStorage` as the database and Web Crypto SHA-256 password hashes. The app has no server or SQL surface, so SQL injection is not applicable; all rendered user text is escaped.

The first-run data set includes 20 pre-registered users with varying scores and completed-stage progress. Their password field contains only a sentinel hash so no plaintext credentials are shipped. The registration flow creates usable accounts and validates the subject's email, username, and password rules. For production deployment, replace the local store with a server-side database using a slow password hash such as Argon2id or bcrypt and secure sessions.

## Run and test

Open `index.html` in a current browser or serve this directory with any static HTTP server. Register an account using a strong password such as `PeaceBreak2026!`, then play through stages. Touch/pointer movement controls the paddle; buttons provide mobile controls.

Manual validation checklist: registration/login validation; stage play, pause, win and lose; replay and best-score persistence; shop confirmation and coin deduction; skin inventory/equip/remove; top-10 leaderboard and current rank; settings confirmations; localStorage persistence; 20 seeded users; and no unescaped user text in UI.

## Limitations

This repository is intentionally offline and has no deployable backend, native package, or real multi-device account synchronization. Seeded accounts have no plaintext passwords in the repository, so evaluators should create a fresh account for the functional walkthrough. Production hardening requires a backend, server-side password hashing, HTTPS, rate limiting, and real authentication/session management.
