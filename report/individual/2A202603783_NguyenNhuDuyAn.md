# Báo cáo cá nhân — Day 01: Lọc tin nhắn rác bằng ML, DL, Embedding và LLM

> Đổi tên file này thành `MSSV_HoTen.md` của bạn, ví dụ `2A20260000_NguyenVanAn.md`, rồi điền từng mục. Xoá các dòng hướng dẫn in nghiêng khi xong.

- MSSV: 2A202603783
- Họ và tên: Nguyễn Như Duy An
- SEED (in ở ô đầu notebook): 761

## 1. Bằng chứng

| Tệp | Có? |
| --- | --- |
| [`day01_lab.ipynb`](day01_lab.ipynb) — notebook đã chạy, còn output | có |
| [`lab1_report.json`](lab1_report.json) — do ô "Báo cáo cuối" sinh ra | có |
| [`hand_calc.jpg`](hand_calc.jpg) — ảnh tính tay có các bước | có |

## 2. Kết quả chính

                                     f1  f1_SUB
1. BoW + LogReg (tự code)        0.898   0.857
2. BoW + MLP (deep learning)     0.949   0.889
3a. Encoder (MiniLM) + kNN       0.947   0.947
3b. Encoder (MiniLM) + LogReg    0.960   0.947
3c. Encoder (MiniLM) + MLP head  0.956   0.947
4a. LLM nhỏ zero-shot            0.927   0.927
4b. LLM lớn zero-shot            0.930   0.930
4c. LLM nhỏ few-shot             0.872   0.872

## 3. Dự đoán và thực tế

Few-shot LLM (Thí nghiệm 4.B): đoán F1 tăng khi bổ sung 4 ví dụ mẫu; thực tế F1 giảm mạnh từ 0.927 xuống 0.872; nguyên nhân do ví dụ dài làm mô hình bị thiên lệch và nghi ngờ quá mức, đoán nhầm tin ham thành spam.

Độ chính xác của BoW trên 50 case khó: đoán BoW đạt khoảng 70% accuracy; thực tế BoW và LogReg chỉ đạt 50% accuracy với F1 tụt xuống 0.324; nguyên nhân do BoW chỉ đọc từ khóa cứng, hoàn toàn bất lực trước kỹ thuật ngụy trang ký tự và nội dung lừa đảo viết theo ngữ điệu đời thường.

Độ trễ LLM so với chuẩn SLA: đoán LLM đáp ứng được ứng dụng thực tế; thực tế p95 của nhóm LLM đều vượt 2.480 ms, gấp gần 50 lần giới hạn SLA 50 ms; nguyên nhân do tắc nghẽn hàng đợi mạng và cơ chế sinh token tuần tự tốn nhiều thời gian.

## 4. Phân tích 50 case khó

Mô hình tụt nhiều nhất: BoW + LogReg tụt sâu nhất, F1 rơi từ 0.857 xuống 0.324. 
Nhóm gây sai sót nghiêm trọng nhất là Né từ khoá (đoán đúng 17%) và Spam giọng tự nhiên (đoán đúng 10%).

Case số 31 (Né từ khoá)
Case số 16 (Spam giọng tự nhiên) 

## 5. Thử thách cá nhân

*Đề theo SEED của bạn, cách làm, kết quả, giải thích.*

## 6. Phương án cho sản phẩm thật

*Với yêu cầu p95 < 50 ms/tin cho 10 triệu SMS/ngày: chọn phương án nào, dẫn số liệu nào, chấp nhận đánh đổi gì.*

## 7. AI log và điều đã học

*Mỗi lần dùng AI: hỏi gì, nhận gì, bạn sửa gì. Sau đó 2–3 câu: điều bạn hiểu ra hôm nay mà trước đó chưa hiểu.*
