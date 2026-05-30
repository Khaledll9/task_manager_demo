# AGENTS.md

## Stack

Angular 18 standalone app (no NgModules). Bootstrap via `bootstrapApplication(AppComponent)` in `src/main.ts`. Builder: `@angular-devkit/build-angular:application` (esbuild-based). Tests: Jasmine + Karma.

DI: both `inject()` and constructor injection used interchangeably.

## Commands

| Command | What it does |
|---------|-------------|
| `ng serve` | Dev server at `http://localhost:4200`, auto-reload |
| `ng build` | Production build to `dist/essentials` |
| `ng test` | Run unit tests (Karma in Chrome) |
| `ng generate component <name>` | Generate a standalone component |

## Code conventions

- **TypeScript**: strict mode on, `noImplicitOverride`, `noPropertyAccessFromIndexSignature`, `strictTemplates`
- **Quotes**: single quotes in `.ts` (`.editorconfig`), double quotes in HTML
- **Indent**: 2 spaces, UTF-8, trailing newline required
- **Format**: CSS/SCSS in component `styleUrl`, templates in `templateUrl`
- **Selectors**: `app` prefix (e.g. `app-root`)
- **Standalone**: all components are `standalone: true`, no NgModules
- **Class fields**: `useDefineForClassFields: false` (Angular convention)

## Project layout

```
src/
  main.ts              -- entrypoint (bootstrapApplication)
  index.html           -- <app-root> mount point
  styles.css           -- global styles
  app/
    app.component.ts   -- root standalone component
    header/            -- app-header (static shell)
    user/              -- app-user (Input/Output, User model)
    tasks/             -- app-tasks (container), task/, new-task/ subdirs
      task/            -- app-task (Task model, NewTaskData)
      new-task/        -- app-new-task (form, ngModel, FormsModule)
      tasks.service.ts -- providedIn: 'root', localStorage-backed
    shared/
      card/            -- app-card (generic wrapper component)
  assets/users/        -- avatar images
```

## Known quirks

- `.vscode/launch.json` targets `http://localhost:8080` (not 4200)
- Output path: `dist/essentials`
- No router configured yet (no `RouterOutlet` or routes)
- `/.angular/cache` gitignored (can delete to clear cache)
- Indentation inconsistent across files (some 2-space, some 4-space despite `.editorconfig` saying 2 spaces)
