---
description: Write unit tests with Vitest. Use when the user wants to create tests, add test coverage, or write unit/integration tests for their code.
---

# Vitest Unit Test Writer

## Instructions

When writing tests with Vitest:

1. **File naming**: Place test files as `*.test.ts` or `*.test.tsx` next to the source file, or in a `__tests__/` directory.

2. **Basic structure**:
   ```tsx
   import { describe, it, expect, vi, beforeEach, afterEach } from "vitest";

   describe("featureName", () => {
     it("should do expected behavior", () => {
       // Arrange
       // Act
       // Assert
     });
   });
   ```

3. **React component testing** with Testing Library:
   ```tsx
   import { render, screen, fireEvent } from "@testing-library/react";
   import userEvent from "@testing-library/user-event";
   import { ComponentName } from "./component-name";

   describe("ComponentName", () => {
     it("renders correctly", () => {
       render(<ComponentName />);
       expect(screen.getByText("expected text")).toBeInTheDocument();
     });
   });
   ```

4. **Mocking**:
   - Use `vi.mock()` for module mocks
   - Use `vi.fn()` for function mocks
   - Use `vi.spyOn()` to spy on methods
   - Mock Next.js router: `vi.mock("next/navigation")`

5. **Async testing**:
   ```tsx
   it("fetches data", async () => {
     const result = await fetchData();
     expect(result).toEqual(expected);
   });
   ```

6. **Test categories to cover**:
   - Happy path (expected usage)
   - Edge cases (empty input, null values, boundary values)
   - Error cases (invalid input, API failures)
   - For components: rendering, user interaction, conditional rendering

7. **Running tests**:
   ```bash
   npx vitest run              # Run all tests once
   npx vitest run path/to/file # Run specific test file
   npx vitest --coverage       # Run with coverage
   ```

8. **Do NOT mock implementation details**. Test behavior and outcomes, not internal state.
