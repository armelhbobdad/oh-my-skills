---
workflowType: 'test-skill'
skillName: 'oms-storybook-react-vite'
skillDir: 'skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite'
runId: '20261106T213301Z-9956fcf3'
testMode: 'naive'
forgeTier: 'Deep'
hardGate: 'blocked'
testResult: 'fail'
score: ''
threshold: '80%'
thresholdSource: 'workflow default (80%)'
analysisConfidence: 'full'
toolingStatus: 'ok'
workspaceDrift: 'ok'
health_check_dispatched: true
testDate: '2026-11-06T21:33:01Z'
stepsCompleted: ['init', 'detect-mode', 'coverage-check', 'coherence-check', 'external-validators', 'hard-gate', 'report']
nextWorkflow: 'update-skill'
---

# Test Report: oms-storybook-react-vite

<!--
Each stage writes its section in place of the heading below that it owns and
the placeholder comment under that heading, so every heading occurs once.
Before the result files are written, report.md §4c checks that each heading
occurs exactly once and that no placeholder comment is left: a stage that
skipped its section stops the run there. Do not reorder or delete the
headings or their placeholder comments.

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

**Mode Rationale:** metadata.json records `skill_type: single`, an individual skill, so the run uses naive mode: API-surface coverage, with a structural-only coherence check that is not scored.

**Analysis Plan:**
- Coverage Check: every tier A public export of the pinned source (storybookjs/storybook at e486d38, v10.3.5) is checked for documentation in SKILL.md and references/, with AST-backed signature and type comparison at Deep tier.
- Coherence Check: structural only (references resolve, sections present); no coherence category in scoring.

## Coverage Analysis

**Tier:** Deep
**Source Access:** full
**Source Path:** /home/armel/.skf/workspace/repos/github.com/storybookjs/storybook
**Workspace Layout:** npm-workspaces
**Denominator:** Stratified scope, denominator: effective_denominator (124 files define its names, 376 exports union)

**Denominator Candidates** (stratified-scope audit trail):
- `stats.effective_denominator`: 370  ← chosen on the scalar branch
- `scope.tier_a_include` union: 376
- `scope.include` union: 1171
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
| `AnchorProps` | interface | no | - | code/addons/docs/src/blocks/blocks/Anchor.tsx:6 | WARN |
| `Animation` | type | yes | - | code/core/src/theming/types.ts:60 | PASS |
| `ArgTypes` | const | yes | no | code/core/src/csf/story.ts:162 | FAIL |
| `Background` | type | yes | - | code/core/src/theming/types.ts:58 | PASS |
| `Badge` | - | yes | - | - | WARN |
| `Bar` | - | yes | - | - | WARN |
| `Blockquote` | - | yes | - | - | WARN |
| `BooleanConfig` | interface | yes | - | code/addons/docs/src/blocks/controls/types.ts:14 | PASS |
| `BooleanControl` | function | yes | yes | code/addons/docs/src/blocks/controls/Boolean.tsx:117 | PASS |
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
| `DateControl` | function | yes | yes | code/addons/docs/src/blocks/controls/Date.tsx:69 | PASS |
| `DateProps` | type | yes | - | code/addons/docs/src/blocks/controls/Date.tsx:68 | PASS |
| `DateValue` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:28 | PASS |
| `Decorator` | type | yes | - | code/renderers/react/src/public-types.ts:77 | PASS |
| `DecoratorFunction` | type | yes | yes (Low) | code/core/src/csf/story.ts:331 | WARN |
| `DecoratorHelpers` | - | yes | - | - | WARN |
| `Description` | const | yes | yes | code/addons/docs/src/blocks/blocks/Description.tsx:74 | PASS |
| `DescriptionType` | enum | yes | - | code/addons/docs/src/blocks/blocks/Description.tsx:9 | PASS |
| `Div` | - | yes | - | - | WARN |
| `Docs` | function | yes | yes | code/addons/docs/src/blocks/blocks/Docs.tsx:17 | PASS |
| `DocsContainer` | function | yes | yes | code/addons/docs/src/blocks/blocks/DocsContainer.tsx:23 | PASS |
| `DocsContainerProps` | interface | no | - | code/addons/docs/src/blocks/blocks/DocsContainer.tsx:18 | WARN |
| `DocsContext` | const | yes | - | code/addons/docs/src/blocks/blocks/DocsContext.ts:18 | PASS |
| `DocsPage` | function | yes | - | code/addons/docs/src/blocks/blocks/DocsPage.tsx:12 | PASS |
| `DocsProps` | type | no | - | code/addons/docs/src/blocks/blocks/Docs.tsx:12 | WARN |
| `DocsRenderer` | class | yes | - | code/addons/docs/src/DocsRenderer.tsx:48 | PASS |
| `DocsStory` | const | yes | yes | code/addons/docs/src/blocks/blocks/DocsStory.tsx:42 | PASS |
| `DocsStoryProps` | type | no | - | code/addons/docs/src/blocks/blocks/types.ts:9 | WARN |
| `DocsTypes` | interface | yes | - | code/addons/docs/src/types.ts:254 | PASS |
| `EVENT_ID` | const | yes | - | code/core/src/actions/constants.ts:4 | PASS |
| `Easing` | type | yes | - | code/core/src/theming/types.ts:61 | PASS |
| `ErrorFormatter` | - | yes | - | - | WARN |
| `ExternalDocs` | function | yes | yes | code/addons/docs/src/blocks/blocks/external/ExternalDocs.tsx:26 | PASS |
| `ExternalDocsContainer` | function | yes | yes | code/addons/docs/src/blocks/blocks/external/ExternalDocsContainer.tsx:12 | PASS |
| `ExternalDocsProps` | type | yes | - | code/addons/docs/src/blocks/blocks/external/ExternalDocs.tsx:11 | PASS |
| `FilesControl` | function | yes | yes | code/addons/docs/src/blocks/controls/Files.tsx:40 | PASS |
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
| `HeadingProps` | interface | no | - | code/addons/docs/src/blocks/blocks/Heading.tsx:11 | WARN |
| `HighlightMenuItem` | interface | yes | - | code/core/src/highlight/types.ts:24 | PASS |
| `HighlightOptions` | interface | yes | - | code/core/src/highlight/types.ts:41 | PASS |
| `HighlightParameters` | - | yes | - | - | WARN |
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
| `Markdown` | const | yes | yes | code/addons/docs/src/blocks/blocks/Markdown.tsx:55 | PASS |
| `MaybeMocked` | - | yes | - | code/core/src/test/spy.ts | PASS |
| `MaybeMockedDeep` | - | no | - | code/core/src/test/spy.ts | WARN |
| `MaybePartiallyMocked` | - | no | - | code/core/src/test/spy.ts | WARN |
| `MaybePartiallyMockedDeep` | - | no | - | code/core/src/test/spy.ts | WARN |
| `Meta` | function | yes | yes | code/addons/docs/src/blocks/blocks/Meta.tsx:15 | PASS |
| `Mock` | - | yes | - | code/core/src/test/spy.ts | PASS |
| `MockInstance` | - | yes | - | code/core/src/test/spy.ts | PASS |
| `Modal` | - | yes | - | - | WARN |
| `NormalizedOptionsConfig` | interface | yes | - | code/addons/docs/src/blocks/controls/types.ts:62 | PASS |
| `NumberConfig` | interface | yes | - | code/addons/docs/src/blocks/controls/types.ts:32 | PASS |
| `NumberControl` | function | yes | yes | code/addons/docs/src/blocks/controls/Number.tsx:28 | PASS |
| `NumberValue` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:31 | PASS |
| `OL` | - | yes | - | - | WARN |
| `ObjectConfig` | interface | yes | - | code/addons/docs/src/blocks/controls/types.ts:41 | PASS |
| `ObjectControl` | function | yes | yes | code/addons/docs/src/blocks/controls/Object.tsx:166 | PASS |
| `ObjectProps` | type | yes | - | code/addons/docs/src/blocks/controls/Object.tsx:164 | PASS |
| `ObjectValue` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:40 | PASS |
| `Of` | type | yes | - | code/addons/docs/src/blocks/blocks/useOf.ts:11 | PASS |
| `Options` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:48 | PASS |
| `OptionsArray` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:46 | PASS |
| `OptionsConfig` | interface | yes | - | code/addons/docs/src/blocks/controls/types.ts:57 | PASS |
| `OptionsControl` | function | yes | yes | code/addons/docs/src/blocks/controls/options/Options.tsx:41 | PASS |
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
| `PropDescriptor` | type | no | - | code/core/src/preview-api/modules/store/filterArgTypes.ts:5 | WARN |
| `ProviderStrategyConfiguration` | interface | yes | - | code/addons/themes/src/decorators/provider.decorator.tsx:13 | PASS |
| `PureArgsTable` | function | yes | yes | code/addons/docs/src/blocks/components/ArgsTable/ArgsTable.tsx:320 | PASS |
| `REMOVE_HIGHLIGHT` | const | yes | - | code/core/src/highlight/constants.ts:4 | PASS |
| `RESET_HIGHLIGHT` | const | yes | - | code/core/src/highlight/constants.ts:5 | PASS |
| `RadioControl` | - | yes | - | - | WARN |
| `RangeConfig` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:38 | PASS |
| `RangeControl` | function | yes | yes | code/addons/docs/src/blocks/controls/Range.tsx:178 | PASS |
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
| `Selection` | - | yes | - | - | WARN |
| `SelectionSpecifier` | - | yes | - | - | WARN |
| `SelectionStore` | interface | yes | - | code/core/src/preview-api/modules/preview-web/SelectionStore.ts:17 | PASS |
| `SelectorWithoutNode` | type | yes | - | code/addons/a11y/src/params.ts:3 | PASS |
| `SortType` | type | yes | - | code/addons/docs/src/blocks/components/ArgsTable/ArgsTable.tsx:186 | PASS |
| `Source` | const | yes | yes | code/addons/docs/src/blocks/blocks/Source.tsx:181 | PASS |
| `SourceContainer` | function | yes | yes | code/addons/docs/src/blocks/blocks/SourceContainer.tsx:38 | PASS |
| `SourceContext` | const | yes | - | code/addons/docs/src/blocks/blocks/SourceContainer.tsx:27 | PASS |
| `SourceContextProps` | interface | yes | - | code/addons/docs/src/blocks/blocks/SourceContainer.tsx:22 | PASS |
| `SourceItem` | interface | yes | - | code/addons/docs/src/blocks/blocks/SourceContainer.tsx:15 | PASS |
| `SourceParameters` | type | no | - | code/addons/docs/src/blocks/blocks/Source.tsx:16 | WARN |
| `SourceProps` | type | no | - | code/addons/docs/src/blocks/blocks/Source.tsx:28 | WARN |
| `Spaced` | - | yes | - | - | WARN |
| `Span` | - | yes | - | - | WARN |
| `Stories` | const | yes | yes | code/addons/docs/src/blocks/blocks/Stories.tsx:74 | PASS |
| `Story` | const | yes | yes (Info) | code/addons/docs/src/blocks/blocks/Story.tsx:134 | WARN |
| `StoryContext` | interface | yes | - | code/core/src/csf/story.ts:268 | PASS |
| `StoryFn` | type | yes | - | code/core/src/csf/story.ts:327 | PASS |
| `StoryIndexGenerator` | - | yes | - | - | WARN |
| `StoryObj` | type | yes | - | code/renderers/react/src/public-types.ts:47 | PASS |
| `StoryProps` | type | no | - | code/addons/docs/src/blocks/blocks/Story.tsx:60 | WARN |
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
| `TextControl` | function | yes | yes | code/addons/docs/src/blocks/controls/Text.tsx:23 | PASS |
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
| `Unstyled` | const | yes | yes | code/addons/docs/src/blocks/blocks/Unstyled.tsx:9 | PASS |
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
| `automock` | - | yes | - | - | WARN |
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
| `extract` | - | yes | - | - | WARN |
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
| `isMockFunction` | - | yes | - | code/core/src/test/spy.ts | PASS |
| `lighten` | const | yes | - | code/core/src/theming/utils.ts:61 | PASS |
| `logDOM` | - | yes | yes | code/core/src/test/testing-library.ts:84 | PASS |
| `logRoles` | - | yes | yes | code/core/src/test/testing-library.ts:85 | PASS |
| `logTracker` | - | yes | - | - | WARN |
| `makeDecorator` | function | yes | - | code/core/src/preview-api/modules/addons/make-decorator.ts:44 | PASS |
| `mockChannel` | function | yes | yes | code/core/src/manager-api/lib/storybook-channel-mock.ts:3 | PASS |
| `mocked` | function | yes | yes | code/core/src/test/spy.ts:119 | PASS |
| `mocks` | - | yes | - | code/core/src/test/spy.ts | PASS |
| `normalizeArrays` | function | yes | yes | code/core/src/preview-api/modules/store/csf/normalizeArrays.ts:1 | PASS |
| `normalizeProjectAnnotations` | function | yes | yes (Low) | code/core/src/preview-api/modules/store/csf/normalizeProjectAnnotations.ts:17 | WARN |
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
| `redirect` | - | yes | - | - | WARN |
| `resetAllMocks` | function | yes | yes | code/core/src/test/spy.ts:89 | PASS |
| `resolve` | - | yes | - | - | WARN |
| `responsiveViewport` | const | yes | - | code/core/src/viewport/responsiveViewport.tsx:4 | PASS |
| `restoreAllMocks` | function | yes | yes | code/core/src/test/spy.ts:98 | PASS |
| `runtime` | - | yes | - | - | WARN |
| `sanitizeStoryContextUpdate` | function | yes | yes (Low) | code/core/src/preview-api/modules/store/decorators.ts:30 | WARN |
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
| `withActions` | const | yes | - | code/core/src/actions/decorator.ts:59 | PASS |
| `withThemeByClassName` | function | yes | yes (Low) | code/addons/themes/src/decorators/class-name.decorator.tsx:19 | WARN |
| `withThemeByDataAttribute` | function | yes | yes (Low) | code/addons/themes/src/decorators/data-attribute.decorator.tsx:19 | WARN |
| `withThemeFromJSXProvider` | function | yes | yes (Low) | code/addons/themes/src/decorators/provider.decorator.tsx:23 | WARN |
| `within` | - | yes | yes | code/core/src/test/testing-library.ts:110 | PASS |
| `withoutVitePlugins` | function | yes | yes | code/builders/builder-vite/src/utils/without-vite-plugins.ts:2 | PASS |

