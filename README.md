# Software Design — OBE-Based Question Paper Package

**Course:** Software Engineering  |  **Topic:** Software Design  |  **Level:** Bachelor (BNQF Level 6)
**Full Marks:** 40  |  **Time:** 1 Hour (60 minutes)  |  **Bloom's Taxonomy:** C1 (Knowledge), C2 (Understanding)

**Sources:** `SoftEng-Design.pdf` (155 lecture slides) and `Developing-Questions-main.zip` (reference `README.md`)

> The question paper is original. The reference README was used only for the academic requirements, assessment structure and topic selection. Every question and every marking point below is traceable to the lecture slides (Deliverable 7).

---

## Contents

| Part | Content |
|---|---|
| **A** | [Analysis of the source files](#part-a--analysis-of-the-source-files) |
| **B** | [Course Outcomes and assessment blueprint](#part-b--course-outcomes-and-assessment-blueprint) |
| **D1** | [Question Paper](#deliverable-1--question-paper) |
| **D2** | [Course Outcome Mapping Table](#deliverable-2--course-outcome-mapping-table) |
| **D3** | [Bloom's Taxonomy Marks Distribution](#deliverable-3--blooms-taxonomy-marks-distribution) |
| **D4** | [Topic-wise Marks Distribution](#deliverable-4--topic-wise-marks-distribution) |
| **D5** | [Suggested Time Allocation](#deliverable-5--suggested-time-allocation) |
| **D6** | [Answer Hints and Marking Scheme](#deliverable-6--answer-hints-and-marking-scheme) |
| **D7** | [Source-to-Question Traceability Table](#deliverable-7--source-to-question-traceability-table) |
| **D8** | [Academic Quality Assurance Report](#deliverable-8--academic-quality-assurance-report) |

---

# Part A — Analysis of the Source Files

## A1. The lecture PDF (`SoftEng-Design.pdf`)

155 slides (PowerPoint export, 720 × 540 pt, with a readable text layer). Slide 1 credits Pfleeger, Sommerville, SWEBOK v3, R.C. Martin, the GoF book and Fowler's *Patterns of Enterprise Application Architecture*.

### A1.1 Slide map and scope

| Slides | Section | Status for this paper |
|:---:|---|---|
| 1 | Title slide | — |
| 2–14 | Design fundamentals | **Main body** |
| 15–29 | Design quality and CK metrics | **Main body** |
| 30–39 | Software architecture and architectural styles | **Main body** |
| 40–80 | GoF design patterns | **Main body** |
| 81–108 | Enterprise Application Architecture (EAA) patterns | **Main body** |
| 109–146 | "More topics on Software Design" (LCOM3, RFC, DIT, Factory Method, Prototype, Singleton, Decorator, Observer) | Additional material — **excluded** |
| 147–155 | User interface design | Separate section — **excluded** |

### A1.2 Content inventory of the main body

**Design fundamentals (slides 2–14)**
- Design is a problem-solving process whose input is the requirements (slide 4).
- Architectural design (high-level) describes how software is organised into components; detailed design describes the desired behaviour of those components (slide 6).
- The outcome is a set of models and artifacts recording the major decisions and their rationale, which supports long-term maintainability (slide 8).
- **Modularity and decomposition:** large software is divided into smaller named components with well-defined interfaces describing their interactions; different functionalities and responsibilities go into different components (slide 10).
- **Coupling:** a measure of the interdependence among components (slide 12). **Cohesion:** a measure of the strength of association of the elements within a component (slide 13). A good split has low coupling and high cohesion.
- **Abstraction:** a view of an object focusing on the information relevant to a particular purpose and ignoring the rest. **Encapsulation and information hiding:** grouping and packaging the internal details of an abstraction and making them inaccessible to external entities (slide 14).

**Design quality and CK metrics (slides 15–29)**

| Metric | Definition on the slides | Slides |
|---|---|:---:|
| CBO | CBO(A) = number of classes used by A (inheritance typically not counted). Example: CBO(Controller) = 2 | 17, 19 |
| LCOM | Q = pairs of methods that use common attributes; P = pairs that do not. LCOM = \|P\| − \|Q\| if \|P\| > \|Q\|, otherwise 0. Example: Q = 3, P = 0 ⇒ LCOM = 0 | 20–22 |
| LCOM2 | LCOM2 = 1 − Σ(mᵃⁱ) / (m × a), with m = number of methods, a = number of attributes, mᵃⁱ = number of methods that use attribute aᵢ (maximum of mᵃⁱ is m). Smaller is better. Example: m = 3, a = 4, Σ = 10 ⇒ LCOM2 = 1 − 10/12 = 1/6 ≈ 0.166 | 23–26 |
| WMC | WMC(A) = Σ Cᵢ over the N methods; Cᵢ is the complexity of method i, measured by lines of code or McCabe (number of conditions + 1). Example: McCabe WMC(Controller) = 10 | 27–29 |

**Architectural styles (slides 30–39)**
- Definition of software architecture: the set of structures needed to reason about the system — elements, relations among them, and properties of both (slide 32).
- Layered: components organised in layers; each layer depends only on the next layer (slide 35).
- Event-based: event producers and consumers, event distribution, consumers register for and consume events (slide 36).
- MVC: model = information about the domain; view = display of the model in the UI; controller = takes user input, manipulates the model, causes the view to update; the UI is the view plus the controller (slide 37).
- Blackboard/repository: **diagram only, no explanatory text** (slide 38).
- Pipes and filters: shown through the UNIX pipeline `ls -l | grep "Aug" | sort +4n | more` (slide 39).

**GoF design patterns (slides 40–80)**
- Pattern idea (Alexander, slide 41); GoF definition (slide 43); classification into Creational, Structural and Behavioral (slide 44). Adapter, Composite and Facade are Structural.
- Slides 45–46 cover Parameterized Factory (a variation of Factory Method). Strategy (47–51), Template Method (52–56) and Command (76–80) are the other patterns in this range.

| Pattern | Intent | Participants | Benefits | Liabilities | Slides |
|---|---|---|---|---|:---:|
| **Composite** | Compose objects into part–whole hierarchies; clients treat individual objects and compositions uniformly | Component (Graphic), Primitive/leaf (Rectangle, Line, Text), Composite (Picture), Client | Simple clients; new component kinds are easy to add | Can make the design too general | 64–69 |
| **Adapter** | Convert one interface into another that clients expect so incompatible classes can work together | Target (Shape), Client (DrawingEditor), Adaptee (TextView), Adapter (TextShape); object and class forms | Adaptees can be used without changing existing code | More classes and a level of indirection increase complexity | 58–62 |
| **Facade** | Unified, higher-level interface to a set of subsystem interfaces | Facade (Compiler), subsystem classes (Scanner, Parser, ProgramNode …) | Shields clients from subsystem components; does not prevent direct use of subsystem classes | Can become a God (complex) class | 71–75 |

**Enterprise Application Architecture (slides 81–108)**
- Domain Model (84–85); Service Layer (86); ORM (88); Data Mapper, also called Repository or DAO (89–90); Identity Field (91); Foreign Key Mapping (92–95); Association Table Mapping (96).
- Inheritance mapping: Single Table (97–98), Class Table (99–100), Concrete Table (101–102), each with advantages and disadvantages.
- Presentation patterns: MVC (104), Page Controller (105), Front Controller (106), Template View (107), Transform View (108).



# Part B — Course Outcomes and Assessment Blueprint

## B1. Course Outcomes

> These are **proposed** outcomes derived from the supplied materials. They are not officially verified university outcomes.

| CO | Course Outcome | Bloom's levels used |
|:---:|---|:---:|
| CO1 | Explain fundamental software design concepts, including modularity, coupling and cohesion. | C1, C2 |
| CO2 | Explain software design quality assessment using object-oriented design metrics. | C1, C2 |
| CO3 | Describe different software architectural styles and their characteristics. | C1, C2 |
| CO4 | Explain GoF design patterns, particularly Composite, Adapter and Facade. | C1, C2 |
| CO5 | Describe enterprise application architecture patterns and database mapping techniques. | C1, C2 |

## B2. Paper blueprint

| Question | Type | Topic | CO | Bloom | Marks |
|:---:|---|---|:---:|:---:|:---:|
| Q1 | Short answer (6 items) | All five topics | CO1–CO5 | C1 | 10 |
| Q2 | Conceptual explanation | Design Fundamentals | CO1 | C2 | 3 |
| Q3 | Conceptual explanation | Design Quality Metrics | CO2 | C2 | 4 |
| Q4 | Comparison + explanation | Architectural Styles | CO3 | C2 | 4 |
| Q5 | Pattern explanation (intent, participants, benefit, liability) | GoF — Composite | CO4 | C2 | 5 |
| Q6 | Comparison | GoF — Adapter vs Facade | CO4 | C2 | 6 |
| Q7 | Conceptual explanation | EAA — Domain Model, ORM, Data Mapper | CO5 | C2 | 4 |
| Q8 | Comparison | EAA — Inheritance mapping | CO5 | C2 | 4 |
| | | | | **Total** | **40** |

---

# Deliverable 1 — Question Paper

&nbsp;

| | |
|---|---|
| **Institution / Department** | ______________________________ |
| **Examination** | ______________________________ |
| **Course Title** | Software Engineering |
| **Course Code** | ______________ |
| **Topic** | Software Design |
| **Programme Level** | Bachelor (BNQF Level 6) |
| **Time** | 1 Hour |
| **Full Marks** | 40 |

**Instructions to candidates**

1. Answer **ALL** questions.
2. Marks for each question or part are shown in the right-hand column.
3. Answer in your own words and use the terminology of the lecture.

---

### Question 1 — Short Questions  `[10 marks]`

| No. | Question | CO | Bloom | Marks |
|:---:|---|:---:|:---:|---:|
| (a) | Define *abstraction* and *information hiding* (encapsulation). | CO1 | C1 | 2 |
| (b) | State what the CBO metric counts for a class, and state how the WMC of a class is calculated. | CO2 | C1 | 2 |
| (c) | Identify the architectural style demonstrated by the UNIX command line `ls -l \| grep "Aug" \| sort +4n \| more`. | CO3 | C1 | 1 |
| (d) | Name the three categories into which the GoF design patterns are classified, and state the category to which the Adapter, Composite and Facade patterns belong. | CO4 | C1 | 2 |
| (e) | State the intent of the Strategy pattern. | CO4 | C1 | 1 |
| (f) | State the purpose of the Identity Field pattern and what it stores in an object. | CO5 | C1 | 2 |

---

### Question 2  `[3 marks]`  — CO1, C2

Large software systems are divided into modules.

| No. | Question | Marks |
|:---:|---|---:|
| (a) | Explain what is meant by *modularity* and *decomposition*. | 1 |
| (b) | Describe how *coupling* and *cohesion* are used to judge whether a decomposition is a good one. | 2 |

---

### Question 3  `[4 marks]`  — CO2, C2

| No. | Question | Marks |
|:---:|---|---:|
| (a) | Explain how the LCOM metric of a class is determined from the sets P and Q of method pairs. | 2 |
| (b) | Explain the LCOM2 formula, identifying every symbol in it, and explain what the values 0 and 1 indicate about the cohesion of a class. | 2 |

---

### Question 4  `[4 marks]`  — CO3, C2

| No. | Question | Marks |
|:---:|---|---:|
| (a) | Compare the *Layered* and the *Event-Based* architectural styles in terms of how their components are organised and how they interact. | 2 |
| (b) | Explain the roles of the model, the view and the controller in the *Model–View–Controller (MVC)* style. | 2 |

---

### Question 5  `[5 marks]`  — CO4, C2

The lecture illustrates the **Composite** pattern with a graphics application in which `Graphic`, `Rectangle`, `Line`, `Text` and `Picture` objects must be handled uniformly.

| No. | Question | Marks |
|:---:|---|---:|
| (a) | Explain the intent of the Composite pattern. | 1 |
| (b) | Describe the roles of its four participants (Component, Primitive, Composite and Client), using `Graphic`, `Rectangle` and `Picture` as examples. | 2 |
| (c) | Explain one benefit and one liability of using the Composite pattern. | 2 |

---

### Question 6  `[6 marks]`  — CO4, C2

Compare the **Adapter** pattern with the **Facade** pattern.

| No. | Question | Marks |
|:---:|---|---:|
| (a) | Compare the intent of the two patterns. | 2 |
| (b) | Compare the participants of the two patterns and the role each participant plays. | 2 |
| (c) | Explain one benefit of the Adapter pattern and one liability of the Facade pattern. | 2 |

---

### Question 7  `[4 marks]`  — CO5, C2

| No. | Question | Marks |
|:---:|---|---:|
| (a) | Explain the Domain Model pattern and the kind of application for which it is suitable. | 2 |
| (b) | Explain the key idea of Object-Relational Mapping (ORM) and describe the responsibility of the Data Mapper pattern. | 2 |

---

### Question 8  `[4 marks]`  — CO5, C2

An inheritance hierarchy of domain classes has to be stored in a relational database.

| No. | Question | Marks |
|:---:|---|---:|
| (a) | Explain how *Single Table Inheritance* and *Class Table Inheritance* each represent the hierarchy in the database. | 2 |
| (b) | Compare the two patterns with respect to (i) retrieving an object and (ii) the effect of moving fields up or down the hierarchy. | 2 |

&nbsp;

<p align="center"><b>— End of Question Paper —</b></p>

---

# Deliverable 2 — Course Outcome Mapping Table

| Question | CO1 | CO2 | CO3 | CO4 | CO5 | Marks | Bloom |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| 1(a) | ✔ | | | | | 2 | C1 |
| 1(b) | | ✔ | | | | 2 | C1 |
| 1(c) | | | ✔ | | | 1 | C1 |
| 1(d) | | | | ✔ | | 2 | C1 |
| 1(e) | | | | ✔ | | 1 | C1 |
| 1(f) | | | | | ✔ | 2 | C1 |
| 2(a) | ✔ | | | | | 1 | C2 |
| 2(b) | ✔ | | | | | 2 | C2 |
| 3(a) | | ✔ | | | | 2 | C2 |
| 3(b) | | ✔ | | | | 2 | C2 |
| 4(a) | | | ✔ | | | 2 | C2 |
| 4(b) | | | ✔ | | | 2 | C2 |
| 5(a) | | | | ✔ | | 1 | C2 |
| 5(b) | | | | ✔ | | 2 | C2 |
| 5(c) | | | | ✔ | | 2 | C2 |
| 6(a) | | | | ✔ | | 2 | C2 |
| 6(b) | | | | ✔ | | 2 | C2 |
| 6(c) | | | | ✔ | | 2 | C2 |
| 7(a) | | | | | ✔ | 2 | C2 |
| 7(b) | | | | | ✔ | 2 | C2 |
| 8(a) | | | | | ✔ | 2 | C2 |
| 8(b) | | | | | ✔ | 2 | C2 |
| **Total marks per CO** | **5** | **6** | **5** | **14** | **10** | **40** | |

**CO-wise breakdown**

| CO | Contributing parts | Marks | Target | Reconciled |
|:---:|---|:---:|:---:|:---:|
| CO1 | 1(a) 2 + 2(a) 1 + 2(b) 2 | 5 | 5 | ✔ |
| CO2 | 1(b) 2 + 3(a) 2 + 3(b) 2 | 6 | 6 | ✔ |
| CO3 | 1(c) 1 + 4(a) 2 + 4(b) 2 | 5 | 5 | ✔ |
| CO4 | 1(d) 2 + 1(e) 1 + 5 (1+2+2) + 6 (2+2+2) | 14 | 14 | ✔ |
| CO5 | 1(f) 2 + 7(a) 2 + 7(b) 2 + 8(a) 2 + 8(b) 2 | 10 | 10 | ✔ |
| **Total** | | **40** | **40** | ✔ |

---

# Deliverable 3 — Bloom's Taxonomy Marks Distribution

| Level | Questions | Marks | Percentage | Target |
|---|---|:---:|:---:|:---:|
| C1 — Knowledge | Q1(a)–(f) | 10 | 25% | 10 / 25% ✔ |
| C2 — Understanding | Q2–Q8 | 30 | 75% | 30 / 75% ✔ |
| **Total** | | **40** | **100%** | |

**Action verbs used**

| Level | Verbs in this paper |
|---|---|
| C1 | Define, State, Identify, Name |
| C2 | Explain, Describe, Compare |

No question requires application, analysis, evaluation or creation (C3 or above). No part asks for a calculation.

---

# Deliverable 4 — Topic-wise Marks Distribution

| Topic | Slides | Questions | Required | Actual | Reconciled |
|---|:---:|---|:---:|:---:|:---:|
| GoF Design Patterns | 40–80 | 1(d) 2, 1(e) 1, Q5 5, Q6 6 | 14 | 14 | ✔ |
| Enterprise Application Architecture | 81–108 | 1(f) 2, Q7 4, Q8 4 | 10 | 10 | ✔ |
| Design Quality Metrics | 15–29 | 1(b) 2, Q3 4 | 6 | 6 | ✔ |
| Design Fundamentals | 1–14 | 1(a) 2, Q2 3 | 5 | 5 | ✔ |
| Architectural Styles | 30–39 | 1(c) 1, Q4 4 | 5 | 5 | ✔ |
| **Total** | | | **40** | **40** | ✔ |

Topic and CO allocations coincide, because each topic maps to exactly one CO (Fundamentals → CO1, Metrics → CO2, Styles → CO3, GoF → CO4, EAA → CO5).

---

# Deliverable 5 — Suggested Time Allocation

| Question | Marks | Time (min) |
|:---:|:---:|:---:|
| Q1 | 10 | 8 |
| Q2 | 3 | 4 |
| Q3 | 4 | 6 |
| Q4 | 4 | 6 |
| Q5 | 5 | 8 |
| Q6 | 6 | 10 |
| Q7 | 4 | 6 |
| Q8 | 4 | 7 |
| Reading and revision | — | 5 |
| **Total** | **40** | **60** |

---

# Deliverable 6 — Answer Hints and Marking Scheme

*For examiners only.* Slide numbers refer to `SoftEng-Design.pdf`. Accept answers that are correct and equivalent in meaning, even if worded differently from the slides.

## Question 1 — Short Questions (10 marks, C1)

**1(a) — 2 marks (CO1) — slide 14**

| Marks | Expected content |
|:---:|---|
| 1 | **Abstraction:** a view of an object that focuses on the information relevant to a particular purpose and ignores the remainder. |
| 1 | **Information hiding / encapsulation:** grouping and packaging the internal details of an abstraction and making those details inaccessible to external entities. |

**1(b) — 2 marks (CO2) — slides 17, 27**

| Marks | Expected content |
|:---:|---|
| 1 | **CBO(A)** = the number of classes used by class A. Inheritance is typically not counted. |
| 1 | **WMC(A)** = Σ Cᵢ, the sum of the complexities of the class's N methods (Cᵢ = complexity of method i). Naming LOC or McCabe (conditions + 1) as ways to measure Cᵢ is acceptable but not required. |

**1(c) — 1 mark (CO3) — slide 39**

| Marks | Expected content |
|:---:|---|
| 1 | **Pipes and filters.** |

**1(d) — 2 marks (CO4) — slide 44**

| Marks | Expected content |
|:---:|---|
| 1 | Creational, Structural, Behavioral (all three required). |
| 1 | Adapter, Composite and Facade are **Structural** patterns. |

**1(e) — 1 mark (CO4) — slide 48**

| Marks | Expected content |
|:---:|---|
| 1 | Define a family of algorithms, encapsulate each one and make them interchangeable; the algorithm varies independently from the clients that use it. (Award the mark for the first clause stated correctly.) |

**1(f) — 2 marks (CO5) — slide 91**

| Marks | Expected content |
|:---:|---|
| 1 | **Purpose:** to maintain identity between an in-memory object and a database table row (so that data can be tied back to the database when written). |
| 1 | **Stores:** the database ID, i.e. the primary key of the relational table, in a field of the object. |

## Question 2 — Modularity, coupling and cohesion (3 marks, C2, CO1)

**2(a) — 1 mark — slide 10**

| Marks | Expected content |
|:---:|---|
| 1 | Decomposing and modularizing = dividing large software into a number of smaller **named components** with **well-defined interfaces** that describe component interactions; usually different functionalities and responsibilities are placed in different components. (Both the smaller-components idea and the interfaces/responsibilities idea are needed.) |

**2(b) — 2 marks — slides 11–13**

| Marks | Expected content |
|:---:|---|
| 1 | **Coupling** is a measure of the interdependence among components; a good split has **low** coupling (components are not heavily dependent on one another). |
| 1 | **Cohesion** is a measure of the strength of association of the elements within a component; a good split has **high** cohesion (each component's elements belong together). |

## Question 3 — LCOM and LCOM2 (4 marks, C2, CO2)

**3(a) — 2 marks — slides 20–22**

| Marks | Expected content |
|:---:|---|
| 1 | **Q** = the set of pairs of class methods that use common attributes; **P** = the set of pairs of class methods that do not use common attributes. |
| 1 | **LCOM = \|P\| − \|Q\|** if \|P\| > \|Q\|; **LCOM = 0** if \|P\| ≤ \|Q\|. |

*Examiner note:* slide 22 illustrates the Rectangle class with Q = 3, P = 0, so LCOM = 0. No calculation is asked in this paper.

**3(b) — 2 marks — slides 23, 26**

| Marks | Expected content |
|:---:|---|
| 1 | **LCOM2 = 1 − Σ(mᵃⁱ) / (m × a)**, where **m** = number of methods in the class, **a** = number of attributes, **mᵃⁱ** = number of methods that use attribute aᵢ (i = 1, …, a); the maximum value of mᵃⁱ is m. (Formula and a correct explanation of all three symbols are needed.) |
| 1 | **Interpretation:** the smaller the value, the better (higher cohesion). **0** — every method uses every attribute (Σ mᵃⁱ = m × a). **1** — no method uses any attribute (Σ mᵃⁱ = 0), i.e. the lowest cohesion. |

*Examiner notes:* (1) Slide 23 poses "LCOM2 = 1 ?" and "LCOM2 = 0 ?" as open questions; the interpretation above follows directly from the formula, so accept answers that justify the values from the formula. (2) Worked example on slide 26 (for reference only): m = 3, a = 4, Σ = 2 + 2 + 3 + 3 = 10, LCOM2 = 1 − 10/12 = 1/6 ≈ 0.166.

## Question 4 — Architectural styles (4 marks, C2, CO3)

**4(a) — 2 marks — slides 35, 36**

| Marks | Expected content |
|:---:|---|
| 1 | **Layered:** components are organised in layers, and each layer depends only on the next layer. |
| 1 | **Event-based:** components are event producers and consumers; consumers register for events, events are distributed, and consumers consume the events they registered for. |

*Examiner note:* the comparison is satisfied when the organisation and interaction of both styles are stated correctly (layers with next-layer dependency versus producers/consumers linked through event distribution).

**4(b) — 2 marks — slides 37, 104**

| Marks | Expected content |
|:---:|---|
| 1 | **Model** represents information about the domain; **View** represents the display of the model in the UI. |
| 1 | **Controller** takes user input, manipulates the model and causes the view to update appropriately. (Noting that the UI is the combination of view and controller is a valid supporting point.) |

## Question 5 — Composite pattern (5 marks, C2, CO4)

**5(a) — 1 mark — slide 64**

| Marks | Expected content |
|:---:|---|
| 1 | Compose objects into structures that represent **part–whole hierarchies**; Composite lets clients treat individual objects and compositions of objects **uniformly**. |

**5(b) — 2 marks — slide 68**

| Marks | Expected content |
|:---:|---|
| 1 | **Component (Graphic):** declares the interface for objects in the composition and implements default behaviour common to all classes. **Primitive (Rectangle, Line, Text):** leaf objects of the composition. |
| 1 | **Composite (Picture):** defines behaviour for components that have children. **Client:** manipulates objects in the composition through the Component interface. |

**5(c) — 2 marks — slide 69**

| Marks | Expected content |
|:---:|---|
| 1 | **Benefit (any one, with explanation):** makes clients simple because they treat composite structures and individual objects uniformly; **or** makes it easier to add new kinds of components, since new Composite or Leaf subclasses work automatically with existing structures and client code. |
| 1 | **Liability:** can make the design too general — the ease of adding components makes it harder to restrict the components of a composite. |

## Question 6 — Adapter vs Facade (6 marks, C2, CO4)

**6(a) — 2 marks — slides 58, 71**

| Marks | Expected content |
|:---:|---|
| 1 | **Adapter:** converts the interface of a class into another interface that clients expect; lets classes work together that could not otherwise because of incompatible interfaces. |
| 1 | **Facade:** provides a unified interface to a set of interfaces in a subsystem; defines a higher-level interface that makes the subsystem easier to use. |

**6(b) — 2 marks — slides 60, 74**

| Marks | Expected content |
|:---:|---|
| 1 | **Adapter participants:** Target (domain-specific interface used by the Client), Client (collaborates with objects conforming to Target), Adaptee (existing interface that needs adapting), Adapter (adapts the Adaptee's interface to the Target interface). Lecture example: Shape, DrawingEditor, TextView, TextShape. Award the mark for at least three roles described correctly. |
| 1 | **Facade participants:** the Facade knows which subsystem classes are responsible for a request and delegates client requests to them; the subsystem classes implement the functionality, handle work assigned by the Facade, and have no knowledge of the Facade (no references to it). Lecture example: Compiler with Scanner, Parser, ProgramNode. Both participants are needed. |

**6(c) — 2 marks — slides 62, 75**

| Marks | Expected content |
|:---:|---|
| 1 | **Adapter benefit:** adaptees can be added and used without changes to existing code. |
| 1 | **Facade liability:** the Facade can become a God (overly complex) class. |

## Question 7 — Domain Model, ORM and Data Mapper (4 marks, C2, CO5)

**7(a) — 2 marks — slides 84, 85**

| Marks | Expected content |
|:---:|---|
| 1 | The **Domain Model** is an object model of the domain that incorporates both behaviour and data (a different object per table row/tuple). |
| 1 | **Suitable for** real-world applications with complex business logic: rules and logic describing many cases are handled by a web of interconnected objects, each representing a meaningful concept. |

**7(b) — 2 marks — slides 88, 89, 90**

| Marks | Expected content |
|:---:|---|
| 1 | **ORM** = mapping objects to database relations and vice versa. Key idea: one database table in the data layer per class of objects in the domain layer, and each object is stored as a table row. |
| 1 | **Data Mapper** (also known as Repository or DAO): a layer of mappers that moves/transfers data between objects and the database while keeping them independent of each other (and of the mapper); the in-memory objects need not even know that a database is present. |

## Question 8 — Inheritance mapping (4 marks, C2, CO5)

**8(a) — 2 marks — slides 97, 99**

| Marks | Expected content |
|:---:|---|
| 1 | **Single Table Inheritance:** the whole hierarchy is stored in one table that has columns for all the fields of the various classes. |
| 1 | **Class Table Inheritance:** one table for each class in the hierarchy, with the tables linked by foreign keys. |

**8(b) — 2 marks — slides 98, 100**

| Marks | Expected content |
|:---:|---|
| 1 | **(i) Retrieving an object:** Single Table — only one table, no joins needed. Class Table — several tables must be touched to load an object, requiring a join or multiple queries and sewing together in memory. |
| 1 | **(ii) Moving fields up or down the hierarchy:** Single Table — the database does not change. Class Table — such refactoring causes changes to the database. |

*Both patterns must be addressed for each criterion to earn its mark.*

## Mark summary check

| Question | Parts | Total |
|:---:|---|:---:|
| Q1 | 2 + 2 + 1 + 2 + 1 + 2 | 10 |
| Q2 | 1 + 2 | 3 |
| Q3 | 2 + 2 | 4 |
| Q4 | 2 + 2 | 4 |
| Q5 | 1 + 2 + 2 | 5 |
| Q6 | 2 + 2 + 2 | 6 |
| Q7 | 2 + 2 | 4 |
| Q8 | 2 + 2 | 4 |
| **Total** | | **40** |

---

# Deliverable 7 — Source-to-Question Traceability Table

| Question | Topic | Supporting slides | Slide content used |
|:---:|---|:---:|---|
| 1(a) | Design Fundamentals | 14 | Definitions of abstraction, encapsulation and information hiding |
| 1(b) | Design Quality Metrics | 17, 27 | CBO definition; WMC definition |
| 1(c) | Architectural Styles | 39 | UNIX pipeline labelled "Pipes and filters" |
| 1(d) | GoF Design Patterns | 44 | Classification table (Creational / Structural / Behavioral) |
| 1(e) | GoF Design Patterns | 48 | Strategy intent |
| 1(f) | EAA | 91 | Identity Field definition and intent |
| 2(a) | Design Fundamentals | 10 | Modularity and decomposition |
| 2(b) | Design Fundamentals | 11–13 | Low coupling; high cohesion; definitions |
| 3(a) | Design Quality Metrics | 20–22 | LCOM with sets P and Q; Rectangle example |
| 3(b) | Design Quality Metrics | 23–26 | LCOM2 formula, symbols, "smaller the better"; worked example |
| 4(a) | Architectural Styles | 35, 36 | Layered; event-based |
| 4(b) | Architectural Styles | 37, 104 | MVC roles |
| 5(a) | GoF — Composite | 64 | Intent |
| 5(b) | GoF — Composite | 68 (65–67 motivation) | Participants: Component, Primitive, Composite, Client |
| 5(c) | GoF — Composite | 69 | Benefits and liability |
| 6(a) | GoF — Adapter, Facade | 58, 71 | Intents |
| 6(b) | GoF — Adapter, Facade | 60, 61, 74 | Adapter and Facade participants |
| 6(c) | GoF — Adapter, Facade | 62, 75 | Adapter benefit; Facade liability |
| 7(a) | EAA | 84, 85 | Domain Model |
| 7(b) | EAA | 88, 89, 90 | ORM key idea; Data Mapper |
| 8(a) | EAA | 97, 99 | Single Table and Class Table definitions |
| 8(b) | EAA | 98, 100 | Advantages and disadvantages of both patterns |

All cited slides lie within slides 1–108. No question draws on slides 109–155.

---

# Deliverable 8 — Academic Quality Assurance Report

## 8.1 Verification of the eleven required checks

| # | Check | Result | Evidence |
|:---:|---|:---:|---|
| 1 | Total marks = 40 | ✔ | Q1 10 + Q2 3 + Q3 4 + Q4 4 + Q5 5 + Q6 6 + Q7 4 + Q8 4 = 40 |
| 2 | Examination time = 60 minutes | ✔ | Deliverable 5: 55 minutes of answering + 5 minutes of revision |
| 3 | C1 = 10 and C2 = 30 | ✔ | C1: Q1 only (10). C2: 3 + 4 + 4 + 5 + 6 + 4 + 4 = 30 |
| 4 | All five COs covered | ✔ | CO1–CO5 each appear in Q1 and in at least one C2 question |
| 5 | CO marks reconcile to topic distribution | ✔ | CO1 5 = Fundamentals 5; CO2 6 = Metrics 6; CO3 5 = Styles 5; CO4 14 = GoF 14; CO5 10 = EAA 10 |
| 6 | Every question has a valid Bloom's level | ✔ | All parts tagged C1 or C2 with matching verbs |
| 7 | Every answer hint corresponds to an actual question | ✔ | Deliverable 6 covers 1(a)–(f), 2(a)–(b), 3(a)–(b), 4(a)–(b), 5(a)–(c), 6(a)–(c), 7(a)–(b), 8(a)–(b) — 22 parts, no extras |
| 8 | Formulas match the slides | ✔ | LCOM, LCOM2, WMC (McCabe) and CBO re-checked against slides 17, 20, 23, 26, 27, 29. Example arithmetic re-verified: LCOM2 = 1 − 10/12 = 1/6; McCabe WMC of Controller = 1 + 1 + 1 + 4 + 3 = 10 |
| 9 | Questions supported by the lecture PDF | ✔ | Deliverable 7 |
| 10 | No unnecessary duplication of the reference questions | ✔ | See 8.3 |
| 11 | No unsupported content or invented slide references | ✔ | All slide numbers were read from the PDF text; see 8.4 for the one interpretive point |

## 8.2 Coverage of the required important topics

| Topic | Assessed in | Note |
|---|---|---|
| Modularity, decomposition | Q2(a) | |
| Low coupling, high cohesion | Q2(b) | |
| Abstraction, encapsulation, information hiding | Q1(a) | |
| CBO | Q1(b) | |
| LCOM | Q3(a) | |
| LCOM2 | Q3(b) | |
| WMC | Q1(b) | |
| Layered, Event-based | Q4(a) | |
| MVC | Q4(b) | |
| Pipes and Filters | Q1(c) | |
| Blackboard/Repository | — | Not assessed; see 8.4 |
| Composite (intent, participants, benefit, liability) | Q5 | |
| Adapter (intent, participants, benefit) | Q6 | |
| Facade (intent, participants, liability) | Q6 | |
| Domain Model | Q7(a) | |
| ORM, Data Mapper | Q7(b) | |
| Single Table and Class Table Inheritance | Q8 | |
| Other mapping concepts | Q1(f) Identity Field | Foreign Key Mapping, Association Table Mapping and Concrete Table Inheritance not assessed (mark budget) |

## 8.3 Originality against the reference paper

The scope, mark weights and priority topics are fixed by the brief, so some topic overlap is unavoidable. The questions themselves were redesigned.

| Area | Reference paper | This paper |
|---|---|---|
| Short questions | Cohesion, CBO, list four styles, Facade intent, ORM | Abstraction and information hiding; CBO and WMC; identify pipes and filters from a command; GoF categories; Strategy intent; Identity Field |
| Fundamentals | Coupling vs cohesion | Modularity and decomposition, then how coupling and cohesion judge a split |
| Metrics | CBO, WMC and LCOM2 together | LCOM from sets P and Q, then LCOM2 formula with symbols and the meaning of 0 and 1 |
| Styles | MVC only | Layered vs Event-based comparison, plus MVC |
| GoF | Composite 7 marks and Adapter 5 marks as separate recall questions | Composite 5 marks (intent, participants, benefit, liability); Adapter vs Facade as a 6-mark comparison |
| EAA | Data Mapper with Domain Model; STI and CTI with one advantage each | Domain Model; ORM with Data Mapper; STI vs CTI compared on two stated criteria |

## 8.4 Assumptions and limitations

1. **Course Outcomes are proposed, not official.** They follow the wording in the brief and have not been verified against any university document.
2. **Header fields are blank.** Institution, examination name and course code were not provided and were not invented.
3. **Verification used the PDF text layer.** UML figures and diagrams were not used as a basis for any mark. Where a slide's text is only a title or diagram label, no question asks for detail beyond that label.
4. **Blackboard/Repository (slide 38) is not assessed.** The slide contains only a heading and a diagram, with no explanatory text, so a fair question could not be set from the slide text.
5. **Slide 23 leaves two questions open** ("LCOM2 = 1 ?", "LCOM2 = 0 ?"). The answers in Q3(b) are derived directly from the slide's own formula, and the marking guide says so.
6. **Q4(a) comparison** rests on the short descriptions on slides 35 and 36. The marking scheme therefore rewards correct statements about each style's organisation and interaction, not additional detail from outside the slides.
7. **Strategy (slide 48) is used once, as a 1-mark C1 item.** Slides 40–80 form the GoF scope in the brief, so Strategy is in scope; Template Method and Command are not assessed. The three priority patterns carry the other 13 GoF marks.
8. **Parameterized Factory (slides 45–46)** lies inside the GoF range but is not a pattern the brief prioritises and is not assessed.
9. **Not assessed within the main body** (mark budget, not exclusion): Service Layer, Foreign Key Mapping, Association Table Mapping, Concrete Table Inheritance, Page Controller, Front Controller, Template View and Transform View.
10. **Excluded as instructed:** slides 109–146 (additional material) and slides 147–155 (UI design). No question draws on them.
11. **Mark splits** were set by expected answer depth and use whole marks only; no half marks appear in the scheme.
12. **Bloom's tagging** is by the verb and the expected depth of answer. Q6 and Q8(b) are comparisons, which sit at C2 because the criteria are stated in the question and no judgement beyond the slides is needed.

## 8.5 Inconsistencies found and corrected during preparation

- An early draft of Q1(e) asked for the intent of Facade, which repeated Q6(a). It was replaced with the Strategy-intent item.
- The first mark split for Q6(c) asked for a benefit and a liability of the same pattern, which left Adapter's benefit unassessed. It was changed to one benefit of Adapter and one liability of Facade.
- Q7(b) originally asked how the Data Mapper "supports" ORM. The slides do not state that relationship, so it was reworded to ask for the Data Mapper's responsibility.

**Conclusion:** after these corrections, no remaining inconsistency was found among the question paper, the mapping tables, the marking guide and the traceability table.
