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

#### **2. Factory Method Design Pattern**

Là một mẫu thiết kế thuộc nhóm **Creational Patterns**, được sử dụng khi bạn cần tạo ra một đối tượng nhưng **không biết trước** đối tượng cụ thể là gì – nó phụ thuộc vào **logic nghiệp vụ (business logic)** tại runtime.

Mẫu này cung cấp **một interface chung để tạo đối tượng**, nhưng cho phép các lớp con **tự quyết định loại đối tượng nào sẽ được tạo ra**.

### Các đặc điểm chính của Factory Method:
- **Tạo đối tượng thông qua interface chung**: Không khởi tạo trực tiếp thông qua `new`.
- **Ẩn logic khởi tạo**: Che giấu toàn bộ quá trình xử lý phức tạp khi tạo object.
- **Hạn chế sự phụ thuộc** giữa client code và các lớp cụ thể.
- **Dễ mở rộng**: Thêm object mới mà không ảnh hưởng đến hệ thống cũ.
- **Tăng tính đa hình**: Lựa chọn object khởi tạo dựa vào tham số truyền vào.

### Ví dụ vấn đề (Trước khi dùng Factory Method)

Giả sử bạn có interface `IAnimal` và các class `Dog`, `Cat`, `Duck` implement nó:

```csharp
IAnimal animal;

if (...) {
    animal = new Dog();
} else if (...) {
    animal = new Cat();
} else {
    animal = new Duck();
}
```

**Nhược điểm**:
- Lặp lại logic khởi tạo ở nhiều nơi.
- Khó bảo trì, dễ lỗi nếu phải sửa ở nhiều chỗ.
- Thiếu tính mở rộng và dễ vi phạm nguyên lý **Open/Closed**.


### Giải pháp: Sử dụng Factory Method

Tạo ra một class `AnimalFactory` để quản lý logic khởi tạo:

```csharp
public class AnimalFactory {
    public static IAnimal CreateAnimal(AnimalType type)
    {
        switch (type) {
            case AnimalType.Cat:
                return new Cat();
            case AnimalType.Dog:
                return new Dog();
            case AnimalType.Duck:
                return new Duck();
            default:
                throw new ArgumentException("Invalid animal type");
        }
    }
}
```


### Kiến trúc của Factory Method Pattern

- **Product**: Interface/abstract class định nghĩa các đối tượng được tạo.
- **ConcreteProduct**: Các class cụ thể implement `Product`.
- **Creator**: Khai báo method tạo `Product`. Có thể chứa default implementation.
- **ConcreteCreator**: Ghi đè `factory method` để tạo `ConcreteProduct`.


### Ưu điểm:
- Tăng tính linh hoạt, dễ bảo trì.
- Tập trung logic khởi tạo tại một nơi.
- Dễ mở rộng (add class mới mà không sửa client).
- Giảm lỗi compile-time, hỗ trợ xử lý lỗi khởi tạo.

### Nhược điểm:
- Tăng số lượng class cần tạo.
- Refactor từ code cũ sang Factory có thể phức tạp.
- Nếu dùng private constructor, các class có thể không kế thừa được.

### Khi nào nên sử dụng:
- Khi bạn có nhiều class con kế thừa từ cùng một interface/abstract class.
- Khi logic khởi tạo phức tạp và được dùng ở nhiều nơi.
- Khi cần dễ dàng mở rộng hệ thống trong tương lai.


### Ví dụ minh họa với C#

```csharp
public interface IPizza
{
    decimal GetPrice();
}

public class HamAndMushroomPizza : IPizza
{
    public decimal GetPrice() => 8.5M;
}

public class DeluxePizza : IPizza
{
    public decimal GetPrice() => 10.5M;
}

public class SeafoodPizza : IPizza
{
    public decimal GetPrice() => 11.5M;
}

public class PizzaFactory
{
    public enum PizzaType { HamMushroom, Deluxe, Seafood }

    public IPizza CreatePizza(PizzaType pizzaType)
    {
        return pizzaType switch
        {
            PizzaType.HamMushroom => new HamAndMushroomPizza(),
            PizzaType.Deluxe => new DeluxePizza(),
            PizzaType.Seafood => new SeafoodPizza(),
            _ => throw new ArgumentException("Invalid pizza type"),
        };
    }
}
```

### Sử dụng Factory Method trong chương trình

```csharp
class Program
{
    static void Main(string[] args)
    {
        var factory = new PizzaFactory();
        var pizza = factory.CreatePizza(PizzaFactory.PizzaType.Seafood);

        Console.WriteLine(pizza.GetPrice()); // 11.5
    }
}
```
**Design Patterns liên quan:**
- **Abstract Factory**: Tạo ra *họ* các đối tượng liên quan thay vì một.
- **Prototype**: Tạo object bằng cách clone thay vì `new`.
- **Builder**: Dùng khi object có nhiều bước khởi tạo phức tạp.


#### **3. Abstract Factory Design Pattern**

