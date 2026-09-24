# Network

The web has to find people and machines without freezing their addresses into the name. Locations die. NATs change. A laptop goes to school. A disk walks to another room. The name should still mean the same thing.

That problem already has a direction: **names stay, locators die.**

## Dialtone and Overtone

Harmonics is the personal internetwork.

**Dialtone** is connection. Identity, session, the possibility of a name that resolves to whoever is currently able to answer for it. You do not dial an IP and hope. You dial a who. The who might be your holo, a surface in the house, a machine you linked, a building that is willing to fetch your record.

**Overtone** is transmission. Bulk bytes, caches, content that can be fetched because you asked for that content. It is allowed to exist only because it is not in the packet path. The session must not depend on a cache being clever. A cache that understands your life is a surveillance point. A cache that stores what it was handed, addressed by content, is a wheelbarrow.

Arachne uses Dialtone as the way identity addresses are resolved and as the way a site fetches a record it does not store. It uses Overtone when a volume, a snapshot, or an update is large enough that "open a session and drip the bytes through the control channel" would be the wrong shape. Control and cargo stay different.

## Machines you have linked

MyMesh is the practical mesh for machines you explicitly trust: pair once, then a shell, a file copy, a tunnel to a service, a name that is yours rather than a public DNS name. It is not a VPN product and it is not the whole internetwork. It is the feeling of *my machines can reach each other because I said so*, including from behind the kinds of networks that do not take port forwards.

Hearth is that feeling with a household policy on it. A child's system paired at home still answers from school. A parent can see that they are there, how long the machine has been in use, and which application has focus — not a screenshot, not a keylog — and can grant time, lock, or push an update. The child machine enforces the last policy it was given even if the parent cannot be reached. Leaving the household is an explicit release, not a daemon the child is expected to kill.

In Arachne these are domains running on the personal internetwork:

- MyMesh is "machines in *my* domain that I linked."
- Hearth is "people in a household domain, including people who are not the administrator."
- A building you visit is a domain you did not link, which can still talk to your Dialtone address without becoming a member of your mesh.

They should not grow three pairing ceremonies and three notions of device identity. Carrier is already the pair you hold up. The path is one pairing gesture, and different policies after the link exists.

## What crosses, and what does not

A session carries proof and small claims. A volume's contents move when a grant says they may, and they move as content, not as "the user's home directory, live, over the wire." Continuity on a visit is a pack, not NFS of your life onto a glass you do not own.

Presence hints — who is near a surface — stay local to the place unless a policy you can read says otherwise. A building does not get a feed of your face. It gets a proof you chose to present, and then only the pages its policy allows.

Relays, when a direct path is impossible, forward encrypted packets. They are not a directory of your files and not a home for your record. If the only way a strand works is by trusting a relay with plaintext, that strand is not done.

## Finding the record

When a site needs your identity record it does not look you up in its user table. The order is:

1. You present an address (and a fresh proof, if the moment calls for it).
2. Dialtone resolves that address to a place that can answer.
3. The record is read from the holo that holds it, or from a social copy if that is all the site can reach.
4. The site applies its own policy to the claims inside.
5. Anything large that then has to move — a continuity pack, a volume you lent, an update — may go by Overtone. The decision to allow it already happened on the session.

If resolution fails, the site falls back along [IDENTITY.md](IDENTITY.md): signature in hand, then a narrower session, not a new account "so we can let you in this once."

## Household, travel, and the office

The same machine can be in more than one relationship over a day. A laptop at home is in your domain. The same laptop at school is still yours, and if it belongs to a child it is also inside Hearth's rules, which were written to survive exactly that trip. The same person standing at an office glass is inside the office domain for that session only. The laptop in the bag does not become an office machine because you walked into the lobby. Session, device, and domain stay distinct so that "I was at work" does not mean "work now owns my holo."
