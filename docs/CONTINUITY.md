# Continuity

Compute, storage, and network are not enough. The fourth thing is **state**: sessions, a half-finished scene, a process in the middle of work, the fact that you were authenticated *here* four minutes ago. Storage can bring back bytes. It cannot bring back a moment of RAM. The web has to have a story for that moment that is not "hope the machine stays up."

## Leases and the clock

Presence leases, session grants, snapshot order, and "is this social copy too old" all assume the strands agree roughly on *now*. A single time server is a place that can lie, and a place that can be unreachable on purpose.

The agreement we want is gossip among peers you already trust. Each machine keeps its own clock. The mesh compares skew with the peers it is willing to believe. Nobody is the source of time. There is enough agreement that "two minutes ago" and "two days ago" do not get confused. The record carries a signed time from the last proof; a surface checks that against its own clock plus the skew it has heard.

If the gossip is thin — you are alone, offline — you fall back to the device clock and you narrow the session as the proof ages. Wrong time should make the web cautious, not authoritative.

## What is allowed to be ephemeral

| Kind of state | When the machine dies | What rehydrates it |
| --- | --- | --- |
| File bytes | Nowhere, if the holo still has members | The volume, by content |
| A scene on a glass | The pixels | GlassSpear, from the scene and the person still present |
| An application grant | The grant | A new take, if the person is still here and the policy still says yes |
| The presence lease | The lease | A new proof; an implausible gap escalates |
| A visit's working set | The pack, if it was not yet flushed | Carrier's continuity pack plus the volumes it named |
| The machine's own configuration | A snapshot of the last accepted machine | AIOS's reconstructible history, and the other boot slot |

Live processes are not sacred. Arachne would rather restart a player in the same scene than pretend a process migration is the product. The feeling of continuity is "the writing is where I left it, on a volume that is mine," not "the Unix process followed me down the hall."

## The steward

AIOS is how a single machine stays a machine without you becoming its administrator. A privileged agent is allowed real room: packages, layout, services, the shape of the box. The control is an envelope of conditions that can be checked without asking the model whether it feels finished. The human owns the highest layer and the brake. Enactment is history you can read, on that machine, not a silent mutation.

The steward is not BuckyBoi and not a personality. Privilege is not a presence. The buddy is who the room sees. The steward is who changes the box when a condition says a change is allowed. Optional work agents, if you asked for them, file requests. They are not a second steward and not a second you.

In the web, the steward's dangerous buttons are Vikett pages. Stage an update. Commit it. Roll it back. Ask for a disk. Those pages are pruned by who is allowed to maintain *this* machine. A guest never sees them. A time-boxed maintainer sees them until the claim dies. The agent does not get a private back door that skips the catalogue.

## Updates and the other slot

The recovery story is an A/B boot. Two roots. You run on one. The next system is prepared on the other. A health check decides whether the next boot is the new one or the one you already trust. Failure returns to the known slot without a person holding a USB in the driveway.

HoloFS already thinks in moments. The inactive slot should be a moment the holo (or the machine's own snapshot) can stand up, not a tarball with a prayer. The update itself arrives as content — signed, addressed, fetched because a page said to fetch it — over the mesh, verified against a key the domain already trusts. Overtone can carry the bulk. Dialtone carries the decision. The steward only commits after the check. If the check fails, the take never becomes the boot.

A household already has a smaller version of "the parent pushes, the child applies, the parent does not become the child's keyboard." That is the right social shape. Arachne's version is the same shape for system images: someone authorized to maintain may *ask* the machine to move to a signed moment. The machine applies it to the quiet slot and only then considers stepping across.

## Soft history

Because names can be removed without the bytes leaving the holo, a bad walk is usually a step back, not a funeral. The steward's reconstructible history and the holo's snapshots are the same comfort at two heights: one for the files, one for the machine that serves them. Forgetting remains explicit, on a clock you set, for chunks no moment still references.

## A node returns

A machine reboots, or you move to the next glass after a fault.

1. The device key says this hardware is still itself.
2. If you are there, a proof refreshes the lease. If you are not, the surface shows the house, not your private scene.
3. Volumes mount from the holo. The last snapshot is the file continuity.
4. GlassSpear rebuilds the scene from policy and presence, not from a hibernated framebuffer.
5. Grants are re-taken. They are not assumed to have survived the gap.
6. If this boot is the inactive slot and the health check has not passed, the next start returns to the slot that had.

Nothing in that list requires a person to decide which disk, which IP, or which container runtime. Those are strand details. The person, if they are present, only notices that the room is theirs again — or, if the proof is stale or the jump was absurd, that the room is being careful.
