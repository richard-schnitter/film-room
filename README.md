# Film Room

A film-study tool for ultimate frisbee teams. Break down YouTube footage together: tag clips, draw on frames, build highlight reels and scouting reports.

**Open it:** https://richard-schnitter.github.io/film-room/

## What it does

- **Three sections:** Opponents (scouting), Our team (self-scout: clips marked *to fix* or *good example*, per-player feedback reels) and Tactics (any other footage worth learning from).
- **Tagging:** `I` / `O` mark a clip (**Cancel clip** or `Esc` throws it away), then tag it (their O or D, stack, force, zone, huck, line ratio…), add players, a priority and a note.
- **Drawing:** `D` pauses on the frame. Draw cuts, throws, zones and O/D markers. Playback stops on drawings so everyone sees them.
- **Team notes:** anyone can add general notes to a team (how they play in wind, who their captains are, what the coaches said). Each note shows who wrote it and when, and they appear in the copied report. Long notes show the first few lines; tap one to expand it, and tap **Notes** to fold the whole list away. **Voice notes:** in *Add note*, upload a voice note a friend sent (WhatsApp .opus, .m4a, .mp3 and so on) and it is turned into text right on your phone or laptop, free. Afrikaans voice notes become an English note, with the Afrikaans kept underneath; pick **Best** on a laptop for Afrikaans, since the phone-sized models are weak at it. The audio is saved with the note (up to 4 MB) and anyone on the team can press **Listen**.
- **Watching:** ±1, ±5 and +20 second jumps, the arrow keys jump 10 seconds, and **CC** turns on subtitles (YouTube's auto-generated ones when the video has no others). YouTube does not let other sites set the picture quality, so **Quality** (the gear on phones) switches to YouTube's own controls: pick the quality from its gear menu. Keep it on while watching, since turning it off resets the quality.
- **Team profiles:** tap a team's name (or **Profile**) to see everything on them in one place: the game plan, every note in full (with any Afrikaans original and the voice note to listen to), what they get tagged for (tap a tag to watch just those clips), their players and their games. **Full screen** spreads it across the whole screen in columns; `Esc` or **Exit full screen** goes back.
- **Player profiles:** everything on one player in one place: tendencies, strengths, weaknesses, how to stop them, what they get tagged for most, and every clip across all games. *Follow while watching* tags every new clip with that player during a deep dive.
- **Highlight reels:** filter by team, player, tag or priority and play only those clips back to back. Each clip's note and who wrote it show across the top of the video and in the *Playing* box.
- **Reports:** per-team summaries. Tap any timestamp or note to play that moment in the video. The copied report has links that open YouTube at the right second.
- **Team sync:** with a Firebase project configured, everything anyone tags appears for the whole team live. Everyone tags the same games, and *Whose clips* shows one person's markers or everyone's. Without Firebase, use Export / Import to swap notes.
- **Phones:** tabs at the bottom, the video stays pinned while you scroll the notes, and big buttons throughout. **Full screen** works on iPhone and Android: turn the phone sideways, tap to show or hide the controls, double-tap the sides to jump 5 seconds, drag the timeline to scrub, and mark clips or draw without leaving full screen. It can also be added to the home screen as an app.

## Who can see the notes

Everyone signs in with Google; there is no other way in. The link is the same for the whole team (https://richard-schnitter.github.io/film-room/) and opens a sign-in page. The organiser (whoever started the room) presses **Team** and adds each teammate's Google email. After that, the teammate signs in and lands straight in the team's film. Someone whose email is not on the list sees "no team has added you yet" and can copy their email to send to the organiser. Removing someone from the list locks them out. Nothing the team tags is ever deleted from the database; removed clips are marked as removed.

## Setting up live team sync

1. Create a Firebase project with a Firestore database.
2. In Authentication, turn on the **Google** sign-in provider and add the site's domain under **Authorized domains**.
3. Publish the rules in [`firestore.rules`](firestore.rules) as the Firestore rules. Publish them again whenever that file changes.
4. Paste the project's web config into `FIREBASE_CONFIG` in `index.html`.
