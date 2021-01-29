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

### Mock Extended Helper
[Using Jest-mock-extended for type safety](https://github.com/marchaos/jest-mock-extended)

```tsx
import { mock } from 'jest-mock-extended';
import { Repository, Connection } from 'typeorm';
import { Example } from '../entity/Example';
import { AnotherExample } from '../entity/AnotherExample';

export const mockCompanyRepo = mock<Repository<Example>>();
export const mockAnotherExampleRepo = mock<Repository<AnotherExample>>();

export const mockGetConnection = () => {
  return {
    manager: {
      getRepository: (type: any) => {
        switch (type) {
          case Company:
            return mockCompanyRepo;
          case AnotherExample:
            return mockAnotherExampleRepo;
          default:
            const error = `You need to add a mock repo for "${type}" to ${__filename}`;
            console.error(error);
            throw Error(error);
        }
      },
    },
  };
};

export const mockConnection = mock<Connection>();
export const mockCreateConnection = jest.fn(() =>
  Promise.resolve(mockConnection),
);
```
Required [Manual Mock Scaffolding](https://jestjs.io/docs/en/manual-mocks)

```tsx
import {
  mockGetConnection,
  mockCreateConnection,
} from '../src/__tests__/mockedRepositories';

const typeorm = jest.genMockFromModule('typeorm') as any;

typeorm.Column = () => jest.fn();
typeorm.Entity = () => jest.fn();
typeorm.PrimaryGeneratedColumn = () => jest.fn();
typeorm.ManyToOne = () => jest.fn();
typeorm.JoinColumn = () => jest.fn();
typeorm.OneToMany = () => jest.fn();
typeorm.OneToOne = () => jest.fn();
typeorm.getConnection = mockGetConnection;
typeorm.createConnection = mockCreateConnection;

module.exports = typeorm;
```
Example Usage

```tsx
import { mockCompanyRepo } from '../../mockedRepositories';

describe('POST /', () => {
  test('does something but with typesafety', (done) => {
    mockExampleRepo.findOne.mockResolvedValue({"This is typesafe"});
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

### 'ums'
Use Make Styles

```ts
const useStyles = makeStyles(() => ({
  $END$
}));
```

## License
MIT © [Joey Leung](https://github.com/dzoyee)
