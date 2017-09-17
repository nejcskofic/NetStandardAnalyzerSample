Instructions for building analyzer targeting netstandard 1.3

Steps to make it work:

- Create new .NET Standard library
- Library must target .NET Standard 1.3. This is required if you wish to run analyzer as extension inside VS (extensions target .NET 4.6). Mapping between standard versions and full framework versions is available here. Also if you try to target lower version than 1.3, you will not be able to include required analyzer packages.
- Add nuget package for Microsoft.Composition latest version. This is needed by Microsoft.CodeAnalysis.CSharp.Workspaces. If you try to add workspaces first, you will get error that referenced composition package is not compatible.
- Add nuget package for Microsoft.CodeAnalysis.CSharp (I'm using latest 1.* version)
- Add nuget package for Microsoft.CodeAnalysis.Csharp.Workspaces (version should match the version of Microsoft.CodeAnalysis.CSharp).
- At this point you can copy code from portable project and build it. There should be no errors (you may have to close and reopen solution if VS is still displaying red squiggles).
- To make VS extension work, just open source.extension.vsixmanifest, go to assets tab and change reference to .NET standard library
- To create .nuget package just execute Pack from context menu of project