---
layout: default
title: The Validator
---

# The Validator (AKA the react app)

The main goal of the validator is to provide a frontend for reviewing (editing and approving) scores.

It's built in TypeScript on the React framework.

## Instructions

At week starts after posting the topic on the forum please go to: (example)

https://rocksmith-cf-champ-assistant.web.app/scores/601 <----- (new weeks #)

Enter url of page 1 of the new week https://customsforge.com/index.php?/topic/80013-rocksmith-2014-championship-week-601/

(the last / is needed also)

Then the app will start to fetch scores at the triggered times.

## Correcting a score

If the score is marked **PUSHED**, select **Remove Pushed** to make it editable. Select **Edit**, correct the values, and save. The **Results** table shows the saved streak, including when you copy the table for statistics.

The official weekly leaderboard is updated separately by Google Apps Script. If a correction lowers a result already on the leaderboard, check the corresponding row in the weekly sheet. The import can skip the lower result when comparing it with the existing row.
