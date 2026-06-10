[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=24113043&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student ID:** HieuGM  
**Name:** HieuGM

---

## Mo ta

Repo nay hoan thanh bai lab ETL va data observability. Pipeline doc du lieu tu `raw_data.json`, validate cac record khong hop le, transform du lieu san pham, them cot audit timestamp, va ghi ket qua ra `processed_data.csv`. Phan stress test so sanh agent khi dung clean data va garbage data de thay tac dong cua data quality len cau tra loi.

---

## Cach chay (How to Run)

### Prerequisites
```bash
pip install pandas pytest
```

### Chay ETL Pipeline
```bash
python solution.py
```

Output mong doi:
- Tao file `processed_data.csv`
- Giu lai 3 valid records
- Loai 2 invalid records
- Them `discounted_price = price * 0.9`
- Them cot `processed_at`

### Chay Agent Simulation (Stress Test)
```bash
python generate_garbage.py
python agent_simulation.py
```

### Chay autograder local
```bash
python -m pytest tests/test_autograder.py -v
```

---

## Cau truc thu muc

```
├── solution.py              # ETL pipeline script
├── raw_data.json            # Raw input data
├── processed_data.csv       # Clean ETL output
├── generate_garbage.py      # Tao garbage_data.csv cho stress test
├── garbage_data.csv         # Poisoned data sample
├── agent_simulation.py      # RAG-like agent simulation
├── experiment_report.md     # Bao cao thi nghiem
└── README.md                # File nay
```

---

## Ket qua

Pipeline da xu ly 5 raw records tu `raw_data.json`. Co 3 records hop le duoc ghi vao `processed_data.csv`: Laptop, Chair, va Monitor. Co 2 records bi loai: `Mystery Box` vi price am va `Phone` vi category rong. Trong stress test, clean data giup agent chon Laptop, con garbage data lam agent chon sai outlier Nuclear Reactor gia 999999.
