# Template Project

Configuring a project can be long depending on how you want it clean, scalable and secure (test, linter, security, database, deployment, authentication, and more ...)

To avoid configuring multiple time new rails project I have decided to create a template of a project with everything I need already configured.

## Table of Contents

- [Rename the project](#rename-the-project)
- [Ruby Linter](#ruby-linter)
- [Javascript Linter](#javascript-linter)
- [Linter and git](#linter-and-git)
- [License](#license)

## Rename the project

To rename the project, change the project name in the 2 following files:
* package.json (The name of the package)
* config/application.rb (The name of the module)

## Ruby Linter

The project use the awesome gem [Rubocop](https://github.com/bbatsov/rubocop) as a ruby linter.

To see the result of the linting, just launch the command: 
```sh
$ rubocop
```

Rubocop behaviors can be configured via [.rubocop.yml](https://github.com/Havlicech/template_project/blob/master/.rubocop.yml)

Rubocop has been added in a [git hook pre commit](#enable-pre-commit-hook) to avoid running it manually every time.

## Javascript Linter

The project use the package [ESlint](https://github.com/eslint/eslint) as a Javascript linter.

To see the result of the linting, just launch the command:
```sh
$ node_modules/.bin/eslint --ext .js app/assets/javascript/
```
ESlint behaviors can be configured via [.eslintrc.yml](https://github.com/Havlicech/template_project/blob/master/.eslintrc.yml)

Note that you might need to [allow some global variable](http://eslint.org/docs/user-guide/configuring#specifying-globals) in your javascript file in order to pass the linter.

ESlint has been added in a [git hook pre commit](#enable-pre-commit-hook) to avoid running it manually every time.

## Linter and git

Git hooks are a way to fire custom scripts before certain git command. In our case, we use got hooks to run linters before every commit.

Fire the linter before commit is a good way to ensure that the versionned code will be clean at all time.

### Enable pre commit hook

To run the linters before every commit on the changed file just run the following command in the template_project directory:
```sh
$ sudo mv pre-commit .git/hooks/
```
Then, before each git commit command, you will see the linters works.

### Disable pre commit hook

Avoiding the pre-commit hook should be done only when a quick fix need to be done.

To avoid the linting of the code before a commit run the git command with the -n option:
```sh
$ git commit -n -m 'Commit message'
```

## License

See [License](https://github.com/Havlicech/template_project/blob/master/LICENSE) for more details.
