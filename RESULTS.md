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

## Part B

1. The tests locate Max Calories per Slice through its label because all three number inputs use the same id, `floating_filled`. An id selector would therefore match more than one element and could change the wrong field. QuickPizza should give this input a unique id such as `max-calories-per-slice` and connect its label with `for="max-calories-per-slice"`. This would give testers a short, stable and unambiguous locator.

2. The comparison in step 7 is a consistency oracle because it checks one result against an earlier result from the same test instead of comparing it with a fixed tool. It confirms that the tool shown in the recommendation is the same tool stored and displayed in the admin list. This check would catch a fault where QuickPizza recommends Pizza cutter but saves Knife or a default tool in the admin record. It would also catch an admin page that displays the tool from the wrong pizza.

3. The test could check the `vegetarian` field in the response to `POST /api/pizza` and require it to be `true`. It could also verify a visible Vegetarian label in the recommendation if the page displayed one. At present the page lists ingredients but does not state whether the result is vegetarian, so the test needs either the API field or a trusted list of vegetarian ingredients. The API field is the simpler and more reliable source for this check.

4. Robot Framework waited explicitly with keywords such as `Wait Until Element Is Visible` and `Wait Until Page Contains`, while Cypress retried `cy.get`, `cy.contains` and `should` automatically for up to 10 seconds. Robot's reusable keywords made QP-01 read like the written test case, while Cypress required more JavaScript for the intercepted request but needed fewer explicit wait steps. The Robot evidence runs took 9.20 and 9.06 seconds, while both Cypress full runs took 12 seconds for two specs. Robot's HTML log was detailed and easy to expand by keyword, while Cypress's videos and command-oriented failure output made the browser actions easier to follow.

5. I would use Cypress for the automated UI tests of Project 2. Its automatic retries reduce the number of explicit waits and make the tests less sensitive to page timing. It also recorded videos and screenshots automatically, which gives clear evidence of a full run. In this lab, `cy.intercept` also let the test compare the page with the real API response and verify that the request sent the 600-calorie limit.

6. If the locator of the calories box changes, I would update `${MAX CALORIES}` in `robot/resources/quickpizza.resource`. The test file calls keywords such as `Fill In The Pizza Request` and does not contain that locator. All keywords that type into or check the calories field use the shared variable, so the repair is made once. This keeps page structure changes out of `pizza_scenario.robot`.

7. QP-01 must remain one Cypress test because Cypress clears cookies before every test. QuickPizza uses a cookie to keep one browser on the same server, so steps 6 and 7 must use the browser that created the pizza in steps 1 to 5. If the admin steps were a second test, they could connect to another server and fail to find the pizza. The second test would also lose the `pizzaName` value and the `@tool` alias created earlier.
