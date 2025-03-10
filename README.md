# Good Gitflow Deployment Practice for Azure App Service

Practice repo for Gitflow Deployment on Azure App Services

## Case Scenario:
1. Your project has different branches for testing, QA, and staging.
2. You want to deploy your project onto Azure app services

## Here a standard flow:

### Continuous Deployment to Staging:
- Every branch (testing, QA, staging) is automatically deployed to its own staging slot so you can easily check and test each branch as soon as changes are made.

### Avoid Direct Production Deployment:
- Instead of enabling continuous delivery directly to production
- deploy your production branch to a non-production slot
- keeps the live environment untouched until you’re sure everything works

### Swapping into Production
- Swap the staging slot into production when your main slot is testing and verified
- swapping prevents downtime becayse you’re not deploying live changes—instead, you’re simply switching environments
  - If something goes wrong, you can roll back easily by swapping back

This is how you maintain that your production is stable at all times

![slot_flow_code_diagam](https://github.com/user-attachments/assets/8b19caef-4b6f-40ee-9d9c-44085e7c422c)

## What I did:

I wanted to mock the flow they had in the chart:

### 1. Created a react and ASP.NET fullstack app and pushed onto the main repo

I created the project in visual studio community
   
### 2. Created three branches: main, stage, dev

**main** - meant for the production-ready, stable code

**stage** - for final testing phase before moving to main

**dev** - development branch

- Keep in mind azure does not charge for a certain amount of deployment slots if you are using standard tier and above
- HOWEVER, all deployment slots and production are shared resources, and on a pay as you consume model.

### 3. Setting up Azure App Services
