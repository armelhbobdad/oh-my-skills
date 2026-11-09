---
workflowType: 'test-skill'
skillName: 'oms-storybook-react-vite'
skillDir: 'skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite'
runId: '20261109T210146Z-513a2838'
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
testDate: '2026-11-09T21:01:46Z'
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

**Mode Rationale:** metadata.json records `skill_type: 'single'`, an individual skill, so naive mode applies: API-surface coverage, with a structural-only coherence check and no coherence category in scoring.

**Analysis Plan:**
- Coverage Check: Deep tier with the pinned source on disk (`/home/armel/.skf/workspace/repos/github.com/storybookjs/storybook` at e486d38): the public export inventory of the source, export coverage against SKILL.md and its references, signature accuracy and type coverage judged against the source by Test Skill's subagents.
- Coherence Check: structural checks only (naive mode): references named in SKILL.md resolve, and the documented examples and sections hold together; no integration-pattern scoring.

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
| `ArgsTable` | - | yes | - | - | WARN |
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
| `BuiltQueryMethods` | - | yes | - | - | WARN |
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
| `DocsParameters` | - | yes | - | - | WARN |
| `DocsProps` | type | yes | - | code/addons/docs/src/blocks/blocks/Docs.tsx:12 | PASS |
| `DocsRenderer` | class | yes | - | code/addons/docs/src/DocsRenderer.tsx:48 | PASS |
| `DocsStory` | const | yes | yes | code/addons/docs/src/blocks/blocks/DocsStory.tsx:42 | PASS |
| `DocsStoryProps` | type | yes | - | code/addons/docs/src/blocks/blocks/types.ts:9 | PASS |
| `DocsTypes` | interface | yes | - | code/addons/docs/src/types.ts:254 | PASS |
| `EVENT_ID` | const | yes | - | code/core/src/actions/constants.ts:4 | PASS |
| `Easing` | type | yes | - | code/core/src/theming/types.ts:61 | PASS |
| `ErrorFormatter` | - | yes | - | - | WARN |
| `EventType` | - | yes | - | - | WARN |
| `ExternalDocs` | function | yes | yes | code/addons/docs/src/blocks/blocks/external/ExternalDocs.tsx:26 | PASS |
| `ExternalDocsContainer` | function | yes | yes | code/addons/docs/src/blocks/blocks/external/ExternalDocsContainer.tsx:12 | PASS |
| `ExternalDocsProps` | type | yes | - | code/addons/docs/src/blocks/blocks/external/ExternalDocs.tsx:11 | PASS |
| `ExternalPreview` | - | yes | - | - | WARN |
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
| `Method` | - | yes | - | - | WARN |
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
| `PrettyDOMOptions` | - | yes | - | - | WARN |
| `Preview` | interface | yes | - | code/core/src/csf/csf-factories.ts:26 | PASS |
| `PreviewWeb` | class | yes | - | code/core/src/preview-api/modules/preview-web/PreviewWeb.tsx:11 | PASS |
| `PreviewWithSelection` | class | yes | - | code/core/src/preview-api/modules/preview-web/PreviewWithSelection.tsx:77 | PASS |
| `Primary` | const | yes | yes | code/addons/docs/src/blocks/blocks/Primary.tsx:16 | PASS |
| `PropDescriptor` | type | yes | - | code/core/src/preview-api/modules/store/filterArgTypes.ts:5 | PASS |
| `ProviderStrategyConfiguration` | interface | yes | - | code/addons/themes/src/decorators/provider.decorator.tsx:13 | PASS |
| `PureArgsTable` | function | yes | - | code/addons/docs/src/blocks/components/ArgsTable/ArgsTable.tsx:320 | PASS |
| `PureSourceProps` | - | yes | - | - | WARN |
| `PureStoryProps` | - | yes | - | - | WARN |
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
| `Variant` | - | yes | - | - | WARN |
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
| `inferArgTypes` | - | yes | - | - | WARN |
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
| `usePrimaryStory` | - | yes | - | - | WARN |
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
| `withMdxComponentOverride` | - | yes | - | - | WARN |
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
- **Stale Documentation:** 102, documented extras included
- **Scoring Warnings:**
  - Type Coverage leaves out each name the stale-scope guard restored or the extraction recorded with no kind, such as an extraction gap (the provenance map, when one is given, gives it no kind Type Coverage reads at its file): `isMockFunction`, `mocks`
