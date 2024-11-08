Dưới đây là cách triển khai một chức năng đơn giản tìm kiếm thông tin của một mẫu giày, áp dụng mô hình 3-Tier với Java Swing và JDBC. Cấu trúc ứng dụng sẽ bao gồm các thành phần theo mô hình 3-Tier: **DAO**, **Service**, **DTO**, **View (tìm kiếm và kết quả)**, và **Controller**.

---

### **1. Tầng Dữ Liệu (Data Layer)**

#### Lớp `ShoeDAO`: Xử lý truy xuất dữ liệu từ cơ sở dữ liệu

```java
import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;

public class ShoeDAO {
    private Connection connection;

    public ShoeDAO(Connection connection) {
        this.connection = connection;
    }

    // Phương thức tìm kiếm giày theo mã giày và trả về DTO
    public ShoeDTO findShoeByCode(String shoeCode) throws SQLException {
        String query = "SELECT * FROM Shoes WHERE shoe_code = ?";
        try (PreparedStatement statement = connection.prepareStatement(query)) {
            statement.setString(1, shoeCode);
            ResultSet resultSet = statement.executeQuery();
            if (resultSet.next()) {
                return new ShoeDTO(
                        resultSet.getString("shoe_code"),
                        resultSet.getString("name"),
                        resultSet.getString("brand"),
                        resultSet.getDouble("price")
                );
            }
        }
        return null; // Trả về null nếu không tìm thấy
    }
}
```

### **2. Tầng Logic (Application Layer)**

#### Lớp `ShoeService`: Xử lý logic nghiệp vụ tìm kiếm giày

```java
public class ShoeService {
    private ShoeDAO shoeDAO;

    public ShoeService(ShoeDAO shoeDAO) {
        this.shoeDAO = shoeDAO;
    }

    // Phương thức tìm kiếm giày theo mã giày
    public ShoeDTO searchShoeByCode(String shoeCode) throws SQLException {
        if (shoeCode == null || shoeCode.isEmpty()) {
            throw new IllegalArgumentException("Mã giày không được để trống.");
        }
        return shoeDAO.findShoeByCode(shoeCode);
    }
}
```

#### Lớp `ShoeDTO`: Đối tượng truyền dữ liệu (DTO)

```java
public class ShoeDTO {
    private String code;
    private String name;
    private String brand;
    private double price;

    public ShoeDTO(String code, String name, String brand, double price) {
        this.code = code;
        this.name = name;
        this.brand = brand;
        this.price = price;
    }

    // Các getter
    public String getCode() { return code; }
    public String getName() { return name; }
    public String getBrand() { return brand; }
    public double getPrice() { return price; }
}
```

---

### **3. Tầng Giao Diện (Presentation Layer)**

#### 3.1. Lớp `ShoeSearchView` (Giao diện tìm kiếm)

```java
import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionListener;

public class ShoeSearchView extends JFrame {
    private JTextField shoeCodeField;
    private JButton searchButton;

    public ShoeSearchView() {
        setupUI();
    }

    private void setupUI() {
        setTitle("Tìm kiếm giày");
        setSize(300, 150);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLocationRelativeTo(null);

        // Tạo các thành phần giao diện
        shoeCodeField = new JTextField(15);
        searchButton = new JButton("Tìm kiếm");

        // Panel nhập mã giày
        JPanel inputPanel = new JPanel();
        inputPanel.add(new JLabel("Mã giày:"));
        inputPanel.add(shoeCodeField);

        // Thêm panel và nút tìm kiếm
        setLayout(new BorderLayout());
        add(inputPanel, BorderLayout.CENTER);
        add(searchButton, BorderLayout.SOUTH);
    }

    // Getter cho mã giày
    public String getShoeCode() {
        return shoeCodeField.getText();
    }

    // Thiết lập ActionListener cho nút tìm kiếm
    public void setSearchButtonListener(ActionListener listener) {
        searchButton.addActionListener(listener);
    }
}
```

#### 3.2. Lớp `ShoeResultView` (Giao diện kết quả)

