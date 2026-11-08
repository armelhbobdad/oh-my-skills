---
workflowType: 'test-skill'
skillName: 'oms-storybook-react-vite'
skillDir: 'skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite'
runId: '20261108T143553Z-31d5d0c1'
testMode: 'naive'
forgeTier: 'Deep'
hardGate: 'passed'
testResult: 'pass'
score: '100%'
threshold: '80%'
thresholdSource: 'workflow default (80%)'
analysisConfidence: 'full'
toolingStatus: 'ok'
workspaceDrift: 'ok'
health_check_dispatched: true
testDate: '2026-11-08T14:35:53Z'
stepsCompleted: ['init', 'detect-mode', 'coverage-check', 'coherence-check', 'external-validators', 'hard-gate', 'score', 'report']
nextWorkflow: 'export-skill'
---

# Test Report: oms-storybook-react-vite

<!--
Each stage writes its section in place of the heading below that it owns and
the placeholder comment under that heading, so every heading occurs once.
Before the result files are written, report.md §4c checks that each heading
occurs exactly once, that no placeholder comment is left and that the title
above names the skill (init.md §6c fills it): a stage that skipped its
section stops the run there. Do not change the title line, and do not
reorder or delete the headings or their placeholder comments.

Heading / owning step:
  Test Summary        → detect-mode §2
  Coverage Analysis   → coverage-check §5
  Coherence Analysis  → coherence-check §6
  External Validation → external-validators §5
  (hard gate)         → step-hard-gate reads the gap ledger; it writes the
                        Completeness Score section only when it blocks the run
  Completeness Score  → score §6, or step-hard-gate §3 on a blocked run
  Gap Report          → report §4c, rendered from the gap ledger (with the
                        Discovery Quality subsection)
-->

## Test Summary

**Skill:** oms-storybook-react-vite
**Test Mode:** naive
**Forge Tier:** Deep

**Mode Rationale:** metadata.json records `skill_type: "single"`, an individual skill, so the run takes naive mode: API-surface coverage, with a structural-only coherence check and no coherence category in the score.

**Analysis Plan:**
- Coverage Check: every documented export of SKILL.md and references/*.md checked against the pinned Storybook source (v10.3.5, e486d38) at Deep tier: name coverage, signature accuracy and type coverage, read from the local source tree with AST-backed tools (ast-grep), QMD and gh available.
- Coherence Check: structural only (naive mode): references named in SKILL.md resolve, and metadata.json agrees with the skill body; not scored as a category.

## Coverage Analysis

**Tier:** Deep
**Source Access:** full
**Source Path:** /home/armel/.skf/workspace/repos/github.com/storybookjs/storybook
**Workspace Layout:** npm-workspaces
**Denominator:** Stratified scope, denominator: effective_denominator (124 files define its names, 370 exports union)

**Denominator Candidates** (stratified-scope audit trail):
- `stats.effective_denominator`: 370  ← chosen on the scalar branch
- `scope.tier_a_include` union: 370
- `scope.include` union: 1157
- exports-map subpath union: 1424
- root barrel: 63

**Files Analyzed:** 304

### Export Coverage

| Export | Type | Documented | Signature | Source Location | Status |
|--------|------|------------|-----------|-----------------|--------|
| `A` | - | yes | - | - | WARN |
| `A11Y_ADDON_ID` | const | yes | - | code/addons/a11y/src/constants.ts:1 | PASS |
| `A11Y_PANEL_ID` | const | yes | - | code/addons/a11y/src/constants.ts:2 | PASS |
| `A11yGlobals` | interface | yes | - | code/addons/a11y/src/types.ts:16 | PASS |
| `A11yParameters` | interface | yes | - | code/addons/a11y/src/params.ts:20 | PASS |
| `A11yReport` | type | yes | - | code/addons/a11y/src/types.ts:5 | PASS |
| `A11yTypes` | interface | yes | - | code/addons/a11y/src/types.ts:55 | PASS |
| `ADDON_ID` | const | yes | - | code/addons/vitest/src/constants.ts:11 | PASS |
| `ActionBar` | - | yes | - | - | WARN |
| `ActionDisplay` | interface | yes | - | code/core/src/actions/models/ActionDisplay.ts:3 | PASS |
| `ActionList` | - | yes | - | - | WARN |
| `ActionOptions` | type | yes | - | code/core/src/actions/models/ActionOptions.ts:11 | PASS |
| `ActionsFunction` | interface | yes | - | code/core/src/actions/models/ActionsFunction.ts:4 | PASS |
| `ActionsMap` | type | yes | - | code/core/src/actions/models/ActionsMap.ts:3 | PASS |
| `AddContext` | function | yes | yes | code/addons/docs/src/blocks/blocks/mdx.tsx:27 | PASS |
| `AddMocks` | type | yes | - | code/renderers/react/src/public-types.ts:69 | PASS |
| `AddonPanel` | - | yes | - | - | WARN |
| `Anchor` | function | yes | yes | code/addons/docs/src/blocks/blocks/Anchor.tsx:10 | PASS |
| `AnchorMdx` | function | yes | yes | code/addons/docs/src/blocks/blocks/mdx.tsx:98 | PASS |
| `AnchorProps` | interface | yes | - | code/addons/docs/src/blocks/blocks/Anchor.tsx:6 | PASS |
| `Animation` | type | yes | - | code/core/src/theming/types.ts:60 | PASS |
| `ArgTypes` | const | yes | yes | code/addons/docs/src/blocks/blocks/ArgTypes.tsx:108 | PASS |
| `Background` | type | yes | - | code/core/src/theming/types.ts:58 | PASS |
| `Badge` | - | yes | - | - | WARN |
| `Bar` | - | yes | - | - | WARN |
| `Blockquote` | - | yes | - | - | WARN |
| `BooleanConfig` | interface | yes | - | code/addons/docs/src/blocks/controls/types.ts:14 | PASS |
| `BooleanControl` | function | yes | - | code/addons/docs/src/blocks/controls/Boolean.tsx:117 | PASS |
| `BooleanProps` | type | yes | - | code/addons/docs/src/blocks/controls/Boolean.tsx:104 | PASS |
| `BooleanValue` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:13 | PASS |
| `Brand` | interface | yes | - | code/core/src/theming/types.ts:64 | PASS |
| `BuilderOptions` | type | yes | - | code/builders/builder-vite/src/types.ts:21 | PASS |
| `Button` | - | yes | - | - | WARN |
| `CLEAR_ID` | const | yes | - | code/core/src/actions/constants.ts:5 | PASS |
| `CYCLIC_KEY` | const | yes | - | code/core/src/actions/constants.ts:6 | PASS |
| `Canvas` | const | yes | yes | code/addons/docs/src/blocks/blocks/Canvas.tsx:100 | PASS |
| `Card` | - | yes | - | - | WARN |
| `Channel` | - | yes | - | - | WARN |
| `CheckboxControl` | - | yes | - | - | WARN |
| `ClassNameStrategyConfiguration` | interface | yes | - | code/addons/themes/src/decorators/class-name.decorator.tsx:8 | PASS |
| `ClickEventDetails` | interface | yes | - | code/core/src/highlight/types.ts:60 | PASS |
| `Code` | - | yes | - | - | WARN |
| `CodeOrSourceMdx` | function | yes | yes | code/addons/docs/src/blocks/blocks/mdx.tsx:39 | PASS |
| `Collapsible` | - | yes | - | - | WARN |
| `Color` | type | yes | - | code/core/src/theming/types.ts:57 | PASS |
| `ColorConfig` | interface | yes | - | code/addons/docs/src/blocks/controls/types.ts:18 | PASS |
| `ColorControl` | function | yes | yes | code/addons/docs/src/blocks/controls/index.tsx:14 | PASS |
| `ColorControlProps` | - | yes | - | - | WARN |
| `ColorItem` | function | yes | yes | code/addons/docs/src/blocks/components/ColorPalette.tsx:182 | PASS |
| `ColorPalette` | function | yes | yes | code/addons/docs/src/blocks/components/ColorPalette.tsx:202 | PASS |
| `ColorProps` | type | yes | - | code/addons/docs/src/blocks/controls/index.tsx:10 | PASS |
| `ColorValue` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:16 | PASS |
| `Component` | type | yes | - | code/addons/docs/src/blocks/blocks/types.ts:7 | PASS |
| `ConfigFile` | - | yes | - | - | WARN |
| `ContextObjectWithoutNode` | type | yes | - | code/addons/a11y/src/params.ts:6 | PASS |
| `ContextSpecWithoutNode` | type | yes | - | code/addons/a11y/src/params.ts:16 | PASS |
| `Control` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:82 | PASS |
| `ControlProps` | interface | yes | - | code/addons/docs/src/blocks/controls/types.ts:3 | PASS |
| `ControlType` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:71 | PASS |
| `Controls` | const | yes | yes | code/addons/docs/src/blocks/blocks/Controls.tsx:109 | PASS |
| `CsfFile` | - | yes | - | - | WARN |
| `DEFAULT_VIEWPORT` | const | yes | - | code/core/src/viewport/defaults.ts:232 | PASS |
| `DL` | - | yes | - | - | WARN |
| `DataAttributeStrategyConfiguration` | interface | yes | - | code/addons/themes/src/decorators/data-attribute.decorator.tsx:8 | PASS |
| `DateConfig` | interface | yes | - | code/addons/docs/src/blocks/controls/types.ts:29 | PASS |
| `DateControl` | function | yes | - | code/addons/docs/src/blocks/controls/Date.tsx:69 | PASS |
| `DateProps` | type | yes | - | code/addons/docs/src/blocks/controls/Date.tsx:68 | PASS |
| `DateValue` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:28 | PASS |
| `Decorator` | type | yes | - | code/renderers/react/src/public-types.ts:77 | PASS |
| `DecoratorFunction` | type | yes | - | code/core/src/actions/models/DecoratorFunction.ts:1 | PASS |
| `DecoratorHelpers` | - | yes | - | - | WARN |
| `Description` | const | yes | yes | code/addons/docs/src/blocks/blocks/Description.tsx:74 | PASS |
| `DescriptionType` | enum | yes | - | code/addons/docs/src/blocks/blocks/Description.tsx:9 | PASS |
| `Div` | - | yes | - | - | WARN |
| `Docs` | function | yes | yes | code/addons/docs/src/blocks/blocks/Docs.tsx:17 | PASS |
| `DocsContainer` | function | yes | yes | code/addons/docs/src/blocks/blocks/DocsContainer.tsx:23 | PASS |
| `DocsContainerProps` | interface | yes | - | code/addons/docs/src/blocks/blocks/DocsContainer.tsx:18 | PASS |
| `DocsContext` | const | yes | - | code/addons/docs/src/blocks/blocks/DocsContext.ts:18 | PASS |
| `DocsPage` | function | yes | - | code/addons/docs/src/blocks/blocks/DocsPage.tsx:12 | PASS |
| `DocsProps` | type | yes | - | code/addons/docs/src/blocks/blocks/Docs.tsx:12 | PASS |
| `DocsRenderer` | class | yes | - | code/addons/docs/src/DocsRenderer.tsx:48 | PASS |
| `DocsStory` | const | yes | yes | code/addons/docs/src/blocks/blocks/DocsStory.tsx:42 | PASS |
| `DocsStoryProps` | type | yes | - | code/addons/docs/src/blocks/blocks/types.ts:9 | PASS |
| `DocsTypes` | interface | yes | - | code/addons/docs/src/types.ts:254 | PASS |
| `EVENT_ID` | const | yes | - | code/core/src/actions/constants.ts:4 | PASS |
| `Easing` | type | yes | - | code/core/src/theming/types.ts:61 | PASS |
| `ErrorFormatter` | - | yes | - | - | WARN |
| `ExternalDocs` | function | yes | yes | code/addons/docs/src/blocks/blocks/external/ExternalDocs.tsx:26 | PASS |
| `ExternalDocsContainer` | function | yes | yes | code/addons/docs/src/blocks/blocks/external/ExternalDocsContainer.tsx:12 | PASS |
| `ExternalDocsProps` | type | yes | - | code/addons/docs/src/blocks/blocks/external/ExternalDocs.tsx:11 | PASS |
| `FilesControl` | function | yes | - | code/addons/docs/src/blocks/controls/Files.tsx:40 | PASS |
| `FilesControlProps` | interface | yes | - | code/addons/docs/src/blocks/controls/Files.tsx:11 | PASS |
| `FlexBar` | - | yes | - | - | WARN |
| `Form` | - | yes | - | - | WARN |
| `FrameworkOptions` | type | yes | - | code/frameworks/react-vite/src/types.ts:14 | PASS |
| `FunctionInterpolation` | type | yes | - | code/core/src/theming/index.ts:23 | PASS |
| `GlobalState` | type | yes | - | code/core/src/viewport/types.ts:16 | PASS |
| `GlobalStateUpdate` | type | yes | - | code/core/src/viewport/types.ts:31 | PASS |
| `H1` | - | yes | - | - | WARN |
| `H6` | - | yes | - | - | WARN |
| `HIGHLIGHT` | const | yes | - | code/core/src/highlight/constants.ts:3 | PASS |
| `HR` | - | yes | - | - | WARN |
| `HandlerFunction` | type | yes | - | code/core/src/actions/models/HandlerFunction.ts:1 | PASS |
| `HeaderMdx` | function | yes | yes | code/addons/docs/src/blocks/blocks/mdx.tsx:215 | PASS |
| `HeadersMdx` | const | yes | - | code/addons/docs/src/blocks/blocks/mdx.tsx:232 | PASS |
| `Heading` | const | yes | yes | code/addons/docs/src/blocks/blocks/Heading.tsx:33 | PASS |
| `HeadingProps` | interface | yes | - | code/addons/docs/src/blocks/blocks/Heading.tsx:11 | PASS |
| `HighlightMenuItem` | interface | yes | - | code/core/src/highlight/types.ts:24 | PASS |
| `HighlightOptions` | interface | yes | - | code/core/src/highlight/types.ts:41 | PASS |
| `HighlightTypes` | interface | yes | - | code/core/src/highlight/types.ts:3 | PASS |
| `HooksContext` | class | yes | - | code/core/src/preview-api/modules/addons/hooks.ts:36 | PASS |
| `INITIAL_VIEWPORTS` | const | yes | - | code/core/src/viewport/defaults.ts:3 | PASS |
| `INTERNAL_DEFAULT_PROJECT_ANNOTATIONS` | const | yes | - | code/renderers/react/src/portable-stories.tsx:58 | PASS |
| `IconButton` | - | yes | - | - | WARN |
| `IconGallery` | function | yes | yes | code/addons/docs/src/blocks/components/IconGallery.tsx:74 | PASS |
| `IconItem` | function | yes | yes | code/addons/docs/src/blocks/components/IconGallery.tsx:62 | PASS |
| `InitialViewportKeys` | type | yes | - | code/core/src/viewport/defaults.ts:230 | PASS |
| `Interpolation` | type | yes | - | code/core/src/theming/index.ts:24 | PASS |
| `LI` | - | yes | - | - | WARN |
| `Loader` | type | yes | - | code/renderers/react/src/public-types.ts:78 | PASS |
| `MINIMAL_VIEWPORTS` | const | yes | - | code/core/src/viewport/defaults.ts:234 | PASS |
| `Markdown` | const | yes | - | code/addons/docs/src/blocks/blocks/Markdown.tsx:55 | PASS |
| `MaybeMocked` | - | yes | - | - | WARN |
| `MaybeMockedDeep` | - | yes | - | - | WARN |
| `MaybePartiallyMocked` | - | yes | - | - | WARN |
| `MaybePartiallyMockedDeep` | - | yes | - | - | WARN |
| `Meta` | function | yes | yes | code/addons/docs/src/blocks/blocks/Meta.tsx:15 | PASS |
| `Mock` | - | yes | - | - | WARN |
| `MockInstance` | - | yes | - | - | WARN |
| `Modal` | - | yes | - | - | WARN |
| `NormalizedOptionsConfig` | interface | yes | - | code/addons/docs/src/blocks/controls/types.ts:62 | PASS |
| `NumberConfig` | interface | yes | - | code/addons/docs/src/blocks/controls/types.ts:32 | PASS |
| `NumberControl` | function | yes | - | code/addons/docs/src/blocks/controls/Number.tsx:28 | PASS |
| `NumberValue` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:31 | PASS |
| `OL` | - | yes | - | - | WARN |
| `ObjectConfig` | interface | yes | - | code/addons/docs/src/blocks/controls/types.ts:41 | PASS |
| `ObjectControl` | function | yes | - | code/addons/docs/src/blocks/controls/Object.tsx:166 | PASS |
| `ObjectProps` | type | yes | - | code/addons/docs/src/blocks/controls/Object.tsx:164 | PASS |
| `ObjectValue` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:40 | PASS |
| `Of` | type | yes | - | code/addons/docs/src/blocks/blocks/useOf.ts:11 | PASS |
| `Options` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:48 | PASS |
| `OptionsArray` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:46 | PASS |
| `OptionsConfig` | interface | yes | - | code/addons/docs/src/blocks/controls/types.ts:57 | PASS |
| `OptionsControl` | function | yes | - | code/addons/docs/src/blocks/controls/options/Options.tsx:41 | PASS |
| `OptionsControlType` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:49 | PASS |
| `OptionsMultiSelection` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:44 | PASS |
| `OptionsObject` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:47 | PASS |
| `OptionsProps` | type | yes | - | code/addons/docs/src/blocks/controls/options/Options.tsx:40 | PASS |
| `OptionsSelection` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:45 | PASS |
| `OptionsSingleSelection` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:43 | PASS |
| `P` | - | yes | - | - | WARN |
| `PANEL_ID` | const | yes | - | code/core/src/actions/constants.ts:3 | PASS |
| `PARAM_KEY` | const | yes | - | code/addons/a11y/src/constants.ts:3 | PASS |
| `PRIMARY_STORY` | const | yes | - | code/addons/docs/src/blocks/blocks/types.ts:3 | PASS |
| `Placeholder` | - | yes | - | - | WARN |
| `Popover` | - | yes | - | - | WARN |
| `PopoverProvider` | - | yes | - | - | WARN |
| `PostMessageTransport` | - | yes | - | - | WARN |
| `Pre` | - | yes | - | - | WARN |
| `PresetColor` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:17 | PASS |
| `Preview` | interface | yes | - | code/core/src/csf/csf-factories.ts:26 | PASS |
| `PreviewWeb` | class | yes | - | code/core/src/preview-api/modules/preview-web/PreviewWeb.tsx:11 | PASS |
| `PreviewWithSelection` | class | yes | - | code/core/src/preview-api/modules/preview-web/PreviewWithSelection.tsx:77 | PASS |
| `Primary` | const | yes | yes | code/addons/docs/src/blocks/blocks/Primary.tsx:16 | PASS |
| `PropDescriptor` | type | yes | - | code/core/src/preview-api/modules/store/filterArgTypes.ts:5 | PASS |
| `ProviderStrategyConfiguration` | interface | yes | - | code/addons/themes/src/decorators/provider.decorator.tsx:13 | PASS |
| `PureArgsTable` | function | yes | - | code/addons/docs/src/blocks/components/ArgsTable/ArgsTable.tsx:320 | PASS |
| `REMOVE_HIGHLIGHT` | const | yes | - | code/core/src/highlight/constants.ts:4 | PASS |
| `RESET_HIGHLIGHT` | const | yes | - | code/core/src/highlight/constants.ts:5 | PASS |
| `RadioControl` | - | yes | - | - | WARN |
| `RangeConfig` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:38 | PASS |
| `RangeControl` | function | yes | - | code/addons/docs/src/blocks/controls/Range.tsx:178 | PASS |
| `ReactMeta` | interface | yes | - | code/renderers/react/src/preview.tsx:147 | PASS |
| `ReactParameters` | - | yes | - | - | WARN |
| `ReactPreview` | interface | yes | - | code/renderers/react/src/preview.tsx:102 | PASS |
| `ReactRenderer` | interface | yes | - | code/renderers/react/src/types.ts:8 | PASS |
| `ReactStory` | interface | yes | - | code/renderers/react/src/preview.tsx:249 | PASS |
| `ReactTypes` | interface | yes | - | code/renderers/react/src/types.ts:33 | PASS |
| `Report` | interface | yes | - | code/core/src/preview-api/modules/store/reporter-api.ts:1 | PASS |
| `ReporterAPI` | class | yes | - | code/core/src/preview-api/modules/store/reporter-api.ts:8 | PASS |
| `SCROLL_INTO_VIEW` | const | yes | - | code/core/src/highlight/constants.ts:6 | PASS |
| `ScrollArea` | - | yes | - | - | WARN |
| `Select` | - | yes | - | - | WARN |
| `SelectControl` | - | yes | - | - | WARN |
| `SelectionStore` | interface | yes | - | code/core/src/preview-api/modules/preview-web/SelectionStore.ts:17 | PASS |
| `SelectorWithoutNode` | type | yes | - | code/addons/a11y/src/params.ts:3 | PASS |
| `SortType` | type | yes | - | code/addons/docs/src/blocks/components/ArgsTable/ArgsTable.tsx:186 | PASS |
| `Source` | const | yes | yes | code/addons/docs/src/blocks/blocks/Source.tsx:181 | PASS |
| `SourceContainer` | function | yes | yes | code/addons/docs/src/blocks/blocks/SourceContainer.tsx:38 | PASS |
| `SourceContext` | const | yes | - | code/addons/docs/src/blocks/blocks/SourceContainer.tsx:27 | PASS |
| `SourceContextProps` | interface | yes | - | code/addons/docs/src/blocks/blocks/SourceContainer.tsx:22 | PASS |
| `SourceItem` | interface | yes | - | code/addons/docs/src/blocks/blocks/SourceContainer.tsx:15 | PASS |
| `SourceParameters` | type | yes | - | code/addons/docs/src/blocks/blocks/Source.tsx:16 | PASS |
| `SourceProps` | type | yes | - | code/addons/docs/src/blocks/blocks/Source.tsx:28 | PASS |
| `Spaced` | - | yes | - | - | WARN |
| `Span` | - | yes | - | - | WARN |
| `Stories` | const | yes | yes | code/addons/docs/src/blocks/blocks/Stories.tsx:74 | PASS |
| `Story` | const | yes | yes (Info) | code/addons/docs/src/blocks/blocks/Story.tsx:134 | WARN |
| `StoryContext` | interface | yes | - | code/core/src/csf/story.ts:268 | PASS |
| `StoryFn` | type | yes | - | code/core/src/csf/story.ts:327 | PASS |
| `StoryIndexGenerator` | - | yes | - | - | WARN |
| `StoryObj` | type | yes | - | code/renderers/react/src/public-types.ts:47 | PASS |
| `StoryProps` | type | yes | - | code/addons/docs/src/blocks/blocks/Story.tsx:60 | PASS |
| `StorySources` | type | yes | - | code/addons/docs/src/blocks/blocks/SourceContainer.tsx:20 | PASS |
| `StoryStore` | class | yes | - | code/core/src/preview-api/modules/store/StoryStore.ts:51 | PASS |
| `StorybookConfig` | interface | yes | - | code/core/src/types/modules/core-common.ts:576 | PASS |
| `StorybookConfigVite` | type | yes | - | code/builders/builder-vite/src/types.ts:17 | PASS |
| `StorybookIcon` | - | yes | - | - | WARN |
| `StorybookLogo` | - | yes | - | - | WARN |
| `StorybookTheme` | interface | yes | - | code/core/src/theming/types.ts:71 | PASS |
| `Subheading` | const | yes | yes | code/addons/docs/src/blocks/blocks/Subheading.tsx:23 | PASS |
| `Subtitle` | const | yes | yes | code/addons/docs/src/blocks/blocks/Subtitle.tsx:55 | PASS |
| `SyntaxHighlighter` | - | yes | - | - | WARN |
| `TOOL_ID` | const | yes | - | code/core/src/viewport/constants.ts:4 | PASS |
| `TabBar` | - | yes | - | - | WARN |
| `TabButton` | - | yes | - | - | WARN |
| `TabList` | - | yes | - | - | WARN |
| `TabPanel` | - | yes | - | - | WARN |
| `TabWrapper` | - | yes | - | - | WARN |
| `Table` | - | yes | - | - | WARN |
| `TableOfContents` | function | yes | - | code/addons/docs/src/blocks/components/TableOfContents.tsx:158 | PASS |
| `Tabs` | - | yes | - | - | WARN |
| `TabsView` | - | yes | - | - | WARN |
| `Tag` | type | yes | - | code/core/src/csf/story.ts:16 | PASS |
| `TextConfig` | interface | yes | - | code/addons/docs/src/blocks/controls/types.ts:67 | PASS |
| `TextControl` | function | yes | - | code/addons/docs/src/blocks/controls/Text.tsx:23 | PASS |
| `TextProps` | type | yes | - | code/addons/docs/src/blocks/controls/Text.tsx:11 | PASS |
| `TextSize` | type | yes | - | code/core/src/theming/types.ts:63 | PASS |
| `TextValue` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:66 | PASS |
| `ThemeAddonState` | - | yes | - | - | WARN |
| `ThemeVars` | interface | yes | - | code/core/src/theming/types.ts:4 | PASS |
| `ThemeVarsColors` | interface | yes | - | code/core/src/theming/types.ts:12 | PASS |
| `ThemeVarsPartial` | interface | yes | - | code/core/src/theming/types.ts:6 | PASS |
| `ThemesGlobals` | interface | yes | - | code/addons/themes/src/types.ts:20 | PASS |
| `ThemesParameters` | - | yes | - | - | WARN |
| `ThemesTypes` | interface | yes | - | code/addons/themes/src/types.ts:25 | PASS |
| `Title` | const | yes | yes | code/addons/docs/src/blocks/blocks/Title.tsx:55 | PASS |
| `ToggleButton` | - | yes | - | - | WARN |
| `Toolbar` | - | yes | - | - | WARN |
| `Tooltip` | - | yes | - | - | WARN |
| `TooltipLinkList` | - | yes | - | - | WARN |
| `TooltipNote` | - | yes | - | - | WARN |
| `Typeset` | function | yes | yes | code/addons/docs/src/blocks/components/Typeset.tsx:50 | PASS |
| `Typography` | type | yes | - | code/core/src/theming/types.ts:59 | PASS |
| `UL` | - | yes | - | - | WARN |
| `UNKNOWN_ARGS_HASH` | const | yes | - | code/addons/docs/src/blocks/blocks/SourceContainer.tsx:36 | PASS |
| `Unstyled` | const | yes | - | code/addons/docs/src/blocks/blocks/Unstyled.tsx:9 | PASS |
| `UrlStore` | class | yes | - | code/core/src/preview-api/modules/preview-web/UrlStore.ts:94 | PASS |
| `UserEvent` | interface | yes | - | code/core/src/test/testing-library.ts:119 | PASS |
| `UserEventObject` | type | yes | - | code/core/src/test/index.ts:15 | PASS |
| `View` | interface | yes | - | code/core/src/preview-api/modules/preview-web/View.ts:3 | PASS |
| `Viewport` | interface | yes | - | code/core/src/viewport/types.ts:1 | PASS |
| `ViewportGlobals` | interface | yes | - | code/core/src/viewport/types.ts:56 | PASS |
| `ViewportMap` | type | yes | - | code/core/src/viewport/types.ts:14 | PASS |
| `ViewportParameters` | interface | yes | - | code/core/src/viewport/types.ts:33 | PASS |
| `ViewportStyles` | interface | yes | - | code/core/src/viewport/types.ts:9 | PASS |
| `ViewportType` | type | yes | - | code/core/src/viewport/types.ts:7 | PASS |
| `ViewportTypes` | interface | yes | - | code/core/src/viewport/types.ts:65 | PASS |
| `ViteBuilder` | type | yes | - | code/builders/builder-vite/src/types.ts:10 | PASS |
| `ViteFinal` | type | yes | - | code/builders/builder-vite/src/types.ts:12 | PASS |
| `WebView` | class | yes | - | code/core/src/preview-api/modules/preview-web/WebView.ts:42 | PASS |
| `WebsocketTransport` | - | yes | - | - | WARN |
| `WithTooltip` | - | yes | - | - | WARN |
| `Wrapper` | const | yes | yes | code/addons/docs/src/blocks/blocks/Wrapper.tsx:10 | PASS |
| `Zoom` | - | yes | - | - | WARN |
| `__definePreview` | function | yes | yes | code/renderers/react/src/preview.tsx:55 | PASS |
| `action` | function | yes | yes | code/core/src/actions/runtime/action.ts:50 | PASS |
| `actions` | function | yes | yes | code/core/src/actions/runtime/actions.ts:5 | PASS |
| `addToGlobalContext` | - | yes | - | - | WARN |
| `addons` | const | yes | - | code/addons/docs/src/preset.ts:155 | PASS |
| `anchorBlockIdFromId` | function | yes | yes | code/addons/docs/src/blocks/blocks/Anchor.tsx:4 | PASS |
| `applyHooks` | function | yes | yes | code/core/src/preview-api/modules/addons/hooks.ts:184 | PASS |
| `argsHash` | function | yes | yes | code/addons/docs/src/blocks/blocks/SourceContainer.tsx:11 | PASS |
| `assertIsFn` | function | yes | yes | code/addons/docs/src/blocks/blocks/mdx.tsx:19 | PASS |
| `background` | const | yes | - | code/core/src/theming/base.ts:44 | PASS |
| `buildQueries` | - | yes | yes | code/core/src/test/testing-library.ts:40 | PASS |
| `clearAllMocks` | function | yes | yes | code/core/src/test/spy.ts:77 | PASS |
| `color` | const | yes | - | code/core/src/theming/base.ts:1 | PASS |
| `colors` | - | yes | - | - | WARN |
| `combineArgs` | function | yes | yes | code/core/src/preview-api/modules/store/args.ts:84 | PASS |
| `combineParameters` | function | yes | yes | code/core/src/manager-api/root.tsx:127 | PASS |
| `componentTransform` | - | yes | - | - | WARN |
| `composeConfigs` | function | yes | yes | code/core/src/preview-api/modules/store/csf/composeConfigs.ts:43 | PASS |
| `composeStepRunners` | function | yes | yes | code/core/src/preview-api/modules/store/csf/stepRunners.ts:27 | PASS |
| `composeStories` | function | yes | yes | code/core/src/preview-api/modules/store/csf/portable-stories.ts:274 | PASS |
| `composeStory` | function | yes | yes | code/core/src/preview-api/modules/store/csf/portable-stories.ts:90 | PASS |
| `config` | const | yes | - | code/core/src/actions/runtime/configureActions.ts:3 | PASS |
| `configure` | - | yes | yes | code/core/src/test/testing-library.ts:41 | PASS |
| `configureActions` | function | yes | - | code/core/src/actions/runtime/configureActions.ts:9 | PASS |
| `convert` | function | yes | yes | code/core/src/docs-tools/argTypes/convert/index.ts:8 | PASS |
| `create` | function | yes | yes | code/core/src/theming/create.ts:29 | PASS |
| `createBrowserChannel` | - | yes | - | - | WARN |
| `createEvent` | - | yes | yes | code/core/src/test/testing-library.ts:42 | PASS |
| `createGlobal` | const | yes | - | code/core/src/theming/global.ts:101 | PASS |
| `createPlaywrightTest` | function | yes | yes | code/core/src/preview-api/modules/store/csf/portable-stories.ts:319 | PASS |
| `createReset` | const | yes | - | code/core/src/theming/global.ts:25 | PASS |
| `darken` | const | yes | - | code/core/src/theming/utils.ts:62 | PASS |
| `decorateStory` | function | yes | yes | code/core/src/preview-api/modules/store/decorators.ts:10 | PASS |
| `default` | function | yes | - | code/addons/a11y/src/postinstall.ts:5 | PASS |
| `defaultDecorateStory` | function | yes | yes | code/core/src/preview-api/modules/store/decorators.ts:49 | PASS |
| `defineMain` | function | yes | yes | code/frameworks/react-vite/src/node/index.ts:3 | PASS |
| `emitTransformCode` | function | yes | yes | code/core/src/preview-api/modules/preview-web/emitTransformCode.ts:15 | PASS |
| `enrichCsf` | - | yes | - | - | WARN |
| `ensure` | function | yes | yes | code/core/src/theming/ensure.ts:10 | PASS |
| `expect` | - | yes | - | code/core/src/test/index.ts:24 | PASS |
| `experimental_loadStorybook` | - | yes | - | - | WARN |
| `extractTitle` | function | yes | yes | code/addons/docs/src/blocks/blocks/Title.tsx:24 | PASS |
| `filterArgTypes` | function | yes | yes | code/core/src/preview-api/modules/store/filterArgTypes.ts:10 | PASS |
| `findAllByAltText` | - | yes | yes | code/core/src/test/testing-library.ts:44 | PASS |
| `findAllByDisplayValue` | - | yes | yes | code/core/src/test/testing-library.ts:45 | PASS |
| `findAllByLabelText` | - | yes | yes | code/core/src/test/testing-library.ts:46 | PASS |
| `findAllByPlaceholderText` | - | yes | yes | code/core/src/test/testing-library.ts:47 | PASS |
| `findAllByRole` | - | yes | yes | code/core/src/test/testing-library.ts:48 | PASS |
| `findAllByTestId` | - | yes | yes | code/core/src/test/testing-library.ts:49 | PASS |
| `findAllByText` | - | yes | yes | code/core/src/test/testing-library.ts:50 | PASS |
| `findAllByTitle` | - | yes | yes | code/core/src/test/testing-library.ts:51 | PASS |
| `findByAltText` | - | yes | yes | code/core/src/test/testing-library.ts:52 | PASS |
| `findByDisplayValue` | - | yes | yes | code/core/src/test/testing-library.ts:53 | PASS |
| `findByLabelText` | - | yes | yes | code/core/src/test/testing-library.ts:54 | PASS |
| `findByPlaceholderText` | - | yes | yes | code/core/src/test/testing-library.ts:55 | PASS |
| `findByRole` | - | yes | yes | code/core/src/test/testing-library.ts:56 | PASS |
| `findByTestId` | - | yes | yes | code/core/src/test/testing-library.ts:57 | PASS |
| `findByText` | - | yes | yes | code/core/src/test/testing-library.ts:58 | PASS |
| `findByTitle` | - | yes | yes | code/core/src/test/testing-library.ts:59 | PASS |
| `fireEvent` | - | yes | - | code/core/src/test/testing-library.ts:43 | PASS |
| `fn` | function | yes | yes | code/core/src/test/spy.ts:48 | PASS |
| `format` | function | yes | yes | code/addons/docs/src/blocks/controls/Number.tsx:22 | PASS |
| `formatDate` | function | yes | yes | code/addons/docs/src/blocks/controls/Date.tsx:26 | PASS |
| `formatTime` | function | yes | yes | code/addons/docs/src/blocks/controls/Date.tsx:34 | PASS |
| `generate` | - | yes | - | - | WARN |
| `generateStoryFile` | - | yes | - | - | WARN |
| `getAllByAltText` | - | yes | yes | code/core/src/test/testing-library.ts:60 | PASS |
| `getAllByDisplayValue` | - | yes | yes | code/core/src/test/testing-library.ts:61 | PASS |
| `getAllByLabelText` | - | yes | yes | code/core/src/test/testing-library.ts:62 | PASS |
| `getAllByPlaceholderText` | - | yes | yes | code/core/src/test/testing-library.ts:63 | PASS |
| `getAllByRole` | - | yes | yes | code/core/src/test/testing-library.ts:64 | PASS |
| `getAllByTestId` | - | yes | yes | code/core/src/test/testing-library.ts:65 | PASS |
| `getAllByText` | - | yes | yes | code/core/src/test/testing-library.ts:66 | PASS |
| `getAllByTitle` | - | yes | yes | code/core/src/test/testing-library.ts:67 | PASS |
| `getByAltText` | - | yes | yes | code/core/src/test/testing-library.ts:68 | PASS |
| `getByDisplayValue` | - | yes | yes | code/core/src/test/testing-library.ts:69 | PASS |
| `getByLabelText` | - | yes | yes | code/core/src/test/testing-library.ts:70 | PASS |
| `getByPlaceholderText` | - | yes | yes | code/core/src/test/testing-library.ts:71 | PASS |
| `getByRole` | - | yes | yes | code/core/src/test/testing-library.ts:72 | PASS |
| `getByTestId` | - | yes | yes | code/core/src/test/testing-library.ts:73 | PASS |
| `getByText` | - | yes | yes | code/core/src/test/testing-library.ts:74 | PASS |
| `getByTitle` | - | yes | yes | code/core/src/test/testing-library.ts:75 | PASS |
| `getConfig` | - | yes | yes | code/core/src/test/testing-library.ts:76 | PASS |
| `getCsfFactoryAnnotations` | function | yes | yes | code/core/src/preview-api/modules/store/csf/csf-factory-utils.ts:10 | PASS |
| `getDefaultNormalizer` | - | yes | yes | code/core/src/test/testing-library.ts:77 | PASS |
| `getElementError` | - | yes | yes | code/core/src/test/testing-library.ts:78 | PASS |
| `getNodeText` | - | yes | yes | code/core/src/test/testing-library.ts:79 | PASS |
| `getPreferredColorScheme` | function | yes | - | code/core/src/theming/utils.ts:66 | PASS |
| `getQueriesForElement` | - | yes | yes | code/core/src/test/testing-library.ts:80 | PASS |
| `getRoles` | - | yes | yes | code/core/src/test/testing-library.ts:81 | PASS |
| `getSessionId` | - | yes | - | - | WARN |
| `getStoryHref` | - | yes | - | - | WARN |
| `getStoryId` | function | yes | yes | code/addons/docs/src/blocks/blocks/Story.tsx:62 | PASS |
| `getStoryProps` | function | yes | yes | code/addons/docs/src/blocks/blocks/Story.tsx:75 | PASS |
| `getStorySortParameter` | - | yes | - | - | WARN |
| `getStorybookMetadata` | - | yes | - | - | WARN |
| `getSuggestedQuery` | - | yes | yes | code/core/src/test/testing-library.ts:82 | PASS |
| `hasVitePlugins` | function | yes | yes | code/builders/builder-vite/src/utils/has-vite-plugins.ts:13 | PASS |
| `ignoreSsrWarning` | const | yes | - | code/core/src/theming/index.ts:43 | PASS |
| `inferControls` | function | yes | - | code/core/src/preview-api/modules/store/inferControls.ts:66 | PASS |
| `initializeThemeState` | function | yes | yes | code/addons/themes/src/decorators/helpers.ts:34 | PASS |
| `isInaccessible` | - | yes | yes | code/core/src/test/testing-library.ts:83 | PASS |
| `isMockFunction` | - | yes | yes | code/core/src/test/spy.ts | PASS |
| `lighten` | const | yes | - | code/core/src/theming/utils.ts:61 | PASS |
| `logDOM` | - | yes | yes | code/core/src/test/testing-library.ts:84 | PASS |
| `logRoles` | - | yes | yes | code/core/src/test/testing-library.ts:85 | PASS |
| `logTracker` | - | yes | - | - | WARN |
| `makeDecorator` | function | yes | - | code/core/src/preview-api/modules/addons/make-decorator.ts:44 | PASS |
| `mockChannel` | function | yes | yes | code/core/src/manager-api/lib/storybook-channel-mock.ts:3 | PASS |
| `mocked` | function | yes | yes | code/core/src/test/spy.ts:119 | PASS |
| `mocks` | - | yes | - | code/core/src/test/spy.ts | PASS |
| `normalizeArrays` | function | yes | yes | code/core/src/preview-api/modules/store/csf/normalizeArrays.ts:1 | PASS |
| `normalizeProjectAnnotations` | function | yes | yes | code/core/src/preview-api/modules/store/csf/normalizeProjectAnnotations.ts:17 | PASS |
| `normalizeStory` | function | yes | yes | code/core/src/preview-api/modules/store/csf/normalizeStory.ts:25 | PASS |
| `onMockCall` | function | yes | yes | code/core/src/test/spy.ts:35 | PASS |
| `parse` | function | yes | yes | code/addons/docs/src/blocks/controls/Number.tsx:17 | PASS |
| `parseDate` | function | yes | yes | code/addons/docs/src/blocks/controls/Date.tsx:11 | PASS |
| `parseTime` | function | yes | yes | code/addons/docs/src/blocks/controls/Date.tsx:18 | PASS |
| `pauseAnimations` | function | yes | yes | code/core/src/preview-api/modules/preview-web/render/animation-utils.ts:18 | PASS |
| `pluckThemeFromContext` | function | yes | yes | code/addons/themes/src/decorators/helpers.ts:16 | PASS |
| `prepareMeta` | function | yes | yes | code/core/src/preview-api/modules/store/csf/prepareStory.ts:171 | PASS |
| `prepareStory` | function | yes | yes | code/core/src/preview-api/modules/store/csf/prepareStory.ts:37 | PASS |
| `prettyDOM` | - | yes | yes | code/core/src/test/testing-library.ts:86 | PASS |
| `prettyFormat` | - | yes | - | code/core/src/test/testing-library.ts:111 | PASS |
| `prompt` | - | yes | - | - | WARN |
| `queries` | - | yes | - | code/core/src/test/testing-library.ts:87 | PASS |
| `queryAllByAltText` | - | yes | yes | code/core/src/test/testing-library.ts:88 | PASS |
| `queryAllByAttribute` | - | yes | yes | code/core/src/test/testing-library.ts:89 | PASS |
| `queryAllByDisplayValue` | - | yes | yes | code/core/src/test/testing-library.ts:90 | PASS |
| `queryAllByLabelText` | - | yes | yes | code/core/src/test/testing-library.ts:91 | PASS |
| `queryAllByPlaceholderText` | - | yes | yes | code/core/src/test/testing-library.ts:92 | PASS |
| `queryAllByRole` | - | yes | yes | code/core/src/test/testing-library.ts:93 | PASS |
| `queryAllByTestId` | - | yes | yes | code/core/src/test/testing-library.ts:94 | PASS |
| `queryAllByText` | - | yes | yes | code/core/src/test/testing-library.ts:95 | PASS |
| `queryAllByTitle` | - | yes | yes | code/core/src/test/testing-library.ts:96 | PASS |
| `queryByAltText` | - | yes | yes | code/core/src/test/testing-library.ts:97 | PASS |
| `queryByAttribute` | - | yes | yes | code/core/src/test/testing-library.ts:98 | PASS |
| `queryByDisplayValue` | - | yes | yes | code/core/src/test/testing-library.ts:99 | PASS |
| `queryByLabelText` | - | yes | yes | code/core/src/test/testing-library.ts:100 | PASS |
| `queryByPlaceholderText` | - | yes | yes | code/core/src/test/testing-library.ts:101 | PASS |
| `queryByRole` | - | yes | yes | code/core/src/test/testing-library.ts:102 | PASS |
| `queryByTestId` | - | yes | yes | code/core/src/test/testing-library.ts:103 | PASS |
| `queryByText` | - | yes | yes | code/core/src/test/testing-library.ts:104 | PASS |
| `queryByTitle` | - | yes | yes | code/core/src/test/testing-library.ts:105 | PASS |
| `queryHelpers` | - | yes | - | code/core/src/test/testing-library.ts:106 | PASS |
| `resetAllMocks` | function | yes | yes | code/core/src/test/spy.ts:89 | PASS |
| `responsiveViewport` | const | yes | - | code/core/src/viewport/responsiveViewport.tsx:4 | PASS |
| `restoreAllMocks` | function | yes | yes | code/core/src/test/spy.ts:98 | PASS |
| `sanitizeStoryContextUpdate` | function | yes | yes | code/core/src/preview-api/modules/store/decorators.ts:30 | PASS |
| `sb` | const | yes | - | code/core/src/test/index.ts:54 | PASS |
| `screen` | - | yes | - | code/core/src/test/testing-library.ts:107 | PASS |
| `setDefaultProjectAnnotations` | function | yes | - | code/core/src/preview-api/modules/store/csf/portable-stories.ts:49 | PASS |
| `setProjectAnnotations` | function | yes | yes | code/core/src/preview-api/modules/store/csf/portable-stories.ts:73 | PASS |
| `simulateDOMContentLoaded` | function | yes | yes | code/core/src/preview-api/modules/preview-web/simulate-pageload.ts:31 | PASS |
| `simulatePageLoad` | function | yes | yes | code/core/src/preview-api/modules/preview-web/simulate-pageload.ts:83 | PASS |
| `slugs` | const | yes | - | code/addons/docs/src/blocks/blocks/Heading.tsx:15 | PASS |
| `sortStoriesV7` | function | yes | yes | code/core/src/preview-api/modules/store/sortStories.ts:37 | PASS |
| `spyOn` | function | yes | yes | code/core/src/test/spy.ts:41 | PASS |
| `srOnlyStyles` | const | yes | - | code/core/src/theming/global.ts:12 | PASS |
| `storybookTest` | function | yes | yes | code/addons/vitest/src/vitest-plugin/index.ts:164 | PASS |
| `telemetry` | - | yes | - | - | WARN |
| `themes` | const | yes | - | code/core/src/theming/create.ts:20 | PASS |
| `tokens` | const | yes | - | code/core/src/theming/base.ts:104 | PASS |
| `traverse` | - | yes | - | - | WARN |
| `typography` | const | yes | - | code/core/src/theming/base.ts:59 | PASS |
| `uninstrumentedUserEvent` | const | yes | - | code/core/src/test/testing-library.ts:121 | PASS |
| `useArgs` | function | yes | yes | code/core/src/manager-api/root.tsx:462 | PASS |
| `useCallback` | function | yes | - | code/core/src/preview-api/modules/addons/hooks.ts:344 | PASS |
| `useChannel` | function | yes | - | code/core/src/manager-api/root.tsx:329 | PASS |
| `useEffect` | function | yes | - | code/core/src/preview-api/modules/addons/hooks.ts:498 | PASS |
| `useGlobals` | function | yes | - | code/core/src/manager-api/root.tsx:481 | PASS |
| `useMemo` | function | yes | - | code/core/src/preview-api/modules/addons/hooks.ts:322 | PASS |
| `useOf` | function | yes | - | code/addons/docs/src/blocks/blocks/useOf.ts:18 | PASS |
| `useParameter` | function | yes | yes | code/core/src/manager-api/root.tsx:346 | PASS |
| `useReducer` | function | yes | - | code/core/src/preview-api/modules/addons/hooks.ts:457 | PASS |
| `useRef` | function | yes | - | code/core/src/preview-api/modules/addons/hooks.ts:367 | PASS |
| `useSourceProps` | function | yes | yes | code/addons/docs/src/blocks/blocks/Source.tsx:101 | PASS |
| `useState` | function | yes | - | code/core/src/preview-api/modules/addons/hooks.ts:418 | PASS |
| `useStoryContext` | function | yes | - | code/core/src/preview-api/modules/addons/hooks.ts:560 | PASS |
| `useTabsState` | - | yes | - | - | WARN |
| `useThemeParameters` | function | yes | yes | code/addons/themes/src/decorators/helpers.ts:20 | PASS |
| `userEvent` | - | yes | - | code/core/src/test/testing-library.ts:123 | PASS |
| `userOrAutoTitle` | function | yes | - | code/core/src/preview-api/modules/store/autoTitle.ts:86 | PASS |
| `userOrAutoTitleFromSpecifier` | function | yes | - | code/core/src/preview-api/modules/store/autoTitle.ts:49 | PASS |
| `vitestTransform` | - | yes | - | - | WARN |
| `waitFor` | - | yes | - | code/core/src/test/testing-library.ts:108 | PASS |
| `waitForAnimations` | function | yes | yes | code/core/src/preview-api/modules/preview-web/render/animation-utils.ts:54 | PASS |
| `waitForElementToBeRemoved` | - | yes | yes | code/core/src/test/testing-library.ts:109 | PASS |
| `withActions` | const | yes | yes | code/core/src/actions/decorator.ts:59 | PASS |
| `withThemeByClassName` | function | yes | yes | code/addons/themes/src/decorators/class-name.decorator.tsx:19 | PASS |
| `withThemeByDataAttribute` | function | yes | yes | code/addons/themes/src/decorators/data-attribute.decorator.tsx:19 | PASS |
| `withThemeFromJSXProvider` | function | yes | yes | code/addons/themes/src/decorators/provider.decorator.tsx:23 | PASS |
| `within` | - | yes | yes | code/core/src/test/testing-library.ts:110 | PASS |
| `withoutVitePlugins` | function | yes | yes | code/builders/builder-vite/src/utils/without-vite-plugins.ts:2 | PASS |

### Coverage Summary

- **Exports Found:** 370
- **Documented:** 370 (100%)
- **Missing Documentation:** 0
- **Signature Mismatches:** 0, plus 1 graded Low or Info and counted as matching
- **Stale Documentation:** 89, documented extras included
- **Scoped Out by the Brief:** `A` (code/core/src/components/components/typography/elements/A.tsx:7), `AbstractToolbar` (code/core/src/components/components/Toolbar/Toolbar.tsx:15), `ActionBar` (code/core/src/components/components/ActionBar/ActionBar.tsx:89), `ActionItem` (code/core/src/components/components/ActionBar/ActionBar.tsx:72), `ActionList` (code/core/src/components/components/ActionList/ActionList.tsx:222), `AddonPanel` (code/core/src/components/components/addon-panel/addon-panel.tsx:36), `AngularMeta` (code/frameworks/angular/src/client/preview.ts:150), `AngularOptions` (code/frameworks/angular/src/types.ts:47), `AngularParameters` (code/frameworks/angular/src/client/types.ts:45), `AngularPreview` (code/frameworks/angular/src/client/preview.ts:81), `AngularRenderer` (code/frameworks/angular/src/client/types.ts:40), `AngularStory` (code/frameworks/angular/src/client/preview.ts:254), `BabelFileClass` (code/core/src/babel/index.ts:43), `BadMetaError` (code/core/src/csf-tools/CsfFile.ts:246), `Badge` (code/core/src/components/components/Badge/Badge.tsx:88), `Bar` (code/core/src/components/components/Bar/Bar.tsx:52), `BarProps` (code/core/src/components/components/Bar/Bar.tsx:7), `BaseLocationProvider` (code/core/src/router/router.tsx:144), `Blockquote` (code/core/src/components/components/typography/elements/Blockquote.tsx:6), `BuildIndexOptions` (code/core/src/core-server/build-index.ts:10), `BuildStaticStandaloneOptions` (code/core/src/core-server/build-static.ts:31), `Button` (code/core/src/components/components/Button/Button.tsx:53), `ButtonProps` (code/core/src/components/components/Button/Button.tsx:14), `CLI_COLORS` (code/core/src/node-logger/logger/colors.ts:3), `CacheEntry` (code/core/src/telemetry/event-cache.ts:12), `Card` (code/core/src/components/components/Card/Card.tsx:98), `Channel` (code/core/src/channels/main.ts:22), `ChannelEvent` (code/core/src/channels/types.ts:18), `ChannelHandler` (code/core/src/channels/types.ts:11), `ChannelLike` (code/core/src/channels/types.ts:36), `ChannelTransport` (code/core/src/channels/types.ts:13), `ClipboardCode` (code/core/src/components/components/clipboard/ClipboardCode.tsx:24), `Code` (code/core/src/components/components/typography/elements/Code.tsx:42), `Collapsible` (code/core/src/components/components/Collapsible/Collapsible.tsx:31), `ComponentArgTypesData` (code/core/src/core-server/utils/get-dummy-args-from-argtypes.ts:8), `ConfigFile` (code/core/src/csf-tools/ConfigFile.ts:140), `ConsoleLogger` (code/core/src/node-logger/logger/console.ts:340), `Context` (code/core/src/telemetry/types.ts:106), `CsfFile` (code/core/src/csf-tools/CsfFile.ts:280), `CsfOptions` (code/core/src/csf-tools/CsfFile.ts:200), `DEEPLY_EQUAL` (code/core/src/router/utils.ts:43), `DL` (code/core/src/components/components/typography/elements/DL.tsx:6), `Dependency` (code/core/src/telemetry/types.ts:48), `Div` (code/core/src/components/components/typography/elements/Div.tsx:5), `DocumentWrapper` (code/core/src/components/components/typography/DocumentWrapper.tsx:3), `EmptyTabContent` (code/core/src/components/components/Tabs/EmptyTabContent.tsx:47), `EnrichCsfOptions` (code/core/src/csf-tools/enrichCsf.ts:6), `ErrorCollector` (code/core/src/telemetry/error-collector.ts:13), `ErrorFormatter` (code/core/src/components/components/ErrorFormatter/ErrorFormatter.tsx:29), `EventType` (code/core/src/telemetry/types.ts:9), `FlexBar` (code/core/src/components/components/Bar/Bar.tsx:129), `Form` (code/core/src/components/components/Form/Form.tsx:11), `GenerateStoryOptions` (code/core/src/core-server/utils/generate-story.ts:21), `GenerateStoryResult` (code/core/src/core-server/utils/generate-story.ts:11), `H1` (code/core/src/components/components/typography/elements/H1.tsx:6), `H2` (code/core/src/components/components/typography/elements/H2.tsx:6), `H3` (code/core/src/components/components/typography/elements/H3.tsx:6), `H4` (code/core/src/components/components/typography/elements/H4.tsx:6), `H5` (code/core/src/components/components/typography/elements/H5.tsx:6), `H6` (code/core/src/components/components/typography/elements/H6.tsx:6), `HEARTBEAT_INTERVAL` (code/core/src/channels/websocket/index.ts:20), `HEARTBEAT_MAX_LATENCY` (code/core/src/channels/websocket/index.ts:21), `HR` (code/core/src/components/components/typography/elements/HR.tsx:3), `IErrorWithStdErrAndStdOut` (code/core/src/telemetry/sanitize.ts:4), `IStory` (code/frameworks/angular/src/client/types.ts:31), `IconButton` (code/core/src/components/components/Button/Button.tsx:327), `Img` (code/core/src/components/components/typography/elements/Img.tsx:3), `InitPayload` (code/core/src/telemetry/types.ts:131), `LI` (code/core/src/components/components/typography/elements/LI.tsx:6), `Link` (code/core/src/components/components/typography/link/link.tsx:198), `LinkProps` (code/core/src/router/types.ts:23), `ListItem` (code/core/src/components/components/tooltip/ListItem.tsx:249), `Listener` (code/core/src/channels/types.ts:24), `Location` (code/core/src/router/router.tsx:81), `LocationProvider` (code/core/src/router/router.tsx:143), `LogLevel` (code/core/src/node-logger/logger/logger.ts:46), `Match` (code/core/src/router/router.tsx:141), `MemoryRouter` (code/core/src/router/router.tsx:145), `MixedFactoryError` (code/core/src/csf-tools/CsfFile.ts:234), `Modal` (code/core/src/components/components/Modal/Modal.tsx:242), `ModalDecorator` (code/core/src/components/components/Modal/Modal.tsx:248), `MultipleMetaError` (code/core/src/csf-tools/CsfFile.ts:222), `NavigateFunction` (code/core/src/router/types.ts:14), `NavigateOptions` (code/core/src/router/types.ts:12), `NoMetaError` (code/core/src/csf-tools/CsfFile.ts:210), `OL` (code/core/src/components/components/typography/elements/OL.tsx:16), `Other` (code/core/src/router/types.ts:7), `P` (code/core/src/components/components/typography/elements/P.tsx:6), `Payload` (code/core/src/telemetry/types.ts:102), `Placeholder` (code/core/src/components/components/placeholder/placeholder.tsx:22), `Popover` (code/core/src/components/components/Popover/Popover.tsx:77), `PopoverProps` (code/core/src/components/components/Popover/Popover.tsx:9), `PopoverProvider` (code/core/src/components/components/Popover/PopoverProvider.tsx:63), `PopoverProviderProps` (code/core/src/components/components/Popover/PopoverProvider.tsx:13), `PopperPlacement` (code/core/src/components/components/shared/overlayHelpers.tsx:22), `PostMessageTransport` (code/core/src/channels/postmessage/index.ts:29), `Pre` (code/core/src/components/components/typography/elements/Pre.tsx:6), `PreactRenderer` (code/renderers/preact/src/types.ts:14), `ProgressSpinner` (code/core/src/components/components/ProgressSpinner/ProgressSpinner.tsx:66), `RenderData` (code/core/src/router/types.ts:21), `ResetWrapper` (code/core/src/components/components/typography/ResetWrapper.tsx:12), `Route` (code/core/src/router/router.tsx:141), `RouterData` (code/core/src/router/types.ts:16), `ScrollArea` (code/core/src/components/components/ScrollArea/ScrollArea.tsx:95), `Select` (code/core/src/components/components/Select/Select.tsx:201), `Separator` (code/core/src/components/components/Bar/Separator.tsx:9), `Spaced` (code/core/src/components/components/spaced/Spaced.tsx:63), `Span` (code/core/src/components/components/typography/elements/Span.tsx:6), `SpinnerInstance` (code/core/src/node-logger/prompts/prompt-provider-base.ts:46), `StatelessTab` (code/core/src/components/components/Tabs/StatelessTab.tsx:57), `StatelessTabList` (code/core/src/components/components/Tabs/StatelessTabList.tsx:66), `StatelessTabListProps` (code/core/src/components/components/Tabs/StatelessTabList.tsx:62), `StatelessTabPanel` (code/core/src/components/components/Tabs/StatelessTabPanel.tsx:30), `StatelessTabPanelProps` (code/core/src/components/components/Tabs/StatelessTabPanel.tsx:9), `StatelessTabProps` (code/core/src/components/components/Tabs/StatelessTab.tsx:7), `StatelessTabsView` (code/core/src/components/components/Tabs/StatelessTabsView.tsx:31), `StatelessTabsViewProps` (code/core/src/components/components/Tabs/StatelessTabsView.tsx:27), `StaticMeta` (code/core/src/csf-tools/CsfFile.ts:258), `StaticStory` (code/core/src/csf-tools/CsfFile.ts:265), `StoryData` (code/core/src/router/utils.ts:9), `StoryIndexGenerator` (code/core/src/core-server/utils/StoryIndexGenerator.ts:101), `StoryTest` (code/core/src/csf-tools/CsfFile.ts:271), `StorybookAddon` (code/core/src/telemetry/types.ts:53), `StorybookBuilderOptions` (code/frameworks/angular/src/builders/build-storybook/index.ts:38), `StorybookBuilderOutput` (code/frameworks/angular/src/builders/build-storybook/index.ts:68), `StorybookIcon` (code/core/src/components/brand/StorybookIcon.tsx:3), `StorybookLogo` (code/core/src/components/brand/StorybookLogo.tsx:7), `StorybookMetadata` (code/core/src/telemetry/types.ts:57), `StyledConsoleLogger` (code/core/src/node-logger/logger/console.ts:340), `SvelteRenderer` (code/renderers/svelte/src/types.ts:11), `SyntaxHighlighter` (code/core/src/components/components/syntaxhighlighter/lazy-syntaxhighlighter.tsx:52), `SyntaxHighlighterFormatTypes` (code/core/src/components/components/syntaxhighlighter/syntaxhighlighter-types.ts:24), `SyntaxHighlighterProps` (code/core/src/components/components/syntaxhighlighter/syntaxhighlighter-types.ts:47), `SyntaxHighlighterRendererProps` (code/core/src/components/components/syntaxhighlighter/syntaxhighlighter-types.ts:5), `TT` (code/core/src/components/components/typography/elements/TT.tsx:5), `TabBar` (code/core/src/components/components/Tabs/Tabs.tsx:61), `TabButton` (code/core/src/components/components/Tabs/Button.tsx:139), `TabList` (code/core/src/components/components/Tabs/TabList.tsx:150), `TabListProps` (code/core/src/components/components/Tabs/TabList.tsx:146), `TabPanel` (code/core/src/components/components/Tabs/TabPanel.tsx:34), `TabPanelProps` (code/core/src/components/components/Tabs/TabPanel.tsx:12), `TabProps` (code/core/src/components/components/Tabs/TabsView.tsx:15), `TabWrapper` (code/core/src/components/components/Tabs/Tabs.tsx:120), `Table` (code/core/src/components/components/typography/elements/Table.tsx:6), `Tabs` (code/core/src/components/components/Tabs/Tabs.tsx:188), `TabsState` (code/core/src/components/components/Tabs/Tabs.tsx:287), `TabsView` (code/core/src/components/components/Tabs/TabsView.tsx:106), `TabsViewProps` (code/core/src/components/components/Tabs/TabsView.tsx:64), `TaskLogInstance` (code/core/src/node-logger/prompts/prompt-provider-base.ts:54), `TelemetryData` (code/core/src/telemetry/types.ts:119), `TelemetryEvent` (code/core/src/telemetry/types.ts:125), `ToggleButton` (code/core/src/components/components/ToggleButton/ToggleButton.tsx:16), `Toolbar` (code/core/src/components/components/Toolbar/Toolbar.tsx:36), `Tooltip` (code/core/src/components/components/tooltip/Tooltip.tsx:7), `TooltipLinkList` (code/core/src/components/components/tooltip/TooltipLinkList.tsx:70), `TooltipLinkListLink` (code/core/src/components/components/tooltip/TooltipLinkList.tsx:39), `TooltipMessage` (code/core/src/components/components/tooltip/TooltipMessage.tsx:47), `TooltipNote` (code/core/src/components/components/tooltip/TooltipNote.tsx:23), `TooltipNoteProps` (code/core/src/components/components/tooltip/TooltipNote.tsx:19), `TooltipProps` (code/core/src/components/components/tooltip/Tooltip.tsx:5), `TooltipProvider` (code/core/src/components/components/tooltip/TooltipProvider.tsx:108), `TooltipProviderProps` (code/core/src/components/components/tooltip/TooltipProvider.tsx:14), `TransformComponentType` (code/frameworks/angular/src/client/public-types.ts:56), `UL` (code/core/src/components/components/typography/elements/UL.tsx:16), `WebComponentsMeta` (code/renderers/web-components/src/preview.ts:160), `WebComponentsPreview` (code/renderers/web-components/src/preview.ts:85), `WebComponentsRenderer` (code/renderers/web-components/src/types.ts:14), `WebComponentsStory` (code/renderers/web-components/src/preview.ts:264), `WebComponentsTypes` (code/renderers/web-components/src/types.ts:24), `WebsocketTransport` (code/core/src/channels/websocket/index.ts:23), `WithTooltip` (code/core/src/components/components/tooltip/lazy-WithTooltip.tsx:8), `WithTooltipPure` (code/core/src/components/components/tooltip/lazy-WithTooltip.tsx:18), `Zoom` (code/core/src/components/components/Zoom/Zoom.tsx:4), `addToGlobalContext` (code/core/src/telemetry/telemetry.ts:26), `applicationConfig` (code/frameworks/angular/src/client/decorators.ts:37), `argsToTemplate` (code/frameworks/angular/src/client/argsToTemplate.ts:59), `babelParseExpression` (code/core/src/babel/babelParse.ts:52), `babelParseFile` (code/core/src/csf-tools/CsfFile.ts:1062), `babelPrint` (code/core/src/babel/babelParse.ts:42), `buildArgsParam` (code/core/src/router/utils.ts:186), `buildDevStandalone` (code/core/src/core-server/build-dev.ts:44), `buildIndex` (code/core/src/core-server/build-index.ts:12), `buildIndexStandalone` (code/core/src/core-server/build-index.ts:39), `buildStaticStandalone` (code/core/src/core-server/build-static.ts:35), `canUpdateVitestConfigFile` (code/core/src/babel/vitest-config-helpers.ts:159), `canUpdateVitestWorkspaceFile` (code/core/src/babel/vitest-config-helpers.ts:204), `cleanPaths` (code/core/src/telemetry/sanitize.ts:24), `codeCommon` (code/core/src/components/components/typography/lib/common.tsx:22), `colors` (code/core/src/node-logger/index.ts:57), `componentTransform` (code/core/src/csf-tools/vitest-plugin/component-transformer.ts:285), `componentWrapperDecorator` (code/frameworks/angular/src/client/decorators.ts:60), `components` (code/core/src/components/index.ts:133), `computeStorybookMetadata` (code/core/src/telemetry/storybook-metadata.ts:105), `convertToReactAriaPlacement` (code/core/src/components/components/shared/overlayHelpers.tsx:24), `createBrowserChannel` (code/core/src/channels/index.ts:32), `createCopyToClipboardFunction` (code/core/src/components/components/syntaxhighlighter/clipboard.ts:26), `createHyperlink` (code/core/src/node-logger/wrap-utils.ts:155), `createReactiveProps` (code/renderers/svelte/static/createReactiveProps.svelte.js:10), `deepDiff` (code/core/src/router/utils.ts:44), `deepMerge` (code/frameworks/angular/src/server/framework-preset-angular-cli.ts:95), `enrichCsf` (code/core/src/csf-tools/enrichCsf.ts:144), `enrichCsfMeta` (code/core/src/csf-tools/enrichCsf.ts:129), `enrichCsfStory` (code/core/src/csf-tools/enrichCsf.ts:12), `experimental_loadStorybook` (code/core/src/core-server/load.ts:18), `extractDescription` (code/core/src/csf-tools/enrichCsf.ts:158), `extractSource` (code/core/src/csf-tools/enrichCsf.ts:152), `formatConfig` (code/core/src/csf-tools/ConfigFile.ts:1165), `formatCsf` (code/core/src/csf-tools/CsfFile.ts:1083), `framework` (code/core/src/core-server/presets/common-override-preset.ts:5), `generate` (code/core/src/babel/index.ts:38), `generateStoryFile` (code/core/src/core-server/utils/generate-story.ts:64), `getConfigObjectFromMergeArg` (code/core/src/babel/vitest-config-helpers.ts:49), `getCustomElements` (code/renderers/web-components/src/framework-api.ts:37), `getEffectiveMergeConfigCall` (code/core/src/babel/vitest-config-helpers.ts:78), `getErrorLevel` (code/core/src/core-server/withTelemetry.ts:40), `getLastEvents` (code/core/src/telemetry/event-cache.ts:41), `getMatch` (code/core/src/router/utils.ts:233), `getPrecedingUpgrade` (code/core/src/telemetry/event-cache.ts:68), `getServerPort` (code/core/src/core-server/utils/server-address.ts:34), `getSessionId` (code/core/src/telemetry/session-id.ts:18), `getStoryHref` (code/core/src/components/components/utils/getStoryHref.ts:15), `getStorySortParameter` (code/core/src/csf-tools/getStorySortParameter.ts:96), `getStorybookMetadata` (code/core/src/telemetry/storybook-metadata.ts:312), `getTargetConfigObject` (code/core/src/babel/vitest-config-helpers.ts:118), `hrefTo` (code/addons/links/src/utils.ts:39), `interleaveSeparators` (code/core/src/components/components/Bar/Separator.tsx:29), `isCsfFactoryPreview` (code/core/src/csf-tools/ConfigFile.ts:1187), `isDefineConfigLike` (code/core/src/babel/vitest-config-helpers.ts:35), `isExampleStoryId` (code/core/src/telemetry/index.ts:26), `isImportedDefineConfigLikeIdentifier` (code/core/src/babel/vitest-config-helpers.ts:18), `isModuleMock` (code/core/src/csf-tools/CsfFile.ts:116), `isTelemetryEnabled` (code/core/src/core-server/withTelemetry.ts:157), `isValidComponent` (code/renderers/web-components/src/framework-api.ts:3), `isValidMetaData` (code/renderers/web-components/src/framework-api.ts:13), `isValidPreviewPath` (code/core/src/csf-tools/CsfFile.ts:43), `linkTo` (code/addons/links/src/utils.ts:61), `loadConfig` (code/core/src/csf-tools/ConfigFile.ts:1160), `loadCsf` (code/core/src/csf-tools/CsfFile.ts:1077), `logTracker` (code/core/src/node-logger/logger/log-tracker.ts:95), `mapStaticDir` (code/core/src/core-server/utils/server-statics.ts:198), `metaFrameworks` (code/core/src/telemetry/storybook-metadata.ts:33), `moduleMetadata` (code/frameworks/angular/src/client/decorators.ts:11), `nameSpaceClassNames` (code/core/src/components/components/typography/DocumentFormatting.tsx:1), `navigate` (code/addons/links/src/utils.ts:36), `oneWayHash` (code/core/src/telemetry/one-way-hash.ts:4), `parsePath` (code/core/src/router/utils.ts:17), `parserOptions` (code/core/src/babel/babelParse.ts:21), `printConfig` (code/core/src/csf-tools/ConfigFile.ts:1169), `printCsf` (code/core/src/csf-tools/CsfFile.ts:1096), `prompt` (code/core/src/node-logger/prompts/index.ts:5), `protectUrls` (code/core/src/node-logger/wrap-utils.ts:70), `queryFromLocation` (code/core/src/router/utils.ts:222), `readConfig` (code/core/src/csf-tools/ConfigFile.ts:1173), `readCsf` (code/core/src/csf-tools/CsfFile.ts:1100), `removeAnsiEscapeCodes` (code/core/src/telemetry/sanitize.ts:15), `resetComponents` (code/core/src/components/index.ts:142), `resolveExpression` (code/core/src/babel/expression-resolver.ts:22), `runNgcc` (code/frameworks/angular/src/server/framework-preset-angular-ivy.ts:37), `sanitizeAddonName` (code/core/src/telemetry/storybook-metadata.ts:50), `sanitizeError` (code/core/src/telemetry/sanitize.ts:64), `sendTelemetryError` (code/core/src/core-server/withTelemetry.ts:91), `setCustomElements` (code/renderers/web-components/src/framework-api.ts:29), `setCustomElementsManifest` (code/renderers/web-components/src/framework-api.ts:33), `stories` (code/core/src/core-server/presets/common-override-preset.ts:18), `stringifyQuery` (code/core/src/router/utils.ts:226), `telemetry` (code/core/src/telemetry/index.ts:31), `traverse` (code/core/src/babel/index.ts:39), `typescript` (code/core/src/core-server/presets/common-override-preset.ts:25), `unwrapTSExpression` (code/core/src/babel/expression-resolver.ts:4), `useNavigate` (code/core/src/router/router.tsx:45), `useTabsState` (code/core/src/components/components/Tabs/TabsView.tsx:30), `vitestTransform` (code/core/src/csf-tools/vitest-plugin/transformer.ts:108), `webpackFinal` (code/frameworks/angular/src/server/framework-preset-angular-cli.ts:15), `withLinks` (code/addons/links/src/utils.ts:110), `withReset` (code/core/src/components/components/typography/lib/common.tsx:36), `withTelemetry` (code/core/src/core-server/withTelemetry.ts:161), `writeConfig` (code/core/src/csf-tools/ConfigFile.ts:1178), `writeCsf` (code/core/src/csf-tools/CsfFile.ts:1105)

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 100% |
| Signature Accuracy | 100% |
| Type Coverage | 100% |

### Coverage Notes

- **Inventory (§1, §1a):** a subagent read SKILL.md and all six reference files (SKILL.md's `## Full` headings are stubs). `validate-inventory.py` accepted its 653 entries on the first pass: no violations, all 391 floor names kept, and no warning, so no compared form is left unbound for want of a place (`at`). 136 names are cross-checked (written in two or more files).
- **Split-body cross-check (§1b):** the reader's cross-check by `signature-comparison-rules.md` found 0 `cross_check_mismatches`, so no `split-body-mismatch` gap and no §5b Split-Body Sources judge.
- **Read by eye (`extraction.readByEye`):** `code/core/src/csf/csf-factories.ts`, `code/core/src/instrumenter/typings.d.ts`, `code/core/src/mocking-utils/esmWalker.ts`, `code/core/src/test/spy.ts` and `code/core/src/typings.d.ts`. ast-grep reported a syntax error in each (`export type * from` and ambient `declare` files). The by-eye read added `isMockFunction` and `mocks` (re-exported by `spy.ts`) to the tier A set, from 368 to 370. `extraction.unread`: none.
- **Unresolved star re-exports** (another package's names, not counted): `code/core/src/test/spy.ts` 15: `export type * from '@vitest/spy';` and `code/core/src/mocking-utils/esmWalker.ts` 37: `export type * from 'estree';`.
- **Extraction gaps:** no recipe found 146 surface names (`extractionGaps`), 73 of them in the tier A set. Their declarations were read at their recorded file and line wherever a check compared them, for example the 66 `storybook/test` testing-library bindings at `code/core/src/test/testing-library.ts:39-112`.
- **Surface warnings:** 39 public entry points lie outside the brief's files in scope (`entry_point_diff.outside_scope`: `code/addons/links`, `storybook/internal/babel`, `/internal/channels`, `/internal/csf-tools`, `/internal/core-server`, `/internal/router`, `/internal/node-logger`, `/internal/telemetry`, `/internal/components` and the other renderers and frameworks). The brief's `scope.exclude` amendments drop them by design, and `effective_denominator` leaves them out.
- **Signature comparison (§2, §2b):** `score-signatures.py plan` listed 170 checks in 68 source files. One judge subagent per `files[]` entry (68 judges) compared them by `signature-comparison-rules.md`. `score` graded 170 of 170 as matching: 0 Critical or Low mismatches, and 1 `omitted-optional` mismatch on a form labelled partial, graded as an Info `Partial signature: Story`. Type Coverage is 128 of 128 tier A types. `score` gave no warnings.
- **Numerator ground truth (§2b):** skipped, because `stats.exports_documented` (378) does not equal `stats.effective_denominator` (370), so the inflation signature is absent.
- **Stale names (§2c):** 89 documented names are not on the source surface. `classify-stale` marked none fabricated. 54 have a `defined_at`, 29 are declared in several files with no single cited declaration, and 6 (`Mock`, `MockInstance`, `MaybeMocked`, `MaybeMockedDeep`, `MaybePartiallyMocked`, `MaybePartiallyMockedDeep`) are types `spy.ts` passes on from `@vitest/spy` through `export type *`. The gap ledger classifies each as an Info `observation` or a Medium `stale-documentation` gap.
- **Metadata count cross-check (§4b):** one Medium `metadata-drift` finding (`stats.exports_public_api` 1335 against `exports[]` 88, 93% drift) and one Info `multi-denominator` finding (barrel 1335, documented 378).
- **Provenance line check (§4c):** `verify` found 0 stale provenance lines.

**Borderline calls** (the rules left these undecided; each is recorded here as the run counted it):

1. **`Story`.** Documented form 0 is `{ of?, meta?, inline?, height?, autoplay? }` at `references/doc-blocks.md:32`, under the `Props (simplified)` header, so it is labelled partial. Source: `code/addons/docs/src/blocks/blocks/Story.tsx:134` (`withMdxComponentOverride('Story', StoryImpl)`, props `StoryProps` at lines 21-60, with optional own props `__forceInitialArgs?` and `__primary?`). The sentence that left it open, from Components: "An optional own prop a typed props list or a table leaves out is an `omitted-optional` difference; one a list of bare names or a usage leaves out, and an optional inherited prop, is no difference." An untyped list whose members carry `?` is neither a typed props list nor a list of bare names. The judge counted it as a mismatch tagged `omitted-optional`. Because the form is labelled partial, `score` graded it as an Info `Partial signature: Story`, which counts as matching, so neither score changes.
2. **`useThemeParameters`.** Documented form `(context?: StoryContext) => ThemesParameters['themes']` at `references/addons.md:126`. Source: `code/addons/themes/src/decorators/helpers.ts:20` (`(context?: StoryContext): ThemesParameters`, where the local alias at line 10 is `type ThemesParameters = Parameters['themes']` over the interface `ThemesParameters` imported as `Parameters` from `code/addons/themes/src/types.ts:6`). The sentence that left it open, from Equivalent spellings: "A type alias the source declares and the type it names." The rules do not say how to read a documented type name that the source declares twice, once as a local alias that shadows the interface. The judge read the documented `ThemesParameters` as the interface, so `ThemesParameters['themes']` is the type the alias names, and counted it as a match.
3. **The `Purpose and key params` column (SKILL.md Key API Summary).** Forms at `SKILL.md:135` (`fn`), `:139` (`composeStories`), `:141` (`withThemeByClassName`), `:142` (`create`) and `:143` (`Meta` and `Canvas` usages), under the header `| Export | Import from | Purpose and key params | Source |` at `SKILL.md:129`. These forms concern the Key API Summary table, not one source declaration. The sentence that left it open is inventory-contract.md's: "An entry whose signature the skill labels partial (simplified, key parameters, …; a label in a table's column header, such as `Props (simplified)`, labels each of its rows) carries `signature_form: "partial"`". The header says "key params" inside a combined "Purpose and …" column, and the floor script did not read it as a partial label. The inventory reader counted it as one and gave those entries `signature_form: "partial"`. No comparison outcome depended on it: all of these forms matched their declarations in full, so neither score changes.

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)
**Migration Section:** Section 4b verification skipped: evidence-report.md pins no `t2_future_count`. For a skill create-skill made, re-run create-skill to regenerate the report with the field (create-stack-skill does not write it).

### Structural Findings

| # | Type | Severity | Detail | Line |
|---|------|----------|--------|------|
| — | none | — | §2.1 required sections all satisfied (description: `Overview`, usage: `Quick Start`, API surface: `Key API Summary`); §2.2 fences balanced (10 fences); §2.3 no bare opening fence; §2.4 every function export is used in a usage-family section or reference file (`zero_usage` empty); §2.5 no export the skill describes as async or sync is called against that claim (10 exports located with calls, none awaited against a sync claim, no async claim unawaited); §2.6 no table drift; §2.7 no `scripts/` or `assets/` folder | — |

**Structural Issues:** 0

### Reference Consistency (split-body)

| # | Reference File | Export | Issue | Other Side | Reference Line | Contradicted Side |
|---|---------------|--------|-------|------------|---------------|-------------------|
| — | — | — | no split-body mismatch found | — | — | — |

**Exports Cross-Checked:** 136
**Mismatches Found:** 0

## External Validation

### skill-check
- **Available:** yes
- **Quality Score:** 100/100
- **Errors:** 0
- **Warnings:** 0
- **Diagnostics:** none

### Tessl Review
- **Result:** off — set tessl_review_workspace in preferences.yaml to enable

### Combined External Score
- **External Validation Score:** 100%
- **Tools used:** skill-check

## Completeness Score

### Score Breakdown

| Category | Score | Weight | Weighted |
|----------|-------|--------|----------|
| Export Coverage | 100% | 45% | 45% |
| Signature Accuracy | 100% | 25% | 25% |
| Type Coverage | 100% | 20% | 20% |
| Coherence | not scored (naive mode) | 0% | 0% |
| External Validation | 100% | 10% | 10% |
| **Total** | | **100%** | **100%** |

### Result

**Score:** 100%
**Threshold:** 80%
**Result:** **PASS**

**Threshold Source:** workflow default (80%)
**Weight Distribution:** naive (redistributed)
**Tier Adjustment:** none
**External Validators:** skill-check only
**Analysis Confidence:** full
**Tooling Status:** ok

## Gap Report

**Total Gaps:** 92
**Blocking (Critical + High):** 0
**Non-blocking (Medium + Low + Info):** 92

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|------------------|
| Critical | 0 | None |
| High | 0 | None |
| Medium | 82 | Add type definitions, interface docs or the missing section |
| Low | 0 | None |
| Info | 10 | Optional improvements, no action required |
| **Total** | **92** | |

### GAP-002: Stale documentation: A

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:426
**Export:** A

**Issue:** `references/core-api.md:426` documents `A`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/A.tsx:7` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `A` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/A.tsx:7`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `A` at references/core-api.md:426.

### GAP-003: Stale documentation: ActionBar

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:431
**Export:** ActionBar

**Issue:** `references/core-api.md:431` documents `ActionBar`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/ActionBar/ActionBar.tsx:89` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `ActionBar` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/ActionBar/ActionBar.tsx:89`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `ActionBar` at references/core-api.md:431.

### GAP-004: Stale documentation: ActionList

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:431
**Export:** ActionList

**Issue:** `references/core-api.md:431` documents `ActionList`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/ActionList/ActionList.tsx:222` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `ActionList` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/ActionList/ActionList.tsx:222`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `ActionList` at references/core-api.md:431.

### GAP-005: Stale documentation: AddonPanel

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:428
**Export:** AddonPanel

**Issue:** `references/core-api.md:428` documents `AddonPanel`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/addon-panel/addon-panel.tsx:36` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `AddonPanel` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/addon-panel/addon-panel.tsx:36`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `AddonPanel` at references/core-api.md:428.

### GAP-006: Stale documentation: Badge

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:426
**Export:** Badge

**Issue:** `references/core-api.md:426` documents `Badge`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Badge/Badge.tsx:88` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Badge` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Badge/Badge.tsx:88`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Badge` at references/core-api.md:426.

### GAP-007: Stale documentation: Bar

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:431
**Export:** Bar

**Issue:** `references/core-api.md:431` documents `Bar`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Bar/Bar.tsx:52` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Bar` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Bar/Bar.tsx:52`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Bar` at references/core-api.md:431.

### GAP-008: Stale documentation: Blockquote

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:426
**Export:** Blockquote

**Issue:** `references/core-api.md:426` documents `Blockquote`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/Blockquote.tsx:6` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Blockquote` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/Blockquote.tsx:6`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Blockquote` at references/core-api.md:426.

### GAP-009: Stale documentation: Button

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:427
**Export:** Button

**Issue:** `references/core-api.md:427` documents `Button`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Button/Button.tsx:53` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Button` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Button/Button.tsx:53`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Button` at references/core-api.md:427.

### GAP-010: Stale documentation: Card

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:428
**Export:** Card

**Issue:** `references/core-api.md:428` documents `Card`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Card/Card.tsx:98` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Card` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Card/Card.tsx:98`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Card` at references/core-api.md:428.

### GAP-011: Stale documentation: Channel

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:444
**Export:** Channel

**Issue:** `references/core-api.md:444` documents `Channel`, which the entry point `code/core/src/channels/index.ts` exports and `code/core/src/channels/main.ts:22` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Channel` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/channels/main.ts:22`, where it is defined, since its `scope.exclude` glob `code/core/src/channels/**` matches that file. To keep its documentation, narrow `code/core/src/channels/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Channel` at references/core-api.md:444.

### GAP-013: Stale documentation: Code

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:426
**Export:** Code

**Issue:** `references/core-api.md:426` documents `Code`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/Code.tsx:42` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Code` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/Code.tsx:42`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Code` at references/core-api.md:426.

### GAP-014: Stale documentation: Collapsible

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:428
**Export:** Collapsible

**Issue:** `references/core-api.md:428` documents `Collapsible`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Collapsible/Collapsible.tsx:31` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Collapsible` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Collapsible/Collapsible.tsx:31`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Collapsible` at references/core-api.md:428.

### GAP-016: Stale documentation: ConfigFile

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:451
**Export:** ConfigFile

**Issue:** `references/core-api.md:451` documents `ConfigFile`, which the entry point `code/core/src/csf-tools/index.ts` exports and `code/core/src/csf-tools/ConfigFile.ts:140` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `ConfigFile` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/csf-tools/ConfigFile.ts:140`, where it is defined, since its `scope.exclude` glob `code/core/src/csf-tools/**` matches that file. To keep its documentation, narrow `code/core/src/csf-tools/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `ConfigFile` at references/core-api.md:451.

### GAP-017: Stale documentation: CsfFile

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:451
**Export:** CsfFile

**Issue:** `references/core-api.md:451` documents `CsfFile`, which the entry point `code/core/src/csf-tools/index.ts` exports and `code/core/src/csf-tools/CsfFile.ts:280` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `CsfFile` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/csf-tools/CsfFile.ts:280`, where it is defined, since its `scope.exclude` glob `code/core/src/csf-tools/**` matches that file. To keep its documentation, narrow `code/core/src/csf-tools/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `CsfFile` at references/core-api.md:451.

### GAP-018: Stale documentation: DL

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:426
**Export:** DL

**Issue:** `references/core-api.md:426` documents `DL`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/DL.tsx:6` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `DL` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/DL.tsx:6`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `DL` at references/core-api.md:426.

### GAP-020: Stale documentation: Div

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:426
**Export:** Div

**Issue:** `references/core-api.md:426` documents `Div`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/Div.tsx:5` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Div` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/Div.tsx:5`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Div` at references/core-api.md:426.

### GAP-021: Stale documentation: ErrorFormatter

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:432
**Export:** ErrorFormatter

**Issue:** `references/core-api.md:432` documents `ErrorFormatter`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/ErrorFormatter/ErrorFormatter.tsx:29` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `ErrorFormatter` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/ErrorFormatter/ErrorFormatter.tsx:29`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `ErrorFormatter` at references/core-api.md:432.

### GAP-022: Stale documentation: FlexBar

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:431
**Export:** FlexBar

**Issue:** `references/core-api.md:431` documents `FlexBar`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Bar/Bar.tsx:129` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `FlexBar` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Bar/Bar.tsx:129`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `FlexBar` at references/core-api.md:431.

### GAP-023: Stale documentation: Form

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:427
**Export:** Form

**Issue:** `references/core-api.md:427` documents `Form`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Form/Form.tsx:11` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Form` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Form/Form.tsx:11`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Form` at references/core-api.md:427.

### GAP-024: Stale documentation: H1

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:426
**Export:** H1

**Issue:** `references/core-api.md:426` documents `H1`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/H1.tsx:6` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `H1` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/H1.tsx:6`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `H1` at references/core-api.md:426.

### GAP-025: Stale documentation: H6

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:426
**Export:** H6

**Issue:** `references/core-api.md:426` documents `H6`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/H6.tsx:6` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `H6` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/H6.tsx:6`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `H6` at references/core-api.md:426.

### GAP-026: Stale documentation: HR

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:426
**Export:** HR

**Issue:** `references/core-api.md:426` documents `HR`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/HR.tsx:3` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `HR` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/HR.tsx:3`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `HR` at references/core-api.md:426.

### GAP-027: Stale documentation: IconButton

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:427
**Export:** IconButton

**Issue:** `references/core-api.md:427` documents `IconButton`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Button/Button.tsx:327` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `IconButton` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Button/Button.tsx:327`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `IconButton` at references/core-api.md:427.

### GAP-028: Stale documentation: LI

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:426
**Export:** LI

**Issue:** `references/core-api.md:426` documents `LI`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/LI.tsx:6` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `LI` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/LI.tsx:6`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `LI` at references/core-api.md:426.

### GAP-029: Stale documentation: MaybeMocked

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:66
**Export:** MaybeMocked

**Issue:** `references/core-api.md:66` documents `MaybeMocked`, which the enumerated source API surface lacks

**Remediation:** Check `MaybeMocked` against the source and update or remove its documentation at references/core-api.md:66: the enumerated source surface does not export it.

### GAP-030: Stale documentation: MaybeMockedDeep

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:67
**Export:** MaybeMockedDeep

**Issue:** `references/core-api.md:67` documents `MaybeMockedDeep`, which the enumerated source API surface lacks

**Remediation:** Check `MaybeMockedDeep` against the source and update or remove its documentation at references/core-api.md:67: the enumerated source surface does not export it.

### GAP-031: Stale documentation: MaybePartiallyMocked

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:68
**Export:** MaybePartiallyMocked

**Issue:** `references/core-api.md:68` documents `MaybePartiallyMocked`, which the enumerated source API surface lacks

**Remediation:** Check `MaybePartiallyMocked` against the source and update or remove its documentation at references/core-api.md:68: the enumerated source surface does not export it.

### GAP-032: Stale documentation: MaybePartiallyMockedDeep

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:69
**Export:** MaybePartiallyMockedDeep

**Issue:** `references/core-api.md:69` documents `MaybePartiallyMockedDeep`, which the enumerated source API surface lacks

**Remediation:** Check `MaybePartiallyMockedDeep` against the source and update or remove its documentation at references/core-api.md:69: the enumerated source surface does not export it.

### GAP-033: Stale documentation: Mock

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:64
**Export:** Mock

**Issue:** `references/core-api.md:64` documents `Mock`, which the enumerated source API surface lacks

**Remediation:** Check `Mock` against the source and update or remove its documentation at references/core-api.md:64: the enumerated source surface does not export it.

### GAP-034: Stale documentation: MockInstance

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:65
**Export:** MockInstance

**Issue:** `references/core-api.md:65` documents `MockInstance`, which the enumerated source API surface lacks

**Remediation:** Check `MockInstance` against the source and update or remove its documentation at references/core-api.md:65: the enumerated source surface does not export it.

### GAP-035: Stale documentation: Modal

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:428
**Export:** Modal

**Issue:** `references/core-api.md:428` documents `Modal`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Modal/Modal.tsx:242` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Modal` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Modal/Modal.tsx:242`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Modal` at references/core-api.md:428.

### GAP-036: Stale documentation: OL

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:426
**Export:** OL

**Issue:** `references/core-api.md:426` documents `OL`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/OL.tsx:16` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `OL` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/OL.tsx:16`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `OL` at references/core-api.md:426.

### GAP-037: Stale documentation: P

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:426
**Export:** P

**Issue:** `references/core-api.md:426` documents `P`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/P.tsx:6` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `P` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/P.tsx:6`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `P` at references/core-api.md:426.

### GAP-038: Stale documentation: Placeholder

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:432
**Export:** Placeholder

**Issue:** `references/core-api.md:432` documents `Placeholder`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/placeholder/placeholder.tsx:22` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Placeholder` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/placeholder/placeholder.tsx:22`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Placeholder` at references/core-api.md:432.

### GAP-039: Stale documentation: Popover

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:430
**Export:** Popover

**Issue:** `references/core-api.md:430` documents `Popover`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Popover/Popover.tsx:77` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Popover` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Popover/Popover.tsx:77`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Popover` at references/core-api.md:430.

### GAP-040: Stale documentation: PopoverProvider

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:430
**Export:** PopoverProvider

**Issue:** `references/core-api.md:430` documents `PopoverProvider`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Popover/PopoverProvider.tsx:63` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `PopoverProvider` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Popover/PopoverProvider.tsx:63`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `PopoverProvider` at references/core-api.md:430.

### GAP-041: Stale documentation: PostMessageTransport

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:444
**Export:** PostMessageTransport

**Issue:** `references/core-api.md:444` documents `PostMessageTransport`, which the entry point `code/core/src/channels/index.ts` exports and `code/core/src/channels/postmessage/index.ts:29` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `PostMessageTransport` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/channels/postmessage/index.ts:29`, where it is defined, since its `scope.exclude` glob `code/core/src/channels/**` matches that file. To keep its documentation, narrow `code/core/src/channels/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `PostMessageTransport` at references/core-api.md:444.

### GAP-042: Stale documentation: Pre

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:426
**Export:** Pre

**Issue:** `references/core-api.md:426` documents `Pre`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/Pre.tsx:6` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Pre` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/Pre.tsx:6`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Pre` at references/core-api.md:426.

### GAP-045: Stale documentation: ScrollArea

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:428
**Export:** ScrollArea

**Issue:** `references/core-api.md:428` documents `ScrollArea`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/ScrollArea/ScrollArea.tsx:95` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `ScrollArea` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/ScrollArea/ScrollArea.tsx:95`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `ScrollArea` at references/core-api.md:428.

### GAP-046: Stale documentation: Select

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:427
**Export:** Select

**Issue:** `references/core-api.md:427` documents `Select`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Select/Select.tsx:201` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Select` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Select/Select.tsx:201`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Select` at references/core-api.md:427.

### GAP-048: Stale documentation: Spaced

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:432
**Export:** Spaced

**Issue:** `references/core-api.md:432` documents `Spaced`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/spaced/Spaced.tsx:63` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Spaced` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/spaced/Spaced.tsx:63`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Spaced` at references/core-api.md:432.

### GAP-049: Stale documentation: Span

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:426
**Export:** Span

**Issue:** `references/core-api.md:426` documents `Span`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/Span.tsx:6` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Span` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/Span.tsx:6`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Span` at references/core-api.md:426.

### GAP-050: Stale documentation: StoryIndexGenerator

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:454
**Export:** StoryIndexGenerator

**Issue:** `references/core-api.md:454` documents `StoryIndexGenerator`, which the entry point `code/core/src/core-server/index.ts` exports and `code/core/src/core-server/utils/StoryIndexGenerator.ts:101` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `StoryIndexGenerator` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/core-server/utils/StoryIndexGenerator.ts:101`, where it is defined, since its `scope.exclude` glob `code/core/src/core-server/**` matches that file. To keep its documentation, narrow `code/core/src/core-server/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `StoryIndexGenerator` at references/core-api.md:454.

### GAP-051: Stale documentation: StorybookIcon

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:433
**Export:** StorybookIcon

**Issue:** `references/core-api.md:433` documents `StorybookIcon`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/brand/StorybookIcon.tsx:3` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `StorybookIcon` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/brand/StorybookIcon.tsx:3`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `StorybookIcon` at references/core-api.md:433.

### GAP-052: Stale documentation: StorybookLogo

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:433
**Export:** StorybookLogo

**Issue:** `references/core-api.md:433` documents `StorybookLogo`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/brand/StorybookLogo.tsx:7` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `StorybookLogo` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/brand/StorybookLogo.tsx:7`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `StorybookLogo` at references/core-api.md:433.

### GAP-053: Stale documentation: SyntaxHighlighter

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:432
**Export:** SyntaxHighlighter

**Issue:** `references/core-api.md:432` documents `SyntaxHighlighter`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/syntaxhighlighter/lazy-syntaxhighlighter.tsx:52` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `SyntaxHighlighter` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/syntaxhighlighter/lazy-syntaxhighlighter.tsx:52`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `SyntaxHighlighter` at references/core-api.md:432.

### GAP-054: Stale documentation: TabBar

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:429
**Export:** TabBar

**Issue:** `references/core-api.md:429` documents `TabBar`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Tabs/Tabs.tsx:61` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `TabBar` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Tabs/Tabs.tsx:61`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `TabBar` at references/core-api.md:429.

### GAP-055: Stale documentation: TabButton

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:429
**Export:** TabButton

**Issue:** `references/core-api.md:429` documents `TabButton`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Tabs/Button.tsx:139` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `TabButton` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Tabs/Button.tsx:139`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `TabButton` at references/core-api.md:429.

### GAP-056: Stale documentation: TabList

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:429
**Export:** TabList

**Issue:** `references/core-api.md:429` documents `TabList`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Tabs/TabList.tsx:150` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `TabList` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Tabs/TabList.tsx:150`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `TabList` at references/core-api.md:429.

### GAP-057: Stale documentation: TabPanel

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:429
**Export:** TabPanel

**Issue:** `references/core-api.md:429` documents `TabPanel`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Tabs/TabPanel.tsx:34` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `TabPanel` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Tabs/TabPanel.tsx:34`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `TabPanel` at references/core-api.md:429.

### GAP-058: Stale documentation: TabWrapper

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:429
**Export:** TabWrapper

**Issue:** `references/core-api.md:429` documents `TabWrapper`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Tabs/Tabs.tsx:120` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `TabWrapper` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Tabs/Tabs.tsx:120`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `TabWrapper` at references/core-api.md:429.

### GAP-059: Stale documentation: Table

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:426
**Export:** Table

**Issue:** `references/core-api.md:426` documents `Table`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/Table.tsx:6` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Table` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/Table.tsx:6`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Table` at references/core-api.md:426.

### GAP-060: Stale documentation: Tabs

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:429
**Export:** Tabs

**Issue:** `references/core-api.md:429` documents `Tabs`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Tabs/Tabs.tsx:188` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Tabs` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Tabs/Tabs.tsx:188`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Tabs` at references/core-api.md:429.

### GAP-061: Stale documentation: TabsView

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:429
**Export:** TabsView

**Issue:** `references/core-api.md:429` documents `TabsView`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Tabs/TabsView.tsx:106` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `TabsView` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Tabs/TabsView.tsx:106`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `TabsView` at references/core-api.md:429.

### GAP-064: Stale documentation: ToggleButton

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:427
**Export:** ToggleButton

**Issue:** `references/core-api.md:427` documents `ToggleButton`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/ToggleButton/ToggleButton.tsx:16` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `ToggleButton` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/ToggleButton/ToggleButton.tsx:16`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `ToggleButton` at references/core-api.md:427.

### GAP-065: Stale documentation: Toolbar

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:431
**Export:** Toolbar

**Issue:** `references/core-api.md:431` documents `Toolbar`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Toolbar/Toolbar.tsx:36` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Toolbar` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Toolbar/Toolbar.tsx:36`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Toolbar` at references/core-api.md:431.

### GAP-066: Stale documentation: Tooltip

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:430
**Export:** Tooltip

**Issue:** `references/core-api.md:430` documents `Tooltip`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/tooltip/Tooltip.tsx:7` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Tooltip` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/tooltip/Tooltip.tsx:7`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Tooltip` at references/core-api.md:430.

### GAP-067: Stale documentation: TooltipLinkList

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:430
**Export:** TooltipLinkList

**Issue:** `references/core-api.md:430` documents `TooltipLinkList`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/tooltip/TooltipLinkList.tsx:70` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `TooltipLinkList` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/tooltip/TooltipLinkList.tsx:70`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `TooltipLinkList` at references/core-api.md:430.

### GAP-068: Stale documentation: TooltipNote

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:430
**Export:** TooltipNote

**Issue:** `references/core-api.md:430` documents `TooltipNote`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/tooltip/TooltipNote.tsx:23` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `TooltipNote` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/tooltip/TooltipNote.tsx:23`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `TooltipNote` at references/core-api.md:430.

### GAP-069: Stale documentation: UL

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:426
**Export:** UL

**Issue:** `references/core-api.md:426` documents `UL`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/UL.tsx:16` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `UL` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/UL.tsx:16`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `UL` at references/core-api.md:426.

### GAP-070: Stale documentation: WebsocketTransport

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:444
**Export:** WebsocketTransport

**Issue:** `references/core-api.md:444` documents `WebsocketTransport`, which the entry point `code/core/src/channels/index.ts` exports and `code/core/src/channels/websocket/index.ts:23` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `WebsocketTransport` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/channels/websocket/index.ts:23`, where it is defined, since its `scope.exclude` glob `code/core/src/channels/**` matches that file. To keep its documentation, narrow `code/core/src/channels/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `WebsocketTransport` at references/core-api.md:444.

### GAP-071: Stale documentation: WithTooltip

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:430
**Export:** WithTooltip

**Issue:** `references/core-api.md:430` documents `WithTooltip`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/tooltip/lazy-WithTooltip.tsx:8` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `WithTooltip` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/tooltip/lazy-WithTooltip.tsx:8`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `WithTooltip` at references/core-api.md:430.

### GAP-072: Stale documentation: Zoom

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:432
**Export:** Zoom

**Issue:** `references/core-api.md:432` documents `Zoom`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Zoom/Zoom.tsx:4` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Zoom` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Zoom/Zoom.tsx:4`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Zoom` at references/core-api.md:432.

### GAP-073: Stale documentation: addToGlobalContext

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:450
**Export:** addToGlobalContext

**Issue:** `references/core-api.md:450` documents `addToGlobalContext`, which the entry point `code/core/src/telemetry/index.ts` exports and `code/core/src/telemetry/telemetry.ts:26` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `addToGlobalContext` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/telemetry/telemetry.ts:26`, where it is defined, since its `scope.exclude` glob `code/core/src/telemetry/**` matches that file. To keep its documentation, narrow `code/core/src/telemetry/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `addToGlobalContext` at references/core-api.md:450.

### GAP-074: Stale documentation: colors

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:449
**Export:** colors

**Issue:** `references/core-api.md:449` documents `colors`, which the entry point `code/core/src/node-logger/index.ts` exports and `code/core/src/node-logger/index.ts:57` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `colors` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/node-logger/index.ts:57`, where it is defined, since its `scope.exclude` glob `code/core/src/node-logger/**` matches that file. To keep its documentation, narrow `code/core/src/node-logger/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `colors` at references/core-api.md:449.

### GAP-075: Stale documentation: componentTransform

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:451
**Export:** componentTransform

**Issue:** `references/core-api.md:451` documents `componentTransform`, which the entry point `code/core/src/csf-tools/index.ts` exports and `code/core/src/csf-tools/vitest-plugin/component-transformer.ts:285` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `componentTransform` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/csf-tools/vitest-plugin/component-transformer.ts:285`, where it is defined, since its `scope.exclude` glob `code/core/src/csf-tools/**` matches that file. To keep its documentation, narrow `code/core/src/csf-tools/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `componentTransform` at references/core-api.md:451.

### GAP-076: Stale documentation: createBrowserChannel

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:444
**Export:** createBrowserChannel

**Issue:** `references/core-api.md:444` documents `createBrowserChannel`, which the entry point `code/core/src/channels/index.ts` exports and `code/core/src/channels/index.ts:32` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `createBrowserChannel` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/channels/index.ts:32`, where it is defined, since its `scope.exclude` glob `code/core/src/channels/**` matches that file. To keep its documentation, narrow `code/core/src/channels/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `createBrowserChannel` at references/core-api.md:444.

### GAP-077: Stale documentation: enrichCsf

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:451
**Export:** enrichCsf

**Issue:** `references/core-api.md:451` documents `enrichCsf`, which the entry point `code/core/src/csf-tools/index.ts` exports and `code/core/src/csf-tools/enrichCsf.ts:144` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `enrichCsf` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/csf-tools/enrichCsf.ts:144`, where it is defined, since its `scope.exclude` glob `code/core/src/csf-tools/**` matches that file. To keep its documentation, narrow `code/core/src/csf-tools/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `enrichCsf` at references/core-api.md:451.

### GAP-078: Stale documentation: experimental_loadStorybook

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:454
**Export:** experimental_loadStorybook

**Issue:** `references/core-api.md:454` documents `experimental_loadStorybook`, which the entry point `code/core/src/core-server/index.ts` exports and `code/core/src/core-server/load.ts:18` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `experimental_loadStorybook` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/core-server/load.ts:18`, where it is defined, since its `scope.exclude` glob `code/core/src/core-server/**` matches that file. To keep its documentation, narrow `code/core/src/core-server/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `experimental_loadStorybook` at references/core-api.md:454.

### GAP-079: Stale documentation: generate

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:456
**Export:** generate

**Issue:** `references/core-api.md:456` documents `generate`, which the entry point `code/core/src/babel/index.ts` exports and `code/core/src/babel/index.ts:38` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `generate` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/babel/index.ts:38`, where it is defined, since its `scope.exclude` glob `code/core/src/babel/**` matches that file. To keep its documentation, narrow `code/core/src/babel/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `generate` at references/core-api.md:456.

### GAP-080: Stale documentation: generateStoryFile

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:454
**Export:** generateStoryFile

**Issue:** `references/core-api.md:454` documents `generateStoryFile`, which the entry point `code/core/src/core-server/index.ts` exports and `code/core/src/core-server/utils/generate-story.ts:64` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `generateStoryFile` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/core-server/utils/generate-story.ts:64`, where it is defined, since its `scope.exclude` glob `code/core/src/core-server/**` matches that file. To keep its documentation, narrow `code/core/src/core-server/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `generateStoryFile` at references/core-api.md:454.

### GAP-081: Stale documentation: getSessionId

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:450
**Export:** getSessionId

**Issue:** `references/core-api.md:450` documents `getSessionId`, which the entry point `code/core/src/telemetry/index.ts` exports and `code/core/src/telemetry/session-id.ts:18` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `getSessionId` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/telemetry/session-id.ts:18`, where it is defined, since its `scope.exclude` glob `code/core/src/telemetry/**` matches that file. To keep its documentation, narrow `code/core/src/telemetry/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `getSessionId` at references/core-api.md:450.

### GAP-082: Stale documentation: getStoryHref

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:432
**Export:** getStoryHref

**Issue:** `references/core-api.md:432` documents `getStoryHref`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/utils/getStoryHref.ts:15` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `getStoryHref` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/utils/getStoryHref.ts:15`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `getStoryHref` at references/core-api.md:432.

### GAP-083: Stale documentation: getStorySortParameter

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:451
**Export:** getStorySortParameter

**Issue:** `references/core-api.md:451` documents `getStorySortParameter`, which the entry point `code/core/src/csf-tools/index.ts` exports and `code/core/src/csf-tools/getStorySortParameter.ts:96` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `getStorySortParameter` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/csf-tools/getStorySortParameter.ts:96`, where it is defined, since its `scope.exclude` glob `code/core/src/csf-tools/**` matches that file. To keep its documentation, narrow `code/core/src/csf-tools/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `getStorySortParameter` at references/core-api.md:451.

### GAP-084: Stale documentation: getStorybookMetadata

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:450
**Export:** getStorybookMetadata

**Issue:** `references/core-api.md:450` documents `getStorybookMetadata`, which the entry point `code/core/src/telemetry/index.ts` exports and `code/core/src/telemetry/storybook-metadata.ts:312` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `getStorybookMetadata` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/telemetry/storybook-metadata.ts:312`, where it is defined, since its `scope.exclude` glob `code/core/src/telemetry/**` matches that file. To keep its documentation, narrow `code/core/src/telemetry/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `getStorybookMetadata` at references/core-api.md:450.

### GAP-085: Stale documentation: logTracker

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:449
**Export:** logTracker

**Issue:** `references/core-api.md:449` documents `logTracker`, which the entry point `code/core/src/node-logger/index.ts` exports and `code/core/src/node-logger/logger/log-tracker.ts:95` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `logTracker` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/node-logger/logger/log-tracker.ts:95`, where it is defined, since its `scope.exclude` glob `code/core/src/node-logger/**` matches that file. To keep its documentation, narrow `code/core/src/node-logger/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `logTracker` at references/core-api.md:449.

### GAP-086: Stale documentation: prompt

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:449
**Export:** prompt

**Issue:** `references/core-api.md:449` documents `prompt`, which the entry point `code/core/src/node-logger/index.ts` exports and `code/core/src/node-logger/prompts/index.ts:5` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `prompt` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/node-logger/prompts/index.ts:5`, where it is defined, since its `scope.exclude` glob `code/core/src/node-logger/**` matches that file. To keep its documentation, narrow `code/core/src/node-logger/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `prompt` at references/core-api.md:449.

### GAP-087: Stale documentation: telemetry

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:450
**Export:** telemetry

**Issue:** `references/core-api.md:450` documents `telemetry`, which the entry point `code/core/src/telemetry/index.ts` exports and `code/core/src/telemetry/index.ts:31` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `telemetry` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/telemetry/index.ts:31`, where it is defined, since its `scope.exclude` glob `code/core/src/telemetry/**` matches that file. To keep its documentation, narrow `code/core/src/telemetry/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `telemetry` at references/core-api.md:450.

### GAP-088: Stale documentation: traverse

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:456
**Export:** traverse

**Issue:** `references/core-api.md:456` documents `traverse`, which the entry point `code/core/src/babel/index.ts` exports and `code/core/src/babel/index.ts:39` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `traverse` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/babel/index.ts:39`, where it is defined, since its `scope.exclude` glob `code/core/src/babel/**` matches that file. To keep its documentation, narrow `code/core/src/babel/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `traverse` at references/core-api.md:456.

### GAP-089: Stale documentation: useTabsState

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:429
**Export:** useTabsState

**Issue:** `references/core-api.md:429` documents `useTabsState`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Tabs/TabsView.tsx:30` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `useTabsState` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Tabs/TabsView.tsx:30`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `useTabsState` at references/core-api.md:429.

### GAP-090: Stale documentation: vitestTransform

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:451
**Export:** vitestTransform

**Issue:** `references/core-api.md:451` documents `vitestTransform`, which the entry point `code/core/src/csf-tools/index.ts` exports and `code/core/src/csf-tools/vitest-plugin/transformer.ts:108` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `vitestTransform` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/csf-tools/vitest-plugin/transformer.ts:108`, where it is defined, since its `scope.exclude` glob `code/core/src/csf-tools/**` matches that file. To keep its documentation, narrow `code/core/src/csf-tools/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `vitestTransform` at references/core-api.md:451.

### GAP-091: metadata drift — barrel export counts diverge

**Severity:** Medium
**Category:** Coverage (metadata-drift)
**Source:** skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/metadata.json

**Issue:** stats.exports_public_api=1335, exports[].length=88 → 93% drift

**Remediation:** Re-run Create Skill, which rebuilds `exports[]` and `stats.exports_public_api` in `skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/metadata.json` from the source. Update Skill does not repair this drift: each time it writes the skill it recounts `stats.exports_public_api` from the source and keeps `exports[]`, adding or dropping only the names its provenance map changes, so a metadata patch does not hold.

### GAP-001: Partial signature: Story

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/docs/src/blocks/blocks/Story.tsx:134
**Export:** Story

**Issue:** the skill labels its documented form of `Story` partial, and it leaves out only members the source marks optional: documented `{ of?, meta?, inline?, height?, autoplay? }`, source `withMdxComponentOverride('Story', StoryImpl): ComponentType<StoryProps>, StoryProps = { of?: ModuleExport; meta?: ModuleExports } & { inline?: boolean; height?: string; autoplay?: boolean; __forceInitialArgs?: boolean; __primary?: boolean }`: documented props list marks optionality with '?' (so it is not a bare-name list) and leaves out the optional own props '__forceInitialArgs' and '__primary' that StoryProps (StoryParameters) declares

**Remediation:** No change: the documented form of `Story` is labelled partial and leaves out only optional members of the signature the source defines at `code/addons/docs/src/blocks/blocks/Story.tsx:134`.

### GAP-012: Documented extra: CheckboxControl

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/docs/src/blocks/controls/options/Checkbox.tsx:57
**Export:** CheckboxControl

**Issue:** `references/doc-blocks.md:291` documents `CheckboxControl`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CheckboxControl` is a documented extra, a name the source still declares at `code/addons/docs/src/blocks/controls/options/Checkbox.tsx:57` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-015: Documented extra: ColorControlProps

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/docs/src/blocks/controls/Color.tsx:360
**Export:** ColorControlProps

**Issue:** `references/doc-blocks.md:270` documents `ColorControlProps`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ColorControlProps` is a documented extra, a name the source still declares at `code/addons/docs/src/blocks/controls/Color.tsx:360` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-019: Documented extra: DecoratorHelpers

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/themes/src/decorators/index.ts:5
**Export:** DecoratorHelpers

**Issue:** `references/addons.md:121` documents `DecoratorHelpers`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `DecoratorHelpers` is a documented extra, a name the source still declares at `code/addons/themes/src/decorators/index.ts:5` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-043: Documented extra: RadioControl

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/docs/src/blocks/controls/options/Radio.tsx:57
**Export:** RadioControl

**Issue:** `references/doc-blocks.md:292` documents `RadioControl`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `RadioControl` is a documented extra, a name the source still declares at `code/addons/docs/src/blocks/controls/options/Radio.tsx:57` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-044: Documented extra: ReactParameters

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/renderers/react/src/types.ts:19
**Export:** ReactParameters

**Issue:** `references/story-types.md:334` documents `ReactParameters`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ReactParameters` is a documented extra, a name the source still declares at `code/renderers/react/src/types.ts:19` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-047: Documented extra: SelectControl

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/docs/src/blocks/controls/options/Select.tsx:170
**Export:** SelectControl

**Issue:** `references/doc-blocks.md:293` documents `SelectControl`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `SelectControl` is a documented extra, a name the source still declares at `code/addons/docs/src/blocks/controls/options/Select.tsx:170` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-062: Documented extra: ThemeAddonState

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/themes/src/types.ts:1
**Export:** ThemeAddonState

**Issue:** `references/addons.md:114` documents `ThemeAddonState`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ThemeAddonState` is a documented extra, a name the source still declares at `code/addons/themes/src/types.ts:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-063: Documented extra: ThemesParameters

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/themes/src/types.ts:6
**Export:** ThemesParameters

**Issue:** `references/addons.md:115` documents `ThemesParameters`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ThemesParameters` is a documented extra, a name the source still declares at `code/addons/themes/src/types.ts:6` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-092: multi-denominator reporting — barrel vs documented surface

**Severity:** Info
**Category:** Coverage (multi-denominator)
**Source:** skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/metadata.json

**Issue:** barrel=1335, documented=378

**Remediation:** No action required: the barrel and the documented surface measure different sets by design, and the report records both counts.

### Discovery Quality

**Discovery Test:** PASS (3/3)

| # | Prompt | Selected Skill | Result |
|---|--------|----------------|--------|
| 1 | can you add an interaction test to my Button stories that clicks it and checks the onClick handler got called? | oms-storybook-react-vite (high) | PASS |
| 2 | i want a light/dark theme toggle that applies to every story preview in the sidebar, where do i wire that up? | oms-storybook-react-vite (high) | PASS |
| 3 | write an mdx docs page for Card that shows the primary story and its controls table | oms-storybook-react-vite (high) | PASS |

Catalog: 4 skills (`oms-cocoindex`, `oms-cognee`, `oms-storybook-react-vite`, `oms-uitripled`). SKILL.md has no Triggers section or conversational example prompts, so the three prompts were synthesized from its capability summary (§4b.1 fallback: vague, implicit and abbreviated patterns). Each was routed by an isolated subagent that was given only the catalog and the prompt. No description optimization hints: Tessl Review did not run, and skill-check flagged no description issue.

