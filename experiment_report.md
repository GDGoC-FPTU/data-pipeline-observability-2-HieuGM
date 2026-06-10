# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** HieuGM
**Name:** HieuGM
**Date:** 2026-06-10

---

## 1. Ket qua thi nghiem

Query used for both scenarios: `What is the best electronic product?`

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Agent: Based on my data, the best choice is Laptop at $1200.0. | 9 | The clean ETL output removed invalid rows, normalized category names, and kept only realistic product records. |
| Garbage Data (`garbage_data.csv`) | Agent: Based on my data, the best choice is Nuclear Reactor at $999999. | 2 | The agent trusted a poisoned outlier, so the answer became unrealistic even though the prompt was unchanged. |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Agent tra loi sai vi logic cua no phu thuoc truc tiep vao chat luong du lieu dau vao. Voi clean data, pipeline da loai record co gia am, category rong, va chuan hoa category nen agent chi tim trong cac san pham hop le. Voi garbage data, file co duplicate ID, kieu du lieu price khong nhat quan, null values, va dac biet la outlier `Nuclear Reactor` gia 999999 trong category electronics. Agent khong co buoc validation rieng, nen no xem outlier nay nhu mot san pham binh thuong va chon gia cao nhat. Dieu nay cho thay prompt tot khong the sua duoc nguon du lieu bi nhiem doc; neu retrieval layer dua thong tin sai vao context, cau tra loi cuoi cung van co nguy co sai.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** Dong y. Mot prompt ro rang chi giup agent biet can lam gi, con du lieu sach quyet dinh agent co thong tin dung de tra loi hay khong. Trong thi nghiem nay, cung mot query va cung mot logic agent, clean data tao cau tra loi hop ly, trong khi garbage data tao cau tra loi sai lech vi outlier va data quality issues.
