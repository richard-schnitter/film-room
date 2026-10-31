# Film Room

A film-study tool for ultimate frisbee teams. Break down YouTube footage together: tag clips, draw on frames, build highlight reels and scouting reports.

**Open it:** https://richard-schnitter.github.io/film-room/

## What it does

- **Three sections:** Opponents (scouting), Our team (self-scout: clips marked *to fix* or *good example*, per-player feedback reels) and Tactics (any other footage worth learning from).
- **Tagging:** `I` / `O` mark a clip, then tag it (their O or D, stack, force, zone, huck, line ratio…), add players, a priority and a note.
- **Drawing:** `D` pauses on the frame. Draw cuts, throws, zones and O/D markers. Playback stops on drawings so everyone sees them.
- **Player profiles:** everything on one player in one place: tendencies, strengths, weaknesses, how to stop them, what they get tagged for most, and every clip across all games. *Follow while watching* tags every new clip with that player during a deep dive.
- **Highlight reels:** filter by team, player, tag or priority and play only those clips back to back.
- **Reports:** per-team summaries with timestamp links that open YouTube at the right second.
- **Team sync:** with a Firebase project configured, everything anyone tags appears for the whole team live. Without one, use Export / Import to swap notes.

## Turning on live team sync

1. Create a Firebase project with a Firestore database.
2. Use these Firestore rules:

   ```
   rules_version = '2';
   service cloud.firestore {
     match /databases/{database}/documents {
       match /rooms/{room}/{coll}/{id} {
         allow read: if room.size() >= 20;
         allow create, update: if room.size() >= 20
           && coll in ['teams', 'players', 'games', 'clips', 'meta'];
       }
     }
   }
   ```

3. Paste the project's web config into `FIREBASE_CONFIG` in `index.html`.

Each team gets a private room. Only people with the invite link can open it. Nothing is ever deleted from the database; removed items are marked as removed.
