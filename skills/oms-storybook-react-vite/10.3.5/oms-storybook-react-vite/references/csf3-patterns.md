# CSF3 / CSF4 Story Patterns — Verbatim Samples

These samples come directly from `code/renderers/react/template/stories/` — the Storybook repo's own canonical exemplars for v10 React story authoring. Use them as the **reference shape** for generated story code. All T1.

## Contents

- [CSF3 core pattern](#csf3-core-pattern) — `satisfies Meta<typeof X>`, named-export stories
- [Sample 1: Decorators](#sample-1-decorators)
- [Sample 2: Play function with args assertions](#sample-2-play-function-with-args-assertions)
- [Sample 3: Component testing with `mount`](#sample-3-component-testing-with-mount)
- [Sample 4: Hooks in `render`](#sample-4-hooks-in-render)
- [Sample 5: Context provider decorator](#sample-5-context-provider-decorator)
- [Sample 6: CSF4 factory API](#sample-6-csf4-factory-api)
- [Common CSF3 vs CSF2 pitfalls](#common-csf3-vs-csf2-pitfalls)

## CSF3 core pattern

```tsx
import type { Meta, StoryObj } from '@storybook/react-vite';  // or '@storybook/react'
import { Button } from './Button';

const meta = {
  component: Button,
  args: { label: 'Default' },
  tags: ['autodocs'],
} satisfies Meta<typeof Button>;

export default meta;
type Story = StoryObj<typeof meta>;

export const Primary: Story = {
  args: { variant: 'primary' },
};

export const WithPlay: Story = {
  play: async ({ canvas, userEvent }) => {
    await userEvent.click(canvas.getByRole('button'));
  },
};
```

Required shape:
- `const meta = { ... } satisfies Meta<typeof Component>` — **use `satisfies`**, not `as`, so `meta.args` retains narrow types for `StoryObj<typeof meta>`.
- `export default meta` — always.
- `type Story = StoryObj<typeof meta>` — typedef aliased for each story export.
- Named exports (`export const Primary`), never a default-exported array of stories (that's CSF2).
- `args` inherited from meta; override per-story in `args`.

## Sample 1: Decorators

Source: `code/renderers/react/template/stories/decorators.stories.tsx`

```tsx
import type { FC } from 'react';
import React, { createContext, useContext, useState } from 'react';
import type { Meta, StoryObj } from '@storybook/react';
import { useParameter } from 'storybook/preview-api';
```

```tsx
export default {
  component: Component,
  tags: ['autodocs'],
  decorators: [
    (Story) => (
      <>
        <p>Component Decorator</p>
        <Story />
      </>
    ),
  ],
} as Meta<typeof Component>;
```

```tsx
export const All: StoryObj<typeof Component> = {
  decorators: [
    (Story) => (
      <>
        <p>Local Decorator</p>
        <Story />
      </>
    ),
  ],
};
```

**Pattern notes:** Demonstrates component-level and story-level decorators combined. `tags: ['autodocs']` enables Autodocs for the component.

## Sample 2: Play function with args assertions

Source: `code/renderers/react/template/stories/test-fn.stories.tsx`

```tsx
import React from 'react';
import type { StoryContext } from '@storybook/react';
import { expect, fn } from 'storybook/test';
import preview from './preview';
```

```tsx
const meta = preview.meta({
  component: Button,
  args: {
    children: 'Default',
    onClick: fn(),
  },
  tags: ['some-tag'],
});

export const Default = meta.story({
  args: {
    children: 'Arg from story',
  },
});

Default.test('simple', async ({ canvas, userEvent, args }) => {
  const button = canvas.getByText('Arg from story');
  await userEvent.click(button);
  await expect(args.onClick).toHaveBeenCalled();
});
```

**Pattern notes:** This is CSF4 (factory API) — note `preview.meta(...)` and `Default.test(...)`. It demonstrates:
- `fn()` from `storybook/test` creates a mock that records calls
- `canvas`, `userEvent`, `args` destructured from the play context
- `expect(args.onClick).toHaveBeenCalled()` — standard Vitest/Chai matchers

## Sample 3: Component testing with `mount`

Source: `code/renderers/react/template/stories/mount-in-play.stories.tsx`

```tsx
import type { FC } from 'react';
import React from 'react';
import type { StoryObj } from '@storybook/react';
```

```tsx
export default {
  component: Button,
};

export const Basic: StoryObj<typeof Button> = {
  args: {
    disabled: true,
  },
  async play({ mount, args }) {
    await mount(<Button {...args} label={'set in play'} />);
  },
};
```

**Pattern notes:** Demonstrates the `mount` fixture in `play`. `mount` lets you render a different JSX tree inside the play function — useful when the component requires dynamic setup that depends on args or fetched data.

## Sample 4: Hooks in `render`

Source: `code/renderers/react/template/stories/hooks.stories.tsx`

```tsx
import type { FC } from 'react';
import React, { useState } from 'react';
```

```tsx
export default {
  component: ButtonWithState,
};

export const Basic = {};
```

**Pattern notes:** Shows the **minimum** valid CSF3 story shape — a component reference on meta, a no-arg named export. The component itself uses `useState` because stories can render React components that use their own hooks. No special Storybook hooks needed here.

## Sample 5: Context provider decorator

Source: `code/renderers/react/template/stories/decorators.stories.tsx` (Context variant)

```tsx
export const Context: StoryObj<typeof Component> = {
  parameters: { docs: { source: { excludeDecorators: true } } },
  decorators: [
    (Story) => (
      <TestContext.Provider value>
        <Story />
      </TestContext.Provider>
    ),
  ],
  render: function Render() {
    const value = useContext(TestContext);
    if (!value) {
      throw new Error('TestContext not set, decorator did not run!');
    }
    return <p>Story</p>;
  },
};
```

**Pattern notes:** Shows:
- Story-level `decorators` wrapping in a context provider
- `render` function override using hooks (`useContext`)
- `parameters.docs.source.excludeDecorators: true` — omit decorator code from the docs source panel
- Runtime assertion inside `render` to catch misconfigured decorator chains

## Sample 6: CSF4 factory API

See Sample 2 above — `preview.meta(...)` and `Default.test(...)` are the CSF4 factory syntax. The key import is `import preview from './preview'` where `./preview` exports a `ReactPreview` built with `definePreview(...)` from `@storybook/react`.

## Common CSF3 vs CSF2 pitfalls

**CSF2 (wrong for v10) — do not generate:**
```tsx
export default {
  title: 'Button',
  component: Button,
};

// Default export array form — CSF2
const Template = (args) => <Button {...args} />;
export const Primary = Template.bind({});
Primary.args = { label: 'Primary' };
```

**CSF3 (correct for v10):**
```tsx
const meta = { component: Button } satisfies Meta<typeof Button>;
export default meta;
type Story = StoryObj<typeof meta>;

export const Primary: Story = {
  args: { label: 'Primary' },
};
```

**Other v10 import gotchas:**
- `import { fn } from 'storybook/test'` ✓ — NOT `'@storybook/test'` (deprecated) `[QMD:oms-storybook-react-vite-temporal:issues.md #9b8716]`
- `import { useArgs } from 'storybook/preview-api'` ✓ — NOT `'@storybook/preview-api'`
- `import { create } from 'storybook/theming/create'` ✓ — NOT `'@storybook/theming/create'`
- `import { Canvas, Meta } from '@storybook/addon-docs/blocks'` ✓ — NOT `'@storybook/blocks'` (v9 path, removed in v10)
- Types can come from `'@storybook/react-vite'` or `'@storybook/react'` — both work. Prefer `react-vite` for framework alignment.

`[AST:code/renderers/react/template/stories/decorators.stories.tsx:L1]` `[AST:code/renderers/react/template/stories/test-fn.stories.tsx:L1]` `[AST:code/renderers/react/template/stories/mount-in-play.stories.tsx:L1]` `[AST:code/core/package.json:L48]`
