# uivibe-pro-toaster

Lightweight toast notification library for React, Next.js, Vue, and Vanilla JavaScript.

[![npm version](https://img.shields.io/npm/v/uivibe-pro-toaster.svg)](https://www.npmjs.com/package/uivibe-pro-toaster)
[![npm downloads](https://img.shields.io/npm/dm/uivibe-pro-toaster.svg)](https://www.npmjs.com/package/uivibe-pro-toaster)
[![license](https://img.shields.io/npm/l/uivibe-pro-toaster.svg)](./LICENSE)
[![live demo](https://img.shields.io/badge/live-demo-6366f1.svg)](https://uivibe-pro-toaster-landing.vercel.app/)

Premium, universal, zero-dependency toast notifications under 5 kB gzipped. Works in **Vanilla JS, React, Vue, Next.js, Svelte, Solid, PHP/Laravel, Python/Django** — anywhere you can run a script tag or import a module.

## Links

- Live demo: https://uivibe-pro-toaster-landing.vercel.app/
- npm package: https://www.npmjs.com/package/uivibe-pro-toaster
- GitHub repository: https://github.com/rashaduldev/uivibe-pro-toaster
- Issues: https://github.com/rashaduldev/uivibe-pro-toaster/issues

- Latest version: `1.0.0`
- License: `MIT`
- Install command: `npm install uivibe-pro-toaster`

- ⚡ **< 5 kB gzipped** — ESM / CJS / Browser-global (UMD-style IIFE)
- 🧊 **Glassmorphism** with `backdrop-filter`, beautiful built-in SVG icons
- ⏳ **Promise-based API** for async loading → success / error transitions
- 🧱 **Smart stacking** with per-position queue and max-visible cap
- 🤙 **Swipe / drag to dismiss** (mouse + touch via Pointer Events)
- 🖱️ **Pause on hover & focus** with accurate remaining-time tracking
- 🎨 **9 positions**, dark / light / auto theme, full **CSS variables**
- ♿ **Full ARIA** (`role="status"` / `role="alert"`, `aria-live`, focusable close)
- 🧩 **Zero dependencies**, TypeScript-first, framework-agnostic

## Install

```bash
npm install uivibe-pro-toaster
# or
pnpm add uivibe-pro-toaster
yarn add uivibe-pro-toaster
bun add uivibe-pro-toaster
```

CDN (browser global `Toast`):

```html
<script src="https://unpkg.com/uivibe-pro-toaster/dist/index.global.js"></script>
<script>Toast.success("Hello!");</script>
```

## Usage guide

Choose the import style that matches your app:

```ts
import { toast } from "uivibe-pro-toaster";
```

```js
const { toast } = require("uivibe-pro-toaster");
```

```html
<script src="https://unpkg.com/uivibe-pro-toaster/dist/index.global.js"></script>
<script>
  Toast.success("Saved!");
</script>
```

## Quick start

```ts
import { toast } from "uivibe-pro-toaster";

toast.success("Listing saved!");
toast.error("Something broke", { duration: 6000 });

toast.promise(api.save(form), {
  loading: "Saving…",
  success: "Saved!",
  error: "Failed",
});
```

## API

| Method | Signature | Notes |
| --- | --- | --- |
| `toast(msg, opts?)` | `(string, ToastOptions?) => id` | Default type |
| `toast.success(msg, opts?)` | same | Green success icon |
| `toast.error(msg, opts?)` | same | `role="alert"`, `aria-live="assertive"` |
| `toast.info(msg, opts?)` | same | |
| `toast.warning(msg, opts?)` | same | |
| `toast.loading(msg, opts?)` | same | Infinite duration + spinner |
| `toast.promise(p, msgs, opts?)` | `(Promise, {loading, success, error}) => Promise` | Async pipeline |
| `toast.update(id, partial)` | | Change type / message / duration in place |
| `toast.dismiss(id?)` | | One or all |
| `toast.configure(globalConfig)` | | Defaults for every subsequent toast |

### Options

| Key | Type | Default |
| --- | --- | --- |
| `duration` | `number \| Infinity` | `4000` |
| `position` | one of 9 positions | `top-right` |
| `icon` | `string \| false` | auto by type |
| `dismissible` | `boolean` | `true` |
| `pauseOnHover` | `boolean` | `true` |
| `swipeToDismiss` | `boolean` | `true` |
| `progress` | `boolean` | `true` |
| `theme` | `'light' \| 'dark' \| 'auto'` | `auto` |
| `description` | `string` | — |
| `action` | `{ label, onClick }` | — |
| `html` | `string` (custom markup) | — |
| `className`, `style` | DOM passthrough | — |
| `onShow`, `onDismiss`, `onClick` | callbacks | — |

### Configuration (defaults)

```ts
toast.configure({
  position: "bottom-right",
  duration: 5000,
  maxVisible: 4,
  theme: "auto",   // 'light' | 'dark' | 'auto'
  gap: 12,
  zIndex: 9999,
});
```

## Theming

Every visual is controlled by CSS variables. Override them anywhere in your app:

```css
:root {
  --uvt-bg: rgba(255, 255, 255, 0.85);
  --uvt-text: #0f172a;
  --uvt-radius: 16px;
  --uvt-success: #16a34a;
  --uvt-error: #dc2626;
  --uvt-font: "Inter", system-ui, sans-serif;
}
```

## React / Next.js

```tsx
"use client";
import { useEffect } from "react";
import { toast } from "uivibe-pro-toaster";

export default function Demo() {
  useEffect(() => toast.configure({ position: "bottom-right" }), []);
  return <button onClick={() => toast.success("Saved!")}>Save</button>;
}
```

## Browser support

Modern evergreen browsers (Chrome, Edge, Firefox, Safari). `backdrop-filter` degrades gracefully to a solid background.

## License

MIT
