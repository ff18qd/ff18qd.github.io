---
layout: post
title:      "Checking syntax errors by Lint (ESLint)"
date:       2018-08-26 23:04:48 +0000
permalink:  checking_syntax_errors_by_lint_eslint
---


I got some code challenges and I coded them in my own sytle (rules that I used and learnt from Flatiron). The mismatching styling rules with the potential company might be caught in the code challenge and it could be a minor issue and it could affect the impression of my code. I did get one comment pointed out that 
> broken markdown, not following codestyle convention (2 indents, line length, method call parentheses)
I felt confused but I do want to follow the rules if I know them in advance. But how can I know? By accident I got another code challenge recently and it gave me a chance to take a glimpse on Lint and ESLint.

Lint is a tool that analyse the source code to flag programming errors, bugs, stylistic errors, and suspicious constructs. ESLint is a pluggable linting utility for JavaScript and JSX. In the package.json (cause it is a project assignment I have this package.json when I forked the repo. If you want to use ESLint you need to install the package and setup the rules by yourself) the devDependencies list eslint package versions. I will link the youtube video tutorial at the end of this article on how to setup your own rule. You can init eslint and during the init process there will some questions and as you fill out the questions the rules are set up. For example, how you like the indentation to be? When to use let and when to use const?  Do you allow console.log? Do you require ES6? etc. After init, the eslintrc file is created and all the rules that you have just setup are listed there. 

In the code it will apply the rules and give you hint of what cause the eslint not happy and there are automatically fix for those simple ones by using --fix option. In case of exemption of rules on certain lines, you can do that by 
`// eslint-disable-next-line no-console` to enable console.log command on the next line. There are airbnb eslint plugin and basic style requirements provided by eslint by default. 

After fix the errors line by line or automatically, the code will have the same style as the dev team has. 

[ESlint tutorial](https://youtu.be/qhuFviJn-es)

[ESLint org](https://eslint.org/)
