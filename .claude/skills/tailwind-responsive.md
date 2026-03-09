---
description: Build responsive layouts with Tailwind CSS. Use when the user wants to create responsive designs, fix layout issues, or implement mobile-first designs.
---

# Tailwind Responsive Layout

## Instructions

When building responsive layouts with Tailwind:

1. **Mobile-first approach**: Start with mobile styles, add breakpoints for larger screens:
   - `sm:` (640px) - Small tablets
   - `md:` (768px) - Tablets
   - `lg:` (1024px) - Laptops
   - `xl:` (1280px) - Desktops
   - `2xl:` (1536px) - Large screens

2. **Common responsive patterns**:

   **Responsive grid**:
   ```tsx
   <div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-4">
   ```

   **Responsive container**:
   ```tsx
   <div className="mx-auto w-full max-w-7xl px-4 sm:px-6 lg:px-8">
   ```

   **Stack to row**:
   ```tsx
   <div className="flex flex-col sm:flex-row gap-4">
   ```

   **Show/hide by breakpoint**:
   ```tsx
   <div className="hidden md:block">Desktop only</div>
   <div className="md:hidden">Mobile only</div>
   ```

3. **Spacing system**: Use Tailwind's spacing scale consistently (4, 6, 8 for gaps/padding at different breakpoints).

4. **Typography scaling**:
   ```tsx
   <h1 className="text-2xl sm:text-3xl lg:text-4xl font-bold">
   ```

5. **Container queries**: Use `@container` for component-level responsiveness when available.

6. **Test all breakpoints**: Ensure layouts don't break at any viewport width, especially between defined breakpoints.
