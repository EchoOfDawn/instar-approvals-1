# instar-approvals — custody of the Instar 2.0 approver passkeys

This repository holds the Instar 2.0 phone approval page and its external verifier. After setup, `installation.json` and one file per passkey in `approvers/` record which passkeys the verifier accepts. Connecting its receipts to the running preview remains separate installation work.

## Custody contract (P-01: the agent never administers its own safeguards)

- **Owner and sole writer: Justin (GitHub `JKHeadley`).** Only his account can merge changes.
- **The repository is public, so anyone can read it; only Justin can write.** The agent (GitHub `EchoOfDawn`) is not a collaborator. It cannot push, merge, or change settings. It proposes changes only by a pull request from its fork.
- **Code changes are pull requests that Justin merges himself; the passkey record counts only when Justin commits it directly.** The verifier reads `installation.json` and `approvers/` at the current commit on the default branch and ignores any version that reached it through a pull request; it never trusts a branch, a fork, or a local copy.
- **Justin created this repository in his own account from a template the agent prepared.** The agent never held any access to it; the verification (a refused push, an unmergeable PR, a refused permission change) is recorded in the Instar 2.0 plan of record as the P-01 check for the approval page.

## Record format

`installation.json` (made by the [setup page](https://jkheadley.github.io/instar-approvals/#setup)): the origin and passkey host this page is served from, this repository, the approving GitHub account, and the verifier's public key. `approvers/<id>.json` (one per passkey): the passkey's public key and the evidence that it was created on this page. To enrol a passkey, open the page's `#enrol` on the device that will hold it; the page opens GitHub's editor with the file filled in, and Justin commits it directly to the default branch. A pull request is never how a passkey is added: the verifier ignores it.

## If you lose your phone

Enrol a passkey on your phone and Mac before relying on approvals, so either one still works; Apple
passkeys also sync through iCloud Keychain. If every passkey is lost: from any computer signed into your
GitHub account (GitHub has its own recovery codes), open the [enrol page](https://jkheadley.github.io/instar-approvals/#enrol), add a new passkey and
commit its file from the page. To retire a lost device, delete its file in `approvers/`. A missing passkey only pauses the changes that need your approval; nothing running stops, the agent keeps working within its limits, and "stop" in Telegram keeps working.
