# Day 10 Lab: Data Pipeline & Data Observability

**Student ID:** 2A202600237
**Student Email:** 26ai.thachnv@vinuni.edu.vn
**Name:** Nguyễn Văn Thạch

## Mo ta

Lab xây dựng một ETL pipeline đơn giản để đọc dữ liệu Json, lọc các record lỗi, chuẩn hóa category, tinh gia giam 10%, va lưu kết quả ra file CSV. Ngoài phần ETL, bài làm còn có stress test để so sánh hành vi của agent khi dùng dữ liệu sạch và dữ liệu rác.


## Cach chay

### Cai dat
```bash
pip install pandas pytest
```

### Chay ETL Pipeline
```bash
python solution.py
```

Lenh nay tao ra file `processed_data.csv`.

### Chay Stress Test
```bash
python generate_garbage.py
python agent_simulation.py
```

## Cau truc thu muc

```text
├── solution.py
├── processed_data.csv
├── experiment_report.md
├── raw_data.json
├── generate_garbage.py
└── README.md
```

## Ket qua

Pipeline đã xử lý 5 bản ghi đầu vào, giữ lại 3 bản ghi hợp lệ và loại bỏ 2 bản ghi không hợp lệ. Output có đầy đủ các cột `discounted_price` và `processed_at`. Agent simulation cho thấy dữ liệu sạch trả về sản phẩm hợp lý, trong khi dữ liệu rác làm mờ hiêu quả của câu trả lời và để agent chọn nhầm mẫu thông tin.
