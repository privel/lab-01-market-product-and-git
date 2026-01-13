# Lab 01 – Products, Architecture & Roles

To kickstart the course, you will explore two things:
>
> 1) How real software products are structured;
> 2) What kind of engineers build and operate them.
>
## Learning Outcomes

By the end of this lab you should be able to:

- Use GitHub to structure your work and collaborate with peers (issues, branches, pull requests, and reviews).
- Explain the basic architecture of a real-world digital product in terms of components, data flow, and deployment.
- Reflect on your career in tech, examine your current skillset, and plan for the future.

## Tasks overview

To complete this lab, you will need to:
- Setup your github account and this lab's repo.
- Pick an existing digital product.
- Sketch its architecture: components, data flow, deployment.
- Map components to tech roles and skills using real job postings and `roadmap.sh`.
- Practice using GitHub issues, branches and pull requests (PRs) to organize your work in a repository (repo) and get feedback from peers.

This and all other lab assignments will simulate real-life engineering practices:
- Follow processes;
- Communicate via issues/PRs;
- Keep the work reviewable;
- Write acceptance criteria;
- Write clear commit messages.

## Repo structure
- `.github/ISSUE_TEMPLATE` – templates for your issues.
- `.github/pull_request_template.md` – a template for PRs.

---

## Lab setup

### Set up a fork
1. Create a GitHub account.
2. Fork this repo to your GitHub account.
3. Continue your work in the forked repo.
4. In the repo -> `Settings` -> `General` -> `Features`, enable `Issues`.
5. In the repo -> `Issues` -> `Labels`, create a new label:
   1. Click `New label`.
   2. Name: `task`.
   3. Click `Create label`.
    <!-- TODO ask students to provide a proof of the setup -->
6. In the repo Settings -> Code and automation -> Add branch ruleset:
   1. Ruleset Name: `push`
   2. Enforcement status: `Active`
   3. Target branches -> Add target -> Include default branch
   4. Rules:
      - [x] Restrict deletions
      - [x] Require a pull request before merging:
         - Required approvals: `1`
         - Require conversation resolution before merging
         - Allowed merge methods: `Merge`.
      - [x] Block force pushes

### Add a classmate as a collaborator

7. In the repo `Settings` -> `Collaborators` -> `Add people`, add a classmate as a collaborator.
8. Make sure your collaborator have accepted the invitation sent to their email.

### Set up your local tools

