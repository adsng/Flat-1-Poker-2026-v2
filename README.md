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
2. For each player, enter the **total they put in this hand** by typing it or tapping +10p, +20p, +50p or +£1. **Call** matches the highest amount so far, and the undo arrow reverses that player's last change.
3. Tap **Fold** for anyone who folded. If only one player is left, they're picked as the winner automatically.
4. Tap who won. Turn on **Split pot** to pick more than one winner. Odd pennies go to whoever sits nearest the dealer's left.
5. Tap **Record hand**. The pot goes to the winner and the button moves on.

You can type amounts like `1.50`, `£1.50` or `50p`.

## All in and side pots

When someone goes all in for less than the others and the others keep betting:

1. Enter what the all-in player put in, and tap their **All in** button.
2. Enter the totals for everyone else as normal.
3. The app splits the money into a **main pot** (everyone can win it) and one or more **side pots** (only the players who put in enough can win them). Money from players who folded goes in too.
4. Tap who won the main pot. Each side pot goes to the best hand still in it. If the main pot winner is in a side pot, they take that too. If not, pick who won the side pot.
5. Any bet nobody called goes straight back to the player who made it.

If a player still in the hand put in less than the others and isn't marked all in, the app asks whether they folded or went all in, with a button for each, before it lets you record the hand.

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

Everything is saved in the browser on the phone you're using, and it survives refreshes and closing the tab. To keep it safe in the cloud, open **⋯ → Cloud backup**. There are two ways.

### 1. Save a backup to iCloud Drive or Google Drive (no setup)

- Tap **Save backup**. On iPhone, choose **Save to Files**, then **iCloud Drive** (or Google Drive if you have the Drive app). On Android, choose **Drive**.
- To get it back on any phone, tap **Load a backup** and pick the file from iCloud Drive or Google Drive.

On Android the file may save as `.txt` instead of `.json`. That's normal, because Android only lets websites share certain file types. Both load fine.

### 2. Automatic Google Drive sync (one-time setup, about 10 minutes)

Once it's set up, the app saves to a file called **Flat 1 Poker data.json** in your Google Drive after every hand. Any phone you connect picks up the latest games. The status next to the blinds shows **Saved to Drive** when it's up to date.

Google asks you to sign in again about once an hour. When that happens the status says **Drive: tap to sync**. Tap it, and Google sends you straight back. Nothing is lost while you wait, because everything is still saved on the phone.

If two phones both change the games before syncing, the app asks which version to keep.

**Setup, step by step.** Do this on a computer if you can, as the Google Cloud website is fiddly on a phone.

1. Go to **console.cloud.google.com** and sign in with the Google account whose Drive you want to use. Accept the terms if asked.
2. **Create a project.** Click the project picker at the top of the page, then **New project**. Name it `Flat 1 Poker` and click **Create**. Make sure it's selected in the project picker afterwards.
3. **Turn on the Google Drive API.** In the search bar at the top, type `Google Drive API`, open it, and click **Enable**.
4. **Set up the sign-in screen.** In the search bar, type `Google Auth Platform` and open it, then click **Get started**.
   - App name: `Flat 1 Poker`. User support email: your email. Click **Next**.
   - Audience: choose **External**. Click **Next**.
   - Contact information: your email. Click **Next**.
   - Tick the agreement and click **Create**.
5. **Add yourself as a test user.** Still in Google Auth Platform, open **Audience**. Under **Test users**, click **Add users**, enter your Gmail address (and the address of anyone else who'll connect a phone), and click **Save**.
6. **Create the client ID.** Open **Clients**, then **Create client**.
   - Application type: **Web application**. Name: `Flat 1 Poker`.
   - Under **Authorized JavaScript origins**, click **Add URI** and enter `https://YOUR-USERNAME.github.io`, with no slash or folder at the end.
   - Under **Authorized redirect URIs**, click **Add URI** and paste the address shown in the app under **⋯ → Cloud backup → Address to add in Google Cloud**. It looks like `https://YOUR-USERNAME.github.io/flat1-poker/` and must match exactly, including the slash at the end.
   - Click **Create**.
7. **Copy the Client ID.** It ends in `.apps.googleusercontent.com`. You don't need the client secret.
8. **Connect in the app.** Open your site, go to **⋯ → Cloud backup**, paste the Client ID, and tap **Connect Google Drive**. Pick your Google account.
   - Google will say **"Google hasn't verified this app"**. That's expected for a personal app like this. Tap **Continue**, then allow access.
   - You're sent back to the app, and it says **Saved to Drive**.
9. **On other phones,** open the same link, paste the same Client ID, and connect with a Google account on the test users list. Any games already in Drive load automatically.

**Optional:** to skip pasting the Client ID on every phone, open `index.html` on GitHub, click the pencil icon, find `var GOOGLE_CLIENT_ID = '';`, put your ID between the quotes, and commit.

The app can only see files it created itself, so it never sees anything else in your Drive.

**If it doesn't work:**
- *"redirect_uri_mismatch"*: the address in step 6 doesn't exactly match the one shown in the app. Copy it again from the app.
- *"Access blocked" or "access_denied"*: the Google account isn't on the test users list (step 5).
- *"Turn on the Google Drive API"*: redo step 3, then wait a minute.

### Other options

- **Export hands (CSV)** gives you a spreadsheet of every hand.
- Clearing your browser's site data deletes the copy on that phone. A backup or Drive sync keeps it safe.
