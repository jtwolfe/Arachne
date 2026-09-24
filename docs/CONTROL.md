# Control

Two catalogues. One shape. Only one of them exists as a project today.

**Vikett** is the control protocol for interaction. Legal moves are pages a person authored. A snapshot of the world prunes the catalogue to live doors. A referee takes one page and fills slots from enums. A driver walks. Silence is a result. Vikett does not emit a shell line, a compositor command it invented, or a path.

**The identity and rules tool** does not exist yet. Arachne requires it, and requires that it be built in Vikett's image rather than as role bindings, allow-lists of filesystem paths, or a model with a tool-use loop. Its catalogue is claims on the three spaces, and the maintenance and lend pages around them. It is not a mode of Vikett unless, later, someone deliberately makes it one. The concept keeps them apart so that choosing a scene cannot be the same code path as granting a volume, even though both code paths must feel the same to the person: either a thing that was always legal happens, or nothing does.

## Vikett's loop, unchanged

```text
who is asking, and what is true
            │
            ▼
    authored interaction pages
            │
            ▼
          prune
            │
            ▼
   lexical match, or a typed choice
   among the labels still live
            │
     ┌──────┴──────┐
     ▼             ▼
   a take        silence
     │
     ▼
 driver walks a driver that already existed
```

In Arachne the drivers are small and named:

| Take | Driver | Does not |
| --- | --- | --- |
| Change or apply a scene | GlassSpear | Mount storage |
| Application action inside a page | That application, inside its already-bound volume | Reach user space or OS space |
| A storage claim | Hand the typed claim to the rules tool | Talk to HoloFS itself |
| Something with no page | Nothing | Ask a model to write a page |

Compound speech is more than one take. "The writing, on the other glass" is two pages or it is silence. Amounts are notches the page defined. Slots are enums. A referee that emits text is the wrong referee. If a model is used, it is a decision model: the live labels in, a choice or a refusal out. It sees labels, never a socket.

Vikett's existing discipline stays: guests change the legal set, pixels are not pages, and an exact alias can be matched without a model at all. Paraphrase is the only reason to call a model, and a wrong walk is worse than silence.

## The rules tool, not yet defined

What Arachne specifies is the contract, not the program.

**Inputs.** A typed claim, as in [SPACES.md](SPACES.md). A person-proof or a machine-proof. The place. The live facts that pruning needs: is a person present, is this a guest session, is a maintenance window open, does this application already hold exclusive access, is Dialtone up, is the named snapshot still a snapshot.

**Catalogue.** Authored pages, at least:

- bind user space for this person in this place
- bind application space for a page id
- project a named user slice into an application page
- snapshot, step back, forget
- lend, revoke
- prepare an OS moment, commit it, abandon it

No page is created because an application requested a permission at runtime. New capability is a person editing the catalogue, then a later session pruning the new page in. That is the same rule Vikett uses for a new door in the house.

**Outputs.** Walk, deny, or silence. A walk is an instruction to HoloFS and, if the source is remote, to Harmonics, in that order of authority: no Dialtone session for a claim that is not being walked, no HoloFS bind for a session that failed, no mount returned to GlassSpear or to the application until HoloFS accepts.

**Non-outputs.** A shell. A path outside the volume. A new identity. A rewritten rule. An explanation the model composed and some other component is expected to execute.

The tool is the binder between identity and HoloFS. Vikett is the binder between a person's intent and drivers. GlassSpear is a driver and a source of "which page ids are on this surface." Harmonics is a driver for "the source is not local." HoloFS is the driver for "make this volume real and small."

## Why the tool is not Vikett

Vikett pages are things a person *does*: show, focus, stop, switch. Claim pages are things a session *is allowed to hold*. Mixing them would mean a successful utterance could carry a mount as a side effect of phrasing. The pattern is the same so that both stay auditable and closed. The catalogues are different so that interaction and authority can change on different clocks. You can add a scene without granting a volume. You can revoke a lend without changing how the glass is operated.

A later design may put both catalogues behind one implementation. Arachne does not require that, and it forbids either catalogue from growing entries by themselves.

## Rules are per place

The catalogue is not global. A home, a building, and a machine you own each have a catalogue. The person's proof is portable. The pages are not. Guest in a building means that building's prune, not a reduced copy of the person's home catalogue. Someone allowed to maintain a machine sees OS pages there and does not see them in a building that did not grant maintenance. The identity tool loads the catalogue of the place the surface belongs to. It does not ask the person's home to authorize the building.

## What "root" is

Root is not a user. It is the set of OS-class pages being live for this subject, in this place, now. It expires when the prune says those pages are gone. An application cannot inherit it. User space cannot contain it. There is no flag on a volume that means root, because OS space was never bound into the session that would read the flag.
