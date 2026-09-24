# HoloFS

HoloFS is the storage base of Arachne. A running instance is a **holo**. Plug a disk in and capacity grows. Unplug one and, if the holo was told it must survive that loss, the bytes are still there. Walk a disk to another machine and the holo is still itself.

Arachne uses that as the pool underneath three isolated spaces: OS, user, and application. How a claim becomes a mount is [SPACES.md](SPACES.md). This document is what the holo itself is responsible for, and what it must refuse to become.

## What only the holo can do

**Membership.** Disks are members, not the filesystem. The holo heals, evacuates a dying member, and can ask for a replacement. A person does not choose which spindle holds a file. A claim does not name a disk. Class rules say how much loss is allowed. Exact OS space and exact user space do not quietly become sketches when a disk is missing. A class that was authored as lossy may. The difference is a property of the class, fixed before any claim.

**Content identity.** Bytes are addressed by what they are. A snapshot is a moment of the name tree, not a copy of every disk. A clone shares what it can. Rename changes the directory's identity, not the file's. This is why retain-on-delete is natural: removing a name drops a pointer. The content remains while any moment still references it. Forget is a later walk, and it can only drop content no moment still names.

**Volumes.** A volume is the thing a claim binds. It has a name inside the holo, a class, a quota, and a key. Quota is a promise on that volume. An application filling its volume does not fill user space and does not fill OS space. A lend wraps a volume's key for someone else, usually read-only. Revoke kills the wrap. The far side goes dark even if they kept the old handle. That is the holo enforcing the end of a claim, not a polite request to unmount.

**A boundary.** Once bound, a mount sees its volume. It does not see the holo's other volumes, the member disks, or the keys. Enforcement is at that edge. The rules tool can be wrong and the mount is still small. This is the property Arachne cannot get from a shared directory plus a policy daemon that applications are trusted to obey.

**Moments.** Snapshots and boot moments are the same idea at two heights. User space can step back. OS space can step back to the previous boot. Application space can be rebound to a snapshot if a page says so. The holo does not decide *when* a moment is taken. A page in the catalogue does, walked by the rules tool.

## What the holo is given, and what it will not decide

The rules tool hands HoloFS a claim that has already survived the catalogue and the prune. HoloFS then:

- creates a volume in that class, or binds one that already exists for that subject and role
- refuses if the class is not one it knows, if the subject does not match the volume's owner, if exclusive access is already held, or if the source snapshot or lend is dead
- returns a mount whose namespace is only that volume
- drops the mount when the session ends, without forgetting the volume

HoloFS does not:

- identify a person
- interpret a sentence
- know what a GlassSpear scene is
- open a Dialtone session on its own because a file was missing
- accept a path that points from one volume into another

If content must be fetched from another site, the rules tool asks Harmonics, and HoloFS consumes the result as a source: a snapshot arriving, a lend unwrapping, a member rejoining. The holo stays the store. Dialtone stays the session. Those roles do not merge.

## OS space on the holo

The machine boots a volume, not "the disk." OS space is that volume, exact, with at least two moments when an update path exists: the one you are in, and the one being prepared. Maintenance claims are the only writes. They are still claims. A maintenance take that fails does not leave OS space half-applied; the running moment stays the running moment until a commit page says otherwise.

People and applications never get this volume in their mount set. GlassSpear's runtime is a process on the machine. Its configuration may live in OS space. The pages it shows do not.

## User space on the holo

A person's documents are a volume (or a small set of volumes) keyed to them. The identity record is not sitting in that mount. It is a volume only the identity tool binds, so an application grant cannot edit who you are by editing a file.

User space moves the way any holo volume moves. Another site of the same holo can catch up. A desk that does not hold the disks can still be where the volume is *used*, if Dialtone can reach the who that holds the members and the claim allowed a remote source. The bytes are not copied into the glass "so it's faster" unless a page said to make a local moment. Convenience copies are how a place accidentally becomes the owner.

Delete, inside user space, removes the name. The moment before the delete is still a moment. Stepping back is a page, not a backup product.

## Application space on the holo

Each granted application gets a volume whose owner is the pair (person or place, application page), not the person alone and not the application alone. The same application for two people is two volumes. The same application in a shared scene, subject the place, is one volume the place owns.

An application that needs a document from the person does not open user space. A projection claim makes a volume, still class `application`, whose source is a named slice. The application writes the projection only if access included write. Closing the session unbinds both the private volume and the projection. Retain keeps the private volume for next time. The projection does not become a second copy of the person's life unless the page that created it said to snapshot it into application space.

Quotas stop one application from becoming the holo. Survival for application space is whatever the class was authored as. A scratch page may be lossy or short-lived. A writing tool's volume is exact. The application does not negotiate this at launch.

## Failure the holo is for

A disk leaves. Exact volumes in OS and user space still read, or the holo says it needs a disk. It does not serve zeros and call them the file.

A process crashes mid-write. The last committed moment of the volume is what the next mount sees. The holo does not resurrect a torn name as a file that half exists.

Two sites, one volume, two writers, when the class did not allow it. The holo keeps the conflict as a conflict. It does not pick a winner by clock. A page resolves it, or it stays unresolved.

A revoked lend. Reads fail. There is no offline cache that still decrypts, unless a separate claim explicitly made a snapshot the recipient was allowed to keep. That snapshot is a different volume, with its own end.
