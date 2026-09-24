# Identity

Identity is the spine. Every other component already assumes a "who." Arachne's job is to make that who the same who, in every strand, without making a single company or a single server the place where who lives.

## More than a keypair

A keypair is the proof mechanism. It is not the identity.

The identity is a **record**: a public key, claims, delegations, and enough history for a stranger's building to know what it is looking at. The record lives somewhere durable — a volume on a holo you control. You do not carry the record around as a blob you might lose. You carry an **address** that resolves to it, and the means to prove you still speak for the key inside it.

That address is a Dialtone name. When you walk into a place that has never enrolled you, you present the address. The place fetches the record from your strand, or from a copy someone you trust is holding, and checks the signature. No account is created. There is no global directory you had to join.

If the place cannot reach your strand, it can still verify a signature it can see. Freshness is the part that suffers, not authenticity. See continuity for how stale proof becomes a narrower session rather than a hard failure.

## Person, device, domain

Three facts are always separate. Collapsing them is how systems become either centralized or unsafe.

| Fact | Question it answers | What holds it |
| --- | --- | --- |
| Person | Are you the one this record names, right now? | Your key, unlocked locally, pointed at by the address you carry |
| Device | Is this hardware a machine some domain has enrolled? | A device key that never leaves that machine, born when the machine is first trusted |
| Domain | What may that person do on the machines *this place* is responsible for? | Policy local to the home, the household, the building, the lab |

Carrier holds the person's ability to prove the record. It is the vault in your pocket: pairing, claims, and later the continuity pack that lets a visit rehydrate. It is not a mesh node and it does not render the house.

A device key is how a work machine can be "a real work machine" without knowing your face, and how a stranger's glass can let you stand at it without swallowing your long-term key. The session minted for those few minutes is signed by you and carries the device's attestation. Revoke the device and its sessions die. Rotate yourself and the hardware enrollment is untouched.

The domain never becomes you. A household, an office, a building each publish what guest, staff, owner, and maintainer mean *there*. An administrator with a higher claim can change that policy. They are editing the building, not your record. They can refuse a claim of yours. They cannot author one in your name.

Hearth is a small, already-real version of domain authority: a parent and a child system, rules that apply on the child's machine even when the parent is offline, and an explicit release when someone leaves the household. Arachne generalizes that pattern past screen-time. The household is one domain. The office is another. Your own machines are another. You cross them with one record.

## Presence, not possession

A credential you only possess can be stolen and used from anywhere. A record that can be *exercised* in two places at once is not a person.

The rule is a **presence lease**. When you prove yourself, the record notes where and when, and only one lease is live. A second use elsewhere does not silently succeed.

Distance and time matter. Being seen at home, and then a minute later in a building across the city, is not an automatic ban. It is an escalation. The first proof might be enough when the jump is plausible. An implausible jump asks for something you are holding — the pocket vault, a second factor — before the place restores a full session. Until then you get the degraded version: read, shared surfaces, nothing personal, nothing with root. The lease also expires. Walk out and do not prove yourself again, and the next surface starts clean. You cannot be stranded by a lease you forgot to close; you can be made to prove yourself again.

BuckyBoi is the sensing end of this on a workstation: face, voice, gesture, more than one person in view, fail closed. It identifies. It does not decide the walk. GlassSpear is the sensing end in a room: who is near which surface. Carrier is the proof you still have when those sensors have nothing local to match against except what you unlock.

Biometrics stay in the convenience layer. They are noisy, they leak forever, and they cannot be rotated. They unlock a key on a device you are touching. They are never sent off as the credential. Stolen video of your face gets an attacker a locked door, not your record.

## Social copies

This is deliberately close to handing someone a card, and deliberately not a replay of keysigning parties.

Your record at rest is encrypted. People you actually know may hold a copy. When you are in their house and your home strand is dark, they can verify you from what you already gave them. The signature still has to check. The copy is a snapshot, so it carries a version. Too old, and the place marks the session degraded instead of pretending the card is current.

The live record on your holo remains the source. Copies are the offline fallback, updated when you next meet a strand that can refresh them. They are not the primary path, which is the mistake that made webs of trust something only specialists used. Refresh wants to be a consequence of use, not a chore.

## What an application is allowed to know

An application does not get your identity. It gets a session, and a volume, and a set of moves. The session says which person authorized it and which domain allowed it. The application's own key is not you. You can revoke the application's grant without rotating yourself. See [CONTROL.md](CONTROL.md).

## Failure, on purpose

| Situation | What should happen |
| --- | --- |
| Pocket vault lost | You recover from a path you set up before, not from a vendor. Devices you still hold can be re-proved. The lost vault's sessions die. |
| Photo of your face leaks | Nothing cryptographic rotates, because the face was never the key. Local unlock on a stolen device still needs the device and its own gate. |
| Home holo offline | Signature checks. Social copy if you have one. Session narrows with age. |
| Two places at once | Second place escalates or degrades. It does not clone you. |
| Domain admin is hostile | They can lock you out of *their* machines. They cannot rewrite the record on your strand. |
| You revoke a claim while a place is offline | That place is wrong until it reconnects, which is why stale proof is narrower, not equal. |
