---
name: react-product-scaffold
description: Scaffold a production-oriented React (Vite) JavaScript UI application using feature-based architecture, React Router, Redux Toolkit, Tailwind CSS, and reusable design-system components. Use when asked to create or initialize a React product application.
---

# React Product Application Scaffold

## Goal
Create a runnable React application with a scalable feature-based architecture, UI-only example pages, centralized Redux Toolkit configuration, feature-local slices, reusable shared components, layouts, routing, and theme tokens.

## When to use
Use when the user asks to **scaffold**, **initialize**, or **create** a React application with this architecture. Do not overwrite an existing project without explicit permission.

## Instructions for the coding agent
1. Confirm the destination project directory and whether it already exists. Default to `my-react-app` if none is provided.
2. Ensure Node.js 20.19+ or 22.12+ and npm are available (Vite compatibility). If missing, explain how to install them.
3. Run the bundled script from this skill directory:

   ```bash
   bash scripts/scaffold.sh my-react-app
   ```

4. Run `cd my-react-app && npm run build` and resolve any build errors.
5. Report the project path and commands `npm run dev`, `npm run build`, and `npm run lint`.
6. Never add API clients, authentication flows, backend logic, or test frameworks during this initial UI scaffold unless separately requested.

## Folder architecture

```text
my-react-app/
├── public/
├── src/
│   ├── app/
│   │   ├── App.jsx
│   │   ├── main.jsx
│   │   ├── router/
│   │   │   ├── AppRouter.jsx
│   │   │   └── routes.jsx
│   │   ├── store/
│   │   │   ├── index.js
│   │   │   └── rootReducer.js
│   │   └── providers/
│   │       └── AppProviders.jsx
│   ├── layouts/
│   │   ├── MainLayout/
│   │   │   ├── MainLayout.jsx
│   │   │   ├── Header.jsx
│   │   │   ├── Sidebar.jsx
│   │   │   └── Footer.jsx
│   │   └── AuthLayout/
│   │       └── AuthLayout.jsx
│   ├── features/
│   │   ├── dashboard/
│   │   │   ├── components/DashboardStats.jsx
│   │   │   ├── pages/DashboardPage.jsx
│   │   │   ├── store/dashboardSlice.js
│   │   │   └── index.js
│   │   ├── users/
│   │   │   ├── components/UserList.jsx
│   │   │   ├── pages/UsersPage.jsx
│   │   │   ├── store/usersSlice.js
│   │   │   └── index.js
│   │   └── ui/store/uiSlice.js
│   ├── shared/
│   │   ├── components/
│   │   │   ├── ui/
│   │   │   │   ├── Button/Button.jsx
│   │   │   │   ├── Button/Button.module.css
│   │   │   │   ├── Input/Input.jsx
│   │   │   │   ├── Modal/Modal.jsx
│   │   │   │   ├── Table/Table.jsx
│   │   │   │   └── Spinner/Spinner.jsx
│   │   │   └── feedback/EmptyState.jsx
│   │   ├── hooks/
│   │   │   ├── useAppDispatch.js
│   │   │   └── useAppSelector.js
│   │   ├── utils/
│   │   └── constants/
│   ├── assets/{images,icons,fonts}/
│   └── styles/
│       ├── tokens.css
│       ├── typography.css
│       ├── themes.css
│       ├── reset.css
│       └── globals.css
├── index.html
├── package.json
├── vite.config.js
└── eslint.config.js
```

## Architecture rules
- `app/` owns the application bootstrap, router, providers, and Redux store assembly.
- `features/<feature>/` owns business-specific pages, components, and Redux slices.
- `shared/` holds generic, reusable UI components and hooks, with no imports from features.
- `layouts/` owns application shells. Feature pages render through React Router `<Outlet />`.
- Keep local-only interaction state in React; use Redux for shared state such as theme, sidebar, and cross-component feature state.
- Prefer semantic HTML, accessible labels, keyboard-accessible controls, and responsive layout.
- Theme colors and typography must come from design tokens; avoid scattered hard-coded brand colors.
- Avoid creating speculative abstraction layers or placeholder business logic.

## Verification checklist
- [ ] `npm install` succeeds.
- [ ] `npm run build` succeeds.
- [ ] `npm run lint` succeeds.
- [ ] Dashboard is visible at `/`.
- [ ] Users page is visible at `/users`.
- [ ] Sidebar navigation works.
- [ ] Theme toggle updates Redux state and the UI.
- [ ] Shared components are reusable without feature imports.

## Manual use without an agent
From the extracted skill directory, run:

```bash
bash scripts/scaffold.sh my-react-app
cd my-react-app
npm run dev
```

The Markdown file is the agent's instruction set; the bundled shell script performs the actual scaffolding.