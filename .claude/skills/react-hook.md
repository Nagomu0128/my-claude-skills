---
description: Create custom React hooks. Use when the user wants to extract reusable stateful logic into a custom hook.
---

# Custom React Hook Creator

## Instructions

When creating custom React hooks:

1. **File naming**: `use-hook-name.ts` (kebab-case with `use-` prefix) in `hooks/` directory.

2. **Structure**:
   ```tsx
   "use client";

   import { useState, useEffect, useCallback } from "react";

   export function useHookName(params: ParamsType) {
     // state
     // effects
     // handlers (wrap in useCallback if passed to children)

     return { data, isLoading, error, actions };
   }
   ```

3. **Return value pattern**: Return an object (not array) for hooks with multiple return values — easier to destructure selectively.

4. **Common hook patterns**:
   - **Data fetching**: Return `{ data, isLoading, error, refetch }`
   - **Toggle/boolean**: Return `{ value, toggle, setTrue, setFalse }`
   - **Form field**: Return `{ value, onChange, error, reset }`
   - **Debounced value**: Accept value + delay, return debounced value
   - **Local storage**: Sync state with localStorage
   - **Media query**: Return boolean for responsive breakpoints

5. **Rules of hooks**:
   - Only call hooks at the top level
   - Only call hooks from React functions
   - Always start name with `use`

6. **Performance**:
   - Use `useCallback` for functions returned by the hook that consumers might pass as props
   - Use `useMemo` for expensive computations
   - Avoid unnecessary re-renders by keeping state minimal

7. **TypeScript**: Explicitly type parameters and return values for public hooks.
