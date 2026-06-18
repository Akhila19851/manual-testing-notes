# Manual Testing — Complete Notes

## 1. What is Software Testing?

Software testing is the process of checking whether a software application works the way it's supposed to — finding bugs before the software reaches actual users.

**Real-life analogy:** Before a shop sells a phone, someone checks the screen, camera, and battery. Same with software — before it goes to customers, a tester checks every feature.

### Key Terms
| Term | Meaning |
|---|---|
| Software | Set of instructions that tells a computer what to do |
| Requirement | Document describing what the customer wants |
| Defect / Bug | Software feature not working as per requirement |
| Error | Mistake made by the developer while writing code |
| Failure | Software crashes or stops working completely |
| Test Engineer (TE) | Person who tests the software manually or via automation |

### Advantages & Disadvantages of Manual Testing

**Advantages:**
- Quality is very good
- Programming knowledge is NOT required
- Human eye catches visual bugs that tools miss
- Best for exploratory & usability testing

**Disadvantages:**
- Time taken is more
- Resource utilization is more
- Tedious and monotonous job
- No consistency across different testers

---

## 2. SDLC — Software Development Life Cycle

**Definition:** SDLC is a step-by-step standard process followed to develop new software.

### 7 Stages of SDLC

1. **Requirement Collection** — Done by Business Analyst (BA)/Product Analyst (PA). BA collects requirements from customer and converts business language into software language.

2. **Feasibility Study** — Done by PM + BA + Architect + Finance Team + HR. Decides whether to accept or reject the project based on resources, technology, and profitability.

3. **Design** — Done by Architect. Two types:
   - **HLD (High Level Design)** — overall architecture (servers, components)
   - **LLD (Low Level Design)** — detailed module-level logic

4. **Coding** — Done by Developers. Code is written based on LLD.

5. **Testing** — Done by Test Engineers. Verify software works as per requirement.

6. **Installation/Implementation** — Done by IT Engineers. Software is deployed at customer's site.

7. **Maintenance** — Done by Developers & TEs. Free service for 6 months–1 year after delivery; charged after that.

### HLD vs LLD

| Aspect | HLD | LLD |
|---|---|---|
| Scope | Whole system | One module at a time |
| Detail | Big picture | Fine detail, logic-level |
| Created by | Architect | Architect/Senior Developer |

---

## 3. SDLC Models

### Model 1: Waterfall Model
Sequential model — each phase completed fully before the next. No backtracking; requirements frozen after Feasibility Study.

**Why "Waterfall"?** Like water flowing only downward, never back up.

**Best for:** Small, simple, fixed-requirement projects.

### Model 2: Iterative / Incremental Model
Software built module by module in repeating cycles. Each cycle: build new module → test it → re-test old modules (Regression Testing).

**Why two names?**
- **Iterative** — same process repeats every cycle
- **Incremental** — software grows bigger every cycle

**Example:** Gmail — Cycle 1: Signup. Cycle 2: Login (+ retest Signup). Cycle 3: Compose (+ retest Login, Signup).

### Model 3: Spiral Model
Extension of Iterative Model + Risk Analysis before building each module. Team analyzes risks before design/coding starts.

**Why "Spiral"?** Each cycle forms a growing loop — looks like a spiral when drawn.

**Example:** Bank login — analyze fraud risk before designing the module.

### Model 4: V and V Model (Verification & Validation)
Every development phase has a matching testing phase planned in parallel.

| Development (Left) | Testing (Right) |
|---|---|
| Requirement Collection | Acceptance Testing |
| Feasibility Study | System Testing |
| HLD | Integration Testing |
| LLD | Unit Testing |

**Why V-shape?** Verification activities (left, going down) + Validation activities (right, going up), meeting at Coding.

### Model 5: Prototype Model
A dummy, non-functional version is built first and shown to customer for approval. Real development starts only after approval.

