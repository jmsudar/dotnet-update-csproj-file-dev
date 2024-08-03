# jmsudar.UpdateCSProj

jmsudar.UpdateCSProj is a .NET library for automating updates to .csproj files. It reads command-line arguments to update various properties in the PropertyGroup section of the project file.

## Features

- Efficiently updates .csproj files with provided command-line arguments.
- Reads, processes, and writes back changes to the original .csproj file.
- Supports a wide range of properties within the PropertyGroup section.

## Usage

This project is meant to be used as a console application. Specifically, it was designed to be used as part of a CI/CD workflow such as GitHub Actions. It will read and edit a .csproj file in place, preserving any structure outside the `PropertyGroup` block. It will also ignore any null blocks, so you need not use all the arguments in the example block below.

Any CI/CD platform that can perform a `dotnet run` command can use this project. Simply clone the repo, include the path to your .csproj file and the arguments you want, and the project file will be updated.

```sh
dotnet run --filePath=path/to/your/project.csproj --packageId=your.Package.ID --version=1.0.0 --authors=JMSudar --description="Your description here" --packageTags="tag1;tag2" --repositoryUrl=https://github.com/your/repo --packageLicenseExpression=GPL-3.0-or-later --packageProjectUrl=https://github.com/your/repo --packageReadmeFile=README.md
```

## License

This project is licensed under the GPL-3.0 License - see the LICENSE file for details.

## Contact

JMSudar - code.jmsudar@gmail.com

Project Link - https://github.com/jmsudar/DotNet-XML