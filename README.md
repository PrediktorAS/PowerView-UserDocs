# Introduction

This is a repository for holding the common help system for PowerView.

## Getting Started

Add existing help from misc clients
Rework all help files.
Keep book structured. Use folders for grouping related content, i.e KPICalculations.

SUMMARY.md is building the menu-structure of the book so new content need to be added to
this file.

## Contribute

To contribute to the help-files, please update any errors or improvements

## Generate book

To generate a book for the help-files, use [MDBook](https://rust-lang.github.io/mdBook/).

To generate the book in an other folder than the source, please use the --dest-dir attribute.
_Example: mdbook build "c:\PowerViewHelp\PowerView-Solar-Help" --dest-dir ../PViewHelp_
This will look for the code in c:\PowerviewHelp\PowerView-Solar-Help and generate the html to the folder c:\PowerViewHelp\PViewHelp

[This link](https://rust-lang.github.io/mdBook/cli/build.html) shows how to build the book.

### Useful tools

For Visual Studio Code, the following extentions are reccomended

* _Github Pull Requests and Issues_ - For syncing with DevOps
* _Markdown All in One_
* _Markdownlint_

Remember to keep your local repo up to date before changing anything to avoid merging.

If you want to learn more about creating good readme files then refer the following [guidelines](https://docs.microsoft.com/en-us/azure/devops/repos/git/create-a-readme?view=azure-devops). You can also seek inspiration from the below readme files:

* [ASP.NET Core](https://github.com/aspnet/Home)
* [Visual Studio Code](https://github.com/Microsoft/vscode)
* [Chakra Core](https://github.com/Microsoft/ChakraCore)
