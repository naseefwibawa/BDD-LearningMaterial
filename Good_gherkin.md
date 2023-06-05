## Proper Behavior

Writing good Gherkin feature files can be challenging at first. It requires a combination of technical and creative skills, much like writing a screenplay or a novel. However, with some guidance and practice, anyone can learn to write effective Gherkin scenarios.

The key to writing good Gherkin is to keep it simple and concise. Use plain English, avoid technical jargon, and focus on the essential details. Start with a clear understanding of the behavior you want to specify, and break it down into small, manageable steps. Each scenario should have a clear goal and a specific outcome.

It's also important to involve stakeholders in the process, such as product owners, developers, and QA. They can provide valuable feedback and help ensure that the scenarios are accurate and complete.

Remember that Gherkin is a tool for communication, not just automation. A well-written Gherkin scenario can serve as a common language between technical and non-technical stakeholders, helping to align everyone's understanding of the desired behavior.

One common mistake made by those new to BDD is approaching Gherkin from a procedural or traditional functional testing mindset. In this approach, feature files are written as a series of step-by-step instructions that include actions and expected results. However, this can result in overly long and complex tests that cover multiple behaviors and are difficult to maintain and investigate when failures occur. A behavior-driven mindset is required when writing Gherkin, focusing on clear and concise scenarios that specify a single behavior or requirement of the system. With this approach, Gherkin becomes a powerful tool for collaboration between business stakeholders and technical team members.

For example, let’s consider a scenario that searches for user admin on User Page CMS. Below would be a reasonable test procedure :

1. Open a CMS Page.

- CMS Page opens successfully.

2. Input a user name and password.

- The username and password inputted into text field.

3. Click on login button.

- User is successfully login into CMS.

4. Click on User Page CMS.

- User is redirect to user page CMS.

5. Enter "admin" in the user search text field bar.

- The text admin should appear on the search bar.

6. Click find button to search.

- Result of searching should be shown to the user.

I have observed many beginners attempting to convert a test like this into Gherkin using the following format :

![bad example please don’t copy !](source\2023-05-11_18h00_47.png)

bad example please don’t copy !

This scenario is not written with a behavior-driven mindset. The author simply added BDD keywords to each step of a traditional test, which does not result in behavior-driven testing.

The first four steps are purely setup and strongly imperative, only describing how to access the CMS. They do not convey any information about the desired behavior being tested. As a result, they can be consolidated into a single declarative step, such as "**Given I am logged into the CMS with valid credentials.**" This new step is easier to read and understand, and focuses on the behavior being tested rather than the specific steps to set it up.

It's important to remember that in Gherkin, each scenario should only cover one behavior. The test example given above contains two behaviors: logging into CMS and performing a user search. This can be addressed by creating two separate scenarios, each with its own Given-When-Then pair. Also, it's important to note that in Gherkin, Given-When-Then steps must appear in order and cannot repeat. Even though some BDD frameworks may allow disordered steps, it goes against the behavior-driven mindset.

It is important to avoid the temptation to arbitrarily change the step types to make scenarios adhere to the Given-When-Then order. Each step type plays a distinct role in the behavior-driven process: Givens set up initial state, When perform an action, and Then verify outcomes. In the example provided, the first Then step could have been converted into a When step, but this would be incorrect since it makes an assertion. It is crucial to respect the integrity of each step type as they serve as a guide for writing effective behavior scenarios.

Additionally, when splitting scenarios, it is possible to uncover unnecessary behavior coverage. It is important to check if a behavior is already covered in another feature file to avoid writing duplicate scenarios. In some cases, a scenario may have multiple When-Then pairs, but it is important to keep in mind that a single scenario should cover one behavior.

The correct feature file would look something like this:

![Correct Example](source\2023-05-11_19h21_51.png)

Correct Example

The second behavior may require the first behavior to be executed first, as it needs to start at the CMS Homepage. However, the login and redirecting steps are merely set up for the behavior of user searching and are not part of it. Therefore, in the second scenario, the Given step can declaratively state that the login and redirecting steps have already been completed, ensuring that the separation of scenarios maintains behavior-level independence.

Remember, behavior scenarios are more than tests – they also represent requirements and acceptance criteria. Just like Uncle Ben said “**Good Gherkin comes from good behavior**”.

## Choosing Effective Scenario and Feature Titles

Having good titles for your scenarios is just as crucial as having good steps. The title serves as the face of a scenario, and it's the first thing people see when they come across it. Thus, it needs to convey the behavior you're testing in a single, clear, and concise line. It's also worth noting that titles are frequently logged by the automation framework, further emphasizing the importance of having a well-crafted and meaningful scenario title.

| BAD EXAMPLE                                                                                                    | GOOD EXAMPLE                                          |
| -------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------- |
| The user can log into the CMS, navigate to the user page CMS, and search the user name, role, and phone number | Search for User Details on CMS with Valid Credentials |

