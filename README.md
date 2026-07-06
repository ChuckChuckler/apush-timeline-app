# APUSH Timeline App
This is a simple APUSH practice app with many events spanning from the 1600s-1900s!

## Features:
- Learn mode: Similar to kahoot or gimkit-- you'll get a term, and you'll have to pick the option out of the four that defines it.
- Practice mode: The original!! You will see a term, and you'll have to classify it into the correct decade.

![The main homepage of the web app, with a settings page where the user can pick which years they'd like to study and which study mode they'd like to do.](/readme-images/homepage.png)
![The learn mode of the web app, similar to a multiple-choice quiz](/readme-images/learn.png)
![The practice mode of the web app, where users sort events into the years they happened in](/readme-images/practice.png)

## How to use
- Choose learn or practice mode from the "practice type" settings.
- Check which decades you'd like to study. You can check the box for a century to test all events from that century, or press the "expand/close" button to view specific decades.
- Once you've chosen what you want to study, just press the "Go!" button and you can get started!

### Learn mode
- A term will be at the top of the screen. You will be presented with four definitions. Pick the definition you think goes with the term. If you're correct, it will turn green; if you're incorrect, it will turn red, and the correct answer will be highlighted.
- You can check your score at the top right.
- You can go back to the settings page with the button at the top left. Learn mode will continue indefinitely until you decide to stop.

### Practice mode
- A term will be at the top of the screen. Pick the box with the decade you think that term belongs in. Another term will take its place-- continue until the "show results" button appears at the top of the screen.
- To switch the placement of a term, click the term that you've already placed down and place it where you think it belongs. You can do this as many times as necessary. You will be able to switch terms even if the "show results" button is visible (as long as you don't press it)
- When you click the "see results" button, terms placed correctly will be highlighted in green, and those placed incorrectly will be highlighted in red.
- Click "see correct placements" to see where those incorrect terms actually belong. Click "see incorrect placements" to see your own placements.
- Click "return home" to return to the settings page.

This web app works best on Chrome. It's a little funky on Firefox-- it still works, just not as well. For example:
- You have to deselect and reselect all terms you want to study every time you go back home and retry or select a different mode. You do not have to do this on Chrome.
- "Show correct placements" can sometimes bug out and not let you see your own placements again.

## Run locally
Open your terminal and navigate to where you'd like to save the repo.

```git clone "https://github.com/ChuckChuckler/apush-timeline-app"```

```cd apush-timeline-app```

```cd timeline-app```

```npm install```

Wait for installation, then run ```npm run dev``` and navigate to the given localhost



