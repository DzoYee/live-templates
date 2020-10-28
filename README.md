# React snippets for Webstorm
Live templates (snippets) for JetBrains product like Webstorm IDE.

## List of snippets

1. [Components](https://github.com/DzoYee/live-templates#react-components)
    1. [React ES6 Component With Interface](https://github.com/DzoYee/live-templates/blob/master/README.md#fsc)
    
2. [Testing](https://github.com/DzoYee/live-templates#testing)
    1. [React Testing Library File](https://github.com/DzoYee/live-templates/blob/master/README.md#rt)

3. [React Hooks](https://github.com/DzoYee/live-templates#hooks)
    1. [Use State](https://github.com/DzoYee/live-templates/blob/master/README.md#us)
    2. [Use Effect](https://github.com/DzoYee/live-templates/blob/master/README.md#ue)

## How to use the Live Templates
The following show the available abbreviations and their default implementations.

## React Components

<!--DOC_START-->
### `fsc`
React ES6 Component With Interface

```ts
import React from 'react';

interface $TM_FILENAME_BASE$Props {
};

const $TM_FILENAME_BASE$ = ({}:$TM_FILENAME_BASE$Props) => {
 return (
  $END$
 );
};

export default $TM_FILENAME_BASE$; 
```

## Testing

### `rt`
React Testing Library File

```tsx
import React from "react";
import { render, screen, fireEvent } from '@testing-library/react';
import "@testing-library/jest-dom/extend-expect";

describe("$TM_FILENAME_BASE$", () => {
  const { getByText } = screen;
  const { click } = fireEvent;
  
  it("$renders$", () => {
    render(<$TM_FILENAME_BASE$/>);
    $END$
  });
});

```

## Hooks
### `us`
Use State Hook

```ts
const [$state$, set$setState$] = useState($initState$);$END$
```

### `ue`
Use Effect Hook

```ts
useEffect(() => {
  return () => {
    $effect$
  };
}, [$input$]);
$END$
```

## License
MIT © [Joey Leung](https://github.com/dzoyee)