**Best for:** Unclear requirements or customer new to the business.

### Model 6: RAD Model (Rapid Application Development)
Builds software fast by reusing existing components/templates instead of coding from scratch.

**Best for:** Tight deadlines.

### Bonus: Agile Model
Software delivered in small 2-week sprints. Requirements can change anytime. Most MNCs use this today.

---

## 4. Types of Software Testing

### Top-Level Categories
- **White Box Testing** — done by developers, code is visible
- **Black Box Testing** — done by Test Engineers, code is NOT visible
- **Grey Box Testing** — combination of both

### White Box Testing — Sub-types
- Unit Testing (most important)
- Path Testing (also called "Path Testing" — alternate name for WBT)
- Conditional Testing
- Loop Testing

### Black Box Testing — 11 Sub-types
1. Functional Testing
2. Integration Testing
3. System Testing
4. Acceptance Testing (UAT)
5. Smoke Testing
6. Regression Testing
7. Compatibility Testing
8. Usability Testing
9. Exploratory Testing
10. Globalization Testing
11. Adhoc Testing

**Most important ones to remember:** Unit Testing (White Box), and Functional, Integration, System, Regression, Smoke (Black Box).

---

## 5. STLC — Software Test Life Cycle

### 6 Stages
1. **Requirement Analysis** — TE understands what needs to be tested
2. **Test Planning** — Test Lead creates the Test Plan
3. **Test Case Design** — TEs write test cases
4. **Test Environment Setup** — Setting up test servers/data
5. **Test Execution** — Running test cases, marking Pass/Fail
6. **Test Closure** — Test Summary Report prepared

---

## 6. Test Cases

A Test Case is a set of conditions/steps to verify if a feature works as per requirement.

### Test Case Format
| Field | Example |
|---|---|
| Test Case ID | TC_LOGIN_001 |
| Title | Verify login with valid credentials |
| Pre-condition | User must have valid account |
| Test Steps | 1. Open browser 2. Enter UN 3. Enter PWD 4. Click Login |
| Test Data | UN: test@gmail.com, PWD: Test@123 |
| Expected Result | Home page displayed |
| Actual Result | (filled after testing) |
| Status | Pass/Fail |

---

## 7. Defect Life Cycle

**Defect** = When software doesn't work as per requirement.

### Stages
New → Assigned → Open → Fixed → Re-test → Closed
(or: Reopen / Rejected / Deferred / Duplicate)

| Status | Meaning |
|---|---|
| New | TE finds and logs the bug |
| Assigned | Lead assigns it to a developer |
| Open | Developer starts fixing |
| Fixed | Developer completes the fix |
| Re-test | TE verifies the fix |
| Closed | Bug confirmed fixed |
| Reopen | Bug still exists after "Fixed" |
| Rejected | Not a bug / works as designed |
| Deferred | Valid bug, fixed in next release |

---

## 8. Introduction to Automation Testing

**Definition:** TE writes code/script using tools like Selenium/QTP/Appium and runs it against the software. Tool automatically tests and gives Pass/Fail result.

### Manual vs Automation

| Manual Testing | Automation Testing |
|---|---|
| Done by humans | Done by scripts |
| Slow | Fast |
| No programming needed | Programming knowledge required |
| Good for new features | Best for Regression Testing |

### Tools
- **Web Automation:** Selenium (free, open source), QTP/UFT (paid)
- **Mobile Automation:** Appium, Selendroid
- **API Testing:** Postman, Python `requests` library

---

## Interview-Ready One-Liners

- **SDLC:** Software Development Life Cycle — step-by-step process to develop new software.
- **STLC:** Software Test Life Cycle — sequence of testing activities within SDLC.
- **Regression Testing:** Re-testing old features after a new change to ensure nothing broke.
- **Smoke Testing:** Quick check on a new build to see if it's stable enough to test further.
- **UAT:** User Acceptance Testing — done by customer to approve software before release.
