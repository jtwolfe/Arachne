# Arachne

A web of compute, spun around a person.

You do not log into machines. You arrive. A kitchen screen, a laptop on a train, a work building, a friend's house, a disk in a pocket — these are not separate systems with separate accounts. They are strands. Whichever strand you are touching becomes your place for as long as you are there, and only as far as that place is willing to let you.

Arachne is the name for that experience, and for the agreement about how the pieces already underway become one system. It is not a new kernel, not a distro, and not a rewrite of those pieces. [HoloFS](https://github.com/jtwolfe/holofs) is still the storage. [Harmonics](https://github.com/jtwolfe/harmonics) is still the internetwork. [GlassSpear](https://github.com/jtwolfe/GlassSpear) is still the house. [Carrier](https://github.com/jtwolfe/carrier) is still what you carry. [BuckyBoi](https://github.com/jtwolfe/buckyboi) still notices you. [Vikett](https://github.com/jtwolfe/vikett) still refuses to invent a command. [AIOS](https://github.com/jtwolfe/AIOS) still keeps a machine reconstructible. Arachne says what they are *for* when a person moves through them.

The name is the weaver. The web is not a network diagram. It is the feeling that compute, storage, and attention are already around you, and that walking into a room is enough.

## What it feels like

Morning. You walk into the kitchen. The glass there was showing the house — weather, the timer, whoever else is home. It does not ask you to sign in. It already has a fresh enough sense of you, from the person you carry and from the fact that you were in this house minutes ago. Your page replaces the house page on the screen nearest you. The other screens stay shared. You did not open an app. A scene arrived.

You sit at the workstation. The overlay buddy turns because it saw you, not because you clicked a login. Listening is gated. A stranger in the chair gets silence.

You say something ordinary: open the thing you were writing, and put it on the second glass. That is not a generated shell command. It is two legal moves from a catalogue the system already authored, pruned to what you are allowed to do in this room, chosen, then walked. If the sentence does not match a move, nothing happens. Silence is a result.

Later you are in a building that has never seen you. You do not create an account. You present an address. The building reads the record that address points at — your key, your claims — and applies *its* policy, not yours. Guest. No root. Shared surfaces only. A person who works there presents the same kind of proof and is recognized as staff, because the building's policy says so. A maintainer from outside might hold a time-boxed claim. Your identity did not change between the three. The building's authority did the sorting.

On the train the network is gone. The record you carry is signed, so the laptop can still check it. A live look or voice unlocks the key that actually matters; the biometric is not the identity. The session is narrower than it would be at home, because the laptop cannot ask your home node whether the record is still fresh. When you are back on a strand that can reach home, the lease and the claims catch up.

You delete a file. The name disappears. The bytes do not. The holo remembers the moment before the mistake.

None of that requires the person to know which machine holds the bytes, which protocol punched the NAT, or which policy file said yes. Those are the web's problems. The person's problem is to be present.

## The shape

Four things have always been required for work to run: **compute**, **storage**, **network**, and the live **state** that dies when a node dies. Arachne does not replace that. It refuses to make you administer it.

Under those four sits one spine: **identity**. Not an account on each box. A record you can prove, that any strand can verify, that no strand is allowed to rewrite.

| Layer | What a person experiences | What actually does it |
| --- | --- | --- |
| Presence | The room, the buddy, the phone know you are here | BuckyBoi, GlassSpear, the phone pane |
| Carry | You can leave every device powered off and still be you | Carrier |
| Authority | This place decides what *you* may do *here* | The site's policy, checked against your claims |
| Attention | Scenes, not window management | GlassSpear, and Vikett choosing the scene |
| Action | Only moves that were authored in advance | Vikett |
| Files | Plug a disk, capacity grows; unplug one, the holo continues | HoloFS |
| Reach | Names stay when addresses die | Dialtone, with Overtone beside it, not inside it |
| Household | The mesh follows the people, including the ones who are not the admin | Hearth, MyMesh |
| The box itself | The machine heals, updates, and stays explainable | AIOS, with update and recovery as signed moves |

```text
you arrive
    │
    ▼
Carrier proves a person · the device proves a machine
    │
    ▼
Dialtone finds the record · HoloFS holds it
    │
    ├─ site policy: guest / staff / owner / maintainer
    │
    ▼
Vikett prunes the catalogue and takes one move
    │
    ├─ GlassSpear walks a scene onto a surface
    ├─ an application walks inside its own volume
    └─ the steward walks a heal, an update, a rollback
```

## What Arachne is not

| It is not | Because |
| --- | --- |
| A login screen with a nicer font | Arrival is the interface. Accounts are a fallback for places that do not know you yet. |
| A container platform | An application is privileged by a signed specification, not trusted because it sits in a box. The volume enforces the grant. |
| A chatbot that runs the house | Models may *choose* among authored moves. They do not invent commands, paths, or policy. |
| One global identity provider | Each home, each building, each person's own machines is its own authority. Identity travels. Authority does not. |
| A new kernel on day one | The experience has to be true on a normal Linux machine first. A filesystem in the kernel is a later strengthening, not the entrance. |
| A memory of you as a person | History exists so files, leases, and machines can be reconstructed. It is not a diary and not a companion. |

## The pieces

Each of these already has a life of its own. Arachne only says how they meet.

| Piece | Role in the web | Where it lives |
| --- | --- | --- |
| **HoloFS** | The durable web. Disks join and leave. Names point at content. Deleting a name is not destroying the past. | [holofs](https://github.com/jtwolfe/holofs) (private) |
| **Harmonics** | Dialtone connects. Overtone carries bytes when asked. The packet path stays dumb. | [harmonics](https://github.com/jtwolfe/harmonics) (private) |
| **MyMesh** | Machines you have personally linked: a shell, a file, a tunnel, without a port forward. | [MyMesh](https://github.com/jtwolfe/MyMesh) |
| **Hearth** | A household on that kind of mesh. Time, presence of a person at a machine, a parent's hand, an update pushed to a child system. | [hearth](https://github.com/jtwolfe/hearth) |
| **Carrier** | The thing in your pocket that can prove you when every other device is off. Pairing, claims, a continuity pack. Not the house, and not a mesh node. | [carrier](https://github.com/jtwolfe/carrier) (private) |
| **GlassSpear** | Surfaces in a place. Scenes instead of desktops. Presence is the UI. | [GlassSpear](https://github.com/jtwolfe/GlassSpear) (private) |
| **glass** | The phone as a surface you hold, not a screen on the wall. | [glass](https://github.com/jtwolfe/glass) |
| **BuckyBoi** | On a machine that still has windows: a presence that can tell people apart and can refuse to listen. | [buckyboi](https://github.com/jtwolfe/buckyboi) |
| **Vikett** | The catalogue of legal moves. Prune, choose, walk, or stay silent. | [vikett](https://github.com/jtwolfe/vikett) |
| **AIOS** | The steward of a single machine. Freedom to change it, inside conditions a human can check. | [AIOS](https://github.com/jtwolfe/AIOS) |

Dearr stays a library on top of storage. It is a client. It is never the mesh.

## Read this as a path

| If you want | Go to |
| --- | --- |
| A day in the web, without architecture | [docs/EXPERIENCE.md](docs/EXPERIENCE.md) |
| Who you are, in more than one place | [docs/IDENTITY.md](docs/IDENTITY.md) |
| Where bytes live, and why a delete is not a delete | [docs/HOLOFS.md](docs/HOLOFS.md) |
| How a name finds a machine | [docs/NETWORK.md](docs/NETWORK.md) |
| Rooms, buddies, and the phone | [docs/SURFACES.md](docs/SURFACES.md) |
| How an application is allowed to act | [docs/CONTROL.md](docs/CONTROL.md) |
| Time, live state, updates, and the steward | [docs/CONTINUITY.md](docs/CONTINUITY.md) |
| What to join up, and in what order | [docs/PATH.md](docs/PATH.md) |

## A note on ambition

The closest systems in the world each solved a slice. Phones sandbox applications and update themselves in pairs of slots. Some desktops isolate work into separate machines and pass resources through a slot. Content-addressed storage, snapshots, and self-sovereign credentials all exist. None of them made identity the spine and then hung storage, rooms, and legal action off that spine so that walking in is the whole interface.

That is the goal. The sci-fi is not a new gadget. It is the absence of the login.
