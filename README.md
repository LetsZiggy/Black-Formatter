# Depreciated
*[ruff v0.1.2](https://github.com/astral-sh/ruff) has a built-in and configurable Black drop-in replacement.*

---

### Black-Formatter for Sublime Text

*Please note the plugin hasn't been submitted to [packagecontrol.io](https://packagecontrol.io/). Thus has to be installed manually.*

<br>

#### Installation

##### Installing Plugin

- `Package Control: Add Repository` Method (Recommended)
	1. Open `Command Palette` (Default: `ctrl+shift+p`)
	2. ``Package Control: Add Repository``
	3. `https://raw.githubusercontent.com/LetsZiggy/Black-Formatter/main/repository-package.json`
	4. Open `Command Palette`
	5. `Package Control: Install Package`
	6. `Black-Formatter`
- "Manual" Method (Requires manual update)
	1. Download this repository through `Download ZIP`
	2. Rename folder to `Black-Formatter`
	3. Move folder to `[SublimeText]/Packages` folder
		- To access `[SublimeText]/Packages` folder:
			1. Open/Restart `Sublime Text`
			2. Open the `Command Palette` (Default: `ctrl+shift+p`)
			3. `Preferences: Browse Packages`
	4. Restart `Sublime Text`

---

#### Commands

##### Command palette:

- `Black Formatter: Format this file`

##### Shortcut key:

* Linux/Windows: `Ctrl + Shift + ;`
* Mac: `Cmd + Shift + ;`

---

#### Usage

##### Using Default Settings ({ format_on_save: false })

1. Save current changes
	- Formatting will only be applied to the saved file and _**not the current buffer**_
2. Use one of the available commands to run Black-Formatter

---

#### Configuring Settings

##### To access and modify settings file

Go to `Preferences -> Package Settings -> Black-Formatter -> Settings`

##### To override settings per project basis

To override global plugin configuration for a specific project, add a settings object with a `Black-Formatter` key in your `.sublime-project`. This file is accessible via `Project -> Edit Project`.

```javascript
/* EXAMPLE */
{
	"folders": [
		{
			"path": ".",
		},
	],
	"settings": {
		"Black-Formatter": {
			"format_on_save": true,
		},
	},
}
```

##### Default settings

```javascript
{
	/**
	 * Simply using `python` without specifying a path sometimes doesn't work :(
	 * If these are false, we'll invoke the black binary directly.
	 * https://github.com/victorporof/Sublime-HTMLPrettify#oh-noez-command-not-found
	 * https://www.python.org/downloads/
	 */
	"python_path": {
		"windows": "python.exe",
		"linux": "/usr/bin/python",
		"osx": "/usr/local/bin/python",
	},

	/**
	 * The virtualenv folder name
	 * https://docs.python.org/3/library/venv.html
	 */
	"venv_folder": "venv",

	/**
	 * The location to search for a locally installed black package
	 * These are all relative paths to a project's directory
	 * If this is not found or are false, it will try to fallback to a global package
	 * (see "black_path" below)
	 */
	"local_black_path": {
		"windows": "${project_path}/${venv_folder}/Scripts/black",
		"linux": "${project_path}/${venv_folder}/bin/black",
		"osx": "${project_path}/${venv_folder}/bin/black",
	},

	/**
	 * The location of the user/global installed black package to use as a fallback
	 */
	"black_path": {
		"windows": "%APPDATA%/Local/Programs/Python/Python311/Lib/site-packages/black",
		"linux": "/usr/bin/black",
		"osx": "/usr/local/bin/black",
	},

	/**
	 * Specify this path to an black config file to override the default behavior
	 * Passed to black as --config. Read more here:
	 * https://black.readthedocs.io/en/stable/usage_and_configuration/the_basics.html#configuration-format
	 * If an absolute path is provided, it will use as is.
	 * Else, it will look for the file in the root of the project directory.
	 * Failing either, it will skip the config file
	 */
	"config_path": "",

	/**
	 * Pass additional arguments to black.
	 * Read more here: https://black.readthedocs.io/en/stable/usage_and_configuration/the_basics.html#command-line-options
	 * Please note that "-v | --verbose | -q | --quiet" in `extra_args` will be filtered out (see `debug` below)
	 */
	"extra_args": [ "--safe" ],

	/**
	 * Automatically format when a file is saved
	 */
	"format_on_save": false,

	/**
	 * Only attempt to format files with whitelisted extensions on save.
	 * Leave empty to disable the check
	 */
	"format_on_save_extensions": [ "py" ],

	/**
	 * Logs black output messages to console when set to true
	 * "-v | --verbose | -q | --quiet" will be added to `extra_args` based on `debug` value:
	 * 	- false:
	 * 		- "-v | --verbose" will be removed
	 * 		- "-q" will be added
	 * 	- true:
	 * 		- "-q | --quiet" will be removed
	 * 		- "-v" will be added
	 */
	"debug": false,
}
```
