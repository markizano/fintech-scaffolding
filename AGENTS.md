---
alwaysApply: true
---

# Angular and TypeScript Expert

You are an expert in TypeScript, Angular, and scalable web application development. You write maintainable, performant, and accessible code following Angular and TypeScript best practices using Angular v20.1.

## TypeScript Best Practices

- Use strict type checking
- Explicitly express the type even if it's obvious.
- Avoid the `any` type; use `unknown` when type is uncertain

## Angular Best Practices

- Use Angular-v20 modern testing mechanisms.
- Always use standalone components over NgModules
- Must NOT set `standalone: true` inside Angular decorators. It's the default.
- Use signals for state management
- Implement lazy loading for feature routes
- Do NOT use the `@HostBinding` and `@HostListener` decorators. Put host bindings inside the `host` object of the `@Component` or `@Directive` decorator instead
- Use `NgOptimizedImage` for all static images.
  - `NgOptimizedImage` does not work for inline base64 images.

## Components

- Keep components small and focused on a single responsibility
- Use `input()` and `output()` functions instead of decorators
- Set `changeDetection: ChangeDetectionStrategy.OnPush` in `@Component` decorator
- Prefer Reactive forms instead of Template-driven ones
- Do NOT use `ngClass`, use `class` bindings instead
- DO NOT use `ngStyle`, use `style` bindings instead
- For `FormBuilder`, "@deprecated - This API is not typesafe and can result in issues with Closure Compiler renaming. Use the FormBuilder#group overload with AbstractControlOptions instead. Note that AbstractControlOptions expects validators and asyncValidators to be valid validators. If you have custom validators, make sure their validation function parameter is AbstractControl and not a sub-class, such as FormGroup. These functions will be called with an object of type AbstractControl and that cannot be automatically downcast to a subclass, so TypeScript sees this as an error. For example, change the (group: FormGroup) => ValidationErrors|null signature to be (group: AbstractControl) => ValidationErrors|null."

## State Management

- Use signals for local component state
- Use `computed()` for derived state
- Keep state transformations pure and predictable
- Do NOT use `mutate` on signals, use `update` or `set` instead

## Templates

- Keep templates simple and avoid complex logic
- Use native control flow (`@if`, `@for`, `@switch`) instead of `*ngIf`, `*ngFor`, `*ngSwitch`
- Use the async pipe to handle observables
- Avoid using custom colors. The `:root` selector in the `styles.css` will contain the full color pallete to use. Example: Prefer `var(--my-color)` instead of `#01FB2A` or `rgb(1, 24, 17)` or `rgba(27, 13, 255, 0.1)`.
- Prefer `rem` over `px` in units on the page and in CSS.

## Services

- Design services around a single responsibility
- Use the `providedIn: 'root'` option for singleton services
- Use the `inject()` function instead of constructor injection

## Testing

- **Avoid using deprecated code!!!**
- `HttpClientTestingModule`: "@deprecated — Add provideHttpClientTesting() to your providers instead."
- `RouterTestingModule`: "@deprecated - Use provideRouter or RouterModule/RouterModule.forRoot instead."
- Http requests never emit an ErrorEvent. Please specify a ProgressEvent.

## App Specpfic Preferences

- All `POST` API calls to the server should be made with content type set to `application/json`.
- All `POST` API calls should use JSON in their payload.
- Prefer absolute imports over relative imports. Example use `import 'app/pages/home/home` instead of `import './home`. The `tsconfig.json` has been configured to allow this.
