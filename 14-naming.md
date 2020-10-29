# Naming

## Template naming rules

_Only_ underscore templates to hide them from routes (not to indicate a partial).

Examples:

- **Nope…**: `_components/_cards/basic.twig`
- **Nope…**: `_components/_cards/_basic.twig`
- **Maybe…**: `components/cards/_basic.twig`
- **Maybe…**: `components/_cards/basic.twig`
- **Yep!**: `_components/cards/basic.twig`

- **Nope…**: `events/detail.twig`
- **Yep!**: `events/_detail.twig`
- **Yep!**: `events/_types/detail.twig`

## Block naming

- Stick to one convention for blocks, e.g. `main`.
- Deal with nested blocks by prefixing, e.g. `headerMain`
- Avoid ambiguity, e.g.
  - `body`: are we talking about the html tag, or the "article body"?
  - `content`: isn't everything content?