```java
import javax.swing.*;

public class ShoeResultView extends JFrame {
    private JLabel nameLabel;
    private JLabel brandLabel;
    private JLabel priceLabel;

    public ShoeResultView() {
        setupUI();
    }

    private void setupUI() {
        setTitle("Thông tin giày");
        setSize(300, 200);
        setDefaultCloseOperation(JFrame.DISPOSE_ON_CLOSE);
        setLocationRelativeTo(null);

        // Tạo các thành phần giao diện để hiển thị thông tin giày
        nameLabel = new JLabel();
        brandLabel = new JLabel();
        priceLabel = new JLabel();

        JPanel panel = new JPanel();
        panel.setLayout(new BoxLayout(panel, BoxLayout.Y_AXIS));
        panel.add(new JLabel("Tên giày:"));
        panel.add(nameLabel);
        panel.add(new JLabel("Thương hiệu:"));
        panel.add(brandLabel);
        panel.add(new JLabel("Giá:"));
        panel.add(priceLabel);

        add(panel);
    }

    // Phương thức hiển thị thông tin giày
    public void displayShoeDetails(ShoeDTO shoe) {
        nameLabel.setText(shoe.getName());
        brandLabel.setText(shoe.getBrand());
        priceLabel.setText(shoe.getPrice() + " VND");
    }
}
```

---

### **4. Controller**

#### Lớp `ShoeController`: Xử lý logic giữa View và Service

```java
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class ShoeController {
    private ShoeSearchView searchView;
    private ShoeService service;

    public ShoeController(ShoeSearchView searchView, ShoeService service) {
        this.searchView = searchView;
        this.service = service;

        // Thiết lập ActionListener cho nút tìm kiếm
        this.searchView.setSearchButtonListener(new SearchButtonListener());
    }

    // Inner class xử lý sự kiện tìm kiếm
    class SearchButtonListener implements ActionListener {
        @Override
        public void actionPerformed(ActionEvent e) {
            String shoeCode = searchView.getShoeCode();
            try {
                ShoeDTO shoe = service.searchShoeByCode(shoeCode);
                if (shoe != null) {
                    // Hiển thị kết quả tìm kiếm trong ShoeResultView
                    ShoeResultView resultView = new ShoeResultView();
                    resultView.displayShoeDetails(shoe);
                    resultView.setVisible(true);
                } else {
                    JOptionPane.showMessageDialog(searchView, "Không tìm thấy giày với mã này.");
                }
            } catch (Exception ex) {
                JOptionPane.showMessageDialog(searchView, "Lỗi: " + ex.getMessage());
            }
        }
    }
}
```

---

### **5. Khởi tạo và chạy ứng dụng**

#### Lớp `Main`: Khởi tạo các thành phần và chạy ứng dụng

```java
import java.sql.Connection;
import java.sql.DriverManager;

public class Main {
    public static void main(String[] args) {
        try {
            // Kết nối cơ sở dữ liệu
            String url = "jdbc:mysql://localhost:3306/your_database_name";
            String user = "your_db_user";
            String password = "your_db_password";
            Connection connection = DriverManager.getConnection(url, user, password);

            // Khởi tạo các lớp DAO, Service, View và Controller
            ShoeDAO shoeDAO = new ShoeDAO(connection);
            ShoeService shoeService = new ShoeService(shoeDAO);
            ShoeSearchView searchView = new ShoeSearchView();
            new ShoeController(searchView, shoeService);

            // Hiển thị giao diện tìm kiếm
            searchView.setVisible(true);

        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

---

### Giải thích sự tách biệt

- **ShoeSearchView (View Tìm Kiếm)**: Giao diện để người dùng nhập mã giày và nhấn nút tìm kiếm.
- **ShoeResultView (View Kết Quả)**: Hiển thị thông tin chi tiết của giày sau khi tìm kiếm.
- **ShoeDTO**: Đối tượng truyền dữ liệu giữa tầng Dữ liệu và Logic, giúp truyền tải dữ liệu giày một cách rõ ràng và dễ quản lý.
- **ShoeController**: Điều khiển luồng dữ liệu giữa các lớp `ShoeSearchView`, `ShoeService`, và `ShoeResultView`, xử lý sự kiện khi nhấn nút tìm kiếm.
