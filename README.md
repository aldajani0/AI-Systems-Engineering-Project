# 🏛️ Multi-Agent Document Auditor for National Data Index

<p align="center">
  <strong>AI-Powered Multi-Agent System for Auditing Government Evidence Packages</strong>
</p>

<p align="center">
  <em>Supporting Saudi Government Entities in validating Nadhee National Data Index submissions.</em>
</p>

<p align="center">

![Status](https://img.shields.io/badge/Status-In%20Development-blue)
![Architecture](https://img.shields.io/badge/Architecture-Multi--Agent-purple)
![AI](https://img.shields.io/badge/AI-Agentic%20AI-green)
![Domain](https://img.shields.io/badge/Domain-Data%20Governance-orange)

</p>

---

# 📌 Project Overview

Government entities in Saudi Arabia must periodically submit supporting documents to prove their maturity level across the **"Nadhee" National Data Index** (المؤشر الوطني للبيانات). This process is error-prone and time-consuming because:

* Each maturity level (0–5) requires a **cumulative** set of supporting documents — a claimed level requires the documents of that level **plus all lower levels**.
* Every document must follow a strict **naming/coding convention** (e.g., `DG.C.1.1`) tied to its role in the index.
* Some documents (coded with **"C"**) affect the entity's **compliance score** independently of the maturity score, even if the entity did not claim that maturity level.
* Each document must satisfy specific **minimum content requirements** (acceptance criteria) to be considered valid.

> ⚠️ **A single missed or mislabeled document can incorrectly lower an entity's official maturity or compliance score.**

**Our System** is a multi-agent AI system that acts as a *virtual auditor*: it validates an entity's document package **before** official submission, checking completeness, naming, and content against the official Nadhee acceptance criteria — with a mandatory human approval gate before anything is finalized.

### 🎯 Target Users

> Data management/governance coordinators in government entities responsible for preparing and submitting Nadhee evidence packages.

---

#  نظرة عامة على المشروع

تلتزم الجهات الحكومية في المملكة برفع وثائق داعمة بشكل دوري لإثبات مستوى نضجها ضمن **المؤشر الوطني للبيانات "نضيء"**. هذه العملية مرهقة وعُرضة للأخطاء للأسباب التالية:

* كل مستوى نضج (0–5) يتطلب مجموعة **تراكمية** من الوثائق الداعمة — فاختيار مستوى معين يعني وجوب رفع وثائق ذلك المستوى **بالإضافة إلى وثائق كل المستويات الأدنى منه**.
* يجب أن تلتزم كل وثيقة بقاعدة **تسمية/ترميز** صارمة (مثل `DG.C.1.1`) مرتبطة بدورها ضمن المؤشر.
* بعض الوثائق (التي تحمل رمز **"C"**) تؤثر على **درجة الامتثال** الخاصة بالجهة بشكل مستقل عن درجة النضج، حتى لو لم تدّعِ الجهة ذلك المستوى تحديداً.
* يجب أن تحقق كل وثيقة **الحد الأدنى من العناصر المطلوبة** (معايير القبول) حتى تُعتبر صالحة.

> ⚠️ أي وثيقة مفقودة أو مسمّاة بشكل خاطئ قد تُنقص خطأً من نتيجة الجهة الرسمية في النضج أو الامتثال.

**نظامنا** هو نظام ذكاء اصطناعي متعدد الوكلاء يعمل بمثابة "مدقق افتراضي": يتحقق من حزمة وثائق الجهة **قبل** الرفع الرسمي، من ناحية الاكتمال والتسمية والمحتوى مقارنةً بمعايير القبول الرسمية لمؤشر نضيء — مع بوابة اعتماد بشري إلزامية قبل اعتماد أي شيء نهائياً.

### 🎯 المستخدمون المستهدفون

> منسّقو/مسؤولو إدارة البيانات وحوكمتها في الجهات الحكومية المكلّفون بتجهيز ورفع حزم الأدلة الداعمة لمؤشر نضيء.

---

# 🗂️ Project Structure

> 🚧 *(Structure will be done once implementation begins )*

---

# 🏗️ Architecture Diagram

> 🔧 **TBD** — Will be added once the system is implemented .

### High-level Component View

```text
           User Input
                │
                ▼
        [ Coordinator Agent ]
                │
                ▼
      [ Requirements Agent ]  ← RAG: Nadhee Knowledge Base
                │
                ▼
   For each uploaded document (parallel):
        [ Classifier Agent ] → [ Content Validator Agent ]
                │
                ▼
          [ Reviewer Agent ]
       (Reflection / Self-Critique)
                │
                ▼
        Final Report
                │
                ▼
       Human Approval Gate
                │
                ▼
       Official Submission
```

---

# 🔄 Workflow Diagram or Explanation

### 1️⃣ Input & Planning

The user specifies the domain, criterion, and claimed maturity level. The Coordinator Agent triggers the Requirements Agent, which — via RAG over the Nadhee criteria — builds the **full cumulative checklist** of required documents (target level + all lower levels + any compliance-only "C"-coded documents).

---

### 2️⃣ Per-document Parallel Validation

For every uploaded file, the Classifier Agent checks naming convention, file type/format, and maps it to the correct checklist item. In parallel, the Content Validator Agent extracts the document's text and checks it against the minimum required elements for that specific document.

---

### 3️⃣ Conditional Routing / Retry Loop

If a document is incomplete or mismatched, the workflow routes back to request re-upload (max 3 retries) instead of halting the entire process.

---

### 4️⃣ Decision Point

Once all documents are processed, the system checks:

> **Are all required documents (maturity + compliance) present and valid?**

---

### 5️⃣ Reflection & Final Review

The Reviewer Agent re-examines any rejection/acceptance decisions from the previous agents (self-critique) to reduce false positives/negatives, then compiles a clear, cited report (which acceptance-criteria clause justified each decision).

---

### 6️⃣ Human Approval Gate

> 👤 No package is marked **"ready for official submission"** without human sign-off.

---

# 🤖 Agents and Their Roles

> 🔧 **TBD**

| Agent                          | Responsibility                                                                                                                                                                                      |
| ------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 🎯 **Coordinator Agent**       | Orchestrates the end-to-end workflow; routes tasks between agents; aggregates the final output for the user.                                                                                        |
| 📋 **Requirements Agent**      | Determines the exact cumulative list of required documents for the claimed maturity level, including lower-level and compliance ("C"-coded) documents, using RAG over the official Nadhee criteria. |
| 🗂️ **Classifier Agent**       | Validates each uploaded file's naming (reference code), format, and maps it to the correct checklist item.                                                                                          |
| 🔍 **Content Validator Agent** | Reads each document's content and verifies it satisfies the minimum required elements defined in the official acceptance criteria.                                                                  |
| 🧠 **Reviewer Agent**          | Applies reflection/self-critique over the other agents' decisions, resolves inconsistencies, and produces the final explainable report before human approval.                                       |

---

## 🧠 Reasoning Patterns Used

### 📋 Plan-and-Execute

Coordinator/Requirements Agent builds the full checklist before execution begins.

### 🏛️ Hierarchical Delegation

Coordinator delegates each document to the Classifier → Content Validator sub-pipeline in parallel.

### 🔄 Reflection/Self-Critique

Reviewer Agent re-evaluates prior agents' accept/reject decisions before finalizing.

---

# 🛠️ Technologies & AI Tools Used

> 🔧 **TBD** — To be finalized during implementation. Planned stack:

| Category                  | Technology                                                            |
| ------------------------- | --------------------------------------------------------------------- |
| ⚙️ **Orchestration**      | LangGraph                                                             |
| 🧠 **LLM**                | (to be decided)                                                       |
| 📚 **RAG**                | Vector store over Nadhee domains/criteria/acceptance rules            |
| 📄 **Document parsing**   | PDF/Word text extraction tool                                         |
| 🔐 **Security**           | Prompt-injection detection, input validation, PII masking, RBAC       |
| 📊 **Logging/Monitoring** | Structured execution logs (tool calls, timings, errors, retry counts) |

---

# ⚙️ Installation and Setup Instructions

> 🚧 Will be completed once the codebase is implemented.

---

# ▶️ How to Run the Project

> 🚧 Will be completed once the codebase is implemented.

---

# 🚀 Future Improvements

* Automatic cross-document consistency checking (e.g., date/approver mismatches between related documents).
* Confidence-score thresholds that auto-escalate low-confidence validations to human review.
* Dashboard for tracking submission status across measurement cycles.
* Support for additional Nadhee domains beyond the initial pilot criterion.

---

# 🔗 SDAIA Academy GitHub Repository

<p align="center">

https://github.com/SDAIAAcademy

</p>

---

<p align="center">
  <strong>🇸🇦 Built for Smarter Data Governance</strong>
</p>
