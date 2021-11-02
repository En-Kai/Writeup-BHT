# Writeup-BHT
  Writeup code lưu đồ thuật toán
# Bài 1
  ![image](https://user-images.githubusercontent.com/91708234/139794976-c37a87fa-032f-41b9-b39a-709be6c7c387.png)
## Ý tưởng
  Tổng quát với dạng mũ n.
  
  Ta có 2 trường hợp của m là m chẵn và m lẽ. Nếu m chẵn thì có thể đưa về dạng (x^(n/2))^2. Còn m nếu lẽ thì tách thành mũ chẵn nhân mũ lẻ rồi làm phần mũ chẵn như đã trình bày.
  
  Làm như vậy cho đến khi nào số mũ còn lại là 1 -> kết thúc.
  
  Vậy phương pháp là như thế nào?
  
  Chia nguyên m cho 2 và ghi lại phần dư. Lấy phần nguyên tiếp tục chia đến khi còn lại 1 và kết thúc.
  
  Trở lại với bài mũ 11:
  
    ```bash
    
    1: 11
    
    2: 5 1
    
    3: 2 1
    
    4: 1 0
    
    ```
  Biểu diễn x^11 = x^5 * x^5 * x = x^2 * x^2 * x * x^2 * x^2 * x * x.
## Code
  Sao chép x vào tmp đại diện cho phần dư của phép chia. Sau đó làm như bước ý tưởng.
  
  ```cpp
  // Cau1 : de bai : tinh x^11 voi so luong phep nhan toi thieu
#include<iostream>
using namespace std;

int main() {
	int n = 11;
	long long x;
	cin >> x;
	int tmp = x;
	x *= x;
	x *= x * tmp;
	x *= x * tmp;
	cout << x;
	return 0;
}
```
