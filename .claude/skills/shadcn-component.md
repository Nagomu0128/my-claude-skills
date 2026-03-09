---
description: Create or compose components using shadcn/ui. Use when the user wants to build UI components, forms, dialogs, tables, or any interactive UI elements.
---

# shadcn/ui Component Builder

## Instructions

When building components with shadcn/ui:

1. **Check installed components first**: Look in `components/ui/` to see which shadcn components are already installed.

2. **Install missing components** if needed:
   ```bash
   npx shadcn@latest add <component-name>
   ```

3. **Component composition patterns**:
   - Place reusable composed components in `components/` (not in `components/ui/`)
   - Keep `components/ui/` for base shadcn components only
   - Use `cn()` utility from `lib/utils` for conditional class merging

4. **Form components** - Use shadcn Form with react-hook-form + zod:
   ```tsx
   import { useForm } from "react-hook-form";
   import { zodResolver } from "@hookform/resolvers/zod";
   import { Form, FormField, FormItem, FormLabel, FormControl, FormMessage } from "@/components/ui/form";
   ```

5. **Common component patterns**:
   - **Data display**: Card, Table, Badge, Avatar
   - **Input**: Input, Textarea, Select, Checkbox, Switch, Slider
   - **Feedback**: Alert, Toast (via Sonner), Skeleton
   - **Overlay**: Dialog, Sheet, Popover, Dropdown Menu, Tooltip
   - **Navigation**: Tabs, Breadcrumb, Pagination
   - **Layout**: Separator, Accordion, Collapsible

6. **Styling**:
   - Use Tailwind utility classes
   - Use CSS variables defined in the theme (e.g., `bg-primary`, `text-muted-foreground`)
   - Use the `cn()` helper for conditional classes
   - Respect the project's existing design tokens and color scheme

7. **Accessibility**: shadcn components are built on Radix UI and are accessible by default. Don't override ARIA attributes unless necessary.
