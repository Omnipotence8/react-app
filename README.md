# react-app

Few notes for windows users:

1.) How to generate an SSH key on windows 10/11
howtogeek.com/762863/how-to-generate-ssh-keys-in-windows-10-and-windows-11/

2.) How to install VIM on your windows machine
https://www.vim.org/download.php

3.) How to npm install - yarn on your machine
https://classic.yarnpkg.com/lang/en/docs/install/#mac-stable

error Command failed with exit code 1.

   yarn upgrade --latest react-scripts

   yarn start


+++ b/e2e/package.json
@@ -4,7 +4,9 @@
"description": "",
"main": "index.js",
"scripts": {
-    "cucumber" : "cucumber-js src/features/**/*.feature --require-module ts-node/register --require src/step-definitions/**/**/*.ts"
+    "cucumber:dev" : "cucumber-js src/features/**/*.feature --tags @dev --require-module ts-node/register --require src/step-definitions/**/**/*.ts",
+    "cucumber:smoke" : "cucumber-js src/features/**/*.feature --tags @smoke --require-module ts-node/register --require src/step-definitions/**/**/*.ts",
+    "cucumber:regression" : "cucumber-js src/features/**/*.feature --tags @regression --require-module ts-node/register --require src/step-definitions/**/**/*.ts"
     },
     "author": "",
     "license": "ISC",

+++ b/e2e/src/features/home-page.feature
@@ -1,6 +1,9 @@
Feature: As a user I expect to be able to navigate to the home page

+  @dev
+  @smoke
+  @regression
   Scenario: As a user I expect to be able to see contacts
-    Given I am on the home page
-    Then the contacts header should contain the text Contacts
-
+    Given I am on the "home" page
+    And the "header logo" should be displayed
+    Then the "contacts header" should contain the text "Contacts"
