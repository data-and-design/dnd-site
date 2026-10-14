---
layout: class
class_id: 4871
title: "Assignment 3: Non-Visual Design | INFO 4871"
description: "INFO 4871 Assignment 3"
---

[Assignments](../) / Assignment 3

# Assignment 3: Non-Visual Design

**Checkpoint 1 due Wednesday, October 28. Checkpoint 2 due Wednesday, November 4. Checkpoint 3 due Wednesday, November 11. Teams of two or three.**

Most screen reader interfaces on the internet, when they are accessible at all, are usually designed by retrofitting screen reader attributes onto an existing visual structure. In this assignment, you will design a non-visual interface from the ground up. The goal of this assignment is to think about usability from a non-visual perspective, and how to think about the affordances of speech and audio (which are not always the same as visual affordances).

## Recreating a shopping flow

Every team will build a non-visual interface for two pages within an online shopping flow. These pages are (1) a search results page (the list of products returned by a query such as "wireless headphones" or "running shoes"), and (2) a product detail page, which shows the full information for a selected product from the list of search results.

Pick your favorite real-world shopping website and run a search on it. Use the results / products listed and recreate that page in your non-visual prototype.

The search results should list products with metadata for each result, which could include things like: title, price, star rating, review count, delivery estimate, and badges such as "sponsored" or "best seller." Each result should open onto a product detail page, which might includes fields like: title, description, a variant selector for size or color, and a list of reviews.

Unless the site you chose has extremely good accessible design (in which case, you might learn more if you choose a different one), the default screen reader experience might be *technically* accessible yet still not a very good experience. For example, maybe you have to tab through all of the information in one search result before you can even get to the next one, even if you can tell from the title that it's not the product you're looking for.

This assignment asks you to design across three dimensions: structure, navigation, and description.

**Structure** — how information is grouped together into a hierarchy and organized into a format the screen reader can traverse

**Navigation** — the ways a user can move around in the structure, whether that's moving to adjacent content or jumping to important landmarks

**Description** — what information the screen reader announces at each location, in what order, and how concise or verbose it is

## Part 1: Prototype and Sketch (Checkpoint 1, due October 28)

Before you implement anything, sketch your interface's structure, navigation, and description on paper. For example, you can draw a diagram of the structure, list out the keyboard interactions that define the navigation, and write a script for what gets announced at each location.

Consider these questions as you prototype:

### Structure

- What structure is the visual hierarchy conveying, and should the non-visual structure match it?
- How should information be grouped together? Are there multiple pieces of information that describe the same entity?
- What tasks might people be trying to accomplish using this interface?
    - Write down specific questions a real user would want answered: "Which of these ship by Friday?", "Is the blue one in stock in a medium?", "Which result has the most reviews?" Questions like "What does the page show?" do not count.

### Navigation

