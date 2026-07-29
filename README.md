# Self-Taught Computer Engineering Degree — Free Course Plan

> A self-study computer-engineering curriculum built from free, link-verified online course material.
> Tailored for a **CS grad** moving into **GPU / GeForce-notebook performance engineering** — focus on the *hardware* side.
>
> Compiled 2026-06-03 · links re-verified 2026-07-29. Every link below was fetched and checked for existence + legality.
> Status flags: ✅ excellent free coverage · ⚠️ a paid/gated/dead caveat to know.
>
> **Note on course-site links:** university course sites rotate their URL each term (e.g. `cs61c.org/su26/`).
> If a term-stamped link 404s or hits a campus login, drop to the site root — it usually redirects to the current term.

---

## The big picture

A CE degree differs from a CS degree mainly in: **circuits & electronics, signals/systems, digital design, deep computer architecture, VLSI/devices, and embedded systems**.

**Key insight:** the canonical CE degree teaches what hardware *is* far better than how to *measure* it or how a notebook's power/thermal envelope constrains it. The three things most relevant to GPU/notebook perf work — **profiling methodology, thermal RC modeling, DVFS/power budgeting** — aren't real courses anywhere, so they're broken out in [The Critical Gaps](#-the-critical-gaps--what-no-ce-course-teaches-but-the-job-demands).

**Availability verdict:** ~90% of what you need is free and legal. Recurring gaps: (1) canonical paid textbooks (Hennessy & Patterson, Patterson & Hennessy, Kirk & Hwu) have **no legal free PDF** — free substitutes cover them; (2) hands-on FPGA labs and graded autograders are mostly gated.

---

## Recommended sequence

| Phase | Courses | Action |
|---|---|---|
| **0. Gap-check (1–2 wk)** | Low-level C/asm, Discrete math/algo/prob | **Skip as courses.** Confirm fluency; re-sharpen *probability/stats* for benchmark noise. |
| **1. Math/physics gaps (4–8 wk)** | Eng. math (ODE/Laplace), Physics (E&M + thermal) | **Skim.** New load-bearing bits: ODEs/transforms (RC + thermal transients), E&M/thermal. |
| **2. Hardware mental model (8–12 wk)** | Circuits, Digital logic, Arch gateway | Read-level circuits; digital logic + a Nand2Tetris CPU build; caches/pipelining. |
| **3. ⭐ Core perf gap-fill (10–14 wk)** | **Advanced microarchitecture, Memory systems** | **Highest ROI.** Quantitative methodology + memory/bandwidth reasoning. |
| **4. 🎯 The bullseye (10–14 wk)** | **GPU/parallel arch + CUDA** | UIUC ECE408 / Stanford CS149 on real hardware with Nsight. |
| **5. Notebook depth (6–10 wk)** | Semiconductor devices, VLSI, Embedded | Take only power/thermal/leakage/V-f intuition + missing thermal/DVFS topics. |
| **6. As-needed** | Signals & systems | Conceptual pass only (clocks/PLLs/jitter). |

---

## Phase 0 — Gap-check (you already own these)

