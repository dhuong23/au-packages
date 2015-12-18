My chocolatey packages:
https://chocolatey.org/profiles/majkinetor


**Prerequisites**

`cinst nuget.commandline`

**Build**

In package directory run `cpack`.

**Test**

If package is not installed:

    choco install [PackageName] -source $pwd

If already installed

    choco upgrade [PackageName] -source $pwd

**Push**

In package directory run `..\push.ps1 [API_KEY]` Once specified `API_KEY` parameter can be omitted.

**Automatic package update**

Instead of using [official method](https://github.com/chocolatey/choco/wiki/AutomaticPackages) this repository uses custom auto updater that works as follows:

- Create script `update.ps1`
- Implement `Get-Latest` function that returns latest version of the software.
- Implement `Get-FileReplace` function that returns hashtable enumerator containing paths to files as key names and array containing replacement data as value.
- Call `..\update-package.ps1` to update packages and optionally push them to chocolatey repository (-Push option).


See [example](https://github.com/majkinetor/chocolatey/blob/master/copyq/update.ps1) for details.
