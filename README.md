# shellscript
Introdução ao shell script
{
    "$schema": "./node_modules/@angular/cli/lib/config/schema.json",
    "version": 1,
    "newProjectRoot": "projects",
    "projects": {
      "lh-angular": {
        "projectType": "application",
        "schematics": {
          "@schematics/angular:application": {
            "strict": true
          }
        },
        "root": "",
        "sourceRoot": "src",
        "prefix": "app",
        "architect": {
          "build": {
            "builder": "@angular-devkit/build-angular:browser",
            "options": {
              "outputPath": "dist/lh-angular",
              "index": "src/index.html",
              "main": "src/main.ts",
              "polyfills": "src/polyfills.ts",
              "tsConfig": "tsconfig.app.json",
              "assets": [
                "src/favicon.ico",
                "src/assets"
              ],
              "styles": [
                "node_modules/bootstrap/dist/css/bootstrap.min.css",
                "src/styles.css"
                
              ],
              "scripts": [
                "node_modules/bootstrap/dist/js/bootstrap.min.js"
              ]
            },
            "configurations": {
              "production": {
                "budgets": [
                  {
                    "type": "initial",
                    "maximumWarning": "500kb",
                    "maximumError": "1mb"
                  },
                  {
                    "type": "anyComponentStyle",
                    "maximumWarning": "2kb",
                    "maximumError": "4kb"
                  }
                ],
                "fileReplacements": [
                  {
                    "replace": "src/environments/environment.ts",
                    "with": "src/environments/environment.prod.ts"
                  }
                ],
                "outputHashing": "all"
              },
              "development": {
                "buildOptimizer": false,
                "optimization": false,
                "vendorChunk": true,
                "extractLicenses": false,
                "sourceMap": true,
                "namedChunks": true
              }
            },
            "defaultConfiguration": "production"
          },
          "serve": {
            "builder": "@angular-devkit/build-angular:dev-server",
            "configurations": {
              "production": {
                "browserTarget": "lh-angular:build:production"
              },
              "development": {
                "browserTarget": "lh-angular:build:development"
              }
            },
            "defaultConfiguration": "development"
          },
          "extract-i18n": {
            "builder": "@angular-devkit/build-angular:extract-i18n",
            "options": {
              "browserTarget": "lh-angular:build"
            }
          },
          "test": {
            "builder": "@angular-devkit/build-angular:karma",
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
                "src/styles.css"
              ],
              "scripts": []
            }
          }
        }
      }
    },
    "defaultProject": "lh-angular"
  }
