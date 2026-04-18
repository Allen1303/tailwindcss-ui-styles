# Tailwind CSS UI Style Guide

> Professional component reference for React applications.
> Each component includes semantic HTML tags, Tailwind class patterns, and iteration notes.

---

## Login Form

### Key Class Patterns

| Pattern            | HTML Tag                   | Classes                                                                                                                                                         |
| ------------------ | -------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Page wrapper       | `<main>`                   | `min-h-screen flex items-center justify-center bg-gray-50 px-4`                                                                                                 |
| Card shell         | `<section>`                | `w-full max-w-sm bg-white border border-gray-200 rounded-2xl p-10 shadow-sm`                                                                                    |
| Branding block     | `<header>`                 | `mb-6`                                                                                                                                                          |
| Page heading       | `<h1>`                     | `text-xl font-semibold text-gray-900 tracking-tight mb-1`                                                                                                       |
| Supporting text    | `<p>`                      | `text-sm text-gray-500`                                                                                                                                         |
| Inline link        | `<a>`                      | `text-indigo-600 font-medium hover:underline`                                                                                                                   |
| Form               | `<form>`                   | `method="POST" action="/login" noValidate`                                                                                                                      |
| Field group        | `<fieldset>`               | `mb-5 border-none p-0`                                                                                                                                          |
| Field group label  | `<legend>`                 | `sr-only` _(visually hidden, read by screen readers)_                                                                                                           |
| Field wrapper      | `<div>`                    | `mb-4`                                                                                                                                                          |
| Input label        | `<label>`                  | `block text-xs font-medium text-gray-500 uppercase tracking-wide mb-1.5`                                                                                        |
| Text input         | `<input>`                  | `w-full h-11 px-3.5 border border-gray-200 rounded-lg text-sm bg-gray-50 text-gray-900`                                                                         |
| Input placeholder  | `<input>`                  | `placeholder:text-gray-400`                                                                                                                                     |
| Input focus ring   | `<input>`                  | `outline-none focus:border-indigo-500 focus:ring-2 focus:ring-indigo-500/10 transition`                                                                         |
| Password wrapper   | `<div>`                    | `relative`                                                                                                                                                      |
| Icon button        | `<button type="button">`   | `absolute right-3 top-1/2 -translate-y-1/2 text-gray-400 hover:text-gray-600`                                                                                   |
| Primary button     | `<button type="submit">`   | `w-full h-11 bg-indigo-600 hover:bg-indigo-700 active:scale-[0.98] text-white text-sm font-semibold rounded-lg transition`                                      |
| Ghost button (SSO) | `<button type="submit">`   | `w-full h-11 flex items-center justify-center gap-2.5 border border-gray-200 rounded-lg text-sm font-medium text-gray-700 bg-white hover:bg-gray-50 transition` |
| Divider            | `<div role="separator">`   | `flex items-center gap-3 mb-5`                                                                                                                                  |
| Divider line       | `<span>`                   | `flex-1 h-px bg-gray-200`                                                                                                                                       |
| Checkbox           | `<input type="checkbox">`  | `accent-indigo-600 w-3.5 h-3.5`                                                                                                                                 |
| Decorative icon    | `<svg aria-hidden="true">` | _(hidden from screen readers — purely visual)_                                                                                                                  |

### Semantic Tags Used

| Tag                      | Location                 | Purpose                                                                          |
| ------------------------ | ------------------------ | -------------------------------------------------------------------------------- |
| `<main>`                 | Outer page wrapper       | Marks primary page content — screen readers navigate directly to it              |
| `<section>`              | Card wrapper             | Self-contained region, more meaningful than a plain `<div>`                      |
| `<header>`               | Logo + heading block     | Groups the introductory/branding content of the section                          |
| `<form>`                 | Credentials + Google SSO | Two separate forms each with their own `action` and submission scope             |
| `<fieldset>`             | Email + password group   | Logically groups related input fields together                                   |
| `<legend>`               | Inside `<fieldset>`      | Labels the field group — `sr-only` hides it visually, screen readers announce it |
| `<label htmlFor>`        | Every input              | Ties label to input via matching `id` — clicking label focuses the input         |
| `<button type="submit">` | Sign in button           | Explicitly tells the browser this button submits the form                        |
| `<button type="button">` | Eye toggle               | Prevents accidental form submission                                              |
| `aria-label`             | Eye toggle button        | Describes the button to screen readers since it has no visible text              |
| `aria-hidden="true"`     | Google SVG icon          | Hides decorative icon from assistive technology                                  |
| `autoComplete`           | Email + password inputs  | Helps browsers autofill credentials correctly                                    |
| `required`               | Email + password inputs  | Enables native browser validation before submission                              |
| `role="separator"`       | SSO divider              | Communicates the dividing element's purpose to assistive technology              |
| `noValidate`             | `<form>`                 | Disables native browser UI so you control custom validation messages             |

### JSX + Tailwind

