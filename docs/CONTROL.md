# Control

The dangerous habit in a system this flexible is letting a model invent the next action. Voice-to-shell looks like magic and fails like a hole. A compositor is a closed machine. A volume grant is a closed machine. An update is a closed machine. The model’s job is to pick, not to author.

Vikett is that discipline, already shaped for a desktop: every legal move is a **page** a human wrote. A snapshot of the world **prunes** the catalogue down to the doors that are open. A referee **takes** one page and fills its slots from lists that already exist — enums, notches, never a free-invented number or a free-invented path. A driver **walks**. Silence is a correct outcome.

Arachne keeps that shape and aims it at the whole web, not only at a window manager.

## The loop

```text
identity claims  +  site policy  +  live world
                 │
                 ▼
        catalogue of authored pages
                 │
                 ▼
              prune
                 │
                 ▼
     referee: exact match, else a typed choice
                 │
         ┌───────┴────────┐
         ▼                ▼
       a take           silence
         │
         ▼
   driver walks
         │
         ▼
   HoloFS volume still allowed to refuse
```

BuckyBoi can say who is speaking. It does not walk. GlassSpear can say which surface is in the room. It does not invent a layout that was never a scene. The application can publish the moves it knows how to perform. It does not receive a shell. The steward can propose a heal or an update only as a page the catalogue already contains.

## Where this sits

Identity says who you are and which claims you carry. The application's pages say what that application is capable of. The domain's policy says which of those capabilities are even legal here — guest, household, owner, a maintainer on a clock. Vikett is the interpreter between those three. It does not own the rules. The site owns the rules. Vikett applies whichever policy belongs to the surface you are touching.

The walk lands on a volume. That is the second interpreter, and it is stricter: storage does not trust the referee. A take that asks for a path the grant does not include does not happen, even if something upstream was wrong. This is the difference between a menu that *asks* the app to behave and a fabric that *will not serve* the bytes.

## Applications, privileged by specification

The usual container starts from almost nothing and punches holes. That is a good instinct and a bad daily experience, and it still trusts the workload with whatever was mounted in.

Arachne starts from a **specification**: the application declares the volumes, the talking-to-others, and the moves it needs. The declaration is signed. The domain verifies the signature, checks policy, and either mints a session or does not. The application then runs with that grant and no other. "Is it contained?" is the wrong question. "Was it authorized, and is the authorization still what is being enforced?" is the right one.

For software you ship, the specification can travel with the application. For software you do not, nobody has automated the honest version of "read the source and emit the lock." Static guesses miss what the program only does at runtime. A learning pass can watch a run and draft rules. The piece worth building is the merge of those two into one profile that does not over-grant — and only as a tool for applications you are willing to stand behind, not as a promise that every binary on the internet will grow a perfect policy by itself. Existing mandatory-access machinery can enforce a finished profile. It will not author one from a build, and Arachne should not pretend otherwise.

Old applications that only understand a filesystem get a familiar tree projected for them. Opens and reads are still checked. New applications do not share files to talk to each other. They use typed doors: each side named what it produces and what it consumes, and the bus only connects them when both grants match. The bus is itself just another volume with a protocol. One policy engine, two kinds of noun — bytes and messages.

The catalogue must stay small. A few dozen legal moves, pruned hard, is a selector. Hundreds of moves is a search engine, and search engines wander. If a desire does not fit a page, the answer is silence or a request that a human author a page. It is not a model writing a new page in the moment.

## Compound speech

"Switch to the film and make it full screen" is two takes. A generated script that does both in one breath is how you get actions the person did not quite ask for. Vikett already treats compound speech that way. The rest of Arachne should too: one authorized move at a time, even when the sentence was lazy.

Amounts are notches — a little, a lot, the next scene — not a model-chosen percentage. Slots are lists. "Set it to 37" when the list does not contain 37 is a refusal you can explain, not a guess.

## System moves are pages too

Launching is not the only walk.

| Kind of page | Examples | Who may see it after prune |
| --- | --- | --- |
| Scene | kitchen, guest mode, lock private | Whoever the room policy names |
| Application | open, save, talk to a named peer app | The person, inside that app's grant |
| Volume | lend, revoke, snapshot, step back | The owner of the volume; sometimes a delegate |
| Household | grant time, lock a child system, release a member | The parent domain, not the guest |
| Steward | stage an update, commit a boot, roll back, ask for a disk | The machine's owner, or a time-boxed maintainer |
| Identity | present a card, refresh a social copy, end a lease | The person, on a device that can prove them |

A maintainer does not get a shell because they are trusted. They get the steward pages their claim includes, for the hours the claim lasts. When the claim ends, those pages prune out. That is the same mechanism as a guest who cannot see mail.

## The referee

Exact wording can be matched without a model at all. Paraphrase is where a decision model earns its place: state in, a typed choice among the *live* pages out, no tokens that could be a command. It sees labels, not the driver, not the disk, not a raw compositor socket. If it is unsure, it stays silent. A wrong walk is worse than nothing.

This is the use of a System One model — a chooser, a scorer, a yes-or-no — not a writer. Generation remains available to people who are *authoring* pages and specifications, offline, with review. It is not on the path between a sentence and a side effect.

## What "root" means

Root is not a person and not a vibe. It is a claim a domain issues, and it only covers the moves that domain put in the owner or maintainer set. A person can be root on the interaction glass of their house and a guest on the servers of a building in the same afternoon, with the same identity record. The web feels continuous because the proof was continuous. The power is local because the catalogue was local.