Clear and concise scenario titles are essential for effective communication and traceability in BDD scenarios. A short one-liner that captures the intended behavior is ideal. If the title is too long, it may indicate that either the author does not fully understand the behavior in focus, or that the scenario lacks a clear main behavior. Additional comments can be included to supplement the scenario description, if needed, to avoid lengthy titles. It's worth noting that BDD test automation frameworks often print scenario titles to logs for traceability, making it even more crucial to have clear and concise titles.

## **Avoiding conjunctive steps**

To ensure clarity and maintain focus on one main behavior, be mindful of using conjunction words such as "and," "or," and "but." These words often suggest that multiple actions or behaviors will be included, which can make scenario titles ambiguous. In cases where multiple behaviors need to be tested, it may be appropriate to use a Scenario Outline instead. However, it's generally best to keep each scenario centered on a single main behavior to avoid confusion and ensure the scenario is easy to understand and test.

Avoid using conjunctions such as "because," "since," and "so." These types of phrases tend to explain why a scenario is necessary, but the scenario title should primarily focus on describing the behavior. It is important to keep the scenario title concise and focused. The reasoning behind the scenario can be inferred from the steps or clarified with comments.

| BAD EXAMPLE                                                                                        | GOOD EXAMPLE                                                                                                     |
| -------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| The last five order history are saved so that the user can track them later by clicking the button | Button displays last 5 order history for user tracking                                                           |
| I should be on my dashboard and I should see "You have successfully logged in.                     | split them into 2 steps. - Then I should be on my dashboard - And I should see "You have successfully logged in” |

## **Avoid Assertion Language**

To write clear and effective scenario titles in BDD, avoid using the words "verify," "assert," or "should." These words shift the focus from the behavior being tested to the assertion being made. While assertions are important for testing, behavior scenarios serve as software specifications, and BDD is a development practice for creating better software products, not just a testing tool. Starting every scenario title with "verify" or "assert" also becomes repetitive and hinders alphabetical ordering. Instead, focus on describing the behavior being tested in a declarative and concise manner.

| BAD EXAMPLE                                                                                | GOOD EXAMPLE                                                     |
| ------------------------------------------------------------------------------------------ | ---------------------------------------------------------------- |
| Verify that the user can change their address on address page microsite                    | Change User Address on Address Page Microsite.                   |
| Assert that the total discount is reduced by Rp 10.000 when user apply the direct discount | Reduce total discount by Rp 10.000 when applying direct discount |
| The user should be able to change the delivery setting                                     | Allow changing the delivery setting for the user.                |

## Maximizing the Benefits of Gherkin Backgrounds

To make your scenarios more concise and readable, you can use Background steps to include common setup steps that are repeated across multiple scenarios in a feature file. These steps will be executed before each scenario in the feature file. However, it's important to avoid adding too many steps in the Background, as it can make scenarios harder to understand. So, use Background steps judiciously and only include essential steps that are required for all the scenarios in the feature file.

![Background usage](source\2023-05-12_21h44_12.png)

Background usage

## Restrict the Number of Scenarios per Feature

Declarative steps in BDD specify what action should be performed without delving into the details of how it will happen. They express actions at a higher level, making them behavior-driven. For instance, instead of writing imperative steps that detail every action, a single declarative step such as "When the user enters 'admin' at the search bar" can be used. Here, the scrolling and keystroking actions are implied and will be handled by the automation in the step definition. If you want to reduce step count, consider using declarative steps whenever possible.

## **Avoid of using gigantic tables**

Excessive scenario outlines can lead to unnecessarily long and complex scenarios, resulting in wasted time during test execution. When dealing with an oversized scenario outline, it is important to ask yourself questions such as: Are all the examples necessary, or are some redundant? Could the scenario be broken down into smaller, more focused scenarios? Are there any common steps that can be moved to a background or reused in other scenarios to reduce duplication? By carefully considering these questions, you can avoid scenario outline abuse and create more efficient and effective behavior scenarios.

- Is each row an equivalence class variation?
- Adding "elephant" to "panda" doesn't add much test value.
- Is every input combination necessary?
- N columns with M inputs each generate MN possible combinations.
- Consider having each input appear only once, regardless of combination.
- Do any columns represent separate behaviors?
- Consider splitting the scenario outline by column if they are never referenced together.
- Does the feature file reader need to know all the data?
- Consider hiding some data in step definitions.
- Some data may be derivable from other data.

While these questions serve as sanity checks, they are not strict rules. The primary goal is to ensure that scenario outlines concentrate on one behavior and incorporate only essential variations.

## **Less is More**

Short and sweet scenarios are recommended, with a suggested step count of less than 10. Lengthy scenarios are often indicative of poor practices, such as using imperative steps instead of declarative steps. Imperative steps focus on the mechanics of how an action should happen and are procedure-driven. As an example, consider the following "When" steps for adding an address on a microsite:

1. when the user open microsite
2. And the user click add address button
3. And the user click on find address bar
4. And the user type their <address>
5. And the user pin point their map
6. And the user click on confirmation button

While it may seem excessive to break down actions into such granular steps, it highlights the fact that imperative steps heavily emphasize how actions are carried out, often requiring numerous steps to complete the intended behavior. Additionally, the intended behavior may not be as clearly conveyed as with declarative steps.
