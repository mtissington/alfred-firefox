# Firefox Assistant for Alfred

Search and manage Firefox bookmarks, history, downloads and tabs directly from Alfred.

![Alfred-Firefox icon](https://github.com/mtissington/alfred-firefox/blob/master/icon.png)

![Animated demo of workflow in use](https://github.com/mtissington/alfred-firefox/blob/master/demo.gif)

This repository is a maintained version of the original [Firefox Assistant for Alfred](https://github.com/deanishe/alfred-firefox), with updated build and release workflows.

The workflow can also be [extended with your own actions](doc/scripts.md).

## Installation

The workflow supports Alfred 4 and later. The Firefox extension works with Firefox, Firefox Nightly and Firefox Developer Edition.

1. Download and install the [latest release](https://github.com/mtissington/alfred-firefox/releases/latest).
2. Run `ffass` in Alfred and choose **Install Firefox Extension** to install the [Firefox extension](https://addons.mozilla.org/en-US/firefox/addon/alfred-launcher-integration/).
3. See the [setup documentation](doc/setup.md) for more details.

## Usage

The main Alfred keywords are:

- `bm <query>` — Search bookmarks
- `bml <query>` — Search bookmarklets
- `hist <query>` — Search browsing history
- `dl [<query>]` — Search downloads
- `tab [<query>]` — Search open tabs
- `ffass [<query>]` — Workflow status and links

See the [usage documentation](doc/usage.md) for full details.

## Integration

Other Alfred workflows can use this workflow to retrieve the title and URL of the active Firefox tab, without relying on AppleScript.

See the [integration documentation](doc/integration.md) for details.

## Building from source

You need [Go](https://go.dev/) (using the version specified in `go.mod`). Builds are driven by [Mage](https://magefile.org/), which Go downloads on first use.

```sh
go run github.com/magefile/mage -l        # List available targets
go run github.com/magefile/mage test      # Run go vet and go test
go run github.com/magefile/mage dist      # Build universal Alfred workflow
go run github.com/magefile/mage build     # Build for this machine only
go run github.com/magefile/mage extension # Build Firefox extension (.xpi)
go run github.com/magefile/mage link      # Link build into Alfred for development
```

The build produces:

- `.alfredworkflow` — the Alfred workflow installer
- `.xpi` — the Firefox extension package

Double-click the `.alfredworkflow` file in `dist/` to install it. The `link` target requires Alfred to be detectable; if it isn't, set `alfred_preferences` to the path of your `Alfred.alfredpreferences`.

## Documentation

- [Setup](doc/setup.md)
- [Usage](doc/usage.md)
- [Custom actions and scripts](doc/scripts.md)
- [Workflow integration](doc/integration.md)

See the [documentation directory](doc/) for the full documentation.

## Maintenance and acknowledgements

This repository is maintained by [mtissington](https://github.com/mtissington). It is based on the original [deanishe/alfred-firefox project](https://github.com/deanishe/alfred-firefox), created by Dean Jackson. Thanks to Dean for the original work.

The project is written in Go and uses the [AwGo library](https://github.com/deanishe/awgo). Icons are based on [Font Awesome](https://fontawesome.com/).

This project is released under the [MIT License](LICENCE.txt).
