# Flat 1 Poker

A hand tracker for the Flat 1 home game: AD, Ollie and Owen, with £0.10 / £0.20 blinds.

It's a single file (`index.html`) with no build step and no server, so it runs on GitHub Pages as-is.

## Put it online with GitHub Pages

1. On GitHub, create a new **public** repository, for example `flat1-poker`.
2. Choose **Add file → Upload files**, drop in `index.html` (and this README if you like), then commit.
3. Go to **Settings → Pages**. Under "Build and deployment", set Source to **Deploy from a branch**, Branch to **main** and folder to **/ (root)**, then save.
4. Wait a minute and refresh the Pages screen. Your link is shown at the top, usually `https://<your-username>.github.io/flat1-poker/`.

On a phone, open the link and use **Add to Home Screen** so it opens full screen like an app.

## How a hand works

1. The dealer button, small blind and big blind are set automatically, and the blinds are already posted.
2. For each player, enter the **total they put in this hand** by typing it or tapping +10p, +20p, +50p, +£1 or +£5. **Call** matches the highest amount so far, and the undo arrow reverses that player's last change.
3. Tap **Fold** for anyone who folded. If only one player is left, they're picked as the winner automatically.
4. Tap who won. Turn on **Split pot** to pick more than one winner. Odd pennies go to whoever sits nearest the dealer's left.
5. Tap **Record hand**. The pot goes to the winner and the button moves on.

You can type amounts like `1.50`, `£1.50` or `50p`.

## Blinds and sitting out

- The button moves one seat clockwise each hand (AD → Ollie → Owen by default, and you can change the order in Settings).
- Three-handed: the player left of the dealer posts the small blind and the next player posts the big blind.
- Heads-up: the dealer posts the small blind and the other player posts the big blind.
- Use the **Sit out** menu to take someone out. The blinds skip them and carry on in the normal order when they come back.
- You can choose a different dealer for one hand from the **Dealer** dropdown. "Back to normal rotation" undoes that.

## Fixing mistakes

- **Undo** on the toast that appears after recording, or **Undo last hand** in the history, puts the hand back in the editor.
- Tap any hand number in the history to edit the amounts or the winner, or to delete the hand.

## Settling up

**Who owes who** shows the fewest payments needed to square everyone up. **Share summary** sends the results to your group chat. At the end of the night, use **⋯ → Start new session** to save the session under Past sessions, and see the all-time totals there.

## Your data

Everything is saved in the browser on the device you're using, and it survives refreshes and closing the tab. It isn't synced between phones, so run the game from one device.

- **Save backup file** downloads everything as a `.json` file.
- **Restore from backup** loads that file back, on the same device or a different one.
- **Export hands (CSV)** gives you a spreadsheet of every hand.

Clearing your browser's site data deletes the saved hands, so save a backup now and then.