- **Borderline Calls:**
  - `composeStories` (references/core-api.md:102), inventory reader: SKILL.md:117 (its third form) and core-api.md:102 (its first form) document storybook/preview-api's core composeStories, which the skill presents as another export than the React composeStories (another import path, citing portable-stories.ts:L274 against portable-stories.tsx:L148); the React forms (SKILL.md:117, SKILL.md:139, core-api.md:102 second form, story-types.md:219, the usages) are compared only with each other and the core forms only with each other, and every such pair agrees, so no cross_check_mismatches entry; left open by: A judge without the surface (coverage-check.md §1's reader) counts two declarations only when the two forms' own citations name two different files and the skill presents the forms as different things (another owner, module or import path); a citation of a re-export (a package `__init__` or index file the skill shows passing the name on) names no declaration, and when unsure the forms are compared as before; the other reading gives: a split-body mismatch, e.g. SKILL.md:139 composeStories(csfExports, projectAnnotations?) against references/core-api.md:102 (storiesImport: TModule, globalConfig: ProjectAnnotations<Renderer>, composeStoryFn: ComposeStoryFn = defaultComposeStory), since the two places that write both forms give neither a citation
  - `composeStory` (references/core-api.md:101), inventory reader: core-api.md:101 is core's renderer-agnostic composeStory (portable-stories.ts:L90, storybook/preview-api) and story-types.md:211 the four-parameter React wrapper (portable-stories.tsx:L106, @storybook/react-vite), which the skill presents as different things, so the two are never compared; left open by: A judge without the surface (coverage-check.md §1's reader) counts two declarations only when the two forms' own citations name two different files and the skill presents the forms as different things (another owner, module or import path); a citation of a re-export (a package `__init__` or index file the skill shows passing the name on) names no declaration, and when unsure the forms are compared as before; the other reading gives: a split-body mismatch: references/core-api.md:101 (storyAnnotations, componentAnnotations, projectAnnotations?, defaultConfig?, exportsName?) against references/story-types.md:211 (story, componentAnnotations, projectAnnotations?, exportsName?)
  - `create` (references/framework-config.md:376), inventory reader: the StorybookTheme row calls it the complete theme object returned by create(): a bare create() mention in another export's description, which states nothing about create's return, so it is not compared with core-api.md:282's ThemeVars; left open by: Each export's form is read alone: what the rows of other exports write, in the same table or file, states nothing about it, so `(action, sink, tracking_record, child_invalidation)` matches `child_invalidation: X | None = None` even when every other row of its table writes its defaults; the other reading gives: a split-body description mismatch on create's return: references/core-api.md:282 returns ThemeVars while references/framework-config.md:376 says create() returns the StorybookTheme
  - `Meta` (SKILL.md:120), inventory reader: Meta (no kindLabel) names both the React type and the addon-docs doc block and keeps one kind, type, taken from its type places; the doc block's places (SKILL.md:120, SKILL.md:143, doc-blocks.md:75) still record the usage and props forms they write, since the doc block is a value, not a type alias; left open by: A `type` alias carries none of them either, even one the skill writes as a function type (`type DecoratorFunction = (fn, c) => R`): only a value is called; the other reading gives: kind function for every Meta place, or the doc block's forms dropped as a type alias's, leaving <Meta of={ButtonStories} /> and MetaProps uncompared; no gap either way for the forms written here
  - `Primary` (SKILL.md:143), inventory reader: the fenced export const Primary: Story = {...} of SKILL.md, csf3-patterns.md and story-types.md declares the reader's own story, not the doc block, so it sets no kind; Primary (no kindLabel) takes function, as the other doc-block components do; left open by: A name the skill declares with `const`, a fenced `export const` included, is a `constant` when the skill gives it no kind label; the other reading gives: kind constant for every Primary place; no signature gap
  - `Primary` (references/doc-blocks.md:33), inventory reader: the Props (simplified) cell's none (FC with no props) is read as an empty props list, params empty with the column's partial label; left open by: An entry with no `params` key and no usage form writes no parameter list: it claims nothing about parameters, and only what it writes, such as its return type, is compared; the other reading gives: no params key (a word, not a form), claiming nothing; no gap either way, since the block takes no props
  - `Primary` (SKILL.md:120), inventory reader: <Primary /> in SKILL.md:120's running text is read as the JSX counterpart of an empty call, a mention, so it gives no entry; left open by: A name written with empty parentheses, or with only `...` or `…` between them, in running text or a description cell is a mention, not a form; the other reading gives: a usage entry <Primary /> at SKILL.md:120; no gap, the block taking no props
  - `Controls` (SKILL.md:120), inventory reader: <Controls /> in SKILL.md:120's running text is read as the JSX counterpart of an empty call, a mention, so it gives no entry; left open by: A name written with empty parentheses, or with only `...` or `…` between them, in running text or a description cell is a mention, not a form; the other reading gives: a usage entry <Controls /> at SKILL.md:120; no gap, every Controls prop being optional
  - `Stories` (SKILL.md:120), inventory reader: <Stories /> in SKILL.md:120's running text is read as the JSX counterpart of an empty call, a mention, so it gives no entry; left open by: A name written with empty parentheses, or with only `...` or `…` between them, in running text or a description cell is a mention, not a form; the other reading gives: a usage entry <Stories /> at SKILL.md:120; no gap, every Stories prop being optional
  - `Wrapper` (SKILL.md:133), inventory reader: <Wrapper><Story /></Wrapper> in the Decorator row is a placeholder wrapper inside an example decorator body, not a call of the addon-docs Wrapper export, so it gives Wrapper no entry at SKILL.md:133; left open by: A name written with arguments in running text or a description cell is a call (below), not a list of bare names, whatever comes before the name, unless it writes a parameter type, a `?`, a bare `*` or `/` (no call writes one), or a return type with no `await`, `new`, assignment, receiver or module path before the name (`await coco.mount(fn) -> Handle` is a call); the other reading gives: a usage entry <Wrapper><Story /></Wrapper> at SKILL.md:133, compared with references/doc-blocks.md:162's <Wrapper>{children}</Wrapper>; both pass children, so no gap
  - `Button` (references/csf3-patterns.md:149), inventory reader: the fenced <Button {...args} label={'set in play'} /> (csf3-patterns.md:149) and <Button {...args} /> (csf3-patterns.md:219) render the reader's Button imported from './Button', not storybook/internal/components' Button, so they give no entry; the sentence names definitions only, and this reading extends it to the example's own import; left open by: A function or class an example defines is the reader's own code, not a form of a same-named export; the other reading gives: usage entries for Button (its only forms being fenced), compared with storybook/internal/components' Button props: a Critical signature-mismatch if that Button takes no label prop
  - `Primary` (references/framework-config.md:354), inventory reader: under ### Per-test-file usage, render(<Primary />) renders the composed story the same block destructures from composeStories(stories), the reader's own component, not the Primary doc block, so it gives no entry; left open by: A call or JSX element of a name that a fenced example writes is not a place of its own when the skill also writes that name's form at a place that is no example (a heading, a table row, a props table, running text or a fenced declaration), unless the nearest heading above the example names a usage, its text holding the word usage whatever qualifies it (`## Usage`, `### Basic usage`, `### Usage pattern`; a bold label line such as `**Usage:**` is no heading): it gives no entry, so it is never compared, and a name whose only forms are in fenced examples keeps them; the other reading gives: a usage entry <Primary /> at framework-config.md:354; it sets no props, so no gap
  - `expect` (references/framework-config.md:355), inventory reader: the block imports expect from 'vitest', so expect(screen.getByRole('button')) under ### Per-test-file usage is Vitest's expect, not storybook/test's, and gives no entry; left open by: A call or JSX element of a name that a fenced example writes is not a place of its own when the skill also writes that name's form at a place that is no example (a heading, a table row, a props table, running text or a fenced declaration), unless the nearest heading above the example names a usage, its text holding the word usage whatever qualifies it (`## Usage`, `### Basic usage`, `### Usage pattern`; a bold label line such as `**Usage:**` is no heading): it gives no entry, so it is never compared, and a name whose only forms are in fenced examples keeps them; the other reading gives: a usage entry expect(screen.getByRole('button')) at framework-config.md:355; one argument, so no gap expected
  - `getByText` (references/csf3-patterns.md:118), inventory reader: the method Canvas.getByText has no form outside fenced examples (core-api.md:179 is the same-named function's), so the fenced canvas.getByText('Arg from story') keeps its method entry; left open by: A call or JSX element of a name that a fenced example writes is not a place of its own when the skill also writes that name's form at a place that is no example (a heading, a table row, a props table, running text or a fenced declaration), unless the nearest heading above the example names a usage, its text holding the word usage whatever qualifies it (`## Usage`, `### Basic usage`, `### Usage pattern`; a bold label line such as `**Usage:**` is no heading): it gives no entry, so it is never compared, and a name whose only forms are in fenced examples keeps them; the other reading gives: no entry, the getByText function's form at references/core-api.md:179 counting as the name's non-example form; no gap
  - `test` (references/csf3-patterns.md:117), inventory reader: Default.test('simple', ...) (csf3-patterns.md:117) and Primary.test('clicks', ...) (story-types.md:350) call a CSF4 story's test method, but the ReactStory declaration the skill writes documents no test member (story-types.md:307 only mentions test()), so they give no method entry; left open by: and so does one the skill calls through an instance or the class it documents with that member (`builder.provide(KEY, value)`, `canvas.getByRole('button')`), the class as `owner` and the call in `usage_signature`, never a usage of a same-named function; the other reading gives: method entries test, owner ReactStory, with those calls as usage_signature
  - `definePreviewAddon` (references/addons.md:184), inventory reader: definePreviewAddon is written only in the fenced excerpt of addon-vitest's index.ts, so that call is kept as its form and gives it an entry; left open by: A call or JSX element of a name that a fenced example writes is not a place of its own when the skill also writes that name's form at a place that is no example (a heading, a table row, a props table, running text or a fenced declaration), unless the nearest heading above the example names a usage, its text holding the word usage whatever qualifies it (`## Usage`, `### Basic usage`, `### Usage pattern`; a bold label line such as `**Usage:**` is no heading): it gives no entry, so it is never compared, and a name whose only forms are in fenced examples keeps them; the other reading gives: no entry, the excerpt showing addon source code rather than documenting a storybook export; no signature gap
  - `ReactParameters` (references/story-types.md:334), inventory reader: ReactParameters is described as exported by types.ts but not re-exported by @storybook/react, read as the skill saying the package does not export it, so with no floor place, heading, export table cell or fenced declaration it gets no entry; left open by: A name the skill presents only as a local import alias of another name, or says the source does not export, is not an export the skill documents either: it gets an entry only from a place `inventory-floor.json` gives it, a heading, an export table's first cell or a fenced declaration of it (an import is not one), never from a code span in prose or a description cell; the other reading gives: an entry at story-types.md:334 with its { react?: { rsc?: boolean; rootOptions?: RootOptions } } shape
  - `DEFAULT_DATA_ATTRIBUTE` (references/addons.md:110), inventory reader: the cell's module-local is read as qualifying both defaults, DEFAULT_ELEMENT_SELECTOR and DEFAULT_DATA_ATTRIBUTE, so neither gets an entry; left open by: A name the skill presents only as a local import alias of another name, or says the source does not export, is not an export the skill documents either: it gets an entry only from a place `inventory-floor.json` gives it, a heading, an export table's first cell or a fenced declaration of it (an import is not one), never from a code span in prose or a description cell; the other reading gives: an entry for DEFAULT_DATA_ATTRIBUTE at addons.md:110 (a code span that is the name), which a stale-name check could flag
  - `SetOptional` (references/story-types.md:95), inventory reader: SetOptional, a code span in (via AddMocks + SetOptional), is the type-fest helper inside StoryObj's declared type, an external library's type rather than a storybook export, so it gets no entry; left open by: A name the skill writes only in a type position (a parameter type, a return type or a type argument inside another entry's documented type or signature, or a parameter table's Type cell) is a type mention, not an export the skill documents, even when its code span is exactly the name, and gets no entry, unless the skill also writes it as one outside a type position: a place `inventory-floor.json` gives it, a heading, an export table's first cell, a code span that is the name or the name then `(`, or a fenced declaration; the other reading gives: an entry for SetOptional at story-types.md:95
  - `AfterEach` (references/addons.md:63), inventory reader: a code span that is exactly the name, outside a type position, documents a name the skill otherwise writes only in type positions, so AfterEach, DocsParameters, BaseAnnotations, CoreTypes, BuiltQueryMethods, EventType, Variant, Method, PrettyDOMOptions, PureSourceProps, PureStoryProps, StoryIdentifier, StoryContextForEnhancers and Renderer each get one entry at their first such place; left open by: A name the skill writes only in a type position (a parameter type, a return type or a type argument inside another entry's documented type or signature, or a parameter table's Type cell) is a type mention, not an export the skill documents, even when its code span is exactly the name, and gets no entry, unless the skill also writes it as one outside a type position: a place `inventory-floor.json` gives it, a heading, an export table's first cell, a code span that is the name or the name then `(`, or a fenced declaration; the other reading gives: no entries for them (code spans that only explain another export's type), so a stale-name check could not flag them nor coverage count them
  - `isStory` (references/core-api.md:143), inventory reader: names the skill writes while explaining another export (isStory and isMeta, written as calls with an argument in a description cell, so usage forms; inferArgTypes, AddonStore, SNIPPET_RENDERED, NAVIGATE_URL, usePrimaryStory, withMdxComponentOverride, ExternalPreview, ArgsTable, ManagerConsumer and useStorybookApi, mentions) are names the skill documents, each with one entry at its first place; left open by: A place that writes a name but no form of it, and no `methods`, `properties` or `fields` its entry would carry (a mention, a bare code span, an import, a heading or prose that names or describes it), gives it no entry when another place gives the name one, unless `inventory-floor.json` gives that place; of several such places of a name the skill documents and no other place gives an entry, the first alone gives one: in SKILL.md, else the file that sorts first by path, at its lowest line; the other reading gives: no entries, these being internals the skill explains rather than exports it documents; isStory(story) and isMeta(meta) would go uncompared
  - `PropDescriptor` (references/core-api.md:121), inventory reader: a type definition written in a cell or prose (PropDescriptor at core-api.md:121, SourceProps and SourceParameters at doc-blocks.md:90, HeadingProps at doc-blocks.md:112, AnchorProps at 114, DocsProps at 131, DocsContainerProps at 133, DocsStoryProps at 134, FrameworkOptions and BuilderOptions at framework-config.md:240) and a fenced type declaration the floor does not list (SKILL.md:175-177, story-types.md:171, 179 and 192-195) writes the type's own form or fields, so each gives an entry; left open by: A place that writes a name but no form of it, and no `methods`, `properties` or `fields` its entry would carry (a mention, a bare code span, an import, a heading or prose that names or describes it), gives it no entry when another place gives the name one, unless `inventory-floor.json` gives that place; of several such places of a name the skill documents and no other place gives an entry, the first alone gives one: in SKILL.md, else the file that sorts first by path, at its lowest line; the other reading gives: no entries at those places (a type alias carries no compared form, so they would count as mentions); no signature gap either way
  - `afterEach` (references/addons.md:63), inventory reader: the Value/Shape column is read as one that writes the row's shape, so its ({ id, reporting, parameters, globals, viewMode }) => Awaitable<void> gives afterEach's params and return_type; left open by: A description cell is any table cell but an export table's first cell and a cell whose column writes the call or signature, by its role (Signature, Props, Params, Parameters, Arguments, Usage, Syntax, Example and the like); a heading or an export table's first cell that writes `name()` is a form, recorded as written; the other reading gives: a description cell with no named call, so no params or return_type and nothing compared; no gap expected either way
  - `srOnlyStyles` (references/core-api.md:263), inventory reader: the shared function/const label of createGlobal, createReset and srOnlyStyles is split by name: function for the two create* helpers, constant for srOnlyStyles; left open by: The contract `validate-inventory.py` checks (coverage-check.md §1a): each `kind` is one of `function`, `class`, `type`, `constant`, `hook`, `interface`, `method`, `struct`, `enum`, `trait`, `macro` or `adapter`; the other reading gives: one kind (function or constant) for all three names; no signature gap
  - `story` (references/story-types.md:325), inventory reader: ReactMeta's story(/* a story object or a render function */) writes only a comment between its parentheses, which states no parameter list, so the method entry gives only its return_type (and so no at); left open by: A comment in a fenced block is no place of its own and states no form or return type: a form or a return it writes (`// start: ({ options }: {...}) => Promise<void>`, `# returns the dataset's PipelineRunInfo`) is a note on the code, not a form of the name; the other reading gives: an empty parameter list claiming story takes none: a Critical signature-mismatch against its overloads, which take a story object or a render function
  - `BooleanControl` (references/doc-blocks.md:269), inventory reader: FC<BooleanProps> in a Signature cell names the component's type, not a parameter list, so BooleanControl (and DateControl, FilesControl, NumberControl, ObjectControl, RangeControl, TextControl, OptionsControl, CheckboxControl, RadioControl and SelectControl, written the same way) get no params; left open by: `FC<P>`, `React.FC<P>`, `FunctionComponent<P>`, `ComponentType<P>`, a `memo`, `forwardRef` or other higher-order component result over `P`, and `(props: P) => JSX.Element` (or `ReactElement`, `ReactNode` or `null`) are one contract, the props `P`: a component's return type and its wrapper are never compared; the other reading gives: params such as props: BooleanProps, compared with the source props; no gap expected while the props type names the source's
  - `Unstyled` (references/doc-blocks.md:115), inventory reader: the Props cell names the props type React.DetailedHTMLProps<React.HTMLAttributes<HTMLDivElement>, HTMLDivElement> and no props list, so Unstyled gets no params; left open by: An entry with no `params` key and no usage form writes no parameter list: it claims nothing about parameters, and only what it writes, such as its return type, is compared; the other reading gives: params holding that props type, compared as inherited div props; no gap expected
  - `Markdown` (references/doc-blocks.md:111), inventory reader: the Props cell names MarkdownProps and describes children, options? and the spread rest in prose, writing no props list, so Markdown gets no params; left open by: An entry with no `params` key and no usage form writes no parameter list: it claims nothing about parameters, and only what it writes, such as its return type, is compared; the other reading gives: params { children, options? } read as a list of bare names; no gap expected
  - `createEvent` (references/core-api.md:208), inventory reader: createEvent, a const typed CreateObject & CreateFunction that the cell says is callable as (eventName, node, init?, options?) => Event, carries that form, and its per-event-name member form is recorded on the one member it names, click; left open by: A `const` whose value is a function (annotated with a function type, bound to an arrow, a `function` or a call that returns one, or written with a parameter list) carries the function form the skill writes for it as `params`; the other reading gives: no params (a data constant) and no click method entry; the source's const is typed by an external package, so no gap expected
  - `simulateDOMContentLoaded` (references/core-api.md:148), inventory reader: simulateDOMContentLoaded() opening a Signature cell is an empty call in a signature column, a form, recorded in usage_signature; left open by: An empty call `X()` written as a call example (in a heading, an export table's first cell, a call or signature column or a fenced example, never a mention) is one too, so it matches a source whose parameters are all optional; the other reading gives: an empty params list instead; either way it claims no required parameter, so no gap
  - `Story` (code/addons/docs/src/blocks/blocks/Story.tsx:134), signature judge: The form '{ of?, meta?, inline?, height?, autoplay? }' writes '?' marks but no types, so it is neither a typed props list nor a list of bare names (which the rules define as having 'no type, default or `?`'). I fell back on 'Its parameter list claims each parameter it lists, in that order, and no other', so leaving out the optional own props '__forceInitialArgs' and '__primary' is reported as an omitted-optional mismatch; left open by: An optional own prop a typed props list or a table leaves out is an `omitted-optional` difference; one a list of bare names or a usage leaves out, and an optional inherited prop, is no difference; the other reading gives: Read as a list of bare names (names without claiming the list is complete), leaving out the two optional own props is no difference: no mismatch
  - `Story` (code/addons/docs/src/blocks/blocks/Story.tsx:134), signature judge: The check's documented form has signature_form 'partial', but the only rule that lets a partial label leave out parameters is the one for the split-body cross-check. Reading a form, which governs this §2 comparison with the source, never consults signature_form, so I did not let the label excuse the two omitted optional props; left open by: A call, a list of bare names or a form its own file labels partial (each side's label is read from that side's file, not from the export's one `signature_form`) may leave out a parameter the other form does not state as required, unless leaving it out shifts a caller's positions (a language without keyword arguments, as above); any other form claims its list is complete, so leaving out a parameter the other writes is a mismatch (inventory-contract.md's examples); the other reading gives: If the partial label also excused omitted optional props against the source, the omitted '__forceInitialArgs' and '__primary' would be no difference: no mismatch
  - `actions` (code/core/src/actions/runtime/actions.ts:5), signature judge: The const's annotation ActionsFunction (code/core/src/actions/models/ActionsFunction.ts:4), an interface of eleven bodiless call signatures, is the function type whose parameters the const declares, and its call signatures form an overload set read as Overload sets says (TS bodiless signatures, a form matching any overload is no mismatch): form 0 `(handlerMap: Record<T, string>, options?: ActionOptions) => ActionsMap<T>` matches its first call signature exactly and form 1 `(...handlers: T[]) => ActionsMap<T>` its second, so neither is a mismatch; left open by: A const annotated with a function type declares that type's parameters: `export const build: ViteBuilder['build'] = async ({ options }) => ...` takes the one parameter `ViteBuilder['build']` names, and the arrow's destructuring is that same parameter; the other reading gives: Compared with the arrow's own `(...args: any[])` (return unannotated, so uncompared) instead, form 0 would be a Critical mismatch (its typed, complete list `handlerMap, options?` against a lone rest parameter `args`), and form 1 a Low or Info `parameter-name` mismatch (`...handlers: T[]` against `...args: any[]`)
  - `expect` (code/core/src/test/index.ts:24), signature judge: The unannotated binding `export const { expect } = instrument({ expect: rawExpect }, ...)` takes the call signature of the in-tree `Expect` interface (code/core/src/test/expect.ts:38, `<T>(actual: T, message?: string): Assertion<T>`), because `instrument<TObj>(obj: TObj, options?): TObj` gives back the type it is passed. The usage `expect(args.onClick)` passes `actual` at position 0, and leaving out the optional `message` makes no difference, so there is no mismatch; left open by: A const annotated with a function type declares that type's parameters: `export const build: ViteBuilder['build'] = async ({ options }) => ...` takes the one parameter `ViteBuilder['build']` names, and the arrow's destructuring is that same parameter; the other reading gives: no mismatch (the other reading, that a binding destructured with no annotation declares no parameter list and so its parameters go uncompared, also gives no mismatch)
- **Scoped Out by the Brief:** `A` (code/core/src/components/components/typography/elements/A.tsx:7), `AbstractToolbar` (code/core/src/components/components/Toolbar/Toolbar.tsx:15), `ActionBar` (code/core/src/components/components/ActionBar/ActionBar.tsx:89), `ActionItem` (code/core/src/components/components/ActionBar/ActionBar.tsx:72), `ActionList` (code/core/src/components/components/ActionList/ActionList.tsx:222), `AddonPanel` (code/core/src/components/components/addon-panel/addon-panel.tsx:36), `AngularMeta` (code/frameworks/angular/src/client/preview.ts:150), `AngularOptions` (code/frameworks/angular/src/types.ts:47), `AngularParameters` (code/frameworks/angular/src/client/types.ts:45), `AngularPreview` (code/frameworks/angular/src/client/preview.ts:81), `AngularRenderer` (code/frameworks/angular/src/client/types.ts:40), `AngularStory` (code/frameworks/angular/src/client/preview.ts:254), `BabelFileClass` (code/core/src/babel/index.ts:43), `BadMetaError` (code/core/src/csf-tools/CsfFile.ts:246), `Badge` (code/core/src/components/components/Badge/Badge.tsx:88), `Bar` (code/core/src/components/components/Bar/Bar.tsx:52), `BarProps` (code/core/src/components/components/Bar/Bar.tsx:7), `BaseLocationProvider` (code/core/src/router/router.tsx:144), `Blockquote` (code/core/src/components/components/typography/elements/Blockquote.tsx:6), `BuildIndexOptions` (code/core/src/core-server/build-index.ts:10), `BuildStaticStandaloneOptions` (code/core/src/core-server/build-static.ts:31), `Button` (code/core/src/components/components/Button/Button.tsx:53), `ButtonProps` (code/core/src/components/components/Button/Button.tsx:14), `CLI_COLORS` (code/core/src/node-logger/logger/colors.ts:3), `CacheEntry` (code/core/src/telemetry/event-cache.ts:12), `Card` (code/core/src/components/components/Card/Card.tsx:98), `Channel` (code/core/src/channels/main.ts:22), `ChannelEvent` (code/core/src/channels/types.ts:18), `ChannelHandler` (code/core/src/channels/types.ts:11), `ChannelLike` (code/core/src/channels/types.ts:36), `ChannelTransport` (code/core/src/channels/types.ts:13), `ClipboardCode` (code/core/src/components/components/clipboard/ClipboardCode.tsx:24), `Code` (code/core/src/components/components/typography/elements/Code.tsx:42), `Collapsible` (code/core/src/components/components/Collapsible/Collapsible.tsx:31), `ComponentArgTypesData` (code/core/src/core-server/utils/get-dummy-args-from-argtypes.ts:8), `ConfigFile` (code/core/src/csf-tools/ConfigFile.ts:140), `ConsoleLogger` (code/core/src/node-logger/logger/console.ts:340), `Context` (code/core/src/telemetry/types.ts:106), `CsfFile` (code/core/src/csf-tools/CsfFile.ts:280), `CsfOptions` (code/core/src/csf-tools/CsfFile.ts:200), `DEEPLY_EQUAL` (code/core/src/router/utils.ts:43), `DL` (code/core/src/components/components/typography/elements/DL.tsx:6), `Dependency` (code/core/src/telemetry/types.ts:48), `Div` (code/core/src/components/components/typography/elements/Div.tsx:5), `DocumentWrapper` (code/core/src/components/components/typography/DocumentWrapper.tsx:3), `EmptyTabContent` (code/core/src/components/components/Tabs/EmptyTabContent.tsx:47), `EnrichCsfOptions` (code/core/src/csf-tools/enrichCsf.ts:6), `ErrorCollector` (code/core/src/telemetry/error-collector.ts:13), `ErrorFormatter` (code/core/src/components/components/ErrorFormatter/ErrorFormatter.tsx:29), `EventType` (code/core/src/telemetry/types.ts:9), `FlexBar` (code/core/src/components/components/Bar/Bar.tsx:129), `Form` (code/core/src/components/components/Form/Form.tsx:11), `GenerateStoryOptions` (code/core/src/core-server/utils/generate-story.ts:21), `GenerateStoryResult` (code/core/src/core-server/utils/generate-story.ts:11), `H1` (code/core/src/components/components/typography/elements/H1.tsx:6), `H2` (code/core/src/components/components/typography/elements/H2.tsx:6), `H3` (code/core/src/components/components/typography/elements/H3.tsx:6), `H4` (code/core/src/components/components/typography/elements/H4.tsx:6), `H5` (code/core/src/components/components/typography/elements/H5.tsx:6), `H6` (code/core/src/components/components/typography/elements/H6.tsx:6), `HEARTBEAT_INTERVAL` (code/core/src/channels/websocket/index.ts:20), `HEARTBEAT_MAX_LATENCY` (code/core/src/channels/websocket/index.ts:21), `HR` (code/core/src/components/components/typography/elements/HR.tsx:3), `IErrorWithStdErrAndStdOut` (code/core/src/telemetry/sanitize.ts:4), `IStory` (code/frameworks/angular/src/client/types.ts:31), `IconButton` (code/core/src/components/components/Button/Button.tsx:327), `Img` (code/core/src/components/components/typography/elements/Img.tsx:3), `InitPayload` (code/core/src/telemetry/types.ts:131), `LI` (code/core/src/components/components/typography/elements/LI.tsx:6), `Link` (code/core/src/components/components/typography/link/link.tsx:198), `LinkProps` (code/core/src/router/types.ts:23), `ListItem` (code/core/src/components/components/tooltip/ListItem.tsx:249), `Listener` (code/core/src/channels/types.ts:24), `Location` (code/core/src/router/router.tsx:81), `LocationProvider` (code/core/src/router/router.tsx:143), `LogLevel` (code/core/src/node-logger/logger/logger.ts:46), `Match` (code/core/src/router/router.tsx:141), `MemoryRouter` (code/core/src/router/router.tsx:145), `MixedFactoryError` (code/core/src/csf-tools/CsfFile.ts:234), `Modal` (code/core/src/components/components/Modal/Modal.tsx:242), `ModalDecorator` (code/core/src/components/components/Modal/Modal.tsx:248), `MultipleMetaError` (code/core/src/csf-tools/CsfFile.ts:222), `NavigateFunction` (code/core/src/router/types.ts:14), `NavigateOptions` (code/core/src/router/types.ts:12), `NoMetaError` (code/core/src/csf-tools/CsfFile.ts:210), `OL` (code/core/src/components/components/typography/elements/OL.tsx:16), `Other` (code/core/src/router/types.ts:7), `P` (code/core/src/components/components/typography/elements/P.tsx:6), `Payload` (code/core/src/telemetry/types.ts:102), `Placeholder` (code/core/src/components/components/placeholder/placeholder.tsx:22), `Popover` (code/core/src/components/components/Popover/Popover.tsx:77), `PopoverProps` (code/core/src/components/components/Popover/Popover.tsx:9), `PopoverProvider` (code/core/src/components/components/Popover/PopoverProvider.tsx:63), `PopoverProviderProps` (code/core/src/components/components/Popover/PopoverProvider.tsx:13), `PopperPlacement` (code/core/src/components/components/shared/overlayHelpers.tsx:22), `PostMessageTransport` (code/core/src/channels/postmessage/index.ts:29), `Pre` (code/core/src/components/components/typography/elements/Pre.tsx:6), `PreactRenderer` (code/renderers/preact/src/types.ts:14), `ProgressSpinner` (code/core/src/components/components/ProgressSpinner/ProgressSpinner.tsx:66), `RenderData` (code/core/src/router/types.ts:21), `ResetWrapper` (code/core/src/components/components/typography/ResetWrapper.tsx:12), `Route` (code/core/src/router/router.tsx:141), `RouterData` (code/core/src/router/types.ts:16), `ScrollArea` (code/core/src/components/components/ScrollArea/ScrollArea.tsx:95), `Select` (code/core/src/components/components/Select/Select.tsx:201), `Separator` (code/core/src/components/components/Bar/Separator.tsx:9), `Spaced` (code/core/src/components/components/spaced/Spaced.tsx:63), `Span` (code/core/src/components/components/typography/elements/Span.tsx:6), `SpinnerInstance` (code/core/src/node-logger/prompts/prompt-provider-base.ts:46), `StatelessTab` (code/core/src/components/components/Tabs/StatelessTab.tsx:57), `StatelessTabList` (code/core/src/components/components/Tabs/StatelessTabList.tsx:66), `StatelessTabListProps` (code/core/src/components/components/Tabs/StatelessTabList.tsx:62), `StatelessTabPanel` (code/core/src/components/components/Tabs/StatelessTabPanel.tsx:30), `StatelessTabPanelProps` (code/core/src/components/components/Tabs/StatelessTabPanel.tsx:9), `StatelessTabProps` (code/core/src/components/components/Tabs/StatelessTab.tsx:7), `StatelessTabsView` (code/core/src/components/components/Tabs/StatelessTabsView.tsx:31), `StatelessTabsViewProps` (code/core/src/components/components/Tabs/StatelessTabsView.tsx:27), `StaticMeta` (code/core/src/csf-tools/CsfFile.ts:258), `StaticStory` (code/core/src/csf-tools/CsfFile.ts:265), `StoryData` (code/core/src/router/utils.ts:9), `StoryIndexGenerator` (code/core/src/core-server/utils/StoryIndexGenerator.ts:101), `StoryTest` (code/core/src/csf-tools/CsfFile.ts:271), `StorybookAddon` (code/core/src/telemetry/types.ts:53), `StorybookBuilderOptions` (code/frameworks/angular/src/builders/build-storybook/index.ts:38), `StorybookBuilderOutput` (code/frameworks/angular/src/builders/build-storybook/index.ts:68), `StorybookIcon` (code/core/src/components/brand/StorybookIcon.tsx:3), `StorybookLogo` (code/core/src/components/brand/StorybookLogo.tsx:7), `StorybookMetadata` (code/core/src/telemetry/types.ts:57), `StyledConsoleLogger` (code/core/src/node-logger/logger/console.ts:340), `SvelteRenderer` (code/renderers/svelte/src/types.ts:11), `SyntaxHighlighter` (code/core/src/components/components/syntaxhighlighter/lazy-syntaxhighlighter.tsx:52), `SyntaxHighlighterFormatTypes` (code/core/src/components/components/syntaxhighlighter/syntaxhighlighter-types.ts:24), `SyntaxHighlighterProps` (code/core/src/components/components/syntaxhighlighter/syntaxhighlighter-types.ts:47), `SyntaxHighlighterRendererProps` (code/core/src/components/components/syntaxhighlighter/syntaxhighlighter-types.ts:5), `TT` (code/core/src/components/components/typography/elements/TT.tsx:5), `TabBar` (code/core/src/components/components/Tabs/Tabs.tsx:61), `TabButton` (code/core/src/components/components/Tabs/Button.tsx:139), `TabList` (code/core/src/components/components/Tabs/TabList.tsx:150), `TabListProps` (code/core/src/components/components/Tabs/TabList.tsx:146), `TabPanel` (code/core/src/components/components/Tabs/TabPanel.tsx:34), `TabPanelProps` (code/core/src/components/components/Tabs/TabPanel.tsx:12), `TabProps` (code/core/src/components/components/Tabs/TabsView.tsx:15), `TabWrapper` (code/core/src/components/components/Tabs/Tabs.tsx:120), `Table` (code/core/src/components/components/typography/elements/Table.tsx:6), `Tabs` (code/core/src/components/components/Tabs/Tabs.tsx:188), `TabsState` (code/core/src/components/components/Tabs/Tabs.tsx:287), `TabsView` (code/core/src/components/components/Tabs/TabsView.tsx:106), `TabsViewProps` (code/core/src/components/components/Tabs/TabsView.tsx:64), `TaskLogInstance` (code/core/src/node-logger/prompts/prompt-provider-base.ts:54), `TelemetryData` (code/core/src/telemetry/types.ts:119), `TelemetryEvent` (code/core/src/telemetry/types.ts:125), `ToggleButton` (code/core/src/components/components/ToggleButton/ToggleButton.tsx:16), `Toolbar` (code/core/src/components/components/Toolbar/Toolbar.tsx:36), `Tooltip` (code/core/src/components/components/tooltip/Tooltip.tsx:7), `TooltipLinkList` (code/core/src/components/components/tooltip/TooltipLinkList.tsx:70), `TooltipLinkListLink` (code/core/src/components/components/tooltip/TooltipLinkList.tsx:39), `TooltipMessage` (code/core/src/components/components/tooltip/TooltipMessage.tsx:47), `TooltipNote` (code/core/src/components/components/tooltip/TooltipNote.tsx:23), `TooltipNoteProps` (code/core/src/components/components/tooltip/TooltipNote.tsx:19), `TooltipProps` (code/core/src/components/components/tooltip/Tooltip.tsx:5), `TooltipProvider` (code/core/src/components/components/tooltip/TooltipProvider.tsx:108), `TooltipProviderProps` (code/core/src/components/components/tooltip/TooltipProvider.tsx:14), `TransformComponentType` (code/frameworks/angular/src/client/public-types.ts:56), `UL` (code/core/src/components/components/typography/elements/UL.tsx:16), `WebComponentsMeta` (code/renderers/web-components/src/preview.ts:160), `WebComponentsPreview` (code/renderers/web-components/src/preview.ts:85), `WebComponentsRenderer` (code/renderers/web-components/src/types.ts:14), `WebComponentsStory` (code/renderers/web-components/src/preview.ts:264), `WebComponentsTypes` (code/renderers/web-components/src/types.ts:24), `WebsocketTransport` (code/core/src/channels/websocket/index.ts:23), `WithTooltip` (code/core/src/components/components/tooltip/lazy-WithTooltip.tsx:8), `WithTooltipPure` (code/core/src/components/components/tooltip/lazy-WithTooltip.tsx:18), `Zoom` (code/core/src/components/components/Zoom/Zoom.tsx:4), `addToGlobalContext` (code/core/src/telemetry/telemetry.ts:26), `applicationConfig` (code/frameworks/angular/src/client/decorators.ts:37), `argsToTemplate` (code/frameworks/angular/src/client/argsToTemplate.ts:59), `babelParseExpression` (code/core/src/babel/babelParse.ts:52), `babelParseFile` (code/core/src/csf-tools/CsfFile.ts:1062), `babelPrint` (code/core/src/babel/babelParse.ts:42), `buildArgsParam` (code/core/src/router/utils.ts:186), `buildDevStandalone` (code/core/src/core-server/build-dev.ts:44), `buildIndex` (code/core/src/core-server/build-index.ts:12), `buildIndexStandalone` (code/core/src/core-server/build-index.ts:39), `buildStaticStandalone` (code/core/src/core-server/build-static.ts:35), `canUpdateVitestConfigFile` (code/core/src/babel/vitest-config-helpers.ts:159), `canUpdateVitestWorkspaceFile` (code/core/src/babel/vitest-config-helpers.ts:204), `cleanPaths` (code/core/src/telemetry/sanitize.ts:24), `codeCommon` (code/core/src/components/components/typography/lib/common.tsx:22), `colors` (code/core/src/node-logger/index.ts:57), `componentTransform` (code/core/src/csf-tools/vitest-plugin/component-transformer.ts:285), `componentWrapperDecorator` (code/frameworks/angular/src/client/decorators.ts:60), `components` (code/core/src/components/index.ts:133), `computeStorybookMetadata` (code/core/src/telemetry/storybook-metadata.ts:105), `convertToReactAriaPlacement` (code/core/src/components/components/shared/overlayHelpers.tsx:24), `createBrowserChannel` (code/core/src/channels/index.ts:32), `createCopyToClipboardFunction` (code/core/src/components/components/syntaxhighlighter/clipboard.ts:26), `createHyperlink` (code/core/src/node-logger/wrap-utils.ts:155), `createReactiveProps` (code/renderers/svelte/static/createReactiveProps.svelte.js:10), `deepDiff` (code/core/src/router/utils.ts:44), `deepMerge` (code/frameworks/angular/src/server/framework-preset-angular-cli.ts:95), `enrichCsf` (code/core/src/csf-tools/enrichCsf.ts:144), `enrichCsfMeta` (code/core/src/csf-tools/enrichCsf.ts:129), `enrichCsfStory` (code/core/src/csf-tools/enrichCsf.ts:12), `experimental_loadStorybook` (code/core/src/core-server/load.ts:18), `extractDescription` (code/core/src/csf-tools/enrichCsf.ts:158), `extractSource` (code/core/src/csf-tools/enrichCsf.ts:152), `formatConfig` (code/core/src/csf-tools/ConfigFile.ts:1165), `formatCsf` (code/core/src/csf-tools/CsfFile.ts:1083), `framework` (code/core/src/core-server/presets/common-override-preset.ts:5), `generate` (code/core/src/babel/index.ts:38), `generateStoryFile` (code/core/src/core-server/utils/generate-story.ts:64), `getConfigObjectFromMergeArg` (code/core/src/babel/vitest-config-helpers.ts:49), `getCustomElements` (code/renderers/web-components/src/framework-api.ts:37), `getEffectiveMergeConfigCall` (code/core/src/babel/vitest-config-helpers.ts:78), `getErrorLevel` (code/core/src/core-server/withTelemetry.ts:40), `getLastEvents` (code/core/src/telemetry/event-cache.ts:41), `getMatch` (code/core/src/router/utils.ts:233), `getPrecedingUpgrade` (code/core/src/telemetry/event-cache.ts:68), `getServerPort` (code/core/src/core-server/utils/server-address.ts:34), `getSessionId` (code/core/src/telemetry/session-id.ts:18), `getStoryHref` (code/core/src/components/components/utils/getStoryHref.ts:15), `getStorySortParameter` (code/core/src/csf-tools/getStorySortParameter.ts:96), `getStorybookMetadata` (code/core/src/telemetry/storybook-metadata.ts:312), `getTargetConfigObject` (code/core/src/babel/vitest-config-helpers.ts:118), `hrefTo` (code/addons/links/src/utils.ts:39), `interleaveSeparators` (code/core/src/components/components/Bar/Separator.tsx:29), `isCsfFactoryPreview` (code/core/src/csf-tools/ConfigFile.ts:1187), `isDefineConfigLike` (code/core/src/babel/vitest-config-helpers.ts:35), `isExampleStoryId` (code/core/src/telemetry/index.ts:26), `isImportedDefineConfigLikeIdentifier` (code/core/src/babel/vitest-config-helpers.ts:18), `isModuleMock` (code/core/src/csf-tools/CsfFile.ts:116), `isTelemetryEnabled` (code/core/src/core-server/withTelemetry.ts:157), `isValidComponent` (code/renderers/web-components/src/framework-api.ts:3), `isValidMetaData` (code/renderers/web-components/src/framework-api.ts:13), `isValidPreviewPath` (code/core/src/csf-tools/CsfFile.ts:43), `linkTo` (code/addons/links/src/utils.ts:61), `loadConfig` (code/core/src/csf-tools/ConfigFile.ts:1160), `loadCsf` (code/core/src/csf-tools/CsfFile.ts:1077), `logTracker` (code/core/src/node-logger/logger/log-tracker.ts:95), `mapStaticDir` (code/core/src/core-server/utils/server-statics.ts:198), `metaFrameworks` (code/core/src/telemetry/storybook-metadata.ts:33), `moduleMetadata` (code/frameworks/angular/src/client/decorators.ts:11), `nameSpaceClassNames` (code/core/src/components/components/typography/DocumentFormatting.tsx:1), `navigate` (code/addons/links/src/utils.ts:36), `oneWayHash` (code/core/src/telemetry/one-way-hash.ts:4), `parsePath` (code/core/src/router/utils.ts:17), `parserOptions` (code/core/src/babel/babelParse.ts:21), `printConfig` (code/core/src/csf-tools/ConfigFile.ts:1169), `printCsf` (code/core/src/csf-tools/CsfFile.ts:1096), `prompt` (code/core/src/node-logger/prompts/index.ts:5), `protectUrls` (code/core/src/node-logger/wrap-utils.ts:70), `queryFromLocation` (code/core/src/router/utils.ts:222), `readConfig` (code/core/src/csf-tools/ConfigFile.ts:1173), `readCsf` (code/core/src/csf-tools/CsfFile.ts:1100), `removeAnsiEscapeCodes` (code/core/src/telemetry/sanitize.ts:15), `resetComponents` (code/core/src/components/index.ts:142), `resolveExpression` (code/core/src/babel/expression-resolver.ts:22), `runNgcc` (code/frameworks/angular/src/server/framework-preset-angular-ivy.ts:37), `sanitizeAddonName` (code/core/src/telemetry/storybook-metadata.ts:50), `sanitizeError` (code/core/src/telemetry/sanitize.ts:64), `sendTelemetryError` (code/core/src/core-server/withTelemetry.ts:91), `setCustomElements` (code/renderers/web-components/src/framework-api.ts:29), `setCustomElementsManifest` (code/renderers/web-components/src/framework-api.ts:33), `stories` (code/core/src/core-server/presets/common-override-preset.ts:18), `stringifyQuery` (code/core/src/router/utils.ts:226), `telemetry` (code/core/src/telemetry/index.ts:31), `traverse` (code/core/src/babel/index.ts:39), `typescript` (code/core/src/core-server/presets/common-override-preset.ts:25), `unwrapTSExpression` (code/core/src/babel/expression-resolver.ts:4), `useNavigate` (code/core/src/router/router.tsx:45), `useTabsState` (code/core/src/components/components/Tabs/TabsView.tsx:30), `vitestTransform` (code/core/src/csf-tools/vitest-plugin/transformer.ts:108), `webpackFinal` (code/frameworks/angular/src/server/framework-preset-angular-cli.ts:15), `withLinks` (code/addons/links/src/utils.ts:110), `withReset` (code/core/src/components/components/typography/lib/common.tsx:36), `withTelemetry` (code/core/src/core-server/withTelemetry.ts:161), `writeConfig` (code/core/src/csf-tools/ConfigFile.ts:1178), `writeCsf` (code/core/src/csf-tools/CsfFile.ts:1105)
- **Extraction Gaps:** `ARGTYPES_INFO_REQUEST` (code/core/src/core-events/index.ts:167), `ARGTYPES_INFO_RESPONSE` (code/core/src/core-events/index.ts:168), `BabelFile` (not located), `CHANNEL_CREATED` (code/core/src/core-events/index.ts:112), `CHANNEL_WS_DISCONNECT` (code/core/src/core-events/index.ts:111), `CONFIG_ERROR` (code/core/src/core-events/index.ts:113), `CREATE_NEW_STORYFILE_REQUEST` (code/core/src/core-events/index.ts:114), `CREATE_NEW_STORYFILE_RESPONSE` (code/core/src/core-events/index.ts:115), `CURRENT_STORY_WAS_SET` (code/core/src/core-events/index.ts:116), `DOCS_PREPARED` (code/core/src/core-events/index.ts:117), `DOCS_RENDERED` (code/core/src/core-events/index.ts:118), `FILE_COMPONENT_SEARCH_REQUEST` (code/core/src/core-events/index.ts:119), `FILE_COMPONENT_SEARCH_RESPONSE` (code/core/src/core-events/index.ts:120), `FORCE_REMOUNT` (code/core/src/core-events/index.ts:122), `FORCE_RE_RENDER` (code/core/src/core-events/index.ts:121), `GHOST_STORIES_REQUEST` (code/core/src/core-events/index.ts:169), `GHOST_STORIES_RESPONSE` (code/core/src/core-events/index.ts:170), `GLOBALS_UPDATED` (code/core/src/core-events/index.ts:123), `GeneratorOptions` (not located), `MANAGER_INERT_ATTRIBUTE_CHANGED` (code/core/src/core-events/index.ts:173), `NAVIGATE_URL` (code/core/src/core-events/index.ts:124), `NodePath` (not located), `OPEN_IN_EDITOR_REQUEST` (code/core/src/core-events/index.ts:171), `OPEN_IN_EDITOR_RESPONSE` (code/core/src/core-events/index.ts:172), `PLAY_FUNCTION_THREW_EXCEPTION` (code/core/src/core-events/index.ts:125), `PRELOAD_ENTRIES` (code/core/src/core-events/index.ts:127), `PREVIEW_BUILDER_PROGRESS` (code/core/src/core-events/index.ts:129), `PREVIEW_INITIALIZED` (code/core/src/core-events/index.ts:128), `PREVIEW_KEYDOWN` (code/core/src/core-events/index.ts:130), `REGISTER_SUBSCRIPTION` (code/core/src/core-events/index.ts:131), `REQUEST_WHATS_NEW_DATA` (code/core/src/core-events/index.ts:160), `RESET_STORY_ARGS` (code/core/src/core-events/index.ts:132), `RESULT_WHATS_NEW_DATA` (code/core/src/core-events/index.ts:161), `SAVE_STORY_REQUEST` (code/core/src/core-events/index.ts:165), `SAVE_STORY_RESPONSE` (code/core/src/core-events/index.ts:166), `SELECT_STORY` (code/core/src/core-events/index.ts:133), `SET_CONFIG` (code/core/src/core-events/index.ts:134), `SET_CURRENT_STORY` (code/core/src/core-events/index.ts:135), `SET_FILTER` (code/core/src/core-events/index.ts:136), `SET_GLOBALS` (code/core/src/core-events/index.ts:137), `SET_INDEX` (code/core/src/core-events/index.ts:138), `SET_STORIES` (code/core/src/core-events/index.ts:139), `SET_WHATS_NEW_CACHE` (code/core/src/core-events/index.ts:162), `SHARED_STATE_CHANGED` (code/core/src/core-events/index.ts:140), `SHARED_STATE_SET` (code/core/src/core-events/index.ts:141), `SHARE_ISOLATE_MODE` (code/core/src/core-events/index.ts:175), `SHARE_POPOVER_OPENED` (code/core/src/core-events/index.ts:176), `SHARE_STORY_LINK` (code/core/src/core-events/index.ts:174), `STORIES_COLLAPSE_ALL` (code/core/src/core-events/index.ts:142), `STORIES_EXPAND_ALL` (code/core/src/core-events/index.ts:143), `STORY_ARGS_UPDATED` (code/core/src/core-events/index.ts:144), `STORY_CHANGED` (code/core/src/core-events/index.ts:145), `STORY_ERRORED` (code/core/src/core-events/index.ts:146), `STORY_FINISHED` (code/core/src/core-events/index.ts:152), `STORY_HOT_UPDATED` (code/core/src/core-events/index.ts:156), `STORY_INDEX_INVALIDATED` (code/core/src/core-events/index.ts:147), `STORY_MISSING` (code/core/src/core-events/index.ts:148), `STORY_PREPARED` (code/core/src/core-events/index.ts:149), `STORY_RENDERED` (code/core/src/core-events/index.ts:151), `STORY_RENDER_PHASE_CHANGED` (code/core/src/core-events/index.ts:150), `STORY_SPECIFIED` (code/core/src/core-events/index.ts:153), `STORY_THREW_EXCEPTION` (code/core/src/core-events/index.ts:154), `STORY_UNCHANGED` (code/core/src/core-events/index.ts:155), `TELEMETRY_ERROR` (code/core/src/core-events/index.ts:164), `TOGGLE_WHATS_NEW_NOTIFICATIONS` (code/core/src/core-events/index.ts:163), `UNHANDLED_ERRORS_WHILE_PLAYING` (code/core/src/core-events/index.ts:126), `UPDATE_GLOBALS` (code/core/src/core-events/index.ts:157), `UPDATE_QUERY_PARAMS` (code/core/src/core-events/index.ts:158), `UPDATE_STORY_ARGS` (code/core/src/core-events/index.ts:159), `analyzeMdx` (not located), `babelParse` (not located), `buildQueries` (code/core/src/test/testing-library.ts:40), `configure` (code/core/src/test/testing-library.ts:41), `createEvent` (code/core/src/test/testing-library.ts:42), `findAllByAltText` (code/core/src/test/testing-library.ts:44), `findAllByDisplayValue` (code/core/src/test/testing-library.ts:45), `findAllByLabelText` (code/core/src/test/testing-library.ts:46), `findAllByPlaceholderText` (code/core/src/test/testing-library.ts:47), `findAllByRole` (code/core/src/test/testing-library.ts:48), `findAllByTestId` (code/core/src/test/testing-library.ts:49), `findAllByText` (code/core/src/test/testing-library.ts:50), `findAllByTitle` (code/core/src/test/testing-library.ts:51), `findByAltText` (code/core/src/test/testing-library.ts:52), `findByDisplayValue` (code/core/src/test/testing-library.ts:53), `findByLabelText` (code/core/src/test/testing-library.ts:54), `findByPlaceholderText` (code/core/src/test/testing-library.ts:55), `findByRole` (code/core/src/test/testing-library.ts:56), `findByTestId` (code/core/src/test/testing-library.ts:57), `findByText` (code/core/src/test/testing-library.ts:58), `findByTitle` (code/core/src/test/testing-library.ts:59), `fireEvent` (code/core/src/test/testing-library.ts:43), `getAllByAltText` (code/core/src/test/testing-library.ts:60), `getAllByDisplayValue` (code/core/src/test/testing-library.ts:61), `getAllByLabelText` (code/core/src/test/testing-library.ts:62), `getAllByPlaceholderText` (code/core/src/test/testing-library.ts:63), `getAllByRole` (code/core/src/test/testing-library.ts:64), `getAllByTestId` (code/core/src/test/testing-library.ts:65), `getAllByText` (code/core/src/test/testing-library.ts:66), `getAllByTitle` (code/core/src/test/testing-library.ts:67), `getByAltText` (code/core/src/test/testing-library.ts:68), `getByDisplayValue` (code/core/src/test/testing-library.ts:69), `getByLabelText` (code/core/src/test/testing-library.ts:70), `getByPlaceholderText` (code/core/src/test/testing-library.ts:71), `getByRole` (code/core/src/test/testing-library.ts:72), `getByTestId` (code/core/src/test/testing-library.ts:73), `getByText` (code/core/src/test/testing-library.ts:74), `getByTitle` (code/core/src/test/testing-library.ts:75), `getConfig` (code/core/src/test/testing-library.ts:76), `getDefaultNormalizer` (code/core/src/test/testing-library.ts:77), `getElementError` (code/core/src/test/testing-library.ts:78), `getNodeText` (code/core/src/test/testing-library.ts:79), `getQueriesForElement` (code/core/src/test/testing-library.ts:80), `getRoles` (code/core/src/test/testing-library.ts:81), `getSuggestedQuery` (code/core/src/test/testing-library.ts:82), `instance` (not located), `isInaccessible` (code/core/src/test/testing-library.ts:83), `logDOM` (code/core/src/test/testing-library.ts:84), `logRoles` (code/core/src/test/testing-library.ts:85), `prettyDOM` (code/core/src/test/testing-library.ts:86), `prettyFormat` (code/core/src/test/testing-library.ts:111), `queries` (code/core/src/test/testing-library.ts:87), `queryAllByAltText` (code/core/src/test/testing-library.ts:88), `queryAllByAttribute` (code/core/src/test/testing-library.ts:89), `queryAllByDisplayValue` (code/core/src/test/testing-library.ts:90), `queryAllByLabelText` (code/core/src/test/testing-library.ts:91), `queryAllByPlaceholderText` (code/core/src/test/testing-library.ts:92), `queryAllByRole` (code/core/src/test/testing-library.ts:93), `queryAllByTestId` (code/core/src/test/testing-library.ts:94), `queryAllByText` (code/core/src/test/testing-library.ts:95), `queryAllByTitle` (code/core/src/test/testing-library.ts:96), `queryByAltText` (code/core/src/test/testing-library.ts:97), `queryByAttribute` (code/core/src/test/testing-library.ts:98), `queryByDisplayValue` (code/core/src/test/testing-library.ts:99), `queryByLabelText` (code/core/src/test/testing-library.ts:100), `queryByPlaceholderText` (code/core/src/test/testing-library.ts:101), `queryByRole` (code/core/src/test/testing-library.ts:102), `queryByTestId` (code/core/src/test/testing-library.ts:103), `queryByText` (code/core/src/test/testing-library.ts:104), `queryByTitle` (code/core/src/test/testing-library.ts:105), `queryHelpers` (code/core/src/test/testing-library.ts:106), `screen` (code/core/src/test/testing-library.ts:107), `transformSync` (not located), `userEvent` (code/core/src/test/testing-library.ts:123), `waitFor` (code/core/src/test/testing-library.ts:108), `waitForElementToBeRemoved` (code/core/src/test/testing-library.ts:109), `within` (code/core/src/test/testing-library.ts:110)

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 100% |
| Signature Accuracy | 100% |
| Type Coverage | 100% |

**Notes:**

- Inventory (§1, §1a): the §1 reader subagent listed 778 entries from SKILL.md and the six `references/*.md` files (SKILL.md's `## Full` headings are stubs that point to them). `validate-inventory.py` accepted it on the first pass: no violations, no warnings (no form left unbound for want of a place), every one of the 464 floor names present, spot-check sample `A`, `ToggleButton`, `withoutVitePlugins` found. 147 names are cross-checked (written in two or more files).
- Split-body cross-check (§1b): the reader found no `cross_check_mismatches`, so no `split-body-mismatch` gap is recorded.
- Files read by eye (§2, `extraction.readByEye`, each a parse error the runner reported): `code/core/src/csf/csf-factories.ts`, `code/core/src/instrumenter/typings.d.ts`, `code/core/src/mocking-utils/esmWalker.ts`, `code/core/src/test/spy.ts`, `code/core/src/typings.d.ts`. Their exports reached the surface through one `surface --per-file` pass; `instrumenter/typings.d.ts` and `typings.d.ts` are global declaration scripts with no module exports. Unread files (`extraction.unread`): none.
- Unresolved stars (`export * from` another package, which adds no name): `code/addons/docs/src/mdx-react-shim.ts: export * from '@mdx-js/react'`, `code/core/src/mocking-utils/esmWalker.ts:37: export type * from 'estree';`, `code/core/src/test/spy.ts:15: export type * from '@vitest/spy';`, `code/frameworks/react-vite/src/index.ts: export * from '@storybook/react'`.
- Signature comparison (§2): `score-signatures.py plan` planned 173 checks over 69 source files; 69 judge subagents, one per `files[]` entry, compared them by `references/signature-comparison-rules.md`. One mismatch came back (`Story`, a partial form, graded Info `Partial signature`); Signature Accuracy 173/173.
- Numerator ground truth (§2b): skipped (the declared count is not equal to the denominator, so there is no inflation signature).
- Metadata count cross-check (§4b): one Medium `metadata-drift` finding (`stats.exports_public_api`=1335 against `exports[].length`=88, 93% drift) and one Info `multi-denominator` finding (barrel 1335, documented 378), recorded in §5b.
- Provenance line check (§4c): 378 map entries checked against the pinned source, 0 stale lines.

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)
**Migration Section:** Section 4b verification skipped: evidence-report.md pins no `t2_future_count`. For a skill create-skill made, re-run create-skill to regenerate the report with the field (create-stack-skill does not write it).

### Structural Findings

| # | Type | Severity | Detail | Line |
|---|------|----------|--------|------|
| - | none | - | No structural issue: the description, usage and API-surface families are served by `## Overview`, `## Quick Start` and `## Key API Summary`; 10 code fences, all balanced and tagged; no table drift; no `scripts/` or `assets/` folder; every function and method export (330) is used in a usage-family section or reference file; no export the skill describes as async or sync is called against that claim | - |

**Structural Issues:** 0

### Reference Consistency (split-body)

| # | Reference File | Export | Issue | Other Side | Reference Line | Contradicted Side |
|---|---------------|--------|-------|------------|---------------|-------------------|
| - | - | - | No split-body mismatch | - | - | - |

**Exports Cross-Checked:** 147
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
**External Validators:** skill-check only (from `skill-check`)
**Analysis Confidence:** full
**Tooling Status:** ok

## Gap Report

**Total Gaps:** 105
**Blocking (Critical + High):** 0
**Non-blocking (Medium + Low + Info):** 105

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|------------------|
| Critical | 0 | None |
| High | 0 | None |
| Medium | 79 | stale-documentation (78): check each name against the source and the brief's scope, then update or remove its documentation or fix the scope (Update Skill does not repair it); metadata-drift (1): re-run Create Skill or edit the brief's scope, as each remediation says (counts that differ only by `Type::method` entries need no fix, and a hand edit of the counts does not hold) |
| Low | 0 | None |
| Info | 26 | observation (25): apply each only when you agree, as its remediation says, since it is advisory (a documented extra needs no change); multi-denominator (1): none, since the barrel and the documented surface measure different sets by design |
| **Total** | **105** | |

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

### GAP-007: Stale documentation: Badge

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:426
**Export:** Badge

**Issue:** `references/core-api.md:426` documents `Badge`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Badge/Badge.tsx:88` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Badge` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Badge/Badge.tsx:88`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Badge` at references/core-api.md:426.

### GAP-008: Stale documentation: Bar

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:431
**Export:** Bar

**Issue:** `references/core-api.md:431` documents `Bar`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Bar/Bar.tsx:52` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Bar` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Bar/Bar.tsx:52`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Bar` at references/core-api.md:431.

### GAP-009: Stale documentation: Blockquote

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:426
**Export:** Blockquote

**Issue:** `references/core-api.md:426` documents `Blockquote`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/Blockquote.tsx:6` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Blockquote` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/Blockquote.tsx:6`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Blockquote` at references/core-api.md:426.

### GAP-010: Stale documentation: BuiltQueryMethods

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:205
**Export:** BuiltQueryMethods

**Issue:** `references/core-api.md:205` documents `BuiltQueryMethods`, which the enumerated source API surface lacks

**Remediation:** Check `BuiltQueryMethods` against the source and update or remove its documentation at references/core-api.md:205: the enumerated source surface does not export it.

### GAP-011: Stale documentation: Button

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:427
**Export:** Button

**Issue:** `references/core-api.md:427` documents `Button`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Button/Button.tsx:53` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Button` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Button/Button.tsx:53`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Button` at references/core-api.md:427.

### GAP-012: Stale documentation: Card

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:428
**Export:** Card

**Issue:** `references/core-api.md:428` documents `Card`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Card/Card.tsx:98` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Card` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Card/Card.tsx:98`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Card` at references/core-api.md:428.

### GAP-013: Stale documentation: Channel

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:444
**Export:** Channel

**Issue:** `references/core-api.md:444` documents `Channel`, which the entry point `code/core/src/channels/index.ts` exports and `code/core/src/channels/main.ts:22` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Channel` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/channels/main.ts:22`, where it is defined, since its `scope.exclude` glob `code/core/src/channels/**` matches that file. To keep its documentation, narrow `code/core/src/channels/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Channel` at references/core-api.md:444.

### GAP-015: Stale documentation: Code

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:426
**Export:** Code

**Issue:** `references/core-api.md:426` documents `Code`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/Code.tsx:42` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Code` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/Code.tsx:42`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Code` at references/core-api.md:426.

### GAP-016: Stale documentation: Collapsible

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:428
**Export:** Collapsible

**Issue:** `references/core-api.md:428` documents `Collapsible`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Collapsible/Collapsible.tsx:31` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Collapsible` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Collapsible/Collapsible.tsx:31`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Collapsible` at references/core-api.md:428.

### GAP-018: Stale documentation: ConfigFile

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:451
**Export:** ConfigFile

**Issue:** `references/core-api.md:451` documents `ConfigFile`, which the entry point `code/core/src/csf-tools/index.ts` exports and `code/core/src/csf-tools/ConfigFile.ts:140` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `ConfigFile` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/csf-tools/ConfigFile.ts:140`, where it is defined, since its `scope.exclude` glob `code/core/src/csf-tools/**` matches that file. To keep its documentation, narrow `code/core/src/csf-tools/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `ConfigFile` at references/core-api.md:451.

### GAP-019: Stale documentation: CsfFile

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:451
**Export:** CsfFile

**Issue:** `references/core-api.md:451` documents `CsfFile`, which the entry point `code/core/src/csf-tools/index.ts` exports and `code/core/src/csf-tools/CsfFile.ts:280` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `CsfFile` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/csf-tools/CsfFile.ts:280`, where it is defined, since its `scope.exclude` glob `code/core/src/csf-tools/**` matches that file. To keep its documentation, narrow `code/core/src/csf-tools/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `CsfFile` at references/core-api.md:451.

### GAP-020: Stale documentation: DL

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:426
**Export:** DL

**Issue:** `references/core-api.md:426` documents `DL`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/DL.tsx:6` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `DL` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/DL.tsx:6`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `DL` at references/core-api.md:426.

### GAP-022: Stale documentation: Div

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:426
**Export:** Div

**Issue:** `references/core-api.md:426` documents `Div`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/Div.tsx:5` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Div` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/Div.tsx:5`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Div` at references/core-api.md:426.

### GAP-024: Stale documentation: ErrorFormatter

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:432
**Export:** ErrorFormatter

**Issue:** `references/core-api.md:432` documents `ErrorFormatter`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/ErrorFormatter/ErrorFormatter.tsx:29` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `ErrorFormatter` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/ErrorFormatter/ErrorFormatter.tsx:29`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `ErrorFormatter` at references/core-api.md:432.

### GAP-025: Stale documentation: EventType

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:208
**Export:** EventType

**Issue:** `references/core-api.md:208` documents `EventType`, which the entry point `code/core/src/telemetry/index.ts` exports and `code/core/src/telemetry/types.ts:9` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `EventType` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/telemetry/types.ts:9`, where it is defined, since its `scope.exclude` glob `code/core/src/telemetry/**` matches that file. To keep its documentation, narrow `code/core/src/telemetry/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `EventType` at references/core-api.md:208.

### GAP-027: Stale documentation: FlexBar

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:431
**Export:** FlexBar

**Issue:** `references/core-api.md:431` documents `FlexBar`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Bar/Bar.tsx:129` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `FlexBar` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Bar/Bar.tsx:129`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `FlexBar` at references/core-api.md:431.

### GAP-028: Stale documentation: Form

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:427
**Export:** Form

**Issue:** `references/core-api.md:427` documents `Form`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Form/Form.tsx:11` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Form` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Form/Form.tsx:11`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Form` at references/core-api.md:427.

### GAP-029: Stale documentation: H1

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:426
**Export:** H1

**Issue:** `references/core-api.md:426` documents `H1`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/H1.tsx:6` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `H1` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/H1.tsx:6`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `H1` at references/core-api.md:426.

### GAP-030: Stale documentation: H6

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:426
**Export:** H6

**Issue:** `references/core-api.md:426` documents `H6`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/H6.tsx:6` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `H6` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/H6.tsx:6`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `H6` at references/core-api.md:426.

### GAP-031: Stale documentation: HR

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:426
**Export:** HR

**Issue:** `references/core-api.md:426` documents `HR`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/HR.tsx:3` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `HR` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/HR.tsx:3`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `HR` at references/core-api.md:426.

### GAP-032: Stale documentation: IconButton

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:427
**Export:** IconButton

**Issue:** `references/core-api.md:427` documents `IconButton`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Button/Button.tsx:327` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `IconButton` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Button/Button.tsx:327`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `IconButton` at references/core-api.md:427.

### GAP-033: Stale documentation: LI

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:426
**Export:** LI

**Issue:** `references/core-api.md:426` documents `LI`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/LI.tsx:6` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `LI` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/LI.tsx:6`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `LI` at references/core-api.md:426.

### GAP-042: Stale documentation: Modal

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:428
**Export:** Modal

**Issue:** `references/core-api.md:428` documents `Modal`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Modal/Modal.tsx:242` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Modal` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Modal/Modal.tsx:242`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Modal` at references/core-api.md:428.

### GAP-043: Stale documentation: OL

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:426
**Export:** OL

**Issue:** `references/core-api.md:426` documents `OL`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/OL.tsx:16` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `OL` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/OL.tsx:16`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `OL` at references/core-api.md:426.

### GAP-044: Stale documentation: P

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:426
**Export:** P

**Issue:** `references/core-api.md:426` documents `P`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/P.tsx:6` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `P` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/P.tsx:6`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `P` at references/core-api.md:426.

### GAP-045: Stale documentation: Placeholder

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:432
**Export:** Placeholder

**Issue:** `references/core-api.md:432` documents `Placeholder`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/placeholder/placeholder.tsx:22` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Placeholder` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/placeholder/placeholder.tsx:22`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Placeholder` at references/core-api.md:432.

### GAP-046: Stale documentation: Popover

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:430
**Export:** Popover

**Issue:** `references/core-api.md:430` documents `Popover`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Popover/Popover.tsx:77` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Popover` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Popover/Popover.tsx:77`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Popover` at references/core-api.md:430.

### GAP-047: Stale documentation: PopoverProvider

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:430
**Export:** PopoverProvider

**Issue:** `references/core-api.md:430` documents `PopoverProvider`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Popover/PopoverProvider.tsx:63` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `PopoverProvider` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Popover/PopoverProvider.tsx:63`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `PopoverProvider` at references/core-api.md:430.

### GAP-048: Stale documentation: PostMessageTransport

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:444
**Export:** PostMessageTransport

**Issue:** `references/core-api.md:444` documents `PostMessageTransport`, which the entry point `code/core/src/channels/index.ts` exports and `code/core/src/channels/postmessage/index.ts:29` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `PostMessageTransport` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/channels/postmessage/index.ts:29`, where it is defined, since its `scope.exclude` glob `code/core/src/channels/**` matches that file. To keep its documentation, narrow `code/core/src/channels/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `PostMessageTransport` at references/core-api.md:444.

### GAP-049: Stale documentation: Pre

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:426
**Export:** Pre

**Issue:** `references/core-api.md:426` documents `Pre`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/Pre.tsx:6` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Pre` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/Pre.tsx:6`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Pre` at references/core-api.md:426.

### GAP-050: Stale documentation: PrettyDOMOptions

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:218
**Export:** PrettyDOMOptions

**Issue:** `references/core-api.md:218` documents `PrettyDOMOptions`, which the enumerated source API surface lacks

**Remediation:** Check `PrettyDOMOptions` against the source and update or remove its documentation at references/core-api.md:218: the enumerated source surface does not export it.

### GAP-054: Stale documentation: ScrollArea

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:428
**Export:** ScrollArea

**Issue:** `references/core-api.md:428` documents `ScrollArea`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/ScrollArea/ScrollArea.tsx:95` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `ScrollArea` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/ScrollArea/ScrollArea.tsx:95`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `ScrollArea` at references/core-api.md:428.

### GAP-055: Stale documentation: Select

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:427
**Export:** Select

**Issue:** `references/core-api.md:427` documents `Select`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Select/Select.tsx:201` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Select` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Select/Select.tsx:201`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Select` at references/core-api.md:427.

### GAP-057: Stale documentation: Spaced

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:432
**Export:** Spaced

**Issue:** `references/core-api.md:432` documents `Spaced`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/spaced/Spaced.tsx:63` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Spaced` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/spaced/Spaced.tsx:63`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Spaced` at references/core-api.md:432.

### GAP-058: Stale documentation: Span

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:426
**Export:** Span

**Issue:** `references/core-api.md:426` documents `Span`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/Span.tsx:6` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Span` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/Span.tsx:6`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Span` at references/core-api.md:426.

### GAP-059: Stale documentation: StoryIndexGenerator

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:454
**Export:** StoryIndexGenerator

**Issue:** `references/core-api.md:454` documents `StoryIndexGenerator`, which the entry point `code/core/src/core-server/index.ts` exports and `code/core/src/core-server/utils/StoryIndexGenerator.ts:101` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `StoryIndexGenerator` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/core-server/utils/StoryIndexGenerator.ts:101`, where it is defined, since its `scope.exclude` glob `code/core/src/core-server/**` matches that file. To keep its documentation, narrow `code/core/src/core-server/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `StoryIndexGenerator` at references/core-api.md:454.

### GAP-060: Stale documentation: StorybookIcon

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:433
**Export:** StorybookIcon

**Issue:** `references/core-api.md:433` documents `StorybookIcon`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/brand/StorybookIcon.tsx:3` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `StorybookIcon` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/brand/StorybookIcon.tsx:3`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `StorybookIcon` at references/core-api.md:433.

### GAP-061: Stale documentation: StorybookLogo

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:433
**Export:** StorybookLogo

**Issue:** `references/core-api.md:433` documents `StorybookLogo`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/brand/StorybookLogo.tsx:7` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `StorybookLogo` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/brand/StorybookLogo.tsx:7`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `StorybookLogo` at references/core-api.md:433.

### GAP-062: Stale documentation: SyntaxHighlighter

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:432
**Export:** SyntaxHighlighter

**Issue:** `references/core-api.md:432` documents `SyntaxHighlighter`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/syntaxhighlighter/lazy-syntaxhighlighter.tsx:52` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `SyntaxHighlighter` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/syntaxhighlighter/lazy-syntaxhighlighter.tsx:52`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `SyntaxHighlighter` at references/core-api.md:432.

### GAP-063: Stale documentation: TabBar

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:429
**Export:** TabBar

**Issue:** `references/core-api.md:429` documents `TabBar`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Tabs/Tabs.tsx:61` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `TabBar` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Tabs/Tabs.tsx:61`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `TabBar` at references/core-api.md:429.

### GAP-064: Stale documentation: TabButton

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:429
**Export:** TabButton

**Issue:** `references/core-api.md:429` documents `TabButton`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Tabs/Button.tsx:139` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `TabButton` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Tabs/Button.tsx:139`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `TabButton` at references/core-api.md:429.

### GAP-065: Stale documentation: TabList

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:429
**Export:** TabList

**Issue:** `references/core-api.md:429` documents `TabList`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Tabs/TabList.tsx:150` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `TabList` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Tabs/TabList.tsx:150`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `TabList` at references/core-api.md:429.

### GAP-066: Stale documentation: TabPanel

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:429
**Export:** TabPanel

**Issue:** `references/core-api.md:429` documents `TabPanel`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Tabs/TabPanel.tsx:34` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `TabPanel` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Tabs/TabPanel.tsx:34`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `TabPanel` at references/core-api.md:429.

### GAP-067: Stale documentation: TabWrapper

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:429
**Export:** TabWrapper

**Issue:** `references/core-api.md:429` documents `TabWrapper`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Tabs/Tabs.tsx:120` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `TabWrapper` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Tabs/Tabs.tsx:120`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `TabWrapper` at references/core-api.md:429.

### GAP-068: Stale documentation: Table

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:426
**Export:** Table

**Issue:** `references/core-api.md:426` documents `Table`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/Table.tsx:6` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Table` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/Table.tsx:6`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Table` at references/core-api.md:426.

### GAP-069: Stale documentation: Tabs

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:429
**Export:** Tabs

**Issue:** `references/core-api.md:429` documents `Tabs`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Tabs/Tabs.tsx:188` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Tabs` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Tabs/Tabs.tsx:188`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Tabs` at references/core-api.md:429.

### GAP-070: Stale documentation: TabsView

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:429
**Export:** TabsView

**Issue:** `references/core-api.md:429` documents `TabsView`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Tabs/TabsView.tsx:106` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `TabsView` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Tabs/TabsView.tsx:106`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `TabsView` at references/core-api.md:429.

### GAP-073: Stale documentation: ToggleButton

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:427
**Export:** ToggleButton

**Issue:** `references/core-api.md:427` documents `ToggleButton`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/ToggleButton/ToggleButton.tsx:16` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `ToggleButton` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/ToggleButton/ToggleButton.tsx:16`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `ToggleButton` at references/core-api.md:427.

### GAP-074: Stale documentation: Toolbar

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:431
**Export:** Toolbar

**Issue:** `references/core-api.md:431` documents `Toolbar`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Toolbar/Toolbar.tsx:36` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Toolbar` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Toolbar/Toolbar.tsx:36`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Toolbar` at references/core-api.md:431.

### GAP-075: Stale documentation: Tooltip

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:430
**Export:** Tooltip

**Issue:** `references/core-api.md:430` documents `Tooltip`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/tooltip/Tooltip.tsx:7` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Tooltip` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/tooltip/Tooltip.tsx:7`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Tooltip` at references/core-api.md:430.

### GAP-076: Stale documentation: TooltipLinkList

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:430
**Export:** TooltipLinkList

**Issue:** `references/core-api.md:430` documents `TooltipLinkList`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/tooltip/TooltipLinkList.tsx:70` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `TooltipLinkList` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/tooltip/TooltipLinkList.tsx:70`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `TooltipLinkList` at references/core-api.md:430.

### GAP-077: Stale documentation: TooltipNote

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:430
**Export:** TooltipNote

**Issue:** `references/core-api.md:430` documents `TooltipNote`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/tooltip/TooltipNote.tsx:23` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `TooltipNote` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/tooltip/TooltipNote.tsx:23`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `TooltipNote` at references/core-api.md:430.

### GAP-078: Stale documentation: UL

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:426
**Export:** UL

**Issue:** `references/core-api.md:426` documents `UL`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/UL.tsx:16` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `UL` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/UL.tsx:16`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `UL` at references/core-api.md:426.

### GAP-080: Stale documentation: WebsocketTransport

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:444
**Export:** WebsocketTransport

**Issue:** `references/core-api.md:444` documents `WebsocketTransport`, which the entry point `code/core/src/channels/index.ts` exports and `code/core/src/channels/websocket/index.ts:23` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `WebsocketTransport` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/channels/websocket/index.ts:23`, where it is defined, since its `scope.exclude` glob `code/core/src/channels/**` matches that file. To keep its documentation, narrow `code/core/src/channels/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `WebsocketTransport` at references/core-api.md:444.

### GAP-081: Stale documentation: WithTooltip

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:430
**Export:** WithTooltip

**Issue:** `references/core-api.md:430` documents `WithTooltip`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/tooltip/lazy-WithTooltip.tsx:8` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `WithTooltip` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/tooltip/lazy-WithTooltip.tsx:8`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `WithTooltip` at references/core-api.md:430.

### GAP-082: Stale documentation: Zoom

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:432
**Export:** Zoom

**Issue:** `references/core-api.md:432` documents `Zoom`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Zoom/Zoom.tsx:4` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Zoom` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Zoom/Zoom.tsx:4`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Zoom` at references/core-api.md:432.

### GAP-083: Stale documentation: addToGlobalContext

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:450
**Export:** addToGlobalContext

**Issue:** `references/core-api.md:450` documents `addToGlobalContext`, which the entry point `code/core/src/telemetry/index.ts` exports and `code/core/src/telemetry/telemetry.ts:26` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `addToGlobalContext` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/telemetry/telemetry.ts:26`, where it is defined, since its `scope.exclude` glob `code/core/src/telemetry/**` matches that file. To keep its documentation, narrow `code/core/src/telemetry/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `addToGlobalContext` at references/core-api.md:450.

### GAP-084: Stale documentation: colors

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:449
**Export:** colors

**Issue:** `references/core-api.md:449` documents `colors`, which the entry point `code/core/src/node-logger/index.ts` exports and `code/core/src/node-logger/index.ts:57` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `colors` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/node-logger/index.ts:57`, where it is defined, since its `scope.exclude` glob `code/core/src/node-logger/**` matches that file. To keep its documentation, narrow `code/core/src/node-logger/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `colors` at references/core-api.md:449.

### GAP-085: Stale documentation: componentTransform

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:451
**Export:** componentTransform

**Issue:** `references/core-api.md:451` documents `componentTransform`, which the entry point `code/core/src/csf-tools/index.ts` exports and `code/core/src/csf-tools/vitest-plugin/component-transformer.ts:285` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `componentTransform` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/csf-tools/vitest-plugin/component-transformer.ts:285`, where it is defined, since its `scope.exclude` glob `code/core/src/csf-tools/**` matches that file. To keep its documentation, narrow `code/core/src/csf-tools/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `componentTransform` at references/core-api.md:451.

### GAP-086: Stale documentation: createBrowserChannel

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:444
**Export:** createBrowserChannel

**Issue:** `references/core-api.md:444` documents `createBrowserChannel`, which the entry point `code/core/src/channels/index.ts` exports and `code/core/src/channels/index.ts:32` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `createBrowserChannel` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/channels/index.ts:32`, where it is defined, since its `scope.exclude` glob `code/core/src/channels/**` matches that file. To keep its documentation, narrow `code/core/src/channels/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `createBrowserChannel` at references/core-api.md:444.

### GAP-087: Stale documentation: enrichCsf

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:451
**Export:** enrichCsf

**Issue:** `references/core-api.md:451` documents `enrichCsf`, which the entry point `code/core/src/csf-tools/index.ts` exports and `code/core/src/csf-tools/enrichCsf.ts:144` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `enrichCsf` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/csf-tools/enrichCsf.ts:144`, where it is defined, since its `scope.exclude` glob `code/core/src/csf-tools/**` matches that file. To keep its documentation, narrow `code/core/src/csf-tools/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `enrichCsf` at references/core-api.md:451.

### GAP-088: Stale documentation: experimental_loadStorybook

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:454
**Export:** experimental_loadStorybook

**Issue:** `references/core-api.md:454` documents `experimental_loadStorybook`, which the entry point `code/core/src/core-server/index.ts` exports and `code/core/src/core-server/load.ts:18` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `experimental_loadStorybook` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/core-server/load.ts:18`, where it is defined, since its `scope.exclude` glob `code/core/src/core-server/**` matches that file. To keep its documentation, narrow `code/core/src/core-server/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `experimental_loadStorybook` at references/core-api.md:454.

### GAP-089: Stale documentation: generate

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:456
**Export:** generate

**Issue:** `references/core-api.md:456` documents `generate`, which the entry point `code/core/src/babel/index.ts` exports and `code/core/src/babel/index.ts:38` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `generate` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/babel/index.ts:38`, where it is defined, since its `scope.exclude` glob `code/core/src/babel/**` matches that file. To keep its documentation, narrow `code/core/src/babel/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `generate` at references/core-api.md:456.

### GAP-090: Stale documentation: generateStoryFile

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:454
**Export:** generateStoryFile

**Issue:** `references/core-api.md:454` documents `generateStoryFile`, which the entry point `code/core/src/core-server/index.ts` exports and `code/core/src/core-server/utils/generate-story.ts:64` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `generateStoryFile` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/core-server/utils/generate-story.ts:64`, where it is defined, since its `scope.exclude` glob `code/core/src/core-server/**` matches that file. To keep its documentation, narrow `code/core/src/core-server/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `generateStoryFile` at references/core-api.md:454.

### GAP-091: Stale documentation: getSessionId

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:450
**Export:** getSessionId

**Issue:** `references/core-api.md:450` documents `getSessionId`, which the entry point `code/core/src/telemetry/index.ts` exports and `code/core/src/telemetry/session-id.ts:18` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `getSessionId` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/telemetry/session-id.ts:18`, where it is defined, since its `scope.exclude` glob `code/core/src/telemetry/**` matches that file. To keep its documentation, narrow `code/core/src/telemetry/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `getSessionId` at references/core-api.md:450.

### GAP-092: Stale documentation: getStoryHref

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:432
**Export:** getStoryHref

**Issue:** `references/core-api.md:432` documents `getStoryHref`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/utils/getStoryHref.ts:15` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `getStoryHref` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/utils/getStoryHref.ts:15`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `getStoryHref` at references/core-api.md:432.

### GAP-093: Stale documentation: getStorySortParameter

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:451
**Export:** getStorySortParameter

**Issue:** `references/core-api.md:451` documents `getStorySortParameter`, which the entry point `code/core/src/csf-tools/index.ts` exports and `code/core/src/csf-tools/getStorySortParameter.ts:96` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `getStorySortParameter` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/csf-tools/getStorySortParameter.ts:96`, where it is defined, since its `scope.exclude` glob `code/core/src/csf-tools/**` matches that file. To keep its documentation, narrow `code/core/src/csf-tools/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `getStorySortParameter` at references/core-api.md:451.

### GAP-094: Stale documentation: getStorybookMetadata

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:450
**Export:** getStorybookMetadata

**Issue:** `references/core-api.md:450` documents `getStorybookMetadata`, which the entry point `code/core/src/telemetry/index.ts` exports and `code/core/src/telemetry/storybook-metadata.ts:312` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `getStorybookMetadata` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/telemetry/storybook-metadata.ts:312`, where it is defined, since its `scope.exclude` glob `code/core/src/telemetry/**` matches that file. To keep its documentation, narrow `code/core/src/telemetry/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `getStorybookMetadata` at references/core-api.md:450.

### GAP-096: Stale documentation: logTracker

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:449
**Export:** logTracker

**Issue:** `references/core-api.md:449` documents `logTracker`, which the entry point `code/core/src/node-logger/index.ts` exports and `code/core/src/node-logger/logger/log-tracker.ts:95` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `logTracker` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/node-logger/logger/log-tracker.ts:95`, where it is defined, since its `scope.exclude` glob `code/core/src/node-logger/**` matches that file. To keep its documentation, narrow `code/core/src/node-logger/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `logTracker` at references/core-api.md:449.

### GAP-097: Stale documentation: prompt

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:449
**Export:** prompt

**Issue:** `references/core-api.md:449` documents `prompt`, which the entry point `code/core/src/node-logger/index.ts` exports and `code/core/src/node-logger/prompts/index.ts:5` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `prompt` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/node-logger/prompts/index.ts:5`, where it is defined, since its `scope.exclude` glob `code/core/src/node-logger/**` matches that file. To keep its documentation, narrow `code/core/src/node-logger/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `prompt` at references/core-api.md:449.

### GAP-098: Stale documentation: telemetry

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:450
**Export:** telemetry

**Issue:** `references/core-api.md:450` documents `telemetry`, which the entry point `code/core/src/telemetry/index.ts` exports and `code/core/src/telemetry/index.ts:31` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `telemetry` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/telemetry/index.ts:31`, where it is defined, since its `scope.exclude` glob `code/core/src/telemetry/**` matches that file. To keep its documentation, narrow `code/core/src/telemetry/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `telemetry` at references/core-api.md:450.

### GAP-099: Stale documentation: traverse

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:456
**Export:** traverse

**Issue:** `references/core-api.md:456` documents `traverse`, which the entry point `code/core/src/babel/index.ts` exports and `code/core/src/babel/index.ts:39` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `traverse` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/babel/index.ts:39`, where it is defined, since its `scope.exclude` glob `code/core/src/babel/**` matches that file. To keep its documentation, narrow `code/core/src/babel/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `traverse` at references/core-api.md:456.

### GAP-101: Stale documentation: useTabsState

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:429
**Export:** useTabsState

**Issue:** `references/core-api.md:429` documents `useTabsState`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Tabs/TabsView.tsx:30` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `useTabsState` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Tabs/TabsView.tsx:30`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `useTabsState` at references/core-api.md:429.

### GAP-102: Stale documentation: vitestTransform

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:451
**Export:** vitestTransform

**Issue:** `references/core-api.md:451` documents `vitestTransform`, which the entry point `code/core/src/csf-tools/index.ts` exports and `code/core/src/csf-tools/vitest-plugin/transformer.ts:108` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `vitestTransform` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/csf-tools/vitest-plugin/transformer.ts:108`, where it is defined, since its `scope.exclude` glob `code/core/src/csf-tools/**` matches that file. To keep its documentation, narrow `code/core/src/csf-tools/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `vitestTransform` at references/core-api.md:451.

### GAP-104: metadata drift — barrel export counts diverge

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

**Issue:** the skill labels its documented form of `Story` partial, and it leaves out only members the source marks optional: documented `{ of?, meta?, inline?, height?, autoplay? }`, source `ComponentType<StoryProps>, props { of?: ModuleExport; meta?: ModuleExports; inline?: boolean; height?: string; autoplay?: boolean; __forceInitialArgs?: boolean; __primary?: boolean }`: the props list marks optionality with '?' (so it is not a list of bare names) and leaves out the optional own props '__forceInitialArgs' and '__primary' that StoryParameters declares in this file

**Remediation:** No change: the documented form of `Story` is labelled partial and leaves out only optional members of the signature the source defines at `code/addons/docs/src/blocks/blocks/Story.tsx:134`.

### GAP-006: Documented extra: ArgsTable

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/docs/src/blocks/components/ArgsTable/ArgsTable.tsx:320
**Export:** ArgsTable

**Issue:** `references/doc-blocks.md:142` documents `ArgsTable`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ArgsTable` is a documented extra, a name the source still declares at `code/addons/docs/src/blocks/components/ArgsTable/ArgsTable.tsx:320` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-014: Documented extra: CheckboxControl

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/docs/src/blocks/controls/options/Checkbox.tsx:57
**Export:** CheckboxControl

**Issue:** `references/doc-blocks.md:291` documents `CheckboxControl`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CheckboxControl` is a documented extra, a name the source still declares at `code/addons/docs/src/blocks/controls/options/Checkbox.tsx:57` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-017: Documented extra: ColorControlProps

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/docs/src/blocks/controls/Color.tsx:360
**Export:** ColorControlProps

**Issue:** `references/doc-blocks.md:270` documents `ColorControlProps`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ColorControlProps` is a documented extra, a name the source still declares at `code/addons/docs/src/blocks/controls/Color.tsx:360` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-021: Documented extra: DecoratorHelpers

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/themes/src/decorators/index.ts:5
**Export:** DecoratorHelpers

**Issue:** `references/addons.md:121` documents `DecoratorHelpers`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `DecoratorHelpers` is a documented extra, a name the source still declares at `code/addons/themes/src/decorators/index.ts:5` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-023: Documented extra: DocsParameters

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/docs/src/types.ts:151
**Export:** DocsParameters

**Issue:** `references/addons.md:252` documents `DocsParameters`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `DocsParameters` is a documented extra, a name the source still declares at `code/addons/docs/src/types.ts:151` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-026: Documented extra: ExternalPreview

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/docs/src/blocks/blocks/external/ExternalPreview.ts:30
**Export:** ExternalPreview

**Issue:** `references/doc-blocks.md:193` documents `ExternalPreview`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ExternalPreview` is a documented extra, a name the source still declares at `code/addons/docs/src/blocks/blocks/external/ExternalPreview.ts:30` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-034: Documented extra: ManagerConsumer

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager-api/root.tsx:266
**Export:** ManagerConsumer

**Issue:** `references/story-types.md:263` documents `ManagerConsumer`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ManagerConsumer` is a documented extra, a name the source still declares at `code/core/src/manager-api/root.tsx:266` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-035: Not checked by script: MaybeMocked (another package's export *)

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/core-api.md:66
**Export:** MaybeMocked

**Issue:** `references/core-api.md:66` documents `MaybeMocked`, which the enumerated source API surface lacks; a file the skill cites passes on another package's names through `export type * from '@vitest/spy';` (`code/core/src/test/spy.ts:15`), which no script resolves

**Remediation:** No change unless the other package does not export `MaybeMocked`: a file the skill cites passes on that package's names through `export type * from '@vitest/spy';` (`code/core/src/test/spy.ts:15`), and no script reads them, so check by hand that the package exports `MaybeMocked`.

### GAP-036: Not checked by script: MaybeMockedDeep (another package's export *)

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/core-api.md:67
**Export:** MaybeMockedDeep

**Issue:** `references/core-api.md:67` documents `MaybeMockedDeep`, which the enumerated source API surface lacks; a file the skill cites passes on another package's names through `export type * from '@vitest/spy';` (`code/core/src/test/spy.ts:15`), which no script resolves

**Remediation:** No change unless the other package does not export `MaybeMockedDeep`: a file the skill cites passes on that package's names through `export type * from '@vitest/spy';` (`code/core/src/test/spy.ts:15`), and no script reads them, so check by hand that the package exports `MaybeMockedDeep`.

### GAP-037: Not checked by script: MaybePartiallyMocked (another package's export *)

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/core-api.md:68
**Export:** MaybePartiallyMocked

**Issue:** `references/core-api.md:68` documents `MaybePartiallyMocked`, which the enumerated source API surface lacks; a file the skill cites passes on another package's names through `export type * from '@vitest/spy';` (`code/core/src/test/spy.ts:15`), which no script resolves

**Remediation:** No change unless the other package does not export `MaybePartiallyMocked`: a file the skill cites passes on that package's names through `export type * from '@vitest/spy';` (`code/core/src/test/spy.ts:15`), and no script reads them, so check by hand that the package exports `MaybePartiallyMocked`.

### GAP-038: Not checked by script: MaybePartiallyMockedDeep (another package's export *)

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/core-api.md:69
**Export:** MaybePartiallyMockedDeep

**Issue:** `references/core-api.md:69` documents `MaybePartiallyMockedDeep`, which the enumerated source API surface lacks; a file the skill cites passes on another package's names through `export type * from '@vitest/spy';` (`code/core/src/test/spy.ts:15`), which no script resolves

**Remediation:** No change unless the other package does not export `MaybePartiallyMockedDeep`: a file the skill cites passes on that package's names through `export type * from '@vitest/spy';` (`code/core/src/test/spy.ts:15`), and no script reads them, so check by hand that the package exports `MaybePartiallyMockedDeep`.

### GAP-039: Documented extra: Method

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/frameworks/angular/src/client/compodoc-types.ts:1
**Export:** Method

**Issue:** `references/core-api.md:214` documents `Method`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Method` is a documented extra, a name the source still declares at `code/frameworks/angular/src/client/compodoc-types.ts:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-040: Not checked by script: Mock (another package's export *)

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/core-api.md:64
**Export:** Mock

**Issue:** `references/core-api.md:64` documents `Mock`, which the enumerated source API surface lacks; a file the skill cites passes on another package's names through `export type * from '@vitest/spy';` (`code/core/src/test/spy.ts:15`), which no script resolves

**Remediation:** No change unless the other package does not export `Mock`: a file the skill cites passes on that package's names through `export type * from '@vitest/spy';` (`code/core/src/test/spy.ts:15`), and no script reads them, so check by hand that the package exports `Mock`.

### GAP-041: Not checked by script: MockInstance (another package's export *)

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/core-api.md:65
**Export:** MockInstance

**Issue:** `references/core-api.md:65` documents `MockInstance`, which the enumerated source API surface lacks; a file the skill cites passes on another package's names through `export type * from '@vitest/spy';` (`code/core/src/test/spy.ts:15`), which no script resolves

**Remediation:** No change unless the other package does not export `MockInstance`: a file the skill cites passes on that package's names through `export type * from '@vitest/spy';` (`code/core/src/test/spy.ts:15`), and no script reads them, so check by hand that the package exports `MockInstance`.

### GAP-051: Documented extra: PureSourceProps

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/docs/src/blocks/blocks/Source.tsx:99
**Export:** PureSourceProps

**Issue:** `references/doc-blocks.md:179` documents `PureSourceProps`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PureSourceProps` is a documented extra, a name the source still declares at `code/addons/docs/src/blocks/blocks/Source.tsx:99` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-052: Documented extra: PureStoryProps

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/docs/src/blocks/blocks/Story.tsx:18
**Export:** PureStoryProps

**Issue:** `references/doc-blocks.md:186` documents `PureStoryProps`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PureStoryProps` is a documented extra, a name the source still declares at `code/addons/docs/src/blocks/blocks/Story.tsx:18` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-053: Documented extra: RadioControl

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/docs/src/blocks/controls/options/Radio.tsx:57
**Export:** RadioControl

**Issue:** `references/doc-blocks.md:292` documents `RadioControl`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `RadioControl` is a documented extra, a name the source still declares at `code/addons/docs/src/blocks/controls/options/Radio.tsx:57` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-056: Documented extra: SelectControl

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/docs/src/blocks/controls/options/Select.tsx:170
**Export:** SelectControl

**Issue:** `references/doc-blocks.md:293` documents `SelectControl`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `SelectControl` is a documented extra, a name the source still declares at `code/addons/docs/src/blocks/controls/options/Select.tsx:170` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-071: Documented extra: ThemeAddonState

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/themes/src/types.ts:1
**Export:** ThemeAddonState

**Issue:** `references/addons.md:114` documents `ThemeAddonState`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ThemeAddonState` is a documented extra, a name the source still declares at `code/addons/themes/src/types.ts:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-072: Documented extra: ThemesParameters

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/themes/src/types.ts:6
**Export:** ThemesParameters

**Issue:** `references/addons.md:115` documents `ThemesParameters`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ThemesParameters` is a documented extra, a name the source still declares at `code/addons/themes/src/types.ts:6` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-079: Documented extra: Variant

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/renderers/react/src/componentManifest/__testfixtures__/types.ts:8
**Export:** Variant

**Issue:** `references/core-api.md:214` documents `Variant`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Variant` is a documented extra, a name the source still declares at `code/renderers/react/src/componentManifest/__testfixtures__/types.ts:8` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-095: Documented extra: inferArgTypes

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/preview-api/modules/store/inferArgTypes.ts:67
**Export:** inferArgTypes

**Issue:** `references/core-api.md:126` documents `inferArgTypes`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `inferArgTypes` is a documented extra, a name the source still declares at `code/core/src/preview-api/modules/store/inferArgTypes.ts:67` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-100: Documented extra: usePrimaryStory

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/docs/src/blocks/blocks/usePrimaryStory.ts:12
**Export:** usePrimaryStory

**Issue:** `references/doc-blocks.md:33` documents `usePrimaryStory`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `usePrimaryStory` is a documented extra, a name the source still declares at `code/addons/docs/src/blocks/blocks/usePrimaryStory.ts:12` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-103: Documented extra: withMdxComponentOverride

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/docs/src/blocks/blocks/with-mdx-component-override.tsx:14
**Export:** withMdxComponentOverride

**Issue:** `references/doc-blocks.md:162` documents `withMdxComponentOverride`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `withMdxComponentOverride` is a documented extra, a name the source still declares at `code/addons/docs/src/blocks/blocks/with-mdx-component-override.tsx:14` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-105: multi-denominator reporting — barrel vs documented surface

**Severity:** Info
**Category:** Coverage (multi-denominator)
**Source:** skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/metadata.json

**Issue:** barrel=1335, documented=378

**Remediation:** No action required: the barrel and the documented surface measure different sets by design, and the report records both counts.

### Discovery Quality

**Discovery Test:** PASS (3/3)

| # | Prompt | Selected Skill | Result |
|---|--------|----------------|--------|
| 1 | the interaction check on our submit control's sandbox page passes even though the click handler never fires — can you make it actually assert the callback got called? | oms-storybook-react-vite (high) | PASS |
| 2 | can you help me with this component-explorer file my lead sent? it still uses the old default-export array style and its imports point at the split-up scoped packages instead of the single core one | oms-storybook-react-vite (high) | PASS |
| 3 | set up the dark/light switcher thing for our component workshop so every example in it renders under both color schemes from a picker at the top | oms-storybook-react-vite (high) | PASS |

Catalog: 4 skills (`oms-cocoindex`, `oms-cognee`, `oms-storybook-react-vite`, `oms-uitripled`). SKILL.md has no Triggers section and its description gives no organic prompt, so the three prompts were synthesized from its capability summary (implicit, vague and abbreviated patterns), naming no export, skill or library. Each went to an isolated subagent (Claude Code's `web-fetch` agent type, the available type with no file or shell tools) given only the catalog and the prompt; each answered with no tool call.
