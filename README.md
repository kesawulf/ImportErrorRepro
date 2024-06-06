Because of requirements from Autodesk Revit, we cannot have shared code or resources in a separate DLL, and thus were using a Shared Project to have a common set of code for multiple different projects.
Upon updating to .NET 8 from Framework 4.8, this Shared Project is now just an `<Import...` line.
In order to be able to build this project separately (so we can use the Windows Forms Designer with it) and also add/remove files to it like normal, we only import the SDK `props` and `targets` when they've not already been imported.

This appears to break Visual Studio and won't let us load both the main project and the imported project at the same time, also requiring multiple restarts or even installs to get one or the other to load.

The following errors can occur at random:

- ProjectRootElement can't reload if it contains unsaved changes.
- A CPS project was dirtied without a write lock.
- Access denied (when right-clicking to reload the project or removing and then re-adding the project via Visual Studio)

Visual Studio Version 17.10.0
