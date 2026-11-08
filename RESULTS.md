# UI lab results

Tool parts that I chose: Part 3 Robot Framework and Part 4 Cypress

## Part 0

- Step 0.1, Chrome version: 157.0.8103.39
- Step 0.3, ChromeDriver version: 157.0.8103.39
- Step 0.4, locator of Pizza, Please!: `button[name="pizza-please"]`
- Step 0.4, locator of Excluded tools: `//label[normalize-space()='Excluded tools']/following-sibling::select`
- Step 0.4, locator of Must be vegetarian: `input#default-checkbox`
- Step 0.4, locator of Custom Pizza Name: `input#pizza-name`
- Step 0.5, pizza name, tool and calories of the run by hand: Lab Pizza 20261108-121000, Pizza cutter, 600 calories per slice

| Step | Actual result | Pass or fail |
|------|---------------|--------------|
| 1    | The heading read `Looking to break out of your pizza routine?` | Pass |
| 2    | Max Calories per Slice, Excluded tools, Must be vegetarian and Custom Pizza Name appeared | Pass |
| 3    | The fields showed 600, Knife, vegetarian selected and `Lab Pizza 20261108-121000` | Pass |
| 4    | The recommendation showed `Lab Pizza 20261108-121000`, Pizza cutter instead of Knife, and 600 calories per slice | Pass |
| 5    | The page showed `Please log in first.` | Pass |
| 6    | After signing in as admin, the page showed `Latest pizza recommendations` | Pass |
| 7    | The admin list showed `Lab Pizza 20261108-121000 (tool=Pizza cutter, ingredients_number=6)` | Pass |

## Part 3: Robot Framework

- robot --version: Robot Framework 7.5.1 (Python 3.14.6 on win32)
- Step 3.2, failure message for the wrong title: `Title should have been 'Web Form' but was 'Web form'.`
- Step 3.8, run 1, result, elapsed time and pizza name: PASS, 9.20 seconds, Lab Pizza 20261108-182440
- Step 3.8, run 2, result, elapsed time and pizza name: PASS, 9.06 seconds, Lab Pizza 20261108-182449

## Part 4: Cypress

- node --version, npm --version and npx cypress version: v26.13.0, 11.20.0, Cypress package and binary 16.2.1
- Step 4.3, failure message for the wrong title: `Timed out retrying after 10000ms`; actual `Web form`, expected `Web Form`
- Step 4.6, tool and calories in the answer of POST /api/pizza: Scissors, 350 calories per slice
- Step 4.7, the line of the admin list that shows your pizza: `Lab Pizza 20261108-184558 (tool=Scissors, ingredients_number=5) (newest)`
- Step 4.8, run 1, result, duration and pizza name: PASS, 12 seconds, Lab Pizza 20261108-184514
- Step 4.8, run 2, result, duration and pizza name: PASS, 12 seconds, Lab Pizza 20261108-184558
- Step 4.9 (optional), browser and result: Not attempted
