# Arachne

A web of compute, spun around a person.

Arachne is a concept for an operating environment. It is not a kernel, not a distribution, and not an integration plan for every adjacent experiment. Four existing efforts are the base, and one tool that does not exist yet is the lock between them.

| Piece | What it is in Arachne |
| --- | --- |
| **[HoloFS](https://github.com/jtwolfe/holofs)** | Storage. A holo: disks join and leave, content keeps its name. OS space, user space, and application space are volumes on that holo, isolated the way a claim isolates storage, not the way a shared home directory hopes. |
| **[Harmonics](https://github.com/jtwolfe/harmonics)** | Reach. Dialtone connects a *who*. Overtone moves bytes only when asked, and never sits in the packet path. |
| **[GlassSpear](https://github.com/jtwolfe/GlassSpear)** | Attention. Surfaces show scenes. A house that knows who is there is the interface. Desktop management disappears on environmental computers. |
| **[Vikett](https://github.com/jtwolfe/vikett)** | Action. Legal moves are authored pages. The live world prunes them. A referee takes one, or stays silent. Nothing invents a command. |
| **Identity and rules** | Not defined yet. The tool that decides whether a storage claim, a scene, or a move is allowed. Its shape is Vikett's: a catalogue, a prune, a typed take, a walk, silence. It is not Vikett itself. |

A person may carry the proof that opens a session. [Carrier](https://github.com/jtwolfe/carrier) is one way to hold that proof. Arachne does not depend on it. Any carry that can present an address and unlock a key satisfies the concept.

## The feeling

You walk into a room. GlassSpear already treats that room as surfaces and scenes, not as a desktop you have to drive. The identity tool — whatever it becomes — checks a proof against the rules of *this* place. It does not create an account.

If the rules allow it, HoloFS binds storage and nothing else:

- The machine is running from **OS space**. You cannot see it, and an application cannot write it.
- Your documents live in **user space**. Applications do not receive that volume.
- The page that just appeared gets **application space**: its own volume, the way a workload gets its own claim, plus only the extra binds the rules explicitly walked.

You say something ordinary. Vikett maps it to pages that exist. Two intents are two takes. A sentence that matches nothing is silence. Harmonics is why the volume you just bound might not be on the disk under the glass: Dialtone finds the who that holds it, and Overtone carries the bytes if the session already said yes.

You leave. Mounts drop. Names you deleted are gone from the tree. The bytes remain in the holo until a rule says to forget them. OS space was never in the session.

## How a session is assembled

```text
proof of a person
        │
        ▼
identity and rules tool          ← not built; Vikett-shaped
catalogue × place × claims
        │
        ├─ refuse or stay silent
        │
        ▼
HoloFS binds only the claims that passed
        │
        ├─ OS space        machine only, already mounted to boot
        ├─ user space      the person, not their applications
        └─ application space
                one volume per granted application
        │
        ▼
GlassSpear places pages on the surfaces this person may see
        │
        ▼
Vikett takes further moves (scene, app action, lend, snapshot)
        │
        ▼
if bytes must move between sites
        Dialtone decides the session
        Overtone moves the content
```

The identity tool is in front of HoloFS on purpose. A volume is not a folder you chmod after the fact. It does not exist in a namespace until a rule has walked a claim. GlassSpear does not mount disks. Vikett does not invent grants. Harmonics does not decide policy. HoloFS does not decide who you are. Each one refuses the job that belongs to another.

## What this is not

| It is not | Because |
| --- | --- |
| A login with better chrome | Arrival is GlassSpear doing its job after a claim succeeds. |
| A container platform | Isolation is which volumes were bound, checked by rules, enforced by the holo. A box around a process is not the model. |
| Kubernetes | The claim shape is borrowed so the storage story is familiar. The authorizer is not RBAC, and the cluster is not the product. |
| A model that runs the house | Vikett, and the rules tool after it, only choose among pages a person authored. |
| One identity provider | A place applies its rules to a record it can verify. It does not own the record. |

## Read

| | |
| --- | --- |
| A day, as a person | [docs/EXPERIENCE.md](docs/EXPERIENCE.md) |
| OS, user, and application space | [docs/SPACES.md](docs/SPACES.md) |
| HoloFS as the substrate | [docs/HOLOFS.md](docs/HOLOFS.md) |
| Dialtone and Overtone | [docs/NETWORK.md](docs/NETWORK.md) |
| GlassSpear | [docs/SURFACES.md](docs/SURFACES.md) |
| Vikett, and the rules tool that does not exist yet | [docs/CONTROL.md](docs/CONTROL.md) |
| Who the proof is | [docs/IDENTITY.md](docs/IDENTITY.md) |
| Leases, deletes, boots, return | [docs/CONTINUITY.md](docs/CONTINUITY.md) |
| What has to be true, in order | [docs/PATH.md](docs/PATH.md) |
