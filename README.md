# Source removal test

Test bed for proposed additions to [keiyoushi/issue-moderator-action](https://github.com/keiyoushi/issue-moderator-action),
from the `source-lifecycle` branch of [hazptr/issue-moderator-action](https://github.com/hazptr/issue-moderator-action/tree/source-lifecycle).

The repository is shaped like keiyoushi/extensions-source: fake extensions under `src/<lang>/<name>`,
an `index.json` in the extension repo format, keiyoushi's issue forms, and its issue moderator workflow
with the new inputs. Every issue and pull request here is a test.

| Extension | Site | Used for |
|---|---|---|
| Not Real Scans (en, fr) | example.com | a source that is up; same name in two languages |
| Dead Scans, Other Dead Scans | `.invalid` domains | removal PRs |
| Changed Scans | `.invalid` | changed after its report, so not removed automatically |
| Twin Scans (twice) | `.invalid` | ambiguous reports |
| Broken Search Scans | example.net | a `Site Issues` issue and its duplicates |
| Disputed Scans | `.invalid` | `Source is not down` |
| Old Scans | (deleted) | `Previously deleted` |

Removal runs on `workflow_dispatch` here, with `removal-days: 0`; keiyoushi would run it daily with 14.
The `/remove` command checks organization membership, which a user-owned repository cannot pass.
