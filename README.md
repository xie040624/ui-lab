# ui-lab

This repository contains Part 3 (Robot Framework) and Part 4 (Cypress) of the UI testing lab.

## Robot Framework

The `robot` folder contains the web form tests, the automated QP-01 scenario, shared QuickPizza keywords and evidence from two passing runs. From the `robot` folder, activate the virtual environment and run:

```powershell
.venv\Scripts\activate
robot first.robot web_form.robot pizza_scenario.robot
```

## Cypress

The `cypress` folder contains the web form and QP-01 specs, a custom admin login command, configuration and evidence from a passing run. From the `cypress` folder, run:

```powershell
$env:Path = 'C:\Program Files\nodejs;' + $env:Path
npx cypress run --browser chrome
```
