# RFID Inventory Accuracy Pilot

**Role:** Inventory Control Manager  
**Format:** Supply chain analytics portfolio case with synthetic data

A grocery retailer sees recurring differences between the inventory in its system and what employees find on the shelf. This case develops a small RFID pilot to test whether better visibility at receiving and during stock counts can improve inventory accuracy.

## 1. Investigate the discrepancy

| Possible cause | How to check it before the pilot |
| --- | --- |
| Receiving transactions are posted late | Compare delivery confirmation, receipt posting and physical count timestamps. |
| Stock is moved without updating its location | Trace a sample of transfers from the receiving area to the backroom and sales floor. |
| Tags are missed, duplicated or mapped to the wrong SKU | Compare a controlled set of tagged units with the reader output and SKU master. Include products with metal packaging or high liquid content. |
| Manual adjustments hide recurring process errors | Review adjustment reasons, timestamps and approvals for the same SKUs over several count cycles. |

These are hypotheses. A missing RFID read is an exception to investigate before changing an inventory balance.

## 2. Select pilot SKUs

Measure baseline mismatch frequency as the number of audited SKU–location counts with unequal system and physical quantities, divided by the number of audited counts. Use product movement and read feasibility to decide which mismatches to investigate first.

| Fictional SKU | Weekly unit movement | Mismatched baseline counts | Pilot decision |
| --- | ---: | ---: | --- |
| A101 · Boxed cereal | 420 | 8 of 20 (40%) | Start here. High movement and frequent discrepancies. |
| B205 · Bottled juice | 360 | 6 of 20 (30%) | Test tag placement and read reliability before including it in the live pilot. |
| C310 · Canned beans | 270 | 5 of 20 (25%) | Test packaging interference separately so reader performance can be diagnosed. |
| D420 · Dry pasta | 110 | 2 of 20 (10%) | Lower-priority candidate. Track it for context, with a separate matched comparison group for evaluation. |

## 3. Set up the inventory controls

1. Link each unique tag ID (EPC) to the correct SKU in the item master. Record the reader zone, event type and timestamp for each read.
2. Consolidate duplicate reads from the same movement. Match the resulting event against the corresponding receipt or transfer.
3. Route unmatched reads and transactions to an exception queue. Record the resolution before making any inventory adjustment.
4. Use independent physical cycle counts as the reference. Align the count with the system snapshot so stock movements during the count do not distort the comparison.

## 4. Evaluate the pilot

| Measure | Definition | Why track it |
| --- | --- | --- |
| SKU–location inventory accuracy | Audited SKU–location counts with exact quantity agreement ÷ all valid audited SKU–location counts | Measures whether recorded inventory matches physical stock. |
| RFID event match rate | Eligible reference movements with a matching RFID event ÷ all eligible reference movements | Measures how consistently the process captures movements. Multiple reads of one movement count once. |
| Count effort | Staff minutes per valid audited SKU–location count | Shows whether accuracy changes come with a change in labour effort. |

Use the same count rules before and after rollout. Compare the pilot SKUs with similar SKUs or locations that continue using the existing process, and record promotions, stock movements and other operational changes during the test.

**Worked example using fictional results.** In the baseline window, 36 of 50 audited counts match the system (72%). In the pilot window, 43 of 50 match (86%), a rise of **14 percentage points**. A matched comparison group rises from 38 of 50 (76%) to 41 of 50 (82%), a rise of **6 percentage points**. The difference in changes is **8 percentage points**. This illustrates the evaluation method. With small samples and no random assignment, the difference alone cannot establish an RFID effect.

Review the accuracy change alongside event match rates and count effort. If discrepancies persist, use the exception records to decide whether the next change should address tag placement, event matching or the receiving process.

---

This portfolio case uses fictional products, quantities and pilot results. It illustrates the proposed controls and evaluation design.
