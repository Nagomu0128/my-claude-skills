---
description: Create Next.js Server Actions for form handling and data mutations. Use when the user wants to handle form submissions, data mutations, or server-side operations triggered from client components.
---

# Next.js Server Action

## Instructions

When creating Server Actions:

1. **File convention**: Create in a dedicated file with `"use server"` at the top:
   ```tsx
   "use server";

   export async function createItem(formData: FormData) {
     // ...
   }
   ```

2. **Validation**: Always validate input with Zod:
   ```tsx
   import { z } from "zod";

   const schema = z.object({
     name: z.string().min(1),
     email: z.string().email(),
   });
   ```

3. **Return pattern** - Use a consistent result type:
   ```tsx
   type ActionResult = {
     success: boolean;
     error?: string;
     data?: unknown;
   };
   ```

4. **Revalidation**: Call `revalidatePath()` or `revalidateTag()` after mutations to update cached data.

5. **Usage with useActionState** (client component):
   ```tsx
   "use client";
   import { useActionState } from "react";
   import { createItem } from "./actions";

   function Form() {
     const [state, action, pending] = useActionState(createItem, null);
     return (
       <form action={action}>
         <Button type="submit" disabled={pending}>Submit</Button>
       </form>
     );
   }
   ```

6. **Auth checks**: Always verify authentication/authorization at the start of the action before performing mutations.
