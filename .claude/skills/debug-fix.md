---
description: Debug and fix errors in a Next.js/TypeScript project. Use when the user reports a bug, error message, or unexpected behavior and needs help troubleshooting.
---

# Debug & Fix

## Instructions

When debugging issues:

1. **Gather context first**:
   - Read the error message carefully — the stack trace tells you the file and line
   - Check the browser console AND terminal (server vs client errors)
   - Read the relevant source files before suggesting fixes

2. **Common Next.js errors**:

   | Error | Likely cause |
   |-------|-------------|
   | "use client" missing | Using hooks/event handlers in a Server Component |
   | Hydration mismatch | Different HTML rendered on server vs client |
   | "Module not found" | Wrong import path or missing package |
   | "Dynamic server usage" | Using dynamic APIs in statically rendered routes |
   | NEXT_REDIRECT error | Using `redirect()` inside try/catch — let it throw |

3. **TypeScript errors**:
   - Read the full error — TypeScript errors are verbose but precise
   - Check `tsconfig.json` paths and `@/` alias configuration
   - Verify imported types match actual data shapes

4. **Debugging approach**:
   - Reproduce the issue first
   - Narrow down: is it server-side or client-side?
   - Check recent changes that might have introduced the bug
   - Fix the root cause, not the symptom
   - Verify the fix doesn't break other functionality

5. **After fixing**: Run the relevant tests (`npx vitest run`) and check for TypeScript errors (`npx tsc --noEmit`) to confirm the fix.
