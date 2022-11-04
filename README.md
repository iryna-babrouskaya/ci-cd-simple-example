# CiCdSimpleExample

## Create a new project

1. ``ng new project-name``
2. ``cd ./project-name``

## Install linters and formattier

3. ``ng add @angular-eslint/schematics``
4. ``npm install prettier --save-dev``
5. add prettier config ``.prettierrc.json`` with [settings](https://prettier.io/docs/en/options.html) f.e
```json  
{
  "tabWidth": 2,
  "useTabs": false,
  "singleQuote": true,
  "semi": true,
  "bracketSpacing": true,
  "arrowParens": "avoid",
  "trailingComma": "es5",
  "bracketSameLine": true,
  "printWidth": 80
}
```
6. add ``.prettierignore`` with the same as ``.gitignore`` settings
7. `` npm i stylelint --save-dev && npm i stylelint-config-standard --save-dev && npm i stylelint-scss --save-dev && npm i stylelint-prettier --save-dev``

8. add ``.stylelintrc`` with [settings](https://stylelint.io/user-guide/configure/)

### Install lib for Git Hooks

9. ``npm i @evilmartians/lefthook --save-dev``

### Create node tasks

10. In ``package.json`` add to `scripts`
``` json    
    {   
        "code:check": "npx prettier \"src/**/*.{js,ts,html,scss}\" --check --cache",
        "code:fix": "npx prettier \"src/**/*.{js,ts,html,scss}\" --write",
        "style:check": "npx stylelint \"**/*.scss\" --cache",
        "style:fix": "npx stylelint \"**/*.scss\" --fix",
        ...
    }
```

11. For commit add task `"commit": "npx git-cz"`

12. Update `lefthook.yml` with
``` yml 
pre-commit:
  parallel: true
  commands:
    stylelint:
      run: npm run style:check
    prettier-check:
      run: npm run code:check
```
