# Planting log

What was deliberately introduced into the corpus, by type and location.

**This file is not the answer key.** It records what the corpus author put in.
The key — which statements are checkable, which are supported, and where the
support lies — is authored separately and by hand, per §8.5 of the Solution
Design Report. A corpus author necessarily knows what they planted; the
separation that matters is between the party defining ground truth and the
model doing the finding.

This log was model-drafted as part of writing the documents. The key was not.

## P2-demo — the nine defect types from §8.1

| # | Defect type | Where | What to expect |
|---|---|---|---|
| 1 | Billed amount transposed against its bill | Letter: Harbor Physical Therapy `$4,820.00`. Exhibit 9 bill: `$4,280.00` | Value mismatch finding showing both figures |
| 2 | Specials total that does not reconcile | Letter: stated medical specials `$11,950.00`; the four lines sum to `$11,550.00` | Arithmetic finding naming the `$400.00` difference |
| 3 | Assertion with no support anywhere | "Ms. Alvarez continued to report headaches through May 2026." No exhibit covers May | Unsupported finding with a search record attached |
| 4 | Cited exhibit superseded | Exhibit 9 (`E09_pt_bill.txt`, issued 05/02) is superseded by `E12_pt_bill_corrected.txt` (issued 05/14) | Currency finding, proposed and awaiting human confirmation |
| 5 | Exhibit indexed but not attached | Index lists Exhibit 12, "Discharge Summary, Harbor Physical Therapy". No such file exists | Indexed-but-absent finding at registration |
| 6 | Attached but cited nowhere | `E90_pharmacy_receipt.txt` and `E91_intake_notes.txt` | Two uncited-attachment findings |
| 7 | Same record attached twice | `E02_er_record.txt` and `E92_beacon_ed_copy.txt` are byte-identical | Duplicate-pair finding; no automatic removal |
| 8 | Mismatch the documents cannot settle | Physical therapy start date: treatment records (Exhibit 8) show visit 1 on 02/23/2026; the billing statement (Exhibit 9) gives dates of service beginning 02/24/2026; the letter says 02/24 | Finding left open and escalated; the system must select neither |
| 9 | Deliberately ambiguous classification | "She has been unable to lift her daughter since the collision." Sourced only from the internal intake note, which is an unverified client account | Classification is genuinely arguable; this is the statement the fourth scenario in §2 turns on |

## P3-hard — cases that are hard rather than defective

| Case | Where | Why it is hard |
|---|---|---|
| Client-sourced assertion, attributed | "Ms. Raman told our office she has been unable to type for extended periods" | Explicitly attributed to the client. Is it unsupported, or supported as a report of what she said? |
| Reference outside the exhibit set | "Her symptoms were worse than those she experienced after a similar incident in 2023." | Nothing in the package can confirm or refute it |
| Support split differently from the citation | Letter cites `$310.00` and `$215.00` separately; Exhibit 3 is a combined bill totalling `$525.00` | Both figures appear as line items; the support exists but not in the shape cited |
| Argument among facts | "Any reasonable driver would have seen Ms. Raman's vehicle." | Characterization sitting in a liability paragraph otherwise made of facts |
| Unreadable file | `E06_scanned_page.bin` | Must quarantine with a reason and continue processing the rest |

## P1-clean

Nothing is planted. Every figure reconciles, every cited exhibit is attached and
current, and no exhibit is uncited. The package exists to prove that an absence
of findings is reported as an absence of findings and never as a clean bill of
health (V1).
