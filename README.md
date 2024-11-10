# Workshop for Hogeschool Windesheim - Countries of the World - Linear

## Introduction
Tests the functionality of naming all countries in the JetPunk country quiz.

This test automates the process of opening the browser, navigating to the JetPunk
"How many countries can you name?" quiz, and verifying that all countries can be
correctly entered and marked as correct answers.

### Steps
1. Arrange: Set up the Playwright environment and browser, and navigate to the quiz page.
2. Act: Accept cookie consent, start the quiz, retrieve all country names, and enter each country into the answer box. Close any popups that appear.
3. Assert: Verify that all entered countries are marked as correct.
4. Cleanup: Close the Playwright browser and environment.

## Prerequisites
* IntelliJ Community Edition (or any other IDE like Eclipse, Visual Studio Code, etc.)
* JDK 21

## Solution
There are many ways to find a locator. But here are locators we used to make it work:
* Consent button -> `[aria-label='Consent']`
* Countries -> `.gxh`
* Start button -> `#start-button`
* Answer box -> `#txt-answer-box`
* Countries marked as correct -> `//td[contains(@class, 'correct') and .= '%s']`

The last locator might be the hardest one. Let us explain it a bit more

### What It Does
This expression finds specific \<td\> elements. Breaking It Down

`//td`

This part means: "Find all \<td\> elements anywhere in the document."

`[contains(@class, 'correct') and .= '%s']`

This part adds two conditions that the \<td\> elements must meet:

1. `contains(@class, 'correct')`

This means: "The class attribute of the \<td\> must have the word 'correct' in it."

2. `.= '%s'`

This means: "The text inside the \<td\> must match '%s'."