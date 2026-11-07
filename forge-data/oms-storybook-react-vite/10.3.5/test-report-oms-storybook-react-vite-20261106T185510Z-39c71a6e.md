---
workflowType: 'test-skill'
skillName: 'oms-storybook-react-vite'
skillDir: 'skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite'
runId: '20261106T185510Z-39c71a6e'
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
testDate: '2026-11-06T18:55:10Z'
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

**Mode Rationale:** metadata.json records `skill_type: 'single'`, an individual skill, so the run checks API-surface coverage (naive mode); coherence is structural only and is not a scored category.

**Analysis Plan:**
- Coverage Check: every documented export in SKILL.md and references/ against the public API surface of the pinned source tree (e486d38, v10.3.5), with AST-backed signature and type verification at Deep tier.
- Coherence Check: structural coherence of SKILL.md and its references (internal links, referenced files, section structure); no cross-skill integration checks in naive mode.

## Coverage Analysis

**Tier:** Deep
**Source Access:** full
**Source Path:** /home/armel/.skf/workspace/repos/github.com/storybookjs/storybook
**Workspace Layout:** npm-workspaces
**Denominator:** Stratified scope, denominator: tier_a_include union (124 files define its names, 370 exports union)

**Denominator Candidates** (stratified-scope audit trail):
- `stats.effective_denominator`: 280
- `scope.tier_a_include` union: 370    ← chosen (the barrel branch's set)
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
| `API_EventMap` | interface | yes | - | code/core/src/manager-api/root.tsx:318 | WARN |
| `API_KeyCollection` | type | yes | - | code/core/src/manager-api/modules/shortcuts.ts:99 | WARN |
| `ActionBar` | - | yes | - | - | WARN |
| `ActionDisplay` | interface | yes | - | code/core/src/actions/models/ActionDisplay.ts:3 | PASS |
| `ActionList` | - | yes | - | - | WARN |
| `ActionOptions` | type | yes | - | code/core/src/actions/models/ActionOptions.ts:11 | PASS |
| `ActionsFunction` | interface | yes | - | code/core/src/actions/models/ActionsFunction.ts:4 | PASS |
| `ActionsMap` | type | yes | - | code/core/src/actions/models/ActionsMap.ts:3 | PASS |
| `AddContext` | function | no | - | code/addons/docs/src/blocks/blocks/mdx.tsx:27 | WARN |
| `AddMocks` | type | no | - | code/renderers/react/src/public-types.ts:69 | WARN |
| `AddonPanel` | - | yes | - | - | WARN |
| `Anchor` | function | yes | yes | code/addons/docs/src/blocks/blocks/Anchor.tsx:10 | PASS |
| `AnchorMdx` | function | no | - | code/addons/docs/src/blocks/blocks/mdx.tsx:98 | WARN |
| `AnchorProps` | interface | yes | - | code/addons/docs/src/blocks/blocks/Anchor.tsx:6 | PASS |
| `Animation` | type | yes | - | code/core/src/theming/types.ts:60 | PASS |
| `ArgTypes` | const | yes | yes | code/addons/docs/src/blocks/blocks/ArgTypes.tsx:108 | PASS |
| `Args` | interface | yes | - | code/core/src/csf/story.ts:153 | WARN |
| `ArgsTableProps` | - | yes | - | - | WARN |
| `BabelFile` | - | yes | - | - | WARN |
| `Background` | type | yes | - | code/core/src/theming/types.ts:58 | PASS |
| `Badge` | - | yes | - | - | WARN |
| `Bar` | - | yes | - | - | WARN |
| `BaseProjectAnnotations` | - | yes | - | - | WARN |
| `Blockquote` | - | yes | - | - | WARN |
| `BooleanConfig` | interface | yes | - | code/addons/docs/src/blocks/controls/types.ts:14 | PASS |
| `BooleanControl` | function | yes | yes | code/addons/docs/src/blocks/controls/Boolean.tsx:117 | PASS |
| `BooleanProps` | type | yes | - | code/addons/docs/src/blocks/controls/Boolean.tsx:104 | PASS |
| `BooleanValue` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:13 | PASS |
| `Brand` | interface | yes | - | code/core/src/theming/types.ts:64 | PASS |
| `BuilderOptions` | type | yes | - | code/builders/builder-vite/src/types.ts:21 | PASS |
| `Button` | - | yes | - | - | WARN |
| `CHANNEL_CREATED` | - | yes | - | code/core/src/core-events/index.ts:112 | WARN |
| `CLEAR_ID` | const | no | - | code/core/src/actions/constants.ts:5 | WARN |
| `COMPONENT_TESTING_PANEL_ID` | const | yes | - | code/core/src/component-testing/constants.ts:2 | WARN |
| `CSFFile` | type | yes | - | code/core/src/types/modules/story.ts:92 | WARN |
| `CSSObject` | - | yes | - | - | WARN |
| `CYCLIC_KEY` | const | no | - | code/core/src/actions/constants.ts:6 | WARN |
| `CacheProvider` | - | yes | - | - | WARN |
| `CalledExtractOnStoreError` | class | yes | - | code/core/src/preview-errors.ts:77 | WARN |
| `CalledPreviewMethodBeforeInitializationError` | class | yes | - | code/core/src/preview-errors.ts:107 | WARN |
| `Canvas` | const | yes | yes | code/addons/docs/src/blocks/blocks/Canvas.tsx:100 | PASS |
| `CanvasProps` | - | yes | - | - | WARN |
| `Card` | - | yes | - | - | WARN |
| `Category` | enum | yes | - | code/core/src/manager-errors.ts:12 | WARN |
| `Channel` | - | yes | - | - | WARN |
| `CheckboxControl` | - | yes | - | - | WARN |
| `ClassNameStrategyConfiguration` | interface | yes | - | code/addons/themes/src/decorators/class-name.decorator.tsx:8 | PASS |
| `ClassNames` | - | yes | - | - | WARN |
| `ClickEventDetails` | interface | yes | - | code/core/src/highlight/types.ts:60 | PASS |
| `Code` | - | yes | - | - | WARN |
| `CodeOrSourceMdx` | function | no | - | code/addons/docs/src/blocks/blocks/mdx.tsx:39 | WARN |
| `Collapsible` | - | yes | - | - | WARN |
| `Color` | type | yes | - | code/core/src/theming/types.ts:57 | PASS |
| `ColorConfig` | interface | yes | - | code/addons/docs/src/blocks/controls/types.ts:18 | PASS |
| `ColorControl` | function | yes | yes | code/addons/docs/src/blocks/controls/index.tsx:14 | PASS |
| `ColorControlProps` | - | yes | - | - | WARN |
| `ColorItem` | function | yes | yes | code/addons/docs/src/blocks/components/ColorPalette.tsx:182 | PASS |
| `ColorPalette` | function | yes | yes | code/addons/docs/src/blocks/components/ColorPalette.tsx:202 | PASS |
| `ColorProps` | type | no | - | code/addons/docs/src/blocks/controls/index.tsx:10 | WARN |
| `ColorValue` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:16 | PASS |
| `Combo` | interface | yes | - | code/core/src/manager-api/root.tsx:116 | WARN |
| `Component` | type | no | - | code/addons/docs/src/blocks/blocks/types.ts:7 | WARN |
| `ComponentAnnotations` | interface | yes | - | code/core/src/csf/story.ts:452 | WARN |
| `ComponentEntry` | - | yes | - | - | WARN |
| `ConfigFile` | - | yes | - | - | WARN |
| `ContextObjectWithoutNode` | type | yes | - | code/addons/a11y/src/params.ts:6 | PASS |
| `ContextSpecWithoutNode` | type | yes | - | code/addons/a11y/src/params.ts:16 | PASS |
| `Control` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:82 | PASS |
| `ControlProps` | interface | yes | - | code/addons/docs/src/blocks/controls/types.ts:3 | PASS |
| `ControlType` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:71 | PASS |
| `Controls` | const | yes | yes | code/addons/docs/src/blocks/blocks/Controls.tsx:109 | PASS |
| `CsfFile` | - | yes | - | - | WARN |
| `DEFAULT_VIEWPORT` | const | no | - | code/core/src/viewport/defaults.ts:232 | WARN |
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
| `DescriptionType` | enum | no | - | code/addons/docs/src/blocks/blocks/Description.tsx:9 | WARN |
| `Div` | - | yes | - | - | WARN |
| `Docs` | function | yes | yes | code/addons/docs/src/blocks/blocks/Docs.tsx:17 | PASS |
| `DocsContainer` | function | yes | yes | code/addons/docs/src/blocks/blocks/DocsContainer.tsx:23 | PASS |
| `DocsContainerProps` | interface | yes | - | code/addons/docs/src/blocks/blocks/DocsContainer.tsx:18 | PASS |
| `DocsContext` | const | yes | - | code/addons/docs/src/blocks/blocks/DocsContext.ts:18 | PASS |
| `DocsEntry` | - | yes | - | - | WARN |
| `DocsPage` | function | yes | - | code/addons/docs/src/blocks/blocks/DocsPage.tsx:12 | PASS |
| `DocsProps` | type | yes | - | code/addons/docs/src/blocks/blocks/Docs.tsx:12 | PASS |
| `DocsRenderer` | class | yes | - | code/addons/docs/src/DocsRenderer.tsx:48 | PASS |
| `DocsStory` | const | yes | yes | code/addons/docs/src/blocks/blocks/DocsStory.tsx:42 | PASS |
| `DocsStoryProps` | type | yes | - | code/addons/docs/src/blocks/blocks/types.ts:9 | PASS |
| `DocsTypes` | interface | yes | - | code/addons/docs/src/types.ts:254 | PASS |
| `EVENT_ID` | const | no | - | code/core/src/actions/constants.ts:4 | WARN |
| `Easing` | type | no | - | code/core/src/theming/types.ts:61 | WARN |
| `EmptyIndexError` | class | yes | - | code/core/src/preview-errors.ts:161 | WARN |
| `ErrorFormatter` | - | yes | - | - | WARN |
| `ExternalDocs` | function | no | - | code/addons/docs/src/blocks/blocks/external/ExternalDocs.tsx:26 | WARN |
| `ExternalDocsContainer` | function | no | - | code/addons/docs/src/blocks/blocks/external/ExternalDocsContainer.tsx:12 | WARN |
| `ExternalDocsProps` | type | no | - | code/addons/docs/src/blocks/blocks/external/ExternalDocs.tsx:11 | WARN |
| `FULL_RUN_TRIGGERS` | const | yes | - | code/addons/vitest/src/constants.ts:61 | WARN |
| `FilesControl` | function | yes | yes | code/addons/docs/src/blocks/controls/Files.tsx:40 | PASS |
| `FilesControlProps` | interface | yes | - | code/addons/docs/src/blocks/controls/Files.tsx:11 | PASS |
| `FlexBar` | - | yes | - | - | WARN |
| `Form` | - | yes | - | - | WARN |
| `FrameworkOptions` | type | yes | - | code/frameworks/react-vite/src/types.ts:14 | PASS |
| `FunctionInterpolation` | type | yes | - | code/core/src/theming/index.ts:23 | PASS |
| `GLOBALS_UPDATED` | - | yes | - | code/core/src/core-events/index.ts:123 | WARN |
| `Global` | - | yes | - | - | WARN |
| `GlobalState` | type | yes | - | code/core/src/viewport/types.ts:16 | PASS |
| `GlobalStateUpdate` | type | no | - | code/core/src/viewport/types.ts:31 | WARN |
| `Globals` | interface | yes | - | code/core/src/csf/story.ts:165 | WARN |
| `GroupEntry` | - | yes | - | - | WARN |
| `H1` | - | yes | - | - | WARN |
| `H6` | - | yes | - | - | WARN |
| `HIGHLIGHT` | const | yes | - | code/core/src/highlight/constants.ts:3 | PASS |
| `HR` | - | yes | - | - | WARN |
| `HandlerFunction` | type | yes | - | code/core/src/actions/models/HandlerFunction.ts:1 | PASS |
| `HashEntry` | - | yes | - | - | WARN |
| `HeaderMdx` | function | no | - | code/addons/docs/src/blocks/blocks/mdx.tsx:215 | WARN |
| `HeadersMdx` | const | no | - | code/addons/docs/src/blocks/blocks/mdx.tsx:232 | WARN |
| `Heading` | const | yes | yes | code/addons/docs/src/blocks/blocks/Heading.tsx:33 | PASS |
| `HeadingProps` | interface | yes | - | code/addons/docs/src/blocks/blocks/Heading.tsx:11 | PASS |
| `HighlightMenuItem` | interface | yes | - | code/core/src/highlight/types.ts:24 | PASS |
| `HighlightOptions` | interface | yes | - | code/core/src/highlight/types.ts:41 | PASS |
| `HighlightTypes` | interface | no | - | code/core/src/highlight/types.ts:3 | WARN |
| `HooksContext` | class | yes | - | code/core/src/preview-api/modules/addons/hooks.ts:36 | PASS |
| `INITIAL_VIEWPORTS` | const | no | - | code/core/src/viewport/defaults.ts:3 | WARN |
| `INTERNAL_DEFAULT_PROJECT_ANNOTATIONS` | const | yes | - | code/renderers/react/src/portable-stories.tsx:58 | PASS |
| `IconButton` | - | yes | - | - | WARN |
| `IconGallery` | function | yes | yes | code/addons/docs/src/blocks/components/IconGallery.tsx:74 | PASS |
| `IconItem` | function | yes | yes | code/addons/docs/src/blocks/components/IconGallery.tsx:62 | PASS |
| `ImplicitActionsDuringRendering` | class | yes | - | code/core/src/preview-errors.ts:56 | WARN |
| `IncludeExcludeOptions` | interface | yes | - | code/core/src/csf/index.ts:38 | WARN |
| `IndexHash` | - | yes | - | - | WARN |
| `InitialViewportKeys` | type | yes | - | code/core/src/viewport/defaults.ts:230 | PASS |
| `Interpolation` | type | yes | - | code/core/src/theming/index.ts:24 | PASS |
| `InvalidFrameworkNameError` | class | yes | - | code/core/src/server-errors.ts:86 | WARN |
| `Keyframes` | - | yes | - | - | WARN |
| `LI` | - | yes | - | - | WARN |
| `LeafEntry` | - | yes | - | - | WARN |
| `Loader` | type | yes | - | code/renderers/react/src/public-types.ts:78 | PASS |
| `LoaderFunction` | type | yes | - | code/core/src/csf/story.ts:249 | WARN |
| `MINIMAL_VIEWPORTS` | const | no | - | code/core/src/viewport/defaults.ts:234 | WARN |
| `ManagerContext` | const | yes | - | code/core/src/manager-api/root.tsx:80 | WARN |
| `ManagerProviderProps` | type | yes | - | code/core/src/manager-api/root.tsx:121 | WARN |
| `Markdown` | const | yes | yes | code/addons/docs/src/blocks/blocks/Markdown.tsx:55 | PASS |
| `MarkdownProps` | - | yes | - | - | WARN |
| `MaybeMocked` | - | yes | - | - | WARN |
| `MdxFileWithNoCsfReferencesError` | class | yes | - | code/core/src/preview-errors.ts:145 | WARN |
| `Meta` | function | yes | yes | code/addons/docs/src/blocks/blocks/Meta.tsx:15 | PASS |
| `MetaProps` | - | yes | - | - | WARN |
| `MissingFrameworkFieldError` | class | yes | - | code/core/src/server-errors.ts:70 | WARN |
| `MissingRenderToCanvasError` | class | yes | - | code/core/src/preview-errors.ts:91 | WARN |
| `MissingStoryAfterHmrError` | class | yes | - | code/core/src/preview-errors.ts:39 | WARN |
| `MissingStoryFromCsfFileError` | class | yes | - | code/core/src/preview-errors.ts:192 | WARN |
| `Mock` | - | yes | - | - | WARN |
| `MockInstance` | - | yes | - | - | WARN |
| `MockUniversalStore` | class | yes | - | code/core/src/shared/universal-store/mock.ts:40 | WARN |
| `Modal` | - | yes | - | - | WARN |
| `MountMustBeDestructuredError` | class | yes | - | code/core/src/preview-errors.ts:226 | WARN |
| `NoRenderFunctionError` | class | yes | - | code/core/src/preview-errors.ts:256 | WARN |
| `NoStoryMatchError` | class | yes | - | code/core/src/preview-errors.ts:176 | WARN |
| `NoStoryMountedError` | class | yes | - | code/core/src/preview-errors.ts:269 | WARN |
| `NodePath` | - | yes | - | - | WARN |
| `NormalizedComponentAnnotations` | type | yes | - | code/core/src/types/modules/story.ts:66 | WARN |
| `NormalizedOptionsConfig` | interface | yes | - | code/addons/docs/src/blocks/controls/types.ts:62 | PASS |
| `NormalizedProjectAnnotations` | type | yes | - | code/core/src/types/modules/story.ts:55 | WARN |
| `NormalizedStoryAnnotations` | type | yes | - | code/core/src/types/modules/story.ts:78 | WARN |
| `NumberConfig` | interface | yes | - | code/addons/docs/src/blocks/controls/types.ts:32 | PASS |
| `NumberControl` | function | yes | yes | code/addons/docs/src/blocks/controls/Number.tsx:28 | PASS |
| `NumberProps` | - | yes | - | - | WARN |
| `NumberValue` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:31 | PASS |
| `NxProjectDetectedError` | class | yes | - | code/core/src/server-errors.ts:56 | WARN |
| `OL` | - | yes | - | - | WARN |
| `ObjectConfig` | interface | yes | - | code/addons/docs/src/blocks/controls/types.ts:41 | PASS |
| `ObjectControl` | function | yes | yes | code/addons/docs/src/blocks/controls/Object.tsx:166 | PASS |
| `ObjectProps` | type | yes | - | code/addons/docs/src/blocks/controls/Object.tsx:164 | PASS |
| `ObjectValue` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:40 | PASS |
| `Of` | type | no | - | code/addons/docs/src/blocks/blocks/useOf.ts:11 | WARN |
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
| `PANEL_ID` | const | no | - | code/core/src/actions/constants.ts:3 | WARN |
| `PARAM_KEY` | const | yes | - | code/addons/a11y/src/constants.ts:3 | PASS |
| `PREVIEW_INITIALIZED` | - | yes | - | code/core/src/core-events/index.ts:128 | WARN |
| `PRIMARY_STORY` | const | no | - | code/addons/docs/src/blocks/blocks/types.ts:3 | WARN |
| `Parameters` | interface | yes | - | code/core/src/csf/story.ts:32 | WARN |
| `Placeholder` | - | yes | - | - | WARN |
| `PlayFunction` | type | yes | - | code/core/src/csf/story.ts:302 | WARN |
| `Popover` | - | yes | - | - | WARN |
| `PopoverProvider` | - | yes | - | - | WARN |
| `PostMessageTransport` | - | yes | - | - | WARN |
| `Pre` | - | yes | - | - | WARN |
| `PreparedStory` | type | yes | - | code/core/src/types/modules/story.ts:99 | WARN |
| `PresetColor` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:17 | PASS |
| `Preview` | interface | yes | - | code/core/src/csf/csf-factories.ts:26 | PASS |
| `PreviewWeb` | class | yes | - | code/core/src/preview-api/modules/preview-web/PreviewWeb.tsx:11 | PASS |
| `PreviewWithSelection` | class | yes | - | code/core/src/preview-api/modules/preview-web/PreviewWithSelection.tsx:77 | PASS |
| `Primary` | const | yes | yes | code/addons/docs/src/blocks/blocks/Primary.tsx:16 | PASS |
| `ProjectAnnotations` | interface | yes | - | code/core/src/csf/story.ts:421 | WARN |
| `PropDescriptor` | type | yes | - | code/core/src/preview-api/modules/store/filterArgTypes.ts:5 | PASS |
| `ProviderStrategyConfiguration` | interface | yes | - | code/addons/themes/src/decorators/provider.decorator.tsx:13 | PASS |
| `PureArgsTable` | function | yes | yes | code/addons/docs/src/blocks/components/ArgsTable/ArgsTable.tsx:320 | PASS |
| `REMOVE_HIGHLIGHT` | const | yes | - | code/core/src/highlight/constants.ts:4 | PASS |
| `RESET_HIGHLIGHT` | const | yes | - | code/core/src/highlight/constants.ts:5 | PASS |
| `RadioControl` | - | yes | - | - | WARN |
| `RangeConfig` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:38 | PASS |
| `RangeControl` | function | yes | yes | code/addons/docs/src/blocks/controls/Range.tsx:178 | PASS |
| `RangeProps` | - | yes | - | - | WARN |
| `ReactMeta` | interface | yes | - | code/renderers/react/src/preview.tsx:147 | PASS |
| `ReactPreview` | interface | yes | - | code/renderers/react/src/preview.tsx:102 | PASS |
| `ReactRenderer` | interface | yes | - | code/renderers/react/src/types.ts:8 | PASS |
| `ReactStory` | interface | yes | - | code/renderers/react/src/preview.tsx:249 | PASS |
| `ReactTypes` | interface | no | - | code/renderers/react/src/types.ts:33 | WARN |
| `Refs` | - | yes | - | - | WARN |
| `RenderContext` | type | yes | - | code/core/src/types/modules/story.ts:129 | WARN |
| `RenderToCanvas` | type | yes | - | code/core/src/types/modules/story.ts:38 | WARN |
| `Report` | interface | no | - | code/core/src/preview-api/modules/store/reporter-api.ts:1 | WARN |
| `ReporterAPI` | class | no | - | code/core/src/preview-api/modules/store/reporter-api.ts:8 | WARN |
| `RootEntry` | - | yes | - | - | WARN |
| `SCROLL_INTO_VIEW` | const | yes | - | code/core/src/highlight/constants.ts:6 | PASS |
| `SELECT_STORY` | - | yes | - | code/core/src/core-events/index.ts:133 | WARN |
| `STORYBOOK_ADDON_TEST_CHANNEL` | const | yes | - | code/addons/vitest/src/constants.ts:13 | WARN |
| `STORY_PREPARED` | - | yes | - | code/core/src/core-events/index.ts:149 | WARN |
| `STORY_RENDERED` | - | yes | - | code/core/src/core-events/index.ts:151 | WARN |
| `STORY_SPECIFIED` | - | yes | - | code/core/src/core-events/index.ts:153 | WARN |
| `ScrollArea` | - | yes | - | - | WARN |
| `Select` | - | yes | - | - | WARN |
| `SelectControl` | - | yes | - | - | WARN |
| `SelectionStore` | interface | no | - | code/core/src/preview-api/modules/preview-web/SelectionStore.ts:17 | WARN |
| `SelectorWithoutNode` | type | yes | - | code/addons/a11y/src/params.ts:3 | PASS |
| `SeparatorOptions` | interface | yes | - | code/core/src/csf/index.ts:63 | WARN |
| `SortType` | type | yes | - | code/addons/docs/src/blocks/components/ArgsTable/ArgsTable.tsx:186 | PASS |
| `Source` | const | yes | yes | code/addons/docs/src/blocks/blocks/Source.tsx:181 | PASS |
| `SourceContainer` | function | no | - | code/addons/docs/src/blocks/blocks/SourceContainer.tsx:38 | WARN |
| `SourceContext` | const | no | - | code/addons/docs/src/blocks/blocks/SourceContainer.tsx:27 | WARN |
| `SourceContextProps` | interface | no | - | code/addons/docs/src/blocks/blocks/SourceContainer.tsx:22 | WARN |
| `SourceItem` | interface | no | - | code/addons/docs/src/blocks/blocks/SourceContainer.tsx:15 | WARN |
| `SourceParameters` | type | yes | - | code/addons/docs/src/blocks/blocks/Source.tsx:16 | PASS |
| `SourceProps` | type | yes | - | code/addons/docs/src/blocks/blocks/Source.tsx:28 | PASS |
| `Spaced` | - | yes | - | - | WARN |
| `Span` | - | yes | - | - | WARN |
| `State` | interface | yes | - | code/core/src/instrumenter/types.ts:72 | WARN |
| `StatusTypeIdMismatchError` | class | yes | - | code/core/src/manager-errors.ts:50 | WARN |
| `StoreOptions` | interface | yes | - | code/core/src/manager-api/store.ts:45 | WARN |
| `Stories` | const | yes | yes | code/addons/docs/src/blocks/blocks/Stories.tsx:74 | PASS |
| `StoriesHash` | - | yes | - | - | WARN |
| `Story` | const | yes | yes (Info) | code/addons/docs/src/blocks/blocks/Story.tsx:134 | WARN |
| `StoryAnnotations` | type | yes | - | code/core/src/csf/story.ts:543 | WARN |
| `StoryContext` | interface | yes | - | code/core/src/csf/story.ts:268 | PASS |
| `StoryEntry` | - | yes | - | - | WARN |
| `StoryFn` | type | yes | - | code/core/src/csf/story.ts:327 | PASS |
| `StoryIndexFetchError` | class | yes | - | code/core/src/preview-errors.ts:125 | WARN |
| `StoryIndexGenerator` | - | yes | - | - | WARN |
| `StoryObj` | type | yes | - | code/renderers/react/src/public-types.ts:47 | PASS |
| `StoryProps` | type | yes | - | code/addons/docs/src/blocks/blocks/Story.tsx:60 | PASS |
| `StorySources` | type | no | - | code/addons/docs/src/blocks/blocks/SourceContainer.tsx:20 | WARN |
| `StoryStore` | class | yes | - | code/core/src/preview-api/modules/store/StoryStore.ts:51 | PASS |
| `StoryStoreAccessedBeforeInitializationError` | class | yes | - | code/core/src/preview-errors.ts:211 | WARN |
| `StorybookConfig` | interface | yes | - | code/core/src/types/modules/core-common.ts:576 | PASS |
| `StorybookConfigVite` | type | yes | - | code/builders/builder-vite/src/types.ts:17 | PASS |
| `StorybookError` | class | yes | - | code/core/src/storybook-error.ts:25 | WARN |
| `StorybookIcon` | - | yes | - | - | WARN |
| `StorybookLogo` | - | yes | - | - | WARN |
| `StorybookParameters` | interface | yes | - | code/core/src/types/modules/csf.ts:75 | WARN |
| `StorybookTheme` | interface | yes | - | code/core/src/theming/types.ts:71 | PASS |
| `StrictArgs` | interface | yes | - | code/core/src/csf/story.ts:157 | WARN |
| `StyledComponent` | - | yes | - | - | WARN |
| `Subheading` | const | yes | yes | code/addons/docs/src/blocks/blocks/Subheading.tsx:23 | PASS |
| `Subtitle` | const | yes | yes | code/addons/docs/src/blocks/blocks/Subtitle.tsx:55 | PASS |
| `SubtitleProps` | - | yes | - | - | WARN |
| `SyntaxHighlighter` | - | yes | - | - | WARN |
| `TEST_PROVIDER_ID` | const | yes | - | code/addons/vitest/src/constants.ts:12 | WARN |
| `TOOL_ID` | const | no | - | code/core/src/viewport/constants.ts:4 | WARN |
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
| `TestRunResult` | type | yes | - | code/addons/vitest/src/constants.ts:81 | WARN |
| `TextConfig` | interface | yes | - | code/addons/docs/src/blocks/controls/types.ts:67 | PASS |
| `TextControl` | function | yes | yes | code/addons/docs/src/blocks/controls/Text.tsx:23 | PASS |
| `TextProps` | type | yes | - | code/addons/docs/src/blocks/controls/Text.tsx:11 | PASS |
| `TextSize` | type | yes | - | code/core/src/theming/types.ts:63 | PASS |
| `TextValue` | type | yes | - | code/addons/docs/src/blocks/controls/types.ts:66 | PASS |
| `Theme` | - | yes | - | - | WARN |
| `ThemeAddonState` | - | yes | - | - | WARN |
| `ThemeProvider` | - | yes | - | - | WARN |
| `ThemeVars` | interface | yes | - | code/core/src/theming/types.ts:4 | PASS |
| `ThemeVarsColors` | interface | yes | - | code/core/src/theming/types.ts:12 | PASS |
| `ThemeVarsPartial` | interface | yes | - | code/core/src/theming/types.ts:6 | PASS |
| `ThemesGlobals` | interface | yes | - | code/addons/themes/src/types.ts:20 | PASS |
| `ThemesParameters` | - | yes | - | - | WARN |
| `ThemesTypes` | interface | yes | - | code/addons/themes/src/types.ts:25 | PASS |
| `Title` | const | yes | yes | code/addons/docs/src/blocks/blocks/Title.tsx:55 | PASS |
| `TitleProps` | - | yes | - | - | WARN |
| `ToggleButton` | - | yes | - | - | WARN |
| `Toolbar` | - | yes | - | - | WARN |
| `Tooltip` | - | yes | - | - | WARN |
| `TooltipLinkList` | - | yes | - | - | WARN |
| `TooltipNote` | - | yes | - | - | WARN |
| `TriggerTestRunRequestPayload` | type | yes | - | code/addons/vitest/src/constants.ts:74 | WARN |
| `TriggerTestRunResponsePayload` | type | yes | - | code/addons/vitest/src/constants.ts:83 | WARN |
| `Typeset` | function | yes | yes | code/addons/docs/src/blocks/components/Typeset.tsx:50 | PASS |
| `Typography` | type | yes | - | code/core/src/theming/types.ts:59 | PASS |
| `UL` | - | yes | - | - | WARN |
| `UNKNOWN_ARGS_HASH` | const | no | - | code/addons/docs/src/blocks/blocks/SourceContainer.tsx:36 | WARN |
| `UPDATE_STORY_ARGS` | - | yes | - | code/core/src/core-events/index.ts:159 | WARN |
| `Unstyled` | const | yes | yes | code/addons/docs/src/blocks/blocks/Unstyled.tsx:9 | PASS |
| `UrlStore` | class | yes | - | code/core/src/preview-api/modules/preview-web/UrlStore.ts:94 | PASS |
| `UserEvent` | interface | no | - | code/core/src/test/testing-library.ts:119 | WARN |
| `UserEventObject` | type | no | - | code/core/src/test/index.ts:15 | WARN |
| `View` | interface | no | - | code/core/src/preview-api/modules/preview-web/View.ts:3 | WARN |
| `ViewMode` | type | yes | - | code/core/src/csf/story.ts:247 | WARN |
| `Viewport` | interface | no | - | code/core/src/viewport/types.ts:1 | WARN |
| `ViewportGlobals` | interface | no | - | code/core/src/viewport/types.ts:56 | WARN |
| `ViewportMap` | type | no | - | code/core/src/viewport/types.ts:14 | WARN |
| `ViewportParameters` | interface | yes | - | code/core/src/viewport/types.ts:33 | PASS |
| `ViewportStyles` | interface | yes | - | code/core/src/viewport/types.ts:9 | PASS |
| `ViewportType` | type | yes | - | code/core/src/viewport/types.ts:7 | PASS |
| `ViewportTypes` | interface | no | - | code/core/src/viewport/types.ts:65 | WARN |
| `ViteBuilder` | type | yes | - | code/builders/builder-vite/src/types.ts:10 | PASS |
| `ViteFinal` | type | yes | yes | code/builders/builder-vite/src/types.ts:12 | PASS |
| `WebRenderer` | interface | yes | - | code/core/src/types/modules/story.ts:28 | WARN |
| `WebView` | class | yes | - | code/core/src/preview-api/modules/preview-web/WebView.ts:42 | PASS |
| `WebsocketTransport` | - | yes | - | - | WARN |
| `WithTooltip` | - | yes | - | - | WARN |
| `Wrapper` | const | no | - | code/addons/docs/src/blocks/blocks/Wrapper.tsx:10 | WARN |
| `Zoom` | - | yes | - | - | WARN |
| `__definePreview` | function | yes | yes | code/renderers/react/src/preview.tsx:55 | PASS |
| `action` | function | yes | yes | code/core/src/actions/runtime/action.ts:50 | PASS |
| `actions` | function | no | - | code/core/src/actions/runtime/actions.ts:5 | WARN |
| `addToGlobalContext` | - | yes | - | - | WARN |
| `addons` | const | yes | - | code/addons/docs/src/preset.ts:155 | PASS |
| `afterEach` | function | yes | no | code/addons/a11y/src/preview.tsx:14 | FAIL |
| `anchorBlockIdFromId` | function | no | - | code/addons/docs/src/blocks/blocks/Anchor.tsx:4 | WARN |
| `applyHooks` | function | yes | yes | code/core/src/preview-api/modules/addons/hooks.ts:184 | PASS |
| `argsHash` | function | no | - | code/addons/docs/src/blocks/blocks/SourceContainer.tsx:11 | WARN |
| `assertIsFn` | function | no | - | code/addons/docs/src/blocks/blocks/mdx.tsx:19 | WARN |
| `automock` | - | yes | - | - | WARN |
| `babelParse` | - | yes | - | - | WARN |
| `background` | const | no | - | code/core/src/theming/base.ts:44 | WARN |
| `bail` | function | yes | yes | code/builders/builder-vite/src/index.ts:37 | WARN |
| `build` | function | yes | yes | code/builders/builder-vite/src/index.ts:63 | WARN |
| `buildQueries` | - | no | - | code/core/src/test/testing-library.ts:40 | WARN |
| `clearAllMocks` | function | yes | yes | code/core/src/test/spy.ts:77 | PASS |
| `color` | const | no | - | code/core/src/theming/base.ts:1 | WARN |
| `colors` | - | yes | - | - | WARN |
| `combineArgs` | function | yes | yes | code/core/src/preview-api/modules/store/args.ts:84 | PASS |
| `combineParameters` | function | yes | yes | code/core/src/manager-api/root.tsx:127 | PASS |
| `combineTags` | function | yes | - | code/core/src/csf/index.ts:81 | WARN |
| `componentTransform` | - | yes | - | - | WARN |
| `composeConfigs` | function | yes | yes | code/core/src/preview-api/modules/store/csf/composeConfigs.ts:43 | PASS |
| `composeStepRunners` | function | yes | yes | code/core/src/preview-api/modules/store/csf/stepRunners.ts:27 | PASS |
| `composeStories` | function | yes | yes | code/core/src/preview-api/modules/store/csf/portable-stories.ts:274 | PASS |
| `composeStory` | function | yes | yes | code/core/src/preview-api/modules/store/csf/portable-stories.ts:90 | PASS |
| `config` | const | no | - | code/core/src/actions/runtime/configureActions.ts:3 | WARN |
| `configure` | - | no | - | code/core/src/test/testing-library.ts:41 | WARN |
| `configureActions` | function | yes | - | code/core/src/actions/runtime/configureActions.ts:9 | PASS |
| `convert` | function | no | - | code/core/src/docs-tools/argTypes/convert/index.ts:8 | WARN |
| `core` | const | yes | - | code/frameworks/react-vite/src/preset.ts:5 | WARN |
| `corePresets` | const | yes | - | code/builders/builder-vite/src/index.ts:67 | WARN |
| `create` | function | yes | yes | code/core/src/theming/create.ts:29 | PASS |
| `createBrowserChannel` | - | yes | - | - | WARN |
| `createCache` | - | yes | - | - | WARN |
| `createEvent` | - | no | - | code/core/src/test/testing-library.ts:42 | WARN |
| `createGlobal` | const | yes | - | code/core/src/theming/global.ts:101 | PASS |
| `createPlaywrightTest` | function | no | - | code/core/src/preview-api/modules/store/csf/portable-stories.ts:319 | WARN |
| `createReset` | const | yes | - | code/core/src/theming/global.ts:25 | PASS |
| `createTest` | - | yes | - | - | WARN |
| `css` | - | yes | - | - | WARN |
| `darken` | const | yes | - | code/core/src/theming/utils.ts:62 | PASS |
| `decorateStory` | function | yes | yes | code/core/src/preview-api/modules/store/decorators.ts:10 | PASS |
| `decorators` | const | yes | - | code/addons/a11y/src/preview.tsx:12 | WARN |
| `default` | function | no | - | code/addons/a11y/src/postinstall.ts:5 | WARN |
| `defaultDecorateStory` | function | yes | yes | code/core/src/preview-api/modules/store/decorators.ts:49 | PASS |
| `defineMain` | function | yes | yes | code/frameworks/react-vite/src/node/index.ts:3 | PASS |
| `definePreview` | function | yes | yes | code/core/src/csf/csf-factories.ts:45 | WARN |
| `deprecate` | const | yes | - | code/core/src/client-logger/index.ts:75 | WARN |
| `emitTransformCode` | function | no | - | code/core/src/preview-api/modules/preview-web/emitTransformCode.ts:15 | WARN |
| `enrichCsf` | - | yes | - | - | WARN |
| `ensure` | function | no | - | code/core/src/theming/ensure.ts:10 | WARN |
| `esmWalker` | function | yes | - | code/core/src/mocking-utils/esmWalker.ts:71 | WARN |
| `expect` | - | yes | yes | code/core/src/test/index.ts:24 | PASS |
| `experimental_UniversalStore` | class | yes | - | code/core/src/shared/universal-store/index.ts:82 | WARN |
| `experimental_getStatusStore` | - | yes | - | code/core/src/manager-api/stores/status.ts:15 | WARN |
| `experimental_getTestProviderStore` | - | yes | - | code/core/src/manager-api/stores/test-provider.ts:16 | WARN |
| `experimental_loadStorybook` | - | yes | - | - | WARN |
| `extract` | - | yes | - | - | WARN |
| `extractTitle` | function | no | - | code/addons/docs/src/blocks/blocks/Title.tsx:24 | WARN |
| `filterArgTypes` | function | yes | yes | code/core/src/preview-api/modules/store/filterArgTypes.ts:10 | PASS |
| `findAllByAltText` | - | no | - | code/core/src/test/testing-library.ts:44 | WARN |
| `findAllByDisplayValue` | - | no | - | code/core/src/test/testing-library.ts:45 | WARN |
| `findAllByLabelText` | - | no | - | code/core/src/test/testing-library.ts:46 | WARN |
| `findAllByPlaceholderText` | - | no | - | code/core/src/test/testing-library.ts:47 | WARN |
| `findAllByRole` | - | no | - | code/core/src/test/testing-library.ts:48 | WARN |
| `findAllByTestId` | - | no | - | code/core/src/test/testing-library.ts:49 | WARN |
| `findAllByText` | - | no | - | code/core/src/test/testing-library.ts:50 | WARN |
| `findAllByTitle` | - | no | - | code/core/src/test/testing-library.ts:51 | WARN |
| `findByAltText` | - | no | - | code/core/src/test/testing-library.ts:52 | WARN |
| `findByDisplayValue` | - | no | - | code/core/src/test/testing-library.ts:53 | WARN |
| `findByLabelText` | - | no | - | code/core/src/test/testing-library.ts:54 | WARN |
| `findByPlaceholderText` | - | no | - | code/core/src/test/testing-library.ts:55 | WARN |
| `findByRole` | - | yes | - | code/core/src/test/testing-library.ts:56 | PASS |
| `findByTestId` | - | no | - | code/core/src/test/testing-library.ts:57 | WARN |
| `findByText` | - | no | - | code/core/src/test/testing-library.ts:58 | WARN |
| `findByTitle` | - | no | - | code/core/src/test/testing-library.ts:59 | WARN |
| `fireEvent` | - | yes | - | code/core/src/test/testing-library.ts:43 | PASS |
| `fn` | function | yes | yes | code/core/src/test/spy.ts:48 | PASS |
| `format` | function | yes | yes | code/addons/docs/src/blocks/controls/Number.tsx:22 | PASS |
| `formatDate` | function | yes | yes | code/addons/docs/src/blocks/controls/Date.tsx:26 | PASS |
| `formatTime` | function | yes | yes | code/addons/docs/src/blocks/controls/Date.tsx:34 | PASS |
| `generate` | - | yes | - | - | WARN |
| `generateStoryFile` | - | yes | - | - | WARN |
| `getAllByAltText` | - | no | - | code/core/src/test/testing-library.ts:60 | WARN |
| `getAllByDisplayValue` | - | no | - | code/core/src/test/testing-library.ts:61 | WARN |
| `getAllByLabelText` | - | no | - | code/core/src/test/testing-library.ts:62 | WARN |
| `getAllByPlaceholderText` | - | no | - | code/core/src/test/testing-library.ts:63 | WARN |
| `getAllByRole` | - | no | - | code/core/src/test/testing-library.ts:64 | WARN |
| `getAllByTestId` | - | no | - | code/core/src/test/testing-library.ts:65 | WARN |
| `getAllByText` | - | no | - | code/core/src/test/testing-library.ts:66 | WARN |
| `getAllByTitle` | - | no | - | code/core/src/test/testing-library.ts:67 | WARN |
| `getByAltText` | - | no | - | code/core/src/test/testing-library.ts:68 | WARN |
| `getByDisplayValue` | - | no | - | code/core/src/test/testing-library.ts:69 | WARN |
| `getByLabelText` | - | no | - | code/core/src/test/testing-library.ts:70 | WARN |
| `getByPlaceholderText` | - | no | - | code/core/src/test/testing-library.ts:71 | WARN |
| `getByRole` | - | yes | - | code/core/src/test/testing-library.ts:72 | PASS |
| `getByTestId` | - | no | - | code/core/src/test/testing-library.ts:73 | WARN |
| `getByText` | - | no | - | code/core/src/test/testing-library.ts:74 | WARN |
| `getByTitle` | - | no | - | code/core/src/test/testing-library.ts:75 | WARN |
| `getConfig` | - | no | - | code/core/src/test/testing-library.ts:76 | WARN |
| `getCsfFactoryAnnotations` | function | no | - | code/core/src/preview-api/modules/store/csf/csf-factory-utils.ts:10 | WARN |
| `getDefaultNormalizer` | - | no | - | code/core/src/test/testing-library.ts:77 | WARN |
| `getElementError` | - | no | - | code/core/src/test/testing-library.ts:78 | WARN |
| `getNodeText` | - | no | - | code/core/src/test/testing-library.ts:79 | WARN |
| `getPreferredColorScheme` | function | yes | - | code/core/src/theming/utils.ts:66 | PASS |
| `getPreviewBodyTemplate` | function | yes | - | code/core/src/common/utils/template.ts:10 | WARN |
| `getPreviewHeadTemplate` | function | yes | - | code/core/src/common/utils/template.ts:29 | WARN |
| `getQueriesForElement` | - | no | - | code/core/src/test/testing-library.ts:80 | WARN |
| `getRoles` | - | no | - | code/core/src/test/testing-library.ts:81 | WARN |
| `getSessionId` | - | yes | - | - | WARN |
| `getStoryHref` | - | yes | - | - | WARN |
| `getStoryId` | function | no | - | code/addons/docs/src/blocks/blocks/Story.tsx:62 | WARN |
| `getStoryProps` | function | no | - | code/addons/docs/src/blocks/blocks/Story.tsx:75 | WARN |
| `getStorySortParameter` | - | yes | - | - | WARN |
| `getStorybookInfo` | function | yes | - | code/core/src/common/utils/get-storybook-info.ts:139 | WARN |
| `getStorybookMetadata` | - | yes | - | - | WARN |
| `getSuggestedQuery` | - | no | - | code/core/src/test/testing-library.ts:82 | WARN |
| `hasVitePlugins` | function | yes | yes | code/builders/builder-vite/src/utils/has-vite-plugins.ts:13 | PASS |
| `ignoreSsrWarning` | const | yes | - | code/core/src/theming/index.ts:43 | PASS |
| `inferControls` | function | yes | - | code/core/src/preview-api/modules/store/inferControls.ts:66 | PASS |
| `initialGlobals` | const | yes | - | code/addons/a11y/src/preview.tsx:98 | WARN |
| `initializeThemeState` | function | yes | yes | code/addons/themes/src/decorators/helpers.ts:34 | PASS |
| `instrument` | function | yes | - | code/core/src/instrumenter/instrumenter.ts:749 | WARN |
| `isExportStory` | function | yes | - | code/core/src/csf/index.ts:51 | WARN |
| `isInaccessible` | - | no | - | code/core/src/test/testing-library.ts:83 | WARN |
| `isMockFunction` | - | yes | - | code/core/src/test/spy.ts | PASS |
| `isPropValid` | - | yes | - | - | WARN |
| `jsx` | - | yes | - | - | WARN |
| `keyframes` | - | yes | - | - | WARN |
| `lighten` | const | yes | - | code/core/src/theming/utils.ts:61 | PASS |
| `loadMainConfig` | function | yes | - | code/core/src/common/utils/load-main-config.ts:14 | WARN |
| `logDOM` | - | no | - | code/core/src/test/testing-library.ts:84 | WARN |
| `logRoles` | - | no | - | code/core/src/test/testing-library.ts:85 | WARN |
| `logTracker` | - | yes | - | - | WARN |
| `logger` | const | yes | - | code/core/src/client-logger/index.ts:23 | WARN |
| `makeDecorator` | function | yes | - | code/core/src/preview-api/modules/addons/make-decorator.ts:44 | PASS |
| `mockChannel` | function | yes | yes | code/core/src/manager-api/lib/storybook-channel-mock.ts:3 | PASS |
| `mocked` | function | yes | yes | code/core/src/test/spy.ts:119 | PASS |
| `mocks` | - | yes | - | code/core/src/test/spy.ts | PASS |
| `normalizeArrays` | function | yes | yes | code/core/src/preview-api/modules/store/csf/normalizeArrays.ts:1 | PASS |
| `normalizeProjectAnnotations` | function | yes | yes (Low) | code/core/src/preview-api/modules/store/csf/normalizeProjectAnnotations.ts:17 | WARN |
| `normalizeStories` | function | yes | - | code/core/src/common/utils/normalize-stories.ts:108 | WARN |
| `normalizeStory` | function | yes | yes | code/core/src/preview-api/modules/store/csf/normalizeStory.ts:25 | PASS |
| `onMockCall` | function | yes | yes | code/core/src/test/spy.ts:35 | PASS |
| `once` | function | yes | - | code/core/src/client-logger/index.ts:57 | WARN |
| `parameters` | const | yes | - | code/addons/a11y/src/preview.tsx:105 | WARN |
| `parse` | function | yes | yes | code/addons/docs/src/blocks/controls/Number.tsx:17 | PASS |
| `parseDate` | function | yes | yes | code/addons/docs/src/blocks/controls/Date.tsx:11 | PASS |
| `parseKind` | function | yes | - | code/core/src/csf/index.ts:69 | WARN |
| `parseTime` | function | yes | yes | code/addons/docs/src/blocks/controls/Date.tsx:18 | PASS |
| `parser` | - | yes | - | - | WARN |
| `pauseAnimations` | function | no | - | code/core/src/preview-api/modules/preview-web/render/animation-utils.ts:18 | WARN |
| `pluckThemeFromContext` | function | yes | yes | code/addons/themes/src/decorators/helpers.ts:16 | PASS |
| `prepareMeta` | function | yes | yes | code/core/src/preview-api/modules/store/csf/prepareStory.ts:171 | PASS |
| `prepareStory` | function | yes | yes | code/core/src/preview-api/modules/store/csf/prepareStory.ts:37 | PASS |
| `pretty` | function | yes | - | code/core/src/client-logger/index.ts:77 | WARN |
| `prettyDOM` | - | no | - | code/core/src/test/testing-library.ts:86 | WARN |
| `prettyFormat` | - | no | - | code/core/src/test/testing-library.ts:111 | WARN |
| `prompt` | - | yes | - | - | WARN |
| `queries` | - | no | - | code/core/src/test/testing-library.ts:87 | WARN |
| `queryAllByAltText` | - | no | - | code/core/src/test/testing-library.ts:88 | WARN |
| `queryAllByAttribute` | - | no | - | code/core/src/test/testing-library.ts:89 | WARN |
| `queryAllByDisplayValue` | - | no | - | code/core/src/test/testing-library.ts:90 | WARN |
| `queryAllByLabelText` | - | no | - | code/core/src/test/testing-library.ts:91 | WARN |
| `queryAllByPlaceholderText` | - | no | - | code/core/src/test/testing-library.ts:92 | WARN |
| `queryAllByRole` | - | no | - | code/core/src/test/testing-library.ts:93 | WARN |
| `queryAllByTestId` | - | no | - | code/core/src/test/testing-library.ts:94 | WARN |
| `queryAllByText` | - | no | - | code/core/src/test/testing-library.ts:95 | WARN |
| `queryAllByTitle` | - | no | - | code/core/src/test/testing-library.ts:96 | WARN |
| `queryByAltText` | - | no | - | code/core/src/test/testing-library.ts:97 | WARN |
| `queryByAttribute` | - | no | - | code/core/src/test/testing-library.ts:98 | WARN |
| `queryByDisplayValue` | - | no | - | code/core/src/test/testing-library.ts:99 | WARN |
| `queryByLabelText` | - | no | - | code/core/src/test/testing-library.ts:100 | WARN |
| `queryByPlaceholderText` | - | no | - | code/core/src/test/testing-library.ts:101 | WARN |
| `queryByRole` | - | yes | - | code/core/src/test/testing-library.ts:102 | PASS |
| `queryByTestId` | - | no | - | code/core/src/test/testing-library.ts:103 | WARN |
| `queryByText` | - | no | - | code/core/src/test/testing-library.ts:104 | WARN |
| `queryByTitle` | - | no | - | code/core/src/test/testing-library.ts:105 | WARN |
| `queryHelpers` | - | no | - | code/core/src/test/testing-library.ts:106 | WARN |
| `recast` | - | yes | - | - | WARN |
| `redirect` | - | yes | - | - | WARN |
| `resetAllMocks` | function | yes | yes | code/core/src/test/spy.ts:89 | PASS |
| `resolve` | - | yes | - | - | WARN |
| `responsiveViewport` | const | no | - | code/core/src/viewport/responsiveViewport.tsx:4 | WARN |
| `restoreAllMocks` | function | yes | yes | code/core/src/test/spy.ts:98 | PASS |
| `runtime` | - | yes | - | - | WARN |
| `sanitize` | function | yes | - | code/core/src/csf/index.ts:8 | WARN |
| `sanitizeStoryContextUpdate` | function | yes | yes (Low) | code/core/src/preview-api/modules/store/decorators.ts:30 | WARN |
| `sb` | const | yes | - | code/core/src/test/index.ts:54 | PASS |
| `screen` | - | yes | - | code/core/src/test/testing-library.ts:107 | PASS |
| `setDefaultProjectAnnotations` | function | yes | - | code/core/src/preview-api/modules/store/csf/portable-stories.ts:49 | PASS |
| `setProjectAnnotations` | function | yes | yes | code/core/src/preview-api/modules/store/csf/portable-stories.ts:73 | PASS |
| `simulateDOMContentLoaded` | function | no | - | code/core/src/preview-api/modules/preview-web/simulate-pageload.ts:31 | WARN |
| `simulatePageLoad` | function | no | - | code/core/src/preview-api/modules/preview-web/simulate-pageload.ts:83 | WARN |
| `slugs` | const | no | - | code/addons/docs/src/blocks/blocks/Heading.tsx:15 | WARN |
| `sortStoriesV7` | function | yes | yes | code/core/src/preview-api/modules/store/sortStories.ts:37 | PASS |
| `spyOn` | function | yes | yes | code/core/src/test/spy.ts:41 | PASS |
| `srOnlyStyles` | const | yes | - | code/core/src/theming/global.ts:12 | PASS |
| `start` | function | yes | yes | code/builders/builder-vite/src/index.ts:41 | WARN |
| `storeOptions` | const | yes | - | code/addons/vitest/src/constants.ts:21 | WARN |
| `storyNameFromExport` | function | yes | - | code/core/src/csf/index.ts:35 | WARN |
| `storybookTest` | function | yes | yes | code/addons/vitest/src/vitest-plugin/index.ts:164 | PASS |
| `styled` | - | yes | - | - | WARN |
| `telemetry` | - | yes | - | - | WARN |
| `themes` | const | yes | - | code/core/src/theming/create.ts:20 | PASS |
| `toId` | function | yes | yes | code/core/src/csf/index.ts:27 | WARN |
| `toTestId` | function | yes | - | code/core/src/csf/index.ts:31 | WARN |
| `tokens` | const | no | - | code/core/src/theming/base.ts:104 | WARN |
| `transformSync` | - | yes | - | - | WARN |
| `traverse` | - | yes | - | - | WARN |
| `types` | const | yes | - | code/core/src/manager-api/root.tsx:510 | WARN |
| `typography` | const | no | - | code/core/src/theming/base.ts:59 | WARN |
| `uninstrumentedUserEvent` | const | no | - | code/core/src/test/testing-library.ts:121 | WARN |
| `useArgs` | function | yes | yes | code/core/src/manager-api/root.tsx:462 | PASS |
| `useCallback` | function | yes | - | code/core/src/preview-api/modules/addons/hooks.ts:344 | PASS |
| `useChannel` | function | yes | - | code/core/src/manager-api/root.tsx:329 | PASS |
| `useEffect` | function | yes | - | code/core/src/preview-api/modules/addons/hooks.ts:498 | PASS |
| `useGlobals` | function | yes | yes | code/core/src/manager-api/root.tsx:481 | PASS |
| `useMemo` | function | yes | - | code/core/src/preview-api/modules/addons/hooks.ts:322 | PASS |
| `useOf` | function | yes | - | code/addons/docs/src/blocks/blocks/useOf.ts:18 | PASS |
| `useParameter` | function | yes | yes (Low) | code/core/src/preview-api/modules/addons/hooks.ts:590 | WARN |
| `useReducer` | function | yes | - | code/core/src/preview-api/modules/addons/hooks.ts:457 | PASS |
| `useRef` | function | yes | - | code/core/src/preview-api/modules/addons/hooks.ts:367 | PASS |
| `useSourceProps` | function | no | - | code/addons/docs/src/blocks/blocks/Source.tsx:101 | WARN |
| `useState` | function | yes | - | code/core/src/preview-api/modules/addons/hooks.ts:418 | PASS |
| `useStatusStore` | - | yes | - | - | WARN |
| `useStoryContext` | function | yes | - | code/core/src/preview-api/modules/addons/hooks.ts:560 | PASS |
| `useTabsState` | - | yes | - | - | WARN |
| `useTestProviderStore` | - | yes | - | - | WARN |
| `useTheme` | - | yes | - | - | WARN |
| `useThemeParameters` | function | yes | yes | code/addons/themes/src/decorators/helpers.ts:20 | PASS |
| `useUniversalStore` | - | yes | - | - | WARN |
| `userEvent` | - | yes | - | code/core/src/test/testing-library.ts:123 | PASS |
| `userOrAutoTitle` | function | yes | - | code/core/src/preview-api/modules/store/autoTitle.ts:86 | PASS |
| `userOrAutoTitleFromSpecifier` | function | yes | - | code/core/src/preview-api/modules/store/autoTitle.ts:49 | PASS |
| `viteFinal` | function | yes | yes | code/addons/docs/src/preset.ts:159 | WARN |
| `vitestTransform` | - | yes | - | - | WARN |
| `waitFor` | - | yes | - | code/core/src/test/testing-library.ts:108 | PASS |
| `waitForAnimations` | function | no | - | code/core/src/preview-api/modules/preview-web/render/animation-utils.ts:54 | WARN |
| `waitForElementToBeRemoved` | - | no | - | code/core/src/test/testing-library.ts:109 | WARN |
| `withActions` | const | yes | - | code/core/src/actions/decorator.ts:59 | PASS |
| `withTheme` | - | yes | - | - | WARN |
| `withThemeByClassName` | function | yes | yes (Low) | code/addons/themes/src/decorators/class-name.decorator.tsx:19 | WARN |
| `withThemeByDataAttribute` | function | yes | yes (Low) | code/addons/themes/src/decorators/data-attribute.decorator.tsx:19 | WARN |
| `withThemeFromJSXProvider` | function | yes | yes (Low) | code/addons/themes/src/decorators/provider.decorator.tsx:23 | WARN |
| `within` | - | yes | yes | code/core/src/test/testing-library.ts:110 | PASS |
| `withoutVitePlugins` | function | yes | yes | code/builders/builder-vite/src/utils/without-vite-plugins.ts:2 | PASS |

### Coverage Summary

- **Exports Found:** 370
- **Documented:** 236 (63.78%)
- **Missing Documentation:** 134
- **Signature Mismatches:** 1, plus 8 graded Low or Info and counted as matching
- **Stale Documentation:** 233, documented extras included
- **Scoped Out by the Brief:** `A` (code/core/src/components/components/typography/elements/A.tsx:7), `AbstractToolbar` (code/core/src/components/components/Toolbar/Toolbar.tsx:15), `ActionBar` (code/core/src/components/components/ActionBar/ActionBar.tsx:89), `ActionItem` (code/core/src/components/components/ActionBar/ActionBar.tsx:72), `ActionList` (code/core/src/components/components/ActionList/ActionList.tsx:222), `AddonPanel` (code/core/src/components/components/addon-panel/addon-panel.tsx:36), `AngularMeta` (code/frameworks/angular/src/client/preview.ts:150), `AngularOptions` (code/frameworks/angular/src/types.ts:47), `AngularParameters` (code/frameworks/angular/src/client/types.ts:45), `AngularPreview` (code/frameworks/angular/src/client/preview.ts:81), `AngularRenderer` (code/frameworks/angular/src/client/types.ts:40), `AngularStory` (code/frameworks/angular/src/client/preview.ts:254), `BabelFileClass` (code/core/src/babel/index.ts:43), `BadMetaError` (code/core/src/csf-tools/CsfFile.ts:246), `Badge` (code/core/src/components/components/Badge/Badge.tsx:88), `Bar` (code/core/src/components/components/Bar/Bar.tsx:52), `BarProps` (code/core/src/components/components/Bar/Bar.tsx:7), `BaseLocationProvider` (code/core/src/router/router.tsx:144), `Blockquote` (code/core/src/components/components/typography/elements/Blockquote.tsx:6), `BuildIndexOptions` (code/core/src/core-server/build-index.ts:10), `BuildStaticStandaloneOptions` (code/core/src/core-server/build-static.ts:31), `Button` (code/core/src/components/components/Button/Button.tsx:53), `ButtonProps` (code/core/src/components/components/Button/Button.tsx:14), `CLI_COLORS` (code/core/src/node-logger/logger/colors.ts:3), `CacheEntry` (code/core/src/telemetry/event-cache.ts:12), `Card` (code/core/src/components/components/Card/Card.tsx:98), `Channel` (code/core/src/channels/main.ts:22), `ChannelEvent` (code/core/src/channels/types.ts:18), `ChannelHandler` (code/core/src/channels/types.ts:11), `ChannelLike` (code/core/src/channels/types.ts:36), `ChannelTransport` (code/core/src/channels/types.ts:13), `ClipboardCode` (code/core/src/components/components/clipboard/ClipboardCode.tsx:24), `Code` (code/core/src/components/components/typography/elements/Code.tsx:42), `Collapsible` (code/core/src/components/components/Collapsible/Collapsible.tsx:31), `ComponentArgTypesData` (code/core/src/core-server/utils/get-dummy-args-from-argtypes.ts:8), `ConfigFile` (code/core/src/csf-tools/ConfigFile.ts:140), `ConsoleLogger` (code/core/src/node-logger/logger/console.ts:340), `Context` (code/core/src/telemetry/types.ts:106), `CsfFile` (code/core/src/csf-tools/CsfFile.ts:280), `CsfOptions` (code/core/src/csf-tools/CsfFile.ts:200), `DEEPLY_EQUAL` (code/core/src/router/utils.ts:43), `DL` (code/core/src/components/components/typography/elements/DL.tsx:6), `Dependency` (code/core/src/telemetry/types.ts:48), `Div` (code/core/src/components/components/typography/elements/Div.tsx:5), `DocumentWrapper` (code/core/src/components/components/typography/DocumentWrapper.tsx:3), `EmptyTabContent` (code/core/src/components/components/Tabs/EmptyTabContent.tsx:47), `EnrichCsfOptions` (code/core/src/csf-tools/enrichCsf.ts:6), `ErrorCollector` (code/core/src/telemetry/error-collector.ts:13), `ErrorFormatter` (code/core/src/components/components/ErrorFormatter/ErrorFormatter.tsx:29), `EventType` (code/core/src/telemetry/types.ts:9), `FlexBar` (code/core/src/components/components/Bar/Bar.tsx:129), `Form` (code/core/src/components/components/Form/Form.tsx:11), `GenerateStoryOptions` (code/core/src/core-server/utils/generate-story.ts:21), `GenerateStoryResult` (code/core/src/core-server/utils/generate-story.ts:11), `H1` (code/core/src/components/components/typography/elements/H1.tsx:6), `H2` (code/core/src/components/components/typography/elements/H2.tsx:6), `H3` (code/core/src/components/components/typography/elements/H3.tsx:6), `H4` (code/core/src/components/components/typography/elements/H4.tsx:6), `H5` (code/core/src/components/components/typography/elements/H5.tsx:6), `H6` (code/core/src/components/components/typography/elements/H6.tsx:6), `HEARTBEAT_INTERVAL` (code/core/src/channels/websocket/index.ts:20), `HEARTBEAT_MAX_LATENCY` (code/core/src/channels/websocket/index.ts:21), `HR` (code/core/src/components/components/typography/elements/HR.tsx:3), `IErrorWithStdErrAndStdOut` (code/core/src/telemetry/sanitize.ts:4), `IStory` (code/frameworks/angular/src/client/types.ts:31), `IconButton` (code/core/src/components/components/Button/Button.tsx:327), `Img` (code/core/src/components/components/typography/elements/Img.tsx:3), `InitPayload` (code/core/src/telemetry/types.ts:131), `LI` (code/core/src/components/components/typography/elements/LI.tsx:6), `Link` (code/core/src/components/components/typography/link/link.tsx:198), `LinkProps` (code/core/src/router/types.ts:23), `ListItem` (code/core/src/components/components/tooltip/ListItem.tsx:249), `Listener` (code/core/src/channels/types.ts:24), `Location` (code/core/src/router/router.tsx:81), `LocationProvider` (code/core/src/router/router.tsx:143), `LogLevel` (code/core/src/node-logger/logger/logger.ts:46), `Match` (code/core/src/router/router.tsx:141), `MemoryRouter` (code/core/src/router/router.tsx:145), `MixedFactoryError` (code/core/src/csf-tools/CsfFile.ts:234), `Modal` (code/core/src/components/components/Modal/Modal.tsx:242), `ModalDecorator` (code/core/src/components/components/Modal/Modal.tsx:248), `MultipleMetaError` (code/core/src/csf-tools/CsfFile.ts:222), `NavigateFunction` (code/core/src/router/types.ts:14), `NavigateOptions` (code/core/src/router/types.ts:12), `NoMetaError` (code/core/src/csf-tools/CsfFile.ts:210), `OL` (code/core/src/components/components/typography/elements/OL.tsx:16), `Other` (code/core/src/router/types.ts:7), `P` (code/core/src/components/components/typography/elements/P.tsx:6), `Payload` (code/core/src/telemetry/types.ts:102), `Placeholder` (code/core/src/components/components/placeholder/placeholder.tsx:22), `Popover` (code/core/src/components/components/Popover/Popover.tsx:77), `PopoverProps` (code/core/src/components/components/Popover/Popover.tsx:9), `PopoverProvider` (code/core/src/components/components/Popover/PopoverProvider.tsx:63), `PopoverProviderProps` (code/core/src/components/components/Popover/PopoverProvider.tsx:13), `PopperPlacement` (code/core/src/components/components/shared/overlayHelpers.tsx:22), `PostMessageTransport` (code/core/src/channels/postmessage/index.ts:29), `Pre` (code/core/src/components/components/typography/elements/Pre.tsx:6), `PreactRenderer` (code/renderers/preact/src/types.ts:14), `ProgressSpinner` (code/core/src/components/components/ProgressSpinner/ProgressSpinner.tsx:66), `RenderData` (code/core/src/router/types.ts:21), `ResetWrapper` (code/core/src/components/components/typography/ResetWrapper.tsx:12), `Route` (code/core/src/router/router.tsx:141), `RouterData` (code/core/src/router/types.ts:16), `ScrollArea` (code/core/src/components/components/ScrollArea/ScrollArea.tsx:95), `Select` (code/core/src/components/components/Select/Select.tsx:201), `Separator` (code/core/src/components/components/Bar/Separator.tsx:9), `Spaced` (code/core/src/components/components/spaced/Spaced.tsx:63), `Span` (code/core/src/components/components/typography/elements/Span.tsx:6), `SpinnerInstance` (code/core/src/node-logger/prompts/prompt-provider-base.ts:46), `StatelessTab` (code/core/src/components/components/Tabs/StatelessTab.tsx:57), `StatelessTabList` (code/core/src/components/components/Tabs/StatelessTabList.tsx:66), `StatelessTabListProps` (code/core/src/components/components/Tabs/StatelessTabList.tsx:62), `StatelessTabPanel` (code/core/src/components/components/Tabs/StatelessTabPanel.tsx:30), `StatelessTabPanelProps` (code/core/src/components/components/Tabs/StatelessTabPanel.tsx:9), `StatelessTabProps` (code/core/src/components/components/Tabs/StatelessTab.tsx:7), `StatelessTabsView` (code/core/src/components/components/Tabs/StatelessTabsView.tsx:31), `StatelessTabsViewProps` (code/core/src/components/components/Tabs/StatelessTabsView.tsx:27), `StaticMeta` (code/core/src/csf-tools/CsfFile.ts:258), `StaticStory` (code/core/src/csf-tools/CsfFile.ts:265), `StoryData` (code/core/src/router/utils.ts:9), `StoryIndexGenerator` (code/core/src/core-server/utils/StoryIndexGenerator.ts:101), `StoryTest` (code/core/src/csf-tools/CsfFile.ts:271), `StorybookAddon` (code/core/src/telemetry/types.ts:53), `StorybookBuilderOptions` (code/frameworks/angular/src/builders/build-storybook/index.ts:38), `StorybookBuilderOutput` (code/frameworks/angular/src/builders/build-storybook/index.ts:68), `StorybookIcon` (code/core/src/components/brand/StorybookIcon.tsx:3), `StorybookLogo` (code/core/src/components/brand/StorybookLogo.tsx:7), `StorybookMetadata` (code/core/src/telemetry/types.ts:57), `StyledConsoleLogger` (code/core/src/node-logger/logger/console.ts:340), `SvelteRenderer` (code/renderers/svelte/src/types.ts:11), `SyntaxHighlighter` (code/core/src/components/components/syntaxhighlighter/lazy-syntaxhighlighter.tsx:52), `SyntaxHighlighterFormatTypes` (code/core/src/components/components/syntaxhighlighter/syntaxhighlighter-types.ts:24), `SyntaxHighlighterProps` (code/core/src/components/components/syntaxhighlighter/syntaxhighlighter-types.ts:47), `SyntaxHighlighterRendererProps` (code/core/src/components/components/syntaxhighlighter/syntaxhighlighter-types.ts:5), `TT` (code/core/src/components/components/typography/elements/TT.tsx:5), `TabBar` (code/core/src/components/components/Tabs/Tabs.tsx:61), `TabButton` (code/core/src/components/components/Tabs/Button.tsx:139), `TabList` (code/core/src/components/components/Tabs/TabList.tsx:150), `TabListProps` (code/core/src/components/components/Tabs/TabList.tsx:146), `TabPanel` (code/core/src/components/components/Tabs/TabPanel.tsx:34), `TabPanelProps` (code/core/src/components/components/Tabs/TabPanel.tsx:12), `TabProps` (code/core/src/components/components/Tabs/TabsView.tsx:15), `TabWrapper` (code/core/src/components/components/Tabs/Tabs.tsx:120), `Table` (code/core/src/components/components/typography/elements/Table.tsx:6), `Tabs` (code/core/src/components/components/Tabs/Tabs.tsx:188), `TabsState` (code/core/src/components/components/Tabs/Tabs.tsx:287), `TabsView` (code/core/src/components/components/Tabs/TabsView.tsx:106), `TabsViewProps` (code/core/src/components/components/Tabs/TabsView.tsx:64), `TaskLogInstance` (code/core/src/node-logger/prompts/prompt-provider-base.ts:54), `TelemetryData` (code/core/src/telemetry/types.ts:119), `TelemetryEvent` (code/core/src/telemetry/types.ts:125), `ToggleButton` (code/core/src/components/components/ToggleButton/ToggleButton.tsx:16), `Toolbar` (code/core/src/components/components/Toolbar/Toolbar.tsx:36), `Tooltip` (code/core/src/components/components/tooltip/Tooltip.tsx:7), `TooltipLinkList` (code/core/src/components/components/tooltip/TooltipLinkList.tsx:70), `TooltipLinkListLink` (code/core/src/components/components/tooltip/TooltipLinkList.tsx:39), `TooltipMessage` (code/core/src/components/components/tooltip/TooltipMessage.tsx:47), `TooltipNote` (code/core/src/components/components/tooltip/TooltipNote.tsx:23), `TooltipNoteProps` (code/core/src/components/components/tooltip/TooltipNote.tsx:19), `TooltipProps` (code/core/src/components/components/tooltip/Tooltip.tsx:5), `TooltipProvider` (code/core/src/components/components/tooltip/TooltipProvider.tsx:108), `TooltipProviderProps` (code/core/src/components/components/tooltip/TooltipProvider.tsx:14), `TransformComponentType` (code/frameworks/angular/src/client/public-types.ts:56), `UL` (code/core/src/components/components/typography/elements/UL.tsx:16), `WebComponentsMeta` (code/renderers/web-components/src/preview.ts:160), `WebComponentsPreview` (code/renderers/web-components/src/preview.ts:85), `WebComponentsRenderer` (code/renderers/web-components/src/types.ts:14), `WebComponentsStory` (code/renderers/web-components/src/preview.ts:264), `WebComponentsTypes` (code/renderers/web-components/src/types.ts:24), `WebsocketTransport` (code/core/src/channels/websocket/index.ts:23), `WithTooltip` (code/core/src/components/components/tooltip/lazy-WithTooltip.tsx:8), `WithTooltipPure` (code/core/src/components/components/tooltip/lazy-WithTooltip.tsx:18), `Zoom` (code/core/src/components/components/Zoom/Zoom.tsx:4), `addToGlobalContext` (code/core/src/telemetry/telemetry.ts:26), `applicationConfig` (code/frameworks/angular/src/client/decorators.ts:37), `argsToTemplate` (code/frameworks/angular/src/client/argsToTemplate.ts:59), `babelParseExpression` (code/core/src/babel/babelParse.ts:52), `babelParseFile` (code/core/src/csf-tools/CsfFile.ts:1062), `babelPrint` (code/core/src/babel/babelParse.ts:42), `buildArgsParam` (code/core/src/router/utils.ts:186), `buildDevStandalone` (code/core/src/core-server/build-dev.ts:44), `buildIndex` (code/core/src/core-server/build-index.ts:12), `buildIndexStandalone` (code/core/src/core-server/build-index.ts:39), `buildStaticStandalone` (code/core/src/core-server/build-static.ts:35), `canUpdateVitestConfigFile` (code/core/src/babel/vitest-config-helpers.ts:159), `canUpdateVitestWorkspaceFile` (code/core/src/babel/vitest-config-helpers.ts:204), `cleanPaths` (code/core/src/telemetry/sanitize.ts:24), `codeCommon` (code/core/src/components/components/typography/lib/common.tsx:22), `colors` (code/core/src/node-logger/index.ts:57), `componentTransform` (code/core/src/csf-tools/vitest-plugin/component-transformer.ts:285), `componentWrapperDecorator` (code/frameworks/angular/src/client/decorators.ts:60), `components` (code/core/src/components/index.ts:133), `computeStorybookMetadata` (code/core/src/telemetry/storybook-metadata.ts:105), `convertToReactAriaPlacement` (code/core/src/components/components/shared/overlayHelpers.tsx:24), `createBrowserChannel` (code/core/src/channels/index.ts:32), `createCopyToClipboardFunction` (code/core/src/components/components/syntaxhighlighter/clipboard.ts:26), `createHyperlink` (code/core/src/node-logger/wrap-utils.ts:155), `createReactiveProps` (code/renderers/svelte/static/createReactiveProps.svelte.js:10), `deepDiff` (code/core/src/router/utils.ts:44), `deepMerge` (code/frameworks/angular/src/server/framework-preset-angular-cli.ts:95), `enrichCsf` (code/core/src/csf-tools/enrichCsf.ts:144), `enrichCsfMeta` (code/core/src/csf-tools/enrichCsf.ts:129), `enrichCsfStory` (code/core/src/csf-tools/enrichCsf.ts:12), `experimental_loadStorybook` (code/core/src/core-server/load.ts:18), `extractDescription` (code/core/src/csf-tools/enrichCsf.ts:158), `extractSource` (code/core/src/csf-tools/enrichCsf.ts:152), `formatConfig` (code/core/src/csf-tools/ConfigFile.ts:1165), `formatCsf` (code/core/src/csf-tools/CsfFile.ts:1083), `framework` (code/core/src/core-server/presets/common-override-preset.ts:5), `generate` (code/core/src/babel/index.ts:38), `generateStoryFile` (code/core/src/core-server/utils/generate-story.ts:64), `getConfigObjectFromMergeArg` (code/core/src/babel/vitest-config-helpers.ts:49), `getCustomElements` (code/renderers/web-components/src/framework-api.ts:37), `getEffectiveMergeConfigCall` (code/core/src/babel/vitest-config-helpers.ts:78), `getErrorLevel` (code/core/src/core-server/withTelemetry.ts:40), `getLastEvents` (code/core/src/telemetry/event-cache.ts:41), `getMatch` (code/core/src/router/utils.ts:233), `getPrecedingUpgrade` (code/core/src/telemetry/event-cache.ts:68), `getServerPort` (code/core/src/core-server/utils/server-address.ts:34), `getSessionId` (code/core/src/telemetry/session-id.ts:18), `getStoryHref` (code/core/src/components/components/utils/getStoryHref.ts:15), `getStorySortParameter` (code/core/src/csf-tools/getStorySortParameter.ts:96), `getStorybookMetadata` (code/core/src/telemetry/storybook-metadata.ts:312), `getTargetConfigObject` (code/core/src/babel/vitest-config-helpers.ts:118), `hrefTo` (code/addons/links/src/utils.ts:39), `interleaveSeparators` (code/core/src/components/components/Bar/Separator.tsx:29), `isCsfFactoryPreview` (code/core/src/csf-tools/ConfigFile.ts:1187), `isDefineConfigLike` (code/core/src/babel/vitest-config-helpers.ts:35), `isExampleStoryId` (code/core/src/telemetry/index.ts:26), `isImportedDefineConfigLikeIdentifier` (code/core/src/babel/vitest-config-helpers.ts:18), `isModuleMock` (code/core/src/csf-tools/CsfFile.ts:116), `isTelemetryEnabled` (code/core/src/core-server/withTelemetry.ts:157), `isValidComponent` (code/renderers/web-components/src/framework-api.ts:3), `isValidMetaData` (code/renderers/web-components/src/framework-api.ts:13), `isValidPreviewPath` (code/core/src/csf-tools/CsfFile.ts:43), `linkTo` (code/addons/links/src/utils.ts:61), `loadConfig` (code/core/src/csf-tools/ConfigFile.ts:1160), `loadCsf` (code/core/src/csf-tools/CsfFile.ts:1077), `logTracker` (code/core/src/node-logger/logger/log-tracker.ts:95), `mapStaticDir` (code/core/src/core-server/utils/server-statics.ts:198), `metaFrameworks` (code/core/src/telemetry/storybook-metadata.ts:33), `moduleMetadata` (code/frameworks/angular/src/client/decorators.ts:11), `nameSpaceClassNames` (code/core/src/components/components/typography/DocumentFormatting.tsx:1), `navigate` (code/addons/links/src/utils.ts:36), `oneWayHash` (code/core/src/telemetry/one-way-hash.ts:4), `parsePath` (code/core/src/router/utils.ts:17), `parserOptions` (code/core/src/babel/babelParse.ts:21), `printConfig` (code/core/src/csf-tools/ConfigFile.ts:1169), `printCsf` (code/core/src/csf-tools/CsfFile.ts:1096), `prompt` (code/core/src/node-logger/prompts/index.ts:5), `protectUrls` (code/core/src/node-logger/wrap-utils.ts:70), `queryFromLocation` (code/core/src/router/utils.ts:222), `readConfig` (code/core/src/csf-tools/ConfigFile.ts:1173), `readCsf` (code/core/src/csf-tools/CsfFile.ts:1100), `removeAnsiEscapeCodes` (code/core/src/telemetry/sanitize.ts:15), `resetComponents` (code/core/src/components/index.ts:142), `resolveExpression` (code/core/src/babel/expression-resolver.ts:22), `runNgcc` (code/frameworks/angular/src/server/framework-preset-angular-ivy.ts:37), `sanitizeAddonName` (code/core/src/telemetry/storybook-metadata.ts:50), `sanitizeError` (code/core/src/telemetry/sanitize.ts:64), `sendTelemetryError` (code/core/src/core-server/withTelemetry.ts:91), `setCustomElements` (code/renderers/web-components/src/framework-api.ts:29), `setCustomElementsManifest` (code/renderers/web-components/src/framework-api.ts:33), `stories` (code/core/src/core-server/presets/common-override-preset.ts:18), `stringifyQuery` (code/core/src/router/utils.ts:226), `telemetry` (code/core/src/telemetry/index.ts:31), `traverse` (code/core/src/babel/index.ts:39), `typescript` (code/core/src/core-server/presets/common-override-preset.ts:25), `unwrapTSExpression` (code/core/src/babel/expression-resolver.ts:4), `useNavigate` (code/core/src/router/router.tsx:45), `useTabsState` (code/core/src/components/components/Tabs/TabsView.tsx:30), `vitestTransform` (code/core/src/csf-tools/vitest-plugin/transformer.ts:108), `webpackFinal` (code/frameworks/angular/src/server/framework-preset-angular-cli.ts:15), `withLinks` (code/addons/links/src/utils.ts:110), `withReset` (code/core/src/components/components/typography/lib/common.tsx:36), `withTelemetry` (code/core/src/core-server/withTelemetry.ts:161), `writeConfig` (code/core/src/csf-tools/ConfigFile.ts:1178), `writeCsf` (code/core/src/csf-tools/CsfFile.ts:1105)

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 63.78% |
| Signature Accuracy | 98.92% |
| Type Coverage | 82.03% |

### Coverage Notes

- **Inventory:** built by the parent from SKILL.md and all six `references/*.md` files (SKILL.md's `## Full` headings are pointer stubs), no subagent tool being available in this session: 606 entries over 469 names, one entry per documentation place. `validate-inventory.py` passed on the first run (schema, spot-check of `A`, `StorybookConfig`, `withoutVitePlugins`, floor: 295 of 295 names kept, every pinned signature carried). No split-body cross-check mismatch (§1b).
- **Read by eye** (the recipe runner could not parse them): `code/core/src/csf/csf-factories.ts`, `code/core/src/instrumenter/typings.d.ts`, `code/core/src/mocking-utils/esmWalker.ts`, `code/core/src/test/spy.ts`, `code/core/src/typings.d.ts`. Their per-file results added `isMockFunction` and `mocks` to the tier A set (368 to 370). **Unread:** none.
- **Extraction gaps:** 146 names no recipe found, all on the surface; the one compared, `within` (`code/core/src/test/testing-library.ts:110`), was read by eye.
- **Signature comparison:** 93 checks over 68 source files, judged in the main thread by `references/signature-comparison-rules.md`, one judge for every file. One Critical mismatch (`afterEach`), seven Low `parameter-name` mismatches and one Info partial signature (`Story`), counted as matching. `score-signatures.py` reported no warnings.
- **Guards:** `guards.deflation` fires: `stats.effective_denominator` 280 against a re-derived tier A set of 370 names (+32.14%), a stale stored count (Medium `metadata-drift`). `guards.inflation` and `guards.staleScope` do not fire.
- **Numerator ground truth:** skipped (the declared count is not the denominator).
- **Metadata count cross-check:** `stats.exports_public_api` 1335 against `exports[]` 88 (93% drift, Medium `metadata-drift`); barrel 1335 against documented 228 (Info `multi-denominator`).
- **Stale names:** 233 documented names outside the tier A set; `classify-stale` found none fabricated, 150 still defined at one declaration, 54 declared in several files, 29 with neither.
- **Provenance line check:** 12 map lines that are not the definition of their export and whose definition the rules could not find (Info `provenance-unverified`).
- **Deep tier, not checked by script:** 14 documentation errors read by hand and recorded as Info observations (ledger records titled `Not checked by script: {name}`): `ComponentAnnotations`, `StoryContext`, `ViewportParameters`, `Brand`, `FULL_RUN_TRIGGERS`, `storeOptions`, `DocsRenderer`, `viteFinal`, `core`, `MockUniversalStore`, `Meta`, `StoryObj`, `Decorator`, `Loader`.

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)
**Migration Section:** Section 4b verification skipped: evidence-report.md pins no `t2_future_count`. For a skill create-skill made, re-run create-skill to regenerate the report with the field (create-stack-skill does not write it).

### Structural Findings

| # | Type | Severity | Detail | Line |
|---|------|----------|--------|------|
| - | none | - | No finding across §§2.1-2.7: the description, usage and API-surface families are served by `## Overview`, `## Quick Start` and `## Key API Summary`; 10 code fences, all balanced and tagged; no table row drifts from its header; all 189 function exports are used in a usage-family section or a reference file; no export is described as async without an await, or as sync while awaited; no `scripts/` or `assets/` folder | - |

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
- **External Validation Score:** 100.0%
- **Tools used:** skill-check

## Completeness Score

**Result:** **FAIL**, not scored: the hard gate blocked this run on 1 Critical or High gap(s), listed first in the Gap Report.

## Gap Report

**Total Gaps:** 405
**Blocking (Critical + High):** 1
**Non-blocking (Medium + Low + Info):** 404

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|------------------|
| Critical | 1 | Read the source code and write or correct the documentation |
| High | 0 | None |
| Medium | 259 | Add type definitions, interface docs or the missing section |
| Low | 7 | Add examples or metadata |
| Info | 138 | Optional improvements, no action required |
| **Total** | **405** | |

### GAP-001: Signature mismatch: afterEach (form 1 of 2)

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/a11y/src/preview.tsx:14
**Export:** afterEach

**Issue:** documented `({ id, reporting, parameters, globals, viewMode }) => Promise<void>`, source `export const afterEach: AfterEach<any> = async ({ id: storyId, reporting, parameters, globals, viewMode }) => {...}; AfterEach<TRenderer, TArgs> = (context: StoryContext<TRenderer, TArgs>) => Awaitable<void>, Awaitable<T> = T | PromiseLike<T> (code/core/src/csf/story.ts:253, 262)`: documented return type Promise<void> does not cover every member the declared return Awaitable<void> (void | PromiseLike<void>) can return; the async block body has no top-level return line to name as evidence, so the declaration decides (documented form 1 of 2: `({ id, reporting, parameters, globals, viewMode }) -> Promise<void>`)

**Remediation:** Update the documented signature of `afterEach` from `({ id, reporting, parameters, globals, viewMode }) => Promise<void>` to `export const afterEach: AfterEach<any> = async ({ id: storyId, reporting, parameters, globals, viewMode }) => {...}; AfterEach<TRenderer, TArgs> = (context: StoryContext<TRenderer, TArgs>) => Awaitable<void>, Awaitable<T> = T | PromiseLike<T> (code/core/src/csf/story.ts:253, 262)`, the signature the source defines at `code/addons/a11y/src/preview.tsx:14`.

### GAP-010: Missing export: AddContext

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/mdx.tsx:27
**Export:** AddContext

**Issue:** `AddContext` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `AddContext` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/mdx.tsx:27` and add its signature, its purpose and a usage example.

### GAP-011: Missing type: AddMocks

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/renderers/react/src/public-types.ts:69
**Export:** AddMocks

**Issue:** the type `AddMocks` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `AddMocks` in SKILL.md: read its definition at `code/renderers/react/src/public-types.ts:69` and list its fields or members.

### GAP-012: Missing export: AnchorMdx

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/mdx.tsx:98
**Export:** AnchorMdx

**Issue:** `AnchorMdx` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `AnchorMdx` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/mdx.tsx:98` and add its signature, its purpose and a usage example.

### GAP-013: Missing export: CLEAR_ID

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/actions/constants.ts:5
**Export:** CLEAR_ID

**Issue:** `CLEAR_ID` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `CLEAR_ID` in SKILL.md: read its definition at `code/core/src/actions/constants.ts:5` and add its signature, its purpose and a usage example.

### GAP-014: Missing export: CYCLIC_KEY

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/actions/constants.ts:6
**Export:** CYCLIC_KEY

**Issue:** `CYCLIC_KEY` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `CYCLIC_KEY` in SKILL.md: read its definition at `code/core/src/actions/constants.ts:6` and add its signature, its purpose and a usage example.

### GAP-015: Missing export: CodeOrSourceMdx

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/mdx.tsx:39
**Export:** CodeOrSourceMdx

**Issue:** `CodeOrSourceMdx` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `CodeOrSourceMdx` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/mdx.tsx:39` and add its signature, its purpose and a usage example.

### GAP-016: Missing type: ColorProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/controls/index.tsx:10
**Export:** ColorProps

**Issue:** the type `ColorProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ColorProps` in SKILL.md: read its definition at `code/addons/docs/src/blocks/controls/index.tsx:10` and list its fields or members.

### GAP-017: Missing type: Component

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/types.ts:7
**Export:** Component

**Issue:** the type `Component` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Component` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/types.ts:7` and list its fields or members.

### GAP-018: Missing export: DEFAULT_VIEWPORT

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/viewport/defaults.ts:232
**Export:** DEFAULT_VIEWPORT

**Issue:** `DEFAULT_VIEWPORT` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `DEFAULT_VIEWPORT` in SKILL.md: read its definition at `code/core/src/viewport/defaults.ts:232` and add its signature, its purpose and a usage example.

### GAP-019: Missing type: DescriptionType

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/Description.tsx:9
**Export:** DescriptionType

**Issue:** the type `DescriptionType` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `DescriptionType` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Description.tsx:9` and list its fields or members.

### GAP-020: Missing export: EVENT_ID

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/actions/constants.ts:4
**Export:** EVENT_ID

**Issue:** `EVENT_ID` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `EVENT_ID` in SKILL.md: read its definition at `code/core/src/actions/constants.ts:4` and add its signature, its purpose and a usage example.

### GAP-021: Missing type: Easing

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/theming/types.ts:61
**Export:** Easing

**Issue:** the type `Easing` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Easing` in SKILL.md: read its definition at `code/core/src/theming/types.ts:61` and list its fields or members.

### GAP-022: Missing export: ExternalDocs

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/external/ExternalDocs.tsx:26
**Export:** ExternalDocs

**Issue:** `ExternalDocs` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `ExternalDocs` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/external/ExternalDocs.tsx:26` and add its signature, its purpose and a usage example.

### GAP-023: Missing export: ExternalDocsContainer

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/external/ExternalDocsContainer.tsx:12
**Export:** ExternalDocsContainer

**Issue:** `ExternalDocsContainer` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `ExternalDocsContainer` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/external/ExternalDocsContainer.tsx:12` and add its signature, its purpose and a usage example.

### GAP-024: Missing type: ExternalDocsProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/external/ExternalDocs.tsx:11
**Export:** ExternalDocsProps

**Issue:** the type `ExternalDocsProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ExternalDocsProps` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/external/ExternalDocs.tsx:11` and list its fields or members.

### GAP-025: Missing type: GlobalStateUpdate

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/viewport/types.ts:31
**Export:** GlobalStateUpdate

**Issue:** the type `GlobalStateUpdate` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `GlobalStateUpdate` in SKILL.md: read its definition at `code/core/src/viewport/types.ts:31` and list its fields or members.

### GAP-026: Missing export: HeaderMdx

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/mdx.tsx:215
**Export:** HeaderMdx

**Issue:** `HeaderMdx` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `HeaderMdx` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/mdx.tsx:215` and add its signature, its purpose and a usage example.

### GAP-027: Missing export: HeadersMdx

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/mdx.tsx:232
**Export:** HeadersMdx

**Issue:** `HeadersMdx` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `HeadersMdx` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/mdx.tsx:232` and add its signature, its purpose and a usage example.

### GAP-028: Missing type: HighlightTypes

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/highlight/types.ts:3
**Export:** HighlightTypes

**Issue:** the type `HighlightTypes` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `HighlightTypes` in SKILL.md: read its definition at `code/core/src/highlight/types.ts:3` and list its fields or members.

### GAP-029: Missing export: INITIAL_VIEWPORTS

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/viewport/defaults.ts:3
**Export:** INITIAL_VIEWPORTS

**Issue:** `INITIAL_VIEWPORTS` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `INITIAL_VIEWPORTS` in SKILL.md: read its definition at `code/core/src/viewport/defaults.ts:3` and add its signature, its purpose and a usage example.

### GAP-030: Missing export: MINIMAL_VIEWPORTS

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/viewport/defaults.ts:234
**Export:** MINIMAL_VIEWPORTS

**Issue:** `MINIMAL_VIEWPORTS` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `MINIMAL_VIEWPORTS` in SKILL.md: read its definition at `code/core/src/viewport/defaults.ts:234` and add its signature, its purpose and a usage example.

### GAP-031: Missing type: Of

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/useOf.ts:11
**Export:** Of

**Issue:** the type `Of` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Of` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/useOf.ts:11` and list its fields or members.

### GAP-032: Missing export: PANEL_ID

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/actions/constants.ts:3
**Export:** PANEL_ID

**Issue:** `PANEL_ID` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `PANEL_ID` in SKILL.md: read its definition at `code/core/src/actions/constants.ts:3` and add its signature, its purpose and a usage example.

### GAP-033: Missing export: PRIMARY_STORY

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/types.ts:3
**Export:** PRIMARY_STORY

**Issue:** `PRIMARY_STORY` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `PRIMARY_STORY` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/types.ts:3` and add its signature, its purpose and a usage example.

### GAP-034: Missing type: ReactTypes

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/renderers/react/src/types.ts:33
**Export:** ReactTypes

**Issue:** the type `ReactTypes` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ReactTypes` in SKILL.md: read its definition at `code/renderers/react/src/types.ts:33` and list its fields or members.

### GAP-035: Missing type: Report

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/preview-api/modules/store/reporter-api.ts:1
**Export:** Report

**Issue:** the type `Report` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Report` in SKILL.md: read its definition at `code/core/src/preview-api/modules/store/reporter-api.ts:1` and list its fields or members.

### GAP-036: Missing type: ReporterAPI

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/preview-api/modules/store/reporter-api.ts:8
**Export:** ReporterAPI

**Issue:** the type `ReporterAPI` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ReporterAPI` in SKILL.md: read its definition at `code/core/src/preview-api/modules/store/reporter-api.ts:8` and list its fields or members.

### GAP-037: Missing type: SelectionStore

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/preview-api/modules/preview-web/SelectionStore.ts:17
**Export:** SelectionStore

**Issue:** the type `SelectionStore` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SelectionStore` in SKILL.md: read its definition at `code/core/src/preview-api/modules/preview-web/SelectionStore.ts:17` and list its fields or members.

### GAP-038: Missing export: SourceContainer

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/SourceContainer.tsx:38
**Export:** SourceContainer

**Issue:** `SourceContainer` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `SourceContainer` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/SourceContainer.tsx:38` and add its signature, its purpose and a usage example.

### GAP-039: Missing export: SourceContext

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/SourceContainer.tsx:27
**Export:** SourceContext

**Issue:** `SourceContext` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `SourceContext` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/SourceContainer.tsx:27` and add its signature, its purpose and a usage example.

### GAP-040: Missing type: SourceContextProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/SourceContainer.tsx:22
**Export:** SourceContextProps

**Issue:** the type `SourceContextProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SourceContextProps` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/SourceContainer.tsx:22` and list its fields or members.

### GAP-041: Missing type: SourceItem

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/SourceContainer.tsx:15
**Export:** SourceItem

**Issue:** the type `SourceItem` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SourceItem` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/SourceContainer.tsx:15` and list its fields or members.

### GAP-042: Missing type: StorySources

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/addons/docs/src/blocks/blocks/SourceContainer.tsx:20
**Export:** StorySources

**Issue:** the type `StorySources` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `StorySources` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/SourceContainer.tsx:20` and list its fields or members.

### GAP-043: Missing export: TOOL_ID

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/viewport/constants.ts:4
**Export:** TOOL_ID

**Issue:** `TOOL_ID` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `TOOL_ID` in SKILL.md: read its definition at `code/core/src/viewport/constants.ts:4` and add its signature, its purpose and a usage example.

### GAP-044: Missing export: UNKNOWN_ARGS_HASH

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/SourceContainer.tsx:36
**Export:** UNKNOWN_ARGS_HASH

**Issue:** `UNKNOWN_ARGS_HASH` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `UNKNOWN_ARGS_HASH` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/SourceContainer.tsx:36` and add its signature, its purpose and a usage example.

### GAP-045: Missing type: UserEvent

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/test/testing-library.ts:119
**Export:** UserEvent

**Issue:** the type `UserEvent` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `UserEvent` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:119` and list its fields or members.

### GAP-046: Missing type: UserEventObject

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/test/index.ts:15
**Export:** UserEventObject

**Issue:** the type `UserEventObject` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `UserEventObject` in SKILL.md: read its definition at `code/core/src/test/index.ts:15` and list its fields or members.

### GAP-047: Missing type: View

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/preview-api/modules/preview-web/View.ts:3
**Export:** View

**Issue:** the type `View` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `View` in SKILL.md: read its definition at `code/core/src/preview-api/modules/preview-web/View.ts:3` and list its fields or members.

### GAP-048: Missing type: Viewport

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/viewport/types.ts:1
**Export:** Viewport

**Issue:** the type `Viewport` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `Viewport` in SKILL.md: read its definition at `code/core/src/viewport/types.ts:1` and list its fields or members.

### GAP-049: Missing type: ViewportGlobals

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/viewport/types.ts:56
**Export:** ViewportGlobals

**Issue:** the type `ViewportGlobals` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ViewportGlobals` in SKILL.md: read its definition at `code/core/src/viewport/types.ts:56` and list its fields or members.

### GAP-050: Missing type: ViewportMap

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/viewport/types.ts:14
**Export:** ViewportMap

**Issue:** the type `ViewportMap` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ViewportMap` in SKILL.md: read its definition at `code/core/src/viewport/types.ts:14` and list its fields or members.

### GAP-051: Missing type: ViewportTypes

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** code/core/src/viewport/types.ts:65
**Export:** ViewportTypes

**Issue:** the type `ViewportTypes` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ViewportTypes` in SKILL.md: read its definition at `code/core/src/viewport/types.ts:65` and list its fields or members.

### GAP-052: Missing export: Wrapper

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/Wrapper.tsx:10
**Export:** Wrapper

**Issue:** `Wrapper` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `Wrapper` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Wrapper.tsx:10` and add its signature, its purpose and a usage example.

### GAP-053: Missing export: actions

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/actions/runtime/actions.ts:5
**Export:** actions

**Issue:** `actions` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `actions` in SKILL.md: read its definition at `code/core/src/actions/runtime/actions.ts:5` and add its signature, its purpose and a usage example.

### GAP-054: Missing export: anchorBlockIdFromId

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/Anchor.tsx:4
**Export:** anchorBlockIdFromId

**Issue:** `anchorBlockIdFromId` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `anchorBlockIdFromId` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Anchor.tsx:4` and add its signature, its purpose and a usage example.

### GAP-055: Missing export: argsHash

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/SourceContainer.tsx:11
**Export:** argsHash

**Issue:** `argsHash` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `argsHash` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/SourceContainer.tsx:11` and add its signature, its purpose and a usage example.

### GAP-056: Missing export: assertIsFn

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/mdx.tsx:19
**Export:** assertIsFn

**Issue:** `assertIsFn` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `assertIsFn` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/mdx.tsx:19` and add its signature, its purpose and a usage example.

### GAP-057: Missing export: background

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/theming/base.ts:44
**Export:** background

**Issue:** `background` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `background` in SKILL.md: read its definition at `code/core/src/theming/base.ts:44` and add its signature, its purpose and a usage example.

### GAP-058: Missing export: buildQueries

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:40
**Export:** buildQueries

**Issue:** `buildQueries` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `buildQueries` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:40` and add its signature, its purpose and a usage example.

### GAP-059: Missing export: color

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/theming/base.ts:1
**Export:** color

**Issue:** `color` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `color` in SKILL.md: read its definition at `code/core/src/theming/base.ts:1` and add its signature, its purpose and a usage example.

### GAP-060: Missing export: config

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/actions/runtime/configureActions.ts:3
**Export:** config

**Issue:** `config` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `config` in SKILL.md: read its definition at `code/core/src/actions/runtime/configureActions.ts:3` and add its signature, its purpose and a usage example.

### GAP-061: Missing export: configure

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:41
**Export:** configure

**Issue:** `configure` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `configure` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:41` and add its signature, its purpose and a usage example.

### GAP-062: Missing export: convert

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/docs-tools/argTypes/convert/index.ts:8
**Export:** convert

**Issue:** `convert` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `convert` in SKILL.md: read its definition at `code/core/src/docs-tools/argTypes/convert/index.ts:8` and add its signature, its purpose and a usage example.

### GAP-063: Missing export: createEvent

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:42
**Export:** createEvent

**Issue:** `createEvent` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `createEvent` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:42` and add its signature, its purpose and a usage example.

### GAP-064: Missing export: createPlaywrightTest

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/preview-api/modules/store/csf/portable-stories.ts:319
**Export:** createPlaywrightTest

**Issue:** `createPlaywrightTest` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `createPlaywrightTest` in SKILL.md: read its definition at `code/core/src/preview-api/modules/store/csf/portable-stories.ts:319` and add its signature, its purpose and a usage example.

### GAP-065: Missing export: default

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/a11y/src/postinstall.ts:5
**Export:** default

**Issue:** `default` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `default` in SKILL.md: read its definition at `code/addons/a11y/src/postinstall.ts:5` and add its signature, its purpose and a usage example.

### GAP-066: Missing export: emitTransformCode

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/preview-api/modules/preview-web/emitTransformCode.ts:15
**Export:** emitTransformCode

**Issue:** `emitTransformCode` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `emitTransformCode` in SKILL.md: read its definition at `code/core/src/preview-api/modules/preview-web/emitTransformCode.ts:15` and add its signature, its purpose and a usage example.

### GAP-067: Missing export: ensure

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/theming/ensure.ts:10
**Export:** ensure

**Issue:** `ensure` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `ensure` in SKILL.md: read its definition at `code/core/src/theming/ensure.ts:10` and add its signature, its purpose and a usage example.

### GAP-068: Missing export: extractTitle

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/Title.tsx:24
**Export:** extractTitle

**Issue:** `extractTitle` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `extractTitle` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Title.tsx:24` and add its signature, its purpose and a usage example.

### GAP-069: Missing export: findAllByAltText

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:44
**Export:** findAllByAltText

**Issue:** `findAllByAltText` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `findAllByAltText` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:44` and add its signature, its purpose and a usage example.

### GAP-070: Missing export: findAllByDisplayValue

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:45
**Export:** findAllByDisplayValue

**Issue:** `findAllByDisplayValue` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `findAllByDisplayValue` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:45` and add its signature, its purpose and a usage example.

### GAP-071: Missing export: findAllByLabelText

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:46
**Export:** findAllByLabelText

**Issue:** `findAllByLabelText` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `findAllByLabelText` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:46` and add its signature, its purpose and a usage example.

### GAP-072: Missing export: findAllByPlaceholderText

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:47
**Export:** findAllByPlaceholderText

**Issue:** `findAllByPlaceholderText` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `findAllByPlaceholderText` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:47` and add its signature, its purpose and a usage example.

### GAP-073: Missing export: findAllByRole

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:48
**Export:** findAllByRole

**Issue:** `findAllByRole` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `findAllByRole` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:48` and add its signature, its purpose and a usage example.

### GAP-074: Missing export: findAllByTestId

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:49
**Export:** findAllByTestId

**Issue:** `findAllByTestId` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `findAllByTestId` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:49` and add its signature, its purpose and a usage example.

### GAP-075: Missing export: findAllByText

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:50
**Export:** findAllByText

**Issue:** `findAllByText` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `findAllByText` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:50` and add its signature, its purpose and a usage example.

### GAP-076: Missing export: findAllByTitle

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:51
**Export:** findAllByTitle

**Issue:** `findAllByTitle` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `findAllByTitle` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:51` and add its signature, its purpose and a usage example.

### GAP-077: Missing export: findByAltText

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:52
**Export:** findByAltText

**Issue:** `findByAltText` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `findByAltText` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:52` and add its signature, its purpose and a usage example.

### GAP-078: Missing export: findByDisplayValue

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:53
**Export:** findByDisplayValue

**Issue:** `findByDisplayValue` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `findByDisplayValue` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:53` and add its signature, its purpose and a usage example.

### GAP-079: Missing export: findByLabelText

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:54
**Export:** findByLabelText

**Issue:** `findByLabelText` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `findByLabelText` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:54` and add its signature, its purpose and a usage example.

### GAP-080: Missing export: findByPlaceholderText

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:55
**Export:** findByPlaceholderText

**Issue:** `findByPlaceholderText` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `findByPlaceholderText` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:55` and add its signature, its purpose and a usage example.

### GAP-081: Missing export: findByTestId

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:57
**Export:** findByTestId

**Issue:** `findByTestId` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `findByTestId` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:57` and add its signature, its purpose and a usage example.

### GAP-082: Missing export: findByText

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:58
**Export:** findByText

**Issue:** `findByText` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `findByText` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:58` and add its signature, its purpose and a usage example.

### GAP-083: Missing export: findByTitle

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:59
**Export:** findByTitle

**Issue:** `findByTitle` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `findByTitle` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:59` and add its signature, its purpose and a usage example.

### GAP-084: Missing export: getAllByAltText

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:60
**Export:** getAllByAltText

**Issue:** `getAllByAltText` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getAllByAltText` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:60` and add its signature, its purpose and a usage example.

### GAP-085: Missing export: getAllByDisplayValue

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:61
**Export:** getAllByDisplayValue

**Issue:** `getAllByDisplayValue` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getAllByDisplayValue` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:61` and add its signature, its purpose and a usage example.

### GAP-086: Missing export: getAllByLabelText

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:62
**Export:** getAllByLabelText

**Issue:** `getAllByLabelText` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getAllByLabelText` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:62` and add its signature, its purpose and a usage example.

### GAP-087: Missing export: getAllByPlaceholderText

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:63
**Export:** getAllByPlaceholderText

**Issue:** `getAllByPlaceholderText` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getAllByPlaceholderText` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:63` and add its signature, its purpose and a usage example.

### GAP-088: Missing export: getAllByRole

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:64
**Export:** getAllByRole

**Issue:** `getAllByRole` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getAllByRole` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:64` and add its signature, its purpose and a usage example.

### GAP-089: Missing export: getAllByTestId

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:65
**Export:** getAllByTestId

**Issue:** `getAllByTestId` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getAllByTestId` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:65` and add its signature, its purpose and a usage example.

### GAP-090: Missing export: getAllByText

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:66
**Export:** getAllByText

**Issue:** `getAllByText` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getAllByText` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:66` and add its signature, its purpose and a usage example.

### GAP-091: Missing export: getAllByTitle

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:67
**Export:** getAllByTitle

**Issue:** `getAllByTitle` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getAllByTitle` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:67` and add its signature, its purpose and a usage example.

### GAP-092: Missing export: getByAltText

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:68
**Export:** getByAltText

**Issue:** `getByAltText` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getByAltText` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:68` and add its signature, its purpose and a usage example.

### GAP-093: Missing export: getByDisplayValue

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:69
**Export:** getByDisplayValue

**Issue:** `getByDisplayValue` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getByDisplayValue` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:69` and add its signature, its purpose and a usage example.

### GAP-094: Missing export: getByLabelText

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:70
**Export:** getByLabelText

**Issue:** `getByLabelText` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getByLabelText` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:70` and add its signature, its purpose and a usage example.

### GAP-095: Missing export: getByPlaceholderText

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:71
**Export:** getByPlaceholderText

**Issue:** `getByPlaceholderText` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getByPlaceholderText` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:71` and add its signature, its purpose and a usage example.

### GAP-096: Missing export: getByTestId

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:73
**Export:** getByTestId

**Issue:** `getByTestId` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getByTestId` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:73` and add its signature, its purpose and a usage example.

### GAP-097: Missing export: getByText

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:74
**Export:** getByText

**Issue:** `getByText` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getByText` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:74` and add its signature, its purpose and a usage example.

### GAP-098: Missing export: getByTitle

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:75
**Export:** getByTitle

**Issue:** `getByTitle` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getByTitle` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:75` and add its signature, its purpose and a usage example.

### GAP-099: Missing export: getConfig

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:76
**Export:** getConfig

**Issue:** `getConfig` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getConfig` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:76` and add its signature, its purpose and a usage example.

### GAP-100: Missing export: getCsfFactoryAnnotations

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/preview-api/modules/store/csf/csf-factory-utils.ts:10
**Export:** getCsfFactoryAnnotations

**Issue:** `getCsfFactoryAnnotations` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getCsfFactoryAnnotations` in SKILL.md: read its definition at `code/core/src/preview-api/modules/store/csf/csf-factory-utils.ts:10` and add its signature, its purpose and a usage example.

### GAP-101: Missing export: getDefaultNormalizer

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:77
**Export:** getDefaultNormalizer

**Issue:** `getDefaultNormalizer` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getDefaultNormalizer` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:77` and add its signature, its purpose and a usage example.

### GAP-102: Missing export: getElementError

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:78
**Export:** getElementError

**Issue:** `getElementError` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getElementError` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:78` and add its signature, its purpose and a usage example.

### GAP-103: Missing export: getNodeText

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:79
**Export:** getNodeText

**Issue:** `getNodeText` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getNodeText` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:79` and add its signature, its purpose and a usage example.

### GAP-104: Missing export: getQueriesForElement

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:80
**Export:** getQueriesForElement

**Issue:** `getQueriesForElement` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getQueriesForElement` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:80` and add its signature, its purpose and a usage example.

### GAP-105: Missing export: getRoles

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:81
**Export:** getRoles

**Issue:** `getRoles` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getRoles` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:81` and add its signature, its purpose and a usage example.

### GAP-106: Missing export: getStoryId

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/Story.tsx:62
**Export:** getStoryId

**Issue:** `getStoryId` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getStoryId` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Story.tsx:62` and add its signature, its purpose and a usage example.

### GAP-107: Missing export: getStoryProps

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/Story.tsx:75
**Export:** getStoryProps

**Issue:** `getStoryProps` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getStoryProps` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Story.tsx:75` and add its signature, its purpose and a usage example.

### GAP-108: Missing export: getSuggestedQuery

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:82
**Export:** getSuggestedQuery

**Issue:** `getSuggestedQuery` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `getSuggestedQuery` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:82` and add its signature, its purpose and a usage example.

### GAP-109: Missing export: isInaccessible

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:83
**Export:** isInaccessible

**Issue:** `isInaccessible` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `isInaccessible` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:83` and add its signature, its purpose and a usage example.

### GAP-110: Missing export: logDOM

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:84
**Export:** logDOM

**Issue:** `logDOM` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `logDOM` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:84` and add its signature, its purpose and a usage example.

### GAP-111: Missing export: logRoles

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:85
**Export:** logRoles

**Issue:** `logRoles` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `logRoles` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:85` and add its signature, its purpose and a usage example.

### GAP-112: Missing export: pauseAnimations

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/preview-api/modules/preview-web/render/animation-utils.ts:18
**Export:** pauseAnimations

**Issue:** `pauseAnimations` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `pauseAnimations` in SKILL.md: read its definition at `code/core/src/preview-api/modules/preview-web/render/animation-utils.ts:18` and add its signature, its purpose and a usage example.

### GAP-113: Missing export: prettyDOM

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:86
**Export:** prettyDOM

**Issue:** `prettyDOM` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `prettyDOM` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:86` and add its signature, its purpose and a usage example.

### GAP-114: Missing export: prettyFormat

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:111
**Export:** prettyFormat

**Issue:** `prettyFormat` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `prettyFormat` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:111` and add its signature, its purpose and a usage example.

### GAP-115: Missing export: queries

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:87
**Export:** queries

**Issue:** `queries` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `queries` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:87` and add its signature, its purpose and a usage example.

### GAP-116: Missing export: queryAllByAltText

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:88
**Export:** queryAllByAltText

**Issue:** `queryAllByAltText` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `queryAllByAltText` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:88` and add its signature, its purpose and a usage example.

### GAP-117: Missing export: queryAllByAttribute

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:89
**Export:** queryAllByAttribute

**Issue:** `queryAllByAttribute` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `queryAllByAttribute` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:89` and add its signature, its purpose and a usage example.

### GAP-118: Missing export: queryAllByDisplayValue

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:90
**Export:** queryAllByDisplayValue

**Issue:** `queryAllByDisplayValue` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `queryAllByDisplayValue` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:90` and add its signature, its purpose and a usage example.

### GAP-119: Missing export: queryAllByLabelText

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:91
**Export:** queryAllByLabelText

**Issue:** `queryAllByLabelText` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `queryAllByLabelText` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:91` and add its signature, its purpose and a usage example.

### GAP-120: Missing export: queryAllByPlaceholderText

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:92
**Export:** queryAllByPlaceholderText

**Issue:** `queryAllByPlaceholderText` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `queryAllByPlaceholderText` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:92` and add its signature, its purpose and a usage example.

### GAP-121: Missing export: queryAllByRole

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:93
**Export:** queryAllByRole

**Issue:** `queryAllByRole` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `queryAllByRole` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:93` and add its signature, its purpose and a usage example.

### GAP-122: Missing export: queryAllByTestId

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:94
**Export:** queryAllByTestId

**Issue:** `queryAllByTestId` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `queryAllByTestId` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:94` and add its signature, its purpose and a usage example.

### GAP-123: Missing export: queryAllByText

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:95
**Export:** queryAllByText

**Issue:** `queryAllByText` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `queryAllByText` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:95` and add its signature, its purpose and a usage example.

### GAP-124: Missing export: queryAllByTitle

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:96
**Export:** queryAllByTitle

**Issue:** `queryAllByTitle` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `queryAllByTitle` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:96` and add its signature, its purpose and a usage example.

### GAP-125: Missing export: queryByAltText

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:97
**Export:** queryByAltText

**Issue:** `queryByAltText` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `queryByAltText` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:97` and add its signature, its purpose and a usage example.

### GAP-126: Missing export: queryByAttribute

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:98
**Export:** queryByAttribute

**Issue:** `queryByAttribute` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `queryByAttribute` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:98` and add its signature, its purpose and a usage example.

### GAP-127: Missing export: queryByDisplayValue

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:99
**Export:** queryByDisplayValue

**Issue:** `queryByDisplayValue` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `queryByDisplayValue` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:99` and add its signature, its purpose and a usage example.

### GAP-128: Missing export: queryByLabelText

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:100
**Export:** queryByLabelText

**Issue:** `queryByLabelText` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `queryByLabelText` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:100` and add its signature, its purpose and a usage example.

### GAP-129: Missing export: queryByPlaceholderText

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:101
**Export:** queryByPlaceholderText

**Issue:** `queryByPlaceholderText` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `queryByPlaceholderText` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:101` and add its signature, its purpose and a usage example.

### GAP-130: Missing export: queryByTestId

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:103
**Export:** queryByTestId

**Issue:** `queryByTestId` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `queryByTestId` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:103` and add its signature, its purpose and a usage example.

### GAP-131: Missing export: queryByText

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:104
**Export:** queryByText

**Issue:** `queryByText` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `queryByText` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:104` and add its signature, its purpose and a usage example.

### GAP-132: Missing export: queryByTitle

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:105
**Export:** queryByTitle

**Issue:** `queryByTitle` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `queryByTitle` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:105` and add its signature, its purpose and a usage example.

### GAP-133: Missing export: queryHelpers

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:106
**Export:** queryHelpers

**Issue:** `queryHelpers` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `queryHelpers` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:106` and add its signature, its purpose and a usage example.

### GAP-134: Missing export: responsiveViewport

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/viewport/responsiveViewport.tsx:4
**Export:** responsiveViewport

**Issue:** `responsiveViewport` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `responsiveViewport` in SKILL.md: read its definition at `code/core/src/viewport/responsiveViewport.tsx:4` and add its signature, its purpose and a usage example.

### GAP-135: Missing export: simulateDOMContentLoaded

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/preview-api/modules/preview-web/simulate-pageload.ts:31
**Export:** simulateDOMContentLoaded

**Issue:** `simulateDOMContentLoaded` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `simulateDOMContentLoaded` in SKILL.md: read its definition at `code/core/src/preview-api/modules/preview-web/simulate-pageload.ts:31` and add its signature, its purpose and a usage example.

### GAP-136: Missing export: simulatePageLoad

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/preview-api/modules/preview-web/simulate-pageload.ts:83
**Export:** simulatePageLoad

**Issue:** `simulatePageLoad` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `simulatePageLoad` in SKILL.md: read its definition at `code/core/src/preview-api/modules/preview-web/simulate-pageload.ts:83` and add its signature, its purpose and a usage example.

### GAP-137: Missing export: slugs

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/Heading.tsx:15
**Export:** slugs

**Issue:** `slugs` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `slugs` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Heading.tsx:15` and add its signature, its purpose and a usage example.

### GAP-138: Missing export: tokens

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/theming/base.ts:104
**Export:** tokens

**Issue:** `tokens` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `tokens` in SKILL.md: read its definition at `code/core/src/theming/base.ts:104` and add its signature, its purpose and a usage example.

### GAP-139: Missing export: typography

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/theming/base.ts:59
**Export:** typography

**Issue:** `typography` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `typography` in SKILL.md: read its definition at `code/core/src/theming/base.ts:59` and add its signature, its purpose and a usage example.

### GAP-140: Missing export: uninstrumentedUserEvent

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:121
**Export:** uninstrumentedUserEvent

**Issue:** `uninstrumentedUserEvent` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `uninstrumentedUserEvent` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:121` and add its signature, its purpose and a usage example.

### GAP-141: Missing export: useSourceProps

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/addons/docs/src/blocks/blocks/Source.tsx:101
**Export:** useSourceProps

**Issue:** `useSourceProps` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `useSourceProps` in SKILL.md: read its definition at `code/addons/docs/src/blocks/blocks/Source.tsx:101` and add its signature, its purpose and a usage example.

### GAP-142: Missing export: waitForAnimations

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/preview-api/modules/preview-web/render/animation-utils.ts:54
**Export:** waitForAnimations

**Issue:** `waitForAnimations` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `waitForAnimations` in SKILL.md: read its definition at `code/core/src/preview-api/modules/preview-web/render/animation-utils.ts:54` and add its signature, its purpose and a usage example.

### GAP-143: Missing export: waitForElementToBeRemoved

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** code/core/src/test/testing-library.ts:109
**Export:** waitForElementToBeRemoved

**Issue:** `waitForElementToBeRemoved` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `waitForElementToBeRemoved` in SKILL.md: read its definition at `code/core/src/test/testing-library.ts:109` and add its signature, its purpose and a usage example.

### GAP-144: Stale documentation: A

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:204
**Export:** A

**Issue:** `SKILL.md:204` documents `A`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/A.tsx:7` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `A` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/A.tsx:7`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `A` at SKILL.md:204.

### GAP-147: Stale documentation: ActionBar

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:316
**Export:** ActionBar

**Issue:** `references/core-api.md:316` documents `ActionBar`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/ActionBar/ActionBar.tsx:89` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `ActionBar` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/ActionBar/ActionBar.tsx:89`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `ActionBar` at references/core-api.md:316.

### GAP-148: Stale documentation: ActionList

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:316
**Export:** ActionList

**Issue:** `references/core-api.md:316` documents `ActionList`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/ActionList/ActionList.tsx:222` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `ActionList` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/ActionList/ActionList.tsx:222`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `ActionList` at references/core-api.md:316.

### GAP-149: Stale documentation: AddonPanel

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:313
**Export:** AddonPanel

**Issue:** `references/core-api.md:313` documents `AddonPanel`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/addon-panel/addon-panel.tsx:36` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `AddonPanel` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/addon-panel/addon-panel.tsx:36`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `AddonPanel` at references/core-api.md:313.

### GAP-150: Stale documentation: Args

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:131
**Export:** Args

**Issue:** SKILL.md documents `Args`, which the enumerated source API surface lacks

**Remediation:** Check `Args` against the source and update or remove its documentation at SKILL.md:131: the enumerated source surface does not export it.

### GAP-151: Stale documentation: ArgsTableProps

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/doc-blocks.md:141
**Export:** ArgsTableProps

**Issue:** SKILL.md documents `ArgsTableProps`, which the enumerated source API surface lacks

**Remediation:** Check `ArgsTableProps` against the source and update or remove its documentation at references/doc-blocks.md:141: the enumerated source surface does not export it.

### GAP-153: Stale documentation: Badge

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:311
**Export:** Badge

**Issue:** `references/core-api.md:311` documents `Badge`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Badge/Badge.tsx:88` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Badge` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Badge/Badge.tsx:88`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Badge` at references/core-api.md:311.

### GAP-154: Stale documentation: Bar

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:316
**Export:** Bar

**Issue:** `references/core-api.md:316` documents `Bar`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Bar/Bar.tsx:52` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Bar` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Bar/Bar.tsx:52`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Bar` at references/core-api.md:316.

### GAP-156: Stale documentation: Blockquote

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:311
**Export:** Blockquote

**Issue:** `references/core-api.md:311` documents `Blockquote`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/Blockquote.tsx:6` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Blockquote` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/Blockquote.tsx:6`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Blockquote` at references/core-api.md:311.

### GAP-157: Stale documentation: Button

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:44
**Export:** Button

**Issue:** `SKILL.md:44` documents `Button`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Button/Button.tsx:53` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Button` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Button/Button.tsx:53`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Button` at SKILL.md:44.

### GAP-161: Stale documentation: CSSObject

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:177
**Export:** CSSObject

**Issue:** SKILL.md documents `CSSObject`, which the enumerated source API surface lacks

**Remediation:** Check `CSSObject` against the source and update or remove its documentation at references/core-api.md:177: the enumerated source surface does not export it.

### GAP-162: Stale documentation: CacheProvider

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:170
**Export:** CacheProvider

**Issue:** SKILL.md documents `CacheProvider`, which the enumerated source API surface lacks

**Remediation:** Check `CacheProvider` against the source and update or remove its documentation at references/core-api.md:170: the enumerated source surface does not export it.

### GAP-165: Stale documentation: CanvasProps

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/doc-blocks.md:37
**Export:** CanvasProps

**Issue:** SKILL.md documents `CanvasProps`, which the enumerated source API surface lacks

**Remediation:** Check `CanvasProps` against the source and update or remove its documentation at references/doc-blocks.md:37: the enumerated source surface does not export it.

### GAP-166: Stale documentation: Card

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:313
**Export:** Card

**Issue:** `references/core-api.md:313` documents `Card`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Card/Card.tsx:98` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Card` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Card/Card.tsx:98`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Card` at references/core-api.md:313.

### GAP-168: Stale documentation: Channel

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:126
**Export:** Channel

**Issue:** `references/core-api.md:126` documents `Channel`, which the entry point `code/core/src/channels/index.ts` exports and `code/core/src/channels/main.ts:22` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Channel` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/channels/main.ts:22`, where it is defined, since its `scope.exclude` glob `code/core/src/channels/**` matches that file. To keep its documentation, narrow `code/core/src/channels/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Channel` at references/core-api.md:126.

### GAP-169: Stale documentation: CheckboxControl

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/doc-blocks.md:211
**Export:** CheckboxControl

**Issue:** SKILL.md documents `CheckboxControl`, which the enumerated source API surface lacks

**Remediation:** Check `CheckboxControl` against the source and update or remove its documentation at references/doc-blocks.md:211: the enumerated source surface does not export it.

### GAP-170: Stale documentation: ClassNames

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:170
**Export:** ClassNames

**Issue:** SKILL.md documents `ClassNames`, which the enumerated source API surface lacks

**Remediation:** Check `ClassNames` against the source and update or remove its documentation at references/core-api.md:170: the enumerated source surface does not export it.

### GAP-171: Stale documentation: Code

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:311
**Export:** Code

**Issue:** `references/core-api.md:311` documents `Code`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/Code.tsx:42` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Code` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/Code.tsx:42`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Code` at references/core-api.md:311.

### GAP-172: Stale documentation: Collapsible

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:313
**Export:** Collapsible

**Issue:** `references/core-api.md:313` documents `Collapsible`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Collapsible/Collapsible.tsx:31` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Collapsible` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Collapsible/Collapsible.tsx:31`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Collapsible` at references/core-api.md:313.

### GAP-173: Stale documentation: ColorControlProps

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/doc-blocks.md:192
**Export:** ColorControlProps

**Issue:** SKILL.md documents `ColorControlProps`, which the enumerated source API surface lacks

**Remediation:** Check `ColorControlProps` against the source and update or remove its documentation at references/doc-blocks.md:192: the enumerated source surface does not export it.

### GAP-177: Stale documentation: ConfigFile

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:336
**Export:** ConfigFile

**Issue:** `references/core-api.md:336` documents `ConfigFile`, which the entry point `code/core/src/csf-tools/index.ts` exports and `code/core/src/csf-tools/ConfigFile.ts:140` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `ConfigFile` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/csf-tools/ConfigFile.ts:140`, where it is defined, since its `scope.exclude` glob `code/core/src/csf-tools/**` matches that file. To keep its documentation, narrow `code/core/src/csf-tools/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `ConfigFile` at references/core-api.md:336.

### GAP-178: Stale documentation: CsfFile

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:336
**Export:** CsfFile

**Issue:** `references/core-api.md:336` documents `CsfFile`, which the entry point `code/core/src/csf-tools/index.ts` exports and `code/core/src/csf-tools/CsfFile.ts:280` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `CsfFile` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/csf-tools/CsfFile.ts:280`, where it is defined, since its `scope.exclude` glob `code/core/src/csf-tools/**` matches that file. To keep its documentation, narrow `code/core/src/csf-tools/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `CsfFile` at references/core-api.md:336.

### GAP-179: Stale documentation: DL

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:311
**Export:** DL

**Issue:** `references/core-api.md:311` documents `DL`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/DL.tsx:6` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `DL` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/DL.tsx:6`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `DL` at references/core-api.md:311.

### GAP-181: Stale documentation: Div

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:311
**Export:** Div

**Issue:** `references/core-api.md:311` documents `Div`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/Div.tsx:5` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Div` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/Div.tsx:5`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Div` at references/core-api.md:311.

### GAP-184: Stale documentation: ErrorFormatter

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:317
**Export:** ErrorFormatter

**Issue:** `references/core-api.md:317` documents `ErrorFormatter`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/ErrorFormatter/ErrorFormatter.tsx:29` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `ErrorFormatter` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/ErrorFormatter/ErrorFormatter.tsx:29`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `ErrorFormatter` at references/core-api.md:317.

### GAP-186: Stale documentation: FlexBar

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:316
**Export:** FlexBar

**Issue:** `references/core-api.md:316` documents `FlexBar`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Bar/Bar.tsx:129` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `FlexBar` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Bar/Bar.tsx:129`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `FlexBar` at references/core-api.md:316.

### GAP-187: Stale documentation: Form

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:312
**Export:** Form

**Issue:** `references/core-api.md:312` documents `Form`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Form/Form.tsx:11` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Form` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Form/Form.tsx:11`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Form` at references/core-api.md:312.

### GAP-189: Stale documentation: Global

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:56
**Export:** Global

**Issue:** SKILL.md documents `Global`, which the enumerated source API surface lacks

**Remediation:** Check `Global` against the source and update or remove its documentation at references/core-api.md:56: the enumerated source surface does not export it.

### GAP-192: Stale documentation: H1

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:311
**Export:** H1

**Issue:** `references/core-api.md:311` documents `H1`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/H1.tsx:6` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `H1` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/H1.tsx:6`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `H1` at references/core-api.md:311.

### GAP-193: Stale documentation: H6

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:311
**Export:** H6

**Issue:** `references/core-api.md:311` documents `H6`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/H6.tsx:6` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `H6` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/H6.tsx:6`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `H6` at references/core-api.md:311.

### GAP-194: Stale documentation: HR

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:311
**Export:** HR

**Issue:** `references/core-api.md:311` documents `HR`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/HR.tsx:3` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `HR` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/HR.tsx:3`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `HR` at references/core-api.md:311.

### GAP-196: Stale documentation: IconButton

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:312
**Export:** IconButton

**Issue:** `references/core-api.md:312` documents `IconButton`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Button/Button.tsx:327` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `IconButton` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Button/Button.tsx:327`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `IconButton` at references/core-api.md:312.

### GAP-201: Stale documentation: Keyframes

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:177
**Export:** Keyframes

**Issue:** SKILL.md documents `Keyframes`, which the enumerated source API surface lacks

**Remediation:** Check `Keyframes` against the source and update or remove its documentation at references/core-api.md:177: the enumerated source surface does not export it.

### GAP-202: Stale documentation: LI

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:311
**Export:** LI

**Issue:** `references/core-api.md:311` documents `LI`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/LI.tsx:6` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `LI` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/LI.tsx:6`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `LI` at references/core-api.md:311.

### GAP-207: Stale documentation: MarkdownProps

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/doc-blocks.md:110
**Export:** MarkdownProps

**Issue:** SKILL.md documents `MarkdownProps`, which the enumerated source API surface lacks

**Remediation:** Check `MarkdownProps` against the source and update or remove its documentation at references/doc-blocks.md:110: the enumerated source surface does not export it.

### GAP-208: Stale documentation: MaybeMocked

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:62
**Export:** MaybeMocked

**Issue:** SKILL.md documents `MaybeMocked`, which the enumerated source API surface lacks

**Remediation:** Check `MaybeMocked` against the source and update or remove its documentation at references/core-api.md:62: the enumerated source surface does not export it.

### GAP-210: Stale documentation: MetaProps

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/doc-blocks.md:74
**Export:** MetaProps

**Issue:** SKILL.md documents `MetaProps`, which the enumerated source API surface lacks

**Remediation:** Check `MetaProps` against the source and update or remove its documentation at references/doc-blocks.md:74: the enumerated source surface does not export it.

### GAP-215: Stale documentation: Mock

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:135
**Export:** Mock

**Issue:** SKILL.md documents `Mock`, which the enumerated source API surface lacks

**Remediation:** Check `Mock` against the source and update or remove its documentation at SKILL.md:135: the enumerated source surface does not export it.

### GAP-216: Stale documentation: MockInstance

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:62
**Export:** MockInstance

**Issue:** SKILL.md documents `MockInstance`, which the enumerated source API surface lacks

**Remediation:** Check `MockInstance` against the source and update or remove its documentation at references/core-api.md:62: the enumerated source surface does not export it.

### GAP-218: Stale documentation: Modal

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:313
**Export:** Modal

**Issue:** `references/core-api.md:313` documents `Modal`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Modal/Modal.tsx:242` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Modal` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Modal/Modal.tsx:242`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Modal` at references/core-api.md:313.

### GAP-223: Stale documentation: NodePath

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:341
**Export:** NodePath

**Issue:** SKILL.md documents `NodePath`, which the enumerated source API surface lacks

**Remediation:** Check `NodePath` against the source and update or remove its documentation at references/core-api.md:341: the enumerated source surface does not export it.

### GAP-227: Stale documentation: NumberProps

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/doc-blocks.md:202
**Export:** NumberProps

**Issue:** SKILL.md documents `NumberProps`, which the enumerated source API surface lacks

**Remediation:** Check `NumberProps` against the source and update or remove its documentation at references/doc-blocks.md:202: the enumerated source surface does not export it.

### GAP-229: Stale documentation: OL

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:311
**Export:** OL

**Issue:** `references/core-api.md:311` documents `OL`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/OL.tsx:16` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `OL` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/OL.tsx:16`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `OL` at references/core-api.md:311.

### GAP-230: Stale documentation: P

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:311
**Export:** P

**Issue:** `references/core-api.md:311` documents `P`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/P.tsx:6` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `P` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/P.tsx:6`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `P` at references/core-api.md:311.

### GAP-232: Stale documentation: Parameters

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/addons.md:126
**Export:** Parameters

**Issue:** SKILL.md documents `Parameters`, which the enumerated source API surface lacks

**Remediation:** Check `Parameters` against the source and update or remove its documentation at references/addons.md:126: the enumerated source surface does not export it.

### GAP-233: Stale documentation: Placeholder

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:317
**Export:** Placeholder

**Issue:** `references/core-api.md:317` documents `Placeholder`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/placeholder/placeholder.tsx:22` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Placeholder` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/placeholder/placeholder.tsx:22`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Placeholder` at references/core-api.md:317.

### GAP-234: Stale documentation: PlayFunction

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:258
**Export:** PlayFunction

**Issue:** SKILL.md documents `PlayFunction`, which the enumerated source API surface lacks

**Remediation:** Check `PlayFunction` against the source and update or remove its documentation at references/core-api.md:258: the enumerated source surface does not export it.

### GAP-235: Stale documentation: Popover

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:315
**Export:** Popover

**Issue:** `references/core-api.md:315` documents `Popover`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Popover/Popover.tsx:77` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Popover` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Popover/Popover.tsx:77`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Popover` at references/core-api.md:315.

### GAP-236: Stale documentation: PopoverProvider

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:315
**Export:** PopoverProvider

**Issue:** `references/core-api.md:315` documents `PopoverProvider`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Popover/PopoverProvider.tsx:63` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `PopoverProvider` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Popover/PopoverProvider.tsx:63`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `PopoverProvider` at references/core-api.md:315.

### GAP-237: Stale documentation: PostMessageTransport

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:329
**Export:** PostMessageTransport

**Issue:** `references/core-api.md:329` documents `PostMessageTransport`, which the entry point `code/core/src/channels/index.ts` exports and `code/core/src/channels/postmessage/index.ts:29` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `PostMessageTransport` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/channels/postmessage/index.ts:29`, where it is defined, since its `scope.exclude` glob `code/core/src/channels/**` matches that file. To keep its documentation, narrow `code/core/src/channels/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `PostMessageTransport` at references/core-api.md:329.

### GAP-238: Stale documentation: Pre

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:311
**Export:** Pre

**Issue:** `references/core-api.md:311` documents `Pre`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/Pre.tsx:6` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Pre` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/Pre.tsx:6`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Pre` at references/core-api.md:311.

### GAP-240: Stale documentation: ProjectAnnotations

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:134
**Export:** ProjectAnnotations

**Issue:** SKILL.md documents `ProjectAnnotations`, which the enumerated source API surface lacks

**Remediation:** Check `ProjectAnnotations` against the source and update or remove its documentation at SKILL.md:134: the enumerated source surface does not export it.

### GAP-241: Stale documentation: RadioControl

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/doc-blocks.md:211
**Export:** RadioControl

**Issue:** SKILL.md documents `RadioControl`, which the enumerated source API surface lacks

**Remediation:** Check `RadioControl` against the source and update or remove its documentation at references/doc-blocks.md:211: the enumerated source surface does not export it.

### GAP-242: Stale documentation: RangeProps

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/doc-blocks.md:207
**Export:** RangeProps

**Issue:** SKILL.md documents `RangeProps`, which the enumerated source API surface lacks

**Remediation:** Check `RangeProps` against the source and update or remove its documentation at references/doc-blocks.md:207: the enumerated source surface does not export it.

### GAP-252: Stale documentation: ScrollArea

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:313
**Export:** ScrollArea

**Issue:** `references/core-api.md:313` documents `ScrollArea`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/ScrollArea/ScrollArea.tsx:95` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `ScrollArea` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/ScrollArea/ScrollArea.tsx:95`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `ScrollArea` at references/core-api.md:313.

### GAP-253: Stale documentation: Select

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:312
**Export:** Select

**Issue:** `references/core-api.md:312` documents `Select`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Select/Select.tsx:201` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Select` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Select/Select.tsx:201`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Select` at references/core-api.md:312.

### GAP-254: Stale documentation: SelectControl

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/doc-blocks.md:211
**Export:** SelectControl

**Issue:** SKILL.md documents `SelectControl`, which the enumerated source API surface lacks

**Remediation:** Check `SelectControl` against the source and update or remove its documentation at references/doc-blocks.md:211: the enumerated source surface does not export it.

### GAP-256: Stale documentation: Spaced

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:317
**Export:** Spaced

**Issue:** `references/core-api.md:317` documents `Spaced`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/spaced/Spaced.tsx:63` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Spaced` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/spaced/Spaced.tsx:63`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Spaced` at references/core-api.md:317.

### GAP-257: Stale documentation: Span

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:311
**Export:** Span

**Issue:** `references/core-api.md:311` documents `Span`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/Span.tsx:6` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Span` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/Span.tsx:6`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Span` at references/core-api.md:311.

### GAP-265: Stale documentation: StoryIndexGenerator

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:339
**Export:** StoryIndexGenerator

**Issue:** `references/core-api.md:339` documents `StoryIndexGenerator`, which the entry point `code/core/src/core-server/index.ts` exports and `code/core/src/core-server/utils/StoryIndexGenerator.ts:101` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `StoryIndexGenerator` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/core-server/utils/StoryIndexGenerator.ts:101`, where it is defined, since its `scope.exclude` glob `code/core/src/core-server/**` matches that file. To keep its documentation, narrow `code/core/src/core-server/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `StoryIndexGenerator` at references/core-api.md:339.

### GAP-268: Stale documentation: StorybookIcon

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:318
**Export:** StorybookIcon

**Issue:** `references/core-api.md:318` documents `StorybookIcon`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/brand/StorybookIcon.tsx:3` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `StorybookIcon` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/brand/StorybookIcon.tsx:3`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `StorybookIcon` at references/core-api.md:318.

### GAP-269: Stale documentation: StorybookLogo

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:318
**Export:** StorybookLogo

**Issue:** `references/core-api.md:318` documents `StorybookLogo`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/brand/StorybookLogo.tsx:7` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `StorybookLogo` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/brand/StorybookLogo.tsx:7`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `StorybookLogo` at references/core-api.md:318.

### GAP-273: Stale documentation: SubtitleProps

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/doc-blocks.md:76
**Export:** SubtitleProps

**Issue:** SKILL.md documents `SubtitleProps`, which the enumerated source API surface lacks

**Remediation:** Check `SubtitleProps` against the source and update or remove its documentation at references/doc-blocks.md:76: the enumerated source surface does not export it.

### GAP-274: Stale documentation: SyntaxHighlighter

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:317
**Export:** SyntaxHighlighter

**Issue:** `references/core-api.md:317` documents `SyntaxHighlighter`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/syntaxhighlighter/lazy-syntaxhighlighter.tsx:52` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `SyntaxHighlighter` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/syntaxhighlighter/lazy-syntaxhighlighter.tsx:52`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `SyntaxHighlighter` at references/core-api.md:317.

### GAP-276: Stale documentation: TabBar

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:314
**Export:** TabBar

**Issue:** `references/core-api.md:314` documents `TabBar`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Tabs/Tabs.tsx:61` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `TabBar` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Tabs/Tabs.tsx:61`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `TabBar` at references/core-api.md:314.

### GAP-277: Stale documentation: TabButton

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:314
**Export:** TabButton

**Issue:** `references/core-api.md:314` documents `TabButton`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Tabs/Button.tsx:139` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `TabButton` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Tabs/Button.tsx:139`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `TabButton` at references/core-api.md:314.

### GAP-278: Stale documentation: TabList

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:314
**Export:** TabList

**Issue:** `references/core-api.md:314` documents `TabList`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Tabs/TabList.tsx:150` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `TabList` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Tabs/TabList.tsx:150`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `TabList` at references/core-api.md:314.

### GAP-279: Stale documentation: TabPanel

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:314
**Export:** TabPanel

**Issue:** `references/core-api.md:314` documents `TabPanel`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Tabs/TabPanel.tsx:34` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `TabPanel` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Tabs/TabPanel.tsx:34`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `TabPanel` at references/core-api.md:314.

### GAP-280: Stale documentation: TabWrapper

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:314
**Export:** TabWrapper

**Issue:** `references/core-api.md:314` documents `TabWrapper`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Tabs/Tabs.tsx:120` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `TabWrapper` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Tabs/Tabs.tsx:120`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `TabWrapper` at references/core-api.md:314.

### GAP-281: Stale documentation: Table

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:311
**Export:** Table

**Issue:** `references/core-api.md:311` documents `Table`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/Table.tsx:6` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Table` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/Table.tsx:6`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Table` at references/core-api.md:311.

### GAP-282: Stale documentation: Tabs

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:314
**Export:** Tabs

**Issue:** `references/core-api.md:314` documents `Tabs`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Tabs/Tabs.tsx:188` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Tabs` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Tabs/Tabs.tsx:188`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Tabs` at references/core-api.md:314.

### GAP-283: Stale documentation: TabsView

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:314
**Export:** TabsView

**Issue:** `references/core-api.md:314` documents `TabsView`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Tabs/TabsView.tsx:106` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `TabsView` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Tabs/TabsView.tsx:106`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `TabsView` at references/core-api.md:314.

### GAP-287: Stale documentation: ThemeProvider

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/addons.md:112
**Export:** ThemeProvider

**Issue:** SKILL.md documents `ThemeProvider`, which the enumerated source API surface lacks

**Remediation:** Check `ThemeProvider` against the source and update or remove its documentation at references/addons.md:112: the enumerated source surface does not export it.

### GAP-290: Stale documentation: ToggleButton

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:312
**Export:** ToggleButton

**Issue:** `references/core-api.md:312` documents `ToggleButton`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/ToggleButton/ToggleButton.tsx:16` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `ToggleButton` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/ToggleButton/ToggleButton.tsx:16`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `ToggleButton` at references/core-api.md:312.

### GAP-291: Stale documentation: Toolbar

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:316
**Export:** Toolbar

**Issue:** `references/core-api.md:316` documents `Toolbar`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Toolbar/Toolbar.tsx:36` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Toolbar` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Toolbar/Toolbar.tsx:36`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Toolbar` at references/core-api.md:316.

### GAP-292: Stale documentation: Tooltip

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:315
**Export:** Tooltip

**Issue:** `references/core-api.md:315` documents `Tooltip`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/tooltip/Tooltip.tsx:7` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Tooltip` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/tooltip/Tooltip.tsx:7`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Tooltip` at references/core-api.md:315.

### GAP-293: Stale documentation: TooltipLinkList

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:315
**Export:** TooltipLinkList

**Issue:** `references/core-api.md:315` documents `TooltipLinkList`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/tooltip/TooltipLinkList.tsx:70` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `TooltipLinkList` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/tooltip/TooltipLinkList.tsx:70`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `TooltipLinkList` at references/core-api.md:315.

### GAP-294: Stale documentation: TooltipNote

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:315
**Export:** TooltipNote

**Issue:** `references/core-api.md:315` documents `TooltipNote`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/tooltip/TooltipNote.tsx:23` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `TooltipNote` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/tooltip/TooltipNote.tsx:23`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `TooltipNote` at references/core-api.md:315.

### GAP-297: Stale documentation: UL

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:311
**Export:** UL

**Issue:** `references/core-api.md:311` documents `UL`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/typography/elements/UL.tsx:16` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `UL` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/typography/elements/UL.tsx:16`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `UL` at references/core-api.md:311.

### GAP-299: Stale documentation: ViewMode

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:269
**Export:** ViewMode

**Issue:** SKILL.md documents `ViewMode`, which the enumerated source API surface lacks

**Remediation:** Check `ViewMode` against the source and update or remove its documentation at references/core-api.md:269: the enumerated source surface does not export it.

### GAP-301: Stale documentation: WebsocketTransport

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:329
**Export:** WebsocketTransport

**Issue:** `references/core-api.md:329` documents `WebsocketTransport`, which the entry point `code/core/src/channels/index.ts` exports and `code/core/src/channels/websocket/index.ts:23` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `WebsocketTransport` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/channels/websocket/index.ts:23`, where it is defined, since its `scope.exclude` glob `code/core/src/channels/**` matches that file. To keep its documentation, narrow `code/core/src/channels/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `WebsocketTransport` at references/core-api.md:329.

### GAP-302: Stale documentation: WithTooltip

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:315
**Export:** WithTooltip

**Issue:** `references/core-api.md:315` documents `WithTooltip`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/tooltip/lazy-WithTooltip.tsx:8` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `WithTooltip` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/tooltip/lazy-WithTooltip.tsx:8`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `WithTooltip` at references/core-api.md:315.

### GAP-303: Stale documentation: Zoom

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:317
**Export:** Zoom

**Issue:** `references/core-api.md:317` documents `Zoom`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Zoom/Zoom.tsx:4` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `Zoom` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Zoom/Zoom.tsx:4`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `Zoom` at references/core-api.md:317.

### GAP-304: Stale documentation: addToGlobalContext

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:335
**Export:** addToGlobalContext

**Issue:** `references/core-api.md:335` documents `addToGlobalContext`, which the entry point `code/core/src/telemetry/index.ts` exports and `code/core/src/telemetry/telemetry.ts:26` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `addToGlobalContext` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/telemetry/telemetry.ts:26`, where it is defined, since its `scope.exclude` glob `code/core/src/telemetry/**` matches that file. To keep its documentation, narrow `code/core/src/telemetry/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `addToGlobalContext` at references/core-api.md:335.

### GAP-306: Stale documentation: automock

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:338
**Export:** automock

**Issue:** SKILL.md documents `automock`, which the enumerated source API surface lacks

**Remediation:** Check `automock` against the source and update or remove its documentation at references/core-api.md:338: the enumerated source surface does not export it.

### GAP-310: Stale documentation: colors

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:334
**Export:** colors

**Issue:** `references/core-api.md:334` documents `colors`, which the entry point `code/core/src/node-logger/index.ts` exports and `code/core/src/node-logger/index.ts:57` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `colors` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/node-logger/index.ts:57`, where it is defined, since its `scope.exclude` glob `code/core/src/node-logger/**` matches that file. To keep its documentation, narrow `code/core/src/node-logger/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `colors` at references/core-api.md:334.

### GAP-312: Stale documentation: componentTransform

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:336
**Export:** componentTransform

**Issue:** `references/core-api.md:336` documents `componentTransform`, which the entry point `code/core/src/csf-tools/index.ts` exports and `code/core/src/csf-tools/vitest-plugin/component-transformer.ts:285` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `componentTransform` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/csf-tools/vitest-plugin/component-transformer.ts:285`, where it is defined, since its `scope.exclude` glob `code/core/src/csf-tools/**` matches that file. To keep its documentation, narrow `code/core/src/csf-tools/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `componentTransform` at references/core-api.md:336.

### GAP-313: Stale documentation: core

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:25
**Export:** core

**Issue:** SKILL.md documents `core`, which the enumerated source API surface lacks

**Remediation:** Check `core` against the source and update or remove its documentation at SKILL.md:25: the enumerated source surface does not export it.

### GAP-314: Stale documentation: corePresets

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/framework-config.md:162
**Export:** corePresets

**Issue:** SKILL.md documents `corePresets`, which the enumerated source API surface lacks

**Remediation:** Check `corePresets` against the source and update or remove its documentation at references/framework-config.md:162: the enumerated source surface does not export it.

### GAP-315: Stale documentation: createBrowserChannel

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:329
**Export:** createBrowserChannel

**Issue:** `references/core-api.md:329` documents `createBrowserChannel`, which the entry point `code/core/src/channels/index.ts` exports and `code/core/src/channels/index.ts:32` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `createBrowserChannel` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/channels/index.ts:32`, where it is defined, since its `scope.exclude` glob `code/core/src/channels/**` matches that file. To keep its documentation, narrow `code/core/src/channels/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `createBrowserChannel` at references/core-api.md:329.

### GAP-317: Stale documentation: createTest

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/framework-config.md:146
**Export:** createTest

**Issue:** SKILL.md documents `createTest`, which the enumerated source API surface lacks

**Remediation:** Check `createTest` against the source and update or remove its documentation at references/framework-config.md:146: the enumerated source surface does not export it.

### GAP-319: Stale documentation: decorators

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:35
**Export:** decorators

**Issue:** SKILL.md documents `decorators`, which the enumerated source API surface lacks

**Remediation:** Check `decorators` against the source and update or remove its documentation at SKILL.md:35: the enumerated source surface does not export it.

### GAP-321: Stale documentation: deprecate

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:333
**Export:** deprecate

**Issue:** SKILL.md documents `deprecate`, which the enumerated source API surface lacks

**Remediation:** Check `deprecate` against the source and update or remove its documentation at references/core-api.md:333: the enumerated source surface does not export it.

### GAP-322: Stale documentation: enrichCsf

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:336
**Export:** enrichCsf

**Issue:** `references/core-api.md:336` documents `enrichCsf`, which the entry point `code/core/src/csf-tools/index.ts` exports and `code/core/src/csf-tools/enrichCsf.ts:144` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `enrichCsf` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/csf-tools/enrichCsf.ts:144`, where it is defined, since its `scope.exclude` glob `code/core/src/csf-tools/**` matches that file. To keep its documentation, narrow `code/core/src/csf-tools/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `enrichCsf` at references/core-api.md:336.

### GAP-327: Stale documentation: experimental_loadStorybook

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:339
**Export:** experimental_loadStorybook

**Issue:** `references/core-api.md:339` documents `experimental_loadStorybook`, which the entry point `code/core/src/core-server/index.ts` exports and `code/core/src/core-server/load.ts:18` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `experimental_loadStorybook` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/core-server/load.ts:18`, where it is defined, since its `scope.exclude` glob `code/core/src/core-server/**` matches that file. To keep its documentation, narrow `code/core/src/core-server/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `experimental_loadStorybook` at references/core-api.md:339.

### GAP-328: Stale documentation: extract

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/addons.md:125
**Export:** extract

**Issue:** SKILL.md documents `extract`, which the enumerated source API surface lacks

**Remediation:** Check `extract` against the source and update or remove its documentation at references/addons.md:125: the enumerated source surface does not export it.

### GAP-329: Stale documentation: generate

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:14
**Export:** generate

**Issue:** `SKILL.md:14` documents `generate`, which the entry point `code/core/src/babel/index.ts` exports and `code/core/src/babel/index.ts:38` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `generate` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/babel/index.ts:38`, where it is defined, since its `scope.exclude` glob `code/core/src/babel/**` matches that file. To keep its documentation, narrow `code/core/src/babel/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `generate` at SKILL.md:14.

### GAP-330: Stale documentation: generateStoryFile

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:339
**Export:** generateStoryFile

**Issue:** `references/core-api.md:339` documents `generateStoryFile`, which the entry point `code/core/src/core-server/index.ts` exports and `code/core/src/core-server/utils/generate-story.ts:64` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `generateStoryFile` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/core-server/utils/generate-story.ts:64`, where it is defined, since its `scope.exclude` glob `code/core/src/core-server/**` matches that file. To keep its documentation, narrow `code/core/src/core-server/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `generateStoryFile` at references/core-api.md:339.

### GAP-333: Stale documentation: getSessionId

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:335
**Export:** getSessionId

**Issue:** `references/core-api.md:335` documents `getSessionId`, which the entry point `code/core/src/telemetry/index.ts` exports and `code/core/src/telemetry/session-id.ts:18` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `getSessionId` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/telemetry/session-id.ts:18`, where it is defined, since its `scope.exclude` glob `code/core/src/telemetry/**` matches that file. To keep its documentation, narrow `code/core/src/telemetry/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `getSessionId` at references/core-api.md:335.

### GAP-334: Stale documentation: getStoryHref

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:317
**Export:** getStoryHref

**Issue:** `references/core-api.md:317` documents `getStoryHref`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/utils/getStoryHref.ts:15` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `getStoryHref` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/utils/getStoryHref.ts:15`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `getStoryHref` at references/core-api.md:317.

### GAP-335: Stale documentation: getStorySortParameter

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:336
**Export:** getStorySortParameter

**Issue:** `references/core-api.md:336` documents `getStorySortParameter`, which the entry point `code/core/src/csf-tools/index.ts` exports and `code/core/src/csf-tools/getStorySortParameter.ts:96` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `getStorySortParameter` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/csf-tools/getStorySortParameter.ts:96`, where it is defined, since its `scope.exclude` glob `code/core/src/csf-tools/**` matches that file. To keep its documentation, narrow `code/core/src/csf-tools/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `getStorySortParameter` at references/core-api.md:336.

### GAP-337: Stale documentation: getStorybookMetadata

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:335
**Export:** getStorybookMetadata

**Issue:** `references/core-api.md:335` documents `getStorybookMetadata`, which the entry point `code/core/src/telemetry/index.ts` exports and `code/core/src/telemetry/storybook-metadata.ts:312` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `getStorybookMetadata` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/telemetry/storybook-metadata.ts:312`, where it is defined, since its `scope.exclude` glob `code/core/src/telemetry/**` matches that file. To keep its documentation, narrow `code/core/src/telemetry/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `getStorybookMetadata` at references/core-api.md:335.

### GAP-342: Stale documentation: jsx

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:169
**Export:** jsx

**Issue:** SKILL.md documents `jsx`, which the enumerated source API surface lacks

**Remediation:** Check `jsx` against the source and update or remove its documentation at references/core-api.md:169: the enumerated source surface does not export it.

### GAP-345: Stale documentation: logTracker

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:334
**Export:** logTracker

**Issue:** `references/core-api.md:334` documents `logTracker`, which the entry point `code/core/src/node-logger/index.ts` exports and `code/core/src/node-logger/logger/log-tracker.ts:95` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `logTracker` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/node-logger/logger/log-tracker.ts:95`, where it is defined, since its `scope.exclude` glob `code/core/src/node-logger/**` matches that file. To keep its documentation, narrow `code/core/src/node-logger/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `logTracker` at references/core-api.md:334.

### GAP-346: Stale documentation: logger

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:35
**Export:** logger

**Issue:** SKILL.md documents `logger`, which the enumerated source API surface lacks

**Remediation:** Check `logger` against the source and update or remove its documentation at references/core-api.md:35: the enumerated source surface does not export it.

### GAP-348: Stale documentation: once

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:117
**Export:** once

**Issue:** SKILL.md documents `once`, which the enumerated source API surface lacks

**Remediation:** Check `once` against the source and update or remove its documentation at SKILL.md:117: the enumerated source surface does not export it.

### GAP-351: Stale documentation: parser

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:341
**Export:** parser

**Issue:** SKILL.md documents `parser`, which the enumerated source API surface lacks

**Remediation:** Check `parser` against the source and update or remove its documentation at references/core-api.md:341: the enumerated source surface does not export it.

### GAP-353: Stale documentation: prompt

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:334
**Export:** prompt

**Issue:** `references/core-api.md:334` documents `prompt`, which the entry point `code/core/src/node-logger/index.ts` exports and `code/core/src/node-logger/prompts/index.ts:5` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `prompt` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/node-logger/prompts/index.ts:5`, where it is defined, since its `scope.exclude` glob `code/core/src/node-logger/**` matches that file. To keep its documentation, narrow `code/core/src/node-logger/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `prompt` at references/core-api.md:334.

### GAP-354: Stale documentation: recast

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:341
**Export:** recast

**Issue:** SKILL.md documents `recast`, which the enumerated source API surface lacks

**Remediation:** Check `recast` against the source and update or remove its documentation at references/core-api.md:341: the enumerated source surface does not export it.

### GAP-355: Stale documentation: redirect

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:338
**Export:** redirect

**Issue:** SKILL.md documents `redirect`, which the enumerated source API surface lacks

**Remediation:** Check `redirect` against the source and update or remove its documentation at references/core-api.md:338: the enumerated source surface does not export it.

### GAP-356: Stale documentation: resolve

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:338
**Export:** resolve

**Issue:** SKILL.md documents `resolve`, which the enumerated source API surface lacks

**Remediation:** Check `resolve` against the source and update or remove its documentation at references/core-api.md:338: the enumerated source surface does not export it.

### GAP-357: Stale documentation: runtime

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:14
**Export:** runtime

**Issue:** SKILL.md documents `runtime`, which the enumerated source API surface lacks

**Remediation:** Check `runtime` against the source and update or remove its documentation at references/core-api.md:14: the enumerated source surface does not export it.

### GAP-363: Stale documentation: telemetry

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:335
**Export:** telemetry

**Issue:** `references/core-api.md:335` documents `telemetry`, which the entry point `code/core/src/telemetry/index.ts` exports and `code/core/src/telemetry/index.ts:31` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `telemetry` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/telemetry/index.ts:31`, where it is defined, since its `scope.exclude` glob `code/core/src/telemetry/**` matches that file. To keep its documentation, narrow `code/core/src/telemetry/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `telemetry` at references/core-api.md:335.

### GAP-366: Stale documentation: transformSync

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:341
**Export:** transformSync

**Issue:** SKILL.md documents `transformSync`, which the enumerated source API surface lacks

**Remediation:** Check `transformSync` against the source and update or remove its documentation at references/core-api.md:341: the enumerated source surface does not export it.

### GAP-367: Stale documentation: traverse

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:341
**Export:** traverse

**Issue:** `references/core-api.md:341` documents `traverse`, which the entry point `code/core/src/babel/index.ts` exports and `code/core/src/babel/index.ts:39` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `traverse` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/babel/index.ts:39`, where it is defined, since its `scope.exclude` glob `code/core/src/babel/**` matches that file. To keep its documentation, narrow `code/core/src/babel/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `traverse` at references/core-api.md:341.

### GAP-369: Stale documentation: useStatusStore

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:152
**Export:** useStatusStore

**Issue:** SKILL.md documents `useStatusStore`, which the enumerated source API surface lacks

**Remediation:** Check `useStatusStore` against the source and update or remove its documentation at references/core-api.md:152: the enumerated source surface does not export it.

### GAP-370: Stale documentation: useTabsState

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:314
**Export:** useTabsState

**Issue:** `references/core-api.md:314` documents `useTabsState`, which the entry point `code/core/src/components/index.ts` exports and `code/core/src/components/components/Tabs/TabsView.tsx:30` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `useTabsState` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/components/components/Tabs/TabsView.tsx:30`, where it is defined, since its `scope.exclude` glob `code/core/src/components/**` matches that file. To keep its documentation, narrow `code/core/src/components/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `useTabsState` at references/core-api.md:314.

### GAP-371: Stale documentation: useTestProviderStore

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:153
**Export:** useTestProviderStore

**Issue:** SKILL.md documents `useTestProviderStore`, which the enumerated source API surface lacks

**Remediation:** Check `useTestProviderStore` against the source and update or remove its documentation at references/core-api.md:153: the enumerated source surface does not export it.

### GAP-372: Stale documentation: useTheme

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:20
**Export:** useTheme

**Issue:** SKILL.md documents `useTheme`, which the enumerated source API surface lacks

**Remediation:** Check `useTheme` against the source and update or remove its documentation at references/core-api.md:20: the enumerated source surface does not export it.

### GAP-373: Stale documentation: useUniversalStore

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:150
**Export:** useUniversalStore

**Issue:** SKILL.md documents `useUniversalStore`, which the enumerated source API surface lacks

**Remediation:** Check `useUniversalStore` against the source and update or remove its documentation at references/core-api.md:150: the enumerated source surface does not export it.

### GAP-374: Stale documentation: viteFinal

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/framework-config.md:27
**Export:** viteFinal

**Issue:** SKILL.md documents `viteFinal`, which the enumerated source API surface lacks

**Remediation:** Check `viteFinal` against the source and update or remove its documentation at references/framework-config.md:27: the enumerated source surface does not export it.

### GAP-375: Stale documentation: vitestTransform

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:336
**Export:** vitestTransform

**Issue:** `references/core-api.md:336` documents `vitestTransform`, which the entry point `code/core/src/csf-tools/index.ts` exports and `code/core/src/csf-tools/vitest-plugin/transformer.ts:108` defines, a file `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `vitestTransform` belongs on the surface: `forge-data/oms-storybook-react-vite/skill-brief.yaml` scopes out `code/core/src/csf-tools/vitest-plugin/transformer.ts:108`, where it is defined, since its `scope.exclude` glob `code/core/src/csf-tools/**` matches that file. To keep its documentation, narrow `code/core/src/csf-tools/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `vitestTransform` at references/core-api.md:336.

### GAP-376: Stale documentation: withTheme

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-api.md:168
**Export:** withTheme

**Issue:** SKILL.md documents `withTheme`, which the enumerated source API surface lacks

**Remediation:** Check `withTheme` against the source and update or remove its documentation at references/core-api.md:168: the enumerated source surface does not export it.

### GAP-377: denominator drift: effective_denominator disagrees with the brief's tier_a_include set

**Severity:** Medium
**Category:** Coverage (metadata-drift)
**Source:** skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/metadata.json

**Issue:** the brief's `scope.tier_a_include` set counts 370 exports, 32.14% above `stats.effective_denominator` (280)

**Remediation:** Re-run Create Skill to recount `stats.effective_denominator` in `skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/metadata.json`: it stores the runner's count of the brief's `scope.tier_a_include` set when `effective_denominator_decision.store` holds and the brief's `scope.notes` documents the stratification, and otherwise drops the stored count. Until then Test Skill counts the `tier_a_include` set as the denominator.

### GAP-378: metadata drift — barrel export counts diverge

**Severity:** Medium
**Category:** Coverage (metadata-drift)
**Source:** skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/metadata.json

**Issue:** stats.exports_public_api=1335, exports[].length=88 → 93% drift

**Remediation:** Re-run Create Skill, which rebuilds `exports[]` and `stats.exports_public_api` in `skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/metadata.json` from the source. Update Skill does not repair this drift: each time it writes the skill it recounts `stats.exports_public_api` from the source and keeps `exports[]`, adding or dropping only the names its provenance map changes, so a metadata patch does not hold.

### GAP-003: Signature mismatch: withThemeByClassName (form 1 of 4)

**Severity:** Low
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/themes/src/decorators/class-name.decorator.tsx:19
**Export:** withThemeByClassName

**Issue:** documented `(config: ClassNameStrategyConfiguration) => DecoratorFunction<R>`, source `<TRenderer extends Renderer = Renderer>({ themes, defaultTheme, parentSelector = DEFAULT_ELEMENT_SELECTOR }: ClassNameStrategyConfiguration): DecoratorFunction<TRenderer>`: the documented parameter is named config; the source declares a destructured parameter (no name) of the same type; types, order, optionality and return type are equal (only the parameter names differ, and a caller of a `.tsx` file passes its arguments by position) (documented form 1 of 4: `(config: ClassNameStrategyConfiguration) -> DecoratorFunction<R>`)

**Remediation:** Update the documented signature of `withThemeByClassName` from `(config: ClassNameStrategyConfiguration) => DecoratorFunction<R>` to `<TRenderer extends Renderer = Renderer>({ themes, defaultTheme, parentSelector = DEFAULT_ELEMENT_SELECTOR }: ClassNameStrategyConfiguration): DecoratorFunction<TRenderer>`, the signature the source defines at `code/addons/themes/src/decorators/class-name.decorator.tsx:19`.

### GAP-004: Signature mismatch: withThemeByDataAttribute (form 1 of 3)

**Severity:** Low
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/themes/src/decorators/data-attribute.decorator.tsx:19
**Export:** withThemeByDataAttribute

**Issue:** documented `(config: DataAttributeStrategyConfiguration) => DecoratorFunction<R>`, source `<TRenderer extends Renderer = any>({ themes, defaultTheme, parentSelector = DEFAULT_ELEMENT_SELECTOR, attributeName = DEFAULT_DATA_ATTRIBUTE }: DataAttributeStrategyConfiguration): DecoratorFunction<TRenderer>`: the documented parameter is named config; the source declares a destructured parameter (no name) of the same type; types, order, optionality and return type are equal (only the parameter names differ, and a caller of a `.tsx` file passes its arguments by position) (documented form 1 of 3: `(config: DataAttributeStrategyConfiguration) -> DecoratorFunction<R>`)

**Remediation:** Update the documented signature of `withThemeByDataAttribute` from `(config: DataAttributeStrategyConfiguration) => DecoratorFunction<R>` to `<TRenderer extends Renderer = any>({ themes, defaultTheme, parentSelector = DEFAULT_ELEMENT_SELECTOR, attributeName = DEFAULT_DATA_ATTRIBUTE }: DataAttributeStrategyConfiguration): DecoratorFunction<TRenderer>`, the signature the source defines at `code/addons/themes/src/decorators/data-attribute.decorator.tsx:19`.

### GAP-005: Signature mismatch: withThemeFromJSXProvider (form 1 of 2)

**Severity:** Low
**Category:** Coverage (signature-mismatch)
**Source:** code/addons/themes/src/decorators/provider.decorator.tsx:23
**Export:** withThemeFromJSXProvider

**Issue:** documented `(config: ProviderStrategyConfiguration) => DecoratorFunction<R>`, source `<TRenderer extends Renderer = any>({ Provider, GlobalStyles, defaultTheme, themes = {} }: ProviderStrategyConfiguration): DecoratorFunction<TRenderer>`: the documented parameter is named config; the source declares a destructured parameter (no name) of the same type; types, order, optionality and return type are equal (only the parameter names differ, and a caller of a `.tsx` file passes its arguments by position) (documented form 1 of 2: `(config: ProviderStrategyConfiguration) -> DecoratorFunction<R>`)

**Remediation:** Update the documented signature of `withThemeFromJSXProvider` from `(config: ProviderStrategyConfiguration) => DecoratorFunction<R>` to `<TRenderer extends Renderer = any>({ Provider, GlobalStyles, defaultTheme, themes = {} }: ProviderStrategyConfiguration): DecoratorFunction<TRenderer>`, the signature the source defines at `code/addons/themes/src/decorators/provider.decorator.tsx:23`.

### GAP-006: Signature mismatch: DecoratorFunction

**Severity:** Low
**Category:** Coverage (signature-mismatch)
**Source:** code/core/src/csf/story.ts:331
**Export:** DecoratorFunction

**Issue:** documented `(storyFn: PartialStoryFn<R, Args>, context: StoryContext<R, Args>) => R['storyResult']`, source `type DecoratorFunction<TRenderer extends Renderer = Renderer, TArgs = Args> = (fn: PartialStoryFn<TRenderer, TArgs>, c: StoryContext<TRenderer, TArgs>) => TRenderer['storyResult']`: parameter names differ (storyFn vs fn, context vs c); types (type variables renamed consistently), order and return type are equal (only the parameter names differ, and a caller of a `.ts` file passes its arguments by position)

**Remediation:** Update the documented signature of `DecoratorFunction` from `(storyFn: PartialStoryFn<R, Args>, context: StoryContext<R, Args>) => R['storyResult']` to `type DecoratorFunction<TRenderer extends Renderer = Renderer, TArgs = Args> = (fn: PartialStoryFn<TRenderer, TArgs>, c: StoryContext<TRenderer, TArgs>) => TRenderer['storyResult']`, the signature the source defines at `code/core/src/csf/story.ts:331`.

### GAP-007: Signature mismatch: useParameter

**Severity:** Low
**Category:** Coverage (signature-mismatch)
**Source:** code/core/src/preview-api/modules/addons/hooks.ts:590
**Export:** useParameter

**Issue:** documented `useParameter(key, default)`, source `useParameter<S>(parameterKey: string, defaultValue?: S): S | undefined`: read as a list of bare names (default cannot be a passed variable): names differ (key vs parameterKey, default vs defaultValue); order equal, the list states no optionality and no types (only the parameter names differ, and a caller of a `.ts` file passes its arguments by position)

**Remediation:** Update the documented signature of `useParameter` from `useParameter(key, default)` to `useParameter<S>(parameterKey: string, defaultValue?: S): S | undefined`, the signature the source defines at `code/core/src/preview-api/modules/addons/hooks.ts:590`.

### GAP-008: Signature mismatch: normalizeProjectAnnotations

**Severity:** Low
**Category:** Coverage (signature-mismatch)
**Source:** code/core/src/preview-api/modules/store/csf/normalizeProjectAnnotations.ts:17
**Export:** normalizeProjectAnnotations

**Issue:** documented `<R>(annotations: ProjectAnnotations<R>) => NormalizedProjectAnnotations<R>`, source `<TRenderer extends Renderer>({ argTypes, argTypesEnhancers, decorators, loaders, beforeEach, afterEach, initialGlobals, ...annotations }: ProjectAnnotations<TRenderer>): NormalizedProjectAnnotations<TRenderer>`: the documented parameter is named annotations; the source declares a destructured parameter (no name) of the same type; types, order, optionality and return type are equal (only the parameter names differ, and a caller of a `.ts` file passes its arguments by position)

**Remediation:** Update the documented signature of `normalizeProjectAnnotations` from `<R>(annotations: ProjectAnnotations<R>) => NormalizedProjectAnnotations<R>` to `<TRenderer extends Renderer>({ argTypes, argTypesEnhancers, decorators, loaders, beforeEach, afterEach, initialGlobals, ...annotations }: ProjectAnnotations<TRenderer>): NormalizedProjectAnnotations<TRenderer>`, the signature the source defines at `code/core/src/preview-api/modules/store/csf/normalizeProjectAnnotations.ts:17`.

### GAP-009: Signature mismatch: sanitizeStoryContextUpdate

**Severity:** Low
**Category:** Coverage (signature-mismatch)
**Source:** code/core/src/preview-api/modules/store/decorators.ts:30
**Export:** sanitizeStoryContextUpdate

**Issue:** documented `(inputContextUpdate?: StoryContextUpdate) => StoryContextUpdate`, source `({ componentId, title, kind, id, name, story, parameters, initialArgs, argTypes, ...update }: StoryContextUpdate = {}): StoryContextUpdate`: the documented parameter is named inputContextUpdate; the source declares a destructured parameter (no name) of the same type, optional by its default; types, order, optionality and return type are equal (only the parameter names differ, and a caller of a `.ts` file passes its arguments by position)

**Remediation:** Update the documented signature of `sanitizeStoryContextUpdate` from `(inputContextUpdate?: StoryContextUpdate) => StoryContextUpdate` to `({ componentId, title, kind, id, name, story, parameters, initialArgs, argTypes, ...update }: StoryContextUpdate = {}): StoryContextUpdate`, the signature the source defines at `code/core/src/preview-api/modules/store/decorators.ts:30`.

### GAP-002: Partial signature: Story

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/docs/src/blocks/blocks/Story.tsx:134
**Export:** Story

**Issue:** the skill labels its documented form of `Story` partial, and it leaves out only members the source marks optional: documented `{ of?, meta?, inline?, height?, autoplay? }`, source `StoryProps = StoryRefProps & StoryParameters: { of?: ModuleExport; meta?: ModuleExports; inline?: boolean; height?: string; autoplay?: boolean; __forceInitialArgs?: boolean; __primary?: boolean } (Story.tsx:21-60)`: the props list leaves out the optional own props __forceInitialArgs? and __primary?

**Remediation:** No change: the documented form of `Story` is labelled partial and leaves out only optional members of the signature the source defines at `code/addons/docs/src/blocks/blocks/Story.tsx:134`.

### GAP-145: Documented extra: API_EventMap

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager-api/root.tsx:318
**Export:** API_EventMap

**Issue:** `references/story-types.md:248` documents `API_EventMap`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `API_EventMap` is a documented extra, a name the source still declares at `code/core/src/manager-api/root.tsx:318` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-146: Documented extra: API_KeyCollection

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager-api/modules/shortcuts.ts:99
**Export:** API_KeyCollection

**Issue:** `references/story-types.md:249` documents `API_KeyCollection`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `API_KeyCollection` is a documented extra, a name the source still declares at `code/core/src/manager-api/modules/shortcuts.ts:99` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-152: Documented extra: BabelFile

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/csf-tools/CsfFile.ts:31
**Export:** BabelFile

**Issue:** `references/core-api.md:341` documents `BabelFile`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `BabelFile` is a documented extra, a name the source still declares at `code/core/src/csf-tools/CsfFile.ts:31` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-155: Documented extra: BaseProjectAnnotations

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/types/modules/csf.ts:38
**Export:** BaseProjectAnnotations

**Issue:** `references/core-api.md:261` documents `BaseProjectAnnotations`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `BaseProjectAnnotations` is a documented extra, a name the source still declares at `code/core/src/types/modules/csf.ts:38` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-158: Documented extra: CHANNEL_CREATED

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/core-events/index.ts:112
**Export:** CHANNEL_CREATED

**Issue:** `references/core-api.md:330` documents `CHANNEL_CREATED`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CHANNEL_CREATED` is a documented extra, a name the source still declares at `code/core/src/core-events/index.ts:112` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-159: Documented extra: COMPONENT_TESTING_PANEL_ID

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/vitest/src/constants.ts:5
**Export:** COMPONENT_TESTING_PANEL_ID

**Issue:** `references/addons.md:196` documents `COMPONENT_TESTING_PANEL_ID`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `COMPONENT_TESTING_PANEL_ID` is a documented extra, a name the source still declares at `code/addons/vitest/src/constants.ts:5` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-160: Documented extra: CSFFile

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/types/modules/story.ts:92
**Export:** CSFFile

**Issue:** `references/core-api.md:273` documents `CSFFile`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CSFFile` is a documented extra, a name the source still declares at `code/core/src/types/modules/story.ts:92` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-163: Documented extra: CalledExtractOnStoreError

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/preview-errors.ts:77
**Export:** CalledExtractOnStoreError

**Issue:** `references/core-api.md:298` documents `CalledExtractOnStoreError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CalledExtractOnStoreError` is a documented extra, a name the source still declares at `code/core/src/preview-errors.ts:77` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-164: Documented extra: CalledPreviewMethodBeforeInitializationError

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/preview-errors.ts:107
**Export:** CalledPreviewMethodBeforeInitializationError

**Issue:** `references/core-api.md:298` documents `CalledPreviewMethodBeforeInitializationError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CalledPreviewMethodBeforeInitializationError` is a documented extra, a name the source still declares at `code/core/src/preview-errors.ts:107` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-167: Documented extra: Category

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/preview-errors.ts:15
**Export:** Category

**Issue:** `references/core-api.md:300` documents `Category`, which the enumerated source API surface lacks and the source still declares; of the 3 files that declare it, the skill cites only `code/core/src/preview-errors.ts`

**Remediation:** No change: `Category` is a documented extra, a name the source still declares at `code/core/src/preview-errors.ts:15` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-174: Documented extra: Combo

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager-api/root.tsx:116
**Export:** Combo

**Issue:** `references/story-types.md:242` documents `Combo`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Combo` is a documented extra, a name the source still declares at `code/core/src/manager-api/root.tsx:116` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-175: Documented extra: ComponentAnnotations

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/csf/story.ts:452
**Export:** ComponentAnnotations

**Issue:** `SKILL.md:208` documents `ComponentAnnotations`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ComponentAnnotations` is a documented extra, a name the source still declares at `code/core/src/csf/story.ts:452` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-176: Documented extra: ComponentEntry

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager-api/root.tsx:308
**Export:** ComponentEntry

**Issue:** `references/story-types.md:259` documents `ComponentEntry`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ComponentEntry` is a documented extra, a name the source still declares at `code/core/src/manager-api/root.tsx:308` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-180: Documented extra: DecoratorHelpers

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/themes/src/decorators/index.ts:5
**Export:** DecoratorHelpers

**Issue:** `references/addons.md:121` documents `DecoratorHelpers`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `DecoratorHelpers` is a documented extra, a name the source still declares at `code/addons/themes/src/decorators/index.ts:5` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-182: Documented extra: DocsEntry

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager-api/root.tsx:309
**Export:** DocsEntry

**Issue:** `references/story-types.md:259` documents `DocsEntry`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `DocsEntry` is a documented extra, a name the source still declares at `code/core/src/manager-api/root.tsx:309` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-183: Documented extra: EmptyIndexError

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/preview-errors.ts:161
**Export:** EmptyIndexError

**Issue:** `references/core-api.md:298` documents `EmptyIndexError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `EmptyIndexError` is a documented extra, a name the source still declares at `code/core/src/preview-errors.ts:161` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-185: Documented extra: FULL_RUN_TRIGGERS

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/vitest/src/constants.ts:61
**Export:** FULL_RUN_TRIGGERS

**Issue:** `references/addons.md:199` documents `FULL_RUN_TRIGGERS`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `FULL_RUN_TRIGGERS` is a documented extra, a name the source still declares at `code/addons/vitest/src/constants.ts:61` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-188: Documented extra: GLOBALS_UPDATED

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/core-events/index.ts:123
**Export:** GLOBALS_UPDATED

**Issue:** `references/core-api.md:330` documents `GLOBALS_UPDATED`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `GLOBALS_UPDATED` is a documented extra, a name the source still declares at `code/core/src/core-events/index.ts:123` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-190: Documented extra: Globals

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/csf/story.ts:165
**Export:** Globals

**Issue:** `references/core-api.md:263` documents `Globals`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Globals` is a documented extra, a name the source still declares at `code/core/src/csf/story.ts:165` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-191: Documented extra: GroupEntry

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager-api/root.tsx:307
**Export:** GroupEntry

**Issue:** `references/story-types.md:259` documents `GroupEntry`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `GroupEntry` is a documented extra, a name the source still declares at `code/core/src/manager-api/root.tsx:307` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-195: Documented extra: HashEntry

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager-api/root.tsx:311
**Export:** HashEntry

**Issue:** `references/story-types.md:254` documents `HashEntry`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `HashEntry` is a documented extra, a name the source still declares at `code/core/src/manager-api/root.tsx:311` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-197: Documented extra: ImplicitActionsDuringRendering

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/preview-errors.ts:56
**Export:** ImplicitActionsDuringRendering

**Issue:** `references/core-api.md:298` documents `ImplicitActionsDuringRendering`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ImplicitActionsDuringRendering` is a documented extra, a name the source still declares at `code/core/src/preview-errors.ts:56` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-198: Documented extra: IncludeExcludeOptions

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/csf/index.ts:38
**Export:** IncludeExcludeOptions

**Issue:** `references/core-api.md:291` documents `IncludeExcludeOptions`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `IncludeExcludeOptions` is a documented extra, a name the source still declares at `code/core/src/csf/index.ts:38` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-199: Documented extra: IndexHash

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager-api/root.tsx:305
**Export:** IndexHash

**Issue:** `references/story-types.md:250` documents `IndexHash`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `IndexHash` is a documented extra, a name the source still declares at `code/core/src/manager-api/root.tsx:305` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-200: Documented extra: InvalidFrameworkNameError

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/server-errors.ts:86
**Export:** InvalidFrameworkNameError

**Issue:** `references/core-api.md:304` documents `InvalidFrameworkNameError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `InvalidFrameworkNameError` is a documented extra, a name the source still declares at `code/core/src/server-errors.ts:86` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-203: Documented extra: LeafEntry

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager-api/root.tsx:312
**Export:** LeafEntry

**Issue:** `references/story-types.md:260` documents `LeafEntry`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LeafEntry` is a documented extra, a name the source still declares at `code/core/src/manager-api/root.tsx:312` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-204: Documented extra: LoaderFunction

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/csf/story.ts:249
**Export:** LoaderFunction

**Issue:** `references/core-api.md:256` documents `LoaderFunction`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LoaderFunction` is a documented extra, a name the source still declares at `code/core/src/csf/story.ts:249` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-205: Documented extra: ManagerContext

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager-api/root.tsx:80
**Export:** ManagerContext

**Issue:** `references/story-types.md:245` documents `ManagerContext`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ManagerContext` is a documented extra, a name the source still declares at `code/core/src/manager-api/root.tsx:80` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-206: Documented extra: ManagerProviderProps

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager-api/root.tsx:121
**Export:** ManagerProviderProps

**Issue:** `references/story-types.md:246` documents `ManagerProviderProps`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ManagerProviderProps` is a documented extra, a name the source still declares at `code/core/src/manager-api/root.tsx:121` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-209: Documented extra: MdxFileWithNoCsfReferencesError

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/preview-errors.ts:145
**Export:** MdxFileWithNoCsfReferencesError

**Issue:** `references/core-api.md:298` documents `MdxFileWithNoCsfReferencesError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MdxFileWithNoCsfReferencesError` is a documented extra, a name the source still declares at `code/core/src/preview-errors.ts:145` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-211: Documented extra: MissingFrameworkFieldError

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/server-errors.ts:70
**Export:** MissingFrameworkFieldError

**Issue:** `references/core-api.md:304` documents `MissingFrameworkFieldError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MissingFrameworkFieldError` is a documented extra, a name the source still declares at `code/core/src/server-errors.ts:70` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-212: Documented extra: MissingRenderToCanvasError

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/preview-errors.ts:91
**Export:** MissingRenderToCanvasError

**Issue:** `references/core-api.md:298` documents `MissingRenderToCanvasError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MissingRenderToCanvasError` is a documented extra, a name the source still declares at `code/core/src/preview-errors.ts:91` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-213: Documented extra: MissingStoryAfterHmrError

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/preview-errors.ts:39
**Export:** MissingStoryAfterHmrError

**Issue:** `references/core-api.md:298` documents `MissingStoryAfterHmrError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MissingStoryAfterHmrError` is a documented extra, a name the source still declares at `code/core/src/preview-errors.ts:39` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-214: Documented extra: MissingStoryFromCsfFileError

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/preview-errors.ts:192
**Export:** MissingStoryFromCsfFileError

**Issue:** `references/core-api.md:298` documents `MissingStoryFromCsfFileError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MissingStoryFromCsfFileError` is a documented extra, a name the source still declares at `code/core/src/preview-errors.ts:192` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-217: Documented extra: MockUniversalStore

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/shared/universal-store/mock.ts:40
**Export:** MockUniversalStore

**Issue:** `references/core-api.md:151` documents `MockUniversalStore`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MockUniversalStore` is a documented extra, a name the source still declares at `code/core/src/shared/universal-store/mock.ts:40` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-219: Documented extra: MountMustBeDestructuredError

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/preview-errors.ts:226
**Export:** MountMustBeDestructuredError

**Issue:** `references/core-api.md:298` documents `MountMustBeDestructuredError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MountMustBeDestructuredError` is a documented extra, a name the source still declares at `code/core/src/preview-errors.ts:226` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-220: Documented extra: NoRenderFunctionError

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/preview-errors.ts:256
**Export:** NoRenderFunctionError

**Issue:** `references/core-api.md:298` documents `NoRenderFunctionError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `NoRenderFunctionError` is a documented extra, a name the source still declares at `code/core/src/preview-errors.ts:256` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-221: Documented extra: NoStoryMatchError

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/preview-errors.ts:176
**Export:** NoStoryMatchError

**Issue:** `references/core-api.md:298` documents `NoStoryMatchError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `NoStoryMatchError` is a documented extra, a name the source still declares at `code/core/src/preview-errors.ts:176` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-222: Documented extra: NoStoryMountedError

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/preview-errors.ts:269
**Export:** NoStoryMountedError

**Issue:** `references/core-api.md:298` documents `NoStoryMountedError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `NoStoryMountedError` is a documented extra, a name the source still declares at `code/core/src/preview-errors.ts:269` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-224: Documented extra: NormalizedComponentAnnotations

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/types/modules/story.ts:66
**Export:** NormalizedComponentAnnotations

**Issue:** `references/core-api.md:116` documents `NormalizedComponentAnnotations`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `NormalizedComponentAnnotations` is a documented extra, a name the source still declares at `code/core/src/types/modules/story.ts:66` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-225: Documented extra: NormalizedProjectAnnotations

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/types/modules/story.ts:55
**Export:** NormalizedProjectAnnotations

**Issue:** `references/core-api.md:112` documents `NormalizedProjectAnnotations`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `NormalizedProjectAnnotations` is a documented extra, a name the source still declares at `code/core/src/types/modules/story.ts:55` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-226: Documented extra: NormalizedStoryAnnotations

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/types/modules/story.ts:78
**Export:** NormalizedStoryAnnotations

**Issue:** `references/core-api.md:116` documents `NormalizedStoryAnnotations`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `NormalizedStoryAnnotations` is a documented extra, a name the source still declares at `code/core/src/types/modules/story.ts:78` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-228: Documented extra: NxProjectDetectedError

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/server-errors.ts:56
**Export:** NxProjectDetectedError

**Issue:** `references/core-api.md:304` documents `NxProjectDetectedError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `NxProjectDetectedError` is a documented extra, a name the source still declares at `code/core/src/server-errors.ts:56` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-231: Documented extra: PREVIEW_INITIALIZED

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/core-events/index.ts:128
**Export:** PREVIEW_INITIALIZED

**Issue:** `references/core-api.md:330` documents `PREVIEW_INITIALIZED`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PREVIEW_INITIALIZED` is a documented extra, a name the source still declares at `code/core/src/core-events/index.ts:128` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-239: Documented extra: PreparedStory

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/types/modules/story.ts:99
**Export:** PreparedStory

**Issue:** `references/core-api.md:119` documents `PreparedStory`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PreparedStory` is a documented extra, a name the source still declares at `code/core/src/types/modules/story.ts:99` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-243: Documented extra: Refs

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager-api/root.tsx:314
**Export:** Refs

**Issue:** `references/story-types.md:247` documents `Refs`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Refs` is a documented extra, a name the source still declares at `code/core/src/manager-api/root.tsx:314` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-244: Documented extra: RenderContext

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/types/modules/story.ts:129
**Export:** RenderContext

**Issue:** `references/core-api.md:276` documents `RenderContext`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `RenderContext` is a documented extra, a name the source still declares at `code/core/src/types/modules/story.ts:129` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-245: Documented extra: RenderToCanvas

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/types/modules/story.ts:38
**Export:** RenderToCanvas

**Issue:** `references/core-api.md:272` documents `RenderToCanvas`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `RenderToCanvas` is a documented extra, a name the source still declares at `code/core/src/types/modules/story.ts:38` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-246: Documented extra: RootEntry

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager-api/root.tsx:306
**Export:** RootEntry

**Issue:** `references/story-types.md:259` documents `RootEntry`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `RootEntry` is a documented extra, a name the source still declares at `code/core/src/manager-api/root.tsx:306` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-247: Documented extra: SELECT_STORY

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/core-events/index.ts:133
**Export:** SELECT_STORY

**Issue:** `references/core-api.md:330` documents `SELECT_STORY`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `SELECT_STORY` is a documented extra, a name the source still declares at `code/core/src/core-events/index.ts:133` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-248: Documented extra: STORYBOOK_ADDON_TEST_CHANNEL

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/vitest/src/constants.ts:13
**Export:** STORYBOOK_ADDON_TEST_CHANNEL

**Issue:** `references/addons.md:195` documents `STORYBOOK_ADDON_TEST_CHANNEL`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `STORYBOOK_ADDON_TEST_CHANNEL` is a documented extra, a name the source still declares at `code/addons/vitest/src/constants.ts:13` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-249: Documented extra: STORY_PREPARED

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/core-events/index.ts:149
**Export:** STORY_PREPARED

**Issue:** `references/core-api.md:330` documents `STORY_PREPARED`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `STORY_PREPARED` is a documented extra, a name the source still declares at `code/core/src/core-events/index.ts:149` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-250: Documented extra: STORY_RENDERED

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/core-events/index.ts:151
**Export:** STORY_RENDERED

**Issue:** `references/core-api.md:330` documents `STORY_RENDERED`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `STORY_RENDERED` is a documented extra, a name the source still declares at `code/core/src/core-events/index.ts:151` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-251: Documented extra: STORY_SPECIFIED

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/core-events/index.ts:153
**Export:** STORY_SPECIFIED

**Issue:** `references/core-api.md:330` documents `STORY_SPECIFIED`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `STORY_SPECIFIED` is a documented extra, a name the source still declares at `code/core/src/core-events/index.ts:153` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-255: Documented extra: SeparatorOptions

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/csf/index.ts:63
**Export:** SeparatorOptions

**Issue:** `references/core-api.md:292` documents `SeparatorOptions`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `SeparatorOptions` is a documented extra, a name the source still declares at `code/core/src/csf/index.ts:63` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-258: Documented extra: State

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager-api/root.tsx:82
**Export:** State

**Issue:** `references/core-api.md:79` documents `State`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `State` is a documented extra, a name the source still declares at `code/core/src/manager-api/root.tsx:82` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-259: Documented extra: StatusTypeIdMismatchError

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/preview-errors.ts:295
**Export:** StatusTypeIdMismatchError

**Issue:** `references/core-api.md:298` documents `StatusTypeIdMismatchError`, which the enumerated source API surface lacks and the source still declares; of the 3 files that declare it, the skill cites only `code/core/src/preview-errors.ts`

**Remediation:** No change: `StatusTypeIdMismatchError` is a documented extra, a name the source still declares at `code/core/src/preview-errors.ts:295` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-260: Documented extra: StoreOptions

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager-api/root.tsx:77
**Export:** StoreOptions

**Issue:** `references/story-types.md:244` documents `StoreOptions`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `StoreOptions` is a documented extra, a name the source still declares at `code/core/src/manager-api/root.tsx:77` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-261: Documented extra: StoriesHash

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager-api/root.tsx:304
**Export:** StoriesHash

**Issue:** `references/story-types.md:250` documents `StoriesHash`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `StoriesHash` is a documented extra, a name the source still declares at `code/core/src/manager-api/root.tsx:304` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-262: Documented extra: StoryAnnotations

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/csf/story.ts:543
**Export:** StoryAnnotations

**Issue:** `SKILL.md:208` documents `StoryAnnotations`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `StoryAnnotations` is a documented extra, a name the source still declares at `code/core/src/csf/story.ts:543` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-263: Documented extra: StoryEntry

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager-api/root.tsx:310
**Export:** StoryEntry

**Issue:** `references/story-types.md:259` documents `StoryEntry`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `StoryEntry` is a documented extra, a name the source still declares at `code/core/src/manager-api/root.tsx:310` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-264: Documented extra: StoryIndexFetchError

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/preview-errors.ts:125
**Export:** StoryIndexFetchError

**Issue:** `references/core-api.md:298` documents `StoryIndexFetchError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `StoryIndexFetchError` is a documented extra, a name the source still declares at `code/core/src/preview-errors.ts:125` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-266: Documented extra: StoryStoreAccessedBeforeInitializationError

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/preview-errors.ts:211
**Export:** StoryStoreAccessedBeforeInitializationError

**Issue:** `references/core-api.md:298` documents `StoryStoreAccessedBeforeInitializationError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `StoryStoreAccessedBeforeInitializationError` is a documented extra, a name the source still declares at `code/core/src/preview-errors.ts:211` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-267: Documented extra: StorybookError

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/storybook-error.ts:25
**Export:** StorybookError

**Issue:** `references/core-api.md:298` documents `StorybookError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `StorybookError` is a documented extra, a name the source still declares at `code/core/src/storybook-error.ts:25` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-270: Documented extra: StorybookParameters

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/types/modules/csf.ts:75
**Export:** StorybookParameters

**Issue:** `references/core-api.md:270` documents `StorybookParameters`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `StorybookParameters` is a documented extra, a name the source still declares at `code/core/src/types/modules/csf.ts:75` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-271: Documented extra: StrictArgs

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/csf/story.ts:157
**Export:** StrictArgs

**Issue:** `SKILL.md:133` documents `StrictArgs`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `StrictArgs` is a documented extra, a name the source still declares at `code/core/src/csf/story.ts:157` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-272: Documented extra: StyledComponent

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/frameworks/angular/template/stories/basics/component-with-style/styled.component.ts:9
**Export:** StyledComponent

**Issue:** `references/core-api.md:177` documents `StyledComponent`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `StyledComponent` is a documented extra, a name the source still declares at `code/frameworks/angular/template/stories/basics/component-with-style/styled.component.ts:9` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-275: Documented extra: TEST_PROVIDER_ID

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/vitest/src/constants.ts:12
**Export:** TEST_PROVIDER_ID

**Issue:** `references/addons.md:194` documents `TEST_PROVIDER_ID`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `TEST_PROVIDER_ID` is a documented extra, a name the source still declares at `code/addons/vitest/src/constants.ts:12` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-284: Documented extra: TestRunResult

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/vitest/src/constants.ts:81
**Export:** TestRunResult

**Issue:** `references/addons.md:201` documents `TestRunResult`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `TestRunResult` is a documented extra, a name the source still declares at `code/addons/vitest/src/constants.ts:81` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-285: Documented extra: Theme

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/themes/src/decorators/provider.decorator.tsx:10
**Export:** Theme

**Issue:** `references/addons.md:98` documents `Theme`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Theme` is a documented extra, a name the source still declares at `code/addons/themes/src/decorators/provider.decorator.tsx:10` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-286: Documented extra: ThemeAddonState

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/themes/src/types.ts:1
**Export:** ThemeAddonState

**Issue:** `references/addons.md:114` documents `ThemeAddonState`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ThemeAddonState` is a documented extra, a name the source still declares at `code/addons/themes/src/types.ts:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-288: Documented extra: ThemesParameters

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/themes/src/types.ts:6
**Export:** ThemesParameters

**Issue:** `references/addons.md:115` documents `ThemesParameters`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ThemesParameters` is a documented extra, a name the source still declares at `code/addons/themes/src/types.ts:6` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-289: Documented extra: TitleProps

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/components/components/tooltip/ListItem.tsx:8
**Export:** TitleProps

**Issue:** `references/doc-blocks.md:75` documents `TitleProps`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `TitleProps` is a documented extra, a name the source still declares at `code/core/src/components/components/tooltip/ListItem.tsx:8` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-295: Documented extra: TriggerTestRunRequestPayload

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/vitest/src/constants.ts:74
**Export:** TriggerTestRunRequestPayload

**Issue:** `references/addons.md:200` documents `TriggerTestRunRequestPayload`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `TriggerTestRunRequestPayload` is a documented extra, a name the source still declares at `code/addons/vitest/src/constants.ts:74` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-296: Documented extra: TriggerTestRunResponsePayload

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/vitest/src/constants.ts:83
**Export:** TriggerTestRunResponsePayload

**Issue:** `references/addons.md:202` documents `TriggerTestRunResponsePayload`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `TriggerTestRunResponsePayload` is a documented extra, a name the source still declares at `code/addons/vitest/src/constants.ts:83` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-298: Documented extra: UPDATE_STORY_ARGS

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/core-events/index.ts:159
**Export:** UPDATE_STORY_ARGS

**Issue:** `references/core-api.md:330` documents `UPDATE_STORY_ARGS`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `UPDATE_STORY_ARGS` is a documented extra, a name the source still declares at `code/core/src/core-events/index.ts:159` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-300: Documented extra: WebRenderer

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/types/modules/story.ts:28
**Export:** WebRenderer

**Issue:** `references/core-api.md:271` documents `WebRenderer`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `WebRenderer` is a documented extra, a name the source still declares at `code/core/src/types/modules/story.ts:28` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-305: Documented extra: afterEach

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/a11y/src/preview.tsx:14
**Export:** afterEach

**Issue:** `references/addons.md:58` documents `afterEach`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `afterEach` is a documented extra, a name the source still declares at `code/addons/a11y/src/preview.tsx:14` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-307: Documented extra: babelParse

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/babel/babelParse.ts:28
**Export:** babelParse

**Issue:** `references/core-api.md:336` documents `babelParse`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `babelParse` is a documented extra, a name the source still declares at `code/core/src/babel/babelParse.ts:28` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-308: Documented extra: bail

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/builders/builder-vite/src/index.ts:37
**Export:** bail

**Issue:** `references/framework-config.md:159` documents `bail`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `bail` is a documented extra, a name the source still declares at `code/builders/builder-vite/src/index.ts:37` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-309: Documented extra: build

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/builders/builder-vite/src/index.ts:63
**Export:** build

**Issue:** `SKILL.md:142` documents `build`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `build` is a documented extra, a name the source still declares at `code/builders/builder-vite/src/index.ts:63` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-311: Documented extra: combineTags

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/csf/index.ts:81
**Export:** combineTags

**Issue:** `references/core-api.md:289` documents `combineTags`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `combineTags` is a documented extra, a name the source still declares at `code/core/src/csf/index.ts:81` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-316: Documented extra: createCache

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/theming/index.ts:33
**Export:** createCache

**Issue:** `references/core-api.md:171` documents `createCache`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `createCache` is a documented extra, a name the source still declares at `code/core/src/theming/index.ts:33` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-318: Documented extra: css

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/pseudo-states/src/stories/CustomElement.tsx:1
**Export:** css

**Issue:** `references/core-api.md:20` documents `css`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `css` is a documented extra, a name the source still declares at `code/addons/pseudo-states/src/stories/CustomElement.tsx:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-320: Documented extra: definePreview

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/frameworks/react-vite/src/index.ts:2
**Export:** definePreview

**Issue:** `references/core-api.md:18` documents `definePreview`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `definePreview` is a documented extra, a name the source still declares at `code/frameworks/react-vite/src/index.ts:2` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-323: Documented extra: esmWalker

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/mocking-utils/esmWalker.ts:71
**Export:** esmWalker

**Issue:** `references/core-api.md:338` documents `esmWalker`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `esmWalker` is a documented extra, a name the source still declares at `code/core/src/mocking-utils/esmWalker.ts:71` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-324: Documented extra: experimental_UniversalStore

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager-api/index.ts:3
**Export:** experimental_UniversalStore

**Issue:** `references/core-api.md:149` documents `experimental_UniversalStore`, which the enumerated source API surface lacks and the source still declares; of the 3 files that declare it, the skill cites only `code/core/src/manager-api/index.ts`

**Remediation:** No change: `experimental_UniversalStore` is a documented extra, a name the source still declares at `code/core/src/manager-api/index.ts:3` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-325: Documented extra: experimental_getStatusStore

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager-api/index.ts:8
**Export:** experimental_getStatusStore

**Issue:** `references/core-api.md:152` documents `experimental_getStatusStore`, which the enumerated source API surface lacks and the source still declares; of the 4 files that declare it, the skill cites only `code/core/src/manager-api/index.ts`

**Remediation:** No change: `experimental_getStatusStore` is a documented extra, a name the source still declares at `code/core/src/manager-api/index.ts:8` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-326: Documented extra: experimental_getTestProviderStore

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager-api/index.ts:15
**Export:** experimental_getTestProviderStore

**Issue:** `references/core-api.md:153` documents `experimental_getTestProviderStore`, which the enumerated source API surface lacks and the source still declares; of the 4 files that declare it, the skill cites only `code/core/src/manager-api/index.ts`

**Remediation:** No change: `experimental_getTestProviderStore` is a documented extra, a name the source still declares at `code/core/src/manager-api/index.ts:15` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-331: Documented extra: getPreviewBodyTemplate

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/common/utils/template.ts:10
**Export:** getPreviewBodyTemplate

**Issue:** `references/core-api.md:339` documents `getPreviewBodyTemplate`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `getPreviewBodyTemplate` is a documented extra, a name the source still declares at `code/core/src/common/utils/template.ts:10` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-332: Documented extra: getPreviewHeadTemplate

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/common/utils/template.ts:29
**Export:** getPreviewHeadTemplate

**Issue:** `references/core-api.md:339` documents `getPreviewHeadTemplate`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `getPreviewHeadTemplate` is a documented extra, a name the source still declares at `code/core/src/common/utils/template.ts:29` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-336: Documented extra: getStorybookInfo

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/common/utils/get-storybook-info.ts:139
**Export:** getStorybookInfo

**Issue:** `references/core-api.md:328` documents `getStorybookInfo`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `getStorybookInfo` is a documented extra, a name the source still declares at `code/core/src/common/utils/get-storybook-info.ts:139` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-338: Documented extra: initialGlobals

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/a11y/src/preview.tsx:98
**Export:** initialGlobals

**Issue:** `references/addons.md:64` documents `initialGlobals`, which the enumerated source API surface lacks and the source still declares; of the 9 files that declare it, the skill cites only `code/addons/a11y/src/preview.tsx`

**Remediation:** No change: `initialGlobals` is a documented extra, a name the source still declares at `code/addons/a11y/src/preview.tsx:98` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-339: Documented extra: instrument

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/instrumenter/instrumenter.ts:749
**Export:** instrument

**Issue:** `references/core-api.md:331` documents `instrument`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `instrument` is a documented extra, a name the source still declares at `code/core/src/instrumenter/instrumenter.ts:749` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-340: Documented extra: isExportStory

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/csf/index.ts:51
**Export:** isExportStory

**Issue:** `references/core-api.md:287` documents `isExportStory`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `isExportStory` is a documented extra, a name the source still declares at `code/core/src/csf/index.ts:51` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-341: Documented extra: isPropValid

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/theming/index.ts:34
**Export:** isPropValid

**Issue:** `references/core-api.md:172` documents `isPropValid`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `isPropValid` is a documented extra, a name the source still declares at `code/core/src/theming/index.ts:34` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-343: Documented extra: keyframes

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/manager/components/TourGuide/HighlightElement.tsx:5
**Export:** keyframes

**Issue:** `references/core-api.md:164` documents `keyframes`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `keyframes` is a documented extra, a name the source still declares at `code/core/src/manager/components/TourGuide/HighlightElement.tsx:5` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-344: Documented extra: loadMainConfig

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/common/utils/load-main-config.ts:14
**Export:** loadMainConfig

**Issue:** `references/core-api.md:328` documents `loadMainConfig`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `loadMainConfig` is a documented extra, a name the source still declares at `code/core/src/common/utils/load-main-config.ts:14` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-347: Documented extra: normalizeStories

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/common/utils/normalize-stories.ts:108
**Export:** normalizeStories

**Issue:** `references/core-api.md:328` documents `normalizeStories`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `normalizeStories` is a documented extra, a name the source still declares at `code/core/src/common/utils/normalize-stories.ts:108` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-349: Documented extra: parameters

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/a11y/src/preview.tsx:105
**Export:** parameters

**Issue:** `SKILL.md:35` documents `parameters`, which the enumerated source API surface lacks and the source still declares; of the 23 files that declare it, the skill cites only `code/addons/a11y/src/preview.tsx`

**Remediation:** No change: `parameters` is a documented extra, a name the source still declares at `code/addons/a11y/src/preview.tsx:105` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-350: Documented extra: parseKind

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/csf/index.ts:69
**Export:** parseKind

**Issue:** `references/core-api.md:288` documents `parseKind`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `parseKind` is a documented extra, a name the source still declares at `code/core/src/csf/index.ts:69` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-352: Documented extra: pretty

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/client-logger/index.ts:77
**Export:** pretty

**Issue:** `references/core-api.md:333` documents `pretty`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `pretty` is a documented extra, a name the source still declares at `code/core/src/client-logger/index.ts:77` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-358: Documented extra: sanitize

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/csf/index.ts:8
**Export:** sanitize

**Issue:** `references/core-api.md:290` documents `sanitize`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `code/core/src/csf/index.ts`

**Remediation:** No change: `sanitize` is a documented extra, a name the source still declares at `code/core/src/csf/index.ts:8` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-359: Documented extra: start

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/builders/builder-vite/src/index.ts:41
**Export:** start

**Issue:** `SKILL.md:169` documents `start`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `start` is a documented extra, a name the source still declares at `code/builders/builder-vite/src/index.ts:41` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-360: Documented extra: storeOptions

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/vitest/src/constants.ts:21
**Export:** storeOptions

**Issue:** `references/addons.md:198` documents `storeOptions`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `storeOptions` is a documented extra, a name the source still declares at `code/addons/vitest/src/constants.ts:21` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-361: Documented extra: storyNameFromExport

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/csf/index.ts:35
**Export:** storyNameFromExport

**Issue:** `references/core-api.md:286` documents `storyNameFromExport`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `storyNameFromExport` is a documented extra, a name the source still declares at `code/core/src/csf/index.ts:35` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-362: Documented extra: styled

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/theming/index.ts:6
**Export:** styled

**Issue:** `references/addons.md:112` documents `styled`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `styled` is a documented extra, a name the source still declares at `code/core/src/theming/index.ts:6` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-364: Documented extra: toId

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/csf/index.ts:27
**Export:** toId

**Issue:** `references/core-api.md:284` documents `toId`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `toId` is a documented extra, a name the source still declares at `code/core/src/csf/index.ts:27` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-365: Documented extra: toTestId

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/core/src/csf/index.ts:31
**Export:** toTestId

**Issue:** `references/core-api.md:285` documents `toTestId`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `toTestId` is a documented extra, a name the source still declares at `code/core/src/csf/index.ts:31` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-368: Documented extra: types

**Severity:** Info
**Category:** Structural (observation)
**Source:** code/addons/themes/src/types.ts:1
**Export:** types

**Issue:** `SKILL.md:96` documents `types`, which the enumerated source API surface lacks and the source still declares; of the 76 files that declare it, the skill cites only `code/addons/themes/src/types.ts`

**Remediation:** No change: `types` is a documented extra, a name the source still declares at `code/addons/themes/src/types.ts:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-379: multi-denominator reporting — barrel vs documented surface

**Severity:** Info
**Category:** Coverage (multi-denominator)
**Source:** skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/metadata.json

**Issue:** barrel=1335, documented=228

**Remediation:** No action required: the barrel and the documented surface measure different sets by design, and the report records both counts.

### GAP-380: Provenance line not verified for ComponentEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:27
**Export:** ComponentEntry

**Issue:** the line-check rules found no definition line for `ComponentEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 27 defines `ComponentEntry`; if another line does, set the provenance `source_line` to it.

### GAP-381: Provenance line not verified for DocsEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:34
**Export:** DocsEntry

**Issue:** the line-check rules found no definition line for `DocsEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 34 defines `DocsEntry`; if another line does, set the provenance `source_line` to it.

### GAP-382: Provenance line not verified for GroupEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:21
**Export:** GroupEntry

**Issue:** the line-check rules found no definition line for `GroupEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 21 defines `GroupEntry`; if another line does, set the provenance `source_line` to it.

### GAP-383: Provenance line not verified for HashEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:67
**Export:** HashEntry

**Issue:** the line-check rules found no definition line for `HashEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 67 defines `HashEntry`; if another line does, set the provenance `source_line` to it.

### GAP-384: Provenance line not verified for IndexHash

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:80
**Export:** IndexHash

**Issue:** the line-check rules found no definition line for `IndexHash` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 80 defines `IndexHash`; if another line does, set the provenance `source_line` to it.

### GAP-385: Provenance line not verified for LeafEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:66
**Export:** LeafEntry

**Issue:** the line-check rules found no definition line for `LeafEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 66 defines `LeafEntry`; if another line does, set the provenance `source_line` to it.

### GAP-386: Provenance line not verified for PureArgsTable

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/docs/src/blocks/components/ArgsTable/ArgsTable.tsx:320
**Export:** PureArgsTable

**Issue:** the line-check rules found no definition line for `PureArgsTable` in `code/addons/docs/src/blocks/components/ArgsTable/ArgsTable.tsx`; check by hand

**Remediation:** Open `code/addons/docs/src/blocks/components/ArgsTable/ArgsTable.tsx` and confirm that line 320 defines `PureArgsTable`; if another line does, set the provenance `source_line` to it.

### GAP-387: Provenance line not verified for RootEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:15
**Export:** RootEntry

**Issue:** the line-check rules found no definition line for `RootEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 15 defines `RootEntry`; if another line does, set the provenance `source_line` to it.

### GAP-388: Provenance line not verified for StoryEntry

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/core/src/types/modules/api-stories.ts:45
**Export:** StoryEntry

**Issue:** the line-check rules found no definition line for `StoryEntry` in `code/core/src/types/modules/api-stories.ts`; check by hand

**Remediation:** Open `code/core/src/types/modules/api-stories.ts` and confirm that line 45 defines `StoryEntry`; if another line does, set the provenance `source_line` to it.

### GAP-389: Provenance line not verified for withThemeByClassName

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/index.ts:1
**Export:** withThemeByClassName

**Issue:** the line-check rules found no definition line for `withThemeByClassName` in `code/addons/themes/src/index.ts`; check by hand

**Remediation:** Open `code/addons/themes/src/index.ts` and confirm that line 1 defines `withThemeByClassName`; if another line does, set the provenance `source_line` to it.

### GAP-390: Provenance line not verified for withThemeByDataAttribute

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/index.ts:1
**Export:** withThemeByDataAttribute

**Issue:** the line-check rules found no definition line for `withThemeByDataAttribute` in `code/addons/themes/src/index.ts`; check by hand

**Remediation:** Open `code/addons/themes/src/index.ts` and confirm that line 1 defines `withThemeByDataAttribute`; if another line does, set the provenance `source_line` to it.

### GAP-391: Provenance line not verified for withThemeFromJSXProvider

**Severity:** Info
**Category:** Coverage (provenance-unverified)
**Source:** code/addons/themes/src/index.ts:1
**Export:** withThemeFromJSXProvider

**Issue:** the line-check rules found no definition line for `withThemeFromJSXProvider` in `code/addons/themes/src/index.ts`; check by hand

**Remediation:** Open `code/addons/themes/src/index.ts` and confirm that line 1 defines `withThemeFromJSXProvider`; if another line does, set the provenance `source_line` to it.

### GAP-392: Not checked by script: ComponentAnnotations

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/story-types.md:74
**Export:** ComponentAnnotations

**Issue:** The field list of ComponentAnnotations<R, Args> includes beforeAll; ComponentAnnotations (code/core/src/csf/story.ts:452) extends BaseAnnotations and adds title, id, includeStories, excludeStories, component, subcomponents, play and globals, while beforeAll is a ProjectAnnotations member (code/core/src/csf/story.ts:442).

**Remediation:** Correct the documentation to match the source; no script checks this.

### GAP-393: Not checked by script: StoryContext

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/story-types.md:161
**Export:** StoryContext

**Issue:** The StoryContext field list includes playUntil; StoryContext (code/core/src/csf/story.ts:268) declares no playUntil member (playUntil is instrumenter state, code/core/src/instrumenter/instrumenter.ts:76).

**Remediation:** Correct the documentation to match the source; no script checks this.

### GAP-394: Not checked by script: ViewportParameters

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/story-types.md:272
**Export:** ViewportParameters

**Issue:** Documented as { viewport?: { disable?: boolean; options: Record<string, ViewportMap> } }; the source (code/core/src/viewport/types.ts:33) types options as Record<string, Viewport>, and ViewportMap is itself Record<string, Viewport> (types.ts:14).

**Remediation:** Correct the documentation to match the source; no script checks this.

### GAP-395: Not checked by script: Brand

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/framework-config.md:375
**Export:** Brand

**Issue:** Documented as { title: string | undefined; url: string | null | undefined; image?: string | null; target?: string }; the source (code/core/src/theming/types.ts:64) declares image: string | null | undefined and target: string | null | undefined, neither optional.

**Remediation:** Correct the documentation to match the source; no script checks this.

### GAP-396: Not checked by script: FULL_RUN_TRIGGERS

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/addons.md:199
**Export:** FULL_RUN_TRIGGERS

**Issue:** Documented with Kind type and the value ('global' | 'run-all')[]; the source declares a constant, export const FULL_RUN_TRIGGERS: RunTrigger[] = ['global', 'run-all'] as const (code/addons/vitest/src/constants.ts:61).

**Remediation:** Correct the documentation to match the source; no script checks this.

### GAP-397: Not checked by script: storeOptions

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/addons.md:198
**Export:** storeOptions

**Issue:** Documented as { initialState: { coverage, a11y, watching, componentTestStatuses, ... } }; in the source (code/addons/vitest/src/constants.ts:21) coverage and a11y sit under initialState.config and componentTestStatuses under initialState.currentRun.

**Remediation:** Correct the documentation to match the source; no script checks this.

### GAP-398: Not checked by script: DocsRenderer

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/doc-blocks.md:149
**Export:** DocsRenderer

**Issue:** Described as the React component that renders an entire docs page (references/addons.md:243 gives Kind component); the source declares export class DocsRenderer<TRenderer extends Renderer> with render and unmount members (code/addons/docs/src/DocsRenderer.tsx:48), a plain class that renders through React, not a component.

**Remediation:** Correct the documentation to match the source; no script checks this.

### GAP-399: Not checked by script: viteFinal

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/framework-config.md:118
**Export:** viteFinal

**Issue:** The quoted react-vite preset declares export const viteFinal: PresetProperty<'viteFinal'> = async (config, options) => ...; code/frameworks/react-vite/src/preset.ts:10 declares export const viteFinal: NonNullable<StorybookConfig['viteFinal']> = async (config, { presets }) => .... The signature check matched the bare names config, options against the addon-docs preset's viteFinal candidate (code/addons/docs/src/preset.ts:159), so no script records the difference.

**Remediation:** Correct the documentation to match the source; no script checks this.

### GAP-400: Not checked by script: core

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/framework-config.md:114
**Export:** core

**Issue:** The quoted react-vite preset sets builder: '@storybook/builder-vite' and renderer: '@storybook/react/preset'; code/frameworks/react-vite/src/preset.ts:5 sets builder: import.meta.resolve('@storybook/builder-vite') and renderer: import.meta.resolve('@storybook/react/preset'), resolved paths rather than the package names.

**Remediation:** Correct the documentation to match the source; no script checks this.

### GAP-401: Not checked by script: MockUniversalStore

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/core-api.md:151
**Export:** MockUniversalStore

**Issue:** Documented as a storybook/manager-api export; code/core/src/manager-api/index.ts:5 exports it only as experimental_MockUniversalStore. The stale classification records it as a documented extra because code/core/src/shared/universal-store/mock.ts:40 declares the class.

**Remediation:** Correct the documentation to match the source; no script checks this.

### GAP-402: Not checked by script: Meta

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/core-api.md:249
**Export:** Meta

**Issue:** Listed as an export of storybook/internal/types (via ComponentAnnotations); code/core/src/types/modules/csf.ts re-exports ComponentAnnotations and no Meta, so import { Meta } from 'storybook/internal/types' fails.

**Remediation:** Correct the documentation to match the source; no script checks this.

### GAP-403: Not checked by script: StoryObj

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/core-api.md:250
**Export:** StoryObj

**Issue:** Listed as an export of storybook/internal/types (via StoryAnnotations); code/core/src/types/modules/csf.ts re-exports StoryAnnotations and no StoryObj.

**Remediation:** Correct the documentation to match the source; no script checks this.

### GAP-404: Not checked by script: Decorator

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/core-api.md:252
**Export:** Decorator

**Issue:** Listed as an export of storybook/internal/types (via DecoratorFunction); code/core/src/types/modules/csf.ts re-exports DecoratorFunction and no Decorator.

**Remediation:** Correct the documentation to match the source; no script checks this.

### GAP-405: Not checked by script: Loader

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/core-api.md:256
**Export:** Loader

**Issue:** Listed as an export of storybook/internal/types (via LoaderFunction); code/core/src/types/modules/csf.ts re-exports LoaderFunction and no Loader.

**Remediation:** Correct the documentation to match the source; no script checks this.

### Discovery Quality

**Discovery Test:** not run: the hard gate blocked the run
