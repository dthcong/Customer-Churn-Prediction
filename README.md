# Customer-Churn-Prediction

![image](https://github.com/dthcong/Customer-Churn-Prediction/assets/156085700/3cc1849e-75c7-4ed3-b100-18f5166240db)

## Overview

Các ngân hàng đều muốn giữ chân khách hàng của mình để duy trì hoạt động kinh doanh và ngân hàng Đa quốc gia ABC cũng muốn điều đó. 
Với vai trò một Data Analyst chúng ta sẽ xây dựng một mô hình dự đoán khách hàng tại Ngân hàng Đa quốc gia ABC sẽ rời bỏ hay tiếp tục sử dụng dịch vụ.
Mô hình này sẽ được team Strategy sử dụng để ước lượng số lượng khách hàng rời bỏ và lên các phương án cải thiện.
 
## Dataset

Link dataset: [Link](https://drive.google.com/file/d/1fFqLRizk_W9WCtRVKusQclwDU_5KaUg7/view?usp=drive_link)
Đây là dữ liệu khách hàng tại Ngân hàng Đa quốc gia ABC (giả định) với 10,000 records và 11 columns.

## Tool

- Google Colab, Pandas: thực hiện EDA, preprocessing.
- Matplotlib, Seaborn: tạo visual trực quan.
- ScikitLearn: feature scaling, xử lý imbalance, khởi tạo - triển khai - so sánh hiệu năng các model Classification.

## Code

File source code `ipynb` xây dựng mô hình [Link](https://github.com/dthcong/Customer-Churn-Prediction/blob/main/Customer_Churn_Prediction.ipynb). 

## Sample Visualization

1. Tỷ lệ KH ngừng sử dụng Dv:

   ![image](https://github.com/dthcong/Customer-Churn-Prediction/assets/156085700/1c1872c8-5ada-43b4-892a-0be469b64317)
   
2. So sánh mức độ liên quan của các feature khác lên Churn:

  ![image](https://github.com/dthcong/Customer-Churn-Prediction/assets/156085700/25c2502f-b905-41a9-b41c-0f7d6a786c1b)

3. So sánh hiệu năng các model với 2 tập feature khác nhau X (All feature) và x (3 feature ảnh hưởng nhất: `age`, `balance`, `active_member`):

   ![image](https://github.com/dthcong/Customer-Churn-Prediction/assets/156085700/7c11a377-18d2-4f04-8fec-451cd417a88b)

## Result

NHẬN XÉT

- Các model sử dụng tập x (3 Features) thường cho ra chỉ số Accuracy cao hơn so với khi sử dụng tập X (Full Feature) trừ 2 trường hợp Decision Tree và Random Forest.
- Các model sử dụng tập x đều cho ra 2 chỉ số F1_score và Recall thấp hơn nhiều so với khi sử dụng tập X.
- Các model dùng tập X cho ra Recall khá tốt (min = 0.69 với Decision Tree) và F1_score ở mức chấp nhận được (min = 0.47 với Logistic Regression).
- Các model dùng tập x cho ra Recall rất kém (max = 0.4 với Decision Tree) và F1_score cũng kém (max = 0.42 với Decision Tree).
- Max Accuracy = 0.83 với SVC (tập x), theo sau là 0.81 của Random Forest (tập X) và một số model khác như Logistic Regression (tập x).
- Max F1_score = 0.61 với Random Forest (tập X).
- Max Recall = 0.79 với SVC (tập X), theo sau là 0.74 của Random Forest (tập X) và một số model khác như KNN (tập X).
- Resampling giúp model hoạt động tốt hơn so với Feature Selection dựa vào Correlation. Tuy nhiên có thể vì correlation giữa 3 Feature age, balance và active_member với Target churn ban đầu khá thấp (< 0.3).

ĐỀ XUẤT

- Trong phạm vi đề bài thì model Random Forest hoạt động tốt nhất (F1_score cao nhất, Accuracy và Recall cao thứ nhì).
- Tuy nhiên trong điều kiện thực tế vẫn nên áp dụng 2 cách tiếp cận trên (Resampling vs Feature Selection) song song với xây dựng nhiều model để có cái nhìn tổng quát và toàn diện hơn so với việc chỉ áp dụng mỗi - Resampling và dùng model Random Forest.
- Đồng thời sau khi tìm ra model hoạt động khả quan nhất trong từng trường hợp cụ thể (Vd Random Forest như trong bài) có thể cân nhắc hiệu chỉnh và tối ưu hóa model đó (Vd sử dụng GridSearchCV tìm ra tham số tối ưu) để hoàn thiện hơn nữa trong điều kiện Tài chính - Nhân lực - Thời gian cho phép.
