# Angular + Tailwind
Instructions for Angular + Tailwind setup

## Install Tailwind
```
npm i -D tailwindcss postcss-import postcss-loader postcss-scss @angular-builders/custom-webpack
```

## Initialize Tailwind
```
npx tailwind init
```

## Modify angular.json
<pre>
"build": {
  "builder": "<strong>@angular-builders/custom-webpack</strong>:browser",
  "options": {
      "outputPath": "dist/Frontend",
      "index": "src/index.html",
      "main": "src/main.ts",
      "polyfills": "src/polyfills.ts",
      "tsConfig": "tsconfig.app.json",
      "aot": true,
      "assets": [
          "src/favicon.ico",
          "src/assets"
      ],
      "styles": [
          "src/styles.scss"
      ],
      "scripts": [],
      <strong>
      "customWebpackConfig": {
          "path": "./webpack.config.js"
      }
      </strong>
  },
  "configurations": {
      "production": {
          "fileReplacements": [
              {
                  "replace": "src/environments/environment.ts",
                  "with": "src/environments/environment.prod.ts"
              }
          ],
          "optimization": true,
          "outputHashing": "all",
          "sourceMap": false,
          "extractCss": true,
          "namedChunks": false,
          "extractLicenses": true,
          "vendorChunk": false,
          "buildOptimizer": true,
          "budgets": [
              {
                  "type": "initial",
                  "maximumWarning": "2mb",
                  "maximumError": "5mb"
              },
              {
                  "type": "anyComponentStyle",
                  "maximumWarning": "6kb",
                  "maximumError": "10kb"
              }
          ]
      }
  }
},
"serve": {
  "builder": "<strong>@angular-builders/custom-webpack</strong>:dev-server",
  "options": {
      "browserTarget": "Frontend:build",
      <strong>
      "customWebpackConfig": {
          "path": "./webpack.config.js"
      }
      </strong>
  },
  "configurations": {
      "production": {
          "browserTarget": "Frontend:build:production"
      }
  }
},
"test": {
  "builder": "<strong>@angular-builders/custom-webpack</strong>:karma",
  "options": {
      "main": "src/test.ts",
      "polyfills": "src/polyfills.ts",
      "tsConfig": "tsconfig.spec.json",
      "karmaConfig": "karma.conf.js",
      "assets": [
          "src/favicon.ico",
          "src/assets"
      ],
      "styles": [
          "src/styles.scss"
      ],
      "scripts": [],
      <strong>
      "customWebpackConfig": {
          "path": "./webpack.config.js"
      }
      </strong>
  }
},
</pre>