### Coverage Summary

- **Exports Found:** 370
- **Documented:** 364 (98.38%)
- **Missing Documentation:** 6
- **Signature Mismatches:** 1, plus 7 graded Low or Info and counted as matching
- **Stale Documentation:** 91, documented extras included
- **Coverage Warnings:**
  - the `tier_a_include` set holds 376 names and the stored count (`stats.effective_denominator`) is 370: the denominator stays the stored count, so `missing` and `missingCount` can differ
- **Scoped Out by the Brief:** `A` (code/core/src/components/components/typography/elements/A.tsx:7), `AbstractToolbar` (code/core/src/components/components/Toolbar/Toolbar.tsx:15), `ActionBar` (code/core/src/components/components/ActionBar/ActionBar.tsx:89), `ActionItem` (code/core/src/components/components/ActionBar/ActionBar.tsx:72), `ActionList` (code/core/src/components/components/ActionList/ActionList.tsx:222), `AddonPanel` (code/core/src/components/components/addon-panel/addon-panel.tsx:36), `AngularMeta` (code/frameworks/angular/src/client/preview.ts:150), `AngularOptions` (code/frameworks/angular/src/types.ts:47), `AngularParameters` (code/frameworks/angular/src/client/types.ts:45), `AngularPreview` (code/frameworks/angular/src/client/preview.ts:81), `AngularRenderer` (code/frameworks/angular/src/client/types.ts:40), `AngularStory` (code/frameworks/angular/src/client/preview.ts:254), `BabelFileClass` (code/core/src/babel/index.ts:43), `BadMetaError` (code/core/src/csf-tools/CsfFile.ts:246), `Badge` (code/core/src/components/components/Badge/Badge.tsx:88), `Bar` (code/core/src/components/components/Bar/Bar.tsx:52), `BarProps` (code/core/src/components/components/Bar/Bar.tsx:7), `BaseLocationProvider` (code/core/src/router/router.tsx:144), `Blockquote` (code/core/src/components/components/typography/elements/Blockquote.tsx:6), `BuildIndexOptions` (code/core/src/core-server/build-index.ts:10), `BuildStaticStandaloneOptions` (code/core/src/core-server/build-static.ts:31), `Button` (code/core/src/components/components/Button/Button.tsx:53), `ButtonProps` (code/core/src/components/components/Button/Button.tsx:14), `CLI_COLORS` (code/core/src/node-logger/logger/colors.ts:3), `CacheEntry` (code/core/src/telemetry/event-cache.ts:12), `Card` (code/core/src/components/components/Card/Card.tsx:98), `Channel` (code/core/src/channels/main.ts:22), `ChannelEvent` (code/core/src/channels/types.ts:18), `ChannelHandler` (code/core/src/channels/types.ts:11), `ChannelLike` (code/core/src/channels/types.ts:36), `ChannelTransport` (code/core/src/channels/types.ts:13), `ClipboardCode` (code/core/src/components/components/clipboard/ClipboardCode.tsx:24), `Code` (code/core/src/components/components/typography/elements/Code.tsx:42), `Collapsible` (code/core/src/components/components/Collapsible/Collapsible.tsx:31), `ComponentArgTypesData` (code/core/src/core-server/utils/get-dummy-args-from-argtypes.ts:8), `ConfigFile` (code/core/src/csf-tools/ConfigFile.ts:140), `ConsoleLogger` (code/core/src/node-logger/logger/console.ts:340), `Context` (code/core/src/telemetry/types.ts:106), `CsfFile` (code/core/src/csf-tools/CsfFile.ts:280), `CsfOptions` (code/core/src/csf-tools/CsfFile.ts:200), `DEEPLY_EQUAL` (code/core/src/router/utils.ts:43), `DL` (code/core/src/components/components/typography/elements/DL.tsx:6), `Dependency` (code/core/src/telemetry/types.ts:48), `Div` (code/core/src/components/components/typography/elements/Div.tsx:5), `DocumentWrapper` (code/core/src/components/components/typography/DocumentWrapper.tsx:3), `EmptyTabContent` (code/core/src/components/components/Tabs/EmptyTabContent.tsx:47), `EnrichCsfOptions` (code/core/src/csf-tools/enrichCsf.ts:6), `ErrorCollector` (code/core/src/telemetry/error-collector.ts:13), `ErrorFormatter` (code/core/src/components/components/ErrorFormatter/ErrorFormatter.tsx:29), `EventType` (code/core/src/telemetry/types.ts:9), `FlexBar` (code/core/src/components/components/Bar/Bar.tsx:129), `Form` (code/core/src/components/components/Form/Form.tsx:11), `GenerateStoryOptions` (code/core/src/core-server/utils/generate-story.ts:21), `GenerateStoryResult` (code/core/src/core-server/utils/generate-story.ts:11), `H1` (code/core/src/components/components/typography/elements/H1.tsx:6), `H2` (code/core/src/components/components/typography/elements/H2.tsx:6), `H3` (code/core/src/components/components/typography/elements/H3.tsx:6), `H4` (code/core/src/components/components/typography/elements/H4.tsx:6), `H5` (code/core/src/components/components/typography/elements/H5.tsx:6), `H6` (code/core/src/components/components/typography/elements/H6.tsx:6), `HEARTBEAT_INTERVAL` (code/core/src/channels/websocket/index.ts:20), `HEARTBEAT_MAX_LATENCY` (code/core/src/channels/websocket/index.ts:21), `HR` (code/core/src/components/components/typography/elements/HR.tsx:3), `IErrorWithStdErrAndStdOut` (code/core/src/telemetry/sanitize.ts:4), `IStory` (code/frameworks/angular/src/client/types.ts:31), `IconButton` (code/core/src/components/components/Button/Button.tsx:327), `Img` (code/core/src/components/components/typography/elements/Img.tsx:3), `InitPayload` (code/core/src/telemetry/types.ts:131), `LI` (code/core/src/components/components/typography/elements/LI.tsx:6), `Link` (code/core/src/components/components/typography/link/link.tsx:198), `LinkProps` (code/core/src/router/types.ts:23), `ListItem` (code/core/src/components/components/tooltip/ListItem.tsx:249), `Listener` (code/core/src/channels/types.ts:24), `Location` (code/core/src/router/router.tsx:81), `LocationProvider` (code/core/src/router/router.tsx:143), `LogLevel` (code/core/src/node-logger/logger/logger.ts:46), `Match` (code/core/src/router/router.tsx:141), `MemoryRouter` (code/core/src/router/router.tsx:145), `MixedFactoryError` (code/core/src/csf-tools/CsfFile.ts:234), `Modal` (code/core/src/components/components/Modal/Modal.tsx:242), `ModalDecorator` (code/core/src/components/components/Modal/Modal.tsx:248), `MultipleMetaError` (code/core/src/csf-tools/CsfFile.ts:222), `NavigateFunction` (code/core/src/router/types.ts:14), `NavigateOptions` (code/core/src/router/types.ts:12), `NoMetaError` (code/core/src/csf-tools/CsfFile.ts:210), `OL` (code/core/src/components/components/typography/elements/OL.tsx:16), `Other` (code/core/src/router/types.ts:7), `P` (code/core/src/components/components/typography/elements/P.tsx:6), `Payload` (code/core/src/telemetry/types.ts:102), `Placeholder` (code/core/src/components/components/placeholder/placeholder.tsx:22), `Popover` (code/core/src/components/components/Popover/Popover.tsx:77), `PopoverProps` (code/core/src/components/components/Popover/Popover.tsx:9), `PopoverProvider` (code/core/src/components/components/Popover/PopoverProvider.tsx:63), `PopoverProviderProps` (code/core/src/components/components/Popover/PopoverProvider.tsx:13), `PopperPlacement` (code/core/src/components/components/shared/overlayHelpers.tsx:22), `PostMessageTransport` (code/core/src/channels/postmessage/index.ts:29), `Pre` (code/core/src/components/components/typography/elements/Pre.tsx:6), `PreactRenderer` (code/renderers/preact/src/types.ts:14), `ProgressSpinner` (code/core/src/components/components/ProgressSpinner/ProgressSpinner.tsx:66), `RenderData` (code/core/src/router/types.ts:21), `ResetWrapper` (code/core/src/components/components/typography/ResetWrapper.tsx:12), `Route` (code/core/src/router/router.tsx:141), `RouterData` (code/core/src/router/types.ts:16), `ScrollArea` (code/core/src/components/components/ScrollArea/ScrollArea.tsx:95), `Select` (code/core/src/components/components/Select/Select.tsx:201), `Separator` (code/core/src/components/components/Bar/Separator.tsx:9), `Spaced` (code/core/src/components/components/spaced/Spaced.tsx:63), `Span` (code/core/src/components/components/typography/elements/Span.tsx:6), `SpinnerInstance` (code/core/src/node-logger/prompts/prompt-provider-base.ts:46), `StatelessTab` (code/core/src/components/components/Tabs/StatelessTab.tsx:57), `StatelessTabList` (code/core/src/components/components/Tabs/StatelessTabList.tsx:66), `StatelessTabListProps` (code/core/src/components/components/Tabs/StatelessTabList.tsx:62), `StatelessTabPanel` (code/core/src/components/components/Tabs/StatelessTabPanel.tsx:30), `StatelessTabPanelProps` (code/core/src/components/components/Tabs/StatelessTabPanel.tsx:9), `StatelessTabProps` (code/core/src/components/components/Tabs/StatelessTab.tsx:7), `StatelessTabsView` (code/core/src/components/components/Tabs/StatelessTabsView.tsx:31), `StatelessTabsViewProps` (code/core/src/components/components/Tabs/StatelessTabsView.tsx:27), `StaticMeta` (code/core/src/csf-tools/CsfFile.ts:258), `StaticStory` (code/core/src/csf-tools/CsfFile.ts:265), `StoryData` (code/core/src/router/utils.ts:9), `StoryIndexGenerator` (code/core/src/core-server/utils/StoryIndexGenerator.ts:101), `StoryTest` (code/core/src/csf-tools/CsfFile.ts:271), `StorybookAddon` (code/core/src/telemetry/types.ts:53), `StorybookBuilderOptions` (code/frameworks/angular/src/builders/build-storybook/index.ts:38), `StorybookBuilderOutput` (code/frameworks/angular/src/builders/build-storybook/index.ts:68), `StorybookIcon` (code/core/src/components/brand/StorybookIcon.tsx:3), `StorybookLogo` (code/core/src/components/brand/StorybookLogo.tsx:7), `StorybookMetadata` (code/core/src/telemetry/types.ts:57), `StyledConsoleLogger` (code/core/src/node-logger/logger/console.ts:340), `SvelteRenderer` (code/renderers/svelte/src/types.ts:11), `SyntaxHighlighter` (code/core/src/components/components/syntaxhighlighter/lazy-syntaxhighlighter.tsx:52), `SyntaxHighlighterFormatTypes` (code/core/src/components/components/syntaxhighlighter/syntaxhighlighter-types.ts:24), `SyntaxHighlighterProps` (code/core/src/components/components/syntaxhighlighter/syntaxhighlighter-types.ts:47), `SyntaxHighlighterRendererProps` (code/core/src/components/components/syntaxhighlighter/syntaxhighlighter-types.ts:5), `TT` (code/core/src/components/components/typography/elements/TT.tsx:5), `TabBar` (code/core/src/components/components/Tabs/Tabs.tsx:61), `TabButton` (code/core/src/components/components/Tabs/Button.tsx:139), `TabList` (code/core/src/components/components/Tabs/TabList.tsx:150), `TabListProps` (code/core/src/components/components/Tabs/TabList.tsx:146), `TabPanel` (code/core/src/components/components/Tabs/TabPanel.tsx:34), `TabPanelProps` (code/core/src/components/components/Tabs/TabPanel.tsx:12), `TabProps` (code/core/src/components/components/Tabs/TabsView.tsx:15), `TabWrapper` (code/core/src/components/components/Tabs/Tabs.tsx:120), `Table` (code/core/src/components/components/typography/elements/Table.tsx:6), `Tabs` (code/core/src/components/components/Tabs/Tabs.tsx:188), `TabsState` (code/core/src/components/components/Tabs/Tabs.tsx:287), `TabsView` (code/core/src/components/components/Tabs/TabsView.tsx:106), `TabsViewProps` (code/core/src/components/components/Tabs/TabsView.tsx:64), `TaskLogInstance` (code/core/src/node-logger/prompts/prompt-provider-base.ts:54), `TelemetryData` (code/core/src/telemetry/types.ts:119), `TelemetryEvent` (code/core/src/telemetry/types.ts:125), `ToggleButton` (code/core/src/components/components/ToggleButton/ToggleButton.tsx:16), `Toolbar` (code/core/src/components/components/Toolbar/Toolbar.tsx:36), `Tooltip` (code/core/src/components/components/tooltip/Tooltip.tsx:7), `TooltipLinkList` (code/core/src/components/components/tooltip/TooltipLinkList.tsx:70), `TooltipLinkListLink` (code/core/src/components/components/tooltip/TooltipLinkList.tsx:39), `TooltipMessage` (code/core/src/components/components/tooltip/TooltipMessage.tsx:47), `TooltipNote` (code/core/src/components/components/tooltip/TooltipNote.tsx:23), `TooltipNoteProps` (code/core/src/components/components/tooltip/TooltipNote.tsx:19), `TooltipProps` (code/core/src/components/components/tooltip/Tooltip.tsx:5), `TooltipProvider` (code/core/src/components/components/tooltip/TooltipProvider.tsx:108), `TooltipProviderProps` (code/core/src/components/components/tooltip/TooltipProvider.tsx:14), `TransformComponentType` (code/frameworks/angular/src/client/public-types.ts:56), `UL` (code/core/src/components/components/typography/elements/UL.tsx:16), `WebComponentsMeta` (code/renderers/web-components/src/preview.ts:160), `WebComponentsPreview` (code/renderers/web-components/src/preview.ts:85), `WebComponentsRenderer` (code/renderers/web-components/src/types.ts:14), `WebComponentsStory` (code/renderers/web-components/src/preview.ts:264), `WebComponentsTypes` (code/renderers/web-components/src/types.ts:24), `WebsocketTransport` (code/core/src/channels/websocket/index.ts:23), `WithTooltip` (code/core/src/components/components/tooltip/lazy-WithTooltip.tsx:8), `WithTooltipPure` (code/core/src/components/components/tooltip/lazy-WithTooltip.tsx:18), `Zoom` (code/core/src/components/components/Zoom/Zoom.tsx:4), `addToGlobalContext` (code/core/src/telemetry/telemetry.ts:26), `applicationConfig` (code/frameworks/angular/src/client/decorators.ts:37), `argsToTemplate` (code/frameworks/angular/src/client/argsToTemplate.ts:59), `babelParseExpression` (code/core/src/babel/babelParse.ts:52), `babelParseFile` (code/core/src/csf-tools/CsfFile.ts:1062), `babelPrint` (code/core/src/babel/babelParse.ts:42), `buildArgsParam` (code/core/src/router/utils.ts:186), `buildDevStandalone` (code/core/src/core-server/build-dev.ts:44), `buildIndex` (code/core/src/core-server/build-index.ts:12), `buildIndexStandalone` (code/core/src/core-server/build-index.ts:39), `buildStaticStandalone` (code/core/src/core-server/build-static.ts:35), `canUpdateVitestConfigFile` (code/core/src/babel/vitest-config-helpers.ts:159), `canUpdateVitestWorkspaceFile` (code/core/src/babel/vitest-config-helpers.ts:204), `cleanPaths` (code/core/src/telemetry/sanitize.ts:24), `codeCommon` (code/core/src/components/components/typography/lib/common.tsx:22), `colors` (code/core/src/node-logger/index.ts:57), `componentTransform` (code/core/src/csf-tools/vitest-plugin/component-transformer.ts:285), `componentWrapperDecorator` (code/frameworks/angular/src/client/decorators.ts:60), `components` (code/core/src/components/index.ts:133), `computeStorybookMetadata` (code/core/src/telemetry/storybook-metadata.ts:105), `convertToReactAriaPlacement` (code/core/src/components/components/shared/overlayHelpers.tsx:24), `createBrowserChannel` (code/core/src/channels/index.ts:32), `createCopyToClipboardFunction` (code/core/src/components/components/syntaxhighlighter/clipboard.ts:26), `createHyperlink` (code/core/src/node-logger/wrap-utils.ts:155), `createReactiveProps` (code/renderers/svelte/static/createReactiveProps.svelte.js:10), `deepDiff` (code/core/src/router/utils.ts:44), `deepMerge` (code/frameworks/angular/src/server/framework-preset-angular-cli.ts:95), `enrichCsf` (code/core/src/csf-tools/enrichCsf.ts:144), `enrichCsfMeta` (code/core/src/csf-tools/enrichCsf.ts:129), `enrichCsfStory` (code/core/src/csf-tools/enrichCsf.ts:12), `experimental_loadStorybook` (code/core/src/core-server/load.ts:18), `extractDescription` (code/core/src/csf-tools/enrichCsf.ts:158), `extractSource` (code/core/src/csf-tools/enrichCsf.ts:152), `formatConfig` (code/core/src/csf-tools/ConfigFile.ts:1165), `formatCsf` (code/core/src/csf-tools/CsfFile.ts:1083), `framework` (code/core/src/core-server/presets/common-override-preset.ts:5), `generate` (code/core/src/babel/index.ts:38), `generateStoryFile` (code/core/src/core-server/utils/generate-story.ts:64), `getConfigObjectFromMergeArg` (code/core/src/babel/vitest-config-helpers.ts:49), `getCustomElements` (code/renderers/web-components/src/framework-api.ts:37), `getEffectiveMergeConfigCall` (code/core/src/babel/vitest-config-helpers.ts:78), `getErrorLevel` (code/core/src/core-server/withTelemetry.ts:40), `getLastEvents` (code/core/src/telemetry/event-cache.ts:41), `getMatch` (code/core/src/router/utils.ts:233), `getPrecedingUpgrade` (code/core/src/telemetry/event-cache.ts:68), `getServerPort` (code/core/src/core-server/utils/server-address.ts:34), `getSessionId` (code/core/src/telemetry/session-id.ts:18), `getStoryHref` (code/core/src/components/components/utils/getStoryHref.ts:15), `getStorySortParameter` (code/core/src/csf-tools/getStorySortParameter.ts:96), `getStorybookMetadata` (code/core/src/telemetry/storybook-metadata.ts:312), `getTargetConfigObject` (code/core/src/babel/vitest-config-helpers.ts:118), `hrefTo` (code/addons/links/src/utils.ts:39), `interleaveSeparators` (code/core/src/components/components/Bar/Separator.tsx:29), `isCsfFactoryPreview` (code/core/src/csf-tools/ConfigFile.ts:1187), `isDefineConfigLike` (code/core/src/babel/vitest-config-helpers.ts:35), `isExampleStoryId` (code/core/src/telemetry/index.ts:26), `isImportedDefineConfigLikeIdentifier` (code/core/src/babel/vitest-config-helpers.ts:18), `isModuleMock` (code/core/src/csf-tools/CsfFile.ts:116), `isTelemetryEnabled` (code/core/src/core-server/withTelemetry.ts:157), `isValidComponent` (code/renderers/web-components/src/framework-api.ts:3), `isValidMetaData` (code/renderers/web-components/src/framework-api.ts:13), `isValidPreviewPath` (code/core/src/csf-tools/CsfFile.ts:43), `linkTo` (code/addons/links/src/utils.ts:61), `loadConfig` (code/core/src/csf-tools/ConfigFile.ts:1160), `loadCsf` (code/core/src/csf-tools/CsfFile.ts:1077), `logTracker` (code/core/src/node-logger/logger/log-tracker.ts:95), `mapStaticDir` (code/core/src/core-server/utils/server-statics.ts:198), `metaFrameworks` (code/core/src/telemetry/storybook-metadata.ts:33), `moduleMetadata` (code/frameworks/angular/src/client/decorators.ts:11), `nameSpaceClassNames` (code/core/src/components/components/typography/DocumentFormatting.tsx:1), `navigate` (code/addons/links/src/utils.ts:36), `oneWayHash` (code/core/src/telemetry/one-way-hash.ts:4), `parsePath` (code/core/src/router/utils.ts:17), `parserOptions` (code/core/src/babel/babelParse.ts:21), `printConfig` (code/core/src/csf-tools/ConfigFile.ts:1169), `printCsf` (code/core/src/csf-tools/CsfFile.ts:1096), `prompt` (code/core/src/node-logger/prompts/index.ts:5), `protectUrls` (code/core/src/node-logger/wrap-utils.ts:70), `queryFromLocation` (code/core/src/router/utils.ts:222), `readConfig` (code/core/src/csf-tools/ConfigFile.ts:1173), `readCsf` (code/core/src/csf-tools/CsfFile.ts:1100), `removeAnsiEscapeCodes` (code/core/src/telemetry/sanitize.ts:15), `resetComponents` (code/core/src/components/index.ts:142), `resolveExpression` (code/core/src/babel/expression-resolver.ts:22), `runNgcc` (code/frameworks/angular/src/server/framework-preset-angular-ivy.ts:37), `sanitizeAddonName` (code/core/src/telemetry/storybook-metadata.ts:50), `sanitizeError` (code/core/src/telemetry/sanitize.ts:64), `sendTelemetryError` (code/core/src/core-server/withTelemetry.ts:91), `setCustomElements` (code/renderers/web-components/src/framework-api.ts:29), `setCustomElementsManifest` (code/renderers/web-components/src/framework-api.ts:33), `stories` (code/core/src/core-server/presets/common-override-preset.ts:18), `stringifyQuery` (code/core/src/router/utils.ts:226), `telemetry` (code/core/src/telemetry/index.ts:31), `traverse` (code/core/src/babel/index.ts:39), `typescript` (code/core/src/core-server/presets/common-override-preset.ts:25), `unwrapTSExpression` (code/core/src/babel/expression-resolver.ts:4), `useNavigate` (code/core/src/router/router.tsx:45), `useTabsState` (code/core/src/components/components/Tabs/TabsView.tsx:30), `vitestTransform` (code/core/src/csf-tools/vitest-plugin/transformer.ts:108), `webpackFinal` (code/frameworks/angular/src/server/framework-preset-angular-cli.ts:15), `withLinks` (code/addons/links/src/utils.ts:110), `withReset` (code/core/src/components/components/typography/lib/common.tsx:36), `withTelemetry` (code/core/src/core-server/withTelemetry.ts:161), `writeConfig` (code/core/src/csf-tools/ConfigFile.ts:1178), `writeCsf` (code/core/src/csf-tools/CsfFile.ts:1105)

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 98.38% |
| Signature Accuracy | 99.45% |
| Type Coverage | 92.97% |

