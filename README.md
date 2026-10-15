# Cost Quest: Factory Lockdown

A complete, browser-only escape-room learning game for Diploma in Accounting, DAC2013 / BAC143 Cost Accounting, Chapter 1. English; 20 questions; five rooms; approximately 25–35 minutes. No installation, backend, API, remote font, analytics or external asset is required. All graphics are CSS or inline SVG.

## Files and local testing

```text
cost-quest/
  index.html       Homepage, arena, challenge dialog and results
  style.css        Responsive layout, factory illustration and controls
  script.js        Labelled editable question bank and all game logic
  README.md        This guide
  FULL_CODE.md     Full source of the four files, labelled by exact filename
```

Unzip the download. Open `index.html` in a current Chrome, Edge, Firefox or Safari browser. No build or local server is required. Keep the HTML, CSS and JavaScript files together. The game also works offline after extracting the files.

## Learning design and source alignment

The original questions follow the user's materials read for this project:

- Chapter 1 THE NATURE AND PURPOSE OF COST AND MANAGEMENT ACCOUNTING.pdf
- DAC2013_Cost_Accounting_Study_Plan_Aug2026.docx (Chapter 1 coverage)
- BAC143_DAC2013_PT1_August_2026_Marking_Scheme.docx (Chapter 1 concepts only)

The game does not reproduce the progress-test questions or expose its other chapters. It covers purpose and users; cost units and centres; responsibility centres; direct and indirect costs; prime and production costs; functional classification; fixed, variable, semi-variable and stepped-fixed costs; graphs; high–low estimation and limitations; and fixed/flexible/flexed budgets. The notes' main outcomes are extended to the budget distinction included later in the chapter.

Outcomes: students identify the purpose of cost information, distinguish cost units/centres, classify costs, compute prime and production cost, interpret cost behaviour, estimate costs using high–low, and calculate a flexed budget. Question 20 uses an unfamiliar laundry scenario to check transfer of high–low understanding.

Rooms 1–3 build conceptual foundations; rooms 4–5 require calculation and judgement. Each terminal contains a question needed to open the next door. Terminal access, locked doors and the room sequence are playable exploration mechanics. Movement has no hazards, penalties or effect on learning marks. A visible Continue button leaves feedback available until the student chooses to move on. Incorrect questions remain unrepaired and can be retried immediately or revisited later. Previously repaired terminals can be reopened for explanation review.

## Controls and scoring

- Computer: arrow keys or WASD to move. Focus the room by clicking its floor if focus is on a button. Enter activates a nearby terminal or exit.
- Mouse/touch: tap a terminal once to approach it, then again to open it. The on-screen directional pad and USE button also work. Approach an unlocked exit and activate it to enter the next room.
- In a challenge: select an answer or press 1–4. Read feedback; choose Continue to return to the room, or Try again after an error. Tab/Enter operate the buttons. Escape closes the challenge (or leaves final practice).
- Repair all four terminals to unlock each exit. After room five, use its exit to see results.
- One mark for each question answered correctly on the first submitted attempt: maximum 20. Each question contributes at most once. Repeated clicks cannot add marks.
- A correct retry repairs the terminal but does not change the first-attempt mark. The report separately shows recovery, first answers, correct answers and explanations for every question.
- Optional final practice revisits questions missed on the first attempt and leaves the original marks unchanged. Students can retry, or read and advance through feedback.
- Untimed is the default. The optional elapsed clock has a soft 30-minute target. It never ends play, penalises marks or hides feedback. Time includes time spent reading feedback.
- Restart starts a fresh mission. Home leaves the mission. Refreshing or closing the page clears progress; there is no persistent student record or teacher dashboard.

## Publish through GitHub Pages

1. Create a GitHub repository, for example `cost-quest`. A public repository is the straightforward option for a GitHub Free account; private Pages availability depends on your plan.
2. Upload the **contents** of the extracted `cost-quest` folder into the repository root. Uploading the ZIP alone will not publish the game. `index.html`, `style.css` and `script.js` must sit together at the root of the publishing folder. README and FULL_CODE are optional for hosting.
3. Commit the files to `main`.
4. Open repository **Settings → Pages**. Under **Build and deployment**, choose **Deploy from a branch**. Select `main` and **/(root)**, then Save.
5. Wait for the Pages deployment and use the site URL displayed there. A normal project URL is `https://YOUR-USERNAME.github.io/cost-quest/`.
6. Share that URL with students through eLearn, WhatsApp or Padlet. Committing later edits to the source branch republishes them; refresh after deployment.

Official publishing guide: https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site

No GitHub repository has been created and no public deployment has been performed as part of this download.

## Edit questions

Open `script.js` in a text editor. The first section is labelled `EDITABLE QUESTION BANK`. Each entry has:

```javascript
{id:"q01", room:0, topic:"Purpose", title:"Your question?",
 options:["Option A","Option B","Option C","Option D"],
 answer:1, explanation:"Explain why option B is correct and the distractors are wrong."}
```

`answer` is zero-based: 0 = first option; 1 = second; 2 = third; 3 = fourth. Use unique IDs. Use four options and one unambiguous correct answer. `room` is zero-based (0–4). Preserve four questions per room for the current four-terminal design. You can replace any question directly. To change the count or rooms, update `ROOMS`, terminal `positions`, homepage count/duration and instructions as well as the bank; the score denominator and progress maximum are dynamic, but the room design is intentionally four terminals per room. Keep a new example as the last question.

`data` optionally holds trusted local HTML for a table or inline SVG. Do not paste untrusted HTML. Other question fields are rendered as plain text. Use quotes correctly and check syntax after editing. Update each explanation when changing numbers or distractors. Search `ROOMS` to change the department names, briefs and terminal labels. Edit `index.html` for the homepage/outcomes and `style.css` for colours/layout.

## Verification completed

JavaScript syntax passed `node --check`. An automated Node VM test with a lightweight simulated DOM checked start, locked exit, tap-to-approach interaction, incorrect/correct feedback state, retries, duplicate-answer protection, all five room transitions, full completion, the 20-question report, unchanged marks during practice, restart reset, home navigation, clock cleanup and question-bank structure. Worked figures and keys were also checked: prime cost RM29; production cost RM10,500; fixed rent RM4 to RM3/unit; variable material RM5,600; supervisors RM9,000; high–low RM4/unit, RM10,000 fixed, RM28,000 forecast; flexed budget RM18,000; final transfer forecast RM16,400.

Actual browser rendering, real keyboard focus and mobile touch were not executed in this environment. The simulated DOM checks do not verify visual appearance or native dialog behaviour. Complete the checklist below before classroom use.

## Manual browser checklist

- [ ] Open locally: the homepage, factory drawing, learning outcome and instructions appear; no console errors or missing files.
- [ ] Start in Untimed mode. Room 1 appears; timer is hidden; score/progress are zero.
- [ ] Test arrows/WASD on the room, Enter near a terminal, tap twice, and the touch pad/USE. All four answer options are readable.
- [ ] Select a wrong answer. The explanation and correct answer appear. Repeated clicks/number keys add no attempts or marks while feedback is shown.
- [ ] Try again and answer correctly. It repairs the terminal but does not award a first-attempt mark. Continue stays manual.
- [ ] Leave an incorrect question with Continue and revisit it; it can still be repaired. Close an unanswered terminal and revisit it; it has no recorded attempt.
- [ ] Open a repaired terminal: it shows the explanation and cannot add marks.
- [ ] Try the exit early: it stays locked. Repair four terminals: exit opens. Approach and activate it to proceed.
- [ ] Finish all 20, including the laundry question, and activate the final exit. Verify first-attempt marks, recovered count and every explanation.
- [ ] Practise missed questions: original report/marks remain unchanged. Restart resets the mission; Home returns to the introduction.
- [ ] Repeat with the mission clock. It counts up without time penalties and stops on Home/completion. The game continues beyond 30 minutes.
- [ ] Test at 360px, 390px, 768px and desktop widths. Check portrait/landscape and 200% zoom. Dialogs scroll, controls remain usable, and tables/answers are readable.
- [ ] Tab through controls; confirm visible focus, keyboard answers, Continue, Escape and return focus. Confirm reduced-motion preference removes movement transitions.
- [ ] Repeat a brief test at the final GitHub Pages project URL to verify relative CSS/JS paths.

Teaching use: ask students to explain one corrected misconception after play. Treat this as formative practice, not a secure examination: the answer bank is visible in browser source.