- From each location, where can the user go? And what key(s) do they press to get there?
- For the user task questions you wrote down in part 1, is there a way to answer all of them? Are some of them easier or harder to answer? (It's not always possible to make every task equally easy to accomplish.)
- How does a user jump between two places that are not adjacent, such as two results at opposite ends of the list?

### Description

- What gets described at each location, and in what order?
- What can a user request on demand instead of receiving automatically? (e.g. by expanding summary/detail for additional info)
- Is there anything you are deliberately leaving out of the non-visual version, and why?


## What to submit

**Design document** covering structure, navigation, and description
    - Include your sketches or early prototypes.
    - For each design dimension, discuss: what choices did you make and why? What alternatives did you consider and why did you reject them?

## Part 2: Build (Checkpoint 2, due November 4)

Implement the design as a web interface that you can test with a screen reader.

**At the November 4 checkpoint**, a running prototype that can be tested. The prototype does not have to be perfect or finished, but there should be a first complete draft of a structure, navigation, and description.

Build your prototype with the [starter template](https://github.com/data-and-design/info-4871-a3-template). In the template, you will write your design as a list of nodes. Each node is one item a screen reader user can move to, and specifies the description the screen reader will there. The template renders your nodes into a webpage with keyboard navigation.

### 1. Get the template

Clone the repository, or download the ZIP and unzip it.

```
git clone https://github.com/data-and-design/info-4871-a3-template.git
```

OR

Download the zip file by going to [the repository](https://github.com/data-and-design/info-4871-a3-template), clicking the green "Code" button, and clicking the "Download ZIP" link at the bottom of the menu.

### 2. Install Node.js

The template runs on Node.js version 22.12 or higher. macOS users should open Terminal. Windows users should open PowerShell. Then type:

```
node --version
```

If the command prints a version number of 22.12 or higher, such as `v24.11.0`, Node is ready and you can go to step 3. If you installed Node for Assignment 2, you should be good to go, but check the version anyway just in case.

If the command shows `command not found`, or prints a version lower than 22.12, download the LTS installer from [nodejs.org](https://nodejs.org/) and run it. Then quit the terminal, open it again, and check the version again.

### 3. Start the app

`cd` to the folder where you cloned or unzipped the template. For example, if the folder is at `~/jzong/code/info-4871-a3-template`, run:

```
cd ~/jzong/code/info-4871-a3-template
```

Tip: you can drag the folder from Finder or File Explorer onto the terminal window to paste the path to that folder.

Then run these two commands:

```
npm install
npm run dev
```

`npm install` downloads the code libraries the template needs. You only need to run it once. `npm run dev` starts the app and prints an address, usually `http://localhost:5173`. Open that address in your browser.

Leave the terminal window open while you work, because closing it stops the app. Each time you save a file, the page in the browser reloads with your change. Press Ctrl-C in the terminal to stop the app, and run `npm run dev` again to restart it.

### 4. Try the starter version

The template starts with a working copy of a sample shopping site's two pages. Before you change anything, try it with the keyboard:

- Make sure focus is on the description (tab or click into it).
- Use the Down arrow to go into a group, the Up arrow to go back out, and the Left and Right arrows to move between items in the same group.
- Press Enter on a search result to open its product page. Press Backspace on a product page to go back to the search results.

You can also try it with a screen reader. See [this documentation](https://umwelt-data.github.io/olli/using/) for screen reader-specific configuration.

### 5. Add your products

Open the template folder in a code editor, such as [Visual Studio Code](https://code.visualstudio.com/). Open `src/data.js` and replace the two sample products with the search results from the shopping site you chose. You don't have to copy every single result from the real page, but copy as many results and fields as you need to communicate your design in a realistic way.

### 6. Build your design

Edit these two files: `src/pages/results.js` for the search results page, and `src/pages/product.js` for the product page. Each file marks the lines to change with `EDIT BELOW THIS LINE` and `EDIT ABOVE THIS LINE`. Leave the rest of each file, and every other file in the template, unchanged.

Each node in those files has up to four fields:

```
{
  id: 'aurora-anc',
  description: 'Aurora ANC Wireless Over-Ear Headphones',
  children: ['aurora-anc-price', 'aurora-anc-rating'],
  navigation: { Enter: 'aurora-anc-page' },
}
```

These fields match the three dimensions of your Part 1 design:

- **Structure** is the `children` list. It contains the ids of the nodes grouped inside this node, in order. Arrow key navigation uses these lists (left/right to move between siblings, up/down to move between parents/children).
- **Description** is the `description` text. The screen reader reads this text when the user reaches the node.
- **Navigation** is the arrow keys plus the `navigation` list of extra keys. Each entry maps a key to the `id` of a node to jump to when that key is pressed.

Work in small steps. Change one thing, save the file, and check the page. You can check your descriptions by reading the page on screen, but test with a screen reader before submitting, because screen readers add additional output to the description.

## What to submit

**Code** either as a zip file, or a link to a deployed version (e.g. on Github pages).

## Part 3: Test and revise (Checkpoint 3, due November 11th)

Give your user task questions and your interface to a classmate from another team. They will work through it with a screen reader and try to answer the questions. Write down which questions they were able to answer and which they could not answer (or answered incorrectly). Iterate on your prototype based on this feedback, and write down what you changed and why.

We will reserve some time for this in class.

## What to submit

**Notes on peer user testing and revisions**, answering:
    - What was an interesting or unexpected moment during testing that you learned from?
    - What did you change about your prototype in response, and how does that change address what happened in testing?


## Rubric

This assignment is worth **10 points**, divided across the criteria below. Each criterion is graded from its full point value (excellent) down to 0 (not present), with partial credit in between.

| Criterion | Points | Description |
|---|---|---|
| **Structure** | 2 | Sketches and prototypes address structure, the user task questions are specific and answerable |
| **Navigation** | 2 | Navigation is fully specified in sketches and prototypes |
| **Description** | 2 | Descriptions are specified and choices about what to include in which order are justified |
| **Build** | 2 | Prototype runs and has enough detail for testing |
| **Testing and revision** | 2 | Written reflections and specific revisions from peer user testing |

---

Previous: [Assignment 2: Accessibility Auditing and Remediation](../a2/) · Next: [Final Project](../final/)
