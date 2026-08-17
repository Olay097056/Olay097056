# NW

**IT support / infrastructure.** I build the tools for the problems I run into —
from the copper up to the routines people forget. Everything below started as
something that broke and had to be fixed, not an exercise.

Most of these you can open and use right now.

---

### The wire

**[serial-loopback](https://github.com/Olay097056/serial-loopback)** · [▶ walkthrough](https://olay097056.github.io/serial-loopback/)

Sweeps a COM port across 11 baud rates through a loopback plug and reports which
speeds it can actually carry. Written twice: Python for a modern workstation,
and a single 40 KB .NET 3.5 executable for the Windows XP instrument controllers
that cannot take new software — copy it on, run it, delete it.

### The network

**switch-wr-tool** · [▶ public demo](https://olay097056.github.io/switch-wr-demo/) · *source closed — employer work, happy to walk through it*

Nightly `write memory` across a 74-switch Cisco fleet, config backup with diff,
MAC-to-port lookup that follows CDP and port-channels to the real access port,
and a CDP topology graph. Flask + React 19 in one container. Fleet state is
computed once in one place and every endpoint's key set is pinned by a test —
after a bug where the main view was wrong on 7 of 10 fields because three code
paths each defined "the fleet" their own way.

### The endpoints

**[txt-to-excel](https://github.com/Olay097056/txt-to-excel)** · [▶ try it](https://olay097056.github.io/txt-to-excel/)

Reads the raw export of ETWIN card-reader terminals and names which terminal is
malfunctioning. Two detection layers: hard rules for impossible values, and
per-terminal frequency for values that are perfectly legal but abnormal *for
that unit* — the failure mode where a reader quietly mangles a digit and nobody
notices until someone's attendance stops adding up.

**[time-etwin](https://github.com/Olay097056/time-etwin)**

The other half of the same problem: floor staff can see a reader is broken but
have no way to say which one. A floor plan with the readers pinned on it, so
they report from where the thing is rather than what it is called.

### The routine

**[line-msg-v2](https://github.com/Olay097056/line-msg-v2)**

Reminders for recurring work nobody schedules, because "we do that every day
anyway" — right up until the day nobody does. Pushes into the LINE group the
team already watches, with dashboard-editable schedules and live quota tracking.
The `sent` row is written to the database *before* the API call, so a uniqueness
constraint prevents duplicate messages rather than the hope that the scheduler
never fires twice.

### Off the clock

**[portfolio-tracker](https://github.com/Olay097056/portfolio-tracker)** · [▶ live app](https://portfolio-tracker-taupe-two.vercel.app)

Stock portfolio tracker with signal scanners and an AI analyst layer. Its
confidence score was measured against real outcomes, found to predict nothing,
and thrown out — replaced by a fitted logistic regression and an LLM read shown
side by side, rather than re-weighted until it looked better.

**[thai-lottery-stats](https://github.com/Olay097056/thai-lottery-stats)** · [▶ run the backtest](https://olay097056.github.io/thai-lottery-stats/demo/)

Backtests every Thai lottery "lucky number formula" against 780 real draws with
holdout discipline and baseline-adjusted edge. The answer is mostly no, and the
app reports it. Change the test window in the demo and watch which formulas keep
their edge — most do not.

---

Python · TypeScript · C# · Flask · FastAPI · React · Docker · Cisco / Netmiko

Every repo has a README in English and Thai.
