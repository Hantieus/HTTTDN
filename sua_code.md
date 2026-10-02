# BÁO CÁO CẬP NHẬT VÀ SỬA LỖI Ô CODE CUỐI CÙNG (BACKPROPAGATION)

---

## 1. Đoạn code hoàn chỉnh sau khi sửa (Ô cuối cùng)

```python
# =====================================================================
# THIẾT LẬP SIÊU THAM SỐ VÀ HUẤN LUYỆN MÔ HÌNH BACKPROPAGATION
# =====================================================================

# 1. Khởi tạo số lượng Epochs và Learning Rate phù hợp
epochs = 10000
learning_rate = 0.1

# 2. Khởi tạo kích thước cho các lớp (Input Layer, Hidden Layer, Output Layer)
input_dim = X.shape[1]    # Số đặc trưng đầu vào (2 đặc trưng cho dữ liệu make_circles)
hidden_dim = 4            # Số lượng neuron trong lớp ẩn (Hidden Layer)
output_dim = 1           # Số lượng neuron lớp đầu ra (Phân loại nhị phân)

# 3. Khởi tạo ngẫu nhiên Trọng số (Weights) và Bias
np.random.seed(42)
W1 = np.random.randn(input_dim, hidden_dim) * 0.01
b1 = np.zeros((1, hidden_dim))

W2 = np.random.randn(hidden_dim, output_dim) * 0.01
b2 = np.zeros((1, output_dim))

# Hàm Kích hoạt Sigmoid và Đạo hàm của Sigmoid
def sigmoid(x):
    return 1 / (1 + np.exp(-x))

def sigmoid_derivative(x):
    return x * (1 - x)

# 4. Vòng lặp huấn luyện (Training Loop)
losses = []

for epoch in range(epochs):
    # -----------------------------------------------------------------
    # A. Lan truyền tiến (Forward Propagation)
    # -----------------------------------------------------------------
    Z1 = np.dot(X, W1) + b1
    A1 = sigmoid(Z1)
    
    Z2 = np.dot(A1, W2) + b2
    A2 = sigmoid(Z2)
    
    # Tính toán giá trị Mất mát (Binary Cross-Entropy Loss)
    m = Y.shape[0]
    loss = -np.mean(Y * np.log(A2 + 1e-8) + (1 - Y) * np.log(1 - A2 + 1e-8))
    losses.append(loss)
    
    # -----------------------------------------------------------------
    # B. Lan truyền ngược (Backpropagation)
    # -----------------------------------------------------------------
    # Tính đạo hàm cho Lớp Đầu Ra (Output Layer)
    dZ2 = A2 - Y
    dW2 = (1 / m) * np.dot(A1.T, dZ2)
    db2 = (1 / m) * np.sum(dZ2, axis=0, keepdims=True)
    
    # Tính đạo hàm cho Lớp Ẩn (Hidden Layer)
    dA1 = np.dot(dZ2, W2.T)
    dZ1 = dA1 * sigmoid_derivative(A1)
    dW1 = (1 / m) * np.dot(X.T, dZ1)
    db1 = (1 / m) * np.sum(dZ1, axis=0, keepdims=True)
    
    # -----------------------------------------------------------------
    # C. Cập nhật Trọng số và Bias (Gradient Descent Update)
    # -----------------------------------------------------------------
    W2 -= learning_rate * dW2
    b2 -= learning_rate * db2
    W1 -= learning_rate * dW1
    b1 -= learning_rate * db1
    
    # In ra giá trị Mất mát định kỳ
    if (epoch + 1) % 1000 == 0:
        print(f"Epoch {epoch + 1}/{epochs} - Loss: {loss:.4f}")

# 5. Trực quan hóa ranh giới phân biệt (Decision Boundary)
plot_decision_boundary(lambda x: sigmoid(np.dot(sigmoid(np.dot(x, W1) + b1), W2) + b2) > 0.5, X, Y)
```

---

## 2. Giải thích chi tiết nguyên nhân lỗi và cách xử lý

### A. Nguyên nhân gây ra lỗi trong ô code gốc:
1. **Sai lệch kích thước ma trận (Shape Mismatch):** Khi nhân ma trận giữa ma trận đầu vào $X$ và $W_1$ hoặc giữa $A_1$ và $W_2$, việc thiếu chuyển vị (`.T`) làm cho các phép nhân `np.dot` không đúng kích thước $m \times n$.
2. **Sai công thức tính Gradient (Backpropagation Error):** Ở bước lan truyền ngược, việc tính $\text{d}Z_1$ từ $\text{d}Z_2$ bị nhầm lẫn giữa tích ma trận (Matrix Multiplication) và tích element-wise (Hadamard Product) với đạo hàm hàm kích hoạt $\sigma'(A_1)$.
3. **Cập nhật sai dấu Gradient:** Đôi khi câu lệnh cập nhật bị ghi nhầm dấu cộng (`+=`) thay vì dấu trừ (`-=`), dẫn đến thuật toán không tối ưu mà làm tăng hàm mất mát (Gradient Ascent thay vì Gradient Descent).
4. **Tràn số khi tính Logarithm:** Trong biểu thức tính Cross-Entropy Loss, giá trị $A_2$ tiệm cận $0$ hoặc $1$ có thể gây ra lỗi $\log(0)$ (kết quả trả về `NaN`).

---

### B. Các bước khắc phục và tối ưu:
1. **Định hình lại các phép nhân ma trận:**
   * $dW_2 = \frac{1}{m} A_1^T \cdot dZ_2$
   * $dZ_1 = (dZ_2 \cdot W_2^T) \odot \sigma'(A_1)$
   * $dW_1 = \frac{1}{m} X^T \cdot dZ_1$
2. **Xử lý ổn định số học (Numerical Stability):**
   * Bổ sung hằng số xấp xỉ nhỏ `1e-8` vào biểu thức hàm mất mát $\log(A_2 + 1e-8)$ để tránh lỗi chia/lấy log cho 0.
3. **Cập nhật quy tắc Gradient Descent đúng quy chuẩn:**
   * Sử dụng dấu trừ: $W = W - \alpha \times dW$ và $b = b - \alpha \times db$.
4. **Gắn kết với hàm vẽ đồ thị:**
   * Định nghĩa đường phân chia dữ liệu bằng hàm `lambda` nhận dữ liệu đầu vào và trả về dự đoán nhị phân ($> 0.5$) để tương thích trực tiếp với hàm `plot_decision_boundary`.