### Coverage Notes

- **Inventory:** built by the parent from SKILL.md and all six `references/*.md` files (SKILL.md's `## Full` headings are pointer stubs), no subagent tool being available in this session: 723 entries over 595 names, one entry per documentation place (the floor's 435 origins, the forms written in prose and fenced examples, and the export tables whose first column is not headed `Export`: the 50 Testing Library queries of core-api.md:170-189 and the control primitives of doc-blocks.md:253-278). Names the skill itself says are not exported or are module-local (`A11yTest`, `CanvasProps`, `LogRolesOptions`, `ArgsHash`, the Testing Library option types) were left out; names that appear only inside another export's signature were left out. The Canvas and Source props-detail tables (doc-blocks.md:40-50, 92-103) are the detail of the Canvas and Source rows, not inventory places; they were read by hand against `Canvas.tsx:18-49` and `Source.tsx:16-42` and agree. `validate-inventory.py` passed on the first run: schema, spot-check (`A`, `ToggleButton`, `withoutVitePlugins` found), floor 380 of 380 names kept and every pinned signature carried.
- **Split-body cross-check (§1b):** 40 names are documented in two or more files; no contradiction under the rules (no `cross_check_mismatches`). The `composeStories`, `composeStory` and `withThemeByClassName` pairs are borderline calls, recorded in the report's notes below.
- **Read by eye** (the recipe runner hit a syntax error in each): `code/core/src/csf/csf-factories.ts`, `code/core/src/instrumenter/typings.d.ts`, `code/core/src/mocking-utils/esmWalker.ts`, `code/core/src/test/spy.ts`, `code/core/src/typings.d.ts`. Their per-file results list each file's export statements; `export type * from '@vitest/spy'` (spy.ts:15) and `export type * from 'estree'` (esmWalker.ts:37) re-export an external package's type names, of which the per-file results list those the file's own imports prove (`Mock`, `MockInstance`, `MaybeMocked`, `MaybeMockedDeep`, `MaybePartiallyMocked`, `MaybePartiallyMockedDeep` from spy.ts:1-6). They added `isMockFunction`, `mocks` and those six types to the tier A set (368 to 376). The two typings files declare globals and export nothing. **Unread:** none.
- **Extraction gaps:** 146 names no recipe found, all on the surface; the 66 compared ones (`code/core/src/test/testing-library.ts`, the destructured bindings at L39-112) were read by eye.
- **Signature comparison:** 181 checks over 77 source files, judged in the main thread by `references/signature-comparison-rules.md`, the same rules for every batch, saved as four result files (plan files 0-27, 28-44, 45-76 but testing-library.ts, and testing-library.ts alone). One Critical mismatch (`ArgTypes`), six Low `parameter-name` mismatches and one Info partial signature (`Story`), counted as matching. `score-signatures.py` reported no warnings.
- **Guards:** `guards.deflation` does not fire (`stats.effective_denominator` 370 against a re-derived tier A set of 376, +1.62%); `guards.inflation` and `guards.staleScope` do not fire. The scalar branch counts the tier A set (376 names, 12 undocumented) over the stored denominator 370, so `missingCount` is 6.
- **Numerator ground truth:** skipped (the declared count is not the denominator).
- **Metadata count cross-check:** `stats.exports_public_api` 1335 against `exports[]` 88 (93% drift, Medium `metadata-drift`); barrel 1335 against documented 365 (Info `multi-denominator`).
- **Stale names:** 91 documented names outside the tier A set and the `all` set; `classify-stale` found none fabricated, 55 still defined at one declaration, 28 declared in several files, 8 with neither.
- **Provenance line check:** one map line that is not the definition of its export and whose definition the rules could not find (`default`, `code/addons/vitest/src/vitest-plugin/index.ts:531`, Info `provenance-unverified`).
- **Deep tier, not checked by script:** 3 documentation errors read by hand and recorded as Info observations (ledger records titled `Not checked by script: {name}`): `HooksContext`, `DocsContext`, `PreviewWeb`.

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)
**Migration Section:** Section 4b verification skipped: evidence-report.md pins no `t2_future_count`. For a skill create-skill made, re-run create-skill to regenerate the report with the field (create-stack-skill does not write it).

