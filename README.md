[![Build Status](https://github.com/coderpatros/ant-path-matching/workflows/.NET%20Core%20CI/badge.svg)](https://github.com/coderpatros/ant-path-matching/actions?workflow=.NET+Core+CI)
[![License](https://img.shields.io/badge/license-MIT-brightgreen.svg)](License)
[![NuGet Version](https://img.shields.io/nuget/v/CoderPatros.AntPathMatching.svg)](https://www.nuget.org/packages/CoderPatros.AntPathMatching/)

# Ant Path Matching

Package for matching paths (files, directories) using the apache ant-style.

Supports .NET Standard 2.0

### Acknowledgement

This has been forked from [WichardRiezebos/ant-path-matching](https://github.com/WichardRiezebos/ant-path-matching)
and updated to target .NET Standard 2.0.

## Getting started

The code below is an example how to use the library.

#### Standalone match

```
using AntPathMatching;
...
var ant = new Ant("/assets/**/*.{js,css}");
var isMatch = ant.IsMatch("/assets/scripts/vendor/angular.js");
```

#### Recursive match

```
using AntPathMatching;
...
var ant = new Ant("/assets/**/*.js");
var antDir = new AntDirectory(ant);
var matchingFiles = ant.SearchRecursively("C:\directory\", includeDirectoryPath: false);
```

#### Dependency Injection

```
using AntPathMatching;
...
constructor(
	IAntFactory antFactory,				
	IAntDirectoryFactory antDirectoryFactory
) {
	var ant = antFactory.CreateNew("/assets/**/*.js");
	var antDir = antDirectoryFactory.CreateNew(ant);
}
```