### Low-Level Programming: C, Assembly & the Machine Model — *likely-already-covered*
*Berkeley CS61C · CMU 15-213/CS:APP · UIUC ECE220*
- [ ] **Lectures (video):** [Berkeley CS61C](https://www.youtube.com/playlist?list=PLhMnuBfGeCDM8pXLpqib90mDFJI-e1lpk) · [CMU 15-213 (Bryant & O'Hallaron)](https://www.youtube.com/playlist?list=PL2dWYoM7ypKy8yuOV01RGMRDEaw5sNyyz)
- [ ] **Textbook (free substitute):** [CS61C course notes](https://notes.cs61c.org/) — the legal open stand-in for the ⚠️ paid CS:APP book
- [ ] **Labs:** [CS:APP self-study labs](https://csapp.cs.cmu.edu/3e/labs.html) (Data/Bomb/Attack/Malloc) · [Nand2Tetris](https://www.nand2tetris.org/) (self-checking)
- [ ] **Exams + solutions:** [CS61C exam archive 2015–2026](https://cs61c.org/su26/resources/exams/) ✅

### Discrete Math, Algorithms & Probability — *likely-already-covered* (re-sharpen probability)
*MIT 6.042J · Berkeley CS70*
- [ ] **Lectures + free textbook:** [MIT 6.042J](https://ocw.mit.edu/courses/6-042j-mathematics-for-computer-science-spring-2015/) + [full free PDF](https://ocw.mit.edu/courses/6-042j-mathematics-for-computer-science-spring-2015/mit6_042js15_textbook.pdf)
- [ ] **Probability practice:** [Berkeley CS70 notes + HW w/ solutions](https://www.eecs70.org/) · [UIUC ECE313 old exams w/ solutions](https://courses.grainger.illinois.edu/ece313/sp2025/old_exams.html)
- ⚠️ CLRS is paid; free algo video via [MIT 6.006](https://ocw.mit.edu/courses/6-006-introduction-to-algorithms-spring-2020/) + [Roughgarden](https://www.algorithmsilluminated.org/).

---

## Phase 1 — Math & physics gaps

### Engineering Math: Multivariable Calc, Linear Algebra & ODEs — *medium*
- [ ] **Lectures + psets + exams (all w/ solutions):** [MIT 18.06SC Linear Algebra (Strang)](https://ocw.mit.edu/courses/18-06sc-linear-algebra-fall-2011/) · [18.02SC Multivariable](https://ocw.mit.edu/courses/18-02sc-multivariable-calculus-fall-2010/) · [18.03SC Differential Equations](https://ocw.mit.edu/courses/18-03sc-differential-equations-fall-2011/) — **the new part for you is ODEs/Laplace** (RC + thermal transients)
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
- [ ] **Psets/exams WITH solutions:** [Berkeley EECS16B](https://eecs16b.org/) ← fills MIT 6.002's missing-solutions gap; linear-algebra framing suits you
- [ ] **On-ramp:** [Khan Academy Circuit Analysis](https://www.khanacademy.org/science/electrical-engineering/ee-circuit-analysis-topic)
- Why for you: RC time constants & power delivery → dVDD droop and throttle behavior.

### Digital Logic Design — *high*
- [ ] **Lectures (best free set):** [Onur Mutlu DDCA (ETH)](https://www.youtube.com/playlist?list=PL5Q2soXY2Zi9Eo29LMgKVcaydS7V1zZW3) · [MIT 6.004](https://ocw.mit.edu/courses/6-004-computation-structures-spring-2017/) + open notes [computationstructures.org](https://computationstructures.org/)
- [ ] **Textbook (free materials):** [Harris & Harris DDCA RISC-V companion](https://pages.hmc.edu/harris/ddca/ddcarv.html) — free Ch.9, appendices, slides, labs, odd solutions; ⚠️ core chapters 2–8 paid (use computationstructures.org as fully-free book)
- [ ] **Hands-on project (auto-checkable, no hardware):** [Nand2Tetris Part I](https://www.nand2tetris.org/) — build a CPU from NAND gates
- Exam practice via 6.004 solved worksheets + Harris odd-solutions.

### Computer Architecture Gateway (Machine Structures) — *high*
- [ ] **Lectures:** [notes.cs61c.org](https://notes.cs61c.org/) · video via [MIT 6.004](https://www.youtube.com/playlist?list=PLUl4u3cNGP62WVs95MNq3dQBqY2vGOtQ2) or [Mutlu DDCA](https://www.youtube.com/playlist?list=PL5Q2soXY2Zi-EImKxYYY1SZuGiOAOBKaf) (⚠️ current CS61C videos login-gated; these are the open routes)
- [ ] **Projects:** [CS61C labs](https://cs61c.org/su26/labs/) + [projects](https://cs61c.org/su26/projects/) — flagship CS61CPU builds a pipelined RISC-V CPU in free Logisim (no FPGA)
- [ ] **Exams + solutions:** [CS61C archive](https://cs61c.org/su26/resources/exams/) ✅ one of the best anywhere
- ⚠️ Patterson & Hennessy textbook is paid; CS61C notes + Harris free chapters substitute.

> **Deferred: standalone HDL/FPGA Lab course** (Berkeley EECS151). Weakest free self-study path: dead slides (expired TLS), login-gated MIT 6.205, flagship project needs a [Xilinx PYNQ-Z1 + Vivado](https://github.com/EECS150), no public autograder. Get RTL/pipelining intuition from **Nand2Tetris** instead. Free RTL refs if you pursue it: [Nandland](https://nandland.com/), [asic-world](http://www.asic-world.com/), [chipverify](https://chipverify.com/).

---

## Phase 3 — ⭐ The core perf gap-fill (highest ROI)

### Advanced Computer Architecture & Microarchitecture — *ESSENTIAL*
*Best free stack found — videos AND homeworks-with-solutions AND exams-with-solutions.*
- [ ] **Lectures (video):** [ETH Computer Architecture Fall 2024 (Mutlu)](https://www.youtube.com/watch?v=ziMRjDlLEwo&list=PL5Q2soXY2Zi-LfDdGgWyLcTSqzm6a26wD) · [all iterations index](https://people.inf.ethz.ch/omutlu/lecture-videos.html)
- [ ] **Slides + HW w/ solutions:** [SAFARI Fall 2024 schedule](https://safari.ethz.ch/architecture/fall2024/doku.php?id=schedule) + [homeworks w/ solution PDFs](https://safari.ethz.ch/architecture/fall2024/doku.php?id=homeworks) (bot-block fetchers but live in a browser)
- [ ] **Exams w/ solutions:** [SAFARI past exams](https://safari.ethz.ch/architecture/fall2023/doku.php?id=exams)
- [ ] **Notes-only alt:** [MIT 6.823](https://ocw.mit.edu/courses/6-823-computer-system-architecture-fall-2005/) / current [MIT 6.5900](https://csg.csail.mit.edu/6.5900/)
- ⚠️ Hennessy & Patterson "Quantitative Approach" has no legal free PDF; Mutlu slides + Harris chapters cover it.

### Memory Systems & the HW-SW Performance Interface — *ESSENTIAL* (your analytical home)
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
- ⚠️ Berkeley CS152 recordings/slides are NOT public (CalNet-gated). Kirk & Hwu PMPP textbook is paid-only — CUDA Guide is the free substitute.

---

## Phase 5 — Notebook-platform depth (take only the power/thermal intuition)

### Semiconductor Devices & Device Physics — *medium*
- [ ] **Lectures (video):** [GT ECE3030 (Shimeng Yu)](https://www.youtube.com/playlist?list=PLnQi8W6dRSW5yadACh5DpkymqrGYOFiay) · [NPTEL Solid State Devices (Karmalkar)](https://nptel.ac.in/courses/117106091)
- [ ] **Free textbook:** [Chenming Hu "Modern Semiconductor Devices for ICs"](https://www.chu.berkeley.edu/modern-semiconductor-devices-for-integrated-circuits-chenming-calvin-hu-2010/) (all 8 chapters free)
- [ ] **Psets/exams WITH solutions:** [MIT 6.012](https://ocw.mit.edu/courses/6-012-microelectronic-devices-and-circuits-fall-2009/pages/exams/)
- Take only: why leakage rises with temp, CV²f dynamic power, the V-f curve bounding boost clocks.

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
- Conceptual pass only — sampling/frequency domain for clock jitter, PLLs, telemetry sampling. ⚠️ Oppenheim & Willsky text has no legal free PDF.

---

## 🔑 The Critical Gaps — what no CE course teaches but the job demands

*Most important section. Not in any curriculum, but closest to your daily work — weave in from Phase 3 onward, don't save for last.*

- [ ] **1. Profiling & measurement methodology** (literally the job) → [Brendan Gregg's free slides + USE Method](https://www.brendangregg.com/usemethod.html)
- [ ] **2. Nsight Systems / Nsight Compute** (reading a real profiler report) → [Nsight Compute Profiling Guide](https://docs.nvidia.com/nsight-compute/ProfilingGuide/) + [GPU MODE lectures](https://github.com/gpu-mode/lectures)
- [ ] **3. The Roofline model** → [Williams/Waterman/Patterson original paper (free PDF)](https://people.eecs.berkeley.edu/~kubitron/cs252/handouts/papers/RooflineVyNoYellow.pdf)
- [ ] **4. CUDA optimization workflow (APOD)** → [NVIDIA CUDA C++ Best Practices Guide](https://docs.nvidia.com/cuda/cuda-c-best-practices-guide/)
- [ ] **5. Current GPU microarch vocabulary** (courses use 2016-era generic material) → [Modal GPU Glossary](https://modal.com/gpu-glossary) + NVIDIA Ada/Hopper/Blackwell whitepapers
- [ ] **6. Heat transfer & thermal RC modeling** ⭐ *most notebook-specific gap* → [MIT OCW 2.051 Intro to Heat Transfer](https://ocw.mit.edu/courses/2-051-introduction-to-heat-transfer-fall-2015/) — junction-to-ambient R_th networks predict throttle behavior
- [ ] **7. Power modeling & DVFS in depth** → Mutlu's lectures + Chenming Hu's CV²f/leakage chapters
- [ ] **8. GPU floating-point** (FP16/BF16/TF32, FMA, non-associativity) → [Goldberg "What Every CS Should Know About Floating-Point"](https://docs.oracle.com/cd/E19957-01/806-3568/ncg_goldberg.html)
- [ ] **9. Interconnect/transfer cost** (PCIe/NVLink, often dominates on Optimus notebooks) → H&P free Appendix F + CUDA Best Practices host-device section
- [ ] **10. OS scheduler/governor/driver noise** (where bad benchmarks come from) → [Brendan Gregg Linux perf](https://www.brendangregg.com/linuxperf.html)

---

## Where free material is weak (honest summary)

- **HDL/FPGA lab** — broken/gated; deprioritize, use Nand2Tetris.
- **Memory systems** — assemble-it-yourself, no exam keys.
- **Embedded** — no graded exams with keys.
- Everything in essential **Phases 3–4** has excellent free coverage.

## Source curricula

[MIT 6-5/6-2](https://catalog.mit.edu/degree-charts/electrical-engineering-computing-course-6-5/) · [Stanford EE](https://bulletin.stanford.edu/programs/EE-BS) · [UIUC CompE](https://catalog.illinois.edu/undergraduate/engineering/computer-engineering-bs/) · [CMU ECE](https://www.ece.cmu.edu/academics/bs-in-ece/academic-guide.html) · [Berkeley EECS](https://guide.berkeley.edu/undergraduate/degree-programs/electrical-engineering-computer-sciences/) · [Georgia Tech CmpE](https://catalog.gatech.edu/programs/computer-engineering-bs/)
