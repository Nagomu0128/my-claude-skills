---
description: Optimize Next.js application performance. Use when the user wants to improve page load speed, reduce bundle size, fix Core Web Vitals, or optimize rendering.
---

# Performance Optimization

## Instructions

When optimizing performance:

1. **Next.js specific optimizations**:
   - Use `next/image` for all images (auto-optimization, lazy loading)
   - Use `next/font` for fonts (zero layout shift)
   - Use `next/dynamic` for code-splitting heavy components
   - Prefer Server Components (zero client JS)
   - Use `loading.tsx` with Skeleton components for perceived performance

2. **Bundle size**:
   - Check bundle: `npx next build` shows route sizes
   - Use `"use client"` only on the smallest component that needs it — don't wrap entire pages
   - Lazy-load heavy libraries: `const Chart = dynamic(() => import("./chart"), { ssr: false })`
   - Check for barrel file imports that pull in entire libraries

3. **Rendering optimization**:
   - `React.memo()` for expensive components that re-render with same props
   - `useMemo` / `useCallback` only when there's a measured performance issue
   - Avoid creating objects/arrays in JSX props (causes re-renders)
   - Use `key` prop correctly in lists

4. **Data fetching**:
   - Use ISR (`revalidate`) for semi-static pages
   - Cache expensive operations with `unstable_cache` or React `cache()`
   - Parallel data fetching with `Promise.all()` instead of sequential awaits
   - Use `Suspense` boundaries to stream content progressively

5. **Images**: Use WebP/AVIF formats, set proper `sizes` attribute, use `priority` for above-the-fold images.

6. **Measure before optimizing**: Use Lighthouse, Web Vitals, or Next.js Analytics to identify actual bottlenecks.
