# Skill #9 - *Continuous Integration* with CircleCI

## I. Overview
- CircleCI is a cloud service that will *automatically* test your code whenever a change is committed to GitHub
  - This means that CircleCI will run our `npm test` script every time we push to GitHub, and email us if it fails
- What is *Continuous Integration* ?
  - "Integrating" (merging code branches) "hurts" - and because it hurts - we should do it more often (rather than less often) and ultimately it will end up hurting *less* over the long run
  - [YouTube - IBM Cloud - What is Continuous Integration? (6:20)](https://www.youtube.com/watch?v=1er2cjUq1UI)
  - [YouTube - IBM Cloud - What is Continuous Delivery? (5:50)](https://www.youtube.com/watch?v=2TTU5BB-k9U)
  - [YouTube - IBM Cloud - Continuous Deployment vs Continuous Delivery (5:34)](https://www.youtube.com/watch?v=LNLKZ4Rvk8w)

<hr>

## II. Setting up CIrcleCI on a project

### II-A. Clone your start code
- We are going to be setting up a CircleCI project that will run tests for us every time we commit a project to GitHub
- Our starter code from today will be the repository we created the `npm test` script for last time - which is **first-web-service** (or **first-web-service-heroku**, or whatever you called it)
- Go ahead and `git clone <url>` this repository to a folder on your hard drive
- `cd` into the **first-web-service-heroku** folder and make it the *cwd*
- Type `npm test` and verify that the test runs and passes (*passing* means there are no errors, but warnings are acceptable)
- Type `npm run nodemon` and verify that the app still functions

### II-B. Set up a CircleCI account

- Sign up for a CircleCI account (using your GitHub account for login credentials) here:
  - https://circleci.com/signup/

<hr>

![screenshot](_images/ss-33.png)

<hr>

### II-C. Create a CircleCI project

- Head to the Dashboard and click the "Add Project" button

<hr>

![screenshot](_images/ss-34.png)

<hr>

- Then locate your GitHub repository in the **Repo** list and click the "Set Up Project" button

<hr>

![screenshot](_images/ss-35.png)

<hr>

- You have now successfully created a CircleCI project! (see screenshot below)
- Now go ahead and download the configuration file by clicking the download button (or you can copy/paste this configuration file directly from the bottom of the page if you wish) - then take a look at the **config.yml** configuration file:
  - It is written in YAML:
    - https://yaml.org/
    - https://blog.stackpath.com/yaml/
  - It has property that looks something like this `node: circleci/node@4.1`
  - This is an "orb"  - this one being a common pre-set for node projects:
    - https://circleci.com/docs/2.0/orb-intro
    - https://circleci.com/developer/orbs/orb/circleci/node
  - If you look under `jobs` and `build-and-test`, you will see the following
  
  ```
  - run:
      name: Run tests
      command: npm test
  ```
  
  - You can see that the `build-and-test` "job" means that our `npm test` script will be run 
  - And down in `workflows` is where the `build-and-test` job is actually told to run

<hr>

![screenshot](_images/ss-36.png)

<hr>

### II-D. Commit the config file

- In your **first-web-service** folder, create a new folder named **.circleci**, put the **config.yml** file that you downloaded into it
- Commit this file (and folder) to your repo:
  - `git status`
  - `git add .`
  - `git commit -m "committed .circleci/config.yml"`
  - `git push`

<hr>

### II-E. 


| <-- Previous Unit | Home | Next Unit -->
| --- | --- | --- 
|   [Skill #8 - Adding developer "tooling"](8-add-developer-tooling.md) |  [**IGME-430**](../) | Skill #10 - TBA
