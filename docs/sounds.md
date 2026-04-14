# Sound Design

Audio system used in the CS2 Case Opening Simulator.

---

## Case Opening Sequence

| Sound | When It Plays | Description |
|-------|---------------|-------------|
| `csgo_ui_crate_open.wav` | Case opening starts | The initial "unlocking" sound |
| `csgo_ui_crate_item_scroll.wav` | During wheel spin | Tick sound as items scroll past |
| `csgo_ui_crate_display.wav` | Wheel slows down | Transition to reveal |

### Item Reveal Sounds (by rarity)

| Sound | Rarity | Color |
|-------|--------|-------|
| `case_awarded_common.wav` | Mil-Spec / High Grade | Blue |
| `case_awarded_uncommon.wav` | Restricted / Remarkable | Purple |
| `case_awarded_rare.wav` | Classified / Exotic | Pink |
| `case_awarded_mythical.wav` | Covert / Extraordinary | Red |
| `case_awarded_legendary.wav` | ★ Rare Special Item | Gold |
| `case_awarded_ancient.wav` | Rare knives / gloves | Gold (special) |

### Item Interaction Sounds

| Sound | When It Plays |
|-------|---------------|
| `item_inspect_01.wav` | Clicking on an item to inspect |
| `item_drop1_common.wav` | Common item added to inventory |
| `item_drop2_uncommon.wav` | Uncommon item added to inventory |
| `item_drop3_rare.wav` | Rare item added |
| `item_drop4_mythical.wav` | Mythical item added |
| `item_drop5_legendary.wav` | Legendary item added |
| `item_drop6_ancient.wav` | Ancient item added |
| `item_reveal3_rare.wav` | Rare item reveal sparkle |
| `item_reveal4_mythical.wav` | Mythical item reveal sparkle |
| `item_reveal5_legendary.wav` | Legendary item reveal sparkle |
| `item_reveal6_ancient.wav` | Ancient item reveal sparkle |

### UI Sounds

| Sound | When It Plays |
|-------|---------------|
| `buttonclick.wav` | Button clicks, menu interactions |
| `case_drop.wav` | Case selection |
| `case_scroll.wav` | Scrolling through cases |
| `case_unlock.wav` | Case unlocked / key used |

---

All 24 sounds are from CS2's game files (extracted from VPK archives). They're included in the [`/sounds/`](../sounds/) folder of this repo.
