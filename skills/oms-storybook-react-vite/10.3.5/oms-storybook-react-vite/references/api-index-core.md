# `storybook/*` Subpaths — Export Index

The exports of the `storybook/*` subpaths that the topic references (`core-api.md`, `story-types.md`) do not document, grouped by import path. Most are addon- and preset-authoring infrastructure (`storybook/internal/*`); the subpaths whose source the skill brief excludes (`components`, `channels`, `csf-tools`, `core-server`, `router`, `node-logger`, `telemetry`, `babel`) are not indexed.

Each row gives the export's declaration as the source writes it at the cited line (`[SRC:...]` for a line read from the source, `[AST:...]` for one an ast-grep recipe matched) and the first sentence of its JSDoc when it has one. An export re-exported under another name says which local name it renames.

## Contents

- [`storybook/internal/common`](#storybookinternalcommon) — 102 exports
- [`storybook/internal/csf`](#storybookinternalcsf) — 70 exports
- [`storybook/internal/docs-tools`](#storybookinternaldocs-tools) — 45 exports
- [`storybook/internal/server-errors`](#storybookinternalserver-errors) — 30 exports
- [`storybook/manager-api`](#storybookmanager-api) — 29 exports
- [`storybook/internal/cli`](#storybookinternalcli) — 28 exports
- [`storybook/internal/mocking-utils`](#storybookinternalmocking-utils) — 23 exports
- [`storybook/internal/core-events`](#storybookinternalcore-events) — 16 exports
- [`storybook/preview-api`](#storybookpreview-api) — 12 exports
- [`storybook/internal/instrumenter`](#storybookinternalinstrumenter) — 9 exports
- [`storybook/viewport`](#storybookviewport) — 8 exports
- [`storybook/actions`](#storybookactions) — 6 exports
- [`storybook/theming`](#storybooktheming) — 6 exports
- [`storybook/internal/preview-errors`](#storybookinternalpreview-errors) — 5 exports
- [`storybook/internal/bin/loader`](#storybookinternalbinloader) — 4 exports
- [`storybook/test`](#storybooktest) — 3 exports
- [`storybook/internal/manager-errors`](#storybookinternalmanager-errors) — 2 exports
- [`storybook/internal/manager/globals`](#storybookinternalmanagerglobals) — 2 exports
- [`storybook/internal/mocking-utils/mocker-runtime`](#storybookinternalmocking-utilsmocker-runtime) — 1 exports

## `storybook/internal/common`

Entry: `code/core/src/common/index.ts`.

| Export | Kind | Declaration | Source |
|---|---|---|---|
| `builderPackages` | const | `export const builderPackages: Record<string, SupportedBuilder> = {` | `[SRC:code/core/src/common/utils/get-storybook-info.ts:L64]` |
| `cache` | const | `export const cache = createFileSystemCache({ basePath: resolvePathInStorybookCache('dev-server'), ns: 'storybook' });` | `[SRC:code/core/src/common/utils/cache.ts:L4]` |
| `checkAddonOrder` | function | `export const checkAddonOrder = async ({ before, after, configFile, getConfig }: Options) => {` | `[SRC:code/core/src/common/utils/check-addon-order.ts:L39]` |
| `checkRef` | function | `export const checkRef = (url: string) =>` | `[SRC:code/core/src/common/utils/get-storybook-refs.ts:L61]` |
| `commonGlobOptions` | function | `export const commonGlobOptions = (glob: string) =>` | `[SRC:code/core/src/common/utils/common-glob-options.ts:L4]` |
| `compilerPackages` | const | `export const compilerPackages: Record<string, CoreWebpackCompiler> = {` | `[SRC:code/core/src/common/utils/get-storybook-info.ts:L71]` |
| `createFileSystemCache` | function | `export function createFileSystemCache(options: FileSystemCacheOptions): FileSystemCache {` | `[SRC:code/core/src/common/utils/file-cache.ts:L160]` |
| `createLogStream` | function | `export const createLogStream = async (logFileName = 'storybook.log'): Promise<{` — Given a file name, creates an object with utilities to manage a log file. | `[SRC:code/core/src/common/utils/cli.ts:L114]` |
| `DEFAULT_FILES_PATTERN` | const | `export const DEFAULT_FILES_PATTERN = '**/*.@(mdx\|stories.@(js\|jsx\|mjs\|ts\|tsx))';` | `[SRC:code/core/src/common/utils/normalize-stories.ts:L15]` |
| `doesVariableOrFunctionDeclarationExist` | function | `export function doesVariableOrFunctionDeclarationExist(node: t.Node, name: string) {` — Checks if the following node declarations exists in the main config file. | `[SRC:code/core/src/common/utils/wrap-getAbsolutePath-utils.ts:L17]` |
| `executeCommand` | function | `export function executeCommand(options: ExecuteCommandOptions): ResultPromise {` | `[SRC:code/core/src/common/utils/command.ts:L49]` |
| `ExecuteCommandOptions` | type | `export type ExecuteCommandOptions = Omit<Options, 'cancelSignal'> & {` | `[SRC:code/core/src/common/utils/command.ts:L19]` |
| `executeCommandSync` | function | `export function executeCommandSync(options: ExecuteCommandOptions): string {` | `[SRC:code/core/src/common/utils/command.ts:L63]` |
| `executeNodeCommand` | function | `export function executeNodeCommand({ scriptPath, args, options }: { scriptPath: string; args?: string[]; options?: Options; }): ResultPromise {` | `[SRC:code/core/src/common/utils/command.ts:L79]` |
| `extractFrameworkPackageName` | function | `export const extractFrameworkPackageName = (framework: string) => {` — Extracts the proper framework name from the given framework field. | `[SRC:code/core/src/common/utils/get-framework-name.ts:L34]` |
| `extractRenderer` | function | `export async function extractRenderer(frameworkName: string) {` — Extracts the proper renderer name from the given framework name. | `[SRC:code/core/src/common/utils/get-renderer-name.ts:L37]` |
| `FileOptions` | type | `` export type FileOptions = MergeExclusive<{ /** * File extension. * * Mutually exclusive with the `name` option. * * _You usually won't need this option. Specify it only when actually needed._ */ readonly extension?: string; }, { /** * Filename. * * Mutually exclusive with the `extension` option. * * _You usually won't need this option. Specify it only when actually needed._ */ readonly name?: string; }>; `` | `[SRC:code/core/src/common/utils/cli.ts:L24]` |
| `FileSystemCache` | class | `export class FileSystemCache {` | `[SRC:code/core/src/common/utils/file-cache.ts:L29]` |
| `filterPresetsConfig` | function | `export function filterPresetsConfig(presetsConfig: PresetConfig[]): PresetConfig[] {` | `[SRC:code/core/src/common/presets.ts:L35]` |
| `findConfigFile` | function | `export const findConfigFile = (prefix: string, configDir: string) => {` | `[SRC:code/core/src/common/utils/get-storybook-info.ts:L105]` |
| `findFilesUp` | function | `export const findFilesUp = (matchers: string[], baseDir = process.cwd()) => {` — Finds files in the directory tree up to the project root | `[SRC:code/core/src/common/utils/paths.ts:L64]` |
| `formatFileContent` | function | `export async function formatFileContent(filePath: string, content: string): Promise<string> {` — Format the content of a file using prettier. | `[SRC:code/core/src/common/utils/formatter.ts:L51]` |
| `frameworkPackages` | const | `export const frameworkPackages: Record<string, SupportedFramework> = {` | `[SRC:code/core/src/common/utils/get-storybook-info.ts:L39]` |
| `frameworkToBuilder` | const | `export const frameworkToBuilder: Record<SupportedFramework, SupportedBuilder> = {` | `[SRC:code/core/src/common/utils/framework.ts:L41]` |
| `frameworkToRenderer` | const | `export const frameworkToRenderer: Record<SupportedFramework \| SupportedRenderer, SupportedRenderer> = {` | `[SRC:code/core/src/common/utils/framework.ts:L3]` |
| `getAbsolutePathWrapperAsCallExpression` | function | `export function getAbsolutePathWrapperAsCallExpression(isConfigTypescript: boolean): t.FunctionDeclaration {` — Returns AST for the following function | `[SRC:code/core/src/common/utils/wrap-getAbsolutePath-utils.ts:L141]` |
| `getAbsolutePathWrapperName` | function | `export function getAbsolutePathWrapperName(config: ConfigFile) {` — Returns the name of the getAbsolutePath wrapper function if it exists in the main config file. | `[SRC:code/core/src/common/utils/wrap-getAbsolutePath-utils.ts:L57]` |
| `getAddonNames` | function | `export const getAddonNames = (mainConfig: StorybookConfig): string[] => {` | `[SRC:code/core/src/common/utils/get-addon-names.ts:L5]` |
| `getAutoRefs` | function | `export const getAutoRefs = async (options: Options): Promise<Record<string, Ref>> => {` | `[SRC:code/core/src/common/utils/get-storybook-refs.ts:L12]` |
| `getConfigInfo` | function | `export const getConfigInfo = (configDir?: string) => {` | `[SRC:code/core/src/common/utils/get-storybook-info.ts:L111]` |
| `getDirectoryFromWorkingDir` | function | `export const getDirectoryFromWorkingDir = ({ configDir, workingDir, directory }: NormalizeOptions & { directory: string }) => {` | `[SRC:code/core/src/common/utils/normalize-stories.ts:L25]` |
| `getEnvConfig` | function | `export function getEnvConfig(program: Record<string, any>, configEnv: Record<string, any>): void {` | `[SRC:code/core/src/common/utils/cli.ts:L69]` |
| `getFieldsForGetAbsolutePathWrapper` | function | `export function getFieldsForGetAbsolutePathWrapper(config: ConfigFile): t.Node[] {` — Get all fields that need to be wrapped with getAbsolutePath wrapper. | `[SRC:code/core/src/common/utils/wrap-getAbsolutePath-utils.ts:L114]` |
| `getFrameworkName` | function | `export async function getFrameworkName(options: Options) {` — Framework can be a string or an object. | `[SRC:code/core/src/common/utils/get-framework-name.ts:L9]` |
| `getInterpretedFile` | function | `export function getInterpretedFile(pathToFile: string) {` | `[SRC:code/core/src/common/utils/interpret-files.ts:L19]` |
| `getPackageDetails` | function | `export function getPackageDetails(pkg: string): [string, string?] {` — Extract package name and version from input | `[SRC:code/core/src/common/js-package-manager/JsPackageManager.ts:L45]` |
| `getPresets` | function | `export async function getPresets(presets: PresetConfig[], storybookOptions: InterPresetOptions): Promise<Presets> {` | `[SRC:code/core/src/common/presets.ts:L318]` |
| `getPrettier` | function | `export async function getPrettier(): Promise<Prettier> {` | `[SRC:code/core/src/common/utils/formatter.ts:L25]` |
| `getProjectRoot` | function | `export const getProjectRoot = () => {` | `[SRC:code/core/src/common/utils/paths.ts:L11]` |
| `getRefs` | function | `export async function getRefs(options: Options) {` | `[SRC:code/core/src/common/utils/get-storybook-refs.ts:L95]` |
| `getRendererName` | function | `export async function getRendererName(options: Options) {` — Render is set as a string on core. | `[SRC:code/core/src/common/utils/get-renderer-name.ts:L11]` |
| `getStorybookConfiguration` | function | `export function getStorybookConfiguration(storybookScript: string, shortName: string, longName: string) {` | `[SRC:code/core/src/common/utils/get-storybook-configuration.ts:L7]` |
| `getStoryTitle` | function | `export function getStoryTitle({ storyFilePath, configDir, stories, workingDir = process.cwd(), userTitle }: Omit<GetStoryIdOptions, 'exportedStoryName'>) {` | `[SRC:code/core/src/common/utils/get-story-id.ts:L49]` |
| `globToRegexp` | function | `export function globToRegexp(glob: string) {` | `[SRC:code/core/src/common/utils/glob-to-regexp.ts:L3]` |
| `groupBy` | function | `export const groupBy = <K extends PropertyKey, T>(items: T[], keySelector: (item: T, index: number) => K) => {` | `[SRC:code/core/src/common/utils/utils.ts:L2]` |
| `HandledError` | class | `export class HandledError extends Error {` | `[SRC:code/core/src/common/utils/HandledError.ts:L1]` |
| `importMetaResolve` | function | `export const importMetaResolve = (...args: Parameters<ImportMeta['resolve']>) => {` — This is just an alias for import.meta.resolve. | `[SRC:code/core/src/shared/utils/module.ts:L15]` |
| `importModule` | function | `export async function importModule(path: string, { skipCache = false }: { skipCache?: boolean } = {}) {` — Dynamically imports a module with TypeScript support, falling back to require if necessary. | `[SRC:code/core/src/shared/utils/module.ts:L65]` |
| `InstallationMetadata` | type | `export type InstallationMetadata = {` | `[SRC:code/core/src/common/js-package-manager/types.ts:L2]` |
| `interpolate` | function | `export const interpolate = (template: string, bindings: Record<string, string>) => {` — Return a string corresponding to template filled with bindings using following pattern: For each (key, value) of `bindings` replace, in template, `{{key}}` by escaped version of `value` | `[SRC:code/core/src/common/utils/interpolate.ts:L10]` |
| `InterPresetOptions` | type | `export type InterPresetOptions = Omit<CLIOptions & LoadOptions & BuilderOptions & { isCritical?: boolean; build?: StorybookConfigRaw['build'] }, 'frameworkPresets'>;` | `[SRC:code/core/src/common/presets.ts:L24]` |
| `invalidateProjectRootCache` | function | `export const invalidateProjectRootCache = () => {` | `[SRC:code/core/src/common/utils/paths.ts:L59]` |
| `invariant` | function | `export function invariant(condition: unknown, message?: string \| (() => string)): asserts condition {` | `[SRC:code/core/src/common/utils/utils.ts:L18]` |
| `isCI` | function | `export function isCI(): boolean \| undefined {` — Consistently determine if we are in a CI environment Doing Boolean(process.env.CI) or !process.env.CI is not enough, because users might set CI=false or CI=0, which would be truthy, and thus return tr | `[SRC:code/core/src/common/utils/envs.ts:L80]` |
| `isCorePackage` | function | `export const isCorePackage = (pkg: string) =>` | `[SRC:code/core/src/common/utils/cli.ts:L141]` |
| `isGetAbsolutePathWrapperNecessary` | function | `export function isGetAbsolutePathWrapperNecessary(node: t.Node, cb: (node: t.StringLiteral \| t.ObjectProperty \| t.ArrayExpression) => void = () => {}) {` — Check if the node needs to be wrapped with getAbsolutePath wrapper. | `[SRC:code/core/src/common/utils/wrap-getAbsolutePath-utils.ts:L76]` |
| `isPreservingSymlinks` | function | `export function isPreservingSymlinks() {` | `[SRC:code/core/src/common/utils/symlinks.ts:L1]` |
| `isSatelliteAddon` | function | `export const isSatelliteAddon = (pkg: string) => satelliteAddons.includes(pkg);` | `[SRC:code/core/src/common/utils/cli.ts:L143]` |
| `JsPackageManager` | class | `export abstract class JsPackageManager {` | `[SRC:code/core/src/common/js-package-manager/JsPackageManager.ts:L70]` |
| `JsPackageManagerFactory` | class | `export class JsPackageManagerFactory {` | `[SRC:code/core/src/common/js-package-manager/JsPackageManagerFactory.ts:L29]` |
| `loadAllPresets` | function | `export async function loadAllPresets(options: CLIOptions & LoadOptions & BuilderOptions & { corePresets: PresetConfig[]; overridePresets: PresetConfig[]; /** Whether preset failures should be critical or not */ isCritical?: boolean; build?: StorybookConfigRaw['build']; channel: ChannelLike; }) {` | `[SRC:code/core/src/common/presets.ts:L330]` |
| `loadEnvs` | function | `export async function loadEnvs(options: { production?: boolean } = {}): Promise<{` | `[SRC:code/core/src/common/utils/envs.ts:L9]` |
| `loadManagerOrAddonsFile` | function | `export function loadManagerOrAddonsFile({ configDir }: { configDir: string }) {` | `[SRC:code/core/src/common/utils/load-manager-or-addons-file.ts:L9]` |
| `loadPreset` | function | `export async function loadPreset(input: PresetConfig, level: number, storybookOptions: InterPresetOptions): Promise<LoadedPreset[]> {` | `[SRC:code/core/src/common/presets.ts:L156]` |
| `loadPreviewOrConfigFile` | function | `export function loadPreviewOrConfigFile({ configDir }: { configDir: string }) {` | `[SRC:code/core/src/common/utils/load-preview-or-config-file.ts:L7]` |
| `logConfig` | function | `export function logConfig(caption: unknown, config: unknown) {` | `[SRC:code/core/src/common/utils/log-config.ts:L3]` |
| `nodePathsToArray` | function | `export const nodePathsToArray = (nodePath: string) =>` | `[SRC:code/core/src/common/utils/paths.ts:L73]` |
| `normalizeStoriesEntry` | function | `export const normalizeStoriesEntry = (entry: StoriesEntry, { configDir, workingDir, defaultFilesPattern = DEFAULT_FILES_PATTERN }: NormalizeOptions): NormalizedStoriesSpecifier => {` | `[SRC:code/core/src/common/utils/normalize-stories.ts:L38]` |
| `normalizeStoryPath` | function | `export function normalizeStoryPath(filename: string) {` — Ensures that a path starts with `./` or `../`, or is entirely `.` or `..` | `[SRC:code/core/src/common/utils/paths.ts:L82]` |
| `optionalEnvToBoolean` | function | `export const optionalEnvToBoolean = (input: string \| undefined): boolean \| undefined => {` | `[SRC:code/core/src/common/utils/envs.ts:L61]` |
| `PackageJsonInfo` | type | `export type PackageJsonInfo = {` | `[SRC:code/core/src/common/js-package-manager/JsPackageManager.ts:L64]` |
| `PackageJsonWithDepsAndDevDeps` | type | `export type PackageJsonWithDepsAndDevDeps = PackageJson &` | `[SRC:code/core/src/common/js-package-manager/PackageJson.ts:L3]` |
| `PackageJsonWithMaybeDeps` | type | `export type PackageJsonWithMaybeDeps = Partial<Pick<PackageJson, 'dependencies' \| 'devDependencies' \| 'peerDependencies' \| 'files'>>;` | `[SRC:code/core/src/common/js-package-manager/PackageJson.ts:L6]` |
| `PackageManagerName` | enum | `export enum PackageManagerName {` | `[SRC:code/core/src/common/js-package-manager/JsPackageManager.ts:L23]` |
| `PackageMetadata` | type | `export type PackageMetadata = { version: string; location?: string; reasons?: string[] };` | `[SRC:code/core/src/common/js-package-manager/types.ts:L1]` |
| `parseList` | function | `export function parseList(str: string): string[] {` | `[SRC:code/core/src/common/utils/cli.ts:L62]` |
| `posix` | function | `export const posix = (localPath: string, seperator: string = sep) =>` — Replaces the path separator with forward slashes | `[SRC:code/core/src/common/utils/posix.ts:L4]` |
| `readTemplate` | function | `export async function readTemplate(filename: string) {` | `[SRC:code/core/src/common/utils/readTemplate.ts:L3]` |
| `removeAddon` | function | `export async function removeAddon(addon: string, options: RemoveAddonOptions) {` — Remove the given addon package and remove it from main.js | `[SRC:code/core/src/common/utils/remove.ts:L24]` |
| `RemoveAddonOptions` | type | `export type RemoveAddonOptions = {` | `[SRC:code/core/src/common/utils/remove.ts:L9]` |
| `rendererPackages` | const | `export const rendererPackages: Record<string, SupportedRenderer> = {` | `[SRC:code/core/src/common/utils/get-storybook-info.ts:L22]` |
| `resolveAddonName` | function | `export const resolveAddonName = (configDir: string, name: string, options: any): CoreCommon_ResolvedAddonPreset \| CoreCommon_ResolvedAddonVirtual \| undefined => {` | `[SRC:code/core/src/common/presets.ts:L68]` |
| `resolveImport` | function | `export function resolveImport(id: string, options: resolve.SyncOpts): string {` | `[SRC:code/core/src/common/utils/interpret-files.ts:L25]` |
| `resolvePackageDir` | function | `export const resolvePackageDir = (pkg: Parameters<ImportMeta['resolve']>[0], parent?: Parameters<ImportMeta['resolve']>[0]) => {` — Resolves the directory of a given package, by resolving its package.json file. | `[SRC:code/core/src/shared/utils/module.ts:L28]` |
| `resolvePathInStorybookCache` | function | `export function resolvePathInStorybookCache(fileOrDirectoryName: string, sub = 'default'): string {` — Get the path of the file or directory with input name inside the Storybook cache directory: - `node_modules/.cache/storybook/{version}/{directoryName}` in a Node.js project or npm package - `.cache/st | `[SRC:code/core/src/common/utils/resolve-path-in-sb-cache.ts:L20]` |
| `safeResolveModule` | function | `export const safeResolveModule = ({ specifier, parent, extensions = ['.mjs', '.js', '.cjs'] }: { specifier: string; parent?: string; extensions?: string[]; }) => {` — Safely resolves a module specifier to its absolute file path. | `[SRC:code/core/src/shared/utils/module.ts:L126]` |
| `satisfies` | function | `export function satisfies<A>() {` — Mimicking the satisfies operator until we can upgrade to TS4.9 | `[SRC:code/core/src/common/utils/satisfies.ts:L2]` |
| `scanAndTransformFiles` | function | `export async function scanAndTransformFiles<T extends Record<string, unknown>>({ promptMessage = 'Enter a custom glob pattern to scan (or press enter to use default):', defaultGlob = '**/*.{mjs,cjs,js,jsx,ts,tsx,mdx}', dryRun = false, force = false, transformFn, transformOptions }: { promptMessage?: string; defaultGlob?: string; dryRun: boolean; force?: boolean; transformFn: (files: string[], options: T, dryRun: boolean) => Promise<Array<{ file: string; error: Error }>>; transformOptions: T; }): Promise<Array<{ file: string; error: Error }>> {` — Helper function to scan for files matching a glob pattern and transform them | `[SRC:code/core/src/common/utils/scan-and-transform-files.ts:L13]` |
| `serverRequire` | function | `export function serverRequire(filePath: string \| string[]) {` | `[SRC:code/core/src/common/utils/interpret-require.ts:L17]` |
| `setupAddonInConfig` | function | `export async function setupAddonInConfig({ addonName, previewConfigPath, configDir, mainConfigCSFFile }: SetupAddonInConfigOptions): Promise<void> {` — Setup an addon in the Storybook configuration by adding it to the addons array in main config and syncing it with preview config. | `[SRC:code/core/src/common/utils/setup-addon-in-config.ts:L24]` |
| `SetupAddonInConfigOptions` | interface | `export interface SetupAddonInConfigOptions {` | `[SRC:code/core/src/common/utils/setup-addon-in-config.ts:L11]` |
| `stringifyEnvs` | function | `export const stringifyEnvs = (raw: Record<string, string>): Record<string, string> =>` | `[SRC:code/core/src/common/utils/envs.ts:L47]` |
| `stringifyProcessEnvs` | function | `export const stringifyProcessEnvs = (raw: Record<string, string>): Record<string, string> => {` | `[SRC:code/core/src/common/utils/envs.ts:L53]` |
| `syncPreviewAddonsWithMainConfig` | function | `export async function syncPreviewAddonsWithMainConfig(mainConfig: StorybookConfig, previewConfig: ConfigFile, configDir: string): Promise<ConfigFile> {` | `[SRC:code/core/src/common/utils/sync-main-preview-addons.ts:L31]` |
| `syncStorybookAddons` | function | `export async function syncStorybookAddons(mainConfig: StorybookConfig, previewConfigPath: string, configDir: string) {` | `[SRC:code/core/src/common/utils/sync-main-preview-addons.ts:L16]` |
| `temporaryDirectory` | function | `export async function temporaryDirectory({ prefix = '' } = {}) {` | `[SRC:code/core/src/common/utils/cli.ts:L18]` |
| `temporaryFile` | function | `export async function temporaryFile({ name, extension }: FileOptions = {}) {` | `[SRC:code/core/src/common/utils/cli.ts:L47]` |
| `transformImportFiles` | function | `export const transformImportFiles = async (files: string[], renamedImports: Record<string, string>, dryRun?: boolean) => {` | `[SRC:code/core/src/common/utils/transform-imports.ts:L19]` |
| `validateConfigurationFiles` | function | `export async function validateConfigurationFiles(configDir: string, cwd?: string) {` | `[SRC:code/core/src/common/utils/validate-configuration-files.ts:L14]` |
| `validateFrameworkName` | function | `export function validateFrameworkName(frameworkName: string \| undefined): asserts frameworkName is string {` | `[SRC:code/core/src/common/utils/validate-config.ts:L16]` |
| `versions` | const | `export default { '@storybook/addon-a11y': '10.3.5', … }` — `default` exported under this name | `[SRC:code/core/src/common/versions.ts:L2]` |
| `wrapValueWithGetAbsolutePathWrapper` | function | `export function wrapValueWithGetAbsolutePathWrapper(config: ConfigFile, node: t.Node) {` | `[SRC:code/core/src/common/utils/wrap-getAbsolutePath-utils.ts:L191]` |

## `storybook/internal/csf`

Entry: `code/core/src/csf/index.ts`.

| Export | Kind | Declaration | Source |
|---|---|---|---|
| `ActionsTypes` | interface | `export interface ActionsTypes {` | `[SRC:code/core/src/actions/types.ts:L51]` |
| `AddonTypes` | interface | `export interface AddonTypes {` — AddonTypes allows addons to extend the type system with additional args, parameters, and globals. | `[SRC:code/core/src/csf/story.ts:L187]` |
| `AfterEach` | type | `export type AfterEach<TRenderer extends Renderer = Renderer, TArgs = Args> = (context: StoryContext<TRenderer, TArgs>) => Awaitable<void>;` | `[SRC:code/core/src/csf/story.ts:L262]` |
| `AnnotatedStoryFn` | type | `export type AnnotatedStoryFn<TRenderer extends Renderer = Renderer, TArgs = Args> = ArgsStoryFn<TRenderer, TArgs> &` | `[SRC:code/core/src/csf/story.ts:L575]` |
| `AnyFramework` | type | `export type AnyFramework = Renderer;` | `[SRC:code/core/src/csf/story.ts:L217]` |
| `ArgsEnhancer` | type | `export type ArgsEnhancer<TRenderer extends Renderer = Renderer, TArgs = Args> = (context: StoryContextForEnhancers<TRenderer, TArgs>) => TArgs;` | `[SRC:code/core/src/csf/story.ts:L230]` |
| `ArgsFromMeta` | type | `export type ArgsFromMeta<TRenderer extends Renderer, Meta> = Meta extends {` | `[SRC:code/core/src/csf/story.ts:L585]` |
| `ArgsStoryFn` | type | `export type ArgsStoryFn<TRenderer extends Renderer = Renderer, TArgs = Args> = (args: TArgs, context: StoryContext<TRenderer, TArgs>) => (TRenderer & { T: TArgs })['storyResult'];` | `[SRC:code/core/src/csf/story.ts:L321]` |
| `ArgTypesEnhancer` | type | `export type ArgTypesEnhancer<TRenderer extends Renderer = Renderer, TArgs = Args> = ((context: StoryContextForEnhancers<TRenderer, TArgs>) => StrictArgTypes<TArgs>) & {` | `[SRC:code/core/src/csf/story.ts:L233]` |
| `BackgroundsGlobals` | interface | `export interface BackgroundsGlobals {` | `[SRC:code/core/src/backgrounds/types.ts:L47]` |
| `BackgroundTypes` | interface | `export interface BackgroundTypes {` | `[SRC:code/core/src/backgrounds/types.ts:L56]` |
| `BaseAnnotations` | interface | `export interface BaseAnnotations<TRenderer extends Renderer = Renderer, TArgs = Args> {` | `[SRC:code/core/src/csf/story.ts:L347]` |
| `BeforeAll` | type | `export type BeforeAll = () => Awaitable<CleanupCallback \| void>;` | `[SRC:code/core/src/csf/story.ts:L256]` |
| `BeforeEach` | type | `export type BeforeEach<TRenderer extends Renderer = Renderer, TArgs = Args> = (context: StoryContext<TRenderer, TArgs>) => Awaitable<CleanupCallback \| void>;` | `[SRC:code/core/src/csf/story.ts:L258]` |
| `CleanupCallback` | type | `export type CleanupCallback = () => Awaitable<unknown>;` | `[SRC:code/core/src/csf/story.ts:L254]` |
| `ComponentId` | type | `export type ComponentId = string;` | `[SRC:code/core/src/csf/story.ts:L9]` |
| `ComponentTitle` | type | `export type ComponentTitle = string;` | `[SRC:code/core/src/csf/story.ts:L10]` |
| `Conditional` | type | `export type Conditional = ConditionalValue & ConditionalTest;` | `[SRC:code/core/src/csf/story.ts:L58]` |
| `ControlsTypes` | interface | `export interface ControlsTypes {` | `[SRC:code/core/src/controls/types.ts:L55]` |
| `CoreTypes` | type | `export type CoreTypes = StorybookTypes &` | `[SRC:code/core/src/csf/core-annotations.ts:L23]` |
| `DecoratorApplicator` | type | `export type DecoratorApplicator<TRenderer extends Renderer = Renderer, TArgs = Args> = (storyFn: LegacyStoryFn<TRenderer, TArgs>, decorators: DecoratorFunction<TRenderer, TArgs>[]) => LegacyStoryFn<TRenderer, TArgs>;` | `[SRC:code/core/src/csf/story.ts:L336]` |
| `definePreviewAddon` | function | `export function definePreviewAddon<TExtraContext extends AddonTypes = AddonTypes>(preview: ProjectAnnotations<Renderer>): PreviewAddon<TExtraContext> {` | `[SRC:code/core/src/csf/csf-factories.ts:L78]` |
| `getCoreAnnotations` | function | `export function getCoreAnnotations() {` | `[SRC:code/core/src/csf/core-annotations.ts:L33]` |
| `getStoryChildren` | function | `export function getStoryChildren<TRenderer extends Renderer>(story: Story<TRenderer>): Story<TRenderer>[] {` | `[SRC:code/core/src/csf/csf-factories.ts:L278]` |
| `GlobalTypes` | interface | `export interface GlobalTypes {` | `[SRC:code/core/src/csf/story.ts:L168]` |
| `HighlightTypes` | interface | `export interface HighlightTypes {` | `[SRC:code/core/src/highlight/types.ts:L3]` |
| `includeConditionalArg` | function | `export const includeConditionalArg = (argType: InputType, args: Args, globals: Globals) => {` — Helper function to include/exclude an arg based on the value of other other args aka "conditional args" | `[SRC:code/core/src/csf/includeConditionalArg.ts:L31]` |
| `InferTypes` | type | `export type InferTypes<T extends PreviewAddon<never>[]> = T extends PreviewAddon<infer C>[]` | `[SRC:code/core/src/csf/csf-factories.ts:L41]` |
| `InputType` | interface | `export interface InputType {` | `[SRC:code/core/src/csf/story.ts:L111]` |
| `isMeta` | function | `export function isMeta(input: unknown): input is Meta<Renderer> {` | `[SRC:code/core/src/csf/csf-factories.ts:L115]` |
| `isPreview` | function | `export function isPreview(input: unknown): input is Preview<Renderer> {` | `[SRC:code/core/src/csf/csf-factories.ts:L84]` |
| `isStory` | function | `export function isStory<TRenderer extends Renderer>(input: unknown): input is Story<TRenderer> {` | `[SRC:code/core/src/csf/csf-factories.ts:L173]` |
| `LegacyAnnotatedStoryFn` | type | `export type LegacyAnnotatedStoryFn<TRenderer extends Renderer = Renderer, TArgs = Args> = StoryFn<TRenderer, TArgs> &` | `[SRC:code/core/src/csf/story.ts:L565]` |
| `LegacyStoryAnnotationsOrFn` | type | `export type LegacyStoryAnnotationsOrFn<TRenderer extends Renderer = Renderer, TArgs = Args> =` | `[SRC:code/core/src/csf/story.ts:L571]` |
| `LegacyStoryFn` | type | `export type LegacyStoryFn<TRenderer extends Renderer = Renderer, TArgs = Args> = (context: StoryContext<TRenderer, TArgs>) => TRenderer['storyResult'];` | `[SRC:code/core/src/csf/story.ts:L316]` |
| `MeasureTypes` | interface | `export interface MeasureTypes {` | `[SRC:code/core/src/measure/types.ts:L18]` |
| `OutlineTypes` | interface | `export interface OutlineTypes {` | `[SRC:code/core/src/outline/types.ts:L18]` |
| `PartialStoryFn` | type | `export type PartialStoryFn<TRenderer extends Renderer = Renderer, TArgs = Args> = (update?: StoryContextUpdate<Partial<TArgs>>) => TRenderer['storyResult'];` | `[SRC:code/core/src/csf/story.ts:L311]` |
| `PlayFunctionContext` | interface | `export interface PlayFunctionContext<TRenderer extends Renderer = Renderer, TArgs = Args> extends StoryContext<TRenderer, TArgs> {}` | `[SRC:code/core/src/csf/story.ts:L290]` |
| `PreviewAddon` | interface | `export interface PreviewAddon<in TExtraContext extends AddonTypes = AddonTypes> extends ProjectAnnotations<Renderer> {}` | `[SRC:code/core/src/csf/csf-factories.ts:L74]` |
| `Renderer` | interface | `export interface Renderer extends AddonTypes {` | `[SRC:code/core/src/csf/story.ts:L193]` |
| `SBArrayType` | type | `export type SBArrayType = SBBaseType & {` | `[SRC:code/core/src/csf/SBType.ts:L10]` |
| `SBEnumType` | type | `export type SBEnumType = SBBaseType & {` | `[SRC:code/core/src/csf/SBType.ts:L23]` |
| `SBIntersectionType` | type | `export type SBIntersectionType = SBBaseType & {` | `[SRC:code/core/src/csf/SBType.ts:L27]` |
| `SBLiteralType` | type | `export type SBLiteralType = SBBaseType & {` | `[SRC:code/core/src/csf/SBType.ts:L35]` |
| `SBNodeType` | type | `export type SBNodeType = SBBaseType & {` | `[SRC:code/core/src/csf/SBType.ts:L14]` |
| `SBObjectType` | type | `export type SBObjectType = SBBaseType & {` | `[SRC:code/core/src/csf/SBType.ts:L19]` |
| `SBOtherType` | type | `export type SBOtherType = SBBaseType & {` | `[SRC:code/core/src/csf/SBType.ts:L43]` |
| `SBScalarType` | type | `export type SBScalarType = SBBaseType & {` | `[SRC:code/core/src/csf/SBType.ts:L6]` |
| `SBTupleType` | type | `export type SBTupleType = SBBaseType & {` | `[SRC:code/core/src/csf/SBType.ts:L39]` |
| `SBType` | type | `export type SBType =` | `[SRC:code/core/src/csf/SBType.ts:L48]` |
| `SBUnionType` | type | `export type SBUnionType = SBBaseType & {` | `[SRC:code/core/src/csf/SBType.ts:L31]` |
| `StepFunction` | type | `export type StepFunction<TRenderer extends Renderer = Renderer, TArgs = Args> = (label: StepLabel, play: PlayFunction<TRenderer, TArgs>) => Promise<void> \| void;` | `[SRC:code/core/src/csf/story.ts:L297]` |
| `StepLabel` | type | `export type StepLabel = string;` | `[SRC:code/core/src/csf/story.ts:L295]` |
| `StepRunner` | type | `export type StepRunner<TRenderer extends Renderer = Renderer, TArgs = Args> = (label: StepLabel, play: PlayFunction<TRenderer, TArgs>, context: StoryContext<TRenderer, TArgs>) => Promise<void>;` | `[SRC:code/core/src/csf/story.ts:L341]` |
| `StoryAnnotationsOrFn` | type | `export type StoryAnnotationsOrFn<TRenderer extends Renderer = Renderer, TArgs = Args> =` | `[SRC:code/core/src/csf/story.ts:L581]` |
| `StoryContextForEnhancers` | interface | `export interface StoryContextForEnhancers<TRenderer extends Renderer = Renderer, TArgs = Args> extends StoryIdentifier {` | `[SRC:code/core/src/csf/story.ts:L219]` |
| `StoryContextForLoaders` | interface | `export interface StoryContextForLoaders<TRenderer extends Renderer = Renderer, TArgs = Args> extends StoryContext<TRenderer, TArgs> {}` | `[SRC:code/core/src/csf/story.ts:L284]` |
| `StoryContextUpdate` | interface | `export interface StoryContextUpdate<TArgs = Args> {` | `[SRC:code/core/src/csf/story.ts:L239]` |
| `StoryId` | type | `export type StoryId = string;` | `[SRC:code/core/src/csf/story.ts:L8]` |
| `StoryIdentifier` | interface | `export interface StoryIdentifier {` | `[SRC:code/core/src/csf/story.ts:L18]` |
| `StoryKind` | type | `export type StoryKind = ComponentTitle;` | `[SRC:code/core/src/csf/story.ts:L14]` |
| `StoryName` | type | `export type StoryName = string;` | `[SRC:code/core/src/csf/story.ts:L11]` |
| `StrictArgTypes` | type | `export type StrictArgTypes<TArgs = Args> = { [name in keyof TArgs]: StrictInputType };` | `[SRC:code/core/src/csf/story.ts:L163]` |
| `StrictInputType` | interface | `export interface StrictInputType extends InputType {` | `[SRC:code/core/src/csf/story.ts:L148]` |
| `StrictParameters` | interface | `export interface StrictParameters {` | `[SRC:code/core/src/csf/story.ts:L36]` |
| `TestFunction` | type | `export type TestFunction<TRenderer extends Renderer = Renderer, TArgs = TRenderer['args']> = (context: StoryContext<TRenderer, TArgs>) => Promise<void> \| void;` | `[SRC:code/core/src/csf/story.ts:L306]` |
| `TestTypes` | interface | `export interface TestTypes {` | `[SRC:code/core/src/test/preview.ts:L165]` |
| `ViewportGlobals` | interface | `export interface ViewportGlobals {` | `[SRC:code/core/src/viewport/types.ts:L56]` |
| `ViewportTypes` | interface | `export interface ViewportTypes {` | `[SRC:code/core/src/viewport/types.ts:L65]` |

## `storybook/internal/docs-tools`

Entry: `code/core/src/docs-tools/index.ts`.

| Export | Kind | Declaration | Source |
|---|---|---|---|
| `ArgTypesExtractor` | type | `export type ArgTypesExtractor = (component: Component) => StrictArgTypes \| null;` | `[SRC:code/core/src/docs-tools/argTypes/docgen/types.ts:L8]` |
| `convert` | function | `export const convert = (docgenInfo: DocgenInfo) => {` | `[SRC:code/core/src/docs-tools/argTypes/convert/index.ts:L8]` |
| `createSummaryValue` | function | `export function createSummaryValue(summary?: string, detail?: string): PropSummaryValue {` | `[SRC:code/core/src/docs-tools/argTypes/utils.ts:L14]` |
| `DocgenFlowType` | interface | `export interface DocgenFlowType extends DocgenType {` | `[SRC:code/core/src/docs-tools/argTypes/docgen/types.ts:L23]` |
| `DocgenInfo` | interface | `export interface DocgenInfo {` | `[SRC:code/core/src/docs-tools/argTypes/docgen/types.ts:L42]` |
| `DocgenPropDefaultValue` | interface | `export interface DocgenPropDefaultValue {` | `[SRC:code/core/src/docs-tools/argTypes/docgen/types.ts:L36]` |
| `DocgenPropType` | interface | `export interface DocgenPropType extends DocgenType {` | `[SRC:code/core/src/docs-tools/argTypes/docgen/types.ts:L17]` |
| `DocgenType` | interface | `export interface DocgenType {` | `[SRC:code/core/src/docs-tools/argTypes/docgen/types.ts:L10]` |
| `DocgenTypeScriptType` | interface | `export interface DocgenTypeScriptType extends DocgenType {` | `[SRC:code/core/src/docs-tools/argTypes/docgen/types.ts:L30]` |
| `enhanceArgTypes` | function | `export const enhanceArgTypes = <TRenderer extends Renderer>(context: StoryContextForEnhancers<TRenderer>) => {` | `[SRC:code/core/src/docs-tools/argTypes/enhanceArgTypes.ts:L5]` |
| `extractComponentDescription` | function | `export function extractComponentDescription(component?: Component): string {` | `[SRC:code/core/src/docs-tools/argTypes/docgen/extractDocgenProps.ts:L106]` |
| `extractComponentProps` | function | `export const extractComponentProps: ExtractProps = (component, section) => {` | `[SRC:code/core/src/docs-tools/argTypes/docgen/extractDocgenProps.ts:L70]` |
| `extractComponentSectionArray` | function | `export const extractComponentSectionArray = (docgenSection: any) => {` | `[SRC:code/core/src/docs-tools/argTypes/docgen/extractDocgenProps.ts:L35]` |
| `extractComponentSectionObject` | function | `export const extractComponentSectionObject = (docgenSection: any) => {` | `[SRC:code/core/src/docs-tools/argTypes/docgen/extractDocgenProps.ts:L54]` |
| `ExtractedJsDoc` | interface | `export interface ExtractedJsDoc {` | `[SRC:code/core/src/docs-tools/argTypes/jsdocParser.ts:L23]` |
| `ExtractedJsDocParam` | interface | `export interface ExtractedJsDocParam extends JsDocParam {` | `[SRC:code/core/src/docs-tools/argTypes/jsdocParser.ts:L12]` |
| `ExtractedJsDocReturns` | interface | `export interface ExtractedJsDocReturns extends JsDocReturns {` | `[SRC:code/core/src/docs-tools/argTypes/jsdocParser.ts:L18]` |
| `ExtractedProp` | interface | `export interface ExtractedProp {` | `[SRC:code/core/src/docs-tools/argTypes/docgen/extractDocgenProps.ts:L10]` |
| `ExtractProps` | type | `export type ExtractProps = (component: Component, section: string) => ExtractedProp[];` | `[SRC:code/core/src/docs-tools/argTypes/docgen/extractDocgenProps.ts:L17]` |
| `getDocgenDescription` | function | `export function getDocgenDescription(component: Component): string {` | `[SRC:code/core/src/docs-tools/argTypes/docgen/utils/docgenInfo.ts:L18]` |
| `getDocgenSection` | function | `export function getDocgenSection(component: Component, section: string): any {` | `[SRC:code/core/src/docs-tools/argTypes/docgen/utils/docgenInfo.ts:L14]` |
| `hasDocgen` | function | `export function hasDocgen<T = any>(component: Component): component is object & { __docgenInfo: T } {` | `[SRC:code/core/src/docs-tools/argTypes/docgen/utils/docgenInfo.ts:L4]` |
| `isDefaultValueBlacklisted` | function | `export function isDefaultValueBlacklisted(value: string): boolean {` | `[SRC:code/core/src/docs-tools/argTypes/docgen/utils/defaultValue.ts:L3]` |
| `isTooLongForDefaultValueSummary` | function | `export function isTooLongForDefaultValueSummary(value: string): boolean {` | `[SRC:code/core/src/docs-tools/argTypes/utils.ts:L10]` |
| `isTooLongForTypeSummary` | function | `export function isTooLongForTypeSummary(value: string): boolean {` | `[SRC:code/core/src/docs-tools/argTypes/utils.ts:L6]` |
| `isValidDocgenSection` | function | `export function isValidDocgenSection(docgenSection: any) {` | `[SRC:code/core/src/docs-tools/argTypes/docgen/utils/docgenInfo.ts:L10]` |
| `JsDocParam` | interface | `export interface JsDocParam {` | `[SRC:code/core/src/docs-tools/argTypes/docgen/PropDef.ts:L3]` |
| `JsDocParsingOptions` | interface | `export interface JsDocParsingOptions {` | `[SRC:code/core/src/docs-tools/argTypes/jsdocParser.ts:L30]` |
| `JsDocParsingResult` | interface | `export interface JsDocParsingResult {` | `[SRC:code/core/src/docs-tools/argTypes/jsdocParser.ts:L34]` |
| `JsDocReturns` | interface | `export interface JsDocReturns {` | `[SRC:code/core/src/docs-tools/argTypes/docgen/PropDef.ts:L8]` |
| `JsDocTags` | interface | `export interface JsDocTags {` | `[SRC:code/core/src/docs-tools/argTypes/docgen/PropDef.ts:L12]` |
| `MAX_DEFAULT_VALUE_SUMMARY_LENGTH` | const | `export const MAX_DEFAULT_VALUE_SUMMARY_LENGTH = 50;` | `[SRC:code/core/src/docs-tools/argTypes/utils.ts:L4]` |
| `MAX_TYPE_SUMMARY_LENGTH` | const | `export const MAX_TYPE_SUMMARY_LENGTH = 90;` | `[SRC:code/core/src/docs-tools/argTypes/utils.ts:L3]` |
| `normalizeNewlines` | function | `export const normalizeNewlines = (string: string) => string.replace(/\\r\\n/g, '\\n');` | `[SRC:code/core/src/docs-tools/argTypes/utils.ts:L21]` |
| `ParseJsDoc` | type | `export type ParseJsDoc = (value: string \| null, options?: JsDocParsingOptions) => JsDocParsingResult;` | `[SRC:code/core/src/docs-tools/argTypes/jsdocParser.ts:L41]` |
| `parseJsDoc` | function | `export const parseJsDoc: ParseJsDoc = (value, options = DEFAULT_OPTIONS) => {` | `[SRC:code/core/src/docs-tools/argTypes/jsdocParser.ts:L75]` |
| `PropDef` | interface | `export interface PropDef {` | `[SRC:code/core/src/docs-tools/argTypes/docgen/PropDef.ts:L25]` |
| `PropDefaultValue` | type | `export type PropDefaultValue = PropSummaryValue;` | `[SRC:code/core/src/docs-tools/argTypes/docgen/PropDef.ts:L23]` |
| `PropsExtractor` | type | `export type PropsExtractor = (component: Component) => { rows?: PropDef[] } \| null;` | `[SRC:code/core/src/docs-tools/argTypes/docgen/types.ts:L6]` |
| `PropSummaryValue` | interface | `export interface PropSummaryValue {` | `[SRC:code/core/src/docs-tools/argTypes/docgen/PropDef.ts:L17]` |
| `PropType` | type | `export type PropType = PropSummaryValue;` | `[SRC:code/core/src/docs-tools/argTypes/docgen/PropDef.ts:L22]` |
| `SNIPPET_RENDERED` | const | `` export const SNIPPET_RENDERED = `${ADDON_ID}/snippet-rendered`; `` | `[SRC:code/core/src/docs-tools/shared.ts:L5]` |
| `SourceType` | enum | `export enum SourceType {` | `[SRC:code/core/src/docs-tools/shared.ts:L7]` |
| `str` | function | `export const str = (obj: any) => {` | `[SRC:code/core/src/docs-tools/argTypes/docgen/utils/string.ts:L1]` |
| `TypeSystem` | enum | `export enum TypeSystem {` | `[SRC:code/core/src/docs-tools/argTypes/docgen/types.ts:L51]` |

## `storybook/internal/server-errors`

Entry: `code/core/src/server-errors.ts`.

| Export | Kind | Declaration | Source |
|---|---|---|---|
| `AddonVitestPostinstallConfigUpdateError` | class | `export class AddonVitestPostinstallConfigUpdateError extends StorybookError {` | `[SRC:code/core/src/server-errors.ts:L501]` |
| `AddonVitestPostinstallError` | class | `export class AddonVitestPostinstallError extends StorybookError {` | `[SRC:code/core/src/server-errors.ts:L517]` |
| `AddonVitestPostinstallFailedAddonA11yError` | class | `export class AddonVitestPostinstallFailedAddonA11yError extends StorybookError {` | `[SRC:code/core/src/server-errors.ts:L473]` |
| `AddonVitestPostinstallPrerequisiteCheckError` | class | `export class AddonVitestPostinstallPrerequisiteCheckError extends StorybookError {` | `[SRC:code/core/src/server-errors.ts:L460]` |
| `AddonVitestPostinstallWorkspaceUpdateError` | class | `export class AddonVitestPostinstallWorkspaceUpdateError extends StorybookError {` | `[SRC:code/core/src/server-errors.ts:L485]` |
| `AngularLegacyBuildOptionsError` | class | `export class AngularLegacyBuildOptionsError extends StorybookError {` | `[SRC:code/core/src/server-errors.ts:L241]` |
| `AutomigrateError` | class | `export class AutomigrateError extends StorybookError {` | `[SRC:code/core/src/server-errors.ts:L656]` |
| `CommonJsConfigNotSupportedError` | class | `export class CommonJsConfigNotSupportedError extends StorybookError {` | `[SRC:code/core/src/server-errors.ts:L639]` |
| `ConflictingStaticDirConfigError` | class | `export class ConflictingStaticDirConfigError extends StorybookError {` | `[SRC:code/core/src/server-errors.ts:L120]` |
| `CouldNotEvaluateFrameworkError` | class | `export class CouldNotEvaluateFrameworkError extends StorybookError {` | `[SRC:code/core/src/server-errors.ts:L103]` |
| `CriticalPresetLoadError` | class | `export class CriticalPresetLoadError extends StorybookError {` | `[SRC:code/core/src/server-errors.ts:L260]` |
| `FindPackageVersionsError` | class | `export class FindPackageVersionsError extends StorybookError {` | `[SRC:code/core/src/server-errors.ts:L580]` |
| `GenerateNewProjectOnInitError` | class | `export class GenerateNewProjectOnInitError extends StorybookError {` | `[SRC:code/core/src/server-errors.ts:L441]` |
| `GoogleFontsDownloadError` | class | `export class GoogleFontsDownloadError extends StorybookError {` | `[SRC:code/core/src/server-errors.ts:L305]` |
| `GoogleFontsLoadingError` | class | `export class GoogleFontsLoadingError extends StorybookError {` | `[SRC:code/core/src/server-errors.ts:L319]` |
| `IncompatiblePostCssConfigError` | class | `export class IncompatiblePostCssConfigError extends StorybookError {` | `[SRC:code/core/src/server-errors.ts:L595]` |
| `InvalidStoriesEntryError` | class | `export class InvalidStoriesEntryError extends StorybookError {` | `[SRC:code/core/src/server-errors.ts:L138]` |
| `MainFileEvaluationError` | class | `export class MainFileEvaluationError extends StorybookError {` | `[SRC:code/core/src/server-errors.ts:L402]` |
| `MainFileMissingError` | class | `export class MainFileMissingError extends StorybookError {` | `[SRC:code/core/src/server-errors.ts:L372]` |
| `MissingAngularJsonError` | class | `export class MissingAngularJsonError extends StorybookError {` | `[SRC:code/core/src/server-errors.ts:L223]` |
| `MissingBuilderError` | class | `export class MissingBuilderError extends StorybookError {` | `[SRC:code/core/src/server-errors.ts:L284]` |
| `NoMatchingExportError` | class | `export class NoMatchingExportError extends StorybookError {` | `[SRC:code/core/src/server-errors.ts:L350]` |
| `NoStatsForViteDevError` | class | `export class NoStatsForViteDevError extends StorybookError {` | `[SRC:code/core/src/server-errors.ts:L566]` |
| `SavingGlobalSettingsFileError` | class | `export class SavingGlobalSettingsFileError extends StorybookError {` | `[SRC:code/core/src/server-errors.ts:L626]` |
| `SvelteViteWithSvelteKitError` | class | `export class SvelteViteWithSvelteKitError extends StorybookError {` | `[SRC:code/core/src/server-errors.ts:L335]` |
| `UpgradeStorybookToLowerVersionError` | class | `export class UpgradeStorybookToLowerVersionError extends StorybookError {` | `[SRC:code/core/src/server-errors.ts:L530]` |
| `UpgradeStorybookUnknownCurrentVersionError` | class | `export class UpgradeStorybookUnknownCurrentVersionError extends StorybookError {` | `[SRC:code/core/src/server-errors.ts:L551]` |
| `WebpackCompilationError` | class | `export class WebpackCompilationError extends StorybookError {` | `[SRC:code/core/src/server-errors.ts:L191]` |
| `WebpackInvocationError` | class | `export class WebpackInvocationError extends StorybookError {` | `[SRC:code/core/src/server-errors.ts:L172]` |
| `WebpackMissingStatsError` | class | `export class WebpackMissingStatsError extends StorybookError {` | `[SRC:code/core/src/server-errors.ts:L155]` |

## `storybook/manager-api`

Entry: `code/core/src/manager-api/index.ts`.

| Export | Kind | Declaration | Source |
|---|---|---|---|
| `ActiveTabs` | const | `export { ActiveTabs };` | `[SRC:code/core/src/manager-api/root.tsx:L78]` |
| `AddonStore` | class | `export class AddonStore {` | `[SRC:code/core/src/manager-api/lib/addons.ts:L31]` |
| `API` | type | `export type API = addons.SubAPI &` | `[SRC:code/core/src/manager-api/root.tsx:L96]` |
| `Consumer` | function | `export { ManagerConsumer as Consumer, ManagerProvider as Provider };` — `ManagerConsumer` exported under this name | `[SRC:code/core/src/manager-api/root.tsx:L316]` |
| `controlOrMetaKey` | function | `export const controlOrMetaKey = () => (isMacLike() ? 'meta' : 'control');` | `[SRC:code/core/src/manager-api/lib/shortcut.ts:L7]` |
| `controlOrMetaSymbol` | function | `export const controlOrMetaSymbol = () => (isMacLike() ? '⌘' : 'ctrl');` | `[SRC:code/core/src/manager-api/lib/shortcut.ts:L6]` |
| `eventMatchesShortcut` | function | `export const eventMatchesShortcut = (e: KeyboardEventLike, shortcut: API_KeyCollection): boolean => {` | `[SRC:code/core/src/manager-api/lib/shortcut.ts:L124]` |
| `eventToShortcut` | function | `export const eventToShortcut = (e: KeyboardEventLike): (string \| string[])[] \| null => {` | `[SRC:code/core/src/manager-api/lib/shortcut.ts:L21]` |
| `experimental_requestResponse` | function | `export const experimental_requestResponse = <RequestPayload, ResponsePayload = void, CreateNewStoryErrorPayload extends Record<string, any> \| void = void>(channel: Channel, requestEvent: string, responseEvent: string, payload: RequestPayload, timeout = 5000): Promise<ResponsePayload> => {` | `[SRC:code/core/src/manager-api/lib/request-response.ts:L13]` |
| `internal_checklistStore` | const | `export const checklistStore = createChecklistStore(universalChecklistStore);` — `checklistStore` exported under this name | `[SRC:code/core/src/manager-api/stores/checklist.ts:L14]` |
| `internal_universalChecklistStore` | const | `export const universalChecklistStore = UniversalStore.create<StoreState, StoreEvent>({ ...UNIVERSAL_CHECKLIST_STORE_OPTIONS, leader: globalThis.CONFIG_TYPE === 'PRODUCTION' });` — `universalChecklistStore` exported under this name | `[SRC:code/core/src/manager-api/stores/checklist.ts:L9]` |
| `isMacLike` | function | `export const isMacLike = () =>` | `[SRC:code/core/src/manager-api/lib/platform.ts:L5]` |
| `isShortcutTaken` | function | `export const isShortcutTaken = (arr1: string[], arr2: string[]): boolean =>` | `[SRC:code/core/src/manager-api/lib/shortcut.ts:L10]` |
| `KeyboardEventLike` | type | `export type KeyboardEventLike = Pick<KeyboardEvent, 'altKey' \| 'ctrlKey' \| 'metaKey' \| 'shiftKey' \| 'key' \| 'code' \| 'keyCode' \| 'preventDefault'>;` | `[SRC:code/core/src/manager-api/lib/shortcut.ts:L14]` |
| `keyToSymbol` | function | `export const keyToSymbol = (key: string): string => {` — Returns a human-readable symbol for a keyboard key. | `[SRC:code/core/src/manager-api/lib/shortcut.ts:L137]` |
| `merge` | function | `export default <TObj = any>(a: TObj, ...b: Partial<TObj>[]): TObj =>` — `default` exported under this name | `[SRC:code/core/src/manager-api/lib/merge.ts:L6]` |
| `optionOrAltSymbol` | function | `export const optionOrAltSymbol = () => (isMacLike() ? '⌥' : 'alt');` | `[SRC:code/core/src/manager-api/lib/shortcut.ts:L8]` |
| `Provider` | class | `export { ManagerConsumer as Consumer, ManagerProvider as Provider };` — `ManagerProvider` exported under this name | `[SRC:code/core/src/manager-api/root.tsx:L316]` |
| `RequestResponseError` | class | `export class RequestResponseError<Payload extends Record<string, any> \| void> extends Error {` | `[SRC:code/core/src/manager-api/lib/request-response.ts:L4]` |
| `shortcutMatchesShortcut` | function | `export const shortcutMatchesShortcut = (inputShortcut: (string \| string[])[], shortcut: API_KeyCollection): boolean => {` | `[SRC:code/core/src/manager-api/lib/shortcut.ts:L102]` |
| `shortcutToAriaKeyshortcuts` | function | `export const shortcutToAriaKeyshortcuts = (shortcut: API_KeyCollection): string => {` | `[SRC:code/core/src/manager-api/lib/shortcut.ts:L180]` |
| `shortcutToHumanString` | function | `export const shortcutToHumanString = (shortcut: API_KeyCollection): string => {` | `[SRC:code/core/src/manager-api/lib/shortcut.ts:L175]` |
| `useAddonState` | function | `export function useAddonState<S>(addonId: string, defaultState?: S) {` | `[SRC:code/core/src/manager-api/root.tsx:L458]` |
| `useArgTypes` | function | `export function useArgTypes(): ArgTypes {` | `[SRC:code/core/src/manager-api/root.tsx:L501]` |
| `useGlobalTypes` | function | `export function useGlobalTypes(): GlobalTypes {` | `[SRC:code/core/src/manager-api/root.tsx:L491]` |
| `useSharedState` | function | `export function useSharedState<S>(stateId: string, defaultState?: S) {` | `[SRC:code/core/src/manager-api/root.tsx:L371]` |
| `useStorybookApi` | function | `export function useStorybookApi(): API {` | `[SRC:code/core/src/manager-api/root.tsx:L297]` |
| `useStorybookState` | function | `export function useStorybookState(): State {` | `[SRC:code/core/src/manager-api/root.tsx:L293]` |
| `useStoryPrepared` | function | `export function useStoryPrepared(storyId?: StoryId) {` | `[SRC:code/core/src/manager-api/root.tsx:L341]` |

## `storybook/internal/cli`

Entry: `code/core/src/cli/index.ts`.

| Export | Kind | Declaration | Source |
|---|---|---|---|
| `AddonVitestCompatibilityOptions` | interface | `export interface AddonVitestCompatibilityOptions {` | `[SRC:code/core/src/cli/AddonVitestService.ts:L23]` |
| `AddonVitestService` | class | `export class AddonVitestService {` — Centralized service for | `[SRC:code/core/src/cli/AddonVitestService.ts:L39]` |
| `addToDevDependenciesIfNotPresent` | function | `export function addToDevDependenciesIfNotPresent(packageJson: PackageJson, name: string, packageVersion: string) {` | `[SRC:code/core/src/cli/helpers.ts:L106]` |
| `adjustTemplate` | function | `export async function adjustTemplate(templatePath: string, templateData: Record<string, any>) {` | `[SRC:code/core/src/cli/helpers.ts:L230]` |
| `ANGULAR_JSON_PATH` | const | `export const ANGULAR_JSON_PATH = 'angular.json';` | `[SRC:code/core/src/cli/angular/helpers.ts:L7]` |
| `AngularJSON` | class | `export class AngularJSON {` | `[SRC:code/core/src/cli/angular/helpers.ts:L9]` |
| `cliStoriesTargetPath` | function | `export const cliStoriesTargetPath = async () => {` | `[SRC:code/core/src/cli/helpers.ts:L161]` |
| `coerceSemver` | function | `export function coerceSemver(version: string) {` | `[SRC:code/core/src/cli/helpers.ts:L242]` |
| `configureEslintPlugin` | function | `export async function configureEslintPlugin({ eslintConfigFile, packageManager, isFlatConfig }: { eslintConfigFile: string \| undefined; packageManager: JsPackageManager; isFlatConfig: boolean; }) {` | `[SRC:code/core/src/cli/eslintPlugin.ts:L265]` |
| `configureFlatConfig` | function | `export const configureFlatConfig = async (code: string) => {` | `[SRC:code/core/src/cli/eslintPlugin.ts:L55]` |
| `copyTemplate` | function | `export function copyTemplate(templateRoot: string, destination = '.') {` | `[SRC:code/core/src/cli/helpers.ts:L122]` |
| `copyTemplateFiles` | function | `export async function copyTemplateFiles({ packageManager, templateLocation, language, destination, commonAssetsDir, features }: CopyTemplateFilesOptions) {` | `[SRC:code/core/src/cli/helpers.ts:L168]` |
| `detectPnp` | function | `export async function detectPnp() {` | `[SRC:code/core/src/cli/detect.ts:L4]` |
| `extractEslintInfo` | function | `export async function extractEslintInfo(packageManager: JsPackageManager): Promise<{` | `[SRC:code/core/src/cli/eslintPlugin.ts:L217]` |
| `findEslintFile` | function | `export const findEslintFile = (instanceDir: string) => {` | `[SRC:code/core/src/cli/eslintPlugin.ts:L18]` |
| `getBabelDependencies` | function | `export async function getBabelDependencies(packageManager: JsPackageManager) {` — Detect if any babel dependencies need to be added to the project This is currently used by react-native generator | `[SRC:code/core/src/cli/helpers.ts:L73]` |
| `getRendererDir` | function | `export async function getRendererDir(packageManager: JsPackageManager, renderer: SupportedFramework \| SupportedRenderer) {` | `[SRC:code/core/src/cli/dirs.ts:L53]` |
| `getVersionSafe` | function | `export async function getVersionSafe(packageManager: JsPackageManager, packageName: string) {` — Return the installed version of a package, or the coerced version specifier from package.json if it's a dependency but not installed (e.g. | `[SRC:code/core/src/cli/helpers.ts:L145]` |
| `globalSettings` | function | `export async function globalSettings(filePath = DEFAULT_SETTINGS_PATH) {` | `[SRC:code/core/src/cli/globalSettings.ts:L61]` |
| `hasStorybookDependencies` | function | `export function hasStorybookDependencies(packageManager: JsPackageManager) {` | `[SRC:code/core/src/cli/helpers.ts:L248]` |
| `normalizeExtends` | function | `export const normalizeExtends = (existingExtends: any): string[] => {` | `[SRC:code/core/src/cli/eslintPlugin.ts:L250]` |
| `NpmOptions` | type | `export type NpmOptions = Parameters<JsPackageManager['addDependencies']>[0];` | `[SRC:code/core/src/cli/NpmOptions.ts:L3]` |
| `ProjectType` | enum | `export enum ProjectType {` | `[SRC:code/core/src/cli/projectTypes.ts:L1]` |
| `readFileAsJson` | function | `export function readFileAsJson(jsonPath: string, allowComments?: boolean) {` | `[SRC:code/core/src/cli/helpers.ts:L25]` |
| `Settings` | class | `export class Settings {` — A class for reading and writing settings from a JSON file. | `[SRC:code/core/src/cli/globalSettings.ts:L91]` |
| `suggestESLintPlugin` | function | `export const suggestESLintPlugin = async (): Promise<boolean> => {` | `[SRC:code/core/src/cli/eslintPlugin.ts:L331]` |
| `SUPPORTED_ESLINT_EXTENSIONS` | const | `export const SUPPORTED_ESLINT_EXTENSIONS = ['ts', 'mts', 'cts', 'mjs', 'js', 'cjs', 'json'];` | `[SRC:code/core/src/cli/eslintPlugin.ts:L15]` |
| `writeFileAsJson` | function | `export const writeFileAsJson = (jsonPath: string, content: unknown) => {` | `[SRC:code/core/src/cli/helpers.ts:L42]` |

## `storybook/internal/mocking-utils`

Entry: `code/core/src/mocking-utils/index.ts`.

| Export | Kind | Declaration | Source |
|---|---|---|---|
| `automockModule` | function | `export function automockModule(code: string, mockType: 'automock' \| 'autospy', parse: (code: string) => any, options: any = {}): MagicString {` — Copyright (c) Vitest https://github.com/vitest-dev/vitest/blob/v3.2.4/packages/mocker/src/node/automockPlugin.ts#L36C17-L36C31 MIT License Copyright (c) 2021-Present Vitest Team Permission is hereby g | `[SRC:code/core/src/mocking-utils/automock.ts:L47]` |
| `babelParser` | function | `export const babelParser = (code: string) => {` — A wrapper around the babel parser that enables the necessary plugins to handle modern JavaScript features, including TSX. | `[SRC:code/core/src/mocking-utils/extract.ts:L44]` |
| `extractMockCalls` | function | `export function extractMockCalls(options: ExtractMockCallsOptions, parse: (input: string, options?: { allowReturnOutsideFunction?: boolean; jsx?: boolean; }) => t.Node, root: string, findMockRedirect: (root: string, absolutePath: string, externalPath: string \| null) => string \| null): MockCall[] {` — Extracts all sb.mock() calls from the preview config file. | `[SRC:code/core/src/mocking-utils/extract.ts:L85]` |
| `getArbitraryModuleIdentifier` | function | `export function getArbitraryModuleIdentifier(node: Identifier \| Literal): string {` | `[SRC:code/core/src/mocking-utils/esmWalker.ts:L341]` |
| `getAutomockCode` | function | `export function getAutomockCode(originalCode: string, isSpy: boolean, parse: ParseFn) {` | `[SRC:code/core/src/mocking-utils/automock.ts:L17]` |
| `getIsExternal` | function | `export function getIsExternal(path: string, importer: string) {` | `[SRC:code/core/src/mocking-utils/resolve.ts:L58]` |
| `getMockerRuntime` | function | `export function getMockerRuntime(): string {` — Returns the bundled mocker runtime script content. | `[SRC:code/core/src/mocking-utils/runtime.ts:L8]` |
| `getRealPath` | function | `export function getRealPath(path: string, preserveSymlinks: boolean): string {` — Normalizes a file path for comparison, resolving symlinks if possible. | `[SRC:code/core/src/mocking-utils/resolve.ts:L124]` |
| `isExternal` | function | `export function isExternal(path: string, from: string) {` — External mean not absolute, and not relative We use `require.resolve` here, because import.meta.resolve needs a experimental node flag (`--experimental-import-meta-resolve`) to be enabled to respect t | `[SRC:code/core/src/mocking-utils/resolve.ts:L112]` |
| `isFunctionNode` | function | `export function isFunctionNode(node: _Node): node is FunctionNode {` | `[SRC:code/core/src/mocking-utils/esmWalker.ts:L320]` |
| `isInDestructuringAssignment` | function | `export function isInDestructuringAssignment(parent: _Node, parentStack: _Node[]): boolean {` | `[SRC:code/core/src/mocking-utils/esmWalker.ts:L333]` |
| `isModuleDirectory` | function | `export function isModuleDirectory(path: string) {` | `[SRC:code/core/src/mocking-utils/extract.ts:L16]` |
| `isNodeInPattern` | function | `export function isNodeInPattern(node: _Node): node is Property {` | `[SRC:code/core/src/mocking-utils/esmWalker.ts:L66]` |
| `isStaticProperty` | function | `export function isStaticProperty(node: _Node): node is Property {` | `[SRC:code/core/src/mocking-utils/esmWalker.ts:L311]` |
| `isStaticPropertyKey` | function | `export function isStaticPropertyKey(node: _Node, parent: _Node): boolean {` | `[SRC:code/core/src/mocking-utils/esmWalker.ts:L315]` |
| `MockCall` | type | `export type MockCall = {` | `[SRC:code/core/src/mocking-utils/extract.ts:L21]` |
| `Node` | type | `export type Node = Positioned<_Node>;` | `[SRC:code/core/src/mocking-utils/esmWalker.ts:L44]` |
| `Positioned` | type | `export type Positioned<T> = T & {` | `[SRC:code/core/src/mocking-utils/esmWalker.ts:L39]` |
| `resolveExternalModule` | function | `export function resolveExternalModule(path: string, root: string) {` — Resolves an external module path to its absolute path. | `[SRC:code/core/src/mocking-utils/resolve.ts:L34]` |
| `resolveMock` | function | `export function resolveMock(path: string, root: string, importer: string, findMockRedirect: (root: string, absolutePath: string, externalPath: string \| null) => string \| null) {` — Resolves a mock path to its absolute path and checks for a `__mocks__` redirect. | `[SRC:code/core/src/mocking-utils/resolve.ts:L74]` |
| `resolveWithExtensions` | function | `export function resolveWithExtensions(path: string, from: string) {` — This is a wrapper around `require.resolve` that tries to resolve the path with different file extensions. | `[SRC:code/core/src/mocking-utils/resolve.ts:L140]` |
| `rewriteSbMockImportCalls` | function | `export function rewriteSbMockImportCalls(code: string) {` — Utility to rewrite sb.mock(import('...'), ...) to sb.mock('...', ...) | `[SRC:code/core/src/mocking-utils/extract.ts:L54]` |
| `setIsNodeInPattern` | function | `export function setIsNodeInPattern(node: Property): WeakSet<_Node> {` | `[SRC:code/core/src/mocking-utils/esmWalker.ts:L63]` |

## `storybook/internal/core-events`

Entry: `code/core/src/core-events/index.ts`.

| Export | Kind | Declaration | Source |
|---|---|---|---|
| `ArgTypesRequestPayload` | interface | `export interface ArgTypesRequestPayload {` | `[SRC:code/core/src/core-events/data/argtypes-info.ts:L3]` |
| `ArgTypesResponsePayload` | interface | `export interface ArgTypesResponsePayload {` | `[SRC:code/core/src/core-events/data/argtypes-info.ts:L7]` |
| `CreateNewStoryErrorPayload` | type | `export type CreateNewStoryErrorPayload = {` | `[SRC:code/core/src/core-events/data/create-new-story.ts:L21]` |
| `CreateNewStoryRequestPayload` | interface | `export interface CreateNewStoryRequestPayload {` | `[SRC:code/core/src/core-events/data/create-new-story.ts:L1]` |
| `CreateNewStoryResponsePayload` | interface | `export interface CreateNewStoryResponsePayload {` | `[SRC:code/core/src/core-events/data/create-new-story.ts:L12]` |
| `FileComponentSearchRequestPayload` | interface | `export interface FileComponentSearchRequestPayload {}` | `[SRC:code/core/src/core-events/data/file-component-search.ts:L1]` |
| `FileComponentSearchResponsePayload` | interface | `export interface FileComponentSearchResponsePayload {` | `[SRC:code/core/src/core-events/data/file-component-search.ts:L3]` |
| `OpenInEditorRequestPayload` | type | `export type OpenInEditorRequestPayload = { file: string; line?: number; column?: number };` | `[SRC:code/core/src/core-events/data/open-in-editor.ts:L1]` |
| `OpenInEditorResponsePayload` | type | `export type OpenInEditorResponsePayload = {` | `[SRC:code/core/src/core-events/data/open-in-editor.ts:L3]` |
| `RequestData` | type | `export type RequestData<Payload = void> = {` | `[SRC:code/core/src/core-events/data/request-response.ts:L1]` |
| `ResponseData` | type | `export type ResponseData<Payload = void, ErrorPayload extends Record<string, any> \| void = void> =` | `[SRC:code/core/src/core-events/data/request-response.ts:L6]` |
| `SaveStoryRequestPayload` | interface | `export interface SaveStoryRequestPayload {` | `[SRC:code/core/src/core-events/data/save-story.ts:L1]` |
| `SaveStoryResponsePayload` | interface | `export interface SaveStoryResponsePayload {` | `[SRC:code/core/src/core-events/data/save-story.ts:L8]` |
| `StoryFinishedPayload` | interface | `export interface StoryFinishedPayload {` | `[SRC:code/core/src/core-events/data/phases.ts:L3]` |
| `WhatsNewCache` | interface | `export interface WhatsNewCache {` | `[SRC:code/core/src/core-events/data/whats-new.ts:L1]` |
| `WhatsNewData` | type | `export type WhatsNewData =` | `[SRC:code/core/src/core-events/data/whats-new.ts:L6]` |

## `storybook/preview-api`

Entry: `code/core/src/preview-api/index.ts`.

| Export | Kind | Declaration | Source |
|---|---|---|---|
| `createPlaywrightTest` | function | `export function createPlaywrightTest<TFixture extends { extend: any }>(baseTest: TFixture): TFixture {` | `[SRC:code/core/src/preview-api/modules/store/csf/portable-stories.ts:L319]` |
| `emitTransformCode` | function | `export async function emitTransformCode(source: string \| undefined, context: ReducedStoryContext) {` | `[SRC:code/core/src/preview-api/modules/preview-web/emitTransformCode.ts:L15]` |
| `getCsfFactoryAnnotations` | function | `export function getCsfFactoryAnnotations<TRenderer extends Renderer = Renderer, TArgs extends Args = Args>(story: LegacyStoryAnnotationsOrFn<TRenderer> \| Story<Renderer>, meta?: ComponentAnnotations<TRenderer, TArgs> \| Meta<Renderer>, projectAnnotations?: ProjectAnnotations<TRenderer>) {` | `[SRC:code/core/src/preview-api/modules/store/csf/csf-factory-utils.ts:L10]` |
| `pauseAnimations` | function | `export function pauseAnimations(atEnd = true): CleanupCallback {` | `[SRC:code/core/src/preview-api/modules/preview-web/render/animation-utils.ts:L18]` |
| `PropDescriptor` | type | `export type PropDescriptor = string[] \| RegExp;` | `[SRC:code/core/src/preview-api/modules/store/filterArgTypes.ts:L5]` |
| `Report` | interface | `export interface Report<T = unknown> {` | `[SRC:code/core/src/preview-api/modules/store/reporter-api.ts:L1]` |
| `ReporterAPI` | class | `export class ReporterAPI {` | `[SRC:code/core/src/preview-api/modules/store/reporter-api.ts:L8]` |
| `SelectionStore` | interface | `export interface SelectionStore {` | `[SRC:code/core/src/preview-api/modules/preview-web/SelectionStore.ts:L17]` |
| `simulateDOMContentLoaded` | function | `export function simulateDOMContentLoaded() {` | `[SRC:code/core/src/preview-api/modules/preview-web/simulate-pageload.ts:L31]` |
| `simulatePageLoad` | function | `export function simulatePageLoad($container: any) {` | `[SRC:code/core/src/preview-api/modules/preview-web/simulate-pageload.ts:L83]` |
| `View` | interface | `export interface View<TStorybookRoot> {` | `[SRC:code/core/src/preview-api/modules/preview-web/View.ts:L3]` |
| `waitForAnimations` | function | `export async function waitForAnimations(signal?: AbortSignal) {` | `[SRC:code/core/src/preview-api/modules/preview-web/render/animation-utils.ts:L54]` |

## `storybook/internal/instrumenter`

Entry: `code/core/src/instrumenter/index.ts`.

| Export | Kind | Declaration | Source |
|---|---|---|---|
| `Call` | interface | `export interface Call {` | `[SRC:code/core/src/instrumenter/types.ts:L7]` |
| `CallRef` | interface | `export interface CallRef {` | `[SRC:code/core/src/instrumenter/types.ts:L37]` |
| `CallStates` | enum | `export enum CallStates {` | `[SRC:code/core/src/instrumenter/types.ts:L30]` |
| `ControlStates` | interface | `export interface ControlStates {` | `[SRC:code/core/src/instrumenter/types.ts:L51]` |
| `ElementRef` | interface | `export interface ElementRef {` | `[SRC:code/core/src/instrumenter/types.ts:L41]` |
| `EVENTS` | const | `export const EVENTS = {` | `[SRC:code/core/src/instrumenter/EVENTS.ts:L1]` |
| `LogItem` | interface | `export interface LogItem {` | `[SRC:code/core/src/instrumenter/types.ts:L60]` |
| `RenderPhase` | type | `export type RenderPhase =` | `[SRC:code/core/src/preview-api/modules/preview-web/render/StoryRender.ts:L36]` |
| `SyncPayload` | interface | `export interface SyncPayload {` | `[SRC:code/core/src/instrumenter/types.ts:L66]` |

## `storybook/viewport`

Entry: `code/core/src/viewport/index.ts`.

| Export | Kind | Declaration | Source |
|---|---|---|---|
| `DEFAULT_VIEWPORT` | const | `export const DEFAULT_VIEWPORT = 'responsive';` | `[SRC:code/core/src/viewport/defaults.ts:L232]` |
| `GlobalStateUpdate` | type | `export type GlobalStateUpdate = Partial<GlobalState>;` | `[SRC:code/core/src/viewport/types.ts:L31]` |
| `INITIAL_VIEWPORTS` | const | `export const INITIAL_VIEWPORTS = {` | `[SRC:code/core/src/viewport/defaults.ts:L3]` |
| `MINIMAL_VIEWPORTS` | const | `export const MINIMAL_VIEWPORTS = {` | `[SRC:code/core/src/viewport/defaults.ts:L234]` |
| `responsiveViewport` | const | `export const responsiveViewport: Viewport = {` | `[SRC:code/core/src/viewport/responsiveViewport.tsx:L4]` |
| `TOOL_ID` | const | `` export const TOOL_ID = `${ADDON_ID}/tool`; `` | `[SRC:code/core/src/viewport/constants.ts:L4]` |
| `Viewport` | interface | `export interface Viewport {` | `[SRC:code/core/src/viewport/types.ts:L1]` |
| `ViewportMap` | type | `export type ViewportMap = Record<string, Viewport>;` | `[SRC:code/core/src/viewport/types.ts:L14]` |

## `storybook/actions`

Entry: `code/core/src/actions/index.ts`.

| Export | Kind | Declaration | Source |
|---|---|---|---|
| `actions` | function | `export const actions: ActionsFunction = (...args: any[]) => {` | `[SRC:code/core/src/actions/runtime/actions.ts:L5]` |
| `CLEAR_ID` | const | `` export const CLEAR_ID = `${ADDON_ID}/action-clear`; `` | `[SRC:code/core/src/actions/constants.ts:L5]` |
| `config` | const | `export const config: ActionOptions = {` | `[SRC:code/core/src/actions/runtime/configureActions.ts:L3]` |
| `CYCLIC_KEY` | const | `export const CYCLIC_KEY = '$___storybook.isCyclic';` | `[SRC:code/core/src/actions/constants.ts:L6]` |
| `EVENT_ID` | const | `` export const EVENT_ID = `${ADDON_ID}/action-event`; `` | `[SRC:code/core/src/actions/constants.ts:L4]` |
| `PANEL_ID` | const | `` export const PANEL_ID = `${ADDON_ID}/panel`; `` | `[SRC:code/core/src/actions/constants.ts:L3]` |

## `storybook/theming`

Entry: `code/core/src/theming/index.ts`.

| Export | Kind | Declaration | Source |
|---|---|---|---|
| `background` | const | `export const background = {` | `[SRC:code/core/src/theming/base.ts:L44]` |
| `color` | const | `export const color = {` | `[SRC:code/core/src/theming/base.ts:L1]` |
| `Easing` | type | `export type Easing = typeof easing;` | `[SRC:code/core/src/theming/types.ts:L61]` |
| `ensure` | function | `export const ensure = (input: ThemeVars): StorybookTheme => {` | `[SRC:code/core/src/theming/ensure.ts:L10]` |
| `tokens` | const | `export const tokens = {` | `[SRC:code/core/src/theming/base.ts:L104]` |
| `typography` | const | `export const typography = {` | `[SRC:code/core/src/theming/base.ts:L59]` |

## `storybook/internal/preview-errors`

Entry: `code/core/src/preview-errors.ts`.

| Export | Kind | Declaration | Source |
|---|---|---|---|
| `ElementA11yParameterError` | class | `export class ElementA11yParameterError extends StorybookError {` | `[SRC:code/core/src/preview-errors.ts:L385]` |
| `NextjsRouterMocksNotAvailable` | class | `export class NextjsRouterMocksNotAvailable extends StorybookError {` | `[SRC:code/core/src/preview-errors.ts:L332]` |
| `NextJsSharpError` | class | `export class NextJsSharpError extends StorybookError {` | `[SRC:code/core/src/preview-errors.ts:L315]` |
| `UnknownArgTypesError` | class | `export class UnknownArgTypesError extends StorybookError {` | `[SRC:code/core/src/preview-errors.ts:L345]` |
| `UnsupportedViewportDimensionError` | class | `export class UnsupportedViewportDimensionError extends StorybookError {` | `[SRC:code/core/src/preview-errors.ts:L365]` |

## `storybook/internal/bin/loader`

Entry: `code/core/src/bin/loader.ts`.

| Export | Kind | Declaration | Source |
|---|---|---|---|
| `addExtensionsToRelativeImports` | function | `export function addExtensionsToRelativeImports(source: string, filePath: string): string {` — Adds extensions to relative imports in the source code. | `[SRC:code/core/src/bin/loader.ts:L64]` |
| `load` | function | `export const load: LoadHook = async (url, context, nextLoad) => {` | `[SRC:code/core/src/bin/loader.ts:L90]` |
| `resolveWithExtension` | function | `export function resolveWithExtension(importPath: string, currentFilePath: string): string {` — Resolves an extensionless file path by trying different extensions. | `[SRC:code/core/src/bin/loader.ts:L34]` |
| `supportedExtensions` | const | `export const supportedExtensions = ['.js', '.mjs', '.cjs', '.jsx', '.ts', '.mts', '.cts', '.tsx'] as const;` | `[SRC:code/core/src/bin/loader.ts:L19]` |

## `storybook/test`

Entry: `code/core/src/test/index.ts`.

| Export | Kind | Declaration | Source |
|---|---|---|---|
| `uninstrumentedUserEvent` | const | `export const uninstrumentedUserEvent = _userEvent.userEvent;` | `[SRC:code/core/src/test/testing-library.ts:L121]` |
| `UserEvent` | interface | `export interface UserEvent extends _UserEvent {}` | `[SRC:code/core/src/test/testing-library.ts:L119]` |
| `UserEventObject` | type | `export type UserEventObject = ReturnType<typeof userEvent.setup>;` | `[SRC:code/core/src/test/index.ts:L15]` |

## `storybook/internal/manager-errors`

Entry: `code/core/src/manager-errors.ts`.

| Export | Kind | Declaration | Source |
|---|---|---|---|
| `ProviderDoesNotExtendBaseProviderError` | class | `export class ProviderDoesNotExtendBaseProviderError extends StorybookError {` | `[SRC:code/core/src/manager-errors.ts:L23]` |
| `UncaughtManagerError` | class | `export class UncaughtManagerError extends StorybookError {` | `[SRC:code/core/src/manager-errors.ts:L34]` |

## `storybook/internal/manager/globals`

Entry: `code/core/src/manager/globals.ts`.

| Export | Kind | Declaration | Source |
|---|---|---|---|
| `globalPackages` | const | `export const globalPackages = Object.keys(globalsNameReferenceMap) as Array<keyof typeof globalsNameReferenceMap>;` | `[SRC:code/core/src/manager/globals/globals.ts:L24]` |
| `globalsNameReferenceMap` | const | `export const globalsNameReferenceMap = {` | `[SRC:code/core/src/manager/globals/globals.ts:L2]` |

## `storybook/internal/mocking-utils/mocker-runtime`

Entry: `code/core/src/mocking-utils/mocker-runtime.js`.

| Export | Kind | Declaration | Source |
|---|---|---|---|
| `ModuleMockerInterceptor` | class | `export class ModuleMockerInterceptor {` — An interceptor for module mocking. | `[SRC:code/core/src/mocking-utils/mocker-runtime.js:L5]` |
