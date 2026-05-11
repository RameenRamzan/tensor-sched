# ⚙️ TensorSched — AI Job Scheduler

A multi-threaded CPU job scheduling simulator built in **C++** as an Operating Systems semester project. TensorSched simulates how an OS dispatches and manages jobs using real scheduling algorithms, with a live terminal UI showing job states, resource usage, and a Gantt chart in real time.

---

## 🧠 Scheduling Algorithms Implemented

- **MLFQ (Multi-Level Feedback Queue)** — 3 priority levels with time quanta of 2, 4, and 8 ticks
- **Priority Scheduling** — Jobs assigned LOW / MEDIUM / HIGH / CRITICAL priority
- **Aging** — Prevents starvation by promoting long-waiting jobs up the queue
- **Preemption** — Higher priority jobs can preempt currently running ones

---

## ✨ Features

- **Real-time Job Dispatch** — Dispatcher thread continuously pulls jobs from the MLFQ and assigns them to worker threads
- **Resource Management** — Tracks CPU (100 units) and Memory (4096 MB) with semaphore-based concurrency control
- **Up to 4 Concurrent Workers** — Max 4 jobs run simultaneously, controlled via semaphores
- **Live Terminal UI** — Built with a TUI library showing:
  - Active worker slots with job names and MLFQ levels
  - CPU & memory usage bars
  - Scrollable event log with color-coded status
  - Real-time Gantt chart
  - Scheduler statistics (throughput, avg wait, avg turnaround, CPU utilization)
- **Job Lifecycle Tracking** — WAITING → READY → RUNNING → PREEMPTED → COMPLETED / FAILED
- **Up to 256 Jobs** supported

---

## 🛠️ Tech Stack

- **Language:** C++ (C++17)
- **OS Concepts Used:** Threads (`pthread`), Semaphores, Mutexes, Scheduling Algorithms, Resource Management, Concurrency
- **UI:** Terminal/TUI rendering with custom fonts (JetBrains Mono, Rajdhani)
- **Platform:** Cross-platform (Linux/Windows via `platform.h` abstraction)

---

## 🚀 How to Run

### Prerequisites
- GCC or Clang with C++17 support
- `pthread` library (Linux) or compatible threading library

### Build & Run
```bash
git clone https://github.com/OS-BCS-4K/semester-project-job-scheduler.git
cd semester-project-job-scheduler
make
./tensorsched
```

> **Windows users:** A `pthread_win.h` compatibility layer is included.

---

## 📁 Project Structure

```
├── main.cpp              # Entry point + TUI rendering loop
├── scheduler.cpp/h       # Core dispatcher, worker threads, aging thread
├── job.h                 # Job struct with MLFQ state, priority, timing
├── job_queue.h           # MLFQ queue implementation
├── resource_manager.h    # CPU/memory tracking, worker slots, semaphores
├── platform.h            # Cross-platform thread/semaphore abstraction
├── pthread_win.h         # Windows pthread compatibility
├── semaphore_win.h       # Windows semaphore compatibility
├── fonts/                # TUI display fonts
├── Makefile              # Build configuration
├── TensorSched_Report.pdf
└── OS Project Proposal.pdf
```

---

## 📊 Scheduler Stats Tracked

| Metric | Description |
|--------|-------------|
| Total Submitted | Jobs added to the queue |
| Total Completed | Successfully finished jobs |
| Total Failed | Jobs that couldn't acquire resources |
| Total Preemptions | How many times a job was preempted |
| Aging Promotions | Jobs moved up the queue to prevent starvation |
| Avg Wait Time | Average ticks a job waited before running |
| Avg Turnaround | Average real time from submit to completion |
| Throughput | Jobs completed per second |
| CPU Utilization | % of CPU in use |

---

## 👥 Contributors

- Umama Zubair | Rameen Ramzan

---

## 📄 Documentation

Full project report and proposal included in the repo as PDFs.

---

Developed for **Operating Systems** — BS Computer Science Semester Project
