## 1) `1_Project_Info/`
**ใช้ทำอะไร:** เก็บข้อมูลภาพรวมโครงการ ขอบเขต วัตถุประสงค์ บทบาททีม รายละเอียดรายวิชา/อาจารย์

**ควรมีไฟล์อะไรบ้าง:**
- `Course_Overview.txt` — รายละเอียดรายวิชา (SCI19 3431), Learning outcomes, วิธีประเมิน
- `Project_Charter.docx` — วัตถุประสงค์ ขอบเขต (In/Out), ข้อกำหนด, ความเสี่ยง, Milestones
- `Stakeholders_and_Roles.xlsx` — สมาชิกทีม บทบาท ช่องทางติดต่อ
- `Meeting_Notes_YYYY-MM-DD.md` — บันทึกการประชุม/ข้อสรุป
- `Timeline_Gantt.*` — แผนงานแบบ Gantt (เช่น `.mpp`, `.xlsx`, `.png`)

**มาตรฐานชื่อไฟล์:** `Meeting_Notes_2025-10-24.md` (ใช้รูปแบบวันที่ `YYYY-MM-DD`)

---

## 2) `2_Data/`
หลักคิด: คุมเวอร์ชันข้อมูลและความเป็นส่วนตัวอย่างเคร่งครัด แยก “ข้อมูลดิบ” ออกจาก “ข้อมูลผ่านการประมวลผล” เพื่อความสามารถในการทำซ้ำ (reproducibility)

### 2.1 `Raw_Data/`
**ใช้ทำอะไร:** เก็บข้อมูลดิบ (ต้นฉบับ) *ห้ามแก้ทับ*

**ตัวอย่างไฟล์:**
- ภาพสแกน/ภาพถ่ายเอกสารราชการ: `scan_XXXX_YYYYMMDD_page01.png`
- PDF ต้นฉบับ: `doc_ministry_XXXX.pdf`
- เมทาดาทา: `raw_manifest.csv` (ที่มา, วันที่เก็บ, สิทธิ์การใช้)

**คำเตือน:** ถ้ามีข้อมูลอ่อนไหว/PII ให้ทำการปกปิด (mask) ก่อนแชร์ลง repo สาธารณะ

### 2.2 `Processed_Data/`
**ใช้ทำอะไร:** ข้อมูลที่ผ่านการทำ preprocessing แล้ว เช่น deskew, denoise, binarize, crop, layout detection

**ตัวอย่างไฟล์:**
- `preprocessed/xxxx_page01_binarized.png`
- `ocr_text/json/xxxx_page01_ocr.json` (ผล OCR พร้อม bounding boxes)
- `cleaned.csv` (ข้อมูลเชิงตารางที่พร้อมใช้งานโมเดล/visualization)

**ควรแนบสคริปต์/โน้ตบุ๊กที่ใช้ preprocess ใน `3_Code/` เสมอ**

### 2.3 `Visualization_Data/`
**ใช้ทำอะไร:** ชุดข้อมูลที่จัดรูปเพื่อทำกราฟ/แดชบอร์ดโดยเฉพาะ (tidy data)

**ตัวอย่างไฟล์:**  
- `viz_summary.csv`, `agg_by_month.csv`  
- `metrics_for_plot.parquet`

**ข้อดี:** แยกชัดว่าชุดนี้ “พร้อมวาดกราฟ” ลดความสับสนเวลา iterate งานนำเสนอ

---

## 3) `3_Code/`
### 3.1 `Notebooks/`
**ใช้ทำอะไร:** ทดลอง/อธิบายขั้นตอนด้วย Jupyter Notebook

**ตัวอย่างไฟล์/ข้อแนะนำ:**
- `01_preprocess.ipynb` — ขั้นตอน preprocessing
- `02_ocr_baseline.ipynb` — เรียกใช้ OCR baseline (Tesseract/PaddleOCR)
- `03_postprocess_normalize.ipynb` — แปลงเลขไทย→อารบิก, พ.ศ.→ค.ศ., regex ตรวจรูปแบบ
- `04_evaluation.ipynb` — คำนวณ CER/WER, Field Accuracy
- ใส่ `requirements.txt` หรือ `environment.yml` ในรากโปรเจคเพื่อรันซ้ำได้

### 3.2 `Scripts/`
**ใช้ทำอะไร:** โค้ด production/CLI ที่แยกเป็นโมดูล

**ตัวอย่างไฟล์:**
- `preprocess.py` — deskew/denoise/threshold/CLAHE
- `ocr_infer.py` — เรียก OCR engine + export JSON/TSV
- `postprocess.py` — normalize ตัวเลขไทย/วันที่ + regex validation
- `extract_fields.py` — ดึง key-value จากเอกสาร
- `evaluate.py` — คำนวณตัวชี้วัด (CER/WER/EM/F1)

**แนวปฏิบัติ:** สร้างโฟลเดอร์ `cli/` สำหรับสคริปต์ที่เรียกผ่านคำสั่ง และโฟลเดอร์ `src/` สำหรับไลบรารี

---

## 4) `4_Models/`
### 4.1 `Trained_Models/`
**ใช้ทำอะไร:** เก็บไฟล์น้ำหนักโมเดลที่เทรนแล้ว (เช่น โมเดล OCR/fine-tuned, layout model)

