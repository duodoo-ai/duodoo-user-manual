**Title: [Phased ERP & acceptance] 19 years in IT: why “phase 1” ERP projects fail (and it’s rarely the software)**

> Series **Phased ERP & acceptance** · Consolidated piece · Handbook English edition (2026-10)  
> Chinese edition: [01 · 干了19年IT…](../../zh/16-专栏与发布/01-干了19年IT-我看透了ERP一期烂尾的真相.md)

I flew back from an overseas factory deployment not long ago. On that site we had just closed **phase 1** of an Odoo rollout—inventory, core finance, HR attendance—and passed UAT. We held the line on **not** cramming full manufacturing into phase 1; that took sustained pushback against headquarters and line managers who wanted “everything now.”

Back in Nanjing, a trading-and-light-manufacturing contact vented: years of fees on a well-known commercial ERP suite, yet sales, finance, and warehouse still run on different truths. They want open-source Odoo but fear another failed project.

I asked: **“What exactly does ‘phase 1 acceptance’ mean in your contract?”**  
He had no answer.

Whether you spend heavily on a branded suite or implement Odoo, failures usually share one root cause: **the word “phase 1” means different things to the CEO, sales, IT, and finance—and nobody wrote the same definition down.**

I have been on the vendor side writing code, on the customer side owning outcomes, and now on site for overseas plants. The painful patterns repeat:

- The CEO says “phase 1 covers everything.” Sales promises it to win the deal. Production wants MES, finance wants heavy costing, HR wants performance management—all in phase 1. UAT runs five rounds; departments pass blame; nobody signs.
- The system is “live,” but finance still adjusts freight and rebates in Excel. Three months later numbers do not tie; the CEO says “the system failed”—when the contract never stated **from which month ledger truth lives only in the system**.
- IT is squeezed because the contract says “go-live,” not **test cases, sign-off pages, and a cutover date for parallel runs**.

### 1. Why phasing must be in the contract

When I led IT at an electromechanical trading/manufacturing company in East China, we mixed WMS, light MES, sales, and warehouse in one blob. I learned: **every verbal promise needs a phased list—email or signed appendix.**

Phasing is not “buy fewer modules.” It is **separating three explosions: scope creep, two sets of books, and forcing the whole company to change habits at once.**

Do not expect “all-in phase 1” to save money. Stuffing MES and complex costing into phase 1 delays go-live and can kill inventory and AR/AP that could have worked. **Close the books and run core flows first; refine later** is the rule that holds across vendors.

### 2. A real boundary call: HR attendance in phase 1

At the overseas plant, phase 1 was explicit: inventory, core finance, HR attendance. Deep manufacturing and heavy costing were deferred to phase 2 in writing.

Attendance sounds minor; in an overseas factory it is often **how you close payroll**.

The local time clocks were a legacy island—no clean API, messy exports. HQ required attendance in Odoo before month-end close. The choices were expensive middleware or custom integration. We built a small bridge: extract punches, clean and dedupe, map shifts, push into Odoo attendance. Painful nights on site—but operations could see attendance in near real time and HR could run payroll. **Whether the stack works is not proven in slides; it is proven in code.**

For domestic trading or light processing, the same idea applies: phase 1 proves **books close, main flows run, people are accounted for**—not a three-year digital plan squeezed into six months.

### 3. A practical phase 1 / phase 2 split (manufacturing + trading)

Pure trading: focus on the first rows. With a shop floor: read the later rows carefully.

| Capability | Phase 1 | Phase 2 | Why |
|------------|:-------:|:-------:|-----|
| Inventory / purchase & sales flows | ✅ | | Close books first |
| Core finance / AR & AP | ✅ | | Avoid a second shadow ledger |
| Master data (items, customers, vendors) | ✅ | | Name owners and approvers |
| HR attendance / heterogeneous device data | ✅ | | Payroll and close depend on it |
| Manufacturing orders / MES / shop floor | | ✅ | Needs stable production |
| Costing / standard cost | | ✅ | After production stabilizes |
| Multi-entity / local invoicing (cross-border) | Case by case | Often ✅ | Compliance path is separate |
| Machine data / dashboards | | ✅ | Do not bind to ERP phase 1 |

Branded ERP, annual suites, or Odoo: **draw phase 1 and 2 first, then estimate effort.** “All-in phase 1” often costs more later—I have seen modest phase-1 budgets balloon into seven-figure rework because immature scope was forced in. That is a **project boundary** problem, not a logo problem.

### 4. Overseas site: how we defined acceptance

A manufacturing entity started operations abroad while HQ pushed for speed. We insisted: **sign-off only for inventory + core finance + HR attendance + departmental UAT**; manufacturing depth and costing stayed in a phase-2 appendix.

Before go-live we nailed backup, upgrade window, and who was on site vs remote. For attendance I worked through shift logic with the floor lead so punches mapped cleanly in Odoo.

Not flashy—but **there was paper to sign on acceptance day.** Domestic plants need the same discipline: phase 1 means **books and people under control**, not the entire multi-year roadmap in one phase.

### 5. Seven lines to check before you sign

Print and tick:

1. **Phase 1 and 2 lists** in an appendix—or confirmed email—not hallway talk.
2. **Master data**: who cleans history, who approves, cutoff date.
3. **When Excel stops** for which ledger—the first “system-only” period in writing.
4. **Roles + dry runs**: purchase-to-pay and order-to-cash walked by key users before go-live day.
5. **Parallel period**: if dual-run drags past three or four months, morale and data quality usually rot.
6. **What acceptance delivers**: cases, open issues, signatures—not “feels fine.”
7. **When phase 2 opens**: e.g. after stable volume production—not silent scope added to phase 1.

IT handing this list to leadership beats arguing in chat whether a module “counts as phase 1.”

### 6. Odoo and the “standard + tailored” anti-failure logic

People ask why open Odoo instead of only a big-brand suite.

**Standard modules for a solid base; tailored code where your process differs—that is a value project.**

Many commercial deals are license-first: misfit customization is expensive or blocked; you still pay annual fees. Odoo brings mature inventory, finance, and attendance out of the box; we extend with Python where needed.

**You hold the code and the narrative of your system.** The asset remains yours; another team can maintain it if relationships change.

Nineteen years across shop-floor admin, energy software PM, regulated pharma IT, Yangtze Delta 0→1 digital builds, and now desert sites with satellite IoT and overseas ERP—I know the buyer’s fear: money gone, users revolting, projects stalling.

**Guarding phase-1 boundaries beats another “digital transformation” slogan.**

### Closing

If phase 1 is undefined, phase 2 is forever “almost ready.”

If you are selecting or stuck in acceptance, run the seven checks internally first. If you still lack clarity—or hit hard integration problems (legacy clocks, master data)—reach us via [duodoo.tech](https://www.duodoo.tech) or [contact form](https://www.duodoo.tech/contactus) · zou.jason@qq.com

**Next:** [02 · Scope creep in phase 1](./02-scope-creep-in-phase-1-is-how-erp-fails.md)

---

**Jason Zou** · **DuodooTekr**

`#Odoo` `#ERP` `#DigitalTransformation` `#ERPImplementation`
