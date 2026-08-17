<a id="top"></a>

**English** · [ภาษาไทย ↓](#thai)

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

<br>

---

<a id="thai"></a>

[English ↑](#top) · **ภาษาไทย**

# NW

**IT support / infrastructure** ผมเขียนเครื่องมือแก้ปัญหาที่ตัวเองเจอหน้างาน —
ตั้งแต่สายแลนกับพอร์ต ไปจนถึงงานประจำที่คนลืมทำ ทุกตัวข้างล่างนี้เริ่มจากของที่พังจริง
และต้องแก้ ไม่ใช่โจทย์ฝึกหัด

ส่วนใหญ่กดเข้าไปลองเล่นได้เลยตอนนี้

---

### สายและพอร์ต

**[serial-loopback](https://github.com/Olay097056/serial-loopback)** · [▶ เดินดูหน้าตา](https://olay097056.github.io/serial-loopback/)

ไล่ทดสอบพอร์ต COM ครบ 11 baud rate ผ่าน loopback plug แล้วบอกว่าพอร์ตนั้นรับส่งได้จริง
ที่ความเร็วไหนบ้าง เขียนไว้สองเวอร์ชัน — Python สำหรับเครื่องสมัยใหม่ และ .NET 3.5
ไฟล์เดียว 40 KB สำหรับเครื่องคุมอุปกรณ์ที่รัน Windows XP ซึ่งลงอะไรเพิ่มไม่ได้
ก๊อปไปวาง รัน แล้วลบทิ้งได้เลย

### เครือข่าย

**switch-wr-tool** · [▶ demo สาธารณะ](https://olay097056.github.io/switch-wr-demo/) · *โค้ดปิด — งานบริษัท ยินดีพาดูเป็นรายคน*

รัน `write memory` อัตโนมัติทุกคืนทั่ว Cisco fleet 74 ตัว สำรอง config พร้อมหน้าเทียบ
ความต่าง ค้นหา MAC ว่าอยู่พอร์ตไหนโดยตาม CDP และ port-channel ต่อจนถึงพอร์ต access จริง
และวาด topology จาก CDP ทำด้วย Flask + React 19 แพ็กเป็นคอนเทนเนอร์เดียว
สถานะของ fleet ถูกคำนวณครั้งเดียวที่เดียว และชุดคีย์ของทุก endpoint ถูกล็อกด้วยเทส —
หลังเจอบั๊กที่หน้าหลักแสดงค่าเพี้ยนไป 7 จาก 10 คีย์ เพราะโค้ดสามเส้นทางต่างคนต่างนิยาม
คำว่า "fleet" ในแบบของตัวเอง

### อุปกรณ์ปลายทาง

**[txt-to-excel](https://github.com/Olay097056/txt-to-excel)** · [▶ ลองใช้](https://olay097056.github.io/txt-to-excel/)

อ่านไฟล์ export ดิบจากเครื่องรูดบัตร ETWIN แล้วชี้ว่าเครื่องไหนกำลังมีปัญหา
ตรวจสองชั้น — กฎตายตัวจับค่าที่เป็นไปไม่ได้ และความถี่รายเครื่องจับค่าที่ถูกต้องสมบูรณ์
แต่ผิดปกติ*สำหรับเครื่องนั้น* ซึ่งเป็นรูปแบบความเสียหายที่เครื่องอ่านเลขเพี้ยนเงียบๆ
โดยไม่มีใครรู้ จนกระทั่งเวลาเข้าออกงานของใครสักคนไม่ตรง

**[time-etwin](https://github.com/Olay097056/time-etwin)**

อีกด้านของปัญหาเดียวกัน — คนหน้างานเห็นว่าเครื่องเสีย แต่ไม่มีช่องทางบอกว่าเครื่องไหน
เลยทำแผนผังพื้นที่ที่ปักหมุดตำแหน่งเครื่องไว้ ให้แจ้งจากตรงที่ของมันตั้งอยู่
แทนที่จะต้องรู้ว่ามันชื่อรหัสอะไร

### งานประจำ

**[line-msg-v2](https://github.com/Olay097056/line-msg-v2)**

แจ้งเตือนงาน routine ที่ไม่มีใครตั้งเตือน เพราะ "ก็ทำอยู่ทุกวันอยู่แล้ว" —
จนถึงวันที่ไม่มีใครทำ ระบบยิงข้อความเข้ากลุ่ม LINE ที่ทีมเฝ้าอยู่แล้ว
แก้เวลาและข้อความได้จากหน้าเว็บ พร้อมติดตามโควต้าที่เหลือแบบเรียลไทม์
แถว `sent` ถูกเขียนลงฐานข้อมูล*ก่อน*เรียก API ให้ข้อบังคับ unique เป็นตัวกันส่งซ้ำ
แทนที่จะหวังว่าตัวจับเวลาจะไม่ยิงซ้อนกันเอง

### นอกเวลางาน

**[portfolio-tracker](https://github.com/Olay097056/portfolio-tracker)** · [▶ เปิดแอปจริง](https://portfolio-tracker-taupe-two.vercel.app)

เว็บบริหารพอร์ตหุ้น มีสแกนสัญญาณและชั้น AI ที่เขียนบทวิเคราะห์ให้
คะแนนความมั่นใจตัวเดิมถูกเอาไปวัดกับผลจริง แล้วพบว่าทำนายอะไรไม่ได้เลย จึงถูกทิ้ง —
แทนที่ด้วย logistic regression ที่ fit กับผลในอดีต วางคู่กับบทวิเคราะห์จาก LLM
แทนที่จะปรับน้ำหนักไปเรื่อยๆ จนตัวเลขดูดีขึ้น

**[thai-lottery-stats](https://github.com/Olay097056/thai-lottery-stats)** · [▶ รัน backtest](https://olay097056.github.io/thai-lottery-stats/demo/)

เอาสูตรหวยทุกสูตรไป backtest กับผลรางวัลจริง 780 งวด ด้วยวินัยเรื่อง holdout
และค่า Edge ที่หักลบเส้นฐานแล้ว คำตอบที่ได้คือส่วนใหญ่ไม่ชนะการสุ่ม และแอปรายงาน
ตามนั้น ลองสลับช่วงทดสอบใน demo แล้วดูว่าสูตรไหนรักษา Edge ไว้ได้ — ส่วนใหญ่รักษาไม่ได้

---

Python · TypeScript · C# · Flask · FastAPI · React · Docker · Cisco / Netmiko

ทุก repo มี README ทั้งภาษาไทยและอังกฤษ

[กลับขึ้นบน ↑](#top)
