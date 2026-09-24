# HoloFS

HoloFS is how Arachne remembers. Not a folder on a computer you have to keep turned on. A **holo**: plug a disk in and capacity grows, unplug one and the holo continues, walk a disk to another machine and it is still the same holo.

That property is the storage half of the web. Compute can be wherever you are standing. The bytes do not have to be.

## What a person should feel

You do not know which disk a file is on. You should not have to. You know the name, and the name resolves. If a disk is dying, the holo asks for another one. If you take a disk to the other side of the house, or to another site, the holo catches up. Two places can see one namespace without becoming one fragile server.

Snapshots are ordinary. You can stand in a moment, change things, and step back. Clones share what they can. A volume can be handed to someone else for reading and later pulled back. None of this is a backup product. It is the filesystem behaving like the web: membership changes, identity of the content does not.

## Names, not places

Content is addressed by what it is. The same bytes are not stored twice under two filenames just because two applications saved them. A rename changes the directory, not the file's identity. That is what makes a snapshot cheap and a move between machines a matter of "which pieces are you missing," not "copy the world."

A delete, in the experience we want, removes the **name**. The bytes stay in the holo until something you trust decides they are old enough to forget. A bad application, or a tired person, does not get to make the only copy vanish. Forgetting is a separate, deliberate act — and even then, only for chunks nothing else still points at. Storage grows until that pass runs. That is a choice about how long the safety net is, not a leak.

Exactness is the default for anything you would be angry to lose. The holo is also allowed to know when a thing is allowed to be lossy — a sketch of a photo when too much is missing — and it must never quietly apply that mercy to an exact volume. The difference is declared by the volume, not guessed at read time.

## Volumes are the unit of trust

A holo is not one big home directory with Unix permissions sprinkled on top. The unit an identity and an application share is a **volume**.

- Your record lives in a volume you control.
- Each application that runs as you gets a volume sealed to that application and to you.
- A household might have a shared volume the domain policy can see.
- A lent volume is readable by someone else until you revoke the wrap. Revoke, and their side goes dark. You do not "hope they delete the copy" as the only control; the key they were given stops working.

The volume is where policy becomes physical. Vikett can choose a move, and the driver can try to walk it, and the volume can still refuse. Enforcement at the boundary means a confused referee is not the last line. This is the opposite of a mount that trusts whoever opened it.

Quotas are promises on a volume, not on a user account. One application filling its place does not fill your record, and does not fill the volume a different application owns.

## How this sits with the rest of the web

Dialtone is how a name finds the holo that should answer. The holo is not the packet path. Transmission of bulky bytes, when it is needed, is Overtone's kind of job: a cache you can ask, beside the session, not a middlebox that has to understand you. Dearr and anything like a personal library are clients of this. They catalogue and present. They do not become the mesh and they do not become the holo.

GlassSpear does not store the house inside a scene file as the only copy. A scene points at pages and at volumes. The scene can be rebuilt. The holo is what would hurt to lose.

Carrier's continuity pack is a *subset* you take into a visit: enough to rehydrate, not a live mirror of every volume. The phone is a poor place to be the only copy of a life. It is a fine place to be the key and the shopping list.

AIOS, on a machine, wants the machine's own definition to be reconstructible. The holo is a natural place for that history to live once the two are introduced — a snapshot you can boot back to, not a tarball on a spare disk. That meeting is later. The feeling, now, is that the machine and the files share one idea of "a moment you can return to."

## What we are not pretending

Today the holo can be reached as a filesystem in ordinary ways, including a projector when the kernel will not host it. Arachne does not require a custom kernel before the experience is allowed to be true. The long strengthening is a real filesystem in the kernel, so the hot path is not a guest in userspace. That work is large. It is not the first join. Metadata that can roll back, and volumes that can be sealed, already carry the experience we need while that work happens.

Per-application volumes are the storage change Arachne actually adds to the idea of the holo: not a new layout on disk for its own sake, but a place that exists *because an identity authorized an application*, and that disappears from the namespace when that authorization does.
