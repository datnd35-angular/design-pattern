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


### Ví dụ 2

**Tình huống thực tế:**
Giả sử bạn đang phát triển phần mềm quản lý nhà máy sản xuất, trong đó có các loại máy móc khác nhau như **Máy in**, **Máy cắt**, **Máy hàn**, mỗi loại máy sẽ có những hành động và đặc tính riêng. Bạn muốn tạo ra các đối tượng của các loại máy này mà không cần phải phụ thuộc vào cụ thể từng lớp máy, giúp mã dễ mở rộng và bảo trì.

**Giải pháp với Factory Method Pattern:**
Bạn sẽ tạo ra một **Factory** cho mỗi loại máy, và sử dụng **Factory Method** để quyết định loại máy sẽ được tạo ra dựa trên các yêu cầu của hệ thống.

**Các lớp trong Factory Method Pattern:**

1. **Product (Máy móc)**: Đây là các lớp mô tả các loại máy móc, ví dụ: `PrintingMachine`, `CuttingMachine`, `WeldingMachine`.

2. **Creator (Factory)**: Lớp factory sẽ có một phương thức `CreateMachine()` để tạo ra các đối tượng máy móc.

3. **ConcreteCreator**: Các lớp con của factory (tạo ra các máy cụ thể như `PrintingMachineCreator`, `CuttingMachineCreator`).

```
// Abstract Product: Các loại máy móc
public interface IMachine
{
    void Operate();
}

// Concrete Products: Các loại máy móc cụ thể
public class PrintingMachine : IMachine
{
    public void Operate()
    {
        Console.WriteLine("Printing machine is operating.");
    }
}

public class CuttingMachine : IMachine
{
    public void Operate()
    {
        Console.WriteLine("Cutting machine is operating.");
    }
}

public class WeldingMachine : IMachine
{
    public void Operate()
    {
        Console.WriteLine("Welding machine is operating.");
    }
}

// Creator (Factory)
public abstract class MachineFactory
{
    public abstract IMachine CreateMachine();  // Factory Method

    // Một phương thức giúp client sử dụng máy mà không cần biết rõ lớp cụ thể
    public void StartMachine()
    {
        IMachine machine = CreateMachine();
        machine.Operate();
    }
}

// Concrete Creators
public class PrintingMachineFactory : MachineFactory
{
    public override IMachine CreateMachine()
    {
        return new PrintingMachine();
    }
}

public class CuttingMachineFactory : MachineFactory
{
    public override IMachine CreateMachine()
    {
        return new CuttingMachine();
    }
}

public class WeldingMachineFactory : MachineFactory
{
    public override IMachine CreateMachine()
    {
        return new WeldingMachine();
    }
}

// Client code
class Program
{
    static void Main(string[] args)
    {
        // Tạo các factory để tạo các loại máy khác nhau
        MachineFactory printingFactory = new PrintingMachineFactory();
        MachineFactory cuttingFactory = new CuttingMachineFactory();
        MachineFactory weldingFactory = new WeldingMachineFactory();

        // Sử dụng factory để tạo và vận hành máy
        printingFactory.StartMachine(); // Output: Printing machine is operating.
        cuttingFactory.StartMachine();  // Output: Cutting machine is operating.
        weldingFactory.StartMachine();  // Output: Welding machine is operating.
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


### **Tình huống thực tế:**
Giả sử bạn đang phát triển phần mềm quản lý nhà máy sản xuất, trong đó có các hệ thống cũ (legacy systems) mà bạn cần tích hợp với phần mềm mới. Một trong những hệ thống cũ là hệ thống quản lý máy móc, có giao diện cũ và không tương thích với các yêu cầu mới của phần mềm quản lý. Bạn cần tích hợp hệ thống này vào phần mềm mới mà không muốn thay đổi mã nguồn cũ.

### **Giải pháp với Adapter Pattern:**
Bạn có thể sử dụng **Adapter Pattern** để "bao bọc" hệ thống cũ, chuyển giao diện của hệ thống cũ thành một giao diện mà phần mềm mới có thể hiểu và làm việc với nó. Điều này giúp bạn giữ nguyên hệ thống cũ mà vẫn có thể tương tác với phần mềm mới.

### **Các lớp trong Adapter Pattern:**

1. **Target (Mục tiêu)**: Giao diện mà phần mềm mới yêu cầu, có thể là các phương thức mà phần mềm quản lý mới cần sử dụng.

2. **Adapter**: Là lớp trung gian giúp chuyển giao diện từ hệ thống cũ (Service) sang giao diện mà phần mềm mới (Client) mong muốn. Lớp Adapter sẽ sử dụng đối tượng cũ để thực hiện các phương thức mà phần mềm mới yêu cầu.

3. **Adaptee (Hệ thống cũ)**: Lớp cũ hoặc hệ thống cũ mà bạn muốn tích hợp vào phần mềm mới, nhưng có giao diện không tương thích.

### **Ví dụ với mã C#**:

Giả sử hệ thống cũ cung cấp một lớp `LegacyMachine` với phương thức `GetMachineData()`, trong khi phần mềm mới yêu cầu một giao diện `IMachine` với phương thức `GetMachineDetails()`.

```csharp
// Target interface
public interface IMachine
{
    string GetMachineDetails();
}

