# Age of Rivalry Legal

Privacy policy and licence credits for **Age of Rivalry** (`com.goethe47.ageofrivalry`),
hosted as a static site so Google Play Console and the game itself can link to them.

## Publishing

Enable GitHub Pages for this repo (Settings → Pages → Source: `main` branch, `/` root):

```
https://goethe47.github.io/AgeOfRivalry-legal/
```

Use that URL as the **Privacy Policy** link in Play Console.

The game links to the same address from **Settings → Age and ads → Privacy policy**.
It is a constant in the game's source, `GameUI.PrivacyPolicyUrl` in
`Assets/Game/UI/ConsentUI.cs`. **If this site is published at a different address, that
constant has to change with it**, or the button in the game leads nowhere.

## Contents

- `index.html` — the privacy policy
- `licenses.html` — third-party data, fonts and software, with their licences
- `styles.css` — dark slate panels and gold rules, the game's own palette

## What these pages claim, and what has to stay true

The pages describe the build as it behaves today. Each of these is a fact about the
app, so if the app changes, the page changes first:

- **Two ad formats only** — a banner in the reserved strip at the **top** of the
  campaign screen, and rewarded video the player chooses. The privacy page states
  explicitly that there are **no full-screen advertisements**. Wiring the interstitial
  (`inter_campaign_end`) makes that sentence false.
- **One network** — Unity Ads through LevelPlay. Adding another adapter means a new
  entry under "Advertising", a new app version and a Data safety update.
- **No advertising before consent** — the SDK is not initialised until the age and
  advertising questions are answered. This is enforced by `Ads.Begin()` and covered by
  `ConsentTests`.
- **No advertising under 13**, and no personalised advertising under 18.
- **No in-app purchases.** If that ever changes, both this page and Data safety change
  with it.

## Play Console Data safety

The privacy page and the Data safety form have to agree. What to declare:

| Question | Answer |
| --- | --- |
| Does the app collect or share user data | Yes |
| Data type | Device or other IDs — advertising ID |
| Purpose | Advertising or marketing |
| Is it required | No, it depends on the player's consent |
| Is it shared with third parties | Yes, with the advertising network |
| Encrypted in transit | Yes |
| Can users request deletion | Yes — consent can be withdrawn in the game's settings |

Name, email, phone, location, contacts and files are **not** collected.

## Before this goes live

- [ ] GitHub Pages is enabled and both pages load.
- [ ] `GameUI.PrivacyPolicyUrl` matches the published address.
- [ ] The date at the top of both pages is the date you publish.
- [ ] Target audience in Play Console is set to 13+; a younger audience pulls the app
      under the Families policy, whose approved-SDK list Unity Ads via LevelPlay does
      not satisfy by default.
