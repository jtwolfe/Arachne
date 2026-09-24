# Surfaces

A surface is anywhere attention lands. A wall glass, a monitor on a desk, a phone in the hand, a buddy drawn over a desktop that still has windows. Arachne cares that these feel like one arrival, not four products that each have a login.

## GlassSpear — the room

Environmental computers are the ones that stay on so a room can be useful: kitchen, bedside, living room, hall. They are not "my laptop." They should not grow a desktop.

GlassSpear treats them as surfaces that show **scenes**. A scene is a named layout and the pages that belong in it, for the people actually there. Shared house content and a personal page can be on the same glass without becoming the same session. If two people are in the room, private pages do not get casual. If you leave, the glass returns to the house, or to whoever is still there.

Presence is the interface. Occupancy and identity decide what appears, so the daily path has no login theater. Voice and a thin remote are how you ask for a different scene. They are not how the system guesses a shell command. The ask is handed to Vikett as a choice among scenes that exist.

Most of what a scene shows can be a page — often a web app — because the content is not the precious part. The precious part is the holo behind it, and the policy that decided this page was legal on this glass for this person. The layout engine underneath can be an ordinary compositor. The product is the control of attention, not a new window manager for enthusiasts. A dev machine and a game machine are out of scope on purpose. Those stay workstations.

## BuckyBoi — the workstation

Some machines are supposed to have windows. On those, the presence should still be a person, not a password dialog.

BuckyBoi is that presence: a small overlay that can see, hear, and take a gesture, for one person or several, and that fails closed. Enrolled people can wake listening and sensitive actions. Anyone else gets a machine that does not obey. The buddy does not walk a door. It tells Vikett and the session layer who is standing there. It is not the identity record and it does not store the long-term key of the household.

This split matters in a room with both kinds of computer. The wall glass is GlassSpear. The desk is a workstation with a buddy. You are the same person on both because both consumed the same proof. They do not each grow a user database.

## The phone

Two roles, and they should not be melted together.

**Carrier** is the vault. It pairs machines, holds the key, presents claims, and eventually carries a continuity pack for a visit. You can put every other device in the house to sleep and still prove yourself with this one. It does not try to be the window manager of the kitchen.

**glass**, the phone pane, is the surface you hold. It is the assistant you raise when the room has no glass of yours, or when the thing you need is private enough that a wall is the wrong place to show it. Long-press, ask, put away. It is a scene with one viewer, not a second copy of the house.

A pocket vault that silently opens because it recognized the office Wi-Fi is a failure. Proximity can be a hint. It is not an unlock. Unlock stays a proof on the device.

## What shows where

| You are… | The surface should… | It should not… |
| --- | --- | --- |
| Alone in the kitchen | Bring your morning scene to the nearest glass | Mirror your private pages onto every glass in the house |
| With a guest | Keep shared scenes, hide private modules | Explain the guest's presence by creating them an account |
| At a desk | Let the buddy gate listening, leave the windows alone | Turn the workstation into a kiosk |
| In a strange building | Show only what that domain granted | Cache your home scene on their disk "for convenience" |
| Offline, on your own laptop | Open a narrower local session from the signed record | Pretend the lease was checked |
| Handing a child a machine | Apply the household domain even at school | Require the parent to be reachable for the rules to exist |

## Hand-off

Walk from the kitchen to the desk and the scene should follow only if the desk is a surface that is allowed to show it. Walk out of the house and the lease on the kitchen glass should lapse. Pick up at the office and you are in a different domain; the hand-off is a new proof against the same record, not a remote desktop of your kitchen.

Task context — the writing you were in the middle of — can follow you when the volume is yours and the new place's policy allows that application. The pixels do not have to follow you. The volume does. GlassSpear recreates the scene. It does not stream a framebuffer across the web as the main idea.

## Sensing, and the line it will not cross

Cameras, radar, a microphone, a voice match: these are how a room avoids asking you to type. They are also how a room becomes a surveillance product if the raw signal leaves.

The rule is local match, minimal claim outward. The sensor decides "this enrolled person" or "someone unknown" or "more than one." What leaves the room, if anything leaves, is a claim already in the identity model — present here, now — not the picture and not the audio. Speaker recognition is a hint. It is not the lock. The lock remains the key you unlock, on a device or with a proof the domain asked to escalate to.

BuckyBoi's enrollment lives with the people of that machine. GlassSpear's notion of who is in the house has to agree with it, and with Carrier, or the web will feel like three houses. One enrollment, projected. Not three.
