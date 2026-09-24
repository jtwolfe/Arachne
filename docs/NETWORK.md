# Harmonics

Harmonics is how Arachne reaches. Names stay. Locators die. A glass, a desk, and a holo full of disks are not required to share a subnet for a claim to be real.

Two parts, and they do not overlap:

| | Job | Not its job |
| --- | --- | --- |
| **Dialtone** | Connection. Identity-addressed sessions. A who, a proof, an optional path onto a local interface, a way to name something that moves. | Storage policy. Scenes. Deciding a claim. Carrying bulk as a side effect of being connected. |
| **Overtone** | Transmission. Content asked for by name, cached because it was asked for, dumb on purpose. | The packet path. Identity. Knowing what the bytes mean. |

Arachne is a concept project. It does not specify Harmonics' wire. It specifies the moments where Arachne is allowed to call one or the other.

## Dialtone in a session

Every subject that can be reached has an address: a person, a machine, a holo that can answer for a volume. Dialtone resolves the address to whatever is currently able to speak for it. IP addresses, room numbers, and "the server in the cupboard" are locators. They can change without the address changing.

The identity tool uses Dialtone in three places:

1. **Fetch a record.** A place that has never stored you is handed an address. Dialtone finds a who that can serve the record. The rules tool checks the signature and applies local rules. Dialtone does not cache the record into OS space "for next time" unless a claim of that shape exists and was walked. A convenience cache of identity is a second source of truth.
2. **Open a session to a holo that is not local.** User space or a lent volume may live on members elsewhere. The claim's source says so. Dialtone is the session. It is not permission. If the rules tool has not walked the claim, there is no session to open, even if Dialtone could find the peer.
3. **Name a machine to itself and to other machines in the place.** The OS has a device identity, distinct from any person. Maintenance claims, health, and "where is the other boot moment being prepared" are conversations between whos, not between user accounts.

When the network is gone, Dialtone is gone. Local binds against a holo whose members are in the machine still work. Remote sources do not. A signed record already in hand can still be checked, and the rules tool narrows the session because it could not refresh. Absence of Dialtone is a prune input, not a crash.

## Overtone in a session

Overtone moves content that is already allowed to move.

- A snapshot authorized as a source.
- A volume whose claim says the bytes may be replicated to this site.
- An OS moment being prepared on the quiet slot, fetched as content, verified, then handed to HoloFS as a source. The fetch is not the commit. The commit is a maintenance page.

Overtone stores what it was given, addressed by content. It does not learn directories, people, or policy. It is not in the path of Dialtone packets. A session must succeed with Overtone dark; it will merely be unable to complete claims whose source is bulk content elsewhere. Those claims fail closed. They do not fall back to tunneling someone's user space through the control channel.

A place that can see Overtone content still cannot mount it. Possession of bytes is not a bind. The rules tool walks a claim, HoloFS unwraps only if the key and the claim agree, and only then does a mount exist. Encrypted content sitting in a cache is not user space.

## What never goes on the wire by default

| Stays local unless a page says otherwise | Why |
| --- | --- |
| Raw presence (whatever GlassSpear used to decide who is at a surface) | The outward claim is "this subject, here, now," if it needs to leave at all. |
| OS space | Another site does not boot your machine by mounting your root. An OS moment is copied only as a maintenance source for *this* machine's quiet slot. |
| The full user volume | Visits get claims, not a live mirror. A projection or a lend is a page. |
| Application volumes of a person | They follow the person only when a new session rebinds them through a claim, at a place whose rules allow that application. |

## How the four base pieces meet on the wire

GlassSpear wants a personal page on a surface. Vikett has already taken "show this page" or the scene change that implied it. The rules tool builds an application-space claim. The volume is local: HoloFS binds, Harmonics is idle. The volume is remote: the rules tool asks Dialtone for a session to the address in the claim source, then asks Overtone for the content the claim named, then asks HoloFS to bind what arrived. If Dialtone fails, the page does not appear half-loaded from leftover cache. If Overtone fails, same. If HoloFS refuses the bind, the session is closed. No component papers over another's no.

A lend to another person is the same shape with a different subject. Dialtone finds them. The wrap is the key HoloFS issued for that claim. Overtone may move a snapshot if the page was "give them a moment," or the far side may read through the session if the page was "let them read while the wrap lives." Revoke is a local HoloFS fact that Dialtone must stop honoring. A peer that keeps talking after revoke is a broken peer, not a policy exception.

## Places

A house, a building, and a machine you own are different places with different catalogues. Harmonics does not merge them into one network identity. Your address is yours in all three. The machine's address is the machine's. The place's rules are what decide whether those two addresses, in combination, may bind user space or only stand in a shared scene. Travel is a new session to the same person-address, under a new place's catalogue. It is not a tunnel back to the glass you left, and it is not the remote place mounting your OS space.