// Adaptee (Hệ thống cũ)
public class LegacyMachine
{
    public string GetMachineData()
    {
        return "Legacy Machine Data";
    }
}

// Adapter class
public class MachineAdapter : IMachine
{
    private readonly LegacyMachine _legacyMachine;

    public MachineAdapter(LegacyMachine legacyMachine)
    {
        _legacyMachine = legacyMachine;
    }

    // Phương thức này chuyển đổi từ hệ thống cũ sang giao diện mới
    public string GetMachineDetails()
    {
        // Chuyển đổi dữ liệu từ hệ thống cũ sang giao diện mới
        return _legacyMachine.GetMachineData();
    }
}

// Client sử dụng giao diện mới
public class Client
{
    private readonly IMachine _machine;

    public Client(IMachine machine)
    {
        _machine = machine;
    }

    public void DisplayMachineDetails()
    {
        Console.WriteLine(_machine.GetMachineDetails());
    }
}

// Sử dụng Adapter trong hàm Main
public class Program
{
    public static void Main(string[] args)
    {
        // Hệ thống cũ
        LegacyMachine legacyMachine = new LegacyMachine();

        // Adapter giúp lớp mới tương tác với hệ thống cũ
        IMachine machine = new MachineAdapter(legacyMachine);

        // Client làm việc với giao diện mới
        Client client = new Client(machine);
        client.DisplayMachineDetails(); // In ra: Legacy Machine Data
    }
}
```

### **Giải thích:**
- **LegacyMachine** là hệ thống cũ với phương thức `GetMachineData()`.
- **IMachine** là giao diện mà phần mềm mới yêu cầu.
- **MachineAdapter** là lớp Adapter, nó "bao bọc" `LegacyMachine` và chuyển đổi phương thức `GetMachineData()` thành `GetMachineDetails()` mà phần mềm mới mong muốn.
- **Client** là phần mềm mới, chỉ giao tiếp với hệ thống qua giao diện `IMachine`, không cần quan tâm hệ thống cũ như thế nào.

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

#### **1. Adapter Design Pattern**

Là một mẫu thiết kế thuộc nhóm **Structural Patterns**, được sử dụng khi bạn muốn **kết nối các class có interface không tương thích** để chúng có thể làm việc cùng nhau.

Adapter đóng vai trò là **cầu nối** giữa một interface có sẵn và một interface mới mà client mong muốn, giúp tái sử dụng code mà không phải sửa đổi lớp gốc.

### 🔍 Đặc điểm chính của Adapter Pattern:
- **Chuyển đổi interface không tương thích thành interface mong muốn**.
- **Tái sử dụng class hiện tại** mà không cần thay đổi code gốc.
- **Tăng tính mở rộng và khả năng tương tác** giữa các hệ thống cũ và mới.
- Có thể thực hiện theo **kế thừa (Class Adapter)** hoặc **composition (Object Adapter)**.

### 🚩 Bài toán cần giải quyết (Trước khi dùng Adapter)

Bạn đang phát triển ứng dụng theo dõi chứng khoán, dữ liệu thị trường được lấy về theo định dạng **XML**, nhưng thư viện phân tích bạn muốn tích hợp lại chỉ hỗ trợ **JSON**.

**Vấn đề**:
- Không thể sửa đổi thư viện hoặc dữ liệu gốc.
- Nếu tự viết logic chuyển đổi trong toàn bộ hệ thống, sẽ làm **phân tán, khó bảo trì**.

### Giải pháp: Sử dụng Adapter

Bạn có thể viết một **Adapter** để chuyển đổi dữ liệu từ XML sang JSON trước khi truyền vào thư viện phân tích.

> Khi client gọi phương thức, Adapter sẽ **"dịch" request** sang dạng mà service (thư viện phân tích) hiểu được.


###  Các kiểu Adapter phổ biến

#### Object Adapter – Composition
- Adapter **chứa (wrap)** một instance của class gốc (Adaptee).
- Adapter **implement interface mới (Target)** để tương thích với client.

**Ưu điểm**:
- Linh hoạt hơn, có thể tái sử dụng với nhiều Adaptee khác nhau.

#### Class Adapter – Inheritance
- Adapter **kế thừa Adaptee** và **implement interface Target**.
- Ghi đè phương thức để chuyển đổi logic khi cần.

**Hạn chế**:
- Bị ràng buộc bởi khả năng kế thừa (chỉ hỗ trợ 1 Adaptee tại một thời điểm).

### So sánh nhanh giữa 2 loại Adapter:

| Tiêu chí              | Object Adapter           | Class Adapter              |
|-----------------------|--------------------------|-----------------------------|
| Dựa trên              | Composition              | Inheritance                 |
| Tái sử dụng nhiều Adaptee | ✔️ Có                  | ❌ Không                    |
| Dễ mở rộng            | ✔️ Có                    | ❌ Khó                      |
| Phù hợp với interface | ✔️                      | ❌ Không nếu là class       |


###  Ưu điểm:
- **Tuân thủ SRP**: Adapter tách biệt logic chuyển đổi khỏi business code.
- **Tuân thủ OCP**: Không cần sửa code gốc khi muốn mở rộng.
- Tái sử dụng dễ dàng, phù hợp khi tích hợp hệ thống bên thứ ba.

###  Nhược điểm:
- Tăng số lượng lớp trong hệ thống.
- Có thể phức tạp hơn nếu chỉ cần sửa một vài dòng code.

### Khi nào nên dùng Adapter Pattern?
- Khi cần **tái sử dụng class cũ** nhưng interface không tương thích.
- Khi bạn không thể sửa class gốc (bên thứ ba, thư viện đóng gói).
- Khi muốn **hợp nhất** hệ thống mới và cũ mà không gây ảnh hưởng ngược.

### Ví dụ minh họa bằng C#

```csharp
public interface IShape
{
    void Draw(int x1, int y1, int x2, int y2);
}

