## **Design Patterns là gì? Tại sao nó là trợ thủ đắc lực của Developers?**

# **I. Định nghĩa**
Design Pattern (mẫu thiết kế) là các giải pháp tối ưu, tái sử dụng để giải quyết các vấn đề phổ biến trong lập trình hướng đối tượng (OOP).  
- **Tính chất**: Là kỹ thuật lập trình, không phụ thuộc vào ngôn ngữ cụ thể.  
- **Mục tiêu**: Cung cấp các giải pháp tối ưu để giải quyết vấn đề một cách hiệu quả.

Tóm lại thì là những kinh nghiệm mà người trước đã đổ máu để rút ra, và khi chúng ta gặp những trường hợp củ thể thì mình có thể áp dụng theo công thức này luôn.


# **II. Lợi ích của Design Patterns đối với Developers**
1. **Tăng tốc độ phát triển phần mềm**:  
   - Cung cấp các giải pháp thông dụng cho các vấn đề phổ biến.  
   - Áp dụng các nguyên tắc OOP để tối ưu hóa thiết kế.  

2. **Code tường minh, dễ làm việc nhóm**:  
   - Định nghĩa ngôn ngữ chung giúp nhóm giao tiếp hiệu quả.  
   - Tiết kiệm thời gian khi chỉ cần nhắc tên pattern là có thể hiểu được ý tưởng.

3. **Tái sử dụng code**:  
   - Giảm thời gian viết code nhờ tái sử dụng các giải pháp đã được kiểm chứng.  
   - Dễ dàng mở rộng hoặc tùy chỉnh.  

4. **Hạn chế lỗi và dễ bảo trì**:  
   - Tránh các vấn đề tiềm ẩn gây lỗi lớn trong tương lai.  
   - Dự án dễ dàng nâng cấp và bảo trì.

# **III. Phân loại Design Patterns**
Hệ thống 23 mẫu design pattern được chia thành 3 nhóm chính theo cuốn *"Design Patterns: Elements of Reusable Object-Oriented Software"*:

## **Creational Patterns (Nhóm khởi tạo)**  
### **Mục tiêu**: Tạo đối tượng mà không cần sử dụng trực tiếp từ khóa `new`.  
### **Mẫu tiêu biểu**:
  - Singleton
  - Factory Method
  - Abstract Factory
  - Builder
  - Prototype  
### **Hiểu thêm**:

#### **1. Singleton Design Pattern**

Là một mẫu thiết kế (design pattern) trong lập trình, được sử dụng để đảm bảo rằng một lớp (class) chỉ có duy nhất một thể hiện (instance) trong toàn bộ ứng dụng và cung cấp một điểm truy cập toàn cầu đến thể hiện đó. Mẫu thiết kế này giúp tiết kiệm bộ nhớ, vì không tạo ra nhiều đối tượng của lớp, đồng thời quản lý trạng thái chung của ứng dụng.

Các đặc điểm chính của Singleton Pattern:
- **Một thể hiện duy nhất**: Lớp chỉ tạo một thể hiện duy nhất trong suốt vòng đời của ứng dụng.
- **Điểm truy cập toàn cục**: Cung cấp một phương thức tĩnh để truy cập thể hiện duy nhất của lớp đó.
- **Khởi tạo lazy**: Thể hiện chỉ được tạo khi nó được yêu cầu (khởi tạo theo nhu cầu, không khởi tạo ngay lập tức khi ứng dụng bắt đầu).
- Tóm lại `Singleton Pattern` là bạn có một đối tượng được khởi tạo và gán giá trị cho biến thì những lần khởi tạo sau thì giá trị của biến không đổi.
Dưới đây là đoạn mã của lớp `Constants` đã được định dạng lại để dễ đọc hơn:

```typescript
export class Constants {
    static serverAddress = environment.serverAddress;

    static snackBarDuration = 2500;



    static MONTH_YEAR_FORMATS: MatDateFormats = {
        parse: {
            dateInput: 'MM/YYYY',
        },
        display: {
            dateInput: 'MM/YYYY',
            monthYearLabel: 'MMM YYYY',
            dateA11yLabel: 'LL',
            monthYearA11yLabel: 'MMMM YYYY',
        },
    };
}
```
- Đoạn mã trên không phải là `Singleton Pattern` mà là một lớp `Constants` đơn giản với các thuộc tính tĩnh (static). Các thuộc tính này có thể được truy cập trực tiếp mà không cần tạo thể hiện của lớp `(new)`, vì tất cả các thuộc tính và phương thức trong lớp đều được khai báo là `static`.

Ví dụ về Singleton Pattern trong JavaScript:

```javascript
class Singleton {
    constructor() {
        if (Singleton.instance) {
            return Singleton.instance;
        }
        this.value = Math.random();
        Singleton.instance = this;
    }

    getValue() {
        return this.value;
    }
}

// Tạo 2 đối tượng
const instance1 = new Singleton();
const instance2 = new Singleton();

console.log(instance1 === instance2); // true, vì chỉ có một instance duy nhất
console.log(instance1.getValue() === instance2.getValue()); // true
```


### **Singleton**
## **Structural Patterns (Nhóm cấu trúc)**  
- **Mục tiêu**: Thiết lập và định nghĩa quan hệ giữa các đối tượng hoặc class.  
- **Mẫu tiêu biểu**:
  - Adapter
  - Bridge
  - Composite
  - Decorator
  - Facade
  - Flyweight
  - Proxy  

## **Behavioral Patterns (Nhóm hành vi)**  
- **Mục tiêu**: Quản lý quan hệ hành vi giữa các đối tượng.  
- **Mẫu tiêu biểu**:
  - Interpreter
  - Template Method
  - Chain of Responsibility
  - Command
  - Iterator
  - Mediator
  - Memento
  - Observer
  - State
  - Strategy
  - Visitor  

# **IV. Kết luận**
Design Patterns là công cụ mạnh mẽ giúp lập trình viên:  
- Xây dựng phần mềm tối ưu hơn.  
- Làm việc nhóm hiệu quả.  
- Bảo trì và mở rộng dự án dễ dàng.  
