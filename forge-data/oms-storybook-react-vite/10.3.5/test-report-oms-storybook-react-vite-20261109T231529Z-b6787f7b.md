---
workflowType: 'test-skill'
skillName: 'oms-storybook-react-vite'
skillDir: 'skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite'
runId: '20261109T231529Z-b6787f7b'
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
testDate: '2026-11-09T23:15:29Z'
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

**Mode Rationale:** metadata.json sets `skill_type: 'single'`, an individual skill, so naive mode applies: API-surface coverage, with structural-only coherence and no coherence category in scoring.

**Analysis Plan:**
- Coverage Check: every public export of the pinned source (storybook v10.3.5 at e486d38) that the skill's scope covers is checked for documentation in SKILL.md and references/; at Deep tier, documented signatures and types are compared against the source by AST-backed reading.
- Coherence Check: structural checks only (references resolve, sections well-formed, examples consistent with the documented API); no cross-skill integration checks.

## Coverage Analysis

**Tier:** Deep
**Source Access:** full
**Source Path:** /home/armel/.skf/workspace/repos/github.com/storybookjs/storybook
**Workspace Layout:** npm-workspaces
**Denominator:** Stratified scope, denominator: effective_denominator (124 files define its names, 370 exports union)

**Denominator Candidates** (stratified-scope audit trail):
- `stats.effective_denominator`: 370  ← chosen on the scalar branch (the `tier_a_include` set is counted: `setCounted` true, `numeratorSource` surface)
- `scope.tier_a_include` union: 370
- `scope.include` union: 1157
- exports-map subpath union: 1424
- root barrel: 63                               (secondary candidate: root-barrel-vs-subpath-union audit)

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
| `ManagerConsumer` | - | yes | - | - | WARN |
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
| `buildQueries` | function | yes | yes | code/core/src/test/testing-library.ts:40 | PASS |
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
| `configure` | function | yes | yes | code/core/src/test/testing-library.ts:41 | PASS |
| `configureActions` | function | yes | - | code/core/src/actions/runtime/configureActions.ts:9 | PASS |
| `convert` | function | yes | yes | code/core/src/docs-tools/argTypes/convert/index.ts:8 | PASS |
| `create` | function | yes | yes | code/core/src/theming/create.ts:29 | PASS |
| `createBrowserChannel` | - | yes | - | - | WARN |
| `createEvent` | const | yes | yes | code/core/src/test/testing-library.ts:42 | PASS |
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
| `expect` | const | yes | yes | code/core/src/test/index.ts:24 | PASS |
| `experimental_loadStorybook` | - | yes | - | - | WARN |
| `extractTitle` | function | yes | yes | code/addons/docs/src/blocks/blocks/Title.tsx:24 | PASS |
| `filterArgTypes` | function | yes | yes | code/core/src/preview-api/modules/store/filterArgTypes.ts:10 | PASS |
| `findAllByAltText` | function | yes | yes | code/core/src/test/testing-library.ts:44 | PASS |
| `findAllByDisplayValue` | function | yes | yes | code/core/src/test/testing-library.ts:45 | PASS |
| `findAllByLabelText` | function | yes | yes | code/core/src/test/testing-library.ts:46 | PASS |
| `findAllByPlaceholderText` | function | yes | yes | code/core/src/test/testing-library.ts:47 | PASS |
| `findAllByRole` | function | yes | yes | code/core/src/test/testing-library.ts:48 | PASS |
| `findAllByTestId` | function | yes | yes | code/core/src/test/testing-library.ts:49 | PASS |
| `findAllByText` | function | yes | yes | code/core/src/test/testing-library.ts:50 | PASS |
| `findAllByTitle` | function | yes | yes | code/core/src/test/testing-library.ts:51 | PASS |
| `findByAltText` | function | yes | yes | code/core/src/test/testing-library.ts:52 | PASS |
| `findByDisplayValue` | function | yes | yes | code/core/src/test/testing-library.ts:53 | PASS |
| `findByLabelText` | function | yes | yes | code/core/src/test/testing-library.ts:54 | PASS |
| `findByPlaceholderText` | function | yes | yes | code/core/src/test/testing-library.ts:55 | PASS |
| `findByRole` | function | yes | yes | code/core/src/test/testing-library.ts:56 | PASS |
| `findByTestId` | function | yes | yes | code/core/src/test/testing-library.ts:57 | PASS |
| `findByText` | function | yes | yes | code/core/src/test/testing-library.ts:58 | PASS |
| `findByTitle` | function | yes | yes | code/core/src/test/testing-library.ts:59 | PASS |
| `fireEvent` | const | yes | - | code/core/src/test/testing-library.ts:43 | PASS |
| `fn` | function | yes | yes | code/core/src/test/spy.ts:48 | PASS |
| `format` | function | yes | yes | code/addons/docs/src/blocks/controls/Number.tsx:22 | PASS |
| `formatDate` | function | yes | yes | code/addons/docs/src/blocks/controls/Date.tsx:26 | PASS |
| `formatTime` | function | yes | yes | code/addons/docs/src/blocks/controls/Date.tsx:34 | PASS |
| `generate` | - | yes | - | - | WARN |
| `generateStoryFile` | - | yes | - | - | WARN |
| `getAllByAltText` | function | yes | yes | code/core/src/test/testing-library.ts:60 | PASS |
| `getAllByDisplayValue` | function | yes | yes | code/core/src/test/testing-library.ts:61 | PASS |
| `getAllByLabelText` | function | yes | yes | code/core/src/test/testing-library.ts:62 | PASS |
| `getAllByPlaceholderText` | function | yes | yes | code/core/src/test/testing-library.ts:63 | PASS |
| `getAllByRole` | function | yes | yes | code/core/src/test/testing-library.ts:64 | PASS |
| `getAllByTestId` | function | yes | yes | code/core/src/test/testing-library.ts:65 | PASS |
| `getAllByText` | function | yes | yes | code/core/src/test/testing-library.ts:66 | PASS |
| `getAllByTitle` | function | yes | yes | code/core/src/test/testing-library.ts:67 | PASS |
| `getByAltText` | function | yes | yes | code/core/src/test/testing-library.ts:68 | PASS |
| `getByDisplayValue` | function | yes | yes | code/core/src/test/testing-library.ts:69 | PASS |
| `getByLabelText` | function | yes | yes | code/core/src/test/testing-library.ts:70 | PASS |
| `getByPlaceholderText` | function | yes | yes | code/core/src/test/testing-library.ts:71 | PASS |
| `getByRole` | function | yes | yes | code/core/src/test/testing-library.ts:72 | PASS |
| `getByTestId` | function | yes | yes | code/core/src/test/testing-library.ts:73 | PASS |
| `getByText` | function | yes | yes | code/core/src/test/testing-library.ts:74 | PASS |
| `getByTitle` | function | yes | yes | code/core/src/test/testing-library.ts:75 | PASS |
| `getConfig` | function | yes | yes | code/core/src/test/testing-library.ts:76 | PASS |
| `getCsfFactoryAnnotations` | function | yes | yes | code/core/src/preview-api/modules/store/csf/csf-factory-utils.ts:10 | PASS |
| `getDefaultNormalizer` | function | yes | yes | code/core/src/test/testing-library.ts:77 | PASS |
| `getElementError` | function | yes | yes | code/core/src/test/testing-library.ts:78 | PASS |
| `getNodeText` | function | yes | yes | code/core/src/test/testing-library.ts:79 | PASS |
| `getPreferredColorScheme` | function | yes | - | code/core/src/theming/utils.ts:66 | PASS |
| `getQueriesForElement` | function | yes | yes | code/core/src/test/testing-library.ts:80 | PASS |
| `getRoles` | function | yes | yes | code/core/src/test/testing-library.ts:81 | PASS |
| `getSessionId` | - | yes | - | - | WARN |
| `getStoryHref` | - | yes | - | - | WARN |
| `getStoryId` | function | yes | yes | code/addons/docs/src/blocks/blocks/Story.tsx:62 | PASS |
| `getStoryProps` | function | yes | yes | code/addons/docs/src/blocks/blocks/Story.tsx:75 | PASS |
| `getStorySortParameter` | - | yes | - | - | WARN |
| `getStorybookMetadata` | - | yes | - | - | WARN |
| `getSuggestedQuery` | function | yes | yes | code/core/src/test/testing-library.ts:82 | PASS |
| `hasVitePlugins` | function | yes | yes | code/builders/builder-vite/src/utils/has-vite-plugins.ts:13 | PASS |
| `ignoreSsrWarning` | const | yes | - | code/core/src/theming/index.ts:43 | PASS |
| `inferControls` | function | yes | - | code/core/src/preview-api/modules/store/inferControls.ts:66 | PASS |
| `initializeThemeState` | function | yes | yes | code/addons/themes/src/decorators/helpers.ts:34 | PASS |
| `isInaccessible` | function | yes | yes | code/core/src/test/testing-library.ts:83 | PASS |
| `isMockFunction` | - | yes | yes | code/core/src/test/spy.ts | PASS |
| `lighten` | const | yes | - | code/core/src/theming/utils.ts:61 | PASS |
| `logDOM` | function | yes | yes | code/core/src/test/testing-library.ts:84 | PASS |
| `logRoles` | function | yes | yes | code/core/src/test/testing-library.ts:85 | PASS |
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
| `prettyDOM` | function | yes | yes | code/core/src/test/testing-library.ts:86 | PASS |
| `prettyFormat` | const | yes | - | code/core/src/test/testing-library.ts:111 | PASS |
| `prompt` | - | yes | - | - | WARN |
| `queries` | const | yes | - | code/core/src/test/testing-library.ts:87 | PASS |
| `queryAllByAltText` | function | yes | yes | code/core/src/test/testing-library.ts:88 | PASS |
| `queryAllByAttribute` | function | yes | yes | code/core/src/test/testing-library.ts:89 | PASS |
| `queryAllByDisplayValue` | function | yes | yes | code/core/src/test/testing-library.ts:90 | PASS |
| `queryAllByLabelText` | function | yes | yes | code/core/src/test/testing-library.ts:91 | PASS |
| `queryAllByPlaceholderText` | function | yes | yes | code/core/src/test/testing-library.ts:92 | PASS |
| `queryAllByRole` | function | yes | yes | code/core/src/test/testing-library.ts:93 | PASS |
| `queryAllByTestId` | function | yes | yes | code/core/src/test/testing-library.ts:94 | PASS |
| `queryAllByText` | function | yes | yes | code/core/src/test/testing-library.ts:95 | PASS |
| `queryAllByTitle` | function | yes | yes | code/core/src/test/testing-library.ts:96 | PASS |
| `queryByAltText` | function | yes | yes | code/core/src/test/testing-library.ts:97 | PASS |
| `queryByAttribute` | function | yes | yes | code/core/src/test/testing-library.ts:98 | PASS |
| `queryByDisplayValue` | function | yes | yes | code/core/src/test/testing-library.ts:99 | PASS |
| `queryByLabelText` | function | yes | yes | code/core/src/test/testing-library.ts:100 | PASS |
| `queryByPlaceholderText` | function | yes | yes | code/core/src/test/testing-library.ts:101 | PASS |
| `queryByRole` | function | yes | yes | code/core/src/test/testing-library.ts:102 | PASS |
| `queryByTestId` | function | yes | yes | code/core/src/test/testing-library.ts:103 | PASS |
| `queryByText` | function | yes | yes | code/core/src/test/testing-library.ts:104 | PASS |
| `queryByTitle` | function | yes | yes | code/core/src/test/testing-library.ts:105 | PASS |
| `queryHelpers` | const | yes | - | code/core/src/test/testing-library.ts:106 | PASS |
| `resetAllMocks` | function | yes | yes | code/core/src/test/spy.ts:89 | PASS |
| `responsiveViewport` | const | yes | - | code/core/src/viewport/responsiveViewport.tsx:4 | PASS |
| `restoreAllMocks` | function | yes | yes | code/core/src/test/spy.ts:98 | PASS |
| `sanitizeStoryContextUpdate` | function | yes | yes | code/core/src/preview-api/modules/store/decorators.ts:30 | PASS |
| `sb` | const | yes | - | code/core/src/test/index.ts:54 | PASS |
| `screen` | const | yes | - | code/core/src/test/testing-library.ts:107 | PASS |
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
| `useArgs` | function | yes | - | code/core/src/manager-api/root.tsx:462 | PASS |
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
| `userEvent` | const | yes | - | code/core/src/test/testing-library.ts:123 | PASS |
| `userOrAutoTitle` | function | yes | - | code/core/src/preview-api/modules/store/autoTitle.ts:86 | PASS |
| `userOrAutoTitleFromSpecifier` | function | yes | - | code/core/src/preview-api/modules/store/autoTitle.ts:49 | PASS |
| `vitestTransform` | - | yes | - | - | WARN |
| `waitFor` | function | yes | - | code/core/src/test/testing-library.ts:108 | PASS |
| `waitForAnimations` | function | yes | yes | code/core/src/preview-api/modules/preview-web/render/animation-utils.ts:54 | PASS |
| `waitForElementToBeRemoved` | function | yes | yes | code/core/src/test/testing-library.ts:109 | PASS |
| `withActions` | const | yes | yes | code/core/src/actions/decorator.ts:59 | PASS |
| `withThemeByClassName` | function | yes | yes | code/addons/themes/src/decorators/class-name.decorator.tsx:19 | PASS |
| `withThemeByDataAttribute` | function | yes | yes | code/addons/themes/src/decorators/data-attribute.decorator.tsx:19 | PASS |
| `withThemeFromJSXProvider` | function | yes | yes | code/addons/themes/src/decorators/provider.decorator.tsx:23 | PASS |
| `within` | function | yes | yes | code/core/src/test/testing-library.ts:110 | PASS |
| `withoutVitePlugins` | function | yes | yes | code/builders/builder-vite/src/utils/without-vite-plugins.ts:2 | PASS |

### Coverage Summary

- **Exports Found:** 370
- **Documented:** 370 (100%)
- **Missing Documentation:** 0
- **Signature Mismatches:** 0, plus 1 graded Low or Info and counted as matching
- **Stale Documentation:** 89, documented extras included
- **Scoring Warnings:**
  - Type Coverage leaves out each name the stale-scope guard restored or the extraction recorded with no kind, such as an extraction gap (the provenance map, when one is given, gives it no kind Type Coverage reads at its file): `isMockFunction`, `mocks`
- **Borderline Calls:**
  - `Meta` (SKILL.md:143), inventory reader: Meta has no kindLabel and names both the React type and the doc block; kind type taken from its type places, the doc-block places keep their usage and props forms; left open by: A name documented in several places is listed once per place, each entry with that place's form (`Card` above), ... and keeps one `kind` in every place; the other reading gives: no gap: kind function keeps the same forms
  - `Primary` (SKILL.md:117), inventory reader: `<Primary />` in render(<Primary />) passes no prop, so it is no usage and gives no entry; left open by: in running text or a description cell, only a call that passes an argument and writes no parameter type, `?`, bare `*` or `/`; the other reading gives: no gap: as a usage it sets no prop and Primary takes none
  - `Primary` (SKILL.md:120), inventory reader: `<Primary />` passes no prop: no usage, no entry; left open by: in running text or a description cell, only a call that passes an argument and writes no parameter type, `?`, bare `*` or `/`; the other reading gives: no gap: Primary takes no props
  - `Controls` (SKILL.md:120), inventory reader: `<Controls />` passes no prop: no usage, no entry; left open by: in running text or a description cell, only a call that passes an argument and writes no parameter type, `?`, bare `*` or `/`; the other reading gives: no gap: every Controls prop is optional
  - `Stories` (SKILL.md:120), inventory reader: `<Stories />` passes no prop: no usage, no entry; left open by: in running text or a description cell, only a call that passes an argument and writes no parameter type, `?`, bare `*` or `/`; the other reading gives: no gap: every Stories prop is optional
  - `Story` (SKILL.md:133), inventory reader: `<Story />` in the Decorator row passes no prop (and names the decorator's parameter): no usage; left open by: in running text or a description cell, only a call that passes an argument and writes no parameter type, `?`, bare `*` or `/`; the other reading gives: no gap: every Story prop is optional
  - `Wrapper` (SKILL.md:133), inventory reader: `<Wrapper><Story /></Wrapper>` passes children, so it is Wrapper's usage; left open by: in running text or a description cell, only a call that passes an argument and writes no parameter type, `?`, bare `*` or `/`; the other reading gives: no gap: read as a placeholder it gives no entry, and the usage passes only children, which Wrapper reads
  - `Button` (references/csf3-patterns.md:149), inventory reader: the documented internal-components Button has no form outside examples and the block does not define Button, so `<Button {...args} label={'set in play'} />` is Button's usage (the reader's-own-code exception covers only names the block defines); left open by: A call or JSX element of a name that a fenced example writes is not a place of its own when the skill also writes that name's form at a place that is no example (...): it gives no entry, so it is never compared, and a name whose only forms are in fenced examples keeps them; the other reading gives: a Critical signature-mismatch if storybook/internal/components' Button takes no `label` prop; read as the user's ./Button component, no entry and no gap
  - `Button` (references/csf3-patterns.md:219), inventory reader: `<Button {...args} />` in the CSF2 block is Button's usage; left open by: A call or JSX element of a name that a fenced example writes is not a place of its own when the skill also writes that name's form at a place that is no example (...): it gives no entry, so it is never compared, and a name whose only forms are in fenced examples keeps them; the other reading gives: no gap either way: the spread names no prop
  - `expect` (references/framework-config.md:355), inventory reader: under ### Per-test-file usage, `expect(screen.getByRole('button'))` is a call of the documented name expect, recorded as its usage although the block imports expect from vitest; left open by: ..., unless the nearest heading above the example names a usage, its text holding the word usage whatever qualifies it; the other reading gives: no gap: read as vitest's expect it gives no entry, and storybook/test's expect is typed outside the source tree
  - `Primary` (references/framework-config.md:354), inventory reader: the block defines Primary (and Clicked) by destructuring composeStories, so `<Primary />` is the reader's own code: no entry; left open by: A function or class an example defines is the reader's own code, not a form of a same-named export, only at a place inventory-floor.json gives no signature and only when its fenced block also defines names the skill does not document as exports; the other reading gives: no gap: as a usage it sets no prop and Primary takes none
  - `Story` (SKILL.md:56), inventory reader: the fenced `type Story = StoryObj<typeof meta>` (also csf3-patterns.md:29, :227 and story-types.md:121) is the reader's own type alias, no entry; left open by: A function or class an example defines is the reader's own code, not a form of a same-named export; the other reading gives: no gap: an entry there carries no compared form
  - `Markdown` (references/doc-blocks.md:111), inventory reader: the Props cell writes the type name MarkdownProps and prose, no props list, so no params; left open by: a blank one is the reader's, left out when the place writes none; the other reading gives: params `MarkdownProps` read as a bare prop name would give a Critical signature-mismatch; `{ children, options? }` no gap
  - `Unstyled` (references/doc-blocks.md:115), inventory reader: the Props cell writes only a React props type, so no params; left open by: a blank one is the reader's, left out when the place writes none; the other reading gives: no gap: props typed by another package are uncompared
  - `Source` (references/doc-blocks.md:86), inventory reader: the props list code span is the form; `SourceProps` names its type; left open by: a blank one is the reader's, left out when the place writes none; the other reading gives: params `SourceProps` read as a bare prop name would give a Critical signature-mismatch
  - `Primary` (references/doc-blocks.md:33), inventory reader: `none (FC with no props)` documents that Primary takes none: params ""; left open by: a function or method carries `params` (`""` or `[]` when it takes none ...); the other reading gives: no gap: with no params key nothing is compared
  - `Meta` (references/doc-blocks.md:75), inventory reader: the leading code span `MetaProps = BaseAnnotations & {...}` is the props form, as the floor records Title's; left open by: a blank one is the reader's, left out when the place writes none; the other reading gives: no gap: no params, or the listed props, match MetaProps
  - `DocsStory` (references/doc-blocks.md:134), inventory reader: the leading code span `DocsStoryProps = {...}` is the props form; left open by: a blank one is the reader's, left out when the place writes none; the other reading gives: no gap
  - `BooleanControl` (references/doc-blocks.md:269), inventory reader: `FC<BooleanProps>` names the props type but writes no props list: no params (likewise DateControl :274, FilesControl :280, NumberControl :281, ObjectControl :285, RangeControl :286, TextControl :288, OptionsControl :290, CheckboxControl :291, RadioControl :292, SelectControl :293); left open by: `FC<P>`, `React.FC<P>`, `FunctionComponent<P>`, ... are one contract, the props `P`; the other reading gives: no gap: `props: BooleanProps` would not be compared by the type's name
  - `PureArgsTable` (references/doc-blocks.md:142), inventory reader: the Purpose cell's option and data props describe ArgsTableProps' union, not one props form: no params; left open by: a blank one is the reader's, left out when the place writes none; the other reading gives: no gap
  - `DocsRenderer` (references/addons.md:251), inventory reader: `unmount: (element: HTMLElement) => void` (also doc-blocks.md:227) is a function-typed property, a properties item, no method entry; left open by: A method a place writes with a form of its own (a class body, a methods list, a row's cell, running text) gets a `method` entry there with that form; the other reading gives: no gap: method entries unmount(element: HTMLElement) agree with each other
  - `click` (references/core-api.md:208), inventory reader: the per-event-name member form, named through createEvent.click, is a method entry; left open by: A method a place writes with a form of its own (a class body, a methods list, a row's cell, running text) gets a `method` entry there with that form; the other reading gives: no gap: without it nothing is compared
  - `test` (references/story-types.md:361), inventory reader: ReactStory is documented with per-story test() methods, so Primary.test(...) is its usage (also csf3-patterns.md:117); left open by: and so does one the skill calls through an instance or the class it documents with that member (`builder.provide(KEY, value)`, `canvas.getByRole('button')`), the class as `owner`; the other reading gives: no gap: with no entry nothing is compared
  - `getByText` (references/csf3-patterns.md:118), inventory reader: Canvas is documented as extending every query, so canvas.getByText(...) is a Canvas method usage; left open by: and so does one the skill calls through an instance or the class it documents with that member; the other reading gives: no gap
  - `inferControls` (references/core-api.md:123), inventory reader: `ArgTypesEnhancer<Renderer>` names a function type but writes no parameter list: no params; left open by: A `const` whose value is a function (...) carries the function form the skill writes for it as `params` (`[]`, never `""`, when it takes none) and `return_type`; the other reading gives: params [] would claim it takes none, a Critical signature-mismatch against the enhancer's context parameter
  - `MissingStoryAfterHmrError` (references/core-api.md:413), inventory reader: names listed as a subpath's exports (error classes, internal components, infrastructure helpers, core-events constants) are documented: one mention entry each; left open by: of several such places of a name the skill documents and no other place gives an entry, the first alone gives one; the other reading gives: no gap: as undocumented they give no entries
  - `H2`, inventory reader: `H1`–`H6` writes only H1 and H6, so H2–H5 get no entries; left open by: of several such places of a name the skill documents and no other place gives an entry, the first alone gives one; the other reading gives: no gap
  - `API_IndexHash` (references/story-types.md:281), inventory reader: the parenthetical code spans naming the API_* declarations (story-types.md:281-288) sit outside a type position: mention entries; left open by: unless the skill also writes it as one outside a type position: ..., a code span that is the name or the name then `(`, or a fenced declaration; the other reading gives: no gap
  - `ManagerConsumer` (references/story-types.md:263), inventory reader: ManagerConsumer and useStorybookApi (story-types.md:266), named as what reads the manager context, are documented: mention entries; left open by: of several such places of a name the skill documents and no other place gives an entry, the first alone gives one; the other reading gives: no gap
  - `Selection` (references/core-api.md:151), inventory reader: Selection and SelectionStore's SelectionSpecifier, and HighlightParameters (core-api.md:337), are helper interfaces described inside another entry's cell, not documented exports: no entries; left open by: A name the skill writes only in a type position ... is a type mention, not an export the skill documents; the other reading gives: no gap: entries would carry no compared form
  - `StorybookError` (references/core-api.md:413), inventory reader: StorybookError (base class from ./storybook-error) and definePreviewAddon (addons.md:184, the addon's own source) are not presented as exports: no entries; left open by: of several such places of a name the skill documents and no other place gives an entry, the first alone gives one; the other reading gives: no gap: a definePreviewAddon({}) usage would match
  - `ComponentAnnotations` (references/story-types.md:74), inventory reader: prose that lists a type's fields gives an entry (also ProjectAnnotations story-types.md:43 and core-api.md:378, StoryAnnotations :112, StoryContext :182, FrameworkOptions and BuilderOptions framework-config.md:240, the props types in doc-blocks cells); left open by: A place that writes a name but no form of it, and no `methods`, `properties` or `fields` its entry would carry ..., gives it no entry when another place gives the name one; the other reading gives: no gap: these entries carry no compared form
  - `experimental_getStatusStore` (references/core-api.md:242), inventory reader: the shared label hook/func gives the use* names kind hook and the get* names kind function (also experimental_getTestProviderStore :243); component labels map to function, namespace to constant, default export to function; left open by: choose its kind from the name's kindLabel; the other reading gives: no gap: kind changes no compared form
  - `Story` (code/addons/docs/src/blocks/blocks/Story.tsx:134), signature judge: The documented `{ of?, meta?, inline?, height?, autoplay? }` writes `?` marks but no types: it is neither a typed props list nor a list of bare names (which has no `?`), so it falls to 'Its parameter list claims each parameter it lists, in that order, and no other', and its `signature_form: partial` label is honored by the rules only in the split-body cross-check; leaving out the optional own props `__forceInitialArgs` and `__primary` is read as an omitted-optional mismatch; left open by: An optional own prop a typed props list or a table leaves out is an `omitted-optional` difference; one a list of bare names or a usage leaves out, and an optional inherited prop, is no difference; the other reading gives: no mismatch (if a `?`-only untyped props list, or a form labeled partial, is read as not claiming a complete list, as a list of bare names does)
- **Scoped Out by the Brief:** `A` (code/core/src/components/components/typography/elements/A.tsx:7), `AbstractToolbar` (code/core/src/components/components/Toolbar/Toolbar.tsx:15), `ActionBar` (code/core/src/components/components/ActionBar/ActionBar.tsx:89), `ActionItem` (code/core/src/components/components/ActionBar/ActionBar.tsx:72), `ActionList` (code/core/src/components/components/ActionList/ActionList.tsx:222), `AddonPanel` (code/core/src/components/components/addon-panel/addon-panel.tsx:36), `AngularMeta` (code/frameworks/angular/src/client/preview.ts:150), `AngularOptions` (code/frameworks/angular/src/types.ts:47), `AngularParameters` (code/frameworks/angular/src/client/types.ts:45), `AngularPreview` (code/frameworks/angular/src/client/preview.ts:81), `AngularRenderer` (code/frameworks/angular/src/client/types.ts:40), `AngularStory` (code/frameworks/angular/src/client/preview.ts:254), `BabelFileClass` (code/core/src/babel/index.ts:43), `BadMetaError` (code/core/src/csf-tools/CsfFile.ts:246), `Badge` (code/core/src/components/components/Badge/Badge.tsx:88), `Bar` (code/core/src/components/components/Bar/Bar.tsx:52), `BarProps` (code/core/src/components/components/Bar/Bar.tsx:7), `BaseLocationProvider` (code/core/src/router/router.tsx:144), `Blockquote` (code/core/src/components/components/typography/elements/Blockquote.tsx:6), `BuildIndexOptions` (code/core/src/core-server/build-index.ts:10), `BuildStaticStandaloneOptions` (code/core/src/core-server/build-static.ts:31), `Button` (code/core/src/components/components/Button/Button.tsx:53), `ButtonProps` (code/core/src/components/components/Button/Button.tsx:14), `CLI_COLORS` (code/core/src/node-logger/logger/colors.ts:3), `CacheEntry` (code/core/src/telemetry/event-cache.ts:12), `Card` (code/core/src/components/components/Card/Card.tsx:98), `Channel` (code/core/src/channels/main.ts:22), `ChannelEvent` (code/core/src/channels/types.ts:18), `ChannelHandler` (code/core/src/channels/types.ts:11), `ChannelLike` (code/core/src/channels/types.ts:36), `ChannelTransport` (code/core/src/channels/types.ts:13), `ClipboardCode` (code/core/src/components/components/clipboard/ClipboardCode.tsx:24), `Code` (code/core/src/components/components/typography/elements/Code.tsx:42), `Collapsible` (code/core/src/components/components/Collapsible/Collapsible.tsx:31), `ComponentArgTypesData` (code/core/src/core-server/utils/get-dummy-args-from-argtypes.ts:8), `ConfigFile` (code/core/src/csf-tools/ConfigFile.ts:140), `ConsoleLogger` (code/core/src/node-logger/logger/console.ts:340), `Context` (code/core/src/telemetry/types.ts:106), `CsfFile` (code/core/src/csf-tools/CsfFile.ts:280), `CsfOptions` (code/core/src/csf-tools/CsfFile.ts:200), `DEEPLY_EQUAL` (code/core/src/router/utils.ts:43), `DL` (code/core/src/components/components/typography/elements/DL.tsx:6), `Dependency` (code/core/src/telemetry/types.ts:48), `Div` (code/core/src/components/components/typography/elements/Div.tsx:5), `DocumentWrapper` (code/core/src/components/components/typography/DocumentWrapper.tsx:3), `EmptyTabContent` (code/core/src/components/components/Tabs/EmptyTabContent.tsx:47), `EnrichCsfOptions` (code/core/src/csf-tools/enrichCsf.ts:6), `ErrorCollector` (code/core/src/telemetry/error-collector.ts:13), `ErrorFormatter` (code/core/src/components/components/ErrorFormatter/ErrorFormatter.tsx:29), `EventType` (code/core/src/telemetry/types.ts:9), `FlexBar` (code/core/src/components/components/Bar/Bar.tsx:129), `Form` (code/core/src/components/components/Form/Form.tsx:11), `GenerateStoryOptions` (code/core/src/core-server/utils/generate-story.ts:21), `GenerateStoryResult` (code/core/src/core-server/utils/generate-story.ts:11), `H1` (code/core/src/components/components/typography/elements/H1.tsx:6), `H2` (code/core/src/components/components/typography/elements/H2.tsx:6), `H3` (code/core/src/components/components/typography/elements/H3.tsx:6), `H4` (code/core/src/components/components/typography/elements/H4.tsx:6), `H5` (code/core/src/components/components/typography/elements/H5.tsx:6), `H6` (code/core/src/components/components/typography/elements/H6.tsx:6), `HEARTBEAT_INTERVAL` (code/core/src/channels/websocket/index.ts:20), `HEARTBEAT_MAX_LATENCY` (code/core/src/channels/websocket/index.ts:21), `HR` (code/core/src/components/components/typography/elements/HR.tsx:3), `IErrorWithStdErrAndStdOut` (code/core/src/telemetry/sanitize.ts:4), `IStory` (code/frameworks/angular/src/client/types.ts:31), `IconButton` (code/core/src/components/components/Button/Button.tsx:327), `Img` (code/core/src/components/components/typography/elements/Img.tsx:3), `InitPayload` (code/core/src/telemetry/types.ts:131), `LI` (code/core/src/components/components/typography/elements/LI.tsx:6), `Link` (code/core/src/components/components/typography/link/link.tsx:198), `LinkProps` (code/core/src/router/types.ts:23), `ListItem` (code/core/src/components/components/tooltip/ListItem.tsx:249), `Listener` (code/core/src/channels/types.ts:24), `Location` (code/core/src/router/router.tsx:81), `LocationProvider` (code/core/src/router/router.tsx:143), `LogLevel` (code/core/src/node-logger/logger/logger.ts:46), `Match` (code/core/src/router/router.tsx:141), `MemoryRouter` (code/core/src/router/router.tsx:145), `MixedFactoryError` (code/core/src/csf-tools/CsfFile.ts:234), `Modal` (code/core/src/components/components/Modal/Modal.tsx:242), `ModalDecorator` (code/core/src/components/components/Modal/Modal.tsx:248), `MultipleMetaError` (code/core/src/csf-tools/CsfFile.ts:222), `NavigateFunction` (code/core/src/router/types.ts:14), `NavigateOptions` (code/core/src/router/types.ts:12), `NoMetaError` (code/core/src/csf-tools/CsfFile.ts:210), `OL` (code/core/src/components/components/typography/elements/OL.tsx:16), `Other` (code/core/src/router/types.ts:7), `P` (code/core/src/components/components/typography/elements/P.tsx:6), `Payload` (code/core/src/telemetry/types.ts:102), `Placeholder` (code/core/src/components/components/placeholder/placeholder.tsx:22), `Popover` (code/core/src/components/components/Popover/Popover.tsx:77), `PopoverProps` (code/core/src/components/components/Popover/Popover.tsx:9), `PopoverProvider` (code/core/src/components/components/Popover/PopoverProvider.tsx:63), `PopoverProviderProps` (code/core/src/components/components/Popover/PopoverProvider.tsx:13), `PopperPlacement` (code/core/src/components/components/shared/overlayHelpers.tsx:22), `PostMessageTransport` (code/core/src/channels/postmessage/index.ts:29), `Pre` (code/core/src/components/components/typography/elements/Pre.tsx:6), `PreactRenderer` (code/renderers/preact/src/types.ts:14), `ProgressSpinner` (code/core/src/components/components/ProgressSpinner/ProgressSpinner.tsx:66), `RenderData` (code/core/src/router/types.ts:21), `ResetWrapper` (code/core/src/components/components/typography/ResetWrapper.tsx:12), `Route` (code/core/src/router/router.tsx:141), `RouterData` (code/core/src/router/types.ts:16), `ScrollArea` (code/core/src/components/components/ScrollArea/ScrollArea.tsx:95), `Select` (code/core/src/components/components/Select/Select.tsx:201), `Separator` (code/core/src/components/components/Bar/Separator.tsx:9), `Spaced` (code/core/src/components/components/spaced/Spaced.tsx:63), `Span` (code/core/src/components/components/typography/elements/Span.tsx:6), `SpinnerInstance` (code/core/src/node-logger/prompts/prompt-provider-base.ts:46), `StatelessTab` (code/core/src/components/components/Tabs/StatelessTab.tsx:57), `StatelessTabList` (code/core/src/components/components/Tabs/StatelessTabList.tsx:66), `StatelessTabListProps` (code/core/src/components/components/Tabs/StatelessTabList.tsx:62), `StatelessTabPanel` (code/core/src/components/components/Tabs/StatelessTabPanel.tsx:30), `StatelessTabPanelProps` (code/core/src/components/components/Tabs/StatelessTabPanel.tsx:9), `StatelessTabProps` (code/core/src/components/components/Tabs/StatelessTab.tsx:7), `StatelessTabsView` (code/core/src/components/components/Tabs/StatelessTabsView.tsx:31), `StatelessTabsViewProps` (code/core/src/components/components/Tabs/StatelessTabsView.tsx:27), `StaticMeta` (code/core/src/csf-tools/CsfFile.ts:258), `StaticStory` (code/core/src/csf-tools/CsfFile.ts:265), `StoryData` (code/core/src/router/utils.ts:9), `StoryIndexGenerator` (code/core/src/core-server/utils/StoryIndexGenerator.ts:101), `StoryTest` (code/core/src/csf-tools/CsfFile.ts:271), `StorybookAddon` (code/core/src/telemetry/types.ts:53), `StorybookBuilderOptions` (code/frameworks/angular/src/builders/build-storybook/index.ts:38), `StorybookBuilderOutput` (code/frameworks/angular/src/builders/build-storybook/index.ts:68), `StorybookIcon` (code/core/src/components/brand/StorybookIcon.tsx:3), `StorybookLogo` (code/core/src/components/brand/StorybookLogo.tsx:7), `StorybookMetadata` (code/core/src/telemetry/types.ts:57), `StyledConsoleLogger` (code/core/src/node-logger/logger/console.ts:340), `SvelteRenderer` (code/renderers/svelte/src/types.ts:11), `SyntaxHighlighter` (code/core/src/components/components/syntaxhighlighter/lazy-syntaxhighlighter.tsx:52), `SyntaxHighlighterFormatTypes` (code/core/src/components/components/syntaxhighlighter/syntaxhighlighter-types.ts:24), `SyntaxHighlighterProps` (code/core/src/components/components/syntaxhighlighter/syntaxhighlighter-types.ts:47), `SyntaxHighlighterRendererProps` (code/core/src/components/components/syntaxhighlighter/syntaxhighlighter-types.ts:5), `TT` (code/core/src/components/components/typography/elements/TT.tsx:5), `TabBar` (code/core/src/components/components/Tabs/Tabs.tsx:61), `TabButton` (code/core/src/components/components/Tabs/Button.tsx:139), `TabList` (code/core/src/components/components/Tabs/TabList.tsx:150), `TabListProps` (code/core/src/components/components/Tabs/TabList.tsx:146), `TabPanel` (code/core/src/components/components/Tabs/TabPanel.tsx:34), `TabPanelProps` (code/core/src/components/components/Tabs/TabPanel.tsx:12), `TabProps` (code/core/src/components/components/Tabs/TabsView.tsx:15), `TabWrapper` (code/core/src/components/components/Tabs/Tabs.tsx:120), `Table` (code/core/src/components/components/typography/elements/Table.tsx:6), `Tabs` (code/core/src/components/components/Tabs/Tabs.tsx:188), `TabsState` (code/core/src/components/components/Tabs/Tabs.tsx:287), `TabsView` (code/core/src/components/components/Tabs/TabsView.tsx:106), `TabsViewProps` (code/core/src/components/components/Tabs/TabsView.tsx:64), `TaskLogInstance` (code/core/src/node-logger/prompts/prompt-provider-base.ts:54), `TelemetryData` (code/core/src/telemetry/types.ts:119), `TelemetryEvent` (code/core/src/telemetry/types.ts:125), `ToggleButton` (code/core/src/components/components/ToggleButton/ToggleButton.tsx:16), `Toolbar` (code/core/src/components/components/Toolbar/Toolbar.tsx:36), `Tooltip` (code/core/src/components/components/tooltip/Tooltip.tsx:7), `TooltipLinkList` (code/core/src/components/components/tooltip/TooltipLinkList.tsx:70), `TooltipLinkListLink` (code/core/src/components/components/tooltip/TooltipLinkList.tsx:39), `TooltipMessage` (code/core/src/components/components/tooltip/TooltipMessage.tsx:47), `TooltipNote` (code/core/src/components/components/tooltip/TooltipNote.tsx:23), `TooltipNoteProps` (code/core/src/components/components/tooltip/TooltipNote.tsx:19), `TooltipProps` (code/core/src/components/components/tooltip/Tooltip.tsx:5), `TooltipProvider` (code/core/src/components/components/tooltip/TooltipProvider.tsx:108), `TooltipProviderProps` (code/core/src/components/components/tooltip/TooltipProvider.tsx:14), `TransformComponentType` (code/frameworks/angular/src/client/public-types.ts:56), `UL` (code/core/src/components/components/typography/elements/UL.tsx:16), `WebComponentsMeta` (code/renderers/web-components/src/preview.ts:160), `WebComponentsPreview` (code/renderers/web-components/src/preview.ts:85), `WebComponentsRenderer` (code/renderers/web-components/src/types.ts:14), `WebComponentsStory` (code/renderers/web-components/src/preview.ts:264), `WebComponentsTypes` (code/renderers/web-components/src/types.ts:24), `WebsocketTransport` (code/core/src/channels/websocket/index.ts:23), `WithTooltip` (code/core/src/components/components/tooltip/lazy-WithTooltip.tsx:8), `WithTooltipPure` (code/core/src/components/components/tooltip/lazy-WithTooltip.tsx:18), `Zoom` (code/core/src/components/components/Zoom/Zoom.tsx:4), `addToGlobalContext` (code/core/src/telemetry/telemetry.ts:26), `applicationConfig` (code/frameworks/angular/src/client/decorators.ts:37), `argsToTemplate` (code/frameworks/angular/src/client/argsToTemplate.ts:59), `babelParseExpression` (code/core/src/babel/babelParse.ts:52), `babelParseFile` (code/core/src/csf-tools/CsfFile.ts:1062), `babelPrint` (code/core/src/babel/babelParse.ts:42), `buildArgsParam` (code/core/src/router/utils.ts:186), `buildDevStandalone` (code/core/src/core-server/build-dev.ts:44), `buildIndex` (code/core/src/core-server/build-index.ts:12), `buildIndexStandalone` (code/core/src/core-server/build-index.ts:39), `buildStaticStandalone` (code/core/src/core-server/build-static.ts:35), `canUpdateVitestConfigFile` (code/core/src/babel/vitest-config-helpers.ts:159), `canUpdateVitestWorkspaceFile` (code/core/src/babel/vitest-config-helpers.ts:204), `cleanPaths` (code/core/src/telemetry/sanitize.ts:24), `codeCommon` (code/core/src/components/components/typography/lib/common.tsx:22), `colors` (code/core/src/node-logger/index.ts:57), `componentTransform` (code/core/src/csf-tools/vitest-plugin/component-transformer.ts:285), `componentWrapperDecorator` (code/frameworks/angular/src/client/decorators.ts:60), `components` (code/core/src/components/index.ts:133), `computeStorybookMetadata` (code/core/src/telemetry/storybook-metadata.ts:105), `convertToReactAriaPlacement` (code/core/src/components/components/shared/overlayHelpers.tsx:24), `createBrowserChannel` (code/core/src/channels/index.ts:32), `createCopyToClipboardFunction` (code/core/src/components/components/syntaxhighlighter/clipboard.ts:26), `createHyperlink` (code/core/src/node-logger/wrap-utils.ts:155), `createReactiveProps` (code/renderers/svelte/static/createReactiveProps.svelte.js:10), `deepDiff` (code/core/src/router/utils.ts:44), `deepMerge` (code/frameworks/angular/src/server/framework-preset-angular-cli.ts:95), `enrichCsf` (code/core/src/csf-tools/enrichCsf.ts:144), `enrichCsfMeta` (code/core/src/csf-tools/enrichCsf.ts:129), `enrichCsfStory` (code/core/src/csf-tools/enrichCsf.ts:12), `experimental_loadStorybook` (code/core/src/core-server/load.ts:18), `extractDescription` (code/core/src/csf-tools/enrichCsf.ts:158), `extractSource` (code/core/src/csf-tools/enrichCsf.ts:152), `formatConfig` (code/core/src/csf-tools/ConfigFile.ts:1165), `formatCsf` (code/core/src/csf-tools/CsfFile.ts:1083), `framework` (code/core/src/core-server/presets/common-override-preset.ts:5), `generate` (code/core/src/babel/index.ts:38), `generateStoryFile` (code/core/src/core-server/utils/generate-story.ts:64), `getConfigObjectFromMergeArg` (code/core/src/babel/vitest-config-helpers.ts:49), `getCustomElements` (code/renderers/web-components/src/framework-api.ts:37), `getEffectiveMergeConfigCall` (code/core/src/babel/vitest-config-helpers.ts:78), `getErrorLevel` (code/core/src/core-server/withTelemetry.ts:40), `getLastEvents` (code/core/src/telemetry/event-cache.ts:41), `getMatch` (code/core/src/router/utils.ts:233), `getPrecedingUpgrade` (code/core/src/telemetry/event-cache.ts:68), `getServerPort` (code/core/src/core-server/utils/server-address.ts:34), `getSessionId` (code/core/src/telemetry/session-id.ts:18), `getStoryHref` (code/core/src/components/components/utils/getStoryHref.ts:15), `getStorySortParameter` (code/core/src/csf-tools/getStorySortParameter.ts:96), `getStorybookMetadata` (code/core/src/telemetry/storybook-metadata.ts:312), `getTargetConfigObject` (code/core/src/babel/vitest-config-helpers.ts:118), `hrefTo` (code/addons/links/src/utils.ts:39), `interleaveSeparators` (code/core/src/components/components/Bar/Separator.tsx:29), `isCsfFactoryPreview` (code/core/src/csf-tools/ConfigFile.ts:1187), `isDefineConfigLike` (code/core/src/babel/vitest-config-helpers.ts:35), `isExampleStoryId` (code/core/src/telemetry/index.ts:26), `isImportedDefineConfigLikeIdentifier` (code/core/src/babel/vitest-config-helpers.ts:18), `isModuleMock` (code/core/src/csf-tools/CsfFile.ts:116), `isTelemetryEnabled` (code/core/src/core-server/withTelemetry.ts:157), `isValidComponent` (code/renderers/web-components/src/framework-api.ts:3), `isValidMetaData` (code/renderers/web-components/src/framework-api.ts:13), `isValidPreviewPath` (code/core/src/csf-tools/CsfFile.ts:43), `linkTo` (code/addons/links/src/utils.ts:61), `loadConfig` (code/core/src/csf-tools/ConfigFile.ts:1160), `loadCsf` (code/core/src/csf-tools/CsfFile.ts:1077), `logTracker` (code/core/src/node-logger/logger/log-tracker.ts:95), `mapStaticDir` (code/core/src/core-server/utils/server-statics.ts:198), `metaFrameworks` (code/core/src/telemetry/storybook-metadata.ts:33), `moduleMetadata` (code/frameworks/angular/src/client/decorators.ts:11), `nameSpaceClassNames` (code/core/src/components/components/typography/DocumentFormatting.tsx:1), `navigate` (code/addons/links/src/utils.ts:36), `oneWayHash` (code/core/src/telemetry/one-way-hash.ts:4), `parsePath` (code/core/src/router/utils.ts:17), `parserOptions` (code/core/src/babel/babelParse.ts:21), `printConfig` (code/core/src/csf-tools/ConfigFile.ts:1169), `printCsf` (code/core/src/csf-tools/CsfFile.ts:1096), `prompt` (code/core/src/node-logger/prompts/index.ts:5), `protectUrls` (code/core/src/node-logger/wrap-utils.ts:70), `queryFromLocation` (code/core/src/router/utils.ts:222), `readConfig` (code/core/src/csf-tools/ConfigFile.ts:1173), `readCsf` (code/core/src/csf-tools/CsfFile.ts:1100), `removeAnsiEscapeCodes` (code/core/src/telemetry/sanitize.ts:15), `resetComponents` (code/core/src/components/index.ts:142), `resolveExpression` (code/core/src/babel/expression-resolver.ts:22), `runNgcc` (code/frameworks/angular/src/server/framework-preset-angular-ivy.ts:37), `sanitizeAddonName` (code/core/src/telemetry/storybook-metadata.ts:50), `sanitizeError` (code/core/src/telemetry/sanitize.ts:64), `sendTelemetryError` (code/core/src/core-server/withTelemetry.ts:91), `setCustomElements` (code/renderers/web-components/src/framework-api.ts:29), `setCustomElementsManifest` (code/renderers/web-components/src/framework-api.ts:33), `stories` (code/core/src/core-server/presets/common-override-preset.ts:18), `stringifyQuery` (code/core/src/router/utils.ts:226), `telemetry` (code/core/src/telemetry/index.ts:31), `traverse` (code/core/src/babel/index.ts:39), `typescript` (code/core/src/core-server/presets/common-override-preset.ts:25), `unwrapTSExpression` (code/core/src/babel/expression-resolver.ts:4), `useNavigate` (code/core/src/router/router.tsx:45), `useTabsState` (code/core/src/components/components/Tabs/TabsView.tsx:30), `vitestTransform` (code/core/src/csf-tools/vitest-plugin/transformer.ts:108), `webpackFinal` (code/frameworks/angular/src/server/framework-preset-angular-cli.ts:15), `withLinks` (code/addons/links/src/utils.ts:110), `withReset` (code/core/src/components/components/typography/lib/common.tsx:36), `withTelemetry` (code/core/src/core-server/withTelemetry.ts:161), `writeConfig` (code/core/src/csf-tools/ConfigFile.ts:1178), `writeCsf` (code/core/src/csf-tools/CsfFile.ts:1105)
- **Extraction Gaps:** `ARGTYPES_INFO_REQUEST` (code/core/src/core-events/index.ts:167), `ARGTYPES_INFO_RESPONSE` (code/core/src/core-events/index.ts:168), `BabelFile` (not located), `CHANNEL_CREATED` (code/core/src/core-events/index.ts:112), `CHANNEL_WS_DISCONNECT` (code/core/src/core-events/index.ts:111), `CONFIG_ERROR` (code/core/src/core-events/index.ts:113), `CREATE_NEW_STORYFILE_REQUEST` (code/core/src/core-events/index.ts:114), `CREATE_NEW_STORYFILE_RESPONSE` (code/core/src/core-events/index.ts:115), `CURRENT_STORY_WAS_SET` (code/core/src/core-events/index.ts:116), `DOCS_PREPARED` (code/core/src/core-events/index.ts:117), `DOCS_RENDERED` (code/core/src/core-events/index.ts:118), `FILE_COMPONENT_SEARCH_REQUEST` (code/core/src/core-events/index.ts:119), `FILE_COMPONENT_SEARCH_RESPONSE` (code/core/src/core-events/index.ts:120), `FORCE_REMOUNT` (code/core/src/core-events/index.ts:122), `FORCE_RE_RENDER` (code/core/src/core-events/index.ts:121), `GHOST_STORIES_REQUEST` (code/core/src/core-events/index.ts:169), `GHOST_STORIES_RESPONSE` (code/core/src/core-events/index.ts:170), `GLOBALS_UPDATED` (code/core/src/core-events/index.ts:123), `GeneratorOptions` (not located), `MANAGER_INERT_ATTRIBUTE_CHANGED` (code/core/src/core-events/index.ts:173), `NAVIGATE_URL` (code/core/src/core-events/index.ts:124), `NodePath` (not located), `OPEN_IN_EDITOR_REQUEST` (code/core/src/core-events/index.ts:171), `OPEN_IN_EDITOR_RESPONSE` (code/core/src/core-events/index.ts:172), `PLAY_FUNCTION_THREW_EXCEPTION` (code/core/src/core-events/index.ts:125), `PRELOAD_ENTRIES` (code/core/src/core-events/index.ts:127), `PREVIEW_BUILDER_PROGRESS` (code/core/src/core-events/index.ts:129), `PREVIEW_INITIALIZED` (code/core/src/core-events/index.ts:128), `PREVIEW_KEYDOWN` (code/core/src/core-events/index.ts:130), `REGISTER_SUBSCRIPTION` (code/core/src/core-events/index.ts:131), `REQUEST_WHATS_NEW_DATA` (code/core/src/core-events/index.ts:160), `RESET_STORY_ARGS` (code/core/src/core-events/index.ts:132), `RESULT_WHATS_NEW_DATA` (code/core/src/core-events/index.ts:161), `SAVE_STORY_REQUEST` (code/core/src/core-events/index.ts:165), `SAVE_STORY_RESPONSE` (code/core/src/core-events/index.ts:166), `SELECT_STORY` (code/core/src/core-events/index.ts:133), `SET_CONFIG` (code/core/src/core-events/index.ts:134), `SET_CURRENT_STORY` (code/core/src/core-events/index.ts:135), `SET_FILTER` (code/core/src/core-events/index.ts:136), `SET_GLOBALS` (code/core/src/core-events/index.ts:137), `SET_INDEX` (code/core/src/core-events/index.ts:138), `SET_STORIES` (code/core/src/core-events/index.ts:139), `SET_WHATS_NEW_CACHE` (code/core/src/core-events/index.ts:162), `SHARED_STATE_CHANGED` (code/core/src/core-events/index.ts:140), `SHARED_STATE_SET` (code/core/src/core-events/index.ts:141), `SHARE_ISOLATE_MODE` (code/core/src/core-events/index.ts:175), `SHARE_POPOVER_OPENED` (code/core/src/core-events/index.ts:176), `SHARE_STORY_LINK` (code/core/src/core-events/index.ts:174), `STORIES_COLLAPSE_ALL` (code/core/src/core-events/index.ts:142), `STORIES_EXPAND_ALL` (code/core/src/core-events/index.ts:143), `STORY_ARGS_UPDATED` (code/core/src/core-events/index.ts:144), `STORY_CHANGED` (code/core/src/core-events/index.ts:145), `STORY_ERRORED` (code/core/src/core-events/index.ts:146), `STORY_FINISHED` (code/core/src/core-events/index.ts:152), `STORY_HOT_UPDATED` (code/core/src/core-events/index.ts:156), `STORY_INDEX_INVALIDATED` (code/core/src/core-events/index.ts:147), `STORY_MISSING` (code/core/src/core-events/index.ts:148), `STORY_PREPARED` (code/core/src/core-events/index.ts:149), `STORY_RENDERED` (code/core/src/core-events/index.ts:151), `STORY_RENDER_PHASE_CHANGED` (code/core/src/core-events/index.ts:150), `STORY_SPECIFIED` (code/core/src/core-events/index.ts:153), `STORY_THREW_EXCEPTION` (code/core/src/core-events/index.ts:154), `STORY_UNCHANGED` (code/core/src/core-events/index.ts:155), `TELEMETRY_ERROR` (code/core/src/core-events/index.ts:164), `TOGGLE_WHATS_NEW_NOTIFICATIONS` (code/core/src/core-events/index.ts:163), `UNHANDLED_ERRORS_WHILE_PLAYING` (code/core/src/core-events/index.ts:126), `UPDATE_GLOBALS` (code/core/src/core-events/index.ts:157), `UPDATE_QUERY_PARAMS` (code/core/src/core-events/index.ts:158), `UPDATE_STORY_ARGS` (code/core/src/core-events/index.ts:159), `analyzeMdx` (not located), `babelParse` (not located), `buildQueries` (code/core/src/test/testing-library.ts:40), `configure` (code/core/src/test/testing-library.ts:41), `createEvent` (code/core/src/test/testing-library.ts:42), `findAllByAltText` (code/core/src/test/testing-library.ts:44), `findAllByDisplayValue` (code/core/src/test/testing-library.ts:45), `findAllByLabelText` (code/core/src/test/testing-library.ts:46), `findAllByPlaceholderText` (code/core/src/test/testing-library.ts:47), `findAllByRole` (code/core/src/test/testing-library.ts:48), `findAllByTestId` (code/core/src/test/testing-library.ts:49), `findAllByText` (code/core/src/test/testing-library.ts:50), `findAllByTitle` (code/core/src/test/testing-library.ts:51), `findByAltText` (code/core/src/test/testing-library.ts:52), `findByDisplayValue` (code/core/src/test/testing-library.ts:53), `findByLabelText` (code/core/src/test/testing-library.ts:54), `findByPlaceholderText` (code/core/src/test/testing-library.ts:55), `findByRole` (code/core/src/test/testing-library.ts:56), `findByTestId` (code/core/src/test/testing-library.ts:57), `findByText` (code/core/src/test/testing-library.ts:58), `findByTitle` (code/core/src/test/testing-library.ts:59), `fireEvent` (code/core/src/test/testing-library.ts:43), `getAllByAltText` (code/core/src/test/testing-library.ts:60), `getAllByDisplayValue` (code/core/src/test/testing-library.ts:61), `getAllByLabelText` (code/core/src/test/testing-library.ts:62), `getAllByPlaceholderText` (code/core/src/test/testing-library.ts:63), `getAllByRole` (code/core/src/test/testing-library.ts:64), `getAllByTestId` (code/core/src/test/testing-library.ts:65), `getAllByText` (code/core/src/test/testing-library.ts:66), `getAllByTitle` (code/core/src/test/testing-library.ts:67), `getByAltText` (code/core/src/test/testing-library.ts:68), `getByDisplayValue` (code/core/src/test/testing-library.ts:69), `getByLabelText` (code/core/src/test/testing-library.ts:70), `getByPlaceholderText` (code/core/src/test/testing-library.ts:71), `getByRole` (code/core/src/test/testing-library.ts:72), `getByTestId` (code/core/src/test/testing-library.ts:73), `getByText` (code/core/src/test/testing-library.ts:74), `getByTitle` (code/core/src/test/testing-library.ts:75), `getConfig` (code/core/src/test/testing-library.ts:76), `getDefaultNormalizer` (code/core/src/test/testing-library.ts:77), `getElementError` (code/core/src/test/testing-library.ts:78), `getNodeText` (code/core/src/test/testing-library.ts:79), `getQueriesForElement` (code/core/src/test/testing-library.ts:80), `getRoles` (code/core/src/test/testing-library.ts:81), `getSuggestedQuery` (code/core/src/test/testing-library.ts:82), `instance` (not located), `isInaccessible` (code/core/src/test/testing-library.ts:83), `logDOM` (code/core/src/test/testing-library.ts:84), `logRoles` (code/core/src/test/testing-library.ts:85), `prettyDOM` (code/core/src/test/testing-library.ts:86), `prettyFormat` (code/core/src/test/testing-library.ts:111), `queries` (code/core/src/test/testing-library.ts:87), `queryAllByAltText` (code/core/src/test/testing-library.ts:88), `queryAllByAttribute` (code/core/src/test/testing-library.ts:89), `queryAllByDisplayValue` (code/core/src/test/testing-library.ts:90), `queryAllByLabelText` (code/core/src/test/testing-library.ts:91), `queryAllByPlaceholderText` (code/core/src/test/testing-library.ts:92), `queryAllByRole` (code/core/src/test/testing-library.ts:93), `queryAllByTestId` (code/core/src/test/testing-library.ts:94), `queryAllByText` (code/core/src/test/testing-library.ts:95), `queryAllByTitle` (code/core/src/test/testing-library.ts:96), `queryByAltText` (code/core/src/test/testing-library.ts:97), `queryByAttribute` (code/core/src/test/testing-library.ts:98), `queryByDisplayValue` (code/core/src/test/testing-library.ts:99), `queryByLabelText` (code/core/src/test/testing-library.ts:100), `queryByPlaceholderText` (code/core/src/test/testing-library.ts:101), `queryByRole` (code/core/src/test/testing-library.ts:102), `queryByTestId` (code/core/src/test/testing-library.ts:103), `queryByText` (code/core/src/test/testing-library.ts:104), `queryByTitle` (code/core/src/test/testing-library.ts:105), `queryHelpers` (code/core/src/test/testing-library.ts:106), `screen` (code/core/src/test/testing-library.ts:107), `transformSync` (not located), `userEvent` (code/core/src/test/testing-library.ts:123), `waitFor` (code/core/src/test/testing-library.ts:108), `waitForElementToBeRemoved` (code/core/src/test/testing-library.ts:109), `within` (code/core/src/test/testing-library.ts:110)

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 100% |
| Signature Accuracy | 100% |
| Type Coverage | 100% |

**Notes (§1a to §4b):**

- §1a: the inventory validated on the first pass (758 entries, floor of 464 names fully kept, spot-check clean); its `warnings` list is empty, so no form was left unbound for want of a place (0 forms).
- §1b: the reader's split-body cross-check returned no `cross_check_mismatches` (145 names written in two or more files), so no `split-body-mismatch` gap.
- §2 read by eye: `code/core/src/csf/csf-factories.ts`, `code/core/src/instrumenter/typings.d.ts`, `code/core/src/mocking-utils/esmWalker.ts`, `code/core/src/test/spy.ts`, `code/core/src/typings.d.ts` (each a file the runner parsed with one syntax error); `surface` ran once more with their per-file results. Unread files: none. The by-eye read of `code/core/src/test/spy.ts` added two names the runner did not record, `isMockFunction` and `mocks` (`export { isMockFunction, mocks };` at line 17, re-exported through `export * from './spy'` in `code/core/src/test/index.ts`); they bring the `tier_a_include` set from the runner's 368 to 370 names, equal to the stored count. Both are documented.
- Unresolved stars (an `export *` / `export type *` from another package, which adds no name):
  - `code/addons/docs/src/mdx-react-shim.ts`: `export * from '@mdx-js/react'`
  - `code/core/src/mocking-utils/esmWalker.ts`: `37: export type * from 'estree';`
  - `code/core/src/test/spy.ts`: `15: export type * from '@vitest/spy';`
  - `code/frameworks/react-vite/src/index.ts`: `export * from '@storybook/react'`
- 39 public entry points sit outside the brief's files in scope (`surface.json` warnings, e.g. `code/addons/links/src/index.ts`, `code/core/src/components/index.ts`); the effective denominator leaves them out by the brief's design.
- §2b numerator ground truth: skipped (no inflation signature: `stats.exports_documented` 378 differs from `stats.effective_denominator` 370).
- §2c stale names: 89 documented names the whole surface lacks; `classify-stale` marks none fabricated (70 with a `defined_at`, 13 with several declaring files, 6 with neither); the ledger grades each.
- §4b metadata count cross-check: Medium `metadata-drift` (stats.exports_public_api=1335 vs exports[].length=88, 93% drift) and Info `multi-denominator` (barrel=1335, documented=378). They describe data quality and change no denominator.
- §4c provenance line check: no `stale[]` item (every provenance line is a definition line).

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)
**Migration Section:** Section 4b verification skipped: evidence-report.md pins no `t2_future_count`. For a skill create-skill made, re-run create-skill to regenerate the report with the field (create-stack-skill does not write it).

### Structural Findings

| # | Type | Severity | Detail | Line |
|---|------|----------|--------|------|
| - | none | - | No structural issue: required sections present (description via `Overview`, usage via `Quick Start`, API surface via `Key API Summary`); 10 code fences, all balanced and language-tagged; no table row drift; no `scripts/` or `assets/` folder; every function and method export (326 names) is referenced in the usage-family scope; no async/sync contradiction among the 12 exports the examples call | - |

**Structural Issues:** 0

### Reference Consistency (split-body)

| # | Reference File | Export | Issue | Other Side | Reference Line | Contradicted Side |
|---|---------------|--------|-------|------------|---------------|-------------------|
| - | - | - | No split-body mismatch | - | - | - |

**Exports Cross-Checked:** 145
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
| Medium | 76 | stale-documentation (75): check each name against the source and the brief's scope, then update or remove its documentation or fix the scope (Update Skill does not repair it); metadata-drift (1): re-run Create Skill or edit the brief's scope, as each remediation says (counts that differ only by `Type::method` entries need no fix, and a hand edit of the counts does not hold) |
| Low | 0 | None |
| Info | 16 | observation (15): apply each only when you agree, as its remediation says, since it is advisory (a documented extra needs no change); multi-denominator (1): none, since the barrel and the documented surface measure different sets by design |
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

### GAP-036: Stale documentation: Modal

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:428
**Export:** Modal

**Issue:** `references/core-api.md:428` documents `Modal`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Modal/Modal.tsx:242` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Modal` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Modal/Modal.tsx:242`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Modal` at references/core-api.md:428.

### GAP-037: Stale documentation: OL

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:426
**Export:** OL

**Issue:** `references/core-api.md:426` documents `OL`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/OL.tsx:16` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `OL` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/OL.tsx:16`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `OL` at references/core-api.md:426.

### GAP-038: Stale documentation: P

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:426
**Export:** P

**Issue:** `references/core-api.md:426` documents `P`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/P.tsx:6` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `P` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/P.tsx:6`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `P` at references/core-api.md:426.

### GAP-039: Stale documentation: Placeholder

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:432
**Export:** Placeholder

**Issue:** `references/core-api.md:432` documents `Placeholder`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/placeholder/placeholder.tsx:22` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Placeholder` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/placeholder/placeholder.tsx:22`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Placeholder` at references/core-api.md:432.

### GAP-040: Stale documentation: Popover

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:430
**Export:** Popover

**Issue:** `references/core-api.md:430` documents `Popover`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Popover/Popover.tsx:77` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Popover` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Popover/Popover.tsx:77`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Popover` at references/core-api.md:430.

### GAP-041: Stale documentation: PopoverProvider

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:430
**Export:** PopoverProvider

**Issue:** `references/core-api.md:430` documents `PopoverProvider`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Popover/PopoverProvider.tsx:63` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `PopoverProvider` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Popover/PopoverProvider.tsx:63`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `PopoverProvider` at references/core-api.md:430.

### GAP-042: Stale documentation: PostMessageTransport

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:444
**Export:** PostMessageTransport

**Issue:** `references/core-api.md:444` documents `PostMessageTransport`, which the entry point `code/core/src/channels/index.ts` exports and `code/core/src/channels/postmessage/index.ts:29` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `PostMessageTransport` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/channels/postmessage/index.ts:29`, where it is defined, since its `scope.exclude` glob `code/core/src/channels/**` matches that file. To keep its documentation, narrow `code/core/src/channels/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `PostMessageTransport` at references/core-api.md:444.

### GAP-043: Stale documentation: Pre

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

**Issue:** the skill labels its documented form of `Story` partial, and it leaves out only members the source marks optional: documented `{ of?, meta?, inline?, height?, autoplay? }`, source `ComponentType<StoryProps>, StoryProps = { of?: ModuleExport; meta?: ModuleExports; inline?: boolean; height?: string; autoplay?: boolean; __forceInitialArgs?: boolean; __primary?: boolean }`: props list marks optionality with `?` (so it is not a list of bare names) and leaves out the optional own props '__forceInitialArgs' and '__primary' of StoryParameters

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

### GAP-029: Documented extra: ManagerConsumer

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager-api/root.tsx:266
**Export:** ManagerConsumer

**Issue:** `references/story-types.md:263` documents `ManagerConsumer`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ManagerConsumer` is a documented extra, a name the source still declares at `code/core/src/manager-api/root.tsx:266` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-030: Not checked by script: MaybeMocked (another package's export *)

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/core-api.md:66
**Export:** MaybeMocked

**Issue:** `references/core-api.md:66` documents `MaybeMocked`, which the enumerated source API surface lacks; a file the skill cites passes on another package's names through `export type * from '@vitest/spy';` (`code/core/src/test/spy.ts:15`), which no script resolves

**Remediation:** No change unless the other package does not export `MaybeMocked`: a file the skill cites passes on that package's names through `export type * from '@vitest/spy';` (`code/core/src/test/spy.ts:15`), and no script reads them, so check by hand that the package exports `MaybeMocked`.

### GAP-031: Not checked by script: MaybeMockedDeep (another package's export *)

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/core-api.md:67
**Export:** MaybeMockedDeep

**Issue:** `references/core-api.md:67` documents `MaybeMockedDeep`, which the enumerated source API surface lacks; a file the skill cites passes on another package's names through `export type * from '@vitest/spy';` (`code/core/src/test/spy.ts:15`), which no script resolves

**Remediation:** No change unless the other package does not export `MaybeMockedDeep`: a file the skill cites passes on that package's names through `export type * from '@vitest/spy';` (`code/core/src/test/spy.ts:15`), and no script reads them, so check by hand that the package exports `MaybeMockedDeep`.

### GAP-032: Not checked by script: MaybePartiallyMocked (another package's export *)

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/core-api.md:68
**Export:** MaybePartiallyMocked

**Issue:** `references/core-api.md:68` documents `MaybePartiallyMocked`, which the enumerated source API surface lacks; a file the skill cites passes on another package's names through `export type * from '@vitest/spy';` (`code/core/src/test/spy.ts:15`), which no script resolves

**Remediation:** No change unless the other package does not export `MaybePartiallyMocked`: a file the skill cites passes on that package's names through `export type * from '@vitest/spy';` (`code/core/src/test/spy.ts:15`), and no script reads them, so check by hand that the package exports `MaybePartiallyMocked`.

### GAP-033: Not checked by script: MaybePartiallyMockedDeep (another package's export *)

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/core-api.md:69
**Export:** MaybePartiallyMockedDeep

**Issue:** `references/core-api.md:69` documents `MaybePartiallyMockedDeep`, which the enumerated source API surface lacks; a file the skill cites passes on another package's names through `export type * from '@vitest/spy';` (`code/core/src/test/spy.ts:15`), which no script resolves

**Remediation:** No change unless the other package does not export `MaybePartiallyMockedDeep`: a file the skill cites passes on that package's names through `export type * from '@vitest/spy';` (`code/core/src/test/spy.ts:15`), and no script reads them, so check by hand that the package exports `MaybePartiallyMockedDeep`.

### GAP-034: Not checked by script: Mock (another package's export *)

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/core-api.md:64
**Export:** Mock

**Issue:** `references/core-api.md:64` documents `Mock`, which the enumerated source API surface lacks; a file the skill cites passes on another package's names through `export type * from '@vitest/spy';` (`code/core/src/test/spy.ts:15`), which no script resolves

**Remediation:** No change unless the other package does not export `Mock`: a file the skill cites passes on that package's names through `export type * from '@vitest/spy';` (`code/core/src/test/spy.ts:15`), and no script reads them, so check by hand that the package exports `Mock`.

### GAP-035: Not checked by script: MockInstance (another package's export *)

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/core-api.md:65
**Export:** MockInstance

**Issue:** `references/core-api.md:65` documents `MockInstance`, which the enumerated source API surface lacks; a file the skill cites passes on another package's names through `export type * from '@vitest/spy';` (`code/core/src/test/spy.ts:15`), which no script resolves

**Remediation:** No change unless the other package does not export `MockInstance`: a file the skill cites passes on that package's names through `export type * from '@vitest/spy';` (`code/core/src/test/spy.ts:15`), and no script reads them, so check by hand that the package exports `MockInstance`.

### GAP-044: Documented extra: RadioControl

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/docs/src/blocks/controls/options/Radio.tsx:57
**Export:** RadioControl

**Issue:** `references/doc-blocks.md:292` documents `RadioControl`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `RadioControl` is a documented extra, a name the source still declares at `code/addons/docs/src/blocks/controls/options/Radio.tsx:57` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

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
| 1 | I've got a component showcase file for my button and I want it to click the button on its own and check that the click callback actually got called — can you wire that up? | oms-storybook-react-vite (medium) | PASS |
| 2 | how do I make every component in my UI workshop switch between light and dark mode from the toolbar? | oms-storybook-react-vite (high) | PASS |
| 3 | reuse the examples I already wrote for my component gallery inside my unit tests so I don't duplicate the setup | oms-storybook-react-vite (high) | PASS |

Prompts synthesized (§4b.1 fallback) from SKILL.md's Common Workflows (the `play` interaction test with a mock action, the global theme decorator, portable stories in unit tests): SKILL.md holds no conversational trigger phrases. Catalog: the 4 skills in `skills/`. No description optimization hint: Tessl Review did not run and skill-check flagged no description issue.
