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

**[switch-wr-tool](https://olay097056.github.io/switch-wr-demo/)** · *source closed — employer work, happy to walk through it*

Nightly `write memory` across a 74-switch Cisco fleet, config backup with diff,
MAC-to-port lookup that follows CDP and port-channels to the real access port,
and a CDP topology graph. Flask + React 19 in one container. Fleet state is
computed once in one place and every endpoint's key set is pinned by a test —
after a bug where the main view was wrong on 7 of 10 fields because three code
paths each defined "the fleet" their own way.

**[printer-monitor](https://olay097056.github.io/printer-monitor-demo/)** · *source closed — employer work, happy to walk through it*

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

**[time-etwin](https://olay097056.github.io/time-etwin-demo/)** · *source closed — employer work, happy to walk through it*

The other half of the same problem: floor staff can see a reader is broken but
have no way to say which one. A floor plan with the readers pinned on it, so
they report from where the thing is rather than what it is called. The rebuilt
app also carries the txt-to-excel analysis in the same page — flag a machine
from the log and it lights up on the map.

### The control room

**bit-vms** · [▶ see the interface](https://olay097056.github.io/bit-vms-demo/) · *source closed — employer work, happy to walk through it*

A web CCTV VMS that replaces Hikvision's iVMS-4200 for a 124-camera /
7-recorder fleet. Hover a live tile, choose "3 minutes back", and the playback
page is already rolling — because the segment pipeline starts serving while
ffmpeg is still capturing, after measuring that whole-file-then-serve could
never beat a recorder pulling at ~1× realtime. Signal probing checks one
sub-stream per channel with 250 ms stagger, exponential backoff, and anti-herd
jitter; a dead camera goes amber within two rounds without making a recorder
stumble. Wall tour auto-switching, a health page readable from across the room
(with a clock-drift badge), and admin/operator/viewer roles with per-camera
grants — every action audited by name.

### The routine

**[line-msg](https://github.com/Olay097056/line-msg)** · [▶ demo](https://line-msg.pages.dev/demo)

Reminders for recurring work nobody schedules, because "we do that every day
anyway" — right up until the day nobody does. Pushes into the LINE group the
team already watches, with dashboard-editable schedules and live quota tracking.
The `sent` row is written to the database *before* the API call, so a uniqueness
constraint prevents duplicate messages rather than the hope that the scheduler
never fires twice.

**[NewHireFormatter](https://olay097056.github.io/newhireformatter-demo/)** · *source closed — employer work, happy to walk through it*

A Windows Forms tool that turns a new-hire spreadsheet into the exact
caret-separated line format the door-access system expects
(`Name^EN^^CostCenter^StartDate^EndDate^Doors`), with a door preset per
department and inline validation before the file can be saved — the format
HR used to build by hand, one column at a time.

### Off the clock

**[portfolio-tracker](https://github.com/Olay097056/portfolio-tracker)** · [▶ live app](https://portfolio-tracker-taupe-two.vercel.app)

Stock portfolio tracker with signal scanners and an AI analyst layer. Its
confidence score was measured against real outcomes, found to predict nothing,
and thrown out — replaced by a fitted logistic regression and an LLM read shown
side by side, rather than re-weighted until it looked better.

**[thai-lottery-stats](https://github.com/Olay097056/thai-lottery-stats)** · [▶ run the backtest](https://olay097056.github.io/thai-lottery-stats/demo/)
**[ttm-bot](https://github.com/Olay097056/ttm-bot)** · *ไม่มี demo — รันในเครื่องเท่านั้น*

แย่งที่นั่งจากคิว thaiticketmajor.com ก่อนที่หน้าเว็บจะนิ่ง — พยายามยัดบัตรใส่ตะกร้า
ก่อนที่คนโทรศัพท์เข้ามาคนต่อไปจะหาแผนผังโซนเจอ เลือกที่จะรันบนเครื่อง Windows
เครื่องนี้ด้วย IP บ้านโดยเจตนา — IP ของ Cloudflare โดน Akamai บล็อก sensor wall ที่
thaiticketmajor.com ตั้งไว้กันบอท บอทเลยต้องรันจากบ้าน Node 24, node:sqlite, session
เดียวของ Playwright ผ่านโปรไฟล์ Chrome ที่ mint ใหม่ แล้ว dashboard ก็ refresh
สถานะของตัวเองทุก 2 วินาทีโดยไม่ต้อง paste token ใส่การ์ด sign-in

ที่มันไม่ทำ: จ่ายเงิน — บอทจะหยุดที่หน้าเลือกช่องทางชำระเงิน ให้ผมเลือกเอง
ไม่มีสคริปต์ไหนแตะบัตรเครดิตจริง

**[Live demo](https://olay097056.github.io/ttm-bot-demo/)** — หน้า static อธิบาย flow ของบอท
**[ttm-bot](https://github.com/Olay097056/ttm-bot)** · *no live demo — runs locally only*

Heads off the thaiticketmajor.com ticket queue before the page even settles.
Tries to put a seat in your cart before the next human caller can find the
zone map. The hosting choice is deliberate — Cloudflare's IP blocks Akamai's
sensor wall that thaiticketmajor.com puts up for bot traffic, so the bot has
to run from this Windows machine on my home IP. Node 24, node:sqlite, a
single Playwright session against a freshly minted Chrome profile, and a
dashboard that refreshes its own state every 2 seconds without me pasting a
token into a sign-in card.

What it does not do: pay. The cart lands on the payment-method screen so I
can pick the channel myself — never letting a script touch a real credit card.

**[Live demo](https://olay097056.github.io/ttm-bot-demo/)** — static page describing the bot's flow, no live checkout

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

**[switch-wr-tool](https://olay097056.github.io/switch-wr-demo/)** · *โค้ดปิด งานบริษัท ยินดีพาดูเป็นรายคน*

รัน `write memory` ให้สวิตช์ Cisco 74 ตัวทุกคืน สำรอง config พร้อมหน้าเทียบความต่าง
ค้นว่า MAC อยู่พอร์ตไหนโดยตาม CDP กับ port-channel ไปจนถึงพอร์ต access จริง
และวาด topology จาก CDP ทำด้วย Flask + React 19 ในคอนเทนเนอร์เดียว

สถานะของ fleet คำนวณครั้งเดียวที่เดียว และชุดคีย์ของทุก endpoint ล็อกไว้ด้วยเทส
กฎนี้มาจากบั๊กจริงที่หน้าหลักแสดงค่าผิดไป 7 จาก 10 คีย์ เพราะโค้ดสามเส้นทาง
ต่างคนต่างนิยามคำว่า fleet กันเอง

**[printer-monitor](https://olay097056.github.io/printer-monitor-demo/)** · *โค้ดปิด งานบริษัท ยินดีพาดูเป็นรายคน*

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

**[time-etwin](https://olay097056.github.io/time-etwin-demo/)** · *โค้ดปิด งานบริษัท ยินดีพาดูเป็นรายคน*

อีกด้านของปัญหาเดียวกัน คนหน้างานเห็นว่าเครื่องเสีย แต่บอกไม่ถูกว่าเครื่องไหน
เลยทำแผนผังพื้นที่ปักหมุดเครื่องไว้ ให้แจ้งจากตรงที่ของมันตั้งอยู่
ไม่ต้องรู้ว่ามันชื่อรหัสอะไร แอปที่สร้างใหม่รวมการวิเคราะห์ log แบบ txt-to-excel
ไว้ในหน้าเดียว เลือกเครื่องจาก log แล้วไฮไลต์บนแผนผังให้ทันที

### ห้องคุมกล้อง

**bit-vms** · [▶ ดูหน้าตาโปรแกรม](https://olay097056.github.io/bit-vms-demo/) · *โค้ดปิด งานบริษัท ยินดีพาดูเป็นรายคน*

Web VMS ที่เขียนแทน iVMS-4200 สำหรับกล้อง 124 ช่อง / 7 เครื่องบันทึก — ชี้ tile
ดูสดเลือก "ถอยหลัง 3 นาที" หน้าย้อนหลังเล่นต่อทันที เพราะ pipeline เสิร์ฟไฟล์
ระหว่างที่ ffmpeg ยังดึงอยู่ (จากการวัดว่าเครื่องบันทึกป้อนข้อมูล ~1× realtime
ถ้ารอไฟล์จบก่อนคือไม่มี timeout ไหนพอ) probe สัญญาณเช็กทีละช่องบนสตรีมย่อย
ทยอย 250ms พร้อม backoff กันทั้งฝูงตื่นพร้อมกัน กล้องหลุดขึ้นไฟอำพันภายใน 2 รอบ
โดยเครื่องบันทึกไม่สะดุด · วนกล้องอัตโนมัติ, หน้าสุขภาพอ่านออกจากฝั่งห้อง
(มีเตือนนาฬิกาเครื่องบันทึกเพี้ยน), และสิทธิ์ admin/operator/viewer รายกล้อง
ที่ audit ทุก action ด้วยชื่อผู้ใช้

### งานประจำ

**[line-msg](https://github.com/Olay097056/line-msg)** · [▶ ลอง demo](https://line-msg.pages.dev/demo)

เตือนงาน routine ที่ไม่มีใครตั้งเตือน เพราะ "ก็ทำทุกวันอยู่แล้ว" จนถึงวันที่ไม่มีใครทำ
ระบบยิงเข้ากลุ่ม LINE ที่ทีมเปิดอยู่แล้ว แก้เวลาและข้อความได้จากหน้าเว็บ
พร้อมดูโควต้าที่เหลือ

แถว `sent` เขียนลงฐานข้อมูลก่อนเรียก API ให้ database constraint เป็นตัวกันส่งซ้ำ
ไม่ใช่หวังว่า cron จะไม่ยิงซ้อนกันเอง

**[NewHireFormatter](https://olay097056.github.io/newhireformatter-demo/)** · *โค้ดปิด งานบริษัท ยินดีพาดูเป็นรายคน*

โปรแกรม Windows Forms แปลงรายชื่อพนักงานใหม่ให้เป็นบรรทัดตามรูปแบบที่ระบบ
ควบคุมประตูต้องการเป๊ะๆ (`Name^EN^^CostCenter^StartDate^EndDate^Doors`
คั่นด้วยเครื่องหมาย ^) มี preset ประตูตามแผนกให้เลือก และตรวจความถูกต้อง
ก่อนบันทึกไฟล์ได้เลย จากเดิมที่ HR ต้องมาเรียงคอลัมน์เองทีละแถว

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
