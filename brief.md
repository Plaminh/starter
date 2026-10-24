# IA#2 — Dynamic HTML: Catalogue

## 1. Context

Course: CSC13008 — Web Application Development

Continue from Session 4 Part A, where the semantic HTML self-check has passed 8/8.

Use OpenAI Codex (VS Code) to implement Part B of the starter project.

Before implementation, read:
- README.md
- index.html
- app.js
- check.js

The TODO comments in `app.js` are the implementation specification. The "Done means" table in `README.md` defines acceptance criteria.

## 2. Scope and constraints

- Modify `app.js` only for Part B.
- Preserve all existing IDs, classes and data attributes.
- Do not modify `style.css` or `check.js`.
- Preserve the completed semantic HTML in `index.html`.
- Do not modify the provided `loadMore()` implementation.
- Do not add frameworks, libraries or dependencies.
- Use `addEventListener` rather than inline handlers.
- Use `textContent` for dynamic text, never `innerHTML` for user input.
- Keep the implementation simple and explainable.
- Do not create Git commits automatically.
- Implement B1, B2, B3 and B4 separately.

## 3. Functional requirements

### B1 — Add to cart

- Use exactly one delegated click listener on `#catalogue`.
- Detect clicks originating from `.add` buttons.
- Ignore clicks outside Add buttons and disabled products.
- Identify products using their card's `data-id`.
- Increment product quantities in the cart object.
- Update `#cart-count` with the total quantity.
- Support dynamically loaded products.

### B2 — Live search

- Filter products on every `input` event.
- Use `trim()` and `toLowerCase()` for case-insensitive matching.
- Match product names using substring search.
- Show or hide cards using `hidden`.
- Empty query: show all products and clear the status.
- Matches: display `Showing X of Y products`.
- No matches: display `No products match "<exactly what the user typed>"`.
- Use `textContent` to prevent HTML injection.
- Include dynamically loaded products in filtering.

### B3 — Form submission

- Handle the search form's `submit` event.
- Call `event.preventDefault()` to prevent page reload.
- Apply the search filter when Enter is pressed.
- Preserve the existing cart state.
- Do not append query parameters to the URL.

### B4 — Cart total

- Calculate total price using quantity × product price.
- Read prices from each card's `data-price`.
- Convert dataset prices using `Number()`.
- Include dynamically loaded products.
- Format totals using `toLocaleString('vi-VN')`.
- Update `#cart-total` without changing the existing cart count markup.

Example: `Cart (3) · 540.000 đ`.

## 4. Acceptance criteria

Manually verify every row of the "Done means" table in README.md:

1. Console reports `Session 4 self-check: 8/8 passed`.
2. The page's original appearance is preserved.
3. Keyboard focus reaches enabled buttons, excluding sold-out Add buttons.
4. Adding T-shirt twice produces `Cart (2)`; sold-out Tote bag does nothing.
5. Pressing Enter on a focused Add button increments the cart count.
6. Loading more products and adding Belt increments the cart count.
7. Searching `scarf` and `SCARF` produces one matching card; after Load more, the status says `Showing 1 of 12 products`. Clearing the input restores all products.
8. Entering `<img src=x onerror=alert(1)>` produces no alert or image, and the status displays the input exactly.
9. Pressing Enter after searching `cap` does not reload the page or reset the cart.
10. Browser Console contains no red errors.
11. Only `index.html` and `app.js` differ from the original starter among the supplied code files.

Additionally, verify B4 calculations using repeated additions, multiple products and dynamically loaded products.

## 5. Review and workflow

For each part:

1. Read the relevant TODO comments.
2. Implement only that part.
3. Explain the changes and their reasoning.
4. Inspect the Git diff.
5. Run the relevant acceptance tests manually.
6. Record actual corrections, rejected suggestions and test evidence in `AI-LOG.md`.
7. Create one Git commit after verification.

Do not claim that tests passed unless they were actually executed.