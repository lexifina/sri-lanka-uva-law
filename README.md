# Uva Province (Sri Lanka): law history in git

The statutes of the Uva Provincial Council, Sri Lanka, as a git history: one folder per statute, one paragraph per line, so `git blame`, `git log` and `git diff` work line by line. The text is the English text of each statute as published in the Gazette of the Democratic Socialist Republic of Sri Lanka (Extraordinary), Part IV (A), Provincial Councils, and posted by the Uva Provincial Council on its website.

It follows the shared design of [lexifina/global-law](https://github.com/lexifina/global-law).

## What this repository holds

**Statutes as published, not yet a history.** The Council posts each statute as the Gazette Extraordinary that published it; there is no consolidated text. So each statute is one commit holding its text as published ("oldest version available"), credited to the Council, not to an amending law. An amending statute is its own folder; its amendments are not applied to the statute it amends.

| Folder | What |
| --- | --- |
| one folder per statute (by the short title it gives itself) | one file per section (`000-title.md` for the heading, long title and enacting words), or one file `000-text.md` with the whole statute where its sections cannot be told apart reliably |

Statutes are enacted in Sinhala and Tamil as well; this repository holds the English text only. Where a statute says which language prevails, it says so in its own words here. A statute is left out until it can be read reliably (see "How it is checked"); this record holds only part of the Uva Provincial Council's statutes.

## Source

[Uva Provincial Council: statutes](https://www.up.gov.lk/publications/statutes/), each a PDF of the Gazette Extraordinary (Part IV (A)) with a text layer. Each PDF's sha256 is recorded with its version in `data/versions.json`.

## Dates

The original 20 records use Gazette publication dates; their commencement dates have not been reviewed here. The seven additional records use the commencement stated in the source and its recorded Governor approval date, or the express commencement date in the retirement amendment. Dates are at noon in Colombo.

## How it is built

Lexifina reads the sources listed here and records each act's dated versions, and the laws that made each change, in one corpus file. `tools/build.py` writes this repository from that file, and the same corpus always gives the same commit hashes; `REPRODUCE.md` gives the details and the checks. A model (Claude) wrote Lexifina's code; it wrote no legal text, and no model runs when the history is built.

The text layer of each PDF (no OCR) becomes the record. Left out: the Gazette masthead, running heads and the Sinhala/Tamil lines in legacy fonts, page labels, printing footers, the Council Secretary's publication notice, and marginal notes where the statute is kept as one file. Where sections are split, each section file gives its marginal note on the line before the section text.

## How it is checked

Every version is read back from git on the day it took effect and must match the corpus. A second, independent reading of every PDF (a different PDF engine, pdftotext) must contain every paragraph of each statute whole, letter for letter and digit for digit, with nothing in the statute's stretch of the Gazette left out. Results are in `REPRODUCE.md`.

## What "author" means

The author of each commit is the publisher, with an e-mail address that cannot exist; the committer is always Lexifina.

## Limits

Only the statutes as published are here: no later amendments, no consolidation, only the English text, and only the statutes the Council posts with a text layer that pass the check. The Gazette is authoritative.

## Licence

See [LICENSE](LICENSE): official texts of a legislative nature are not protected by copyright under the Intellectual Property Act, No. 36 of 2003, section 8. Source: Uva Provincial Council; Gazette of the Democratic Socialist Republic of Sri Lanka (Department of Government Printing).