9. (If needed) On your computer, configure [`git`](https://git-scm.com/):

    ```bash
    git config --global user.name "Your Name"
    git config --global user.email "your@email"
    ```

10. Install [`VS Code`](https://code.visualstudio.com/). This is our code editor of choice that we'll use in this course.
    <!-- TODO: Add a screenshot with all key elements marked. -->
    Optionally, you can learn more about it:
    - [Basic Layout](https://code.visualstudio.com/docs/getstarted/userinterface#_basic-layout).
    - [Activity Bar](https://code.visualstudio.com/api/ux-guidelines/activity-bar)
    - [Command Palette](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette)
    - [Terminal](https://code.visualstudio.com/docs/terminal/getting-started).
    - [Source Control](https://code.visualstudio.com/docs/sourcecontrol/overview).
    - [Extension Marketplace](https://code.visualstudio.com/docs/configure/extensions/extension-marketplace).
    - How to enable [`files.autoSave`](https://code.visualstudio.com/docs/editing/codebasics#_save-auto-save) and [`editor.formatOnSave`](https://code.visualstudio.com/docs/editing/codebasics#_formatting).

### Open the repository on your machine
11. On your computer, create a directory `pre-swp`.
12. In that directory, clone the lab repo.

    ```bash
    git clone https://github.com/your-username/lab-01-market-product-and-git
    ```

13. Open the repo in `VS Code`.

    ```bash
    cd pre-swp
    code lab-01-market-product-and-git
    ```

### Set up VS Code extensions
14. Install the recommended VS Code extensions (listed in `./.vscode/extensions.json`) when VS Code suggests to install them.
15. Sign in to accounts.
    In the Activity Bar:
    1. Click `Accounts`
    2. Click `Sign in with GitHub`
    3. Repeat for any of the extensions if neeeded.

<!-- TODO: move all gitlens related points to extra section (recommendations) -->
16. Check GitLens.

    In the Activity Bar:

    1. Click `Source Control`
    2. In the `GitLens` panel, click `Remotes`.
    3. Make sure `origin` points to your repo URL.
    4. In the `GitLens` panel, click `Commits`.
    5. Make sure you can see commits to this repo.

### Set up an agent
17. Set up [Kilo Code](https://kilo.ai/install) with Qwen3 Coder (watch [tutorial](https://www.youtube.com/watch?v=G0uIVEt3aj4)) or another [free model](https://openrouter.ai/collections/free-models).

### Skim the lab description
18. Skim this `README.md` file once so you know what’s coming.

---

## Submission checklist

By the end of the lab:

- Make sure that each non-optional task has a corresponding issue linked to a PR.
- Close the issues for which all related activities are done.
<!-- - TODO how does a TA check the work? -->
- Explain your diagram, chosen role in a short conversation with the TA.

<!-- TODO check out all completed steps -->

---

## Procedure for each task

1. [Create](https://docs.github.com/en/issues/tracking-your-work-with-issues/using-issues/creating-an-issue) a GitHub issue in your forked repo using the "Lab Task" option and fill in the details.
2. Create a new branch for the issue via [GitHub](https://docs.github.com/en/issues/tracking-your-work-with-issues/using-issues/creating-a-branch-for-an-issue) or via `git checkout -b <branch name>`.
3. Make [commits](https://smartprogramming.in/tutorials/git-and-github/git-commit) to that branch to complete the task.
     - Commit messages must follow the [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) format.
     - Commit to the branch using one of these approaches:
       1. Using VS Code (see [docs](https://code.visualstudio.com/docs/sourcecontrol/staging-commits)): "Activity Bar" -> "Source Control" -> Click a file -> Select lines in the editor -> Right mouse click the selected lines -> Click `Stage Selected Ranges` -> Write a commit message -> Click `Commit`.
       2. Using a terminal (adds all changes in these files to the staging area):

          ```console
          git add <file 1> <file 2> ... <file n>
          git commit -m "<message>"
          ```

4. Push the branch to your forked repo via [GitLens](https://www.gitkraken.com/blog/vs-code-pull-request) or via the terminal:

    ```console
    git push -u origin <branch name>
    ```

5. Create a PR to the `main` branch via [GitLens](https://www.gitkraken.com/blog/vs-code-pull-request) or via [GitHub](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request).
6. Write an appropriate PR description following the PR template.
7. [Link the PR](https://docs.github.com/en/issues/tracking-your-work-with-issues/using-issues/linking-a-pull-request-to-an-issue#linking-a-pull-request-to-an-issue-using-a-keyword) to the issue, e.g. `Closes #<issue number>`.
8. Request a review of the PR from the collaborator.
9. Address the comments, e.g., make fixes or ask to clarify the comment.
10. Get the collaborator to approve the PR.
11. Merge the PR to the `main` branch.
12. Close the issue.

## PR reviews

As a PR reviewer, you must:

- Review the assigned PR and leave at least 2 meaningful comments created for [particular lines](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/commenting-on-a-pull-request#adding-comments-to-a-pull-request).
- Approve the PR if you're satisfied with the PR.

As a PR author, you must:

- Reply to comments in a meaningful way, e.g., write “Fixed in d0d5aeb” (`d0d5aeb` being the id of commit where you addressed the comment), ask to clarify the comment, or explain why you disagree.
- Make necessary changes based on the review.

---

## Tasks

You work **independently** on the tasks below in your forked repo.

For each task, follow the [procedure](#procedure-for-each-task).

Tasks are non-optional unless marked as "optional".

### 1. Pick a product and describe its architecture

1. [ ] Create an issue `[Task] Product & architecture description`.
2. [ ] Decide on how to make the architecture diagrams. We suggest the following approaches:
   1. You can *prototype* diagrams via the [`hediet.vscode-drawio`](https://marketplace.visualstudio.com/items?itemName=hediet.vscode-drawio) extension. However, it's not a good idea to version control images because you can't conveniently visualize their diffs and therefore can't track changes. Therefore, you must use the ["diagrams as code"](https://simmering.dev/blog/diagrams/) approach and eventually switch to one of the other approaches.
   2. You can write [`PlantUML`](https://plantuml.com/) code.
      - [ ] Install the [`jebbs.plantuml`](https://marketplace.visualstudio.com/items?itemName=jebbs.plantuml) VS Code extension.
      - [ ] Install [`Docker`](https://docs.docker.com/get-started/get-docker/).
      - [ ] Run `docker run --name plantuml-server -d -p 48080:8080 plantuml/plantuml-server:jetty` to access the `PlantUML` server. The `48080` port is already set in `./.vscode/settings.json`.
      - [ ] Write the `PlantUML` code in `./docs/diagrams/src/` and render the diagrams to SVG in `./docs/diagrams/out/` using the `jebbs.plantuml` extension. These directories are already set in `./.vscode/settings.json`.
      - [ ] [Include](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax) the rendered images into your Markdown file.
   3. You can write [Mermaid](https://mermaid.js.org/) code in Markdown code blocks with the `mermaid` language tag (see [docs](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/creating-diagrams#creating-mermaid-diagrams)).
   4. You can use any other tool if it supports the "diagrams as code" approach, e.g., [`Structurizr`](https://structurizr.com/), [`D2`](https://d2lang.com/), [`LikeC4`](https://github.com/likec4/likec4) etc.

    > [!IMPORTANT]
    >
    > The goal of the diagram drawing tasks is to get familiar with certain architectural views (static, dynamic), not to design a system.
    >
    > To design a system rationally, you need to consider the architectural drivers. This approach is outlined in the optional [Task 4](#4-update-architecture-optional-stretch-task).

3. [ ] Create `./docs/architecture.md`. In `./docs/architecture.md`:
    1. [ ] In the `## Product choice` section:
         - [ ] Pick one product from this list or propose your own:
             - Yandex Taxi
             - Telegram
             - ChatGPT.com
             - Wildberries.ru
             - Uchi.ru
             - Any other widely used full-stack app (except for Uber because it's used in diagram examples). Agree with your TA if you choose this option.
         - [ ] Provide:
           - [ ] The product's name;
           - [ ] A link to the product's website.
           - [ ] A short description of the product (1–2 sentences).
    2. [ ] In the `## Motivation` section:
         - [ ] Explain in 3-4 sentences why you personally would be interested to work on this product as a tech specialist.
    3. [ ] In the `## Main components` section:
        - [ ] Select at least 5 main [components](https://c4model.com/abstractions/component) of the product. For example:
          - Mobile app
          - Backend API
          - Authentication service
          - Payment / billing
          - Notifications
          - Admin panel
          - Data analytics
        - [ ] For each component, explain in 1–2 sentences what it does.
        - [ ] Provide a [component diagram](https://en.wikipedia.org/wiki/Component_diagram).
          - [ ] If you use [`PlantUML`](https://plantuml.com/component-diagram):
            - [ ] Store the diagram source code in `./docs/diagrams/src/architecture-component.puml`.
            - [ ] See [how to draw a connection](https://stackoverflow.com/questions/55077828/using-required-provided-interfaces-in-component-diagrams-plantuml/57134601#57134601).
    4. [ ] In the `## Data flow` section:
          - [ ] Describe what happens when a typical user action occurs (e.g. user orders a taxi / sends a message).
          - [ ] Mention which components talk to each other and what kind of data they exchange.
          - [ ] Provide a [sequence diagram](https://en.wikipedia.org/wiki/Sequence_diagram).
            - [ ] If you use [`PlantUML`](https://plantuml.com/sequence-diagram):
              - [ ] Store the diagram source code in `./docs/diagrams/src/architecture-sequence.puml`.
            - [ ] Alternatively, use [`Mermaid`](https://mermaid.js.org/syntax/sequenceDiagram.html).
    5. [ ] In the `## Deployment` section:
         - [ ] Briefly describe where these components live (high-level view). Example:
             - On user devices (mobile/web app).
             - On servers (backend services, databases).
         - [ ] Provide a [deployment diagram](https://en.wikipedia.org/wiki/Deployment_diagram).
           - [ ] If you use [`PlantUML`](https://plantuml.com/deployment-diagram):
             - [ ] Store the diagram source code in `./docs/diagrams/src/architecture-deployment.puml`.
           - [ ] Alternatively, use [`Mermaid`](https://mermaid.js.org/syntax/c4.html#c4-deployment-diagram-c4deployment).
    6. [ ] In the `## Knowledge Gaps` section:
         - [ ] Write at least two things in your architecture that you are not fully sure about (guesses, questions, etc.).

---

### 2. Roles, skills, roadmap.sh, and job postings

1. [ ] Create an issue `[Task] Roles and skills mapping`.

    > [!IMPORTANT]
    > You can ask an LLM “what does a *role* usually do?”, but:
    >
    > - You must visit `roadmap.sh` and real job postings yourself.
    > - Your reflections about what you have / don’t have must be honest and personal.

2. [ ] In `./docs/roles-and-skills.md`:

     - [ ] In the `## Roles for components` section:
        - [ ] For each component from `architecture.md`, list IT roles that are likely involved in the development and maintenance of that component.
        - [ ] Use a nested list. Example:
          - Mobile app
            - Mobile engineer (iOS/Android)
            - QA
            - ...
          - Payment service
            - Back end engineer
            - DevOps
            - QA
          - ...

     - [ ] In the `## Common skills across roles` section:
       - [ ] Based on your intuition and some research, list **skills that almost everyone needs**. Example:
          - Git
          - Basic Linux usage
          - Understanding of HTTP / REST APIs
          - Agentic coding
          - Communicating in a team
          - Writing clear issues/PR descriptions
          - Planning
          - ...

3. [ ] Choose *one* role that seems most interesting to you now.
4. [ ] Go to [`roadmap.sh`](https://roadmap.sh/) and sign up.
5. [ ] Find the roadmap relevant for the role you chose.
6. [ ] In that roadmap, mark the items you already have at least some knowledge in.
7. [ ] In `./docs/roles-and-skills.md`, in the `## My chosen role` section, write:

    ```markdown
    ### Role
    
    <name>
    
    ### Skills I already have
    <!-- from roadmap.sh -->
    - ...
    
    ### Skills I clearly lack
    <!-- from roadmap.sh, 8-10 skills -->
    - ...
    ```

8. [ ] Find **5-7 job postings** for this role on [`HH.ru`](https://hh.ru) or a similar job site.
9. [ ] For each posting, list:
    - Link to the posting.
    - Company name.
    - Role title.
    - 3–5 key skills/requirements they mention.
10. [ ] In `./docs/roles-and-skills.md`, in the `## Job market snapshot` section, write:

    ```markdown
    ### Skills that appear in almost every posting
    <!-- 3-10 skills -->
    - ...
    
    ### Skills from postings that I haven't yet seen on roadmap.sh
    <!-- 1-5 skills -->
    - ...
    
    ### My key takeaway
    ...
    ```

---

### 3. Short personal reflection

1. [ ] Create the issue `[Task] Personal reflection`.

    > [!IMPORTANT]
    > Write this section **without** an LLM. It’s about your own thoughts.

2. [ ] In `./docs/reflection.md` write 5–10 sentences answering:
    - [ ] Which role did you choose and why?
    - [ ] What is one thing about the product’s architecture that was new to you?
    - [ ] Which course topics (Git, Linux, Docker, REST, CI/CD, fullstack, data) seem most relevant to your chosen role?
    - [ ] What is one concrete skill you would like to improve this semester?

---

### 4. Update architecture (optional stretch task)

1. Create the issue `[Task] Update architecture`.
2. [ ] In `./docs/architecture.md`:
    - [ ] In the `## Architectural drivers` section:
      - [ ] List 10-15 [architectural drivers](https://github.com/inno-se/the-guide?tab=readme-ov-file#architectural-drivers) for the system:
        - [ ] business goals;
        - [ ] technical constraints;
        - [ ] primary functional requirements;
        - [ ] quality requirements.
        - [ ] architectural concerns.
    - [ ] In the `## Design decisions` section:
      - [ ] List 5-7 key design decisions for the system ([example](https://github.com/otrebmuh/HotelPricingSystem/blob/433e061f712a8748fdf04a6f767752e12be2f4b9/Design/Architecture.md#10-design-decisions)).
      - [ ] Link each decision to an architectural driver.
      - [ ] Justify each decision (provide rationale) in 1-2 sentences.
      - [ ] List 1-2 discarded alternatives for each decision.

3. [ ] Update the diagrams to match your design decisions.

### 5. Work on an agent (optional stretch task)

1. Create the issue `[Task] Work on an agent`.
2. [ ] In `docs/agent-idea.md`, sketch how an AI agent could:
    - [ ] Read `README.md`;
    - [ ] Generate GitHub issues automatically;
    - [ ] Create initial markdown files for you.
    - [ ] Complete all tasks for you.

3. [ ] Try to implement a part of that agent.
4. [ ] Test that agent in a different fork of this repo.


### Take home exercise
- Learn about Git -> Github -> Github flow
https://hackmd.io/@aabounegm/SWP-git
