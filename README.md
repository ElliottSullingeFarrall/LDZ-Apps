# Installation

Download the **LDZ** program (**.exe** for windows or **.app** for Mac OS) from the [Releases](https://github.com/ElliottSullingeFarrall/LDZ-Apps/releases/latest) page and save it somewhere accessible on your PC. Run the program and accept any of the required permissions.

# Usage

### Selecting a Profile

When running the program, you will be given an option to select which profile you wish to record data for. You may select one of: **MASA**, **AS&D** or **Embedded**.

### Changing Profile

To change the the profile, go to **Profile &rarr; Switch Profile** in the menu bar. This will take you back to the profile selection window.

### Submitting Data

Once you have entered all the required information into the fields, simply press **Submit** to submit that data into the record sheet for the current profile.

### Viewing & Deleting Data

To view all the submitted data for the current profile, go to **Data &rarr; View\Delete Data**. You will now be able to see all the data that has been submitted in a table in a new window. Clicking a row of the table will delete that entry from the record sheet and close the window.

### Importing Data

To import data from an existing record sheet, go to **Data &rarr; Import Data...** in the menu bar. You will be asked to choose an excel sheet(s) to import the data from and then asked if you would like to clear the existing data you have submitted from the record.

### Exporting Data

To export data to a excel spreadsheet, go to **Data &rarr; Export Data...** in the menu bar. You will be asked to pick a name for the created spreadsheet and then asked if you would like to clear the existing data you have submitted from the record.

### Clearing Data

There is no dedicated button for clearing the record sheet. If you wish to do so, please see the sections on [Importing Data](#importing-data) and [Exporting Data](#exporting-data).

### Syncing Multiple Sheets of Data

If you wish to merge multiple record sheets, go to **Data &rarr; Export Data...** in the menu bar and highlight all the sheets you would like to sync. For further details, consult the section on [Importing Data](#importing-data).

# Development

This app was developed using NixOS with an environment configured using a combination of **direnv**, **nix-shell** and **poetry**. I have also provided some basic steps for setting up a development environment in Windows and Mac OS.

### Windows

Start by using **powershell** to install [chocolatey](https://chocolatey.org/install#individual) and then we can install some packages.

```
choco install visualstudio2022-workload-vctools
choco install git
choco install python
```
Poetry cannot be installed through chocolatey so this must be installed seperately. There are [instructions](https://python-poetry.org/docs/#installing-with-the-official-installer) on how to do this using powershell.

Next we configure some environment variables for python.

```
$env:Path += ";$env:APPDATA\Python\Scripts;C:\Windows\System32\downlevel;C:\Windows\System64\downlevel"
$env:PYTHON_KEYRING_BACKEND="keyring.backends.null.Keyring"
```

From here we setup the project directory and exclude it from the builtin anti-virus so that pyInstaller can compile correctly.

```
Add-MpPreference -ExclusionPath "$([Environment]::CurrentDirectory)"
```

Finally, we use poetry to setup the environment and compile.

```
poetry install
poetry run python compile.py
```

### Mac OS

Start by using a shell to install [homebrew](https://brew.sh) and then we can install some packages.

```
brew install git
brew install tcl-tk
brew install python-tk
brew install poetry
```

Then use poetry to setup the environment and compile.

```
poetry env use $(which python3)
poetry install
poetry run python compile.py
```

# Troubleshooting

In the event of any issues, please contact [me](elliott.sullinge-farrall@surrey.ac.uk).
