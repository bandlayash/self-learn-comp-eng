# Self-Taught Computer Engineering Degree — Free Course Plan

> A self-study computer-engineering curriculum assembled entirely from free, link-verified online course material.
> The curation lens is the **hardware** side of CE, aimed at **GPU Performance Engineering** as an end goal.
>
> Compiled 2026-06-03 · links re-verified 2026-07-29. Every link was fetched and checked for existence + legality.
> Status flags: ✅ excellent free coverage · ⚠️ a paid/gated/dead caveat to know.

---

## What this is

A sequenced reading/watching/problem-solving list that covers the hardware core of an undergraduate computer-engineering
degree using only material that is **free and legal to access** — university OpenCourseWare, open-access textbooks,
public lecture recordings, and self-checking projects.

It is not a degree, and there is no credential at the end. What it offers instead is a defensible ordering, an honest
account of where the free material is strong and where it falls apart, and — for the topics that matter most — links to
courses that publish **problem sets and exams with solutions**, so progress is actually measurable without an instructor.

Two things to know up front:

- **It has a point of view.** The material is weighted toward the topics that pay off in performance engineering:
  microarchitecture, memory systems, GPUs, and power/thermal behavior. Circuits and signals are deliberately treated as
  read-level background rather than design skills. See [Adapting this for other CE focuses](#adapting-this-for-other-ce-focuses)
  to re-weight it.
- **It assumes programming fluency.** Not a CS degree — but comfort writing and debugging real programs. Anyone starting
  from zero should do [CS50x](https://cs50.harvard.edu/x/) or [MIT 6.0001](https://ocw.mit.edu/courses/6-0001-introduction-to-computer-science-and-programming-in-python-fall-2016/)
  first, then come back.

---

## Computer engineering vs. computer science

The two degrees overlap heavily and then diverge at the hardware boundary. If the mental model is fuzzy, this is the
short version:

| | Computer Science | Computer Engineering |
|---|---|---|
| **Central question** | What can be computed, and at what cost? | How is a machine that computes actually built? |
| **Shared core** | programming · data structures · algorithms · discrete math · operating systems · intro architecture | |
| **Mostly CE-only** | — | circuits & electronics · signals/systems · digital logic design · VLSI & device physics · embedded/firmware · deep microarchitecture |
| **Mostly CS-only** | theory of computation · compilers · databases · AI/ML · programming languages · distributed systems | — |
| **Math emphasis** | discrete math, probability, logic | all of that **plus** calculus through ODEs, linear algebra, and E&M/thermal physics |
| **Typical output** | software that is correct and scalable | hardware, or software that is fast *because* it respects the hardware |

The practical difference: CS teaches the machine as an abstraction that mostly holds. CE teaches where the abstraction
leaks — cache hierarchies, memory bandwidth, clock domains, power budgets, heat — and how to reason about the leaks.

This plan covers the CE-only column and the math/physics that supports it. It does **not** re-teach the shared core.

---

## Who this is for

| Starting point | Where to start | What to expect |
|---|---|---|
| **CS degree or equivalent self-study** | Gap-check [Phase 0](#phase-0--prerequisites) in a week or two, then start at [Phase 1](#phase-1--math--physics-gaps) | The intended path. Phase 0 is already covered; the new material begins with ODEs and circuits. |
| **Self-taught programmer, no formal CS** | Work [Phase 0](#phase-0--prerequisites) as real courses, not a checklist | Adds roughly 3–6 months. Phase 0 links are full courses with labs and exams — they hold up as a first pass. |
| **EE or physics background** | Skim Phases 1–2, start in earnest at [Phase 3](#phase-3---the-core-perf-gap-fill-highest-roi) | Circuits, signals, and devices are likely already covered. The gap is architecture and memory systems. |
| **Working engineer wanting specific gaps** | Ignore the sequence; go straight to [The Critical Gaps](#-the-critical-gaps--what-no-ce-course-teaches-but-the-job-demands) | That section is standalone and the most immediately applicable. |

---

## How to use this

- **Time budget.** Phases 1–5 total roughly 38–58 weeks. At a sustainable 10–15 hours/week that is **9–14 months**;
  full-time it compresses to about 4–5. The phase estimates below assume the CS-background starting point.
- **Check the boxes.** Every item is a GitHub task-list checkbox. Fork the repo and tick them off as a progress log.
- **Do the problem sets.** The single biggest predictor of whether self-study works is doing graded work. Courses here
  were chosen partly for publishing **solutions** — prioritize those over lecture-only material.
- **Don't chase completeness.** Several phases say *skim* or *take only X*. That is deliberate. The goal is a working
  mental model of the hardware, not coverage of every topic a degree would examine.
- **Expect link rot.** University course sites rotate their URL each term (e.g. `cs61c.org/su26/`). If a term-stamped
  link 404s or hits a campus login, drop to the site root — it usually redirects to the current term. Broken links are
  worth an issue or a PR.

---

## The big picture

A CE degree differs from a CS degree mainly in: **circuits & electronics, signals/systems, digital design, deep computer
architecture, VLSI/devices, and embedded systems**.

**Key insight:** the canonical CE degree teaches what hardware *is* far better than how to *measure* it, or how a power
and thermal envelope constrains it. The three things most relevant to real performance work —
**profiling methodology, thermal RC modeling, DVFS/power budgeting** — aren't real courses anywhere, so they're broken out
in [The Critical Gaps](#-the-critical-gaps--what-no-ce-course-teaches-but-the-job-demands).

**Availability verdict:** ~90% of the needed material is free and legal. Recurring gaps: (1) the canonical paid textbooks
(Hennessy & Patterson, Patterson & Hennessy, Kirk & Hwu) have **no legal free PDF** — free substitutes cover them;
(2) hands-on FPGA labs and graded autograders are mostly gated.

---

## Recommended sequence

| Phase | Courses | Action |
|---|---|---|
| **0. Prerequisites (1–2 wk to verify)** | Low-level C/asm, Discrete math/algo/prob | **Verify fluency, don't re-take.** Without this background, work them as full courses instead. Re-sharpen *probability/stats* — it underpins benchmark noise. |
| **1. Math/physics gaps (4–8 wk)** | Eng. math (ODE/Laplace), Physics (E&M + thermal) | **Skim.** The load-bearing additions are ODEs/transforms (RC + thermal transients) and E&M/thermal. |
| **2. Hardware mental model (8–12 wk)** | Circuits, Digital logic, Arch gateway | Read-level circuits; digital logic plus a Nand2Tetris CPU build; caches/pipelining. |
| **3. ⭐ Core perf gap-fill (10–14 wk)** | **Advanced microarchitecture, Memory systems** | **Highest ROI.** Quantitative methodology and memory/bandwidth reasoning. |
| **4. 🎯 The bullseye (10–14 wk)** | **GPU/parallel arch + CUDA** | UIUC ECE408 / Stanford CS149 on real hardware with Nsight. |
| **5. Power & thermal depth (6–10 wk)** | Semiconductor devices, VLSI, Embedded | Take only power/thermal/leakage/V-f intuition plus the missing thermal/DVFS topics. |
| **6. As-needed** | Signals & systems | Conceptual pass only (clocks/PLLs/jitter). |

---

## Phase 0 — Prerequisites

*Assumed knowledge for anyone with a CS background — verify fluency and move on. Without that background, these are full
courses worth doing properly, and they are good ones.*

### Low-Level Programming: C, Assembly & the Machine Model
*Berkeley CS61C · CMU 15-213/CS:APP · UIUC ECE220*
- [ ] **Lectures (video):** [Berkeley CS61C](https://www.youtube.com/playlist?list=PLhMnuBfGeCDM8pXLpqib90mDFJI-e1lpk) · [CMU 15-213 (Bryant & O'Hallaron)](https://www.youtube.com/playlist?list=PL2dWYoM7ypKy8yuOV01RGMRDEaw5sNyyz)
- [ ] **Textbook (free substitute):** [CS61C course notes](https://notes.cs61c.org/) — the legal open stand-in for the ⚠️ paid CS:APP book
- [ ] **Labs:** [CS:APP self-study labs](https://csapp.cs.cmu.edu/3e/labs.html) (Data/Bomb/Attack/Malloc) · [Nand2Tetris](https://www.nand2tetris.org/) (self-checking)
- [ ] **Exams + solutions:** [CS61C exam archive 2015–2026](https://cs61c.org/su26/resources/exams/) ✅

### Discrete Math, Algorithms & Probability
*MIT 6.042J · Berkeley CS70 — probability is the part worth re-sharpening even with a CS degree*
- [ ] **Lectures + free textbook:** [MIT 6.042J](https://ocw.mit.edu/courses/6-042j-mathematics-for-computer-science-spring-2015/) + [full free PDF](https://ocw.mit.edu/courses/6-042j-mathematics-for-computer-science-spring-2015/mit6_042js15_textbook.pdf)
- [ ] **Probability practice:** [Berkeley CS70 notes + HW w/ solutions](https://www.eecs70.org/) · [UIUC ECE313 old exams w/ solutions](https://courses.grainger.illinois.edu/ece313/sp2025/old_exams.html)
- ⚠️ CLRS is paid; free algo video via [MIT 6.006](https://ocw.mit.edu/courses/6-006-introduction-to-algorithms-spring-2020/) + [Roughgarden](https://www.algorithmsilluminated.org/).

> **Coming from zero?** These two entries are the hardware-facing slice of a CS foundation, not the whole thing.
> For the full picture, [teachyourselfcs.com](https://teachyourselfcs.com/) and [OSSU](https://github.com/ossu/computer-science)
> are the two best free CS self-study guides, and they pair cleanly with this plan.

---

## Phase 1 — Math & physics gaps

### Engineering Math: Multivariable Calc, Linear Algebra & ODEs — *medium*
- [ ] **Lectures + psets + exams (all w/ solutions):** [MIT 18.06SC Linear Algebra (Strang)](https://ocw.mit.edu/courses/18-06sc-linear-algebra-fall-2011/) · [18.02SC Multivariable](https://ocw.mit.edu/courses/18-02sc-multivariable-calculus-fall-2010/) · [18.03SC Differential Equations](https://ocw.mit.edu/courses/18-03sc-differential-equations-fall-2011/) — **the load-bearing part is ODEs/Laplace** (RC + thermal transients)
- [ ] **Free textbooks:** [OpenStax Calculus Vol 3](https://openstax.org/details/books/calculus-volume-3) · [Lebl "Notes on Diffy Qs"](https://www.jirka.org/diffyqs/) · [Hefferon Linear Algebra](https://www.openintro.org/book/linalg/)
- [ ] **Intuition:** [3Blue1Brown — Essence of Linear Algebra](https://www.youtube.com/playlist?list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab)
- ⚠️ Strang's own textbook has no free legal copy — use the substitutes.

### Physics for Engineers: E&M, Thermal & Quantum — *medium (conceptual)*
- [ ] **Lectures (video):** [Walter Lewin MIT 8.02 E&M (36 lectures)](https://www.youtube.com/playlist?list=PLUdYlQf0_sSsfcNOPSNPQKHDhSjTJATPu) · [MIT 8.02 OCW 2019](https://ocw.mit.edu/courses/8-02-physics-ii-electricity-and-magnetism-spring-2019/)
- [ ] **Free textbooks:** [OpenStax University Physics Vol 2](https://openstax.org/details/books/university-physics-volume-2) (thermo + E&M) · [Vol 3](https://openstax.org/details/books/university-physics-volume-3) (quantum)
- [ ] **Psets + exams w/ solutions:** [MIT 8.02X assignments](https://ocw.mit.edu/courses/8-02x-physics-ii-electricity-magnetism-with-an-experimental-focus-spring-2005/pages/assignments/) + [quizzes w/ solutions](https://ocw.mit.edu/courses/8-02x-physics-ii-electricity-magnetism-with-an-experimental-focus-spring-2005/pages/exams/) · [MIT 8.044 Statistical Physics](https://ocw.mit.edu/courses/8-044-statistical-physics-i-spring-2013/)
- Skip the heavy quantum problem sets — conceptual pass only.

---

## Phase 2 — The hardware mental model

### Circuit Analysis & Modeling — *high* (read, don't design)
- [ ] **Lectures (video):** [MIT 6.002 Circuits & Electronics (Agarwal)](https://ocw.mit.edu/courses/6-002-circuits-and-electronics-spring-2007/video_galleries/video-lectures/)
- [ ] **Free textbook:** [Ulaby, Maharbiz & Furse "Circuit Analysis and Design"](https://cad3e.eecs.umich.edu/) (open-access; substitute for ⚠️ paid Agarwal & Lang)
- [ ] **Psets/exams WITH solutions:** [Berkeley EECS16B](https://eecs16b.org/) ← fills MIT 6.002's missing-solutions gap, and frames circuits in linear-algebra terms
- [ ] **On-ramp:** [Khan Academy Circuit Analysis](https://www.khanacademy.org/science/electrical-engineering/ee-circuit-analysis-topic)
- Why it matters: RC time constants and power delivery → supply-voltage droop and throttle behavior.

### Digital Logic Design — *high*
- [ ] **Lectures (best free set):** [Onur Mutlu DDCA (ETH)](https://www.youtube.com/playlist?list=PL5Q2soXY2Zi9Eo29LMgKVcaydS7V1zZW3) · [MIT 6.004](https://ocw.mit.edu/courses/6-004-computation-structures-spring-2017/) + open notes [computationstructures.org](https://computationstructures.org/)
- [ ] **Textbook (free materials):** [Harris & Harris DDCA RISC-V companion](https://pages.hmc.edu/harris/ddca/ddcarv.html) — free Ch.9, appendices, slides, labs, odd solutions; ⚠️ core chapters 2–8 paid (use computationstructures.org as the fully-free book)
- [ ] **Hands-on project (auto-checkable, no hardware):** [Nand2Tetris Part I](https://www.nand2tetris.org/) — build a CPU from NAND gates
- Exam practice via 6.004 solved worksheets + Harris odd-solutions.

### Computer Architecture Gateway (Machine Structures) — *high*
- [ ] **Lectures:** [notes.cs61c.org](https://notes.cs61c.org/) · video via [MIT 6.004](https://www.youtube.com/playlist?list=PLUl4u3cNGP62WVs95MNq3dQBqY2vGOtQ2) or [Mutlu DDCA](https://www.youtube.com/playlist?list=PL5Q2soXY2Zi-EImKxYYY1SZuGiOAOBKaf) (⚠️ current CS61C videos login-gated; these are the open routes)
- [ ] **Projects:** [CS61C labs](https://cs61c.org/su26/labs/) + [projects](https://cs61c.org/su26/projects/) — flagship CS61CPU builds a pipelined RISC-V CPU in free Logisim (no FPGA)
- [ ] **Exams + solutions:** [CS61C archive](https://cs61c.org/su26/resources/exams/) ✅ one of the best anywhere
- ⚠️ Patterson & Hennessy textbook is paid; CS61C notes + Harris free chapters substitute.

> **Deferred: standalone HDL/FPGA Lab course** (Berkeley EECS151). Weakest free self-study path: dead slides (expired TLS), login-gated MIT 6.205, flagship project needs a [Xilinx PYNQ-Z1 + Vivado](https://github.com/EECS150), no public autograder. Get RTL/pipelining intuition from **Nand2Tetris** instead. Free RTL refs for anyone pursuing it: [Nandland](https://nandland.com/), [asic-world](http://www.asic-world.com/), [chipverify](https://chipverify.com/).

---

## Phase 3 — ⭐ The core perf gap-fill (highest ROI)

### Advanced Computer Architecture & Microarchitecture — *ESSENTIAL*
*Best free stack found — videos AND homeworks-with-solutions AND exams-with-solutions.*
- [ ] **Lectures (video):** [ETH Computer Architecture Fall 2024 (Mutlu)](https://www.youtube.com/watch?v=ziMRjDlLEwo&list=PL5Q2soXY2Zi-LfDdGgWyLcTSqzm6a26wD) · [all iterations index](https://people.inf.ethz.ch/omutlu/lecture-videos.html)
- [ ] **Slides + HW w/ solutions:** [SAFARI Fall 2024 schedule](https://safari.ethz.ch/architecture/fall2024/doku.php?id=schedule) + [homeworks w/ solution PDFs](https://safari.ethz.ch/architecture/fall2024/doku.php?id=homeworks) (bot-block fetchers but live in a browser)
- [ ] **Exams w/ solutions:** [SAFARI past exams](https://safari.ethz.ch/architecture/fall2023/doku.php?id=exams)
- [ ] **Notes-only alt:** [MIT 6.823](https://ocw.mit.edu/courses/6-823-computer-system-architecture-fall-2005/) / current [MIT 6.5900](https://csg.csail.mit.edu/6.5900/)
- ⚠️ Hennessy & Patterson "Quantitative Approach" has no legal free PDF; Mutlu slides + Harris chapters cover it.

### Memory Systems & the HW-SW Performance Interface — *ESSENTIAL*
*The analytical heart of performance work — where most real-world bottlenecks actually live.*
- [ ] **Lectures (video):** [Mutlu "Memory Systems & Memory-Centric Computing" (ACACES 2024)](https://www.youtube.com/playlist?list=PL5Q2soXY2Zi9-RzPBbP_z7TlJcYUzClVT)
- [ ] **Slides:** [CMU 18-344](https://course.ece.cmu.edu/~ece344/calendar.html) (slides only; lab tarballs AFS-gated) — ⚠️ the host's TLS cert is expired, so browsers will show a security warning; content is still served
- [ ] **Free textbook:** [Primer on Memory Consistency & Cache Coherence, 2nd ed.](https://library.oapen.org/handle/20.500.12657/61248) (open-access) + [CS:APP slides/labs](http://csapp.cs.cmu.edu/)
- ⚠️ No single course gives free video + assignments + exam keys; assemble-it-yourself mosaic. Roadmap: [Stanford EE282 syllabus](https://web.stanford.edu/class/ee282/).

---

## Phase 4 — 🎯 The bullseye: GPU architecture + CUDA

### Parallel & GPU Architecture and CUDA Programming — *ESSENTIAL*
- [ ] **Lectures:** [Stanford CS149 slides](https://gfxcourses.stanford.edu/cs149/fall24/lecture/) · video via [CMU 15-418 (Kayvon Fatahalian)](https://www.youtube.com/playlist?list=PLpIxOj-HnDsO4Atvrp86c-4La9Mq3kMQZ) · [UIUC ECE408 CUDA slides](https://lumetta.web.engr.illinois.edu/408-Sum25/) (co-developed with NVIDIA)
- [ ] **Free reference:** [NVIDIA CUDA C++ Programming Guide](https://docs.nvidia.com/cuda/cuda-c-programming-guide/index.html) + [H&P free appendices A-M](https://shop.elsevier.com/books/book-companion/9780128119051)
- [ ] **Projects w/ self-grader:** [Stanford CS149 GitHub](https://github.com/stanford-cs149) — asst3 CUDA circle-renderer + `checker.py` (needs a GPU)
- [ ] **Exams WITH solutions:** [UIUC ECE408 past exams + keys](https://lumetta.web.engr.illinois.edu/408-Sum25/) — strongest free GPU exams
- [ ] **DNN accelerators (bonus):** [MIT 6.5930 Hardware for Deep Learning (Emer & Sze)](https://csg.csail.mit.edu/6.5930/syllabus.html)
- ⚠️ Berkeley CS152 recordings/slides are NOT public (CalNet-gated). Kirk & Hwu PMPP textbook is paid-only — the CUDA Guide is the free substitute.
- 💡 No local GPU? Free-tier Google Colab and Kaggle notebooks both provide one, which is enough for the CS149 and ECE408 assignments.

---

## Phase 5 — Power & thermal depth (take only the physical-limits intuition)

### Semiconductor Devices & Device Physics — *medium*
- [ ] **Lectures (video):** [GT ECE3030 (Shimeng Yu)](https://www.youtube.com/playlist?list=PLnQi8W6dRSW5yadACh5DpkymqrGYOFiay) · [NPTEL Solid State Devices (Karmalkar)](https://nptel.ac.in/courses/117106091)
- [ ] **Free textbook:** [Chenming Hu "Modern Semiconductor Devices for ICs"](https://www.chu.berkeley.edu/modern-semiconductor-devices-for-integrated-circuits-chenming-calvin-hu-2010/) (all 8 chapters free)
- [ ] **Psets/exams WITH solutions:** [MIT 6.012](https://ocw.mit.edu/courses/6-012-microelectronic-devices-and-circuits-fall-2009/pages/exams/)
- Take only: why leakage rises with temperature, CV²f dynamic power, and the V-f curve that bounds boost clocks.

### VLSI & Digital IC Design — *medium* (concepts, skip the tape-out)
- [ ] **Lectures + slides + exams w/ solutions:** [Berkeley EECS151 site](https://eecs150.github.io/) + [YouTube](https://www.youtube.com/playlist?list=PL0my2vWlgbox1lt-13GcaOx43--4b0rby) + [HKN exam archive w/ solutions](https://hkn.eecs.berkeley.edu/exams/course/eecs/151)
- [ ] **Free textbook materials:** [Weste & Harris "CMOS VLSI Design" companion](https://pages.hmc.edu/harris/cmosvlsi/4e/) (free slides, figures, odd solutions; ⚠️ full prose paid)
- Take only: logical effort, the power equation, clock trees. Skip the commercial-EDA tape-out flow.

### Embedded Systems & HW-SW Co-Design — *low* (skim for platform/firmware context)
- [ ] **Lectures (video):** [UT Austin "Shape The World" (Valvano)](https://users.ece.utexas.edu/~valvano/arm/lectures.html) — ~170 free videos
- [ ] **Free textbooks:** [Lee & Seshia "Intro to Embedded Systems" (full free PDF)](https://ptolemy.berkeley.edu/books/leeseshia/) · [Valvano Volume 1 e-book](https://users.ece.utexas.edu/~valvano/Volume1/E-Book/) (⚠️ Vol 2 / RTOS internals paid)
- [ ] **Assessment:** [free edX audit](https://www.edx.org/course/embedded-systems-shape-the-world-microcontroller-i)
- ⚠️ CMU 18-349 handout PDFs currently return HTTP 500 (broken); Lee & Seshia + Valvano cover the ground.

---

## Phase 6 — As-needed

### Signals & Systems / DSP — *low*
- [ ] **Lectures + psets + exams ALL w/ solutions:** [MIT 6.003](https://ocw.mit.edu/courses/6-003-signals-and-systems-fall-2011/) · classic [MIT RES.6-007 (Oppenheim)](https://ocw.mit.edu/courses/res-6-007-signals-and-systems-spring-2011/video_galleries/video-lectures/)
- [ ] **Free textbooks:** [Michael Adams "Signals and Systems"](https://www.ece.uvic.ca/~frodo/sigsysbook/) · [Baraniuk (LibreTexts)](https://eng.libretexts.org/Bookshelves/Electrical_Engineering/Signal_Processing_and_Modeling/Signals_and_Systems_(Baraniuk_et_al.))
- Conceptual pass only — sampling and the frequency domain, for clock jitter, PLLs, and telemetry sampling. ⚠️ Oppenheim & Willsky text has no legal free PDF.

---

## 🔑 The Critical Gaps — what no CE course teaches but the job demands

*The most important section. None of this is in a standard curriculum, yet it is closest to the actual day-to-day work of
performance engineering. Weave it in from Phase 3 onward rather than saving it for last.*

- [ ] **1. Profiling & measurement methodology** (literally the job) → [Brendan Gregg's free slides + USE Method](https://www.brendangregg.com/usemethod.html)
- [ ] **2. Nsight Systems / Nsight Compute** (reading a real profiler report) → [Nsight Compute Profiling Guide](https://docs.nvidia.com/nsight-compute/ProfilingGuide/) + [GPU MODE lectures](https://github.com/gpu-mode/lectures)
- [ ] **3. The Roofline model** → [Williams/Waterman/Patterson original paper (free PDF)](https://people.eecs.berkeley.edu/~kubitron/cs252/handouts/papers/RooflineVyNoYellow.pdf)
- [ ] **4. CUDA optimization workflow (APOD)** → [NVIDIA CUDA C++ Best Practices Guide](https://docs.nvidia.com/cuda/cuda-c-best-practices-guide/)
- [ ] **5. Current GPU microarch vocabulary** (courses use 2016-era generic material) → [Modal GPU Glossary](https://modal.com/gpu-glossary) + NVIDIA Ada/Hopper/Blackwell whitepapers
- [ ] **6. Heat transfer & thermal RC modeling** ⭐ *the widest gap between coursework and practice* → [MIT OCW 2.051 Intro to Heat Transfer](https://ocw.mit.edu/courses/2-051-introduction-to-heat-transfer-fall-2015/) — junction-to-ambient R_th networks predict throttle behavior on anything power-limited, from a phone SoC to a datacenter GPU
- [ ] **7. Power modeling & DVFS in depth** → Mutlu's lectures + Chenming Hu's CV²f/leakage chapters
- [ ] **8. GPU floating-point** (FP16/BF16/TF32, FMA, non-associativity) → [Goldberg "What Every CS Should Know About Floating-Point"](https://docs.oracle.com/cd/E19957-01/806-3568/ncg_goldberg.html)
- [ ] **9. Interconnect/transfer cost** (PCIe/NVLink — host-device transfer often dominates the kernel it feeds) → H&P free Appendix F + CUDA Best Practices host-device section
- [ ] **10. OS scheduler/governor/driver noise** (where bad benchmarks come from) → [Brendan Gregg Linux perf](https://www.brendangregg.com/linuxperf.html)

---

## Adapting this for other CE focuses

The sequence above optimizes for performance engineering. Other CE careers re-weight the same material:

| Goal | Emphasize | De-emphasize |
|---|---|---|
| **Embedded / firmware** | Phase 5 embedded (promote to a full course), Phase 2 digital logic, Phase 1 circuits at design level | Phase 4 GPU, Phase 3 advanced microarchitecture |
| **RTL / ASIC / FPGA design** | Phase 2 digital logic + the deferred HDL/FPGA track, Phase 5 VLSI (full, including the EDA flow) | Phase 4 CUDA, the Critical Gaps profiling items |
| **Systems software / OS / compilers** | Phase 2 arch gateway, Phase 3 both courses, Critical Gaps 1 and 10 | Phase 1 physics, Phase 5 devices and VLSI |
| **ML systems / accelerators** | Phase 3, Phase 4 (including MIT 6.5930), Critical Gaps 2–5 and 8–9 | Phase 5 embedded, Phase 6 signals |
| **Hardware-adjacent SWE breadth** | Phase 2 in full, Phase 3 microarchitecture | Phases 1, 5, and 6 — skim only |

The one section worth keeping regardless of goal is **Phase 2** — it is the shared foundation every other path builds on.

---

## Where free material is weak (honest summary)

- **HDL/FPGA lab** — broken or gated; deprioritize and use Nand2Tetris instead.
- **Memory systems** — assemble-it-yourself, no exam keys.
- **Embedded** — no graded exams with keys.
- **Canonical textbooks** — Hennessy & Patterson, Patterson & Hennessy, Kirk & Hwu, Oppenheim & Willsky, and Strang all lack a legal free PDF. Substitutes are listed inline; used copies are usually cheap.
- Everything in the essential **Phases 3–4** has excellent free coverage.

## Source curricula

Degree requirements these phases were reverse-engineered from:

[MIT 6-5/6-2](https://catalog.mit.edu/degree-charts/electrical-engineering-computing-course-6-5/) · [Stanford EE](https://bulletin.stanford.edu/programs/EE-BS) · [UIUC CompE](https://catalog.illinois.edu/undergraduate/engineering/computer-engineering-bs/) · [CMU ECE](https://www.ece.cmu.edu/academics/bs-in-ece/academic-guide.html) · [Berkeley EECS](https://guide.berkeley.edu/undergraduate/degree-programs/electrical-engineering-computer-sciences/) · [Georgia Tech CmpE](https://catalog.gatech.edu/programs/computer-engineering-bs/)

## Contributing

Corrections welcome, especially:

- **Dead or newly-gated links.** Course sites rotate URLs every term; this list will rot without help.
- **Better free substitutes**, particularly for the paid textbooks and the weak areas listed above.
- **Free material with published solutions** — the scarcest and most valuable resource for self-study.

Open an issue or a PR. Please keep the ✅/⚠️ status flags accurate, and verify that any added link is both live and legal
to access for free.

## License

The curriculum itself — the sequencing, the annotations, and the prose — is released under
[Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).
Copy it, fork it, remix it, or build a course on it; just credit the source.

**This does not extend to the linked material.** Every course, lecture recording, textbook, and problem set referenced
here remains under its own license and terms — MIT OCW's CC BY-NC-SA, individual publisher terms, university course
policies, and so on. Everything was checked to be free and legal to *access* at the time of linking, which is a narrower
claim than being free to redistribute. Check the source before republishing anything from it.
