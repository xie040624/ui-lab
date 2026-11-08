# UI lab results

Tool parts that I chose:

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
