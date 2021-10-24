# Changelog for Ferium

This changelog is formatted based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),

## [3.5.0] - 24.10.2021

### Added

- Build and release workflow
- `config` command

### Changed

- Internet connection timeout
- Improved `remove` command by showing mods and repos at once
- `ferium list` formatting
- `get_config_file` returns `None`, rather than erroring out, after first time setup
- `Select` and `MultiSelect` use the colorful theme
- Switched to Mozilla Public License 2.0
- Functions which change `config` values now don't write to the `config_file`. The main function does so with those functions receiving a `&mut Config` instead
- All the Todo list items have been moved to [a GitHub Project](https://github.com/theRookieCoder/ferium/projects/1) and `README.md`'s todo list section has been removed

### Fixed

- Mod files for Github Releases now use the correct names
- Repositories which do not release anything no longer crash the program
- Creation of output directory before `upgrade`ing

## [3.4.0] - 23.10.2021

- Upgraded to 2021 edition
- Added `make install` to compile and install `ferium`
- Added proper error checking! (no more `unwrap()`s and `panic!()`s, only `?`s)
- Added check for an internet connection
- Improved check for empty config file
- Added `remove` command to remove to remove mods or repositories from config
- Improved checking of releases for `.jar` assets
- Removed `does_exist` for mod versions, use `match get_mod(...)` instead
- Added checking of releases and versions for mc version and mod loader compatibility
- Converted using `format!()`s for path manipulation to using `pathbuf.join()`
- Made `clap` use version from `crate_version` rather than hardcoding it
- Added `FError` and `FResult` for error checking support
- Added first time setup where user selects mod loader, mc version, and mods directory
- Added abstractions for Mojang's launcher_meta API
- Added function to get `n` of the latest versions of Minecraft (using launcher_meta)
- 

## [3.3.0] - 17.08.2021

### Added

- Some metadata in `cargo.toml`
- Improved CLI to use Clap's built in `version` and `help` subcommands

### Changed

- Renamed `funcs.rs` to `calls.rs` in Labrinth and Octorok
- Removed glob imports where possible
- Switched deserialisation of the file to Serde's built in `from_reader`
- The relative flag in `request` has been replace with a `relative_request` function
- Improved file manipulation in `main.rs` and `wrappers.rs` to use `.join()`s instead of `format!()`
- Removed all `match` and `exit()` pairs to improve error handling in the future. _For now_ these have been replaced with `unwrap()`s
- Made `print()` accept `impl Display` to decrease `String` copies

## [3.2.0] - 06.08.2021

### Added

- Support for GitHub Releases
- `Octorok`, a Github API for Rust
- Made the help page a 'copy' of the README file with suitable formatting
- Version command for checking the version
- Repositories to the configuration

### Changed

- Made HTTP calls non-blocking and asynchronous
- Made all HTTP calls reuse a predefined client
- Added more documentation
- Made `make` builds timed

## [3.1.2] - 06.08.2021

### Added

- Added a makefile for building this project
- Added full documentation for Labrinth structs

### Changed

- Updated `cli.yaml`'s documentation to match the help page
- Moved around Labrinth struct definitions to match its documentation

## [3.1.1] - 05.08.2021

### Changed

- Made the `License` struct's `url` field nullable

## [3.1.0] - 05.08.2021

### Added

- This changelog
- Command line interface and corresponding code (under `cli.rs` and `cli.yaml`)
- Help page and command, add mod command, list mods command
- `Users` struct for Labrinth
- JSON file write
- `does_exist()` function for checking if a mod exists
- Error codes (see changed)

### Changed

- Moved utilities to `util` folder
- Made all panics into `println!`s and exits (with descriptive error codes)
- Commented code better