### Structural Findings

| # | Type | Severity | Detail | Line |
|---|------|----------|--------|------|
| - | none | - | No finding across §§2.1-2.7: the description, usage and API-surface families are served by `## Overview`, `## Quick Start` and `## Key API Summary`; 10 code fences, all balanced and tagged; no table row drifts from its header; all 276 function exports of the inventory are used in a usage-family section or a reference file; no export is described as async without an await, or as sync while awaited (`getByRole`'s two awaited calls sit in the arguments of `userEvent.click`, a JavaScript callee); no `scripts/` or `assets/` folder | - |

**Structural Issues:** 0

### Reference Consistency (split-body)

| # | Reference File | Export | Issue | Other Side | Reference Line | Contradicted Side |
|---|---------------|--------|-------|------------|---------------|-------------------|
| - | - | - | No split-body mismatch | - | - | none |

**Exports Cross-Checked:** 40
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

**Result:** **FAIL**, not scored: the hard gate blocked this run on 1 Critical or High gap(s), listed first in the Gap Report.

## Gap Report

**Total Gaps:** 117
**Blocking (Critical + High):** 1
**Non-blocking (Medium + Low + Info):** 116

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|------------------|
| Critical | 1 | Read the source code and write or correct the documentation |
| High | 0 | None |
| Medium | 97 | Add type definitions, interface docs or the missing section |
| Low | 6 | Add examples or metadata |
| Info | 13 | Optional improvements, no action required |
| **Total** | **117** | |

### GAP-005: Signature mismatch: ArgTypes

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/core/src/csf/story.ts:162
**Export:** ArgTypes

**Issue:** documented `{ of?, include?, exclude?, sort? }`, source `export type ArgTypes<TArgs = Args> = { [name in keyof TArgs]: InputType };`: the documented form is a props list (of?, include?, exclude?, sort?); the declaration the check names is the CSF mapped type ArgTypes<TArgs>, which takes no props or parameters

**Remediation:** Update the documented signature of `ArgTypes` from `{ of?, include?, exclude?, sort? }` to `export type ArgTypes<TArgs = Args> = { [name in keyof TArgs]: InputType };`, the signature the source defines at `code/core/src/csf/story.ts:162`.

### GAP-009: Missing type: AnchorProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/Anchor.tsx:6
**Export:** AnchorProps

**Issue:** the type `AnchorProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `AnchorProps` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Anchor.tsx:6` and list its fields or members.

### GAP-010: Missing type: DocsContainerProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/DocsContainer.tsx:18
**Export:** DocsContainerProps

**Issue:** the type `DocsContainerProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `DocsContainerProps` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/DocsContainer.tsx:18` and list its fields or members.

### GAP-011: Missing type: DocsProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/Docs.tsx:12
**Export:** DocsProps

**Issue:** the type `DocsProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `DocsProps` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Docs.tsx:12` and list its fields or members.

### GAP-012: Missing type: DocsStoryProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/types.ts:9
**Export:** DocsStoryProps

**Issue:** the type `DocsStoryProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `DocsStoryProps` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/types.ts:9` and list its fields or members.

### GAP-013: Missing type: HeadingProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/Heading.tsx:11
**Export:** HeadingProps

**Issue:** the type `HeadingProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `HeadingProps` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Heading.tsx:11` and list its fields or members.

### GAP-014: Missing export: MaybeMockedDeep

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/spy.ts
**Export:** MaybeMockedDeep

**Issue:** `MaybeMockedDeep` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `MaybeMockedDeep` in SKILL.md: read its definition at `code/core/src/test/spy.ts` and add its signature, its purpose and a usage example.

### GAP-015: Missing export: MaybePartiallyMocked

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/spy.ts
**Export:** MaybePartiallyMocked

**Issue:** `MaybePartiallyMocked` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `MaybePartiallyMocked` in SKILL.md: read its definition at `code/core/src/test/spy.ts` and add its signature, its purpose and a usage example.

### GAP-016: Missing export: MaybePartiallyMockedDeep

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/spy.ts
**Export:** MaybePartiallyMockedDeep

**Issue:** `MaybePartiallyMockedDeep` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `MaybePartiallyMockedDeep` in SKILL.md: read its definition at `code/core/src/test/spy.ts` and add its signature, its purpose and a usage example.

### GAP-017: Missing type: PropDescriptor

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/preview-api/modules/store/filterArgTypes.ts:5
**Export:** PropDescriptor

**Issue:** the type `PropDescriptor` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `PropDescriptor` in SKILL.md: read its definition at `code/core/src/preview-api/modules/store/filterArgTypes.ts:5` and list its fields or members.

### GAP-018: Missing type: SourceParameters

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/Source.tsx:16
**Export:** SourceParameters

**Issue:** the type `SourceParameters` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SourceParameters` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Source.tsx:16` and list its fields or members.

### GAP-019: Missing type: SourceProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/Source.tsx:28
**Export:** SourceProps

**Issue:** the type `SourceProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SourceProps` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Source.tsx:28` and list its fields or members.

### GAP-020: Missing type: StoryProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/Story.tsx:60
**Export:** StoryProps

**Issue:** the type `StoryProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StoryProps` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Story.tsx:60` and list its fields or members.

### GAP-021: Stale documentation: A

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:204
**Export:** A

**Issue:** `SKILL.md:204` documents `A`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/A.tsx:7` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `A` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/A.tsx:7`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `A` at SKILL.md:204.

### GAP-022: Stale documentation: ActionBar

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:418
**Export:** ActionBar

**Issue:** `references/core-api.md:418` documents `ActionBar`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/ActionBar/ActionBar.tsx:89` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `ActionBar` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/ActionBar/ActionBar.tsx:89`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `ActionBar` at references/core-api.md:418.

### GAP-023: Stale documentation: ActionList

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:418
**Export:** ActionList

**Issue:** `references/core-api.md:418` documents `ActionList`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/ActionList/ActionList.tsx:222` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `ActionList` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/ActionList/ActionList.tsx:222`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `ActionList` at references/core-api.md:418.

### GAP-024: Stale documentation: AddonPanel

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:415
**Export:** AddonPanel

**Issue:** `references/core-api.md:415` documents `AddonPanel`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/addon-panel/addon-panel.tsx:36` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `AddonPanel` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/addon-panel/addon-panel.tsx:36`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `AddonPanel` at references/core-api.md:415.

### GAP-025: Stale documentation: Badge

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:413
**Export:** Badge

**Issue:** `references/core-api.md:413` documents `Badge`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Badge/Badge.tsx:88` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Badge` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Badge/Badge.tsx:88`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Badge` at references/core-api.md:413.

### GAP-026: Stale documentation: Bar

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:418
**Export:** Bar

**Issue:** `references/core-api.md:418` documents `Bar`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Bar/Bar.tsx:52` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Bar` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Bar/Bar.tsx:52`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Bar` at references/core-api.md:418.

### GAP-027: Stale documentation: Blockquote

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:413
**Export:** Blockquote

**Issue:** `references/core-api.md:413` documents `Blockquote`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/Blockquote.tsx:6` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Blockquote` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/Blockquote.tsx:6`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Blockquote` at references/core-api.md:413.

### GAP-028: Stale documentation: Button

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:44
**Export:** Button

**Issue:** `SKILL.md:44` documents `Button`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Button/Button.tsx:53` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Button` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Button/Button.tsx:53`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Button` at SKILL.md:44.

### GAP-029: Stale documentation: Card

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:415
**Export:** Card

**Issue:** `references/core-api.md:415` documents `Card`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Card/Card.tsx:98` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Card` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Card/Card.tsx:98`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Card` at references/core-api.md:415.

### GAP-030: Stale documentation: Channel

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:126
**Export:** Channel

**Issue:** `references/core-api.md:126` documents `Channel`, which the entry point `code/core/src/channels/index.ts` exports and `code/core/src/channels/main.ts:22` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Channel` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/channels/main.ts:22`, where it is defined, since its `scope.exclude` glob `code/core/src/channels/**` matches that file. To keep its documentation, narrow `code/core/src/channels/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Channel` at references/core-api.md:126.

### GAP-031: Stale documentation: CheckboxControl

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/doc-blocks.md:275
**Export:** CheckboxControl

**Issue:** SKILL.md documents `CheckboxControl`, which the enumerated source API surface lacks

**Remediation:** Check `CheckboxControl` against the source and update or remove its documentation at references/doc-blocks.md:275: the enumerated source surface does not export it.

### GAP-032: Stale documentation: Code

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:413
**Export:** Code

**Issue:** `references/core-api.md:413` documents `Code`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/Code.tsx:42` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Code` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/Code.tsx:42`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Code` at references/core-api.md:413.

### GAP-033: Stale documentation: Collapsible

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:415
**Export:** Collapsible

**Issue:** `references/core-api.md:415` documents `Collapsible`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Collapsible/Collapsible.tsx:31` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Collapsible` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Collapsible/Collapsible.tsx:31`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Collapsible` at references/core-api.md:415.

### GAP-034: Stale documentation: ColorControlProps

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/doc-blocks.md:255
**Export:** ColorControlProps

**Issue:** SKILL.md documents `ColorControlProps`, which the enumerated source API surface lacks

**Remediation:** Check `ColorControlProps` against the source and update or remove its documentation at references/doc-blocks.md:255: the enumerated source surface does not export it.

### GAP-035: Stale documentation: ConfigFile

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:438
**Export:** ConfigFile

**Issue:** `references/core-api.md:438` documents `ConfigFile`, which the entry point `code/core/src/csf-tools/index.ts` exports and `code/core/src/csf-tools/ConfigFile.ts:140` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `ConfigFile` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/csf-tools/ConfigFile.ts:140`, where it is defined, since its `scope.exclude` glob `code/core/src/csf-tools/**` matches that file. To keep its documentation, narrow `code/core/src/csf-tools/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `ConfigFile` at references/core-api.md:438.

### GAP-036: Stale documentation: CsfFile

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:438
**Export:** CsfFile

**Issue:** `references/core-api.md:438` documents `CsfFile`, which the entry point `code/core/src/csf-tools/index.ts` exports and `code/core/src/csf-tools/CsfFile.ts:280` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `CsfFile` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/csf-tools/CsfFile.ts:280`, where it is defined, since its `scope.exclude` glob `code/core/src/csf-tools/**` matches that file. To keep its documentation, narrow `code/core/src/csf-tools/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `CsfFile` at references/core-api.md:438.

### GAP-037: Stale documentation: DL

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:413
**Export:** DL

**Issue:** `references/core-api.md:413` documents `DL`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/DL.tsx:6` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `DL` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/DL.tsx:6`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `DL` at references/core-api.md:413.

### GAP-039: Stale documentation: Div

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:413
**Export:** Div

**Issue:** `references/core-api.md:413` documents `Div`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/Div.tsx:5` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Div` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/Div.tsx:5`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Div` at references/core-api.md:413.

### GAP-040: Stale documentation: ErrorFormatter

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:419
**Export:** ErrorFormatter

**Issue:** `references/core-api.md:419` documents `ErrorFormatter`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/ErrorFormatter/ErrorFormatter.tsx:29` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `ErrorFormatter` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/ErrorFormatter/ErrorFormatter.tsx:29`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `ErrorFormatter` at references/core-api.md:419.

### GAP-041: Stale documentation: FlexBar

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:418
**Export:** FlexBar

**Issue:** `references/core-api.md:418` documents `FlexBar`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Bar/Bar.tsx:129` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `FlexBar` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Bar/Bar.tsx:129`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `FlexBar` at references/core-api.md:418.

### GAP-042: Stale documentation: Form

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:414
**Export:** Form

**Issue:** `references/core-api.md:414` documents `Form`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Form/Form.tsx:11` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Form` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Form/Form.tsx:11`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Form` at references/core-api.md:414.

### GAP-043: Stale documentation: H1

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:413
**Export:** H1

**Issue:** `references/core-api.md:413` documents `H1`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/H1.tsx:6` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `H1` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/H1.tsx:6`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `H1` at references/core-api.md:413.

### GAP-044: Stale documentation: H6

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:413
**Export:** H6

**Issue:** `references/core-api.md:413` documents `H6`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/H6.tsx:6` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `H6` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/H6.tsx:6`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `H6` at references/core-api.md:413.

### GAP-045: Stale documentation: HR

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:413
**Export:** HR

**Issue:** `references/core-api.md:413` documents `HR`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/HR.tsx:3` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `HR` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/HR.tsx:3`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `HR` at references/core-api.md:413.

### GAP-047: Stale documentation: IconButton

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:414
**Export:** IconButton

**Issue:** `references/core-api.md:414` documents `IconButton`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Button/Button.tsx:327` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `IconButton` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Button/Button.tsx:327`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `IconButton` at references/core-api.md:414.

### GAP-048: Stale documentation: LI

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:413
**Export:** LI

**Issue:** `references/core-api.md:413` documents `LI`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/LI.tsx:6` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `LI` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/LI.tsx:6`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `LI` at references/core-api.md:413.

### GAP-049: Stale documentation: Modal

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:415
**Export:** Modal

**Issue:** `references/core-api.md:415` documents `Modal`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Modal/Modal.tsx:242` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Modal` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Modal/Modal.tsx:242`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Modal` at references/core-api.md:415.

### GAP-050: Stale documentation: OL

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:413
**Export:** OL

**Issue:** `references/core-api.md:413` documents `OL`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/OL.tsx:16` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `OL` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/OL.tsx:16`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `OL` at references/core-api.md:413.

### GAP-051: Stale documentation: P

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:413
**Export:** P

**Issue:** `references/core-api.md:413` documents `P`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/P.tsx:6` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `P` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/P.tsx:6`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `P` at references/core-api.md:413.

### GAP-052: Stale documentation: Placeholder

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:419
**Export:** Placeholder

**Issue:** `references/core-api.md:419` documents `Placeholder`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/placeholder/placeholder.tsx:22` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Placeholder` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/placeholder/placeholder.tsx:22`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Placeholder` at references/core-api.md:419.

### GAP-053: Stale documentation: Popover

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:417
**Export:** Popover

**Issue:** `references/core-api.md:417` documents `Popover`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Popover/Popover.tsx:77` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Popover` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Popover/Popover.tsx:77`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Popover` at references/core-api.md:417.

### GAP-054: Stale documentation: PopoverProvider

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:417
**Export:** PopoverProvider

**Issue:** `references/core-api.md:417` documents `PopoverProvider`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Popover/PopoverProvider.tsx:63` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `PopoverProvider` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Popover/PopoverProvider.tsx:63`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `PopoverProvider` at references/core-api.md:417.

### GAP-055: Stale documentation: PostMessageTransport

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:431
**Export:** PostMessageTransport

**Issue:** `references/core-api.md:431` documents `PostMessageTransport`, which the entry point `code/core/src/channels/index.ts` exports and `code/core/src/channels/postmessage/index.ts:29` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `PostMessageTransport` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/channels/postmessage/index.ts:29`, where it is defined, since its `scope.exclude` glob `code/core/src/channels/**` matches that file. To keep its documentation, narrow `code/core/src/channels/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `PostMessageTransport` at references/core-api.md:431.

### GAP-056: Stale documentation: Pre

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:413
**Export:** Pre

**Issue:** `references/core-api.md:413` documents `Pre`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/Pre.tsx:6` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Pre` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/Pre.tsx:6`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Pre` at references/core-api.md:413.

### GAP-057: Stale documentation: RadioControl

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/doc-blocks.md:275
**Export:** RadioControl

**Issue:** SKILL.md documents `RadioControl`, which the enumerated source API surface lacks

**Remediation:** Check `RadioControl` against the source and update or remove its documentation at references/doc-blocks.md:275: the enumerated source surface does not export it.

### GAP-059: Stale documentation: ScrollArea

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:415
**Export:** ScrollArea

**Issue:** `references/core-api.md:415` documents `ScrollArea`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/ScrollArea/ScrollArea.tsx:95` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `ScrollArea` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/ScrollArea/ScrollArea.tsx:95`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `ScrollArea` at references/core-api.md:415.

### GAP-060: Stale documentation: Select

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:414
**Export:** Select

**Issue:** `references/core-api.md:414` documents `Select`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Select/Select.tsx:201` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Select` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Select/Select.tsx:201`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Select` at references/core-api.md:414.

### GAP-061: Stale documentation: SelectControl

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/doc-blocks.md:275
**Export:** SelectControl

**Issue:** SKILL.md documents `SelectControl`, which the enumerated source API surface lacks

**Remediation:** Check `SelectControl` against the source and update or remove its documentation at references/doc-blocks.md:275: the enumerated source surface does not export it.

### GAP-064: Stale documentation: Spaced

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:419
**Export:** Spaced

**Issue:** `references/core-api.md:419` documents `Spaced`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/spaced/Spaced.tsx:63` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Spaced` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/spaced/Spaced.tsx:63`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Spaced` at references/core-api.md:419.

### GAP-065: Stale documentation: Span

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:413
**Export:** Span

**Issue:** `references/core-api.md:413` documents `Span`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/Span.tsx:6` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Span` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/Span.tsx:6`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Span` at references/core-api.md:413.

### GAP-066: Stale documentation: StoryIndexGenerator

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:441
**Export:** StoryIndexGenerator

**Issue:** `references/core-api.md:441` documents `StoryIndexGenerator`, which the entry point `code/core/src/core-server/index.ts` exports and `code/core/src/core-server/utils/StoryIndexGenerator.ts:101` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `StoryIndexGenerator` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/core-server/utils/StoryIndexGenerator.ts:101`, where it is defined, since its `scope.exclude` glob `code/core/src/core-server/**` matches that file. To keep its documentation, narrow `code/core/src/core-server/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `StoryIndexGenerator` at references/core-api.md:441.

### GAP-067: Stale documentation: StorybookIcon

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:420
**Export:** StorybookIcon

**Issue:** `references/core-api.md:420` documents `StorybookIcon`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/brand/StorybookIcon.tsx:3` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `StorybookIcon` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/brand/StorybookIcon.tsx:3`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `StorybookIcon` at references/core-api.md:420.

### GAP-068: Stale documentation: StorybookLogo

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:420
**Export:** StorybookLogo

**Issue:** `references/core-api.md:420` documents `StorybookLogo`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/brand/StorybookLogo.tsx:7` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `StorybookLogo` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/brand/StorybookLogo.tsx:7`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `StorybookLogo` at references/core-api.md:420.

### GAP-069: Stale documentation: SyntaxHighlighter

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:419
**Export:** SyntaxHighlighter

**Issue:** `references/core-api.md:419` documents `SyntaxHighlighter`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/syntaxhighlighter/lazy-syntaxhighlighter.tsx:52` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `SyntaxHighlighter` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/syntaxhighlighter/lazy-syntaxhighlighter.tsx:52`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `SyntaxHighlighter` at references/core-api.md:419.

### GAP-070: Stale documentation: TabBar

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:416
**Export:** TabBar

**Issue:** `references/core-api.md:416` documents `TabBar`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Tabs/Tabs.tsx:61` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `TabBar` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Tabs/Tabs.tsx:61`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `TabBar` at references/core-api.md:416.

### GAP-071: Stale documentation: TabButton

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:416
**Export:** TabButton

**Issue:** `references/core-api.md:416` documents `TabButton`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Tabs/Button.tsx:139` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `TabButton` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Tabs/Button.tsx:139`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `TabButton` at references/core-api.md:416.

### GAP-072: Stale documentation: TabList

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:416
**Export:** TabList

**Issue:** `references/core-api.md:416` documents `TabList`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Tabs/TabList.tsx:150` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `TabList` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Tabs/TabList.tsx:150`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `TabList` at references/core-api.md:416.

### GAP-073: Stale documentation: TabPanel

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:416
**Export:** TabPanel

**Issue:** `references/core-api.md:416` documents `TabPanel`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Tabs/TabPanel.tsx:34` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `TabPanel` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Tabs/TabPanel.tsx:34`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `TabPanel` at references/core-api.md:416.

### GAP-074: Stale documentation: TabWrapper

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:416
**Export:** TabWrapper

**Issue:** `references/core-api.md:416` documents `TabWrapper`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Tabs/Tabs.tsx:120` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `TabWrapper` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Tabs/Tabs.tsx:120`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `TabWrapper` at references/core-api.md:416.

### GAP-075: Stale documentation: Table

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:413
**Export:** Table

**Issue:** `references/core-api.md:413` documents `Table`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/Table.tsx:6` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Table` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/Table.tsx:6`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Table` at references/core-api.md:413.

### GAP-076: Stale documentation: Tabs

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:416
**Export:** Tabs

**Issue:** `references/core-api.md:416` documents `Tabs`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Tabs/Tabs.tsx:188` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Tabs` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Tabs/Tabs.tsx:188`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Tabs` at references/core-api.md:416.

### GAP-077: Stale documentation: TabsView

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:416
**Export:** TabsView

**Issue:** `references/core-api.md:416` documents `TabsView`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Tabs/TabsView.tsx:106` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `TabsView` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Tabs/TabsView.tsx:106`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `TabsView` at references/core-api.md:416.

### GAP-080: Stale documentation: ToggleButton

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:414
**Export:** ToggleButton

**Issue:** `references/core-api.md:414` documents `ToggleButton`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/ToggleButton/ToggleButton.tsx:16` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `ToggleButton` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/ToggleButton/ToggleButton.tsx:16`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `ToggleButton` at references/core-api.md:414.

### GAP-081: Stale documentation: Toolbar

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:418
**Export:** Toolbar

**Issue:** `references/core-api.md:418` documents `Toolbar`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Toolbar/Toolbar.tsx:36` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Toolbar` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Toolbar/Toolbar.tsx:36`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Toolbar` at references/core-api.md:418.

### GAP-082: Stale documentation: Tooltip

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:417
**Export:** Tooltip

**Issue:** `references/core-api.md:417` documents `Tooltip`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/tooltip/Tooltip.tsx:7` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Tooltip` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/tooltip/Tooltip.tsx:7`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Tooltip` at references/core-api.md:417.

### GAP-083: Stale documentation: TooltipLinkList

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:417
**Export:** TooltipLinkList

**Issue:** `references/core-api.md:417` documents `TooltipLinkList`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/tooltip/TooltipLinkList.tsx:70` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `TooltipLinkList` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/tooltip/TooltipLinkList.tsx:70`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `TooltipLinkList` at references/core-api.md:417.

### GAP-084: Stale documentation: TooltipNote

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:417
**Export:** TooltipNote

**Issue:** `references/core-api.md:417` documents `TooltipNote`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/tooltip/TooltipNote.tsx:23` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `TooltipNote` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/tooltip/TooltipNote.tsx:23`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `TooltipNote` at references/core-api.md:417.

### GAP-085: Stale documentation: UL

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:413
**Export:** UL

**Issue:** `references/core-api.md:413` documents `UL`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/UL.tsx:16` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `UL` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/UL.tsx:16`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `UL` at references/core-api.md:413.

### GAP-086: Stale documentation: WebsocketTransport

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:431
**Export:** WebsocketTransport

**Issue:** `references/core-api.md:431` documents `WebsocketTransport`, which the entry point `code/core/src/channels/index.ts` exports and `code/core/src/channels/websocket/index.ts:23` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `WebsocketTransport` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/channels/websocket/index.ts:23`, where it is defined, since its `scope.exclude` glob `code/core/src/channels/**` matches that file. To keep its documentation, narrow `code/core/src/channels/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `WebsocketTransport` at references/core-api.md:431.

### GAP-087: Stale documentation: WithTooltip

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:417
**Export:** WithTooltip

**Issue:** `references/core-api.md:417` documents `WithTooltip`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/tooltip/lazy-WithTooltip.tsx:8` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `WithTooltip` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/tooltip/lazy-WithTooltip.tsx:8`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `WithTooltip` at references/core-api.md:417.

### GAP-088: Stale documentation: Zoom

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:419
**Export:** Zoom

**Issue:** `references/core-api.md:419` documents `Zoom`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Zoom/Zoom.tsx:4` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Zoom` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Zoom/Zoom.tsx:4`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Zoom` at references/core-api.md:419.

### GAP-089: Stale documentation: addToGlobalContext

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:437
**Export:** addToGlobalContext

**Issue:** `references/core-api.md:437` documents `addToGlobalContext`, which the entry point `code/core/src/telemetry/index.ts` exports and `code/core/src/telemetry/telemetry.ts:26` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `addToGlobalContext` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/telemetry/telemetry.ts:26`, where it is defined, since its `scope.exclude` glob `code/core/src/telemetry/**` matches that file. To keep its documentation, narrow `code/core/src/telemetry/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `addToGlobalContext` at references/core-api.md:437.

### GAP-090: Stale documentation: automock

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:440
**Export:** automock

**Issue:** SKILL.md documents `automock`, which the enumerated source API surface lacks

**Remediation:** Check `automock` against the source and update or remove its documentation at references/core-api.md:440: the enumerated source surface does not export it.

### GAP-091: Stale documentation: colors

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:258
**Export:** colors

**Issue:** `references/core-api.md:258` documents `colors`, which the entry point `code/core/src/node-logger/index.ts` exports and `code/core/src/node-logger/index.ts:57` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `colors` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/node-logger/index.ts:57`, where it is defined, since its `scope.exclude` glob `code/core/src/node-logger/**` matches that file. To keep its documentation, narrow `code/core/src/node-logger/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `colors` at references/core-api.md:258.

### GAP-092: Stale documentation: componentTransform

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:438
**Export:** componentTransform

**Issue:** `references/core-api.md:438` documents `componentTransform`, which the entry point `code/core/src/csf-tools/index.ts` exports and `code/core/src/csf-tools/vitest-plugin/component-transformer.ts:285` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `componentTransform` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/csf-tools/vitest-plugin/component-transformer.ts:285`, where it is defined, since its `scope.exclude` glob `code/core/src/csf-tools/**` matches that file. To keep its documentation, narrow `code/core/src/csf-tools/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `componentTransform` at references/core-api.md:438.

### GAP-093: Stale documentation: createBrowserChannel

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:431
**Export:** createBrowserChannel

**Issue:** `references/core-api.md:431` documents `createBrowserChannel`, which the entry point `code/core/src/channels/index.ts` exports and `code/core/src/channels/index.ts:32` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `createBrowserChannel` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/channels/index.ts:32`, where it is defined, since its `scope.exclude` glob `code/core/src/channels/**` matches that file. To keep its documentation, narrow `code/core/src/channels/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `createBrowserChannel` at references/core-api.md:431.

### GAP-094: Stale documentation: enrichCsf

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:438
**Export:** enrichCsf

**Issue:** `references/core-api.md:438` documents `enrichCsf`, which the entry point `code/core/src/csf-tools/index.ts` exports and `code/core/src/csf-tools/enrichCsf.ts:144` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `enrichCsf` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/csf-tools/enrichCsf.ts:144`, where it is defined, since its `scope.exclude` glob `code/core/src/csf-tools/**` matches that file. To keep its documentation, narrow `code/core/src/csf-tools/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `enrichCsf` at references/core-api.md:438.

### GAP-095: Stale documentation: experimental_loadStorybook

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:441
**Export:** experimental_loadStorybook

**Issue:** `references/core-api.md:441` documents `experimental_loadStorybook`, which the entry point `code/core/src/core-server/index.ts` exports and `code/core/src/core-server/load.ts:18` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `experimental_loadStorybook` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/core-server/load.ts:18`, where it is defined, since its `scope.exclude` glob `code/core/src/core-server/**` matches that file. To keep its documentation, narrow `code/core/src/core-server/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `experimental_loadStorybook` at references/core-api.md:441.

### GAP-096: Stale documentation: extract

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/addons.md:125
**Export:** extract

**Issue:** SKILL.md documents `extract`, which the enumerated source API surface lacks

**Remediation:** Check `extract` against the source and update or remove its documentation at references/addons.md:125: the enumerated source surface does not export it.

### GAP-097: Stale documentation: generate

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:14
**Export:** generate

**Issue:** `SKILL.md:14` documents `generate`, which the entry point `code/core/src/babel/index.ts` exports and `code/core/src/babel/index.ts:38` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `generate` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/babel/index.ts:38`, where it is defined, since its `scope.exclude` glob `code/core/src/babel/**` matches that file. To keep its documentation, narrow `code/core/src/babel/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `generate` at SKILL.md:14.

### GAP-098: Stale documentation: generateStoryFile

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:441
**Export:** generateStoryFile

**Issue:** `references/core-api.md:441` documents `generateStoryFile`, which the entry point `code/core/src/core-server/index.ts` exports and `code/core/src/core-server/utils/generate-story.ts:64` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `generateStoryFile` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/core-server/utils/generate-story.ts:64`, where it is defined, since its `scope.exclude` glob `code/core/src/core-server/**` matches that file. To keep its documentation, narrow `code/core/src/core-server/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `generateStoryFile` at references/core-api.md:441.

### GAP-099: Stale documentation: getSessionId

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:437
**Export:** getSessionId

**Issue:** `references/core-api.md:437` documents `getSessionId`, which the entry point `code/core/src/telemetry/index.ts` exports and `code/core/src/telemetry/session-id.ts:18` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `getSessionId` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/telemetry/session-id.ts:18`, where it is defined, since its `scope.exclude` glob `code/core/src/telemetry/**` matches that file. To keep its documentation, narrow `code/core/src/telemetry/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `getSessionId` at references/core-api.md:437.

### GAP-100: Stale documentation: getStoryHref

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:419
**Export:** getStoryHref

**Issue:** `references/core-api.md:419` documents `getStoryHref`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/utils/getStoryHref.ts:15` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `getStoryHref` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/utils/getStoryHref.ts:15`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `getStoryHref` at references/core-api.md:419.

### GAP-101: Stale documentation: getStorySortParameter

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:438
**Export:** getStorySortParameter

**Issue:** `references/core-api.md:438` documents `getStorySortParameter`, which the entry point `code/core/src/csf-tools/index.ts` exports and `code/core/src/csf-tools/getStorySortParameter.ts:96` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `getStorySortParameter` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/csf-tools/getStorySortParameter.ts:96`, where it is defined, since its `scope.exclude` glob `code/core/src/csf-tools/**` matches that file. To keep its documentation, narrow `code/core/src/csf-tools/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `getStorySortParameter` at references/core-api.md:438.

### GAP-102: Stale documentation: getStorybookMetadata

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:437
**Export:** getStorybookMetadata

**Issue:** `references/core-api.md:437` documents `getStorybookMetadata`, which the entry point `code/core/src/telemetry/index.ts` exports and `code/core/src/telemetry/storybook-metadata.ts:312` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `getStorybookMetadata` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/telemetry/storybook-metadata.ts:312`, where it is defined, since its `scope.exclude` glob `code/core/src/telemetry/**` matches that file. To keep its documentation, narrow `code/core/src/telemetry/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `getStorybookMetadata` at references/core-api.md:437.

### GAP-103: Stale documentation: logTracker

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:436
**Export:** logTracker

**Issue:** `references/core-api.md:436` documents `logTracker`, which the entry point `code/core/src/node-logger/index.ts` exports and `code/core/src/node-logger/logger/log-tracker.ts:95` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `logTracker` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/node-logger/logger/log-tracker.ts:95`, where it is defined, since its `scope.exclude` glob `code/core/src/node-logger/**` matches that file. To keep its documentation, narrow `code/core/src/node-logger/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `logTracker` at references/core-api.md:436.

### GAP-104: Stale documentation: prompt

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:436
**Export:** prompt

**Issue:** `references/core-api.md:436` documents `prompt`, which the entry point `code/core/src/node-logger/index.ts` exports and `code/core/src/node-logger/prompts/index.ts:5` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `prompt` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/node-logger/prompts/index.ts:5`, where it is defined, since its `scope.exclude` glob `code/core/src/node-logger/**` matches that file. To keep its documentation, narrow `code/core/src/node-logger/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `prompt` at references/core-api.md:436.

### GAP-105: Stale documentation: redirect

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:440
**Export:** redirect

**Issue:** SKILL.md documents `redirect`, which the enumerated source API surface lacks

**Remediation:** Check `redirect` against the source and update or remove its documentation at references/core-api.md:440: the enumerated source surface does not export it.

### GAP-106: Stale documentation: resolve

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:214
**Export:** resolve

**Issue:** SKILL.md documents `resolve`, which the enumerated source API surface lacks

**Remediation:** Check `resolve` against the source and update or remove its documentation at references/core-api.md:214: the enumerated source surface does not export it.

### GAP-107: Stale documentation: runtime

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:14
**Export:** runtime

**Issue:** SKILL.md documents `runtime`, which the enumerated source API surface lacks

**Remediation:** Check `runtime` against the source and update or remove its documentation at references/core-api.md:14: the enumerated source surface does not export it.

### GAP-108: Stale documentation: telemetry

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:437
**Export:** telemetry

**Issue:** `references/core-api.md:437` documents `telemetry`, which the entry point `code/core/src/telemetry/index.ts` exports and `code/core/src/telemetry/index.ts:31` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `telemetry` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/telemetry/index.ts:31`, where it is defined, since its `scope.exclude` glob `code/core/src/telemetry/**` matches that file. To keep its documentation, narrow `code/core/src/telemetry/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `telemetry` at references/core-api.md:437.

### GAP-109: Stale documentation: traverse

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:443
**Export:** traverse

**Issue:** `references/core-api.md:443` documents `traverse`, which the entry point `code/core/src/babel/index.ts` exports and `code/core/src/babel/index.ts:39` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `traverse` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/babel/index.ts:39`, where it is defined, since its `scope.exclude` glob `code/core/src/babel/**` matches that file. To keep its documentation, narrow `code/core/src/babel/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `traverse` at references/core-api.md:443.

### GAP-110: Stale documentation: useTabsState

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:416
**Export:** useTabsState

**Issue:** `references/core-api.md:416` documents `useTabsState`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Tabs/TabsView.tsx:30` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `useTabsState` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Tabs/TabsView.tsx:30`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `useTabsState` at references/core-api.md:416.

### GAP-111: Stale documentation: vitestTransform

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:438
**Export:** vitestTransform

**Issue:** `references/core-api.md:438` documents `vitestTransform`, which the entry point `code/core/src/csf-tools/index.ts` exports and `code/core/src/csf-tools/vitest-plugin/transformer.ts:108` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `vitestTransform` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/csf-tools/vitest-plugin/transformer.ts:108`, where it is defined, since its `scope.exclude` glob `code/core/src/csf-tools/**` matches that file. To keep its documentation, narrow `code/core/src/csf-tools/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `vitestTransform` at references/core-api.md:438.

### GAP-112: metadata drift — barrel export counts diverge

**Severity:** Medium
**Category:** Coverage (metadata-drift)
**Source:** skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/metadata.json

**Issue:** stats.exports_public_api=1335, exports[].length=88 → 93% drift

**Remediation:** Re-run Create Skill, which rebuilds `exports[]` and `stats.exports_public_api` in `skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/metadata.json` from the source. Update Skill does not repair this drift: each time it writes the skill it recounts `stats.exports_public_api` from the source and keeps `exports[]`, adding or dropping only the names its provenance map changes, so a metadata patch does not hold.

### GAP-002: Signature mismatch: withThemeByClassName (form 2 of 4)

**Severity:** Low
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/themes/src/decorators/class-name.decorator.tsx:19
**Export:** withThemeByClassName

**Issue:** documented `(config: ClassNameStrategyConfiguration) => DecoratorFunction<R>`, source `<TRenderer extends Renderer = Renderer>({ themes, defaultTheme, parentSelector = DEFAULT_ELEMENT_SELECTOR }: ClassNameStrategyConfiguration): DecoratorFunction<TRenderer>`: the documented parameter is named `config`; the source's one parameter is a destructuring pattern of the same type ClassNameStrategyConfiguration (types, order, optionality and return type equal) (only the parameter names differ, and a caller of a `.tsx` file passes its arguments by position) (documented form 2 of 4: `(config: ClassNameStrategyConfiguration) -> DecoratorFunction<R>`)

**Remediation:** Update the documented signature of `withThemeByClassName` from `(config: ClassNameStrategyConfiguration) => DecoratorFunction<R>` to `<TRenderer extends Renderer = Renderer>({ themes, defaultTheme, parentSelector = DEFAULT_ELEMENT_SELECTOR }: ClassNameStrategyConfiguration): DecoratorFunction<TRenderer>`, the signature the source defines at `code/addons/themes/src/decorators/class-name.decorator.tsx:19`.

### GAP-003: Signature mismatch: withThemeByDataAttribute (form 1 of 3)

**Severity:** Low
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/themes/src/decorators/data-attribute.decorator.tsx:19
**Export:** withThemeByDataAttribute

**Issue:** documented `(config: DataAttributeStrategyConfiguration) => DecoratorFunction<R>`, source `<TRenderer extends Renderer = any>({ themes, defaultTheme, parentSelector = DEFAULT_ELEMENT_SELECTOR, attributeName = DEFAULT_DATA_ATTRIBUTE }: DataAttributeStrategyConfiguration): DecoratorFunction<TRenderer>`: the documented parameter is named `config`; the source's one parameter is a destructuring pattern of the same type DataAttributeStrategyConfiguration (types, order, optionality and return type equal) (only the parameter names differ, and a caller of a `.tsx` file passes its arguments by position) (documented form 1 of 3: `(config: DataAttributeStrategyConfiguration) -> DecoratorFunction<R>`)

**Remediation:** Update the documented signature of `withThemeByDataAttribute` from `(config: DataAttributeStrategyConfiguration) => DecoratorFunction<R>` to `<TRenderer extends Renderer = any>({ themes, defaultTheme, parentSelector = DEFAULT_ELEMENT_SELECTOR, attributeName = DEFAULT_DATA_ATTRIBUTE }: DataAttributeStrategyConfiguration): DecoratorFunction<TRenderer>`, the signature the source defines at `code/addons/themes/src/decorators/data-attribute.decorator.tsx:19`.

### GAP-004: Signature mismatch: withThemeFromJSXProvider (form 1 of 2)

**Severity:** Low
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/themes/src/decorators/provider.decorator.tsx:23
**Export:** withThemeFromJSXProvider

**Issue:** documented `(config: ProviderStrategyConfiguration) => DecoratorFunction<R>`, source `<TRenderer extends Renderer = any>({ Provider, GlobalStyles, defaultTheme, themes = {} }: ProviderStrategyConfiguration): DecoratorFunction<TRenderer>`: the documented parameter is named `config`; the source's one parameter is a destructuring pattern of the same type ProviderStrategyConfiguration (types, order, optionality and return type equal) (only the parameter names differ, and a caller of a `.tsx` file passes its arguments by position) (documented form 1 of 2: `(config: ProviderStrategyConfiguration) -> DecoratorFunction<R>`)

**Remediation:** Update the documented signature of `withThemeFromJSXProvider` from `(config: ProviderStrategyConfiguration) => DecoratorFunction<R>` to `<TRenderer extends Renderer = any>({ Provider, GlobalStyles, defaultTheme, themes = {} }: ProviderStrategyConfiguration): DecoratorFunction<TRenderer>`, the signature the source defines at `code/addons/themes/src/decorators/provider.decorator.tsx:23`.

### GAP-006: Signature mismatch: DecoratorFunction

**Severity:** Low
**Category:** Coverage (signature-mismatch)
**Source:** code/core/src/csf/story.ts:331
**Export:** DecoratorFunction

**Issue:** documented `(storyFn: PartialStoryFn<R, Args>, context: StoryContext<R, Args>) => R['storyResult']`, source `export type DecoratorFunction<TRenderer extends Renderer = Renderer, TArgs = Args> = (fn: PartialStoryFn<TRenderer, TArgs>, c: StoryContext<TRenderer, TArgs>) => TRenderer['storyResult']`: the documented parameters are named storyFn and context; the source names them fn and c (types, with the type variables renamed consistently, order and return type equal); the closest candidate is code/core/src/csf/story.ts:331, the other candidate code/core/src/actions/models/DecoratorFunction.ts:1 being (args: any[]) => any[] (only the parameter names differ, and a caller of a `.ts` file passes its arguments by position)

**Remediation:** Update the documented signature of `DecoratorFunction` from `(storyFn: PartialStoryFn<R, Args>, context: StoryContext<R, Args>) => R['storyResult']` to `export type DecoratorFunction<TRenderer extends Renderer = Renderer, TArgs = Args> = (fn: PartialStoryFn<TRenderer, TArgs>, c: StoryContext<TRenderer, TArgs>) => TRenderer['storyResult']`, the signature the source defines at `code/core/src/csf/story.ts:331`.

### GAP-007: Signature mismatch: normalizeProjectAnnotations

**Severity:** Low
**Category:** Coverage (signature-mismatch)
**Source:** code/core/src/preview-api/modules/store/csf/normalizeProjectAnnotations.ts:17
**Export:** normalizeProjectAnnotations

**Issue:** documented `(annotations: ProjectAnnotations<R>) => NormalizedProjectAnnotations<R>`, source `normalizeProjectAnnotations<TRenderer extends Renderer>({ argTypes, argTypesEnhancers, decorators, loaders, beforeEach, afterEach, initialGlobals, ...annotations }: ProjectAnnotations<TRenderer>): NormalizedProjectAnnotations<TRenderer>`: the documented parameter is named `annotations`; the source's one parameter is a destructuring pattern of the same type ProjectAnnotations<TRenderer> (types, order, optionality and return type equal) (only the parameter names differ, and a caller of a `.ts` file passes its arguments by position)

**Remediation:** Update the documented signature of `normalizeProjectAnnotations` from `(annotations: ProjectAnnotations<R>) => NormalizedProjectAnnotations<R>` to `normalizeProjectAnnotations<TRenderer extends Renderer>({ argTypes, argTypesEnhancers, decorators, loaders, beforeEach, afterEach, initialGlobals, ...annotations }: ProjectAnnotations<TRenderer>): NormalizedProjectAnnotations<TRenderer>`, the signature the source defines at `code/core/src/preview-api/modules/store/csf/normalizeProjectAnnotations.ts:17`.

### GAP-008: Signature mismatch: sanitizeStoryContextUpdate

**Severity:** Low
**Category:** Coverage (signature-mismatch)
**Source:** code/core/src/preview-api/modules/store/decorators.ts:30
**Export:** sanitizeStoryContextUpdate

**Issue:** documented `(inputContextUpdate?: StoryContextUpdate) => StoryContextUpdate`, source `sanitizeStoryContextUpdate({ componentId, title, kind, id, name, story, parameters, initialArgs, argTypes, ...update }: StoryContextUpdate = {}): StoryContextUpdate`: the documented parameter is named `inputContextUpdate`; the source's one parameter is a destructuring pattern of the same type StoryContextUpdate, optional by its default `{}` (types, order, optionality and return type equal) (only the parameter names differ, and a caller of a `.ts` file passes its arguments by position)

**Remediation:** Update the documented signature of `sanitizeStoryContextUpdate` from `(inputContextUpdate?: StoryContextUpdate) => StoryContextUpdate` to `sanitizeStoryContextUpdate({ componentId, title, kind, id, name, story, parameters, initialArgs, argTypes, ...update }: StoryContextUpdate = {}): StoryContextUpdate`, the signature the source defines at `code/core/src/preview-api/modules/store/decorators.ts:30`.

### GAP-001: Partial signature: Story

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/docs/src/blocks/blocks/Story.tsx:134
**Export:** Story

**Issue:** the skill labels its documented form of `Story` partial, and it leaves out only members the source marks optional: documented `{ of?, meta?, inline?, height?, autoplay? }`, source `export const Story = withMdxComponentOverride('Story', StoryImpl); StoryImpl: FC<StoryProps>, StoryProps = StoryRefProps & StoryParameters = { of?: ModuleExport; meta?: ModuleExports } & { inline?: boolean; height?: string; autoplay?: boolean; __forceInitialArgs?: boolean; __primary?: boolean } (Story.tsx:21-60)`: the documented props list leaves out the optional own props __forceInitialArgs? and __primary? of StoryProps

**Remediation:** No change: the documented form of `Story` is labelled partial and leaves out only optional members of the signature the source defines at `code/addons/docs/src/blocks/blocks/Story.tsx:134`.

### GAP-038: Documented extra: DecoratorHelpers

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/themes/src/decorators/index.ts:5
**Export:** DecoratorHelpers

**Issue:** `references/addons.md:121` documents `DecoratorHelpers`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `DecoratorHelpers` is a documented extra, a name the source still declares at `code/addons/themes/src/decorators/index.ts:5` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-046: Documented extra: HighlightParameters

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/highlight/types.ts:7
**Export:** HighlightParameters

**Issue:** `references/core-api.md:326` documents `HighlightParameters`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `HighlightParameters` is a documented extra, a name the source still declares at `code/core/src/highlight/types.ts:7` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-058: Documented extra: ReactParameters

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/renderers/react/src/types.ts:19
**Export:** ReactParameters

**Issue:** `references/story-types.md:326` documents `ReactParameters`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ReactParameters` is a documented extra, a name the source still declares at `code/renderers/react/src/types.ts:19` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-062: Documented extra: Selection

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/preview-api/modules/preview-web/SelectionStore.ts:12
**Export:** Selection

**Issue:** `references/core-api.md:143` documents `Selection`, which the enumerated source API surface lacks and the source still declares; of the 4 files that declare it, the skill cites only `code/core/src/preview-api/modules/preview-web/SelectionStore.ts`

**Remediation:** No change: `Selection` is a documented extra, a name the source still declares at `code/core/src/preview-api/modules/preview-web/SelectionStore.ts:12` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-063: Documented extra: SelectionSpecifier

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/preview-api/modules/preview-web/SelectionStore.ts:5
**Export:** SelectionSpecifier

**Issue:** `references/core-api.md:143` documents `SelectionSpecifier`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `SelectionSpecifier` is a documented extra, a name the source still declares at `code/core/src/preview-api/modules/preview-web/SelectionStore.ts:5` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-078: Documented extra: ThemeAddonState

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/themes/src/types.ts:1
**Export:** ThemeAddonState

**Issue:** `references/addons.md:114` documents `ThemeAddonState`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ThemeAddonState` is a documented extra, a name the source still declares at `code/addons/themes/src/types.ts:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-079: Documented extra: ThemesParameters

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/themes/src/types.ts:6
**Export:** ThemesParameters

**Issue:** `references/addons.md:115` documents `ThemesParameters`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ThemesParameters` is a documented extra, a name the source still declares at `code/addons/themes/src/types.ts:6` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-113: multi-denominator reporting — barrel vs documented surface

**Severity:** Info
**Category:** Coverage (multi-denominator)
**Source:** skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/metadata.json

**Issue:** barrel=1335, documented=365

**Remediation:** No action required: the barrel and the documented surface measure different sets by design, and the report records both counts.

### GAP-114: Provenance line not verified for default

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/vitest/src/vitest-plugin/index.ts:531
**Export:** default

**Issue:** the line-check rules found no definition line for `default` in `code/addons/vitest/src/vitest-plugin/index.ts`; check by hand

**Remediation:** Open `code/addons/vitest/src/vitest-plugin/index.ts` and confirm that line 531 defines `default`; if another line does, set the provenance `source_line` to it.

### GAP-115: Not checked by script: HooksContext

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/core-api.md:98
**Export:** HooksContext

**Issue:** The row labels `HooksContext` a type ("Hooks context shape"); `storybook/preview-api` exports it as a class, `export class HooksContext<TRenderer extends Renderer, TArgs extends Args = Args>` (code/core/src/preview-api/modules/addons/hooks.ts:36), re-exported as a value at code/core/src/preview-api/index.ts:17.

**Remediation:** Correct the documentation to match the source; no script checks this. In references/core-api.md:98, label `HooksContext` a class, citing code/core/src/preview-api/modules/addons/hooks.ts:36.

### GAP-116: Not checked by script: DocsContext

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/core-api.md:99
**Export:** DocsContext

**Issue:** The row labels `storybook/preview-api`'s `DocsContext` a type ("Autodocs rendering context"); the entry re-exports a class, `export class DocsContext<TRenderer extends Renderer> implements DocsContextProps<TRenderer>` (code/core/src/preview-api/modules/preview-web/docs-context/DocsContext.ts:20), through code/core/src/preview-api/index.ts:41.

**Remediation:** Correct the documentation to match the source; no script checks this. In references/core-api.md:99, label `DocsContext` a class, citing code/core/src/preview-api/modules/preview-web/docs-context/DocsContext.ts:20.

### GAP-117: Not checked by script: PreviewWeb

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/core-api.md:100
**Export:** PreviewWeb

**Issue:** The row says the runtime `Preview` class "is aliased to `PreviewWeb` at `PreviewWeb.tsx:11`"; that line declares a distinct subclass, `export class PreviewWeb<TRenderer extends Renderer> extends PreviewWithSelection<TRenderer>` (code/core/src/preview-api/modules/preview-web/PreviewWeb.tsx:11), and `PreviewWithSelection` extends `Preview` (PreviewWithSelection.tsx:77).

**Remediation:** Correct the documentation to match the source; no script checks this. In references/core-api.md:100, say that `PreviewWeb` (PreviewWeb.tsx:11) extends `PreviewWithSelection` (PreviewWithSelection.tsx:77), which extends `Preview` (Preview.tsx:60), instead of calling it an alias.

### Discovery Quality

**Discovery Test:** not run: the hard gate blocked the run
