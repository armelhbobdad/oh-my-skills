# Framework, Renderer, Builder and Addon Packages — Export Index

The exports of the framework, renderer, builder and addon package entry points that the topic references (`framework-config.md`, `addons.md`, `doc-blocks.md`) do not document, grouped by import path. Several are preset hooks Storybook itself calls (`@storybook/*/preset`) rather than functions to import.

Each row gives the export's declaration as the source writes it at the cited line (`[SRC:...]` for a line read from the source, `[AST:...]` for one an ast-grep recipe matched) and the first sentence of its JSDoc when it has one. An export re-exported under another name says which local name it renames.

## Contents

- [`@storybook/addon-docs/blocks`](#storybookaddon-docsblocks) — 36 exports
- [`@storybook/addon-vitest/constants`](#storybookaddon-vitestconstants) — 11 exports
- [`@storybook/addon-docs/preset`](#storybookaddon-docspreset) — 5 exports
- [`@storybook/addon-docs/mdx-loader`](#storybookaddon-docsmdx-loader) — 2 exports
- [`@storybook/addon-vitest/internal/coverage-reporter`](#storybookaddon-vitestinternalcoverage-reporter) — 2 exports
- [`@storybook/addon-vitest/internal/global-setup`](#storybookaddon-vitestinternalglobal-setup) — 2 exports
- [`@storybook/addon-vitest/internal/setup-file`](#storybookaddon-vitestinternalsetup-file) — 2 exports
- [`@storybook/addon-vitest/internal/test-utils`](#storybookaddon-vitestinternaltest-utils) — 2 exports
- [`@storybook/addon-vitest/preset`](#storybookaddon-vitestpreset) — 2 exports
- [`@storybook/react/entry-preview`](#storybookreactentry-preview) — 2 exports
- [`@storybook/react/preset`](#storybookreactpreset) — 2 exports
- [`@storybook/addon-a11y/postinstall`](#storybookaddon-a11ypostinstall) — 1 exports
- [`@storybook/addon-a11y/preset`](#storybookaddon-a11ypreset) — 1 exports
- [`@storybook/addon-docs/angular`](#storybookaddon-docsangular) — 1 exports
- [`@storybook/addon-docs/ember`](#storybookaddon-docsember) — 1 exports
- [`@storybook/addon-vitest/postinstall`](#storybookaddon-vitestpostinstall) — 1 exports
- [`@storybook/builder-vite/preset`](#storybookbuilder-vitepreset) — 1 exports
- [`@storybook/react`](#storybookreact) — 1 exports

## `@storybook/addon-docs/blocks`

Entry: `code/addons/docs/src/blocks.ts`.

| Export | Kind | Declaration | Source |
|---|---|---|---|
| `AddContext` | function | `export const AddContext: FC<PropsWithChildren<DocsContextProps>> = (props) => {` | `[SRC:code/addons/docs/src/blocks/blocks/mdx.tsx:L27]` |
| `anchorBlockIdFromId` | function | `` export const anchorBlockIdFromId = (storyId: string) => `anchor--${storyId}`; `` | `[SRC:code/addons/docs/src/blocks/blocks/Anchor.tsx:L4]` |
| `AnchorMdx` | function | `export const AnchorMdx: FC<PropsWithChildren<AnchorMdxProps>> = (props) => {` | `[SRC:code/addons/docs/src/blocks/blocks/mdx.tsx:L98]` |
| `AnchorProps` | interface | `export interface AnchorProps {` | `[SRC:code/addons/docs/src/blocks/blocks/Anchor.tsx:L6]` |
| `argsHash` | function | `export function argsHash(args: Args): ArgsHash {` | `[SRC:code/addons/docs/src/blocks/blocks/SourceContainer.tsx:L11]` |
| `assertIsFn` | function | `export const assertIsFn = (val: any) => {` | `[SRC:code/addons/docs/src/blocks/blocks/mdx.tsx:L19]` |
| `CodeOrSourceMdx` | function | `export const CodeOrSourceMdx: FC<PropsWithChildren<CodeOrSourceMdxProps>> = ({ className, children, ...rest }) => {` | `[SRC:code/addons/docs/src/blocks/blocks/mdx.tsx:L39]` |
| `ColorProps` | type | `export type ColorProps = ColorControlProps;` | `[SRC:code/addons/docs/src/blocks/controls/index.tsx:L10]` |
| `Component` | type | `export type Component = any;` | `[SRC:code/addons/docs/src/blocks/blocks/types.ts:L7]` |
| `DescriptionType` | enum | `export enum DescriptionType {` | `[SRC:code/addons/docs/src/blocks/blocks/Description.tsx:L9]` |
| `DocsContainerProps` | interface | `export interface DocsContainerProps<TFramework extends Renderer = Renderer> {` | `[SRC:code/addons/docs/src/blocks/blocks/DocsContainer.tsx:L18]` |
| `DocsProps` | type | `export type DocsProps<TRenderer extends Renderer = Renderer> = {` | `[SRC:code/addons/docs/src/blocks/blocks/Docs.tsx:L12]` |
| `DocsStoryProps` | type | `export type DocsStoryProps = {` | `[SRC:code/addons/docs/src/blocks/blocks/types.ts:L9]` |
| `ExternalDocs` | function | `export function ExternalDocs<TRenderer extends Renderer = Renderer>({ projectAnnotationsList, children }: PropsWithChildren<ExternalDocsProps<TRenderer>>) {` | `[SRC:code/addons/docs/src/blocks/blocks/external/ExternalDocs.tsx:L26]` |
| `ExternalDocsContainer` | function | `export const ExternalDocsContainer: React.FC<React.PropsWithChildren<{ projectAnnotations: any }>> = ({ projectAnnotations, children }) => {` | `[SRC:code/addons/docs/src/blocks/blocks/external/ExternalDocsContainer.tsx:L12]` |
| `ExternalDocsProps` | type | `export type ExternalDocsProps<TRenderer extends Renderer = Renderer> = {` | `[SRC:code/addons/docs/src/blocks/blocks/external/ExternalDocs.tsx:L11]` |
| `extractTitle` | function | `export const extractTitle = (title: ComponentTitle) => {` | `[SRC:code/addons/docs/src/blocks/blocks/Title.tsx:L24]` |
| `getStoryId` | function | `export const getStoryId = (props: StoryProps, context: DocsContextProps): StoryId => {` | `[SRC:code/addons/docs/src/blocks/blocks/Story.tsx:L62]` |
| `getStoryProps` | function | `export const getStoryProps = <TFramework extends Renderer>(props: StoryParameters, story: PreparedStory<TFramework>, context: DocsContextProps<TFramework>): PureStoryProps => {` | `[SRC:code/addons/docs/src/blocks/blocks/Story.tsx:L75]` |
| `HeaderMdx` | function | `export const HeaderMdx: FC<PropsWithChildren<HeaderMdxProps>> = (props) => {` | `[SRC:code/addons/docs/src/blocks/blocks/mdx.tsx:L215]` |
| `HeadersMdx` | const | `export const HeadersMdx = SUPPORTED_MDX_HEADERS.reduce((acc, headerType) => ({ ...acc, [headerType]: (props: object) => <HeaderMdx as={headerType} {...props} /> }), {});` | `[SRC:code/addons/docs/src/blocks/blocks/mdx.tsx:L232]` |
| `HeadingProps` | interface | `export interface HeadingProps {` | `[SRC:code/addons/docs/src/blocks/blocks/Heading.tsx:L11]` |
| `Of` | type | `export type Of = Parameters<DocsContextProps['resolveOf']>[0];` | `[SRC:code/addons/docs/src/blocks/blocks/useOf.ts:L11]` |
| `PRIMARY_STORY` | const | `export const PRIMARY_STORY = '^';` | `[SRC:code/addons/docs/src/blocks/blocks/types.ts:L3]` |
| `slugs` | const | `export const slugs = new GithubSlugger();` | `[SRC:code/addons/docs/src/blocks/blocks/Heading.tsx:L15]` |
| `SourceContainer` | function | `export const SourceContainer: FC<PropsWithChildren<{ channel: DocsContextProps['channel'] }>> = ({ children, channel }) => {` | `[SRC:code/addons/docs/src/blocks/blocks/SourceContainer.tsx:L38]` |
| `SourceContext` | const | `export const SourceContext: Context<SourceContextProps> = createContext({ sources: {} });` | `[SRC:code/addons/docs/src/blocks/blocks/SourceContainer.tsx:L27]` |
| `SourceContextProps` | interface | `export interface SourceContextProps {` | `[SRC:code/addons/docs/src/blocks/blocks/SourceContainer.tsx:L22]` |
| `SourceItem` | interface | `export interface SourceItem {` | `[SRC:code/addons/docs/src/blocks/blocks/SourceContainer.tsx:L15]` |
| `SourceParameters` | type | `export type SourceParameters = SourceCodeProps & {` | `[SRC:code/addons/docs/src/blocks/blocks/Source.tsx:L16]` |
| `SourceProps` | type | `export type SourceProps = SourceParameters & {` | `[SRC:code/addons/docs/src/blocks/blocks/Source.tsx:L28]` |
| `StoryProps` | type | `export type StoryProps = StoryRefProps & StoryParameters;` | `[SRC:code/addons/docs/src/blocks/blocks/Story.tsx:L60]` |
| `StorySources` | type | `export type StorySources = Record<StoryId, Record<ArgsHash, SourceItem>>;` | `[SRC:code/addons/docs/src/blocks/blocks/SourceContainer.tsx:L20]` |
| `UNKNOWN_ARGS_HASH` | const | `export const UNKNOWN_ARGS_HASH = '--unknown--';` | `[SRC:code/addons/docs/src/blocks/blocks/SourceContainer.tsx:L36]` |
| `useSourceProps` | function | `export const useSourceProps = (props: SourceProps, docsContext: DocsContextProps<any>, sourceContext: SourceContextProps): PureSourceProps => {` | `[SRC:code/addons/docs/src/blocks/blocks/Source.tsx:L101]` |
| `Wrapper` | const | `export const Wrapper = withMdxComponentOverride('Wrapper', WrapperImpl);` | `[SRC:code/addons/docs/src/blocks/blocks/Wrapper.tsx:L10]` |

## `@storybook/addon-vitest/constants`

Entry: `code/addons/vitest/src/constants.ts`.

| Export | Kind | Declaration | Source |
|---|---|---|---|
| `COVERAGE_DIRECTORY` | const | `export const COVERAGE_DIRECTORY = 'coverage';` | `[SRC:code/addons/vitest/src/constants.ts:L19]` |
| `DOCUMENTATION_FATAL_ERROR_LINK` | const | `` export const DOCUMENTATION_FATAL_ERROR_LINK = `${DOCUMENTATION_LINK}#what-happens-if-vitest-itself-has-an-error`; `` | `[SRC:code/addons/vitest/src/constants.ts:L17]` |
| `DOCUMENTATION_LINK` | const | `export const DOCUMENTATION_LINK = 'writing-tests/integrations/vitest-addon';` | `[SRC:code/addons/vitest/src/constants.ts:L16]` |
| `STATUS_STORE_CHANNEL_EVENT_NAME` | const | `export const STATUS_STORE_CHANNEL_EVENT_NAME = 'UNIVERSAL_STORE:storybook/status';` | `[SRC:code/addons/vitest/src/constants.ts:L64]` |
| `STATUS_TYPE_ID_A11Y` | const | `export const STATUS_TYPE_ID_A11Y = 'storybook/a11y';` | `[SRC:code/addons/vitest/src/constants.ts:L68]` |
| `STATUS_TYPE_ID_COMPONENT_TEST` | const | `export const STATUS_TYPE_ID_COMPONENT_TEST = 'storybook/component-test';` | `[SRC:code/addons/vitest/src/constants.ts:L67]` |
| `STORE_CHANNEL_EVENT_NAME` | const | `` export const STORE_CHANNEL_EVENT_NAME = `UNIVERSAL_STORE:${storeOptions.id}`; `` | `[SRC:code/addons/vitest/src/constants.ts:L63]` |
| `TEST_PROVIDER_STORE_CHANNEL_EVENT_NAME` | const | `export const TEST_PROVIDER_STORE_CHANNEL_EVENT_NAME = 'UNIVERSAL_STORE:storybook/test-provider';` | `[SRC:code/addons/vitest/src/constants.ts:L65]` |
| `TRIGGER_TEST_RUN_REQUEST` | const | `` export const TRIGGER_TEST_RUN_REQUEST = `${ADDON_ID}/trigger-test-run-request`; `` | `[SRC:code/addons/vitest/src/constants.ts:L71]` |
| `TRIGGER_TEST_RUN_RESPONSE` | const | `` export const TRIGGER_TEST_RUN_RESPONSE = `${ADDON_ID}/trigger-test-run-response`; `` | `[SRC:code/addons/vitest/src/constants.ts:L72]` |
| `TUTORIAL_VIDEO_LINK` | const | `export const TUTORIAL_VIDEO_LINK = 'https://youtu.be/Waht9qq7AoA';` | `[SRC:code/addons/vitest/src/constants.ts:L15]` |

## `@storybook/addon-docs/preset`

Entry: `code/addons/docs/src/preset.ts`.

| Export | Kind | Declaration | Source |
|---|---|---|---|
| `docs` | const | `export { webpackX as webpack, docsX as docs, optimizeViteDeps };` — `docsX` exported under this name | `[SRC:code/addons/docs/src/preset.ts:L224]` |
| `experimental_manifests` | function | `export const manifests: PresetPropertyFn<'experimental_manifests', StorybookConfigRaw, { manifestEntries: IndexEntry[] }> = async (existingManifests = {}, { manifestEntries }) => {` — `manifests` exported under this name; Generates a manifest of docs entries. | `[SRC:code/addons/docs/src/manifest.ts:L135]` |
| `optimizeViteDeps` | const | `export { webpackX as webpack, docsX as docs, optimizeViteDeps };` | `[SRC:code/addons/docs/src/preset.ts:L224]` |
| `resolvedReact` | function | `export const resolvedReact = async (existing: any) => ({ react: existing?.react ?? resolvePackageDir('react'), reactDom: existing?.reactDom ?? resolvePackageDir('react-dom'), mdx: existing?.mdx ?? fileURLToPath(import.meta.resolve('@mdx-js/react')) });` — If the user has not installed react explicitly in their project, the resolvedReact preset will not be set. | `[SRC:code/addons/docs/src/preset.ts:L208]` |
| `webpack` | const | `export { webpackX as webpack, docsX as docs, optimizeViteDeps };` — `webpackX` exported under this name | `[SRC:code/addons/docs/src/preset.ts:L224]` |

## `@storybook/addon-docs/mdx-loader`

Entry: `code/addons/docs/src/mdx-loader.ts`.

| Export | Kind | Declaration | Source |
|---|---|---|---|
| `CompileOptions` | interface | `export interface CompileOptions {` | `[SRC:code/addons/docs/src/mdx-loader.ts:L7]` |
| `MdxCompileOptions` | type | `export type MdxCompileOptions = Parameters<typeof mdxCompile>[1];` | `[SRC:code/addons/docs/src/mdx-loader.ts:L5]` |

## `@storybook/addon-vitest/internal/coverage-reporter`

Entry: `code/addons/vitest/src/node/coverage-reporter.ts`.

| Export | Kind | Declaration | Source |
|---|---|---|---|
| `module.exports` | class | `export { StorybookCoverageReporter as 'module.exports' };` — `StorybookCoverageReporter` exported under this name; This is exported weirdly because the coverage tool loading this uses `Cont = require(name)`. | `[AST:code/addons/vitest/src/node/coverage-reporter.ts:L56]` |
| `StorybookCoverageReporterOptions` | type | `export type StorybookCoverageReporterOptions = {` | `[SRC:code/addons/vitest/src/node/coverage-reporter.ts:L9]` |

## `@storybook/addon-vitest/internal/global-setup`

Entry: `code/addons/vitest/src/vitest-plugin/global-setup.ts`.

| Export | Kind | Declaration | Source |
|---|---|---|---|
| `setup` | function | `export const setup = async ({ config }: TestProject) => {` | `[SRC:code/addons/vitest/src/vitest-plugin/global-setup.ts:L71]` |
| `teardown` | function | `export const teardown = async () => {` | `[SRC:code/addons/vitest/src/vitest-plugin/global-setup.ts:L77]` |

## `@storybook/addon-vitest/internal/setup-file`

Entry: `code/addons/vitest/src/vitest-plugin/setup-file.ts`.

| Export | Kind | Declaration | Source |
|---|---|---|---|
| `modifyErrorMessage` | function | `export const modifyErrorMessage = ({ task }: { task: Task }) => {` | `[SRC:code/addons/vitest/src/vitest-plugin/setup-file.ts:L22]` |
| `Task` | type | `export type Task = Partial<RunnerTask> & {` | `[SRC:code/addons/vitest/src/vitest-plugin/setup-file.ts:L15]` |

## `@storybook/addon-vitest/internal/test-utils`

Entry: `code/addons/vitest/src/vitest-plugin/test-utils.ts`.

| Export | Kind | Declaration | Source |
|---|---|---|---|
| `convertToFilePath` | function | `export const convertToFilePath = (url: string): string => {` — Converts a file URL to a file path, handling URL encoding | `[SRC:code/addons/vitest/src/vitest-plugin/test-utils.ts:L25]` |
| `testStory` | function | `export const testStory = ({ exportName, story, meta, skipTags, storyId, componentPath, testName, componentName }: { exportName: string; story: ComposedStoryFn \| Story<Renderer>; meta: ComponentAnnotations \| Meta<Renderer>; skipTags: string[]; storyId: string; componentPath?: string; testName?: string; componentName?: string; }) => {` | `[SRC:code/addons/vitest/src/vitest-plugin/test-utils.ts:L34]` |

## `@storybook/addon-vitest/preset`

Entry: `code/addons/vitest/src/preset.ts`.

| Export | Kind | Declaration | Source |
|---|---|---|---|
| `experimental_serverChannel` | function | `export const experimental_serverChannel = async (channel: Channel, options: Options) => {` | `[SRC:code/addons/vitest/src/preset.ts:L59]` |
| `staticDirs` | function | `export const staticDirs: PresetPropertyFn<'staticDirs'> = async (values = [], options) => {` | `[SRC:code/addons/vitest/src/preset.ts:L308]` |

## `@storybook/react/entry-preview`

Entry: `code/renderers/react/src/entry-preview.tsx`.

| Export | Kind | Declaration | Source |
|---|---|---|---|
| `beforeAll` | function | `export const beforeAll = async () => {` | `[SRC:code/renderers/react/src/entry-preview.tsx:L49]` |
| `mount` | function | `export const mount: BaseAnnotations<ReactRenderer>['mount'] =` | `[SRC:code/renderers/react/src/mount.ts:L5]` |

## `@storybook/react/preset`

Entry: `code/renderers/react/src/preset.ts`.

| Export | Kind | Declaration | Source |
|---|---|---|---|
| `experimental_enrichCsf` | function | `export const enrichCsf: PresetPropertyFn<'experimental_enrichCsf'> = async (input, options) => {` — `enrichCsf` exported under this name | `[SRC:code/renderers/react/src/enrichCsf.ts:L10]` |
| `internal_getArgTypesData` | function | `export async function internal_getArgTypesData(_input: unknown, options: InternalGetArgTypesDataOptions): Promise<ArgTypes \| null> {` | `[SRC:code/renderers/react/src/preset.ts:L87]` |

## `@storybook/addon-a11y/postinstall`

Entry: `code/addons/a11y/src/postinstall.ts`.

| Export | Kind | Declaration | Source |
|---|---|---|---|
| `default` | function | `export default async function postinstall(options: PostinstallOptions) {` — `postinstall` exported under this name | `[SRC:code/addons/a11y/src/postinstall.ts:L5]` |

## `@storybook/addon-a11y/preset`

Entry: `code/addons/a11y/src/preset.ts`.

| Export | Kind | Declaration | Source |
|---|---|---|---|
| `isAddonA11yEnabled` | const | `export const isAddonA11yEnabled = true;` | `[SRC:code/addons/a11y/src/preset.ts:L3]` |

## `@storybook/addon-docs/angular`

Entry: `code/addons/docs/src/angular/index.ts`.

| Export | Kind | Declaration | Source |
|---|---|---|---|
| `setCompodocJson` | function | `export const setCompodocJson = (compodocJson: any) => {` | `[SRC:code/addons/docs/src/angular/index.ts:L1]` |

## `@storybook/addon-docs/ember`

Entry: `code/addons/docs/src/ember/index.ts`.

| Export | Kind | Declaration | Source |
|---|---|---|---|
| `setJSONDoc` | function | `export const setJSONDoc = (jsondoc: any) => {` | `[SRC:code/addons/docs/src/ember/index.ts:L1]` |

## `@storybook/addon-vitest/postinstall`

Entry: `code/addons/vitest/src/postinstall.ts`.

| Export | Kind | Declaration | Source |
|---|---|---|---|
| `isConfigAlreadySetup` | function | `export function isConfigAlreadySetup(_configPath: string, configContent: string) {` | `[SRC:code/addons/vitest/src/postinstall.ts:L410]` |

## `@storybook/builder-vite/preset`

Entry: `code/builders/builder-vite/src/preset.ts`.

| Export | Kind | Declaration | Source |
|---|---|---|---|
| `viteCorePlugins` | function | `export async function viteCorePlugins(_: PluginOption[], options: Options): Promise<PluginOption[]> {` — Preset that provides the core Storybook Vite plugins shared between `@storybook/builder-vite` and `@storybook/addon-vitest`. | `[SRC:code/builders/builder-vite/src/preset.ts:L19]` |

## `@storybook/react`

Entry: `code/renderers/react/src/index.ts`.

| Export | Kind | Declaration | Source |
|---|---|---|---|
| `ReactTypes` | interface | `export interface ReactTypes extends ReactRenderer {` | `[SRC:code/renderers/react/src/types.ts:L33]` |