```jsx
export default function LoginForm() {
  return (
    <main className="min-h-screen flex items-center justify-center bg-gray-50 px-4">
      <section className="w-full max-w-sm bg-white border border-gray-200 rounded-2xl p-10 shadow-sm">
        {/* Brand / Logo */}
        <header className="mb-6">
          <div className="w-9 h-9 bg-gray-900 rounded-lg flex items-center justify-center mb-4">
            <span className="text-indigo-300 text-sm font-bold">A</span>
          </div>
          <h1 className="text-xl font-semibold text-gray-900 tracking-tight mb-1">
            Welcome back
          </h1>
          <p className="text-sm text-gray-500">
            Don't have an account?{" "}
            <a href="#" className="text-indigo-600 font-medium hover:underline">
              Sign up free
            </a>
          </p>
        </header>

        {/* Login Form */}
        <form method="POST" action="/login" noValidate>
          <fieldset className="mb-5 border-none p-0">
            <legend className="sr-only">Account credentials</legend>

            {/* Email Field */}
            <div className="mb-4">
              <label
                htmlFor="email"
                className="block text-xs font-medium text-gray-500 uppercase tracking-wide mb-1.5"
              >
                Email
              </label>
              <input
                id="email"
                name="email"
                type="email"
                autoComplete="email"
                required
                placeholder="you@example.com"
                className="w-full h-11 px-3.5 border border-gray-200 rounded-lg text-sm bg-gray-50 text-gray-900 placeholder:text-gray-400 outline-none focus:border-indigo-500 focus:ring-2 focus:ring-indigo-500/10 transition"
              />
            </div>

            {/* Password Field */}
            <div className="mb-5">
              <label
                htmlFor="password"
                className="block text-xs font-medium text-gray-500 uppercase tracking-wide mb-1.5"
              >
                Password
              </label>
              <div className="relative">
                <input
                  id="password"
                  name="password"
                  type="password"
                  autoComplete="current-password"
                  required
                  placeholder="••••••••"
                  className="w-full h-11 px-3.5 pr-11 border border-gray-200 rounded-lg text-sm bg-gray-50 text-gray-900 placeholder:text-gray-400 outline-none focus:border-indigo-500 focus:ring-2 focus:ring-indigo-500/10 transition"
                />
                {/* Eye toggle — wire with useState to toggle type */}
                <button
                  type="button"
                  aria-label="Toggle password visibility"
                  className="absolute right-3 top-1/2 -translate-y-1/2 text-gray-400 hover:text-gray-600"
                >
                  👁
                </button>
              </div>
            </div>
          </fieldset>

          {/* Remember me + Forgot password */}
          <div className="flex items-center justify-between mb-6">
            <label
              htmlFor="remember"
              className="flex items-center gap-2 text-sm text-gray-500 cursor-pointer"
            >
              <input
                id="remember"
                name="remember"
                type="checkbox"
                className="accent-indigo-600 w-3.5 h-3.5"
              />
              Remember me
            </label>
            <a
              href="/forgot-password"
              className="text-sm text-indigo-600 font-medium hover:underline"
            >
              Forgot password?
            </a>
          </div>

          {/* Submit */}
          <button
            type="submit"
            className="w-full h-11 bg-indigo-600 hover:bg-indigo-700 active:scale-[0.98] text-white text-sm font-semibold rounded-lg transition mb-5"
          >
            Sign in
          </button>
        </form>

        {/* SSO Divider */}
        <div role="separator" className="flex items-center gap-3 mb-5">
          <span className="flex-1 h-px bg-gray-200" />
          <span className="text-xs text-gray-400">or continue with</span>
          <span className="flex-1 h-px bg-gray-200" />
        </div>

        {/* Google SSO — separate form, its own submission */}
        <form method="POST" action="/auth/google">
          <button
            type="submit"
            className="w-full h-11 flex items-center justify-center gap-2.5 border border-gray-200 rounded-lg text-sm font-medium text-gray-700 bg-white hover:bg-gray-50 transition"
          >
            <svg width="16" height="16" viewBox="0 0 24 24" aria-hidden="true">
              <path
                fill="#4285F4"
                d="M22.56 12.25c0-.78-.07-1.53-.2-2.25H12v4.26h5.92c-.26 1.37-1.04 2.53-2.21 3.31v2.77h3.57c2.08-1.92 3.28-4.74 3.28-8.09z"
              />
              <path
                fill="#34A853"
                d="M12 23c2.97 0 5.46-.98 7.28-2.66l-3.57-2.77c-.98.66-2.23 1.06-3.71 1.06-2.86 0-5.29-1.93-6.16-4.53H2.18v2.84C3.99 20.53 7.7 23 12 23z"
              />
              <path
                fill="#FBBC05"
                d="M5.84 14.09c-.22-.66-.35-1.36-.35-2.09s.13-1.43.35-2.09V7.07H2.18C1.43 8.55 1 10.22 1 12s.43 3.45 1.18 4.93l2.85-2.22.81-.62z"
              />
              <path
                fill="#EA4335"
                d="M12 5.38c1.62 0 3.06.56 4.21 1.64l3.15-3.15C17.45 2.09 14.97 1 12 1 7.7 1 3.99 3.47 2.18 7.07l3.66 2.84c.87-2.6 3.3-4.53 6.16-4.53z"
              />
            </svg>
            Continue with Google
          </button>
        </form>
      </section>
    </main>
  );
}
```

### Iteration Notes

- **Dark mode:** swap `bg-gray-50` → `bg-zinc-950`, `bg-white` → `bg-zinc-900`, `border-gray-200` → `border-zinc-800`, `text-gray-900` → `text-zinc-100`
- **Brand accent:** replace all `indigo-*` with your project color e.g. `violet-*`, `blue-*`, `emerald-*`
- **No social login:** remove the SSO divider and Google `<form>` block entirely
- **Validation errors:** add `<p role="alert" className="text-red-500 text-xs mt-1">Message</p>` below each input
- **Loading state:** add `disabled` + a spinner inside the submit `<button>` while awaiting response
- **Controlled inputs:** add `value` + `onChange` props to each input when wiring with `useState`

---
