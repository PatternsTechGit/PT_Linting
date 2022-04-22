# Incorporating ESLint in Angular Application

### What is Linting?
Linting is the automated checking of source code for programmatic and stylistic errors. This is done by using a lint tool (otherwise known as linter). A lint tool is a basic static code analyzer, we will be using [ESLint](https://dev.to/shivambmgupta/eslint-what-why-when-how-5f1d "ESLint").

### Why Linting?
Linting is important to reduce errors and improve the overall code quality. Using lint tools can help you accelerate development and reduce costs by finding errors earlier.

Linting is important in order to maintain consistent code style, prevent code cruft (e.g. unused local variables or unreachable code) and more complex rules like performance optimizations when there are multiple ways to achieve the same result.

It also ensures, writing the code efficiently and consistently across the teams.

Companies using ESLint in their tech stacks, includes **Udemy**, **Airbnb** and **Asana** etc.


### About this exercise
Previously we have 
- Scaffolded a newly angular application
- Install Bootstrap and FontAwesome
- Integrated bootstrap Navbar component

In this lab we will
- Install ESLint.
- Set up AirBnB ESLint Dependencies
- Fix Lint errors automatically
- Install ESLint Extension
- Fix Lint errors manually

------------


#### Step 1: Installing ESLint
First we will install ESLint in our project, by running the following command

```typescript
ng lint
```
The terminal will ask for installing the ESLint package, We will select `Yes` 

The file `.eslintrc.json` is also generated at the root level of the project after the ESlint is installed. This is the configuration file for ESLint. It defines the configuration structure.

For available linting rules please visit [here](https://eslint.org/docs/rules/ "here")


#### Step 2: Setting up AirBnB ESLint Dependencies
Install the correct versions of each package, which are listed by the command:

```typescript
npm info "eslint-config-airbnb-base@latest" peerDependencies
```
![esLINT_airBnB_Dependencies](https://github.com/PatternsTechGit/PT_Linting/blob/main/Readme-images/esLINT_airBnB_Depndencies.png)

As we can see, currently there are two Dependencies and we have already installed `eslint`, Now we will install the `eslint-plugin-import` by using the following command

```typescript
npm i -D eslint-config-airbnb-base eslint-plugin-import
```
If any issues and vulnerabilities arises, run the following command to fix all of them.

```typescript
npm audit fix
```

#### Step 3: Configure ESLint AirBnB base for Typescript
Within ESLint config file i.e `.eslintrc.json`  there is an array named `"extends" : [ ]` Add `airbnb-base` in the array to tell from where the linting rules are being matched

```typescript
extends: [
"plugin:@angular-eslint/recommended",
"plugin:@angular-eslint/template/process-inline-templates",
"airbnb-base",
]
```
As, the `airbnb-base` rule is only for Javascript, So for Typescript support there is another package, To install that run the following command

```typescript
npm i -D eslint-config-airbnb-typescript
```
After that, add the following content in the `"extends" : [ ]` array
```typescript
extends: [
"plugin:@angular-eslint/recommended",
"plugin:@angular-eslint/template/process-inline-templates",
"airbnb-base",
"airbnb-typescript/base"
]
```


#### Step 4: Fix Lint errors Automatically

Run the following command to see all the lint errors.

```typescript
ng lint
```
![Linting erros list](https://github.com/PatternsTechGit/PT_Linting/blob/main/Readme-images/Linting_erros_list.png)

As we can in the above image, we have 262 Errors (261 errors and 1 warning), Lets run the following command to fix these errors automatically

```typescript
ng lint --fix
```
![Linting erros list after autofix](https://github.com/PatternsTechGit/PT_Linting/blob/main/Readme-images/Linting_errors_list_after_autofix.png)

After running the command we are only left with 15 errors and 1 warning, which we will solve manually in the coming steps....

#### Step 5: Installing ESLint Extension
Install the ESLint extension by Microsoft for VS Code to highlight Lint erros in our project file easily.

Reload the VS Code after installing the extension.

![ESLint Extension](https://github.com/PatternsTechGit/PT_Linting/blob/main/Readme-images/ESLint_Extension.png)

#### Step 6: Fix Lint Errors Manually
Now again run the `ng lint` command to get list all lint errors. Now we can see the where ever we have lint error, it is being highlighted with the help of the ESLint extension. Also we can resolve the error with this extension.
