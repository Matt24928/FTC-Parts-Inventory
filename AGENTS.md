# Project Overview

This project is an Android application for FTC teams to manage their parts inventory.

The current goal is to build **V1**, which focuses only on **team accounts** and **parts inventory management**.

This is **not** an FTC marketplace yet.

---

# V1 Scope

The app should currently support:

- team account registration
- login with email and password
- one account per FTC team
- team profile creation
- parts inventory management
- parts catalog browsing
- search and filters for inventory

V1 should **not** include:

- trading between teams
- public listings
- marketplace features
- messaging between teams
- notifications
- image upload for every part by default
- advanced admin systems

---

# Core Product Rules

- Each FTC team should have **only one account**.
- The **international FTC team number** is required and should be treated as unique.
- Team data should be stored in Firebase.
- Inventory items belong to a specific team.
- The app should remain simple and usable for V1.
- Do not add future features unless explicitly requested.

---

# Tech Stack

Use the following stack unless explicitly told otherwise:

- **Kotlin**
- **Android Studio**
- **Jetpack Compose**
- **Material 3**
- **Firebase Authentication**
- **Cloud Firestore**

Do not introduce unnecessary libraries.

Avoid adding dependency injection frameworks like Hilt for now unless explicitly requested.

---

# Architecture Guidelines

Keep architecture simple and understandable.

Preferred structure:

- `model/`
- `auth/`
- `data/`
- `navigation/`
- `ui/screens/`
- `ui/components/`

Guidelines:

- keep files small and focused
- prefer clear naming
- avoid overengineering
- avoid premature abstraction
- prefer readable code over “clever” code
- do not create complicated architecture patterns unless needed

---

# UI Guidelines

- Use **Jetpack Compose**
- Use **Material 3**
- Keep screens clean and functional
- Prefer simple layouts with good spacing
- Forms should be easy to understand
- Show loading and error states where appropriate
- Avoid placeholder-only UI unless explicitly asked

---

# Firebase Rules

Authentication:
- Use **Email/Password** authentication
- Registration should check whether a team with the same `teamNumber` already exists
- Only allow account creation if the team number is not already used

Firestore:
- Store teams in a `teams` collection
- Use the authenticated Firebase user ID as the Firestore document ID when appropriate
- Keep team profile fields structured and consistent

Important:
- Do not hardcode secrets
- Do not move or expose sensitive config files unnecessarily
- Assume `google-services.json` is already configured locally

---

# Current Navigation Flow

Current intended flow:

- `Login`
- `Register`
- `CreateTeamProfile`
- `Home`
- `Inventory`

Do not break this flow unless the task explicitly requires it.

---

# Inventory Rules for V1

Inventory is private to each team.

For now:
- teams manage their own inventory
- inventory items should be linked to the owning team
- trading-related fields should not be added to the visible UI
- do not build public inventory discovery yet

The catalog may contain standard parts with predefined images.

Custom parts may be supported later or in a limited form, but keep V1 focused on inventory basics.

---

# Coding Rules

- Use `PascalCase` for classes and composables
- Use `camelCase` for variables and functions
- Keep composables focused
- Prefer state hoisting when reasonable
- Avoid giant files
- Avoid mixing unrelated responsibilities in one file

When updating code:
- preserve existing working behavior unless task requires changing it
- do not remove useful comments without reason
- do not rewrite unrelated files unnecessarily

---

# Dependency Rules

Before adding a new dependency:
- check if existing AndroidX / Firebase tools already solve the problem
- avoid adding libraries just for convenience
- do not add experimental libraries without a clear reason

---

# Definition of Done

A task is done only if:

- the project still builds successfully
- the relevant screen or feature works
- navigation is not broken
- no unrelated functionality is changed
- code is readable and consistent with this project
- the implementation stays within V1 scope unless explicitly requested otherwise

---

# Preferred Task Style

When implementing changes:

1. understand the requested scope
2. make the smallest clean change that solves the problem
3. avoid speculative future features
4. preserve simplicity
5. keep the app aligned with V1 goals

---

# What To Avoid

Do not:

- add trading features
- add chat or messaging
- add marketplace logic
- redesign the whole app unless requested
- introduce backend complexity not needed for the current task
- replace the stack with another framework
- create web or iOS versions
- add unnecessary animations or visual complexity

---

# If Unsure

If a request is ambiguous, prefer:
- the simplest implementation
- preserving current structure
- staying within V1 scope
- making minimal safe changes
