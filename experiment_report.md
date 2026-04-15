# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** 2A202600237
**Name:** Nguyễn Văn Thạch
**Date:** 15/04/2026

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Agent: Based on my data, the best choice is Laptop at $1200. | 9 | Dữ liệu đã được làm sạch nên agent trả lời ổn định và có cơ sở độc lập rõ ràng  |
| Garbage Data (`garbage_data.csv`) | Agent: Based on my data, the best choice is Nuclear Reactor at $999999. | 2 | Dữ liệu rác có outlier và bản ghi không hợp lệ khiến agent chọn sai. |

---

## 2. Phan tich & nhan xet

### Tại sao Agent trả lời sai khi dùng Garbage Data?

Dữ liệu rải rác làm mờ quan hệ giữa câu hỏi và kết quả trả lời vì nó chứa nhiều vấn đề chất lượng cơ bản. Trong file garbage, có duplicate ID, kiểu dữ liệu sai ở cột price, giá trị outlier cực lớn và các trường null. Khi agent tìm sản phẩm electronic có giá cao nhất, nó không hiểu được rằng "Nuclear Reactor" là một bản ghi không hợp lệ về mặt nghiệp vụ, nên vẫn xem đó là ứng viên tốt nhất. Điều này cho thấy mô hình trả lời đang phụ thuộc mạnh vào input data, nên chỉ cần dữ liệu ban đầu bị nhiễm là dự án phải trả giá bằng kết quả sai.

Ngoài ra, dữ liệu rác không có bước validation và chuẩn hóa trước khi nạp vào agent. Nếu có ETL làm sạch, giảm outlier, loại bỏ null và chuẩn hóa category, agent sẽ có cơ sở suy luận ổn định hơn nhiều. Vì vậy, chất lượng dữ liệu có tác động trực tiếp đến độ tin cậy của kết quả, đôi khi còn mạnh hơn cả cách viết prompt.

---

## 3. Ket luan

***Quality Data > Quality Prompt?** Đồng ý. Một prompt tốt vẫn có thể cho kết quả sai nếu dữ liệu nền bị lỗi, bổ sung giá trị sai hoặc không nhất quán. Trong bài này, dữ liệu sạch giúp agent trả lời đúng hơn rõ rệt, còn dữ liệu rác với nội dung nhiễu nhiễm đã kéo kết quả lệch hướng. Do đó, chất lượng dữ liệu là điều kiện tiên quyết để có kết quả tin cậy.