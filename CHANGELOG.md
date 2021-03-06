# Changelog

## v1.3.1

- [Rolled back re-exported const enums no longer break emit in watch mode as performance cost was too high](https://github.com/TypeStrong/ts-loader/pull/406) resolves #393

## v1.3.0

- [Introduce meaningful error when importing TypeScript from `node_modules`](https://github.com/TypeStrong/ts-loader/pull/399)
- [Introduce `entryFileIsJs` loader option which allows having an entry file which is js.](https://github.com/TypeStrong/ts-loader/pull/399) resolves #388 and #401 - thanks @Wykks and @pqr.  

NB Previously the `entryFileIsJs` option was on by default when `allowJs` was true.  Now it has to be specified directly.  Strictly speaking this is a breaking change; however given this is a rarely used option which exists for what is arguably an edge case this is being added without moving to 2.0.  If this breaks people then we'll never do this again; I'd be surprised if anyone is relying on this though so we're taking a chance.  Related tests have been suffixed "-entryFileIsJs" in the test name.

## v1.2.2

- [Re-exported const enums no longer break emit in watch mode](https://github.com/TypeStrong/ts-loader/pull/377) [#376] - thanks @smphhh
- [typescript.sys should be compiler.sys](https://github.com/TypeStrong/ts-loader/pull/380) [#379] - thanks @johnnyreilly and @jbrantly

## v1.2.1

- [Fix TS module resolution paths on Windows - watch mode becomes faster](https://github.com/TypeStrong/ts-loader/pull/373) [#372] - thanks @smphhh

## v1.2.0

- [Crash when adding/removing files in watch-mode](https://github.com/TypeStrong/ts-loader/pull/364) [#358] - thanks @jbbr for the suggested fix
- [Provided an option to produce Visual Studio compatible error output](https://github.com/TypeStrong/ts-loader/pull/356) [#355] - thanks @gamli

## v1.1.0

- [Added support for vuejs via `appendTsSuffixTo` option](https://github.com/TypeStrong/ts-loader/pull/354) [#270] - thanks @HerringtonDarkholme

## v1.0.0

- [General refactor of ts-loader; some performance improvements](https://github.com/TypeStrong/ts-loader/pull/343) [#335] - thanks @johnnyreilly
- [Make the loader resilient to watched declaration files being removed.](https://github.com/TypeStrong/ts-loader/pull/281) - thanks @opichals

## v0.9.5

- [Improve performance for watch mode / `after-compile` plugin](https://github.com/TypeStrong/ts-loader/pull/187) - thanks @Strate

## v0.9.4

- [Make logging to stderr or stdout configurable; introduce logging levels](https://github.com/TypeStrong/ts-loader/pull/313) [#214] - thanks @ThYpHo0n
- [Fix regression that broke hot module replacement](https://github.com/TypeStrong/ts-loader/pull/322) [#321] - thanks @dopare

## v0.9.3

- [Added support for allowJs](https://github.com/TypeStrong/ts-loader/pull/320) (#316) - thanks @dschnare

## v0.9.2

- [Added support for @types](https://github.com/TypeStrong/ts-loader/pull/318) (#247) -thanks @basarat for the ideas

## v0.9.1

- [Normalize dependency graph paths - Fix broken dependencies on Windows ](https://github.com/TypeStrong/ts-loader/pull/286) - thanks @pzavolinsky
- [Fixed the declaration issue](https://github.com/TypeStrong/ts-loader/pull/307) (#214 part deux) - thanks @dizel3d

## v0.9.0

- [Made ts-loader compatible with node v6](https://github.com/TypeStrong/ts-loader/commit/a4f835345e495f45b40365f025afce72d1817996) - thanks @Blechhirn
- [Fixed the declaration issue](https://github.com/TypeStrong/ts-loader/commit/3bb0fec73a2fab47953b51d256f0f5378f236ad1) (#214) - thanks @17cupsofcoffee
- [Declarations update independent of compiler.watchFileSystem](https://github.com/TypeStrong/ts-loader/pull/167/commits/ae824b2676b226bdd0c860a787754a4ae28e339c) (#155) - thanks @opichals

Now built using TypeScript v2.0

## v0.8.2

- Elided imports are now watched (#156, #169)
- Declaration files for `.d.ts` files are now emitted (thanks @rob-bateman) (#174, #175)

## v0.8.1

- Add better error messaging when a file in tsconfig.json can not be loaded (#117, #145)
- Fix incompatibility with html-webpack-plugin (#152, #154)

## v0.8.0

- Add support for emitting declaration files when `declaration: true` is set (#48, #128)
- Fix bug with specifying `target: es6` and `module: commonjs` at the same time when using
  TS 1.7+ (#111, #132, #140).
- Fix bug with resolving dependencies which are linked using `npm link` (#134, #141) 

## v0.7.2

- Fix regression with watching definition files (#109, #110)

## v0.7.1

- Fix regression with Windows that was introduced in v0.7.0 (#92)

## v0.7.0

- Fix bug with webpack resolution that could sometimes cause TypeScript to not find modules (#92, #102)
- Loader output is now written to stderr instead of stdout. (#95, #103)

## v0.6.1

- Improve initial build performance significantly for larger projects (#100)
- Fix issue with nightly (#96)

## v0.6.0

- Remove support for 1.5 and 1.6-beta. TypeScript 1.6 (stable) is the now the lowest version
  supported.
- Fix issue when using source maps and Babel in certain situations (#81)
- Fix issue with nightly (#83)

## v0.5.6

- Add ignoreDiagnostics feature
- Fix issue with node resolution and `noEmitOnError` (#71)

## v0.5.5

- Fix issue with nightly (Microsoft/TypeScript#4738)
- Add support for the NoErrorsPlugin

## v0.5.4

- Fix issue with nightly (Microsoft/TypeScript#4497)

## v0.5.3

- Utilize TypeScript's new custom module resolution logic to integrate with webpack. This essentially
  means that TypeScript will resolve files exactly the same as webpack does (supporting aliases, etc).
  See the [aliasResolution test](test/aliasResolution) for an example. Only supported in TS 1.6 and
  above.
- Rework error reporting to resolve certain edge cases with dependencies. In general errors should
  be much more consistent now in watch mode.
- Fix issue with targeting ES6 and transpile mode (#36)

## v0.5.2

- Fix issue with TypeScript nightly and new node module resolution strategy (#34)

## v0.5.1

- Tweaked error message output to include error code (#32)
- Add helpful messages around the TypeScript dependency 
  - Suggest how to install TypeScript if it hasn't been installed
  - Show TypeScript version when compiling
  - Warn if TypeScript version is incompatible

## v0.5.0

- Add support for `transpileOnly` loader option. See README for more information.
- TypeScript is no longer a dependency of the loader and must be installed separately
- Loader options can now be set as a property in `webpack.config.js`
- TypeScript options can be set through the loader option `compilerOptions`
- Improved error reporting
  - Errors from all files in the TypeScript application are now reported in watch mode instead of 
    from just those files that changed. This means that making a breaking change in a dependency
    will now be correctly reported as an error in the dependent file.
  - Errors with TypeScript options are now reported as webpack errors instead of logged to console
  - Error output no longer contains the filename once from webpack and again in the error message.
    Instead, the filename is only reported by webpack
  - Fixed issue with latest version of webpack where filenames could be reported twice for the same
    error in certain situations
- Using the `declaration` TypeScript option no longer results in errors
- Add support for the `newLine` TypeScript option
- Tests have been revamped to be full integration tests with nightly builds against the current stable
  and nightly TypeScript. Many new tests have been added.

## v0.4.7

- Update TypeScript dependency to 1.5 release (1.5.3)

## v0.4.6

- Improve error reporting related to tsconfig.json
  - Fix bug that reported the wrong errors
  - Errors are now reported as webpack errors instead of logged to console
- Add support for latest TypeScript nightly (#24)

## v0.4.5

- Add `silent` flag (#22)

## v0.4.4

- Add support for "noLib" compiler option (#19)
- Make errors easier to parse programmatically (#20)
  - Errors in declaration files are now added to the stats object instead of written to console
  - Errors now include `file`, `rawMessage`, and `location` properties
- Make --watch option more robust
  - Fix issue where changes to entry file were not detected
  - Fix issue where changes to typing information only did not result in a rebuild (#21)

## v0.4.3

- Fix error locations to be 1-based instead of 0-based (#18)

## v0.4.2

- Rework the way dependencies are loaded (#14)
- Fix NPM dependency on TypeScript (#15, #16)

## v0.4.1

- Fix Windows issue with paths (#14)

## v0.4.0

- TypeScript 1.5 support! (#14)
- tsconfig.json support (#2, #9)
- ES6 target support
- Remove TS-related options in favor of specifying them in tsconfig.json
- Add `configFileName` option for custom tsconfig files

## v0.3.4

- Exclude TS 1.5 as a dependency since there are breaking changes

## v0.3.3

- Add support for reporting errors in declaration files (#10)
- Add support for watch mode for declaration files (#11)
- Fix issue with extra `sourceMappingURL` in output files (#12)

## v0.3.2

- Add support for manually adding files (#6)
- Add paths to source maps (#8)

## v0.3.1

- Add support for specifying a custom TypeScript compiler

## v0.3.0

- Change how modules are resolved. Imports and declaration file references are
now resolved through TypeScript instead of being resolved through webpack's
`resolve` API. This fixes a number of issues and better aligns the loader to
work as a replacement for the `tsc` command. (#3, #4, #5)

## v0.2.3

- Add noImplicitAny option (#2)

## v0.2.2

- Fix issue with source maps

## v0.2.1

- Add colors to error output

## v0.2.0

- Add new configuration options (#1)
  - target, module, sourceMap, instance
  - sourceMap default changed from `true` to `false`
- Workaround issue with TypeScript always emitting Windows-style new lines
- Add tests

## v0.1.0

- Initial version
