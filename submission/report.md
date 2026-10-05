# Báo cáo Lab Ngày 18

Link notebook đã chạy:
https://github.com/hongneuk65/Track04-Day18-2D-perception-detection-segmentation-keypoints/blob/main/lab_2d_perception_student.ipynb

## Kết quả thực nghiệm

- Môi trường: Tesla T4, CUDA; Ultralytics 8.4.171.
- Fine-tune tiger-pose: 40 epoch, imgsz 640; 210 ảnh train, 53 ảnh val.
- Box mAP50–95: 0.9303; Pose mAP50: 0.995; Pose mAP50–95: 0.4573.
- OKS trung bình: 0.745; không bỏ sót hổ trên 53 ảnh val; 4/53 ảnh nghi đảo trái/phải.
- Auto-label: 5 đối tượng; IoU polygon dựng lại so với mask SAM từ 0.967 đến 0.983.
- Các hàm bắt buộc và FLIP_IDX đều qua bộ kiểm tra, không dùng phao.
- Bonus đã làm: average_precision và đồ thị PR (1D). Chưa làm 4C hoặc bài tập về nhà bonus.

## Phân tích lỗi

Frame_54.jpg và Frame_51.jpg cho thấy dự đoán bàn chân trước lệch về giữa hai vị trí nhãn; right_front_paw có sai số chuẩn hóa lớn nhất, khoảng 0.26. Hướng cải thiện: bổ sung nhiều pha bước chân, rà soát nhãn và thử tăng độ phân giải.

Frame_31.jpg và Frame_67.jpg cho thấy khó định vị chân sau khi chồng lấp. Hướng cải thiện: thêm góc nhìn và mức che khuất, kiểm tra nhãn trái/phải nhất quán; thống kê nghi đảo nhãn cần được kiểm tra từng ảnh.

## Ghi chú kiểm tra

Notebook giữ output của lần chạy tuần tự đã lưu và checklist final_report đạt các mục bắt buộc, 12/12 câu trả lời. Q2 được hiệu chỉnh sau lần chạy để khớp bảng latency hiện tại; phần answers.Q2 trong ket_qua.json được đồng bộ, không đổi các số đo hoặc trạng thái kiểm tra. Chưa chạy lại GPU sau hiệu chỉnh này; trước khi nộp, thực hiện Restart session and run all và xuất lại submission để xác nhận tái lập. Nếu số latency thay đổi, cập nhật Q2 theo bảng mới. Giữ report.md khi xuất lại submission.
