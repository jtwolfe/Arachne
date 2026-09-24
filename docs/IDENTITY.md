# Identity

Arachne needs a way to answer three questions without turning them into one account.

| Question | Answered by |
| --- | --- |
| Are you this person, now? | A proof: an address, a signature, a key unlocked locally |
| Is this hardware a machine this place enrolled? | A device key that stays on the machine |
| What may that pair do here? | The place's catalogue, pruned and walked by the rules tool |

The tool that checks proofs and walks claims **is not defined**. Its shape is defined, in [CONTROL.md](CONTROL.md), because Vikett already showed that closed catalogues beat invented actions. Identity is not a component you can clone from an existing repository and drop in. It is the missing lock.

## The record

A keypair is how you sign. The **record** is who a place thinks it is verifying: a public key, claims, delegations, a version, a time of last proof. The record lives in a volume that only the identity tool can bind. It is not in OS space (the machine must not own you) and not in the user-space mount (applications must not edit you).

You do not carry the whole record as the only copy. You carry an **address** Dialtone can resolve, and the means to prove you still speak for the key. A place that has never seen you fetches the record or reads a copy it was given. It verifies the signature. It then applies *its* catalogue. No account is written.

[Carrier](https://github.com/jtwolfe/carrier) is one experiment in holding that proof on a phone. Arachne does not depend on Carrier, its pairing flow, or its roadmap. Any carry that can present the address and unlock the key is enough for the concept. A machine you are touching may also hold an unlock for a key, if the rules of that machine say the key may live there. Biometrics, if used, only unlock. They are not the record and they are not sent as the credential.

## Person and machine stay apart

The machine boots from OS space with its own device key, before anyone arrives. That key is how maintenance claims know they are on the enrolled machine and not on a copy of the disks. It is not a person.

When a person proves themselves, the rules tool mints a session that names both: this person-proof, this device, this place, this expiry. Application claims and user-space claims hang off that session. They are not hung off the login name, because there is not one.

A place you do not own can accept your proof for a guest prune without storing your key. Your key can unlock on hardware you do not own for the length of the session without that hardware becoming your carry. When the session ends, the place keeps an audit of which pages were walked, not a replica of user space, unless a claim explicitly lent or snapshotted something. Audit is OS space or a place-owned volume. It is not your record.

## Prune inputs that identity must supply

The rules tool is useless if "who" is a string. These are the facts a proof has to be able to support, and no others are required by the concept:

- subject id (the public key, not a display name)
- which place-authored claims this record carries, if any (resident, maintainer-until, nothing)
- version and signed time, so a stale proof can be pruned harder
- whether this session's key was unlocked on a carry the place accepts, or only on the local machine

Display names, avatars, and "the admin role" are not identity. Resident versus guest versus maintainer are claims a **place** decided to honor, stored as what the catalogue prunes on, not as a global role.

## What a place must not do

- Edit the record. It can refuse a claim. It cannot author one in the person's name.
- Treat presence as the proof. GlassSpear may assert that someone is at a surface. The identity tool still requires a proof the catalogue accepts before user space or personal application space binds. A shared scene whose subject is the place may show without a person. A personal page may not.
- Collapse every machine the person touches into one trust domain. Dialtone reachability is not enrollment. Enrollment is an OS-class or place-class page that was walked when the machine joined, and it can be revoked.

## When the proof is thin

Offline, or home unreachable: the signature still checks if the record or a copy is present. The rules tool's prune treats age as a fact. Fresh enough, the usual pages for this place. Older, fewer pages — typically no user-space bind, no lend, no maintenance, application space only if that page was authored as safe without a refresh. The concept does not pick the timeout. It requires that staleness narrows the catalogue rather than failing closed into "make a local account so they can work."

An implausible second session — the same subject proving somewhere else in a way the rules call impossible — is also a prune input. The second place does not become a second copy of the person. It walks a smaller catalogue, or it denies, until a proof the catalogue counts as strong enough. Arachne does not specify the physics of "implausible." It specifies that the rules tool must have a slot for it, and that the slot cannot be filled by an application.
