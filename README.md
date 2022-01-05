# Mercari Price Suggestion Challenge

![Mercari Price Suggestion Challenge](images/mercari.png)

### Tổng quan bài toán

Mercari là một hệ thống mua bán trực tuyến, là nơi mọi người có thể thoải mái trao đổi buôn bán. Hệ thống muốn đề xuất giá cho người bán, tuy nhiên đây là một nhiệm vụ khó khăn bởi sự đa dạng của sản phẩm trên hệ thống của Mercari.

Để biết giá trị của mọi sản phẩm thì rất khó khăn. Một chi tiết nhỏ trên sản phẩm cũng có thể khiến cho giá của sản phẩm thay đổi. Như ví dụ ở dưới, với 2 mô tả khác nhau, một trong hai sweater có giá là 335$, còn áo còn lại có giá trị 9.99$.

![2_side_prices](images/2side.png)


### Phân tích bài toán

- Nhiệm vụ của bài toán là xây dựng 1 thuật toán gợi ý giá cho sản phẩm cho 1 ứng dụng mua sắm. Được biết các thông tin về Tên của sản phẩm - phần thông tin người dùng nhập, Loại sản phẩm, Nhãn sản phẩm, Loại sản phẩm, Thông tin chuyển phát.
- Phần huấn luyện và suy luận của mô hình được thực hiện trong môi trường nhất định. Mô hình phải hoàn thành trong 60 phút, và hệ thống 4 core - 16GB RAM - 1GB bộ nhớ cho phép.

### Đầu vào - Input

- Vì bài toán Mercari trên Kaggle đã kết thúc nên tập Dataset để sử dụng cho bài toán này là **train.tsv** và **test_stg2.tsv**
- Dataset chứa thông tin của danh sách các sản phẩm. Có 8 trường thông tin trong mỗi file:
    - train_id / test_id: id của sản phẩm trong tệp train hoặc test
    - name: Tên của sản phẩm
    - item_condition_id: Trạng thái của sản phẩm được cung cấp bởi người bán
    - category_name: Danh mục của sản phẩm
    - brand_name: Nhãn hiệu của sản phẩm
    - price: Giá bán của sản phẩm. Đây là mục tiêu ta cần phải dự đoán. Trường này chỉ có trong tệp **train.tsv** không có trong tệp **test_stg2.tsv**
    - shipping: Có giá trị là 1 nếu phí vận chuyển được trả bởi người bán, 0 nếu được trả bởi người mua
    - item_description: Mô tả của sản phẩm

### Đầu ra - Output

- Giá tiền dự đoán của sản phẩm tương ứng trên tập dữ liệu test.

### Hàm đánh giá mô hình

- Sử dụng hàm RMSLE - Root Mean Squared Logarithmic Error

<br />

![RMSLE](https://latex.codecogs.com/png.image?\dpi{150}&space;\epsilon&space;=&space;\sqrt&space;{\frac&space;1&space;n&space;\sum&space;^n_{i=1}(log(p_i&space;&plus;1)-log(a_i&space;&plus;&space;1))^2&space;})

<br />

#### Link Kaggle: https://www.kaggle.com/c/mercari-price-suggestion-challenges