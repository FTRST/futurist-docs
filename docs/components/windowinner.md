# WindowInner (Deprecated)

> **⚠ Deprecated** — This component is kept for backwards compatibility but will be removed in a future version. Use **[WindowContent](windowcontent.md)** instead.

---

## Replacement

The three-layer pattern (`WindowInset` → `WindowSpacing` → `WindowInner`) has been replaced by a single **WindowContent** component that applies all visual styling in one wrapper:

```jsx
// OLD — three layers
<WindowInset>
  <WindowSpacing>
    <WindowInner>
      <p>Content</p>
    </WindowInner>
  </WindowSpacing>
</WindowInset>

// NEW — single wrapper
<WindowContent>
  <p>Content</p>
</WindowContent>
```

---

## Why Deprecated

- Hardcoded `rebeccapurple` background in WindowSpacing — conflicts with modern themes
- Triple nesting produced layout edge cases (margin leaking, double borders)
- Single `WindowContent` is simpler, cleaner, and fully theme-driven