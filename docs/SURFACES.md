# GlassSpear

GlassSpear is how Arachne shows itself. Environmental computers — the glass in a kitchen, by a bed, in a room — are not laptops. Desktop management should disappear on them. A place that knows who is present, and which surface they are near, *is* the interface.

Arachne does not redesign GlassSpear. It says what a scene is allowed to do to storage, identity, and action.

## Surfaces, scenes, pages

| Word | Meaning |
| --- | --- |
| Surface | A display endpoint. It runs a real system underneath. The product is not a new kernel on that box. |
| Scene | A named layout and the pages that belong in it. Not a pile of windows someone last left open. |
| Page | A slot in a scene. Often a web app. Sometimes something native. A page is also a Vikett role: the application id that application-space claims use. |
| Profile | What a person may see on glass in this place: which scenes, which private pages. The profile is a view of rules, not a home directory. |
| Presence | Who is near which surface. It selects scenes. It does not unlock a key by itself, and it does not bind a volume. |

Shared pages and personal pages can share a surface and must not share a volume. The subject on the claim is different. A house timer is the place's application space. A person's writing is that person's application space. GlassSpear lays them out. HoloFS keeps them apart. The rules tool is what refused to bind the writing into the house volume.

## What happens when you arrive

1. Something in the place asserts that a person is at a surface. How it senses is GlassSpear's concern. Arachne only requires the assertion to be a subject the identity tool can check, not a guess the compositor acts on.
2. The identity tool evaluates the proof under this place's catalogue. No account is created. Guest, resident, or someone allowed to maintain the machine are different prunes of the same catalogue.
3. For every page the chosen scene wants to show, GlassSpear asks for a bind of application space. It does not mount anything itself. Pages whose claims do not walk are not shown. A scene with holes is acceptable. A scene that fills holes from user space or OS space is not.
4. Vikett remains the way a person *changes* what is showing. "The other scene." "This page, on the other surface." Those are authored pages. GlassSpear applies the take. If the take needs a bind that is not live, the rules tool says so and the glass does not improvise.

Leaving a surface drops the session's mounts. The next person does not inherit them. The glass returns to a scene whose subject is the place, or to whoever is still there.

## What GlassSpear will not hold

- OS space. The machine boots and is maintained outside the scene model. A scene has no path into it.
- User space, as a tree to browse. Personal pages get application volumes and, only through a projection page, a named slice.
- The rules. GlassSpear can know which scene is appropriate. The catalogue of what that implies for storage lives in the rules tool, modeled on Vikett, not in a layout file that happens to list filesystem paths.
- The packet path. If a page's volume is remote, GlassSpear still only asks for a bind. Harmonics is underneath the bind, not a feature of the scene.

A workstation that still has windows is out of scope for GlassSpear, and it is out of scope for this concept. Arachne does not require a second presence product on the desk. If a person uses a machine that is not environmental glass, that machine is still the same three spaces and the same rules. It simply does not pretend to be a scene OS.

## Two people, one glass

Both are subjects. The surface may show a shared scene plus, if the rules allow, a personal page for the person the surface considers primary. The other person's application volumes are not mounted. Private pages do not appear because a microphone heard a name. If the place cannot decide a single subject cleanly, it shows only pages whose subject is the place. That failure mode is a scene, not an error dialog, and not a merge of volumes.

## A page is not a grant

GlassSpear authors scenes as layouts and content. Vikett authors interaction pages, including "show scene" and "focus page." The rules tool authors which of those are allowed to bind storage. The three lists are written by people, reviewed as lists, and kept small. A scene file that embeds a filesystem path, a shell line, or a Dialtone address with a key in it is not a scene. It is a hole. Content references a page id. The page id is what the claim's role slot carries. Resolution to a volume happens only after a walk.
