# How I made this

Nestlife is a family planner in one HTML file. I built it with Claude. This is how the work was split, what broke, and what still needs a person.

## 1. The problem

Back in 2015, I was in business school, interning at Deloitte, with a toddler at home. I ran all of it out of a 365-page planner.

This is the tool I wish I'd had then. It's for anyone in a similar spot.

The version I'm sharing has three limits:

- One HTML file, so anyone can open it, copy it or host it.
- No account, and the app doesn't upload what you type.
- A demo people can play with before they decide whether they want the code.

## 2. How I split the work

| Handled by rules | Drafted by AI | Needs a person |
| --- | --- | --- |
| Repeating dates and due dates | Fixes to the demo and its phone layout | Deciding what to build and who it's for |
| Combining grocery items and sorting by aisle | The README and this page, from my notes and the project history | Choosing to make it free, and what stays private |
| Star totals, sleep hours and budget sums | Test steps, and the checks that found the bugs below | Trying it on a real phone, in a real week |
| Merging backups: the newest edit wins | The image shown when the demo link is shared | Confirming every claim on this page is true |

There is no AI inside the app. AI helped make it, but the planner itself runs on ordinary rules, so the same entries always give the same result.

## 3. What I used

| Tool | What it did |
| --- | --- |
| Claude | Wrote and tested the changes described here; the planner started as a Claude artifact |
| GitHub | Holds the code and this page |
| Netlify | Hosts the demo |

## 4. The steps and prompts

I started by asking Claude to help me build a second brain, with the sections Nestlife has now.

The later prompts were short. These are real, lightly trimmed:

1. **"I need this to be on the git repo."** Claude compared the artifact with my local copy, flagged that a public repo would give the whole app away, and set up a private one.
2. **"I have this hosted on Netlify. What next? Guide me."** Claude tested both live sites and came back with a list of problems instead of a launch plan.
3. **"I make a post on LinkedIn. It redirects people to the demo. Comment if you need the git repo."** That changed the goal, so the advice changed with it: make it free, open every section, add a license.
4. **"Yes, make it free."** Claude removed the locked screens and shop links, added a link preview, moved the phone menu and retested it.

The lesson: say what the thing is for. The list of problems barely changed between steps 2 and 3, but which ones mattered did.

## 5. What went wrong

**The demo's locks weren't real.** Locked sections were hidden by one setting, but their code was still in the page. Anyone who read the page source could find it. Comparing the demo with the full version showed that the setting was the only meaningful difference. Making it free solved that.

**The host covered the menu.** On a phone-sized screen, Netlify's badge sat on top of Add, Grocery and More. It only showed up when Claude checked what a tap would hit, because the page loaded without errors.

**A fix broke something else.** When Claude removed the locks, Quick add still called the code that was gone, and would have crashed. Searching for leftover references caught it before release.

## 6. How I knew it was good enough

| Check | Result |
| --- | --- |
| Open all 39 sections | No errors |
| Tap all five phone menu buttons at 375 px wide | Work on the live demo, with Netlify's badge showing |
| Add an entry in the demo | Not saved, as intended |
| Turn the demo off, add an entry and reload | Still there |
| Search the code for upload calls | None found |
| Use the planner on a real iPad | Two weeks of family use, before this demo version |
| Try the demo's menu on a real phone | All five buttons work |
| Use it on both iPhone and Android | Not done yet |
| Export a backup and import it | Not done yet |
| Independent security review of the vault | Not done |

Claude ran the checks that have results, apart from the iPad and the phone, which were mine. I've had the planner on our family iPad for two weeks, and it's been an absolute lifesaver.

**My bar: it had to be private and not connected to the internet.** Here's how that holds up:

- **Your own copy:** open the downloaded file in a browser on a computer, and it has nothing to fetch from the internet. The code has no upload calls and loads no outside scripts, fonts or images.
- **The demo:** it's a website, so it needs the internet to load, and Netlify adds its own badge script. Nothing you enter is saved, but please don't type anything private into it.
- **A copy you host:** entries stay in your browser, but the page comes from your host, which may add scripts of its own.

## Try this on your own idea

1. Write down what happens today, step by step.
2. Mark each step: rule, AI draft, or human check.
3. Build the smallest version someone can use.
4. Decide what it must get right before anyone relies on it.
