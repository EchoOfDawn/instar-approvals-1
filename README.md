# instar-approvals — custody of the Instar 2.0 approver passkeys

This repository holds exactly one record: `approvers.json`, the list of passkeys whose signatures the Instar 2.0 preview accepts as the operator's explicit "yes" on its phone approval page.

## Custody contract (P-01: the agent never administers its own safeguards)

- **Owner and sole writer: Justin (GitHub `JKHeadley`).** Only his account can merge changes.
- **The repository is public, so anyone can read it; only Justin can write.** The agent (GitHub `EchoOfDawn`) is not a collaborator. It cannot push, merge, or change settings. It proposes changes only by a pull request from its fork.
- **Every change is a pull request that Justin merges himself.** The agent reads the record at the merged commit on the default branch; it never trusts a branch, a fork, or a local copy.
- **Justin created this repository in his own account from a template the agent prepared.** The agent never held any access to it; the verification (a refused push, an unmergeable PR, a refused permission change) is recorded in the Instar 2.0 plan of record as the P-01 check for the approval page.

## Record format

`approvers.json`: `schema`, `rpId` (the dashboard host the passkeys are bound to), `operator` (who may approve), and `passkeys` (each: `id` = credential id, `publicKey` = COSE/SPKI public key, `label`, `addedAt`). It starts empty; Justin's first passkey is added by a pull request after he enrolls it on the page.
## If you lose your phone

Losing a phone never locks you out, because no single device is the only way in:

- **Keep at least two passkeys enrolled** (your phone and your Mac, or a hardware key). Apple passkeys sync through iCloud Keychain, so a new phone signed into the same Apple account already has them.
- **This repository is the recovery path.** From any computer signed into GitHub (which has its own recovery codes), you can add a new passkey to `approvers.json` and remove a lost one. No phone is needed.
- **A missing passkey never stops the running system.** Only the changes that need your approval wait until you approve them with another passkey or restore one here.