// Adaptee: không tương thích với IShape
public class LegacyLine
{
    public void Draw(int x1, int y1, int x2, int y2)
    {
        Console.WriteLine($"Drawing line from ({x1}, {y1}) to ({x2}, {y2})");
    }
}

// Adapter: giúp LegacyLine tương thích với IShape
public class LineAdapter : IShape
{
    private readonly LegacyLine _legacyLine;

    public LineAdapter(LegacyLine legacyLine)
    {
        _legacyLine = legacyLine;
    }

    public void Draw(int x1, int y1, int x2, int y2)
    {
        _legacyLine.Draw(x1, y1, x2, y2);
    }
}
```

```csharp
// Adaptee khác
public class LegacyRectangle
{
    public void Draw(int x, int y, int w, int h)
    {
        Console.WriteLine($"Drawing rectangle at ({x},{y}) width {w} height {h}");
    }
}

// Adapter cho LegacyRectangle
public class RectangleAdapter : IShape
{
    private readonly LegacyRectangle _legacyRectangle;

    public RectangleAdapter(LegacyRectangle legacyRectangle)
    {
        _legacyRectangle = legacyRectangle;
    }

    public void Draw(int x1, int y1, int x2, int y2)
    {
        int x = Math.Min(x1, x2);
        int y = Math.Min(y1, y2);
        int w = Math.Abs(x2 - x1);
        int h = Math.Abs(y2 - y1);
        _legacyRectangle.Draw(x, y, w, h);
    }
}
```

```csharp
// Client code sử dụng interface thống nhất
class Program
{
    static void Main(string[] args)
    {
        List<IShape> shapes = new List<IShape>
        {
            new LineAdapter(new LegacyLine()),
            new RectangleAdapter(new LegacyRectangle())
        };

        shapes.ForEach(shape => shape.Draw(5, 10, -3, 2));
    }
}
```

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
