# Writeup-BHT
  Writeup code lưu đồ thuật toán
# Câu 1
  ![image](https://user-images.githubusercontent.com/91708234/139794976-c37a87fa-032f-41b9-b39a-709be6c7c387.png)
## Ý tưởng
  Tổng quát với dạng mũ n.
  
  Ta có 2 trường hợp của m là m chẵn và m lẽ. Nếu m chẵn thì có thể đưa 
  về dạng (x^(n/2))^2. Còn m nếu lẽ thì tách thành mũ chẵn nhân mũ lẻ rồi làm phần mũ chẵn như đã trình bày.
  
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
# Câu 2
![image](https://user-images.githubusercontent.com/91708234/139796856-1b9b1080-34ac-4cd4-9712-fb652fff24ec.png)

## Ý tưởng
	Muốn tính tổng các chữ số của một số thì ta phải có các chữ số đó đã. Vậy ta nghĩ đến việc tách số. 
	
	Làm sao để tách số? Khi chia dư một số cho 10 thì sẽ lấy được chữ số cuối của số đó. 
	
	Tiếp theo tiến hành loại bỏ chữ số cuối cùng bằng việc chia nguyên với 10. Vậy là ta đã bóc được số cuối cùng ra.
	
	Việc còn lại là thực hiện lặp và cộng những chữ số này lại là xong.
## Code
```cpp
// Cau 2 : tinh tong cac chu so cua so nguyen duong n
#include<iostream>
using namespace std;

int main() {
	int n;
	int ket_qua = 0;
	cin >> n;
	while (n > 0) {
		ket_qua += n % 10;
		n /= 10;
	}
	cout << ket_qua;
}
```
# Câu 3
![image](https://user-images.githubusercontent.com/91708234/139797518-1a58ad65-3c64-4dc2-86e3-f352be0ef82a.png)
## Ý tưởng
	Dễ thấy tử số của số hạng sau bằng x lần tử số của số hạng trước 
	
	và mẫu số của số hạng sau bằng mẫu số của số hạng trước cộng thêm n ( n là số mũ của tử số )
	
	Vậy ta chỉ cần lần lượt tăng tử số và mẫu số lên để có được số hạng và cộng các số hạng lại với nhau để được kết quả.
	
## Code
```cpp
#include<iostream>
using namespace std;

int main() {
	int n, x;
	cin >> n >> x;
	int tu = x;
	int mau = 1;
	double ket_qua = 0;
	for (int i = 2; i <= n+1; i++) {
		ket_qua += tu*1.0 / mau;
		tu *= x;
		mau += i;
	}
	cout << ket_qua;
	return 0;
}
```

# Câu 4
![image](https://user-images.githubusercontent.com/91708234/139797977-08c70e03-c793-4202-b282-9ed3be07ed8b.png)

## Ý tưởng
	Dễ thấy số hạng sau bằng số hạng trước nhân thêm -x*x. 
	
	Vậy chỉ cần tạo biến tạm tmp = -x*x  và sử dụng vòng lặp để tính tổng.
	
## Code
```cpp
#include<iostream>
using namespace std;

int main() {
	int x, n;
	cin >> n >> x;
	long tmp = -x * x;
	long long ket_qua = 0;
	for (int i = 0; i < n; i++) {
		ket_qua += tmp;
		tmp *= tmp;
	}
	cout << ket_qua;
	return 0;
}
```
# Câu 5
![image](https://user-images.githubusercontent.com/91708234/139798451-a11143a3-5cd8-41a4-8d6f-507a67896057.png)
## Ý tưởng
	Câu này kiểu căn lồng căn, nhìn phức tạp nhưng không phức tạp. 
	
	Mình quan sát thấy tính từ trong ra ngoài là khá dễ để giải quyết bài này. 
	
	Ví dụ n = 2 thì chỉ cần tính sqrt(x) rồi cộng nó vào x^2 và tiếp tục tính căn.
	
	Trờ lại bài toán, cứ làm như ví dụ ở trên cho đến số mũ bằng n thì dừng lại.
	
## Code
```cpp
#include<iostream>
using namespace std;

int main() {
	int n, x;
	cin >> n >> x;
	double ket_qua = 0;
	double a = x; // bien phu tinh x^n
	for (int i = 1; i <= n; i++) {
		ket_qua = sqrt(ket_qua + a);
		a *= x;
	}
	cout << ket_qua;
}
```
# Câu 6
![image](https://user-images.githubusercontent.com/91708234/139799119-22bb6179-1c4e-431c-9da1-0826885fd4f0.png)
## Ý tưởng
	Trong đề bài có một từ khá khó hiểu đó là độ chính xác 10^-6. 
	
	Vậy ý nghĩa của nó là gì? Độ chính xác α tì số hạng trong tổng phải >= α.
	
	Bây giờ bài toán trở nên dễ hiểu hơn. Ta chỉ cần tính tổng các số hạng cho đến khi số hạng < 10^-6 thì dừng lại -> vòng lặp.
	
## Code
```cpp
#include<iostream>
using namespace std;

int main() {
	double e = 1e-6;
	double ket_qua = 0;
	for (int i = 1; i <= 1e+6; i++) {
		if (1.0 / i >= e) {
			ket_qua += 1.0 / i;
		}
		else {
			break;
		}
	}
	cout << ket_qua;
}
```

# Câu 7
![image](https://user-images.githubusercontent.com/91708234/139799603-db6c3333-9ad5-4a2b-ad48-7b90f4df3141.png)

## Ý tưởng
	Muốn tính an thì phải có an-1, 3^n và 7^n. 
	
	3^n = 3.3.3...3 ( n số 3, tương tự với 7^n ) 
	
	an-1 có được từ an-2 ... a2 có từ a1 mà a1 = -2.
	
	Vậy muốn tính an thì phải tính a2, a3, a4, ... an-1.
	
	-> Đưa tất cả vào vòng lặp.
	
## Code
	Ở đây mình dùng biến mu_3 và mu_7 để lưu lại gia trị của 3^n và 7^n. 
	
	Sau đó mình sử dụng vòng lặp để lần lượt tính a2, a3,..., an.
	
```cpp
#include<iostream>
using namespace std;
int main() {
	int n;
	cin >> n;
	long long an = -2;
	long long mu_3 = 3, mu_7 = 7;
	for (int i = 2; i <= n; i++) {
		mu_3 *= 3;
		mu_7 *= 7;
		an = 5 * an + 2 * mu_3 - 6 * mu_7 + 12;
	}
	cout << an;
}
```
# Câu 8
![image](https://user-images.githubusercontent.com/91708234/139800414-8196ab2e-fd8b-4c37-a52b-b3d49a6ae6bc.png)
## Ý tưởng
	Đề bài đã cho x, y, z là 3 cạnh của tam giác nên minh sẽ không xét điều kiện x, y, z là 3 cạnh của tam giác nữa.
	
	Ở đây đề không đề cập tới kiểu tam giác cụ thể nên mình sẽ chia thành một số loại sau : 
	
		+ Tam giác vuông: xét theo định lý pytago
		
		+ Tam giác vuông cân: tiên quyết là tam giác vuông và sau đó là có 2 cạnh bằng nhau.
		
		+ Tam giác đều: tam giác có 3 cạnh bằng nhau.
		
		+ Tam giác cân: có its nhất 2 cạnh bằng nhau.
		
		+ Tam giác thường: các loại như tam giác nhọn, tam giác tù, ...
		
## Code
```cpp
#include<iostream>
using namespace std;

int main() {
	double x, y, z;
	cin >> x >> y >> z;
	if (x * x + y * y == z * z || y * y + z * z == x * x || z * z + x * x == y * y) {
		if (x == y || y == z || x == z) {
			cout << "Tam giac vuong can";
		}
		else {
			cout << "Tam giac vuong";
		}
	}
	if (x == y || y == z || x == z) cout << "Tam giac can";
	if (x == y && y == z) cout << "Tam giac deu";
	return 0;
}
```

# Câu 9
![image](https://user-images.githubusercontent.com/91708234/139801540-ab45dbd3-30ff-4f18-a501-e5967685d6ad.png)

## Ý tưởng
	Số chính phương là số khi lấy căn bậc 2 chính nó bằng 1 số nguyên.
	
	Vậy chỉ cần chạy vòng lặp từ 0 đến chính nó khi nào có 
	
	số bình phương bằng số cần xét thì thoát vòng lặp là xong.
	
	Nhưng như vậy nếu nó không phải số chính phương nhưng lại quá lớn thì sao? 
	
	Nó sẽ gây tốn thời gian để thực hiện vòng lặp. Mình sẽ thêm điều kiện nếu 
	
	bình phương của biến vòng lặp lớn hơn số đang xét thì thoát vòng lặp.
	
## Code
	Gia trị 1 đại diện cho đúng và 0 đại diện cho sai.
```cpp
#include <iostream>
#include<math.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    for (int i = 0; i <= n; i++) {
        if (i * i == n) {
            cout << 1;
            break;
        }
        if (i * i > n) {
	    cout << 0;
	    break;
	}
    }
    return 0;
}
```
## Bonus - cách dùng thư viện
	Mình chỉ cần kiểm tra xem căn của số đang xét có phải số nguyên hay không là xong.
	
	Gia trị 1 đại diện cho đúng và 0 đại diện cho sai.
```cpp
#include<iostream>
using namespace std;

int main() {
	long long n;
	cin >> n;
	if (sqrt(n) == int(sqrt(n))) cout << 1;
	else cout << 0;
	return 0;
}
```

# Câu 10
![image](https://user-images.githubusercontent.com/91708234/139802605-310dba69-90d4-4a26-8de2-4f82222deff5.png)

## Ý tưởng
	Ta có 5^0 = 1, 5^m = 5.5.5...5 (n số 5). Vậy một số muốn có dạng 5^m thì khi chia nguyên nó cho 5 không thu được số chấm động trước khi thu được số 1.

## Code
	Ở đây mình sử dụng điều kiện vòng lặp là n > 1 
	vì nếu n=1 thì chuyển ngay sang bước in kết quả.
	Gia trị 1 đại diện cho đúng và 0 đại diện cho sai.
```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;
    while (n > 1) {
        n /= 5;
    }
    if (n == 1) cout << 1;
    else cout << 0;
    return 0;
}
```
## Bonus
	Mình tham khảo ý tưởng từ 1 bạn trong ban. 
	
	Nếu n có dạng 5^m thì log(n) / log(5) = m. 
	
	Chuyển về bài thì mình chưa biết m là bao nhiêu nên mình đổi thành kiểm tra nó có phải số nguyên hay hông.
	
	Gia trị 1 đại diện cho đúng và 0 đại diện cho sai.
```cpp
#include<iostream>
#include<math.h>
using namespace std;

int main() {
	long long n;
	cin >> n;
	if (log(n) / log(5) == int(log(n) / log(5))) cout << 1;
	else cout << 0;
	return 0;
}
```
