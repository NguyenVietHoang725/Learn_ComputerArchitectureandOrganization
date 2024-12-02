# CHƯƠNG 3: BỘ XỬ LÝ TRUNG TÂM

---

## 1. Mô hình máy tính

Các loại mô hình:

- **Havard**: Lệnh và dữ liệu được lưu trữ trên hệ thông `bộ nhớ riêng biệt`.
- **Von Neumann**: Lệnh và dữ liệu được lưu trữ `trộn lẫn trên cùng một hệ thống bộ nhớ`. Đây là mô hình chính của máy tính cá nhân hiện nay.

![Hình 3.1. Mô hình máy tính](../Images/Hinh3.1.png)

Hình ảnh trên là một biểu diễn cơ bản về cấu trúc của một máy tính, bao gồm các thành phần chính và cách chúng giao tiếp với nhau thông qua các `bus`. Dưới đây là giải thích chi tiết về các phần trong mô hình này:

1. **CPU (Central Processing Unit)**:

- Đây là bộ xử lý trung tâm, đóng vai trò thực hiện các phép tính và điều khiển hoạt động của toàn bộ hệ thống.
- CPU giao tiếp với các thành phần khác thông qua `Address Bus`, `Data Bus`, và `Control Bus`.

2. **Memory Subsystem**:

- Đây là hệ thống bộ nhớ, nơi `lưu trữ dữ liệu và chương trình` mà CPU cần để thực hiện các tác vụ.
- CPU sử dụng `Address Bus` để chỉ định vị trí trong bộ nhớ mà nó muốn truy cập.
- `Data Bus` được dùng để truyền dữ liệu giữa CPU và bộ nhớ.
- `Control Bus` truyền tín hiệu điều khiển để đồng bộ hóa các hoạt động.

3. **I/O Subsystem (Input/Output Subsystem)**:

- Đây là hệ thống vào/ra, bao gồm các thiết bị như bàn phím, chuột, màn hình, máy in, v.v.
- Các thiết bị này được kết nối thông qua `I/O Devices` (các thiết bị đầu vào/đầu ra).
- CPU giao tiếp với các `thiết bị I/O` thông qua các bus tương tự như giao tiếp với bộ nhớ.

4. **Bus**:

- `Address Bus`: Truyền địa chỉ từ CPU đến các thành phần khác (bộ nhớ hoặc I/O) để chỉ định vị trí dữ liệu.
- `Data Bus`: Truyền dữ liệu giữa CPU và các thành phần khác.
- `Control Bus`: Truyền các tín hiệu điều khiển để quản lý và đồng bộ hóa hoạt động của các thành phần.

5. **Mối quan hệ và giao tiếp**:

- `CPU` là trung tâm điều khiển, gửi địa chỉ và tín hiệu điều khiển để xác định và thực hiện tác vụ trên `bộ nhớ` hoặc `thiết bị I/O`.
- `Hệ thống bus` là phương tiện chính giúp các thành phần trong máy tính giao tiếp với nhau.

Mô hình này minh họa cách tổ chức cơ bản của máy tính, được gọi là `kiến trúc Von Neumann`, nơi các thành phần chính chia sẻ chung một hệ thống bus để giao tiếp.

---

## 2. Sơ đồ khối tổng quát

![Hình 3.2: Sơ đồ khối tổng quát](../Images/Hinh3.2.png)

Hình ảnh này minh họa kiến trúc bên trong của một CPU (Central Processing Unit), với các thành phần chính và cách chúng tương tác với nhau. Dưới đây là giải thích chi tiết:

1. **Các thành phần chính của CPU**:

- `CU (Control Unit)`: Bộ điều khiển, chịu trách nhiệm điều phối hoạt động của các thành phần khác trong CPU và điều khiển luồng dữ liệu giữa CPU, bộ nhớ, và thiết bị I/O.
- `IR (Instruction Register)`: Thanh ghi lệnh, dùng để lưu trữ lệnh hiện tại mà CPU đang thực thi.
- `PC (Program Counter)`: Bộ đếm chương trình, chứa địa chỉ của lệnh tiếp theo cần thực thi.
- `MAR (Memory Address Register)`: Thanh ghi địa chỉ bộ nhớ, lưu địa chỉ bộ nhớ mà CPU muốn đọc hoặc ghi dữ liệu.
- `MBR (Memory Buffer Register)`: Thanh ghi đệm bộ nhớ, dùng để lưu dữ liệu được đọc từ bộ nhớ hoặc chuẩn bị ghi vào bộ nhớ.
- `A (Accumulator Register)`: Thanh ghi tích lũy, lưu trữ kết quả trung gian của các phép tính toán trong quá trình xử lý.
- `Y, Z (Temporary Register)`: Thanh ghi tạm thời, dùng để lưu trữ dữ liệu trong các bước trung gian của một phép tính hoặc xử lý.
- `FR (Flag Register)`: Thanh ghi cờ, lưu trạng thái của CPU (ví dụ: cờ zero, cờ carry) để hỗ trợ xử lý các điều kiện rẽ nhánh hoặc phép toán.
- `ALU (Arithmetic and Logic Unit)`: Bộ tính toán và logic, thực hiện các phép toán số học (cộng, trừ, nhân, chia) và logic (và, hoặc, phủ định).

2. **Các kết nối và Bus**:

- `A Bus (Address Bus)`: Truyền địa chỉ giữa các thành phần, đặc biệt là giữa PC, MAR và bộ nhớ.
- `D Bus (Data Bus)`: Truyền dữ liệu giữa các thanh ghi, ALU, và bộ nhớ hoặc thiết bị ngoại vi.

3. **Luồng hoạt động cơ bản**:

- Lệnh được nạp từ bộ nhớ vào IR thông qua MAR và MBR.
- PC được sử dụng để giữ địa chỉ của lệnh tiếp theo.
- Bộ điều khiển CU giải mã lệnh từ IR và điều phối hoạt động của các thanh ghi, bus, và ALU để thực hiện lệnh.
- ALU thực hiện các phép toán số học/logic dựa trên dữ liệu từ các thanh ghi như - A, Y, Z, và trạng thái được lưu trong FR.

**Tóm tắt ý nghĩa**: Sơ đồ này giúp minh họa cách CPU hoạt động, tập trung vào các bước chính của chu trình lệnh: nạp lệnh, giải mã, và thực thi. Các bus và thanh ghi đóng vai trò quan trọng trong việc lưu trữ và truyền dữ liệu nhanh chóng giữa các thành phần trong CPU.

---

## 3. Cấu trúc cơ bản của CPU

![Hình 3.3: Sơ đồ cấu trúc cơ bản của CPU](../Images/Hinh3.3.png)

Sơ đồ cấu trúc cơ bản của CPU trong hình minh họa các thành phần chính và cách chúng tương tác qua các bus:

1. **Các thành phần chính của CPU**:

- Đơn vị điều khiển (CU - Control Unit):

  - Điều phối hoạt động của các thành phần khác trong CPU.
  - Chịu trách nhiệm giải mã lệnh và điều khiển luồng dữ liệu trong và ngoài CPU.

- Đơn vị số học và logic (ALU - Arithmetic and Logic Unit):

  - Thực hiện các phép toán số học (như cộng, trừ) và logic (như AND, OR).
  - Là thành phần xử lý chính trong CPU.

- Tập các thanh ghi (RF - Register File):

  - Là các bộ nhớ nhỏ, tốc độ cao bên trong CPU.
  - Lưu trữ dữ liệu tạm thời trong quá trình thực hiện lệnh.

- Đơn vị nối ghép bus (BIU - Bus Interface Unit):

  - Đóng vai trò trung gian giữa CPU và các thiết bị bên ngoài qua hệ thống bus.
  - Đảm bảo giao tiếp dữ liệu, địa chỉ, và điều khiển.

2. **Các loại bus**:

- Bus điều khiển: Truyền tín hiệu điều khiển từ CU tới các thành phần khác và thiết bị ngoại vi.
- Bus dữ liệu: Truyền dữ liệu giữa CPU và bộ nhớ hoặc thiết bị I/O.
- Bus địa chỉ: Truyền địa chỉ bộ nhớ hoặc thiết bị ngoại vi để đọc hoặc ghi dữ liệu.

3. **Cách hoạt động cơ bản**:

- CU điều khiển luồng dữ liệu giữa các thanh ghi trong RF, ALU, và bộ nhớ ngoài qua BIU.
- Dữ liệu và địa chỉ được truyền qua các bus tương ứng.
- ALU xử lý dữ liệu, và kết quả được lưu trữ trong RF hoặc ghi vào bộ nhớ.

---

## 4. Hoạt động của CPU

### 4.1. Nhiệm vụ của CPU

- Nhận lệnh (Fetch Instruction): CPU đọc lệnh từ bộ nhớ.
- Giải mã lệnh (Decode Instruction): Xác định thao tác mà lệnh yêu cầu.
- Nhận dữ liệu (Fetch Data): Nhận dữ liệu từ bộ nhớ hoặc các cổng vào-ra.
- Xử lý dữ liệu (Process Data): Thực hiện phép toán số học hay phép toán logic với các dữ liệu.
- Ghi dữ liệu (Write Data): Ghi dữ liệu ra bộ nhớ hay cổng vào-ra.
