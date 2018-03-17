# :beginner: Writing Good Gherkin Syntax :beginner:
This repository outlines some good rules of thumb when dealing with Gherkin syntax when creating an automation framework that will
utilize a BDD manner.

## Overall Guidelines: :beginner:

- BDD/Cucumber is not designed as a "test aid", it is a development aid and firstly we should remove the thoughts of it being solely for testing from our head.
- One scenario should be explicit of one individual behaviour
- Feature files should be readable by someone who has no awareness of the application
- Feature files should be 1 `.feature` file for a single feature
- Feature files should contain no more than a dozen scenarios, even that is arguably questionable
- Scenario definitions should be no more than 10 steps in length
- Gherkin should be written declaratively, not imperatively.  By this I mean that you should avoid writing large amounts of step definitions for each individual action.
- First words of the scenario title should be capitalized, rest in lower case
- Feature declarations should be capitalized for the first word
- All scenarios should be written in a third person sense, do **NOT** use the word "I" do X

## Scenario declarations and Scenario Titles: :beginner:

- Avoid using words like: 'but', 'or', 'and' in the scenario or title
- Avoid using words like: 'like', 'since', 'so' in the scenario or title
- Avoid using words like: 'verify', 'assert', 'should' in the scenario or title
- Scenario titles should be concise one-liners, outlining the behaviour being examined
- Scenarios themselves should be short and sweet

## Steps Overview: :beginner:

- Given steps should be written in the past-tense, e.g `Given an admin user **has** been created`
- When steps should be written in the present-tense, e.g `When the admin **deletes** a user account`
- Then steps should be written in the present-tense, e.g `Then the user **is** unable to login`

## Tags: :beginner:
- Tags should be written in lower case
- Tags should be word seperated by hyphens
- Tags should be concise and not extremely short
- For example: `@example-tag`

## Example [Bad] (Imperative)
```
Feature: Google searching

  Scenario: Google search shows results
    Given the user opens a web browser `<-- Present tense`
    And the user navigates to "https://www.google.com/" `<-- Questionable hard coded test data (throughout)`
    When the user enters "panda" into the search bar `<-- Imperative`
    And the user presses the search button `<-- Imperative`
    Then links related to "panda" are shown on the results page
    When the user clicks on the "Images" link at the top of the results page `<-- Disrespectful of BDD syntax`
    Then images related to "panda" are shown on the results page `<-- Disrespectful of BDD syntax`
```

## Example [Good] (Declarative)
```
Feature: Google searching

  Scenario: Searching on google returns accurate results
    Given the google search page has been loaded `<-- Past tense`
    When the user performs a search for "panda" `<-- Declarative, present-tense`
    Then the returned results are accurate `<-- Declarative, present-tense, Respectful of the BDD syntax`
