**Title: [Boundaries] Packing too much into “phase 1” does not save money—it starts the failure**

> Series **Phased ERP & acceptance** · Part 2 · Handbook English edition (2026-10)  
> Part 1: [01 · 19 years in IT…](./01-19-years-in-IT-why-phase-1-ERP-projects-fail.md)  
> Chinese edition: [02 · 边界…](../../zh/16-专栏与发布/02-边界-一期塞太多不是省钱是烂尾的开始.md)

After the consolidated piece on phasing tables and the seven-line checklist, a common reply was: “We saved the table, but the CEO still says ‘phase 1 is everything,’ and the project keeps sliding.”

This article is only about **boundaries**. If boundaries are not on paper, the prettiest matrix is decoration. Below: patterns familiar in domestic trading and manufacturing—and two lessons from an **overseas manufacturing go-live** on Odoo where finance and UAT were stricter than the business demo.

### The dinner-table line

Same trading contact. Annual fees on a major suite; three departments, three ledgers. He wants a change but fears another wreck.

I asked: if acceptance were in three months, **what would you personally sign for?**  
Long pause: “Inventory and reports, I guess.”  
“Production? Attendance? Tie the overseas entity in?” Wave of the hand: “All of it—as fast as possible.”

That is where many failures start. **Not because the logo on the contract was wrong**, but because “phase 1” loaded different modules in every head—and no attachment listed them.

### Phasing is not “buying fewer features”

The costly misunderstanding: phasing means “cheaper because fewer boxes checked.”

Phasing means **not letting scope inflation, two ledgers, and whole-company habit change detonate in the same quarter.** Overseas adds another rule: **the person who can finally sign is often finance.** Operations can look green while month-end close or statutory reporting is not acceptable—then phase 1 is not delivered.

In Saudi Arabia and similar markets, finance and audit typically ask early about **Odoo Saudi localization (`l10n_sa`)**, **ZATCA e-invoicing (Fatoora)**, and **GOSI (social insurance) on payroll**—not as IT hobbies, but as close prerequisites. Whether production credentials, declarations, and module purchases match *your* entity is case-specific; what matters for the project is **writing them into the blueprint and UAT**, not sales assurances.

Branded suites, annual clouds, or open Odoo: **verbal phase 1** fails the same way.

### Failure mode 1: Excel still closes the month

Orders and shipments work; sales celebrates. Finance adjusts freight and rebates in spreadsheets. Month three reconciliation blows up; leadership blames “the system.”

The contract never said **from which month numbers in the system are authoritative.**

I failed this as customer IT once; as implementer I have seen payment held on “acceptance not recognized.” **Without a written close policy, IT owns the blame**—domestic or overseas.

### Failure mode 2: “We went live” is not acceptance

Sales: flows work. Warehouse: scanning. Finance: reports wrong. Contract: “implementation complete, one training.” No UAT scripts, no sign-off.

The PM says live; finance says live ≠ close.

Overseas, a sales invoice may need a full **ZATCA** chain—XML generation, signing, reporting or sandbox validation, status and QR write-back. Local finance will not nod if any step is fuzzy. **Acceptance deliverables must be defined**, not assumed from a go-live banner.

### Overseas lesson 1: finance was not in the blueprint early enough

Cross-border ERP is not “same as HQ, different language.” **Chart rules, allocation, and what “done” means for finance** shape phase 1.

Our internal line was clear: **delivery closes when finance can operate compliantly**—inventory and HR must still land where finance can sign.

Looking back, the regret is familiar: **a finance owner with signing authority was not deep enough in discovery early enough.** Items that should have been decided once kept reopening:

- ZATCA: must phase 1 issue compliant e-invoices, or internal books first and Fatoora production later?
- GOSI: Saudi nationals only, or expatriate rules and employer/employee split accounts fixed up front?
- Freight, insurance, customs—cost vs expense and which GL accounts?

Scope, allocation, and COA rules stayed unstable; meetings multiplied. That is the twin of **“phase 1 does everything” in the room**: without finance locking boundaries at the start, every module adds a late cut.

### Overseas lesson 2: one untested voucher path costs a week

Before go-live UAT, local tax practice is not a template swap. With **`l10n_sa`**, each line of business should reach **posted entries**: sales, purchase, stock, HR, assets, expenses, FX, customs-related charges, freight allocations—who clicks what, which accounts, which consolidations.

Two scenarios finance actually gates (generic chains, no internal doc IDs):

1. **Sales → ZATCA**: order/delivery → customer invoice → e-invoice payload → sign/report (or sandbox) → status/QR back. “We can print PDF” is not the same as finance acceptance.
2. **Payroll → GOSI**: attendance and payslip → base, allowances, OT, **employee GOSI deduction** visible → accrual to **GOSI payable and expense** → payment clearance. UAT must cover employee categories, not one sample ID.

Lessons we took seriously:

- **Business action → journal entry** coverage, including invoicing and social insurance paths.
- Overseas finance is cautious on **VAT, audit trail, e-invoice state**; sign-off cycles run longer than in many domestic projects.
- Rules not frozen early push **UAT completion and voucher sign-off**—and the calendar slips.

“Warehouse is live” is a milestone for operations; for finance it can mean **not ready to sign**.

### Failure mode 3: “Finish phase 1” in one meeting

CRM into phase 1, MES into phase 1, attendance, costing—five UAT rounds, everyone’s wish list on one slide. **Scope creep with a timeline that never fit.** “All-in phase 1” often costs more; overseas adds **rework from tax and compliance gaps**.

### It is not “wrong vendor”

Blaming the product is easy. Annual suites and open source share the same failure modes: **written boundaries, change control, acceptance artifacts finance can recognize.** Production certs, GOSI accounts, Enterprise modules—**belong in blueprint appendices and UAT lists**, not hallway “we can do that.”

**Align phase 1/2 and finance sign-off criteria before debating man-days.**

### Two rules (overseas and domestic)

1. **Blueprint rule:** A finance leader who can **finally approve** scope joins early—COA, allocation, phase split in attachments, fewer mid-project “version 7” fights.
2. **UAT rule:** Against local books and enabled compliance features (e.g. **`l10n_sa`**, **ZATCA/GOSI** as scoped), test **modules, scenarios, and voucher chains**; treat **compliant reporting, close, and reviewable invoice/social-insurance states** as go-live bar—not only “sales clicked through.”

Not exporting yet? Still do two things: ask IT **what must be signable in three months**, and **email or attach** the phase 1/2 list. Deeper tables and checklists may follow in later pieces.

### Closing

Undefined phase 1 means eternal phase 2.

Domestic: watch **paper boundaries**. Overseas: also **finance in the blueprint** and **UAT through vouchers**—with **ZATCA, GOSI, and similar items explicitly in scope and tested on realistic documents**, not slide promises.

Part 1 has the module table and seven-line self-check. If parallel ledgers, scope sign-off, or overseas finance close are stuck, [duodoo.tech](https://www.duodoo.tech) · [contact](https://www.duodoo.tech/contactus) · zou.jason@qq.com

---

**Jason Zou** · **DuodooTekr**

`#Odoo` `#ERP` `#ZATCA` `#GOSI` `#DigitalTransformation`
