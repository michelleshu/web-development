# Final Project

Over the next several weeks, in teams of 3-4, you will design and implement a fully functioning web application using React and Firebase. 

---

## Ideation

After forming your team, your first task is to decide on what to build. You have freedom in this decision, under the following constraints.

First, your application must persist user-specified data to Firebase. An anti-example is the keyboard drum kit page we implemented several weeks ago, which provides a fun acoustic experience but does not persist any data across sessions. A better example would be a drum beat interface that allows users to create, play, and save loops. If necessary, your application should perform validation on user input to prevent persisting any malformed data. If user input is invalid, then your application must indicate this clearly to the user. 

Second, your application must provide non-trivial functionality beyond persisting and displaying data. As an anti-example, a basic to-do list that allows the user to create and complete to-do items in a static list does not provide sufficient functionality beyond persistence. A better example would be a to-do list that allows the user to group them by project and/or date, provides a drag-and-drop UI for re-organizing tasks, and supports searching/filtering on tasks.

> Note: You can earn an extra 10 points (on top of 100) by integrating with a third-party API. Just as your application should provide functionality beyond simply displaying persisted data, you should aim to go beyond simply tacking on an unrelated display of third-party data. An anti-example is to add a list of recent Trump tweets to your to-do app. A better example is to extend your to-do list with a simple calendar view that juxtaposes your Google Calendar events alongside your tasks within each day.
>
> Alternatively, you can earn an extra 10 points by utilizing a visualization library like [D3.js](https://d3js.org/). Once again, you should aim to go beyond a trivial usage of the library. Whatever you build with the library should constitute a fundamental piece of your application's user interface/experience.
>
> You cannot earn more than 10 extra points.

If you are having trouble coming up with your own idea, you are welcome to implement the to-do list or drum beat loop ideas above. Depending on how large your group is, we may ask that you further extend the application with additional features. If you choose to implement the to-do list application, then you are required to come up with additional features that differ from what was proposed above---this is because I use the to-do list application to give you a sample tech spec in the next section. Another idea similar in spirit to the to-do list is a personal expense manager in which you can record purchases and display summary statistics. This would be a good candidate for making use of the D3.js library.

---

## Specification

Once you have decided upon what to build, your first assignment is to complete a design and technical specification for your application. Your specification should include the following pieces:
- mocks/sketches of your application in its various states
- a comprehensive list of user stories
- a complete React component hierarchy derived from your mocks
- the structure of persisted user-specified data
- if you utilize a third-party library, a description of the specific objects/classes/functions that you expect to leverage
- if you integrate with a third-party API, the API routes and the structure of the third-party data

You should treat this specification as a living document that you update as needed throughout the project timeline. (No need to update your initial mocks unless you undertake a drastic re-design.) From our perspective, we will be treating this specification as your documentation. How well-maintained your tech spec is will contribute to your project grade. 

[Here](../notes/example-spec.md) is an example of such a specification for the to-do list application described in the previous section.

---

## Process

### Using Git & GitHub

Since you will be working in teams, it is essential that you leverage Git and GitHub effectively to organize and distribute your work. Each project team will be given a new GitHub repository in which to host their shared code.

As is the case with your personal repos, the `master` branch will be protected so that you cannot push changes directly to it. Each individual will contribute changes to the `master` branch through our familiar assignment submission procedure: check out the latest version of the GitHub repo to your local machine, create a new branch, commit and push your changes, and open a pull request to merge your branch into `master`. Review and approval by another team member will be required to merge.

In adopting this process, you will be practicing a standard workflow for collaboration in modern software development. This approach has important benefits: (1) developing on individual branches allows team members to work concurrently on the same codebase without stepping on each other's toes, (2) establishing a formal process for merging into `master` upholds its sanctity, and (3) pull requests provide a good way to present the changes you made to your team members.

### Stand-Up Meetings

Each week, we will schedule a 10-15 minute stand-up meeting with each team. In each meeting, every team member should be prepared to answer the following questions:
1. What did you accomplish in the past week?
2. Are you blocked on anything? If so, on what?
3. What will you be working on next?

You should be as specific as possible in your responses. When describing what you accomplished, mention some important details in your implementation and justify those choices if necessary, particularly if they affect the rest of the group. If you are blocked, come prepared with as detailed understanding of your issue as possible as well as specific questions. Think ahead about what you will be working on next, and discuss with team members how to distribute the next leg of work.

Your communication in these stand-up meetings will contribute to your overall project grade. This aspect does not depend on what you accomplished, but rather how clearly you communicate the details of your progress and any issues. It is expected that you will encounter unexpected issues.

---

## Demo + Presentation

On 05/23, your group will give a final demo and slide-based presentation of your project. The demo and presentation together should take 15-20 minutes.

Think of your demo as an elevator pitch to potential investors. Your demo should present a cohesive narrative of how the user would engage with your application, motivating and demonstrating its key features.

Your presentation will then dive into the details of implementation. Present the overall hierarchy of your React components, the data flow between them, and the structure of the data persisted to Firebase. Reflect on your implementation experience and highlight any challenges you encountered. Describe what the problem was, how you addressed the issue, and what you took away from the experience once you resolved the issue.

Finally, your presentation should conclude with a retrospective on the software development process. How did you coordinate with and distribute work across your team? Which tools and workflows did you find useful, and which did you find to be burdensome? When did your plans or communication go awry? What would you do differently next time? What would you repeat? Be as specific as possible, citing concrete details and/or anecdotes.

---

## Milestones

You should aim to meet the following milestones:
- Week 1 (04/25)
  - tech spec complete
- Week 2 (05/02)
  - tech spec revised based on feedback
  - React components can render (not necessarily styled) (similar to Lab 5)
  - React Router is set up
- Week 3 (05/09)
  - React component props and state are implemented
  - data flows up and down the component hiearchy
- Week 4 (05/16)
  - application can persist user-specified data to Firebase
  - integration with third-party APIs (if any) is complete
- Week 5 (05/23):
  - application is styled and polished
  - demo + presentation are prepared

These milestones are a rough guideline -- they may not make sense for your particular application. Let us know if you feel that some of the milestones above need to be rearranged for your application. For example, if your application is particularly UI-heavy with very simple persisted data, then some of the work that is due for Weeks 2 and 3 could be shifted a week back. However, you must let us know at least a week in advance before shifting any milestone. If we hit Week 1 and you have not talked with us about changing the work due for Week 2, then it is expected that you complete the Week 2 milestone described above.

Only the code on `master` in your GitHub repo will be considered submitted each week. 

---

## Grading Rubric

- tech spec (15 points)
  - Does your spec include mocks/sketches of your application in all of its possible states?
  - Does your spec include a comprehensive list of user stories?
  - Does your spec include a complete React component hiearchy?
  - Does your spec include the JSON structure of your persisted data?
  - If you utilize a third-party library, does your spec provide a description of the specific objects/classes/functions you will leverage?
  - If you intend on incorporating third-party data, does your spec include the JSON structure of the data and cite the API documentation?
- code (50 points)
  - Does your code successfully implement each of your user stories?
  - Have you resolved error messages in the Chrome console?
  - Is your application reasonably styled and easy to use?
  - Are your components and any significant functions documented?
  - Does your code persist user-specified data?
  - Does your code provide non-trivial functionality beyond persisting and displaying data?
- process (25 points)
  - Is your tech spec maintained and updated as the project progresses? 
  - Are you creating Git branches and using GitHub pull requests to merge your work into the master branch?
  - Are you planning ahead and distributing work evenly among your teammates (as measured by number and size of pull requests)?
  - Are you meeting your weekly milestones?
  - Are you prepared for your stand-up meetings? Are you clearly communicating what you worked on, if and on what you are blocked, and what you will be working on next?
- presentation (10 points)


