# The PowerView Help System

Based on MDBook, this is a repository for holding the common help system for PowerView. It allows for easy editing and updating of the help system even if the help is not part of the main PowerView repository or you are not a developer.

## Getting Started

First of all, you need to have this repository cloned to your local machine. If you are not familiar with Git, you can use the [GitHub Desktop](https://desktop.github.com/) application to clone the repository. If you are familiar with Git, you can clone the repository using the command line or any other Git client.

To run the help system, you need to have [MDBook](https://rust-lang.github.io/mdBook/) installed. You can install MDBook on your machine or use the EXE-file located in the root folder (Windows only). From the root of the repository, you can run the following command to start the help system:

```bash
mdbook serve
```

This will start a local web server on port 3000. You can access the help system by opening a browser and navigating to `http://localhost:3000`. Any changes you make to the help files will be automatically updated in the browser.

If you have done changes to the structure of the help system (i.e. added or removed files), you should run the following command to update/test the help system:

```bash
mdbook test
```

When files are uploaded to git tests will be run and the build will fail if the tests fail. You are not allowed to push to the main branch without passing tests. If tests are passed and your branch is approved, the build will be deployed to the live environment.


## Structure
All help files are located in the src folder. The structure follows the structure in the `SUMMARY.md` file located in the root of the repository. The `SUMMARY.md` file is used to build the menu structure of the book. Any pages you add in the `SUMMARY.md` file will be added to the menu structure of the book (or visa versa).

When you have served or built the book, you will find a folder called `book` in the root of the repository. This folder contains the built book. You can open the `index.html` file in the `book` folder to view the book in your browser. The `book` folder is ignored by git, so you will not be able to commit changes to the `book` folder.


## Approvals needed
You will be allowed to create Pull Requests to the main branch. However, you will not be allowed to merge the PR without approval (approvers will be notified). This is to ensure that the help system is kept up to date and that the help system is not broken.

For approvals to be granted, you need to have kept to the following rules:
- Keep the book structured. Use folders for grouping related content, i.e KPICalculations.
- Use the same structure as the `SUMMARY.md` file.
- Use the same naming convention as the other files.
- Use the same format as the other files.
- Use the same style as the other files.
- Use the same language, spelling and grammar as the other files.
- Make sure that you have tested the changes before creating the PR.


### Useful tools

For Visual Studio Code, the following extentions are reccomended

* _Github Pull Requests and Issues_ - For syncing with DevOps
* _Markdown All in One_
* _Markdownlint_

If you want to learn more about creating good readme files then refer the following [guidelines](https://docs.microsoft.com/en-us/azure/devops/repos/git/create-a-readme?view=azure-devops). You can also seek inspiration from the below readme files:

* [ASP.NET Core](https://github.com/aspnet/Home)
* [Visual Studio Code](https://github.com/Microsoft/vscode)
* [Chakra Core](https://github.com/Microsoft/ChakraCore)
