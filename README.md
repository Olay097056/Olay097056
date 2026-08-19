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

**[printer-monitor](https://github.com/Olay097056/printer-monitor)** · [▶ public demo](https://olay097056.github.io/printer-monitor-demo/) · *source closed — employer work, happy to walk through it*

Hourly SNMP poll of a 20-printer fleet against the standard Printer-MIB
marker-supplies table, so it reads any vendor's toner level — page counts, a
depletion trend per cartridge, and the date each one runs dry predicted by
linear regression. Every supply charts on its own card and the "needs
attention" strip lists what will run out first. Fastify + SQLite + static
frontend behind a single password.

### The endpoints

**[txt-to-excel](https://github.com/Olay097056/txt-to-excel)** · [▶ try it](https://olay097056.github.io/txt-to-excel/)

Reads the raw export of ETWIN card-reader terminals and names which terminal is
malfunctioning. Two detection layers: hard rules for impossible values, and
per-terminal frequency for values that are perfectly legal but abnormal *for
that unit* — the failure mode where a reader quietly mangles a digit and nobody
notices until someone's attendance stops adding up.

**[time-etwin](https://github.com/Olay097056/time-etwin)** · [▶ demo](https://olay097056.github.io/time-etwin/demo/)

The other half of the same problem: floor staff can see a reader is broken but
have no way to say which one. A floor plan with the readers pinned on it, so
they report from where the thing is rather than what it is called. The rebuilt
app also carries the txt-to-excel analysis in the same page — flag a machine
from the log and it lights up on the map.

### The routine

**[line-msg](https://github.com/Olay097056/line-msg)** · [▶ demo](https://olay097056.github.io/line-msg-demo/)

Reminders for recurring work nobody schedules, because "we do that every day
anyway" — right up until the day nobody does. Pushes into the LINE group the
team already watches, with dashboard-editable schedules and live quota tracking.
The `sent` row is written to the database *before* the API call, so a uniqueness
constraint prevents duplicate messages rather than the hope that the scheduler
never fires twice.

**[NewHireFormatter](https://github.com/Olay097056/NewHireFormatter)** · [▶ demo](https://github.com/Olay097056/NewHireFormatter)

C# Windows Forms Application for formatting new hire employee data to integrate with Access Door systems. Streamlines HR onboarding by automating data formatting for physical access control, eliminating manual entry errors and reducing processing time. Supports CSV/TXT input formats with built-in validation and self-testing utilities.

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

**IT support / infrastructure** ผมเขียนเครื่องมือแก้ปัญหาที่ตัวเองเจอหน้างาน
ตั้งแต่สายแลนกับพอร์ต ไปจนถึงงานประจำที่คนลืมทำ

ทุกตัวข้างล่างนี้เริ่มจากของที่พังจริงแล้วต้องแก้ ไม่ใช่โจทย์ฝึกหัด
ส่วนใหญ่กดเข้าไปลองเล่นได้เลย

---

### สายและพอร์ต

**[serial-loopback](https://github.com/Olay097056/serial-loopback)** · [▶ เดินดูหน้าตา](https://olay097056.github.io/serial-loopback/)

ไล่ทดสอบพอร์ต COM ครบ 11 baud rate ผ่าน loopback plug แล้วบอกว่าพอร์ตนั้นใช้ได้จริง
ที่ความเร็วไหนบ้าง

เขียนไว้สองเวอร์ชัน Python สำหรับเครื่องสมัยใหม่ กับ .NET 3.5 ไฟล์เดียว 40 KB
สำหรับเครื่องคุมอุปกรณ์ที่ยังรัน Windows XP ลงอะไรเพิ่มไม่ได้ ก๊อปไปวาง รัน แล้วลบทิ้ง

### เครือข่าย

**switch-wr-tool** · [▶ demo สาธารณะ](https://olay097056.github.io/switch-wr-demo/) · *โค้ดปิด งานบริษัท ยินดีพาดูเป็นรายคน*

รัน `write memory` ให้สวิตช์ Cisco 74 ตัวทุกคืน สำรอง config พร้อมหน้าเทียบความต่าง
ค้นว่า MAC อยู่พอร์ตไหนโดยตาม CDP กับ port-channel ไปจนถึงพอร์ต access จริง
และวาด topology จาก CDP ทำด้วย Flask + React 19 ในคอนเทนเนอร์เดียว

สถานะของ fleet คำนวณครั้งเดียวที่เดียว และชุดคีย์ของทุก endpoint ล็อกไว้ด้วยเทส
กฎนี้มาจากบั๊กจริงที่หน้าหลักแสดงค่าผิดไป 7 จาก 10 คีย์ เพราะโค้ดสามเส้นทาง
ต่างคนต่างนิยามคำว่า fleet กันเอง

**[printer-monitor](https://github.com/Olay097056/printer-monitor)** · [▶ demo สาธารณะ](https://olay097056.github.io/printer-monitor-demo/) · *โค้ดปิด งานบริษัท ยินดีพาดูเป็นรายคน*

ดึงค่าหมึกจากฝูงเครื่องพิมพ์ 20 ตัวผ่าน SNMP ทุกชั่วโมง โดยอ่านตาราง
marker-supplies ของ Printer-MIB มาตรฐาน ใช้ได้กับหมึกทุกยี่ห้อ พร้อมนับจำนวน
หน้าที่พิมพ์, กราฟแนวโน้มหมึกของแต่ละตลับ และทำนายวันที่หมึกจะหมดด้วย
linear regression ทุกตลับมีกราฟของตัวเอง แถบ "ต้องการความสนใจ" บอกตัวไหนจะ
หมดก่อน ทำด้วย Fastify + SQLite + หน้าเว็บ static ปกป้องด้วยรหัสผ่านเดียว

### อุปกรณ์ปลายทาง

**[txt-to-excel](https://github.com/Olay097056/txt-to-excel)** · [▶ ลองใช้](https://olay097056.github.io/txt-to-excel/)

อ่านไฟล์ export จากเครื่องรูดบัตร ETWIN แล้วบอกว่าเครื่องไหนกำลังมีปัญหา

ตรวจสองชั้น ชั้นแรกเป็นกฎตายตัวจับค่าที่เป็นไปไม่ได้ ชั้นที่สองดูความถี่รายเครื่อง
จับค่าที่ถูกต้องทุกอย่างแต่ผิดปกติสำหรับเครื่องนั้น เพราะเครื่องที่อ่านเลขเพี้ยน
จะไม่บอกใคร กว่าจะรู้ก็ตอนเวลาเข้างานของใครสักคนไม่ตรง

**[time-etwin](https://github.com/Olay097056/time-etwin)** · [▶ demo](https://olay097056.github.io/time-etwin/demo/)

อีกด้านของปัญหาเดียวกัน คนหน้างานเห็นว่าเครื่องเสีย แต่บอกไม่ถูกว่าเครื่องไหน
เลยทำแผนผังพื้นที่ปักหมุดเครื่องไว้ ให้แจ้งจากตรงที่ของมันตั้งอยู่
ไม่ต้องรู้ว่ามันชื่อรหัสอะไร แอปที่สร้างใหม่รวมการวิเคราะห์ log แบบ txt-to-excel
ไว้ในหน้าเดียว เลือกเครื่องจาก log แล้วไฮไลต์บนแผนผังให้ทันที

### งานประจำ

**[line-msg](https://github.com/Olay097056/line-msg)** · [▶ ลอง demo](https://olay097056.github.io/line-msg-demo/)

เตือนงาน routine ที่ไม่มีใครตั้งเตือน เพราะ "ก็ทำทุกวันอยู่แล้ว" จนถึงวันที่ไม่มีใครทำ
ระบบยิงเข้ากลุ่ม LINE ที่ทีมเปิดอยู่แล้ว แก้เวลาและข้อความได้จากหน้าเว็บ
พร้อมดูโควต้าที่เหลือ

แถว `sent` เขียนลงฐานข้อมูลก่อนเรียก API ให้ database constraint เป็นตัวกันส่งซ้ำ
ไม่ใช่หวังว่า cron จะไม่ยิงซ้อนกันเอง

### นอกเวลางาน

**[portfolio-tracker](https://github.com/Olay097056/portfolio-tracker)** · [▶ เปิดแอปจริง](https://portfolio-tracker-taupe-two.vercel.app)

เว็บบริหารพอร์ตหุ้น มีสแกนสัญญาณกับชั้น AI ที่เขียนบทวิเคราะห์ให้

คะแนนความมั่นใจตัวเดิมเอาไปวัดกับผลจริงแล้วพบว่าทำนายอะไรไม่ได้เลย ก็เลยทิ้ง
แล้วเปลี่ยนเป็น logistic regression ที่ fit กับผลในอดีต วางคู่กับบทวิเคราะห์จาก LLM
แทนที่จะปรับน้ำหนักไปเรื่อยจนตัวเลขดูดีขึ้น

**[thai-lottery-stats](https://github.com/Olay097056/thai-lottery-stats)** · [▶ รัน backtest](https://olay097056.github.io/thai-lottery-stats/demo/)

เอาสูตรหวยทุกสูตรไป backtest กับผลรางวัลจริง 780 งวด ใช้ holdout อย่างมีวินัย
และคิด Edge แบบหักเส้นฐานแล้ว

คำตอบคือส่วนใหญ่ไม่ชนะการสุ่ม และแอปก็รายงานตามนั้น ลองสลับช่วงทดสอบใน demo
แล้วดูว่าสูตรไหนรักษา Edge ไว้ได้ ส่วนใหญ่รักษาไม่ได้

---

Python · TypeScript · C# · Flask · FastAPI · React · Docker · Cisco / Netmiko

ทุก repo มี README ทั้งไทยและอังกฤษ

[กลับขึ้นบน ↑](#top)
