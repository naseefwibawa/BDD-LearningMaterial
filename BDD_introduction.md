# What is BDD ?

Behavior-Driven Development (BDD) is a way of working on software development that involves different team members collaborating together. It's not a tool or a specific type of testing. BDD was created to help address the problem of unclear requirements and misunderstandings between the people who request software and those who build it.

BDD is similar to Test-Driven Development (TDD), but instead of only developers writing unit tests, the whole team writes tests that describe the desired behavior of the software feature. BDD focuses on defining the expected behavior of a feature from the very beginning using realistic examples, instead of vague technical language. These examples serve as the requirements or acceptance criteria before the feature is built and as test cases or scenarios after development.

Gherkin is a popular language for writing formal behavior specifications in BDD. It uses "Given-When-Then" scenarios to describe the behavior of a feature. BDD scenarios are easy to write and read since they are written in plain English. BDD helps keep developers and QA teams focused on delivering what the product owner wants.

## What is a Behavior ? Why it’s important ?

Behavior is how a product or feature operates. It’s defined as a scenario of inputs, actions, and output. A product or feature exhibits countless behaviors. Identifying behaviors individually brings clarity and simplicity. It also helps explain how behavior are related. Check the example below.

- Login into a web page
- Clicking link on navigation bar
- Submit a form
- Receive expected error

Separating those individual behaviors make it easy to define a system without unnecessary repetition. For example, there may be multiple ways to navigate to the same page.

## What is Three Amigos ?

When a new feature is to be implemented, a group of people with different roles - often called the "three amigos" - get together to discuss and define the requirements. This group typically includes business analysts, programmers, and testers. They work collaboratively to come up with concrete examples of how the software should behave. To document these examples, they write them down in a format called Cucumber Scenarios. This helps to ensure that everyone has a clear understanding of what needs to be built, and serves as a starting point for writing the code that will make the feature a reality.

## What is the benefits of using BDD ?

There are a lot of awesome benefits of using BDD. BDD improves the development process in several ways :

| Inclusion        | BDD scenarios are easy to write because they are written in plain English. It's like The Three Amigos - anyone from the development team, QA team, or product owners can participate and write scenarios together, ensuring everyone is on the same page.                                |
| ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Clarity          | By using scenarios, BDD helps ensure everyone involved in creating the product understands exactly what it needs to do. This reduces confusion and makes it easier to develop the right features.                                                                                        |
| Streamlining     | Using BDD, the requirements for a software feature are expressed as acceptance criteria in a modular format, which can also serve as test cases. This approach can make the automation of tests faster and more efficient.                                                               |
| Shift-Left       | With BDD, defining test cases for a feature is integrated into the early stages of product development, which helps ensure that the team understands the requirements and expectations from the beginning.                                                                               |
| Artifacts        | Scenarios serve as a set of test cases for the development team. If any of the tests are not automated, they can be added to a list of tasks to be automated in the future.                                                                                                              |
| Automation       | BDD frameworks make it easy to turn scenarios into automated tests.                                                                                                                                                                                                                      |
| Test-Driven      | With BDD frameworks, scenarios can be run as tests to identify any issues before the feature is implemented. This helps catch errors early on and ensures that the final product meets the expected behavior outlined in the scenarios.                                                  |
| Code Reuse       | By using the "Given-When-Then" syntax to write scenarios, steps can be reused across multiple scenarios, which saves time and effort in writing and maintaining tests.                                                                                                                   |
| Parameterization | Steps in BDD scenarios can be customized by adding parameters, which allow for greater flexibility and reusability. For example, a step to click a button can be written to accept the button's ID as a parameter, making it applicable to different buttons throughout the application. |
| Variation        | Example tables can be used to provide different combinations of inputs and run the same scenario with ease by utilizing parameters.                                                                                                                                                      |
| Momentum         | As the number of step definitions increases, writing and automating scenarios become easier and faster.                                                                                                                                                                                  |
| Adaptability     | Scenarios can be easily updated as products and features evolve, making it simple to ensure that the software remains aligned with business needs.                                                                                                                                       |

## Where do I start and How to start it ?

When starting a new product or feature, it's best to begin with BDD. This means creating scenarios that clearly define the expected behaviors of the product, with each scenario focused on one specific thing. To avoid ambiguity, behaviors are described in plain language, and any uncertainties can be clarified with Example Mapping. By doing this, everyone involved in the development process can be on the same page, making it easier to collaborate and ensure that the final product meets everyone's expectations.

Behavior-Driven Development has two key objectives: improving collaboration and automation. However, it can be challenging to know where to start and which scenarios to write when working together.

One technique that can make collaboration easier in Behavior-Driven Development is "Example Mapping," a practice developed by the Cucumber team. To use Example Mapping, all you need is a pack of index cards and a big table.

1. write the story being discussed on a yellow card at the top of the table.
2. write a rule for each known acceptance criterion on a blue card under the story.
3. write each example for a rule on a green card.
4. write each open question on a red card to discuss later.

By following this process, the team can quickly see if a story is too big or needs further refinement. The engineers can easily turn the example cards into Gherkin scenarios, and any questions can be assigned to owners to get answers. This process provides clear, fast feedback for stories and should take about 25 minutes per story.

If you interested in learning more about Example Learning, maybe you can read more about it in Matt Wynne’s seminal post on the practice, [Introducing Example Mapping](https://cucumber.io/blog/bdd/example-mapping-introduction/)

Or if you preferred to see the real actual sample on how to implement Example Mapping, you can see this video :

https://www.youtube.com/watch?v=VwvrGfWmG_U
