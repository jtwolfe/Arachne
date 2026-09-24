# Spaces

Storage in Arachne is not a shared filesystem with permissions painted on afterwards. It is three kinds of space on a HoloFS holo. A running thing sees only the volumes that were **bound** for it. Binding is not a mount flag. It is a decision from an identity and rules tool that has not been defined yet, shaped like Vikett.

The nearest familiar picture is a PersistentVolume and a PersistentVolumeClaim. That picture is only for the storage relationship. Arachne is not a cluster, and the thing that says yes is not a role binding.

## The analogy, and where it stops

| Kubernetes | Arachne | What it means here |
| --- | --- | --- |
| Storage pool | The holo | Capacity is membership of disks, not a disk that "is" the filesystem. Pull one and the space remains if the holo was built to survive that. |
| StorageClass | A **class**: `os`, `user`, `application` | Class fixes survival, who may claim it, and whether the data is exact. It is not a performance tier with a marketing name. |
| PersistentVolume | A **volume** on the holo | A real, named body of content. It can be snapshotted, cloned, lent, and walked to another site of the same holo. It exists whether or not anyone has it mounted. |
| PersistentVolumeClaim | A **claim** | A typed request: this subject, in this place, wants this class, with this access, from this source. |
| Binding | A **walk** that succeeds | The rules tool allows the claim. HoloFS binds a volume to it. Until that happens there is nothing to mount. |
| Namespace | A **place** plus a **subject** | A house, a building, a machine. A person, or the machine itself. A claim in one place does not become visible in another because the bytes happen to be reachable. |
| Pod | A **session** | The OS session, a person's session, or one application inside that session. |
| volumeMount | The only tree that session can name | No bind, no path. Path traversal into another class is not a bug to be patched. The path is not there. |
| ReclaimPolicy Retain | **Retain** | Unbind or delete the name. Chunks stay in the holo while any snapshot still points at them. |
| ReclaimPolicy Delete | **Forget** | A separate, authored rule. Chunks with no remaining name may be dropped. |
| RBAC | Does not correspond | Authorization is a Vikett-shaped catalogue. See below. |

What the analogy must not drag in: a control plane you administer, a default service account, a cluster-admin that sees every volume, or dynamic provisioning that creates a volume because a string in a spec matched a class. Provisioning happens only when a page in the catalogue is live for this subject and a take walks it.

## Three classes

### OS space

The machine's own body.

OS space holds the boot volume, the system tree, and the moments the machine can return to. It is claimed by the machine, not by a person who happens to be standing at it. GlassSpear runs *on* a machine that already booted from OS space. It does not store itself in a user's volume, and a scene cannot name OS paths.

Properties:

- Bound before a person arrives, by the machine's own enrollment, not by a guest proof.
- Not mountable by a user session or an application session. There is no page that grants "just this one system file."
- Writable only by claims the catalogue calls maintenance: prepare the other boot moment, commit it, step back, ask the holo for a disk. Those are pages. They prune out for everyone except a subject the place has marked as allowed to maintain *this machine*.
- Exact. A lossy reconstruction is not acceptable for a root you boot.
- Retain by default. A bad maintenance take removes a name or abandons a moment. It does not erase the previous boot.

Two moments of OS space are how a machine survives its own update. One is running. The other is prepared. The rules tool commits the switch only as a take. If the new moment is not healthy, the next start is the old one. HoloFS already thinks in snapshots; the inactive slot is a moment, not a tarball.

### User space

The person's body of documents, records, and history. One person's user space is not another's. A place does not get a copy of it because you visited.

User space is bound to a **person session**, after the identity tool accepts a proof and the place's rules allow a user volume here at all. Many places will not. A guest may be allowed scenes and nothing of their home volume. A home will bind the volume that already exists on this holo. A desk you own may bind it locally or, if the volume lives on another site, ask Harmonics to reach it (Dialtone for the session, Overtone for the bytes).

Applications do not receive the user volume. That is the whole point of the class. "Open my files" is not an access mode. If an application needs a document, the catalogue contains a page for that kind of grant — a named collection, read or write, as an extra claim of class `application` whose **source** is a slice of user space. The slice is an enum the rules already know, not a path the model or the application invented. There is no page called "the home directory."

The identity record itself is stored with the person, but it is not a file applications can open. Treat it as its own volume inside the person's authority, classed so that only the identity tool can bind it. Putting the record in the general user mount would make every granted application a root of trust.

### Application space

One volume per granted application per person session (or per shared scene, when the page is a house application rather than a personal one).

This is the claim that looks most like a PVC mounted into a pod:

