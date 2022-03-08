# Cypress med Cucumber

npm-paketet [cypress-cucumber-preprocessor](https://www.npmjs.com/package/cypress-cucumber-preprocessor) gör att Cypress fungerar med feature-filer.

## Kom igång

### Grundkrav
* [Cypress version 8 eller senare](https://www.npmjs.com/package/cypress)
* [Cucumber (Gherkin) Full Support](https://marketplace.visualstudio.com/items?itemName=alexkrechik.cucumberautocomplete) (Extension till Visual Studio Code)

### Installation

Öppna *Git Bash* (eller annan terminal efter smak) i Cypress-installationens rot-mapp och kör nedan kommando:

```shell
npm install cypress-cucumber-preprocessor --save-dev
```

## Konfiguration

### Cypress

Anslut cypress-cucumber-preprocessor till Cypress:  
`plugins/index.js`

```javascript
const cucumber = require('cypress-cucumber-preprocessor').default;

module.exports = (on, config) => {
  on('file:preprocessor', cucumber());
}
```

Lägg till stöd för feature-filer:  
`cypress.json`

```json
{
  "ignoreTestFiles": "*.js",
  "testFiles": "**/*.{feature, features}"
}
```
Anpassade inställningar:  
`package.json`

```json
{
  "cypress-cucumber-preprocessor": {
    "nonGlobalStepDefinitions": true
  }
}
```

IntelliSense:  
`jsconfig.json`

```json
{
  "include": ["./node_modules/cypress", "cypress/**/*.js"]
}
```

### Cucumber på svenska

Inkludera följande tagg på första raden i feature-filen:

```gherkin
# language: sv
```

Skapa alias för stegen i mappningsfilen/filerna:  
Exempel: `steg.js`

```javascript
import { Given as Givet, When as När, Then as Så } from 'cypress-cucumber-preprocessor/steps';
```
