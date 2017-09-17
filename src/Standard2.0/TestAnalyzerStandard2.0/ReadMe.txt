These are unofficial instructions how to make netstandard2.0 analyzers work in VS2017.

Tested on following environment:
- Visual Studio Community 2017, version 15.3.4
- Installed .NET Core 2.0 SDK (x86 and x64)

To create netstandard2.0 analyzer follow the same steps as for netstandard 1.3.

Differences:
- Analyzer project targets netsandard 2.0
- Nuget versions for Microsoft.CodeAnalysis.CSharp and Microsoft.CodeAnalysis.CSharp.Workspaces are 2.3.0 (the same version as available on local machine under '.\Microsoft Visual Studio\2017\Community\MSBuild\15.0\Bin\Roslyn')
- Vsix project targets .NET Framework 4.6.1

To make it work inside VS 2017 IDE, you have to copy netstandard.dll (2.0.0) forwarding assembly to one of locations from which IDE loads DLLs. MSBuild knows how to handle 2.0 standard so you can take DLL from '.\Microsoft Visual Studio\2017\Community\MSBuild\Microsoft\Microsoft.NET.Build.Extensions\net461\lib\nestandard.dll' and place it into '.\Microsoft Visual Studio\2017\Community\Common7\IDE'.

As far as I am aware analyzers are working, though there are still some warnings if they are referenced via Nuget packages. This instructions were not extensively tested and use them at your own risk.