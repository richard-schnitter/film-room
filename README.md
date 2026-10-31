# Film Room

A film-study tool for ultimate frisbee teams. Break down YouTube footage together: tag clips, draw on frames, build highlight reels and scouting reports.

**Open it:** https://richard-schnitter.github.io/film-room/

## What it does

- **Three sections:** Opponents (scouting), Our team (self-scout: clips marked *to fix* or *good example*, per-player feedback reels) and Tactics (any other footage worth learning from).
- **Tagging:** `I` / `O` mark a clip, then tag it (their O or D, stack, force, zone, huck, line ratio…), add players, a priority and a note.
- **Drawing:** `D` pauses on the frame. Draw cuts, throws, zones and O/D markers. Playback stops on drawings so everyone sees them.
- **Team notes:** anyone can add general notes to a team (how they play in wind, who their captains are, what the coaches said). Each note shows who wrote it and when, and they appear in the copied report.
- **Watching:** ±1, ±5 and +20 second jumps, the arrow keys jump 10 seconds, and **CC** turns on subtitles (YouTube's auto-generated ones when the video has no others). YouTube chooses the picture quality itself, based on the player's size and the connection, so full screen gives the sharpest picture.
- **Player profiles:** everything on one player in one place: tendencies, strengths, weaknesses, how to stop them, what they get tagged for most, and every clip across all games. *Follow while watching* tags every new clip with that player during a deep dive.
- **Highlight reels:** filter by team, player, tag or priority and play only those clips back to back.
- **Reports:** per-team summaries with timestamp links that open YouTube at the right second.
- **Team sync:** with a Firebase project configured, everything anyone tags appears for the whole team live. Everyone tags the same games, and *Whose clips* shows one person's markers or everyone's. Without Firebase, use Export / Import to swap notes.
- **Phones:** tabs at the bottom, the video stays pinned while you scroll the notes, and big buttons throughout. **Full screen** works on iPhone and Android: turn the phone sideways, tap to show or hide the controls, double-tap the sides to jump 5 seconds, drag the timeline to scrub, and mark clips or draw without leaving full screen. It can also be added to the home screen as an app.

## Who can see the notes

Each team gets a private room. Everyone signs in with Google. The invite link only lets someone *ask* to join: the organiser (whoever started the room) sees each request under **Team** and taps **Let in**, and can remove anyone later. Someone who is not let in, or not signed in, cannot read or write anything, even with the link. Nothing is ever deleted from the database; removed items are marked as removed.

## Setting up live team sync

1. Create a Firebase project with a Firestore database.
2. In Authentication, turn on the **Google** sign-in provider and add the site's domain under **Authorized domains**.
3. Publish the rules in [`firestore.rules`](firestore.rules) as the Firestore rules.
4. Paste the project's web config into `FIREBASE_CONFIG` in `index.html`.
