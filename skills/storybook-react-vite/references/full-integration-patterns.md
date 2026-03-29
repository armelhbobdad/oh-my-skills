## Full Integration Patterns

### Co-import Patterns

| External Package | Storybook Integration | Pattern |
|-----------------|----------------------|---------|
| `@emotion/react` | `storybook/theming` | `styled`, `css`, `ThemeProvider`, `keyframes` are re-exports from emotion `[SRC:code/core/src/theming/index.ts:L5]` |
| `@emotion/styled` | `storybook/theming` | `styled` factory for CSS-in-JS components `[SRC:code/core/src/theming/index.ts:L5]` |
| `@vitest/spy` | `storybook/test` | `fn`, `spyOn`, `mocked`, `isMockFunction` wrap vitest spy with instrumentation `[SRC:code/core/src/test/index.ts:L26]` |
| `@vitest/expect` | `storybook/test` | `expect` wraps vitest expect with instrumented step tracking `[SRC:code/core/src/test/index.ts:L24]` |
| `@testing-library/dom` | `storybook/test` | `screen`, `within`, `getByRole`, `getByText`, etc. wrapped with instrumentation `[SRC:code/core/src/test/index.ts:L33]` |
| `@testing-library/user-event` | `storybook/test` | `userEvent` wraps user-event with instrumented step tracking `[SRC:code/core/src/test/index.ts:L31]` |
| `axe-core` | `@storybook/addon-a11y` | `A11yParameters.config` accepts axe `Spec`, `.options` accepts `RunOptions` `[SRC:code/addons/a11y/src/types.ts:L1]` |
| `vite` | `@storybook/builder-vite` | `viteFinal` receives and returns Vite `UserConfig` `[SRC:code/builders/builder-vite/src/types.ts:L5]` |
| `@playwright/test` | `@storybook/react` | `createTest` from `/experimental-playwright` creates Playwright CT test `[SRC:code/renderers/react/src/experimental-playwright.ts:L5]` |
| `vitest` | `@storybook/addon-vitest` | `storybookTest()` is a Vite plugin consumed by vitest config `[SRC:code/addons/vitest/src/vitest-plugin/index.ts:L28]` |

### Addon Composition

Combining a11y + docs + themes + vitest in a single project:

```ts
// .storybook/main.ts
import type { StorybookConfig } from '@storybook/react-vite';

const config: StorybookConfig = {
  stories: ['../src/**/*.stories.@(ts|tsx)'],
  addons: [
    '@storybook/addon-docs',
    '@storybook/addon-a11y',
    '@storybook/addon-themes',
    '@storybook/addon-vitest',
  ],
  framework: {
    name: '@storybook/react-vite',
    options: { strictMode: true },
  },
  docs: { autodocs: 'tag' },
};
export default config;
```

```tsx
// .storybook/preview.ts
import type { Preview } from '@storybook/react';
import { withThemeByClassName } from '@storybook/addon-themes';

const preview: Preview = {
  decorators: [
    withThemeByClassName({
      themes: { light: '', dark: 'dark' },
      defaultTheme: 'light',
    }),
  ],
  parameters: {
    a11y: { test: 'error' },
    docs: { toc: true },
  },
  tags: ['autodocs'],
};
export default preview;
```

`[SRC:code/frameworks/react-vite/src/types.ts:L1]`

### CSF Factories Pattern

The new CSF factory API (`definePreview` -> `meta` -> `story`) provides type-safe chaining:

```tsx
// .storybook/preview.ts
import { definePreview } from '@storybook/react-vite';

export default definePreview({
  parameters: { layout: 'centered' },
  tags: ['autodocs'],
});
```

```tsx
// src/components/Button.stories.tsx
import preview from '../../.storybook/preview';
import { Button } from './Button';

const meta = preview.meta({
  component: Button,
  title: 'Components/Button',
});

export const Primary = meta.story({
  args: { primary: true, label: 'Button' },
});

export const Secondary = meta.story({
  args: { label: 'Button' },
});
```

`[SRC:code/core/src/csf/definePreview.ts:L8]`
`[SRC:code/core/src/csf/types.ts:L1]`

### Portable Stories Testing

Use composed stories in any test runner (Jest, Vitest, Playwright):

```tsx
// src/components/Button.test.tsx
import { composeStories } from '@storybook/react';
import { render, screen } from '@testing-library/react';
import * as stories from './Button.stories';

const { Primary, WithInteraction } = composeStories(stories);

test('renders primary button', () => {
  render(<Primary />);
  expect(screen.getByRole('button')).toBeInTheDocument();
});

test('interaction test', async () => {
  const { container } = render(<WithInteraction />);
  await WithInteraction.play({ canvasElement: container });
  // Assertions from play function are executed
});
```

`[SRC:code/renderers/react/src/portable-stories.ts:L18]`

### Custom Manager Addon

Build a custom addon panel using the manager API:

```tsx
// .storybook/manager.ts
import { addons, types } from 'storybook/manager-api';
import { useStorybookApi, useChannel } from 'storybook/manager-api';
import { HIGHLIGHT } from 'storybook/highlight';

addons.register('my-addon', (api) => {
  addons.add('my-addon/panel', {
    type: types.PANEL,
    title: 'My Panel',
    render: ({ active }) => {
      const storybookApi = useStorybookApi();
      const emit = useChannel({});

      const highlight = () => {
        emit(HIGHLIGHT, {
          elements: ['.my-element'],
          color: '#ff4785',
        });
      };

      if (!active) return null;
      return <button onClick={highlight}>Highlight</button>;
    },
  });
});
```

`[SRC:code/core/src/manager-api/index.ts:L12]`
`[SRC:code/core/src/highlight/index.ts:L3]`

### Docs Page Customization

Create a custom documentation page using doc blocks:

```tsx
// src/components/Button.mdx
import { Canvas, Meta, Story, ArgTypes, Source, Title, Description, Primary, Stories } from '@storybook/addon-docs/blocks';
import * as ButtonStories from './Button.stories';

<Meta of={ButtonStories} />

<Title />
<Description />

## Interactive Demo
<Primary />

## All Variants
<Stories />

## Props
<ArgTypes of={ButtonStories} />
```

`[SRC:code/addons/docs/src/blocks/Canvas.tsx:L12]`
`[SRC:code/addons/docs/src/blocks/ArgTypes.tsx:L8]`

### Vite Configuration Customization

Extend the Vite config via `viteFinal`:

```ts
// .storybook/main.ts
import type { StorybookConfig } from '@storybook/react-vite';

const config: StorybookConfig = {
  stories: ['../src/**/*.stories.@(ts|tsx)'],
  framework: '@storybook/react-vite',
  async viteFinal(config) {
    const { mergeConfig } = await import('vite');
    return mergeConfig(config, {
      resolve: {
        alias: { '@': '/src' },
      },
      css: {
        modules: { localsConvention: 'camelCase' },
      },
    });
  },
};
export default config;
```

Use `withoutVitePlugins` and `hasVitePlugins` from `@storybook/builder-vite` to manage plugin conflicts:

```ts
import { withoutVitePlugins } from '@storybook/builder-vite';

async viteFinal(config) {
  return {
    ...config,
    plugins: await withoutVitePlugins(config.plugins, ['vite:legacy']),
  };
}
```

`[SRC:code/builders/builder-vite/src/utils/without-vite-plugins.ts:L3]`
`[SRC:code/builders/builder-vite/src/types.ts:L5]`
