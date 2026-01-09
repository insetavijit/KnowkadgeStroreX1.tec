| **Subtopic** | **Focus & Purpose** | **Key Concepts / Details** | **One-Line Recall** |
|---|---|---|---|
| **[[WP4.1.3.1 Selector Nesting]]** | Basic Nesting | `.nav { li { a { } } }` hierarchy structure | Mirror HTML structure in CSS. |
| **[[WP4.1.3.2 Parent Selector]]** | Ampersand Usage | `&:hover`, `&.active`, `&__element` (BEM) | Reference current selector with `&`. |
| **[[WP4.1.3.3 Property Nesting]]** | Namespace Grouping | `font: { family: ...; size: ...; weight: ...; }` | Group related properties together. |
| **[[WP4.1.3.4 Nesting Best Practices]]** | Depth Limits | Max 3-4 levels deep, avoid specificity wars | Don't mirror every HTML level. |
| **[[WP4.1.3.5 Media Query Nesting]]** | Responsive Patterns | Nest `@media` inside selectors for context | Keep responsive code with components. |
