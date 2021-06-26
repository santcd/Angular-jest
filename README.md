# Angular unit test with Jest

In this project you can find some cases such as:

* Services
* Conditionals
* Static classes
* Route navigation
* [MatDialog component](https://material.angular.io/components/dialog/overview) 

# Jest installation
1. * With yarn: yarn add jest-junit jest @types/jest jest-preset-angular --save-dev
   * With ng: npm i jest-junit
2. yarn remove karma karma-chrome-launcher karma-coverage-istanbul-reporter karma-jasmine karma-jasmine-html-reporter @types/jasmine @types/jasminewd2 jasmine-core jasmine-spec-reporter
3. Remove from angular.json 
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
4. Remove karma.conf.js and src/test.ts files
5. Create a jest-setup.ts file in the root.
6. Copy an paste -> import 'jest-preset-angular'; in the jest-setup.ts file
7. Modify tsconfig.spec.json
        {
        "extends": "./tsconfig.json",
        "compilerOptions": {
            "outDir": "./out-tsc/spec",
            "types": [
            "jest",
            "node"
            ]
        },
        "files": [
            "src/polyfills.ts"
        ],
        "include": [
            "src/**/*.spec.ts",
            "src/**/*.d.ts"
        ]
        }
8. Add this to package.json


    "jest": {
    "coverageReporters": [
      "html",
      "lcovonly",
      "text-summary",
      "coverage"
    ],
    "reporters": [
      "default",
      "jest-junit"
    ],
    "preset": "jest-preset-angular",
    "setupFilesAfterEnv": [
      "<rootDir>/jest-setup.ts"
    ],
    "collectCoverageFrom": [
      "**/*.ts",
      "!<rootDir>/src/main.ts",
      "!<rootDir>/src/polyfills.ts",
      "!<rootDir>/src/environments/**",
      "!**/*.{module,model,mock,constants,interceptor,guard}.ts"
    ]
  }

9. Modify the "test" in the "scripts" from package.json to 
    "test": "jest --ci --reporters=default --coverage"

# Versions
Angular CLI: 11.0.7
Node: 15.6.0

# Other configurations

 * Angular Material: ng add @angular/material