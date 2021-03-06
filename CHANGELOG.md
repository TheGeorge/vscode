## Changelog

### 0.0.18

Server (0.8.0 -> 0.9.0):

- Support jumping from record field to record definition (thanks to @gomoripeti)
- Allow usage of long names for the runtime node (thanks to @zsoci)
- Fix macro renaming, where one extra character was deleted (thanks to @gomoripeti)
- Build Dialyzer Persistent Lookup Table (plt) as part of make ci (thanks to @alanz)

### 0.0.17

Extension:

- Fork grammar used for Syntax Highlighting
- Move CHANGELOG to separate file
- Remove references to `debug` profile

Server:

- Suggest type specifications via TypEr
- Jump to definition for parse transforms
- Show OTP version on startup
- Take into account parse transforms runtime dependencies
- Silence Elvis during tests
- Don't crash if compiler options are not found (thanks to @zsoci)
- Handle macros in patterns (thanks to @gomoripeti)
- Be able to add directories to code path via the code_path_extra_dirs config parameter (thanks to @zsoci)
- Remove leftovers of db_dir (thanks to @gomoripeti)
- Be able to define a custom path for the elvis.config file via the elvis_config_path config parameter (thanks to @define-null)

### 0.0.16

Server:

- Add support for [snippets](https://erlang-ls.github.io/articles/snippets-are-here/)
- Fix a number of bugs related to POI ranges (thanks to @garazdawi)
- Complete with arity only when dealing with a remote fun
- Complete facelift for docs on hover
- Include function clauses on hover
- Refactor docs handling into separate module
- Separate docs fetching from formatting
- Refactor test code for hover into separate modules
- Introduce symbol highlighting
- More robust els_code_navigation:find_in_document/5 (thanks to @alanz)
- Add support for renaming macros and callback functions
- Be able to navigate to record definitions from types (thanks to @onno-vos-dev )
- Include project name in Erlang LS node names
- Add support for code navigation for record definitions from type specs
- Rename "xref" diagnostics to "crossref" (since they don't use XRef)
- Add support for unused include files detection
- Do not report crossref diagnostics for known pseudo-functions
- Make docs chunk search use Erlang LS DB rather than code path
- Remove dependency on Mnesia, use ETS only

### 0.0.15

Server:

- Do not crash while fetching docs due to missing encoding
- Fix support for OTP 23 in CI
- Remove obsolete `company-lsp` instructions
- Pass custom macros to Dialyzer
- Assume `COMPLETION_TRIGGER_KIND_INVOKED` when no context is provided
- Do not ask for _text_ on save
- Include experimental support for _DAP_ protocol
- Add loop detection into dependency discovery
- Fix path to PLT cache in CI
- Handle `epp` error messages as diagnostics for included files
- Remove spurious call to `els_dt_document:lookup/1`
- Provide `serverInfo` in `initialize` response
- Include OTP path to `server-info` lens to ease troubleshooting
- Add support for `COMPLETION_TRIGGER_KIND_FOR_INCOMPLETE_COMPLETIONS`

### 0.0.14

Server:

- Do not attempt to load dependencies from sticky directories
- Fix crash from asking erl_lint format our own error messages

### 0.0.13

This release is equivalent to `0.0.12`, but built using OTP 21, to avoid issues for old OTP users

### 0.0.12

Extension:

- Link documentation from README
- Fix security alert for minimalist dependency
- Add missing repository property to avoid warning
- Bump VSCode dependencies
- Ignore files according to the lsp-sample extension
- Bump erlang_ls to 0.4.0

Server:

- Add support for OTP 23
- Fix support for OTP Doc Chunks
- Show diagnostics for module dependencies
- Use correct compilation options when reloading module dependencies
- Do not crash when fetching docs for escriptized modules
- Do not crash if root path contains spaces
- Introduce log message when starting a new session
- Add experimental XREF diagnostics (disabled by default)
- Fix bug which caused a server crash when a notification contained a tilde (~)
- When multiple instances of the same module are indexed, sort them deterministically
- Fix various issues affecting Windows users
- Allow underscore macros
- Introduce experimental runtime node
- Introduce experimental code lens for running CT tests (disabled by default)
- New logo \o/
- Fix support for parse transforms
- Include module name in progress reports for diagnostics
- Wait for tables asynchronously
- Add support for unbound progress reports
- Show progress progress during DB initialization
- Be able to jump to definition from a module import
- Switch to stdio as the default transport
- Be able to enable/disable code lenses and diagnostics
- Do not consider all functions from the erlang module as BIFs
- Remove deprecated port option from escript
- Introduce general provider
- Add code lens to show behaviour usages
- Fix race condition where a server-initiated request was occasionally seen as a response
- Fix type mismatch between protocol and transport types
- Precalculate type specs
- Minor fixes and improvements

### 0.0.11

Extension:

- Include .escript among known file extensions

Server:

- Improve URI handling
- Introduce support for code lenses
- Introduce server-info code lense (disabled by default)
- Fix some Windows incompatibilities
- Avoid the entire server crashing in case of failing providers
- Improve support for Unicode
- Introduce background jobs
- Show progress while indexing
- Fix handling of empty RootUri (Sublime users should enjoy this)
- Add support for .escript files
- Update logging framework
- Add support for finding type references
- Enable logging by default
- Remove eflame dependency
- Add auto-completion for built-in functions and types
- Goto definition on an atom goes to that module if it exists
- Fix symlinks handling
- Add auto-completion for atoms
- Add edoc support for OTP modules (requires OTP 23 once available)
- Introduce CLI help menu via getopt

### 0.0.10

Extension:

- Configurable log level (default: none)
- Configurable log path

Server:

- Add auto completion for types in `spec` and `export_types` contexts
- Fix Elvis diagnostics for modules not belonging to the workspace
- Fix off-by-one folding ranges for some editors
- Restrict dependencies from accessing stdio, avoiding crashes on hover
- Speed up indexing
- Add syntax-highlighting for hover information
- Fix inclusion path for dependencies
- Show function information when hovering the `export` list
- Add plumbing for code lenses
- Find module references
- Find macro references
- Update code formatter to latest available version
- Fix ranges for Dialyzer diagnostics
- Avoid crash in presence of : within strings
- Fix supervision strategy
- Avoid un-necessary parsing
- Asynchronous diagnostics

### 0.0.9

Server:

- Add support for behaviours diagnostics (compiler, dialyzer)
- Add support for parse transform (compiler)
- Find references for records
- Fix support for `$/` notifications and requests
- Be able to specify a different location for the `erlang_ls.config` file
- Fix issue with Elvis diagnostics polluting stdio
- Add root uri to start-up message
- Fix include_dirs passed to Dialyzer
- Inject exit message when TCP socket is closed
- Add support for custom macros
- Add support for hot-code reloading

### 0.0.8

Extension:

- Fix support for Windows
- Add option to override the path to the language server

### 0.0.7

Extension:

- Add list of features to README
- Enable debug mode

### 0.0.6

Extension:

- Bump vscode-languageclient to 6.0.0

Server:

- Add navigation to callback functions for OTP behaviours
- Add support for folding ranges
- Allow a system-wide erlang_ls.config file
- Show edoc for local functions
- Support cancel requests
- Fix support for Dialyzer diagnostics
- Show errors from included .hrl files
- Correctly handle macros on record access
- Remove dependency on wx
- Use platform-dependent log directories
- Automatically generate diagnostics when opening a file
- Limit the amount of symbols returned as workspace symbols
- Add plumbing for a formatter
- Add support for umbrella projects
- Add code completion for record fields
- Use a persistent database (Mnesia) to store indexed information
- Add support for Elvis diagnostics
- Handle multiple export sections
- Do not crash on un-handled extensions
- Do not crash when macros are used as function names
- Other bug fixes and stability improvements

### 0.0.5

Extension:

- Ignore TextMate folders that are not used by the extension
- Add language configuration, including comments and brackets

Server:

- Report server version on startup
- Fix ranges for compiler diagnostics
- Fix completion of function/arity in export lists
- Introduce document highlighting
- Improve performance of workspace symbol lookups
- Add completion for record names
- Improve indexing performances
- Properly cleanup outdated references
- Other bug fixes and stability improvements

### 0.0.4

Extension:

- Do not include un-necessary files in the package, reducing the
  extension size from 20MB to 15MB

### 0.0.3

Extension:

- Add configuration option to enable tracing calls between client and server

### 0.0.2

Server:

- Performance improvements for the indexing process
- Add code navigation for opaque types
- Fix issue with non-unicode modules
- Skip indexing of some OTP applications by default (diameter, megaco, snmp, wx)
- Fix support for Markdown content on hover requests

### 0.0.1

Initial version of the extension.