**ข้อแนะนำ:**
- ไม่ควรเก็บไฟล์ใหญ่ลง Git โดยตรง — ใช้ Git LFS หรือเก็บลิงก์ดาวน์โหลด + checksum
- แนบ `model_card.md` อธิบายเวอร์ชัน, ชุดข้อมูล, เมตริก, วิธีใช้งาน

### 4.2 `Experiments/`
**ใช้ทำอะไร:** ผลการทดลอง (config, logs, metrics, charts)

**มาตรฐานชื่อโฟลเดอร์:** `YYYYMMDD_short-name/` เช่น `20251024_tesseract-tha-v1/`

**ภายในควรมี:**
- `config.yaml` — พารามิเตอร์ที่ใช้
- `metrics.json` — CER/WER/Field Accuracy
- `samples/` — ตัวอย่างทำนายถูก/ผิด
- `notes.md` — สรุปสิ่งที่พบ/บทสรุปการทดลอง

---

## 5) `5_Reports/`
### 5.1 `Drafts/`
**ใช้ทำอะไร:** รายงานฉบับร่าง แยกตามบท/เวอร์ชัน

**ตัวอย่างไฟล์:** `chapter1_intro_v2.docx`, `literature_review_notes.md`

### 5.2 `Final/`
**ใช้ทำอะไร:** รายงานฉบับสมบูรณ์ (PDF/Docx) พร้อมส่ง

**ข้อแนะนำ:** ใส่วันที่/เวอร์ชันในชื่อไฟล์ เช่น `final_report_2025-10-24.pdf`

---

## 6) `6_Presentations/`
### 6.1 `Slides/`
**ใช้ทำอะไร:** สไลด์นำเสนอ (progress/midterm/final) และภาพประกอบ

### 6.2 `Demo/`
**ใช้ทำอะไร:** วิดีโอสาธิต/สคริปต์รันเดโม, ไฟล์สำหรับ live demo

---

## 7) `7_Submission/`
**ใช้ทำอะไร:** ไฟล์ที่ “ต้องส่งจริง” ตามที่อาจารย์กำหนด รวมไว้เป็นที่เดียว

**ตัวอย่าง:**  
- `report.pdf`, `code.zip`, `dataset_sample.zip`, `demo_video.mp4`  
- `README_for_teacher.txt` — วิธีรันโค้ด/สภาพแวดล้อมที่ต้องการ

---

## มาตรฐานการตั้งชื่อไฟล์ (Naming Conventions)
- ใช้ตัวพิมพ์เล็ก + `_` หรือ `-` คั่นคำ: `ocr_results_2025-10-24.csv`
- วันที่ใช้รูปแบบ `YYYY-MM-DD` หรือ `YYYYMMDD`
- เวอร์ชัน `v1`, `v2` เมื่อปรับเอกสาร/รายงาน
- ไม่ใช้ช่องว่าง/อักขระพิเศษในชื่อไฟล์

---

## นโยบายข้อมูล (Data Policy & Privacy)
- หลีกเลี่ยงการเก็บ PII/ข้อมูลอ่อนไหวใน repo สาธารณะ
- ถ้าต้องแชร์: ทำการ anonymize/mask ก่อน และแนบ `DATA_LICENSE.txt`
- เก็บ `data_manifest.csv` ระบุแหล่งที่มา, สิทธิ์การใช้, วันที่รวบรวม

---

## การทำซ้ำได้ (Reproducibility)
- ระบุสภาพแวดล้อมใน `requirements.txt` หรือ `environment.yml`
- ใช้ seed แบบกำหนดเองใน Notebook/Scripts
- เก็บ config ของการทดลองทุกครั้งใน `4_Models/Experiments/`

---

## เวิร์กโฟลว์ทีม (Collaboration)
- ใช้กิ่ง (branch) ต่อฟีเจอร์: `feature/ocr-postprocess`, `exp/paddleocr-v2`
- เปิด Pull Request พร้อมคำอธิบาย/ผลทดสอบ
- หลีกเลี่ยง commit ไฟล์ใหญ่/ข้อมูลดิบลง Git (ใช้ LFS/Cloud แทน)

---

## ไฟล์ที่ควรมีที่รากโปรเจค (Root)
- `README.md` (ไฟล์นี้)
- `requirements.txt` หรือ `environment.yml`
- `.gitignore` (เช่น ignore: `2_Data/*`, `4_Models/Trained_Models/*`, `*.ipynb_checkpoints/`, `__pycache__/`)

ตัวอย่าง `.gitignore` สั้น ๆ:
```
2_Data/*
!2_Data/Visualization_Data/*
4_Models/Trained_Models/*
*.ipynb_checkpoints
__pycache__/
.env
.DS_Store
```

---

## รายการตรวจสอบก่อนส่ง (Submission Checklist)
- [ ] ทำความสะอาด/แอนอนิไมซ์ข้อมูล (ถ้ามี PII)
- [ ] แนบวิธีรัน + requirements ครบ
- [ ] แนบผลเมตริกประเมิน (CER/WER/Field Accuracy)
- [ ] แนบสไลด์/วิดีโอเดโม (ถ้ากำหนด)
- [ ] ใส่ไฟล์ใน `7_Submission/` ครบถ้วน
