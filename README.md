# MonoGame Tutorial (M2 MacBook)
Monogame tutorial set up with [Contentless](https://github.com/Ellpeck/Contentless) to bypass mgcb
## Run
`dotnet run`
## How-To Set up MonoGame on Apple Silicon Mac
> [!NOTE]
> Feel free to give feedback if this worked for you or had any issues. It should work for any Mac; especially M1, M2, M3, etc.
### First Time Setup:
- Install x64 version of dotnet
- add `export PATH=/usr/local/share/dotnet/x64:$PATH` to the bottom of `~/.zshrc` 
	- May need to restart terminal or computer for it to take effect
	- Test if it is working by running `which dotnet`. The output should be `/usr/local/share/dotnet/x64/dotnet`
- Run `dotnet new install MonoGame.Templates.CSharp`
- Install "C# Dev Kit" Extension in VS Code 
### Each Project:
Either:
- Clone/Fork this repository and work from there

Or:
- Create a folder for the new project
- Open the folder in VS Code
- Open the terminal with Ctrl + \` (backtick)
- Run `dotnet new mgdesktopgl`
- Run `dotnet add package Contentless --version 4.0.0` 
	- Check [NuGet](https://www.nuget.org/packages/Contentless/) for the latest version number
- Open the file ending in `.csproj` 
	- You will find that the file is structured something like
		```
		<Project Sdk="Microsoft.NET.Sdk">
			<PropertyGroup>
				...
			</PropertyGroup>
			<ItemGroup>
				...
			</ItemGroup>
		</Project>
		```
	- After one of the item groups ends, (`</ItemGroup>`) paste the following:
		```
		<ItemGroup>
		    <MonoGameContentReference Include="Content\Content.mgcb" />
		</ItemGroup>
		```
	- Save and close the file
- Run your project with `dotnet run`.  Instead of using mgcb-editor to add content, just add it to the "Content" folder. It will be automatically added to the project. When you delete a file, you will need to remove the entry for it from Content/Content.mgcb or it will give an error. You can also delete the whole content section of that file and it will be regenerated based on what is actually in the Content folder.
