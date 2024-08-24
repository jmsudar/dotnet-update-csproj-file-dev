# jmsudar.UpdateCSProj

jmsudar.UpdateCSProj is a .NET library for automating updates to .csproj files. It reads command-line arguments to update various properties in the PropertyGroup section of the project file.

## Features

- Efficiently updates .csproj files with provided command-line arguments.
- Reads, processes, and writes back changes to the original .csproj file.
- Supports a wide range of properties within the PropertyGroup section.
- Available as a reusable GitHub Action for seamless integration into CI/CD workflows.


## Usage

### As a Console Application

This project is meant to be used as a console application. Specifically, it was designed to be used as part of a CI/CD workflow such as GitHub Actions. It will read and edit a .csproj file in place, preserving any structure outside the `PropertyGroup` block. It will also ignore any null blocks, so you need not use all the arguments in the example block below.

Any CI/CD platform that can perform a `dotnet run` command can use this project. Simply clone the repo, include the path to your .csproj file and the arguments you want, and the project file will be updated.

```sh
dotnet run --filePath=path/to/your/project.csproj --packageId=your.Package.ID --version=1.0.0 --authors=JMSudar --description="Your description here" --packageTags="tag1;tag2" --repositoryUrl=https://github.com/your/repo --packageLicenseExpression=GPL-3.0-or-later --packageProjectUrl=https://github.com/your/repo --packageReadmeFile=README.md
```

### As a GitHub Action

You can now use jmsudar.UpdateCSProj directly within your GitHub Actions workflows. This action allows you to update .csproj files as part of your CI/CD pipeline, ensuring your project metadata is always up-to-date.

To run this as an action, include a block following the pattern of the step below in your CD workflow.

```shell
- name: Update .csproj file
uses: jmsudar/UpdateCSProj@v1
with:
    file-path: 'src/YourProject/YourProject.csproj'
    package-id: 'com.example.YourProject'
    version: '1.0.0'
    package-tags: 'utility,automation'
    package-license: 'MIT'
```

#### Input Parameters

The following input parameters are supported when used as a GitHub Action.

- file-path: (Required) The path to the .csproj file you want to update.
- target-framework: Specifies the .NET framework version for your project. Defaults to net6.0 but should be set based on your project’s requirements.
- implicit-usings: Determines whether to use implicit using directives. Set to true to enable, false to disable. Defaults to false.
- nullable: Enables or disables nullable reference types. Set to true to enable, false to disable. Defaults to true.
- package-id: (Required) The unique package ID for your project, typically following the reverse domain name notation, e.g., com.example.project.
- version: (Required) The version number for your project, e.g., 1.0.0.
- author: Specifies the author of the project. Defaults to the GitHub repository owner but can be set to any string or multiple owners.
- package-tags: Tags for your package to help categorize it, separated by commas, e.g., utility,automation.
- repository-url: The URL of your project’s GitHub repository. Defaults to git@github.com:<owner>/<repository>.git, but you can override it with a different URL.
- package-license: (Required) The license under which your project is distributed, e.g., MIT, GPL-3.0.
- package-project-url: The URL of your project’s homepage or main page. Defaults to your repository URL. Defaults to git@github.com:<owner>/<repository>.git, but you can override it with a different URL.
- package-readme-file: The path to your README file to include in your package. Defaults to README.md.

## License

This project is licensed under the GPL-3.0 License - see the LICENSE file for details.

## Contact

JMSudar - code.jmsudar@gmail.com

Project Link - https://github.com/jmsudar/DotNet-XML