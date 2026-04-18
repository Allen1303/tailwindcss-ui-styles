# Tailwind CSS UI Reference

---

## Login Form

**Aesthetic:** Refined / SaaS — indigo accent, subtle card, clean labels

### JSX + Tailwind

```jsx
export default function LoginForm() {
  return (
    <div className="min-h-screen flex items-center justify-center bg-gray-50 px-4">
      <div className="w-full max-w-sm bg-white border border-gray-200 rounded-2xl p-10 shadow-sm">
        {/* Logo */}
        <div className="w-9 h-9 bg-gray-900 rounded-lg flex items-center justify-center mb-6">
          <span className="text-indigo-300 text-sm font-bold">A</span>
        </div>

        {/* Heading */}
        <h1 className="text-xl font-semibold text-gray-900 tracking-tight mb-1">
          Welcome back
        </h1>
        <p className="text-sm text-gray-500 mb-8">
          Don't have an account?{" "}
          <a href="#" className="text-indigo-600 font-medium hover:underline">
            Sign up free
          </a>
        </p>

        {/* Email */}
        <div className="mb-4">
          <label className="block text-xs font-medium text-gray-500 uppercase tracking-wide mb-1.5">
            Email
          </label>
          <input
            type="email"
            placeholder="you@example.com"
            className="w-full h-11 px-3.5 border border-gray-200 rounded-lg text-sm bg-gray-50 text-gray-900 placeholder:text-gray-400 outline-none focus:border-indigo-500 focus:ring-2 focus:ring-indigo-500/10 transition"
          />
        </div>

        {/* Password */}
        <div className="mb-5">
          <label className="block text-xs font-medium text-gray-500 uppercase tracking-wide mb-1.5">
            Password
          </label>
          <div className="relative">
            <input
              type="password"
              placeholder="••••••••"
              className="w-full h-11 px-3.5 pr-11 border border-gray-200 rounded-lg text-sm bg-gray-50 text-gray-900 placeholder:text-gray-400 outline-none focus:border-indigo-500 focus:ring-2 focus:ring-indigo-500/10 transition"
            />
            {/* Eye toggle — wire with useState */}
            <button className="absolute right-3 top-1/2 -translate-y-1/2 text-gray-400 hover:text-gray-600"></button>
          </div>
        </div>

        {/* Remember + Forgot */}
        <div className="flex items-center justify-between mb-6">
          <label className="flex items-center gap-2 text-sm text-gray-500 cursor-pointer">
            <input type="checkbox" className="accent-indigo-600 w-3.5 h-3.5" />
            Remember me
          </label>
          <a
            href="#"
            className="text-sm text-indigo-600 font-medium hover:underline"
          >
            Forgot password?
          </a>
        </div>

        {/* Submit */}
        <button className="w-full h-11 bg-indigo-600 hover:bg-indigo-700 active:scale-[0.98] text-white text-sm font-semibold rounded-lg transition mb-5">
          Sign in
        </button>

        {/* Divider */}
        <div className="flex items-center gap-3 mb-5">
          <span className="flex-1 h-px bg-gray-200" />
          <span className="text-xs text-gray-400">or continue with</span>
          <span className="flex-1 h-px bg-gray-200" />
        </div>

        {/* Google SSO */}
        <button className="w-full h-11 flex items-center justify-center gap-2.5 border border-gray-200 rounded-lg text-sm font-medium text-gray-700 bg-white hover:bg-gray-50 transition">
          {/* Swap for actual Google SVG icon */}
          <span>G</span>
          Continue with Google
        </button>
      </div>
    </div>
  );
}
```

### Key class patterns to remember

| Pattern          | Classes                                                                                     |
| ---------------- | ------------------------------------------------------------------------------------------- |
| Card shell       | `bg-white border border-gray-200 rounded-2xl shadow-sm`                                     |
| Input base       | `w-full h-11 px-3.5 border border-gray-200 rounded-lg text-sm bg-gray-50`                   |
| Input focus ring | `focus:border-indigo-500 focus:ring-2 focus:ring-indigo-500/10`                             |
| Label style      | `text-xs font-medium text-gray-500 uppercase tracking-wide`                                 |
| Primary button   | `bg-indigo-600 hover:bg-indigo-700 active:scale-[0.98] text-white font-semibold rounded-lg` |
| Divider line     | `flex-1 h-px bg-gray-200`                                                                   |

### Iteration notes

- **Dark mode:** swap `bg-gray-50` → `bg-zinc-950`, `bg-white` → `bg-zinc-900`, `border-gray-200` → `border-zinc-800`
- **Brand color:** replace all `indigo-*` with your accent (e.g. `violet-*`, `blue-*`, `emerald-*`)
- **No social login:** remove divider + Google button block
- **Add validation:** wrap inputs in a `<form>` and add `text-red-500 text-xs mt-1` error messages below each field

---
