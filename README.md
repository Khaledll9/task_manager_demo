# EasyTask — Task Management Dashboard

A responsive single-page application built with **Angular 18** (standalone components API) for managing user tasks. Users can browse a list of team members, select one to view their tasks, add new tasks via a modal form, and mark tasks as complete. Task data persists across sessions using `localStorage`.

## Key Features

- **User selection** — click a user avatar to highlight and load their task list
- **Task CRUD** — view per-user tasks, add new tasks with a title/summary/due date, and remove completed items
- **Persistent state** — tasks survive page reloads via `localStorage`
- **Modal entry form** — add-task dialog with two-way `ngModel` binding and validation-ready template
- **Responsive layout** — CSS Grid with a side-panel / main-area breakpoint at 768 px
- **Shared UI primitives** — reusable `app-card` wrapper component used across user and task views

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Framework | Angular 18 (standalone, no NgModules) |
| Language | TypeScript 5.4 (strict mode) |
| Build tool | Angular CLI + esbuild (`@angular-devkit/build-angular:application`) |
| Styling | Plain CSS (global + per-component) |
| Forms | `@angular/forms` — template-driven with `ngModel` |
| Testing | Jasmine 5 + Karma (Chrome headless) |
| Persistence | `localStorage` (via `TasksService`) |
| Font | Poppins (Google Fonts) |

## Project Structure

```
src/
  main.ts                       App bootstrap (bootstrapApplication)
  index.html                    SPA shell — <app-root> mount point
  styles.css                    Global resets, dark background, Poppins font
  app/
    app.component.ts            Root component — user list + selected-user tasks
    dummy-users.ts              Static user seed data (6 users)
    header/                     App header with logo and tagline
    user/
      user.component.ts         User avatar card with selection highlight
      user.model.ts             User interface (id, avatar, name)
    tasks/
      tasks.component.ts        Task list container for a selected user
      tasks.service.ts          In-memory store backed by localStorage
      task/
        task.component.ts       Single task card with complete button
        task.model.ts           Task + NewTaskData interfaces
      new-task/
        new-task.component.ts   Modal form for creating a task
    shared/
      card/
        card.component.ts       Generic content projection wrapper
  assets/
    users/                      User avatar images (user-1.jpg … user-6.jpg)
    task-management-logo.png    Header logo
```

## Prerequisites

- **Node.js** 18.19+ or 20.11+
- **npm** 10+
- **Angular CLI** 18.x (`npm install -g @angular/cli`)

## Installation & Setup

```bash
# 1. Clone the repository
git clone <repo-url>
cd essentials

# 2. Install dependencies
npm install

# 3. Start the development server
ng serve
```

Open `http://localhost:4200` in your browser. The app automatically reloads when source files change.

## Available Scripts

| Command | Description |
|---------|-------------|
| `ng serve` | Start dev server at `http://localhost:4200` with HMR |
| `ng build` | Production build to `dist/essentials/` |
| `ng build --configuration development` | Dev build with source maps (no optimizations) |
| `ng test` | Run unit tests with Karma + Jasmine in Chrome |
| `ng generate component <name>` | Scaffold a new standalone component |
| `ng serve --port 4201` | Dev server on a custom port |

## Learning Objectives

This project was built as a hands-on Angular practice exercise covering:

- **Standalone components** — no `NgModule` wrappers, `bootstrapApplication` entrypoint
- **Control flow syntax** — `@for`, `@if` blocks (Angular 17+)
- **Component communication** — `@Input` / `@Output` with `EventEmitter`
- **Dependency injection** — both `inject()` function and constructor injection
- **Template-driven forms** — `ngModel` two-way binding with `FormsModule`
- **Pipes** — `DatePipe` for date formatting
- **Content projection** — `<ng-content>` in the shared `CardComponent`
- **Service architecture** — `providedIn: 'root'` singleton service with `localStorage` persistence
- **Responsive CSS** — media queries with CSS Grid layout