- The application asks for nothing. GlassSpear, or Vikett walking an "open" page, submits a claim: class `application`, subject this person (or this place, for a shared page), role this page's application, access exclusive write, source empty or a named snapshot.
- The rules tool prunes. A guest's catalogue does not contain that page. A second person in the room does not inherit the first person's volume. An application that is not in the scene does not have a claim waiting.
- On allow, HoloFS creates or rebinds the volume and returns a mount. The application sees that tree. It does not see OS space, user space, or any sibling application.
- When the session ends, the mount drops. Reclaim is retain unless a forget-page is walked later. The next session of the same application for the same person binds the same volume if the rules still say yes. Data survives the process. The grant does not survive the person leaving.

Shared house applications (a timer, a shared scene) are still application space. The subject of the claim is the place, not whichever person happens to be nearest the glass. Personal pages are claims whose subject is the person. GlassSpear decides which pages a surface may show. It does not decide which volume they get. It asks.

## What a claim looks like

The schema is not fixed. The slots are. A claim that arrives with a free-typed path, a free-typed size string, or a free-typed user name is not a claim. It is noise, and the tool stays silent.

| Slot | Comes from | Never |
| --- | --- | --- |
| Class | `os`, `user`, `application` | A new class coined in the request |
| Subject | A person proof, or the machine | "Whoever is nearby" |
| Place | The domain whose rules are in force | The subject's opinion of the domain |
| Role | A page id, `person`, or `machine` | An executable path |
| Access | A small enum: read, write, exclusive | A mode bit string the caller composed |
| Source | Empty, a snapshot id, a lend id, a named user slice | A filesystem path |
| Reclaim | Retain or forget | "Delete everything under" |

Size, survival, and exactness belong to the class, decided when the class was authored, not restated by each claim. An application does not get to ask for a weaker survival bracket than its class.

## How the rules tool says yes

The tool is undefined. The behavior is not. It is Vikett's loop pointed at claims instead of at a compositor.

1. **Shape.** If the slots are not from the enums, stop. Silence or a hard refuse. Do not repair the request.
2. **Catalogue.** The place has authored the legal claim-pages: bind user space, bind application space for a named page, project a named user slice into an application, lend, revoke, snapshot, step back, forget, prepare OS moment, commit OS moment. Humans write these. The tool does not grow them at runtime.
3. **Prune.** Drop every page the live world makes illegal. No person present means no user bind. Guest policy means the mail page and the user-space page are absent, not merely hidden. The machine is not in maintenance means every OS write page is absent. An application already at its class quota means a new exclusive write is absent.
4. **Take.** A human sentence is Vikett's problem first: it chooses an interaction page or stays silent. A claim that is already typed is this tool's problem: it either matches a live page or it does not. A decision model, if one is used, sees live page labels only. It never sees a HoloFS handle, a Dialtone socket, or a mount path.
5. **Walk.** HoloFS performs the bind. The tool does not mount by a side path.
6. **Refuse again at the volume.** The mount HoloFS returns cannot name anything outside the claim. A confused walk still dies at the volume boundary. That second check is HoloFS's job, not a courtesy.

Deny is different from silence. Silence means the utterance or the claim was not a live page. Deny means it was a known page and this subject, now, is not allowed to walk it. Both results do zero mounts.

## Isolation, stated as failures

| Attempt | Result |
| --- | --- |
| Application opens a path in OS space | The path is not in its mount. |
| Application opens another application's volume | No such mount. |
| Application lists the person's documents | User space was not bound to it. A slice appears only if a page projected that slice. |
| Person reads another person's user space | The claim does not prune in. HoloFS has no mount to offer. |
| Guest bind of user space | The page is not live under guest rules. |
| Maintenance page walked by the person who only lives here | Pruned. OS space stays on the boot binding. |
| Lend still used after revoke | The wrap is dead. The far side goes dark. Dialtone cannot keep serving a volume whose claim ended. |
| Deleted file | The name is gone from the volume. The bytes remain until forget, and until no snapshot references them. |
| Two writers, one application volume | Access said exclusive. The second bind does not happen. |

## Where the other components sit

**HoloFS** is the pool, the volume, the snapshot, the lend, and the boundary that makes a mount unable to see its neighbors. It does not know GlassSpear's scenes and it does not interpret speech.

**The rules tool** is the binder. It is the only thing allowed to ask HoloFS to attach a volume to a subject. It does not draw pixels and it does not carry packets.

**Vikett** is the interaction catalogue. "Put the writing on the other glass" becomes takes. If a take needs storage that is not already bound, Vikett does not mount it. It emits a typed claim and the rules tool either walks it or does not. Same manners, two catalogues, so a window-page cannot quietly become a disk grant.

**GlassSpear** chooses which pages a surface shows for who is there. Showing a page is not binding a volume. The surface runtime may display a page only after application space for that page is bound. Shared scenes and personal pages are different subjects on the claim, which is how two people can look at one glass without sharing volumes.

**Harmonics** is how a bound volume is allowed to be somewhere other than the local disks. Dialtone is the session to the who that holds the holo. Overtone moves content when the claim's source is remote and the rules already allowed it. Neither of them can bind a class the rules tool did not walk. A reachable holo is not a mounted holo.
