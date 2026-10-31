# DRishti: Test Cases

**How these were tested:** the website's own script (`index.html`) was run automatically against a mock page, with each input set as listed. The image-quality tests used computer-generated pixel patterns, not real photos. Print preview (test 11) needs a real browser and was **not** tested yet.

To repeat by hand: open `index.html`, add any retina photo (or tap **Try a sample case**), choose the image grade, enter the readings and tap **Analyse**.

## Risk scoring

Score = grade points (No DR 0, Mild 2, Severe 5) + sugar (180-249: 1, 250+: 2) + top BP (140+: 1) + diabetes years (5-9: 1, 10+: 2).
High if grade is Severe or score is 6+. Medium if 3-5. Otherwise Low.

| # | Test | Grade | Sugar | BP | Years | Expected score | Expected level | Actual result | Pass/Fail |
|---|---|---|---|---|---|---|---|---|---|
| 1 | Healthy reading | No DR | 126 | 128 | 2 | 0 | Low | Score 0, Low risk | Pass |
| 2 | Sample case button | Mild | 210 | 145 | 8 | 5 | Medium | Score 5, Medium risk (fields filled automatically) | Pass |
| 3 | Severe image only | Severe | 110 | 120 | 1 | 5 | High (grade is Severe) | Score 5, High risk | Pass |
| 4 | Many risk factors, no DR | No DR | 260 | 150 | 12 | 5 | Medium | Score 5, Medium risk | Pass |
| 5 | Mild image + many risk factors | Mild | 260 | 150 | 12 | 7 | High | Score 7, High risk | Pass |
| 6 | Boundary: stays Low | No DR | 180 | 139 | 5 | 2 | Low | Score 2, Low risk | Pass |
| 7 | Boundary: becomes Medium | No DR | 180 | 140 | 5 | 3 | Medium | Score 3, Medium risk | Pass |

## Input checks

| # | Test | Expected result | Actual result | Pass/Fail |
|---|---|---|---|---|
| 8 | Tap Analyse with no photo | Message asking for a retina photo and all three readings | Message shown: "Please add a retina photo and fill in all three readings." | Pass |
| 9 | Photo added, one reading left empty | Same message as test 8 | Same message shown | Pass |
| 10 | Switch language to English and Kannada | Risk label, advice and disclaimer change language | English: "Medium risk"; Kannada: "ಮಧ್ಯಮ ಅಪಾಯ" with Kannada advice and score label | Pass |
| 11 | Tap Print result | Print preview shows only the result | Not tested yet (needs a real browser) | To do |

## Image quality check (guide only)

| # | Test | Expected message | Actual result | Pass/Fail |
|---|---|---|---|---|
| 12 | Very dark image | Image looks too dark. Retake with a little more light. | Message matched | Pass |
| 13 | Very bright image | Too bright or glare. Soften the flash and retake. | Message matched | Pass |
| 14 | Out-of-focus image | Image may be blurry. Hold steady and retake. | Message matched | Pass |
| 15 | Clear, evenly lit image | Image quality looks OK. | Message matched | Pass |

Tests 12-15 used generated pixel patterns. The quality thresholds are not calibrated, so also try real retina photos on your phone and note anything unexpected.

## Sample data

Use 3 to 5 images from APTOS 2019 or IDRiD (credit them) in `sample-data/`, one for each class: No DR, Mild, Severe.