Là một mẫu thiết kế thuộc nhóm **Creational Patterns** – chuyên dùng để khởi tạo đối tượng. Mẫu này cung cấp một **interface để tạo ra các họ (family) đối tượng liên quan hoặc phụ thuộc với nhau**, mà không cần chỉ rõ lớp cụ thể của chúng.

Khác với Factory Method chỉ tạo một object, **Abstract Factory tạo ra cả tập hợp (kit)** các object liên quan. Đây được xem là **“factory của các factory”**, một tầng trừu tượng cao hơn so với Factory Method.

### Các đặc điểm chính của Abstract Factory:
- **Tạo ra tập hợp các đối tượng liên quan** (cùng family).
- **Không phụ thuộc vào các lớp cụ thể** của object.
- **Hạn chế sự phụ thuộc giữa creator và concrete products**.
- **Dễ dàng mở rộng** và hỗ trợ các biến thể mới của sản phẩm.

### Mục đích sử dụng
- Cung cấp một interface cho việc khởi tạo các họ sản phẩm có liên quan.
- Tăng tính **đóng gói và tách biệt logic khởi tạo**.
- Tăng khả năng mở rộng: dễ thêm họ sản phẩm mới.
- Tạo ra các object tương thích với nhau trong cùng một cấu hình.

Ví dụ: Trong ứng dụng quản lý số điện thoại, mỗi quốc gia có quy tắc mã số riêng. Việc hỗ trợ thêm quốc gia mới sẽ phức tạp nếu không áp dụng Abstract Factory.

### Kiến trúc của Abstract Factory Pattern

**Các thành phần chính:**

- **AbstractFactory**: Interface/abstract class định nghĩa các phương thức để tạo ra các AbstractProduct.
- **ConcreteFactory**: Cài đặt các phương thức từ AbstractFactory để tạo ra ConcreteProduct tương ứng.
- **AbstractProduct**: Interface/abstract class của từng loại product.
- **ConcreteProduct**: Cài đặt cụ thể của AbstractProduct.
- **Client**: Sử dụng AbstractFactory và AbstractProduct, tương tác qua interface mà không cần biết lớp cụ thể.

### Ưu điểm
- Đảm bảo các sản phẩm tạo ra **tương thích với nhau**.
- Tránh ràng buộc chặt chẽ giữa **client** và **concrete product**.
- Dễ dàng mở rộng hoặc thêm biến thể sản phẩm mới.
- Tuân thủ **Nguyên tắc đơn lẻ** và **Open/Closed Principle**.

### Nhược điểm
- Tăng số lượng lớp và interface trong chương trình.
- Có thể khiến hệ thống trở nên **phức tạp không cần thiết** nếu không có nhiều họ sản phẩm.

### Khi nào nên sử dụng
- Khi các đối tượng cần được tạo ra theo **tập hợp tương thích**.
- Khi chương trình cần được **cấu hình với nhiều họ sản phẩm** khác nhau.
- Khi muốn **ẩn đi logic tạo ra đối tượng cụ thể** khỏi phía client.

### Ví dụ minh họa với C#

```csharp
// Abstract Factory
interface MonAnFactory
{
    HuTieu LayToHuTieu();
    My LayToMy();
}

// Abstract Product A
interface HuTieu
{
    string GetModelDetails();
}

// Abstract Product B
interface My
{
    string GetModelDetails();
}

// Concrete Factory 1
class LoaiGioFactory : MonAnFactory
{
    public HuTieu LayToHuTieu() => new HuTieuGio();
    public My LayToMy() => new MyGio();
}

// Concrete Factory 2
class LoaiNacFactory : MonAnFactory
{
    public HuTieu LayToHuTieu() => new HuTieuNac();
    public My LayToMy() => new MyNac();
}

// Concrete Products
class HuTieuNac : HuTieu
{
    public string GetModelDetails() => "HU TIEU NAC của em đây";
}

class HuTieuGio : HuTieu
{
    public string GetModelDetails() => "HU TIEU GIO của em đây";
}

class MyNac : My
{
    public string GetModelDetails() => "MY NAC của em đây";
}

class MyGio : My
{
    public string GetModelDetails() => "MY GIO của em đây";
}

// Client
class Client
{
    HuTieu hutieu;
    My my;

    public Client(MonAnFactory factory)
    {
        hutieu = factory.LayToHuTieu();
        my = factory.LayToMy();
    }

    public string GetHuTieuDetails() => hutieu.GetModelDetails();
    public string GetMyDetails() => my.GetModelDetails();
}
```

### Sử dụng trong `Main`

```csharp
class Program
{
    static void Main(string[] args)
    {
        MonAnFactory loaiNac = new LoaiNacFactory();
        Client nacClient = new Client(loaiNac);

        MonAnFactory loaiGio = new LoaiGioFactory();
        Client gioClient = new Client(loaiGio);

        Console.WriteLine("********* HU TIEU **********");
        Console.WriteLine(nacClient.GetHuTieuDetails());
        Console.WriteLine(gioClient.GetHuTieuDetails());

        Console.WriteLine("******* MY **********");
        Console.WriteLine(nacClient.GetMyDetails());
        Console.WriteLine(gioClient.GetMyDetails());

        Console.ReadKey();
    }
}
```

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
