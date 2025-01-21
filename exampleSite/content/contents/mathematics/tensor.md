---
title: Tensor
description: "Tensor và tensor field"
params:
  math: true
---

# Tìm hiểu về **Rank-(k,l) Tensors**

Trong hình học vi phân (differential geometry) và đại số đa tuyến (multilinear algebra), bạn thường thấy khái niệm **\((k,l)\)-tensor** — đôi khi còn được gọi là **“rank-(k,l) tensor”**. Nhưng ký hiệu này thật sự có nghĩa là gì, và tại sao có sự nhầm lẫn về thứ như \((1,0)\)-tensor?

Bài viết này nhằm **làm rõ** những hiểu lầm thường gặp về cách **vector** và **covector** liên hệ với ký hiệu **\((k,l)\)-tensor**.

---

## 1. Định nghĩa cơ bản

Một **\((k,l)\)-tensor** trên không gian vectơ \(V\) (trên một trường \(\mathbf{F}\), thường là \(\mathbf{R}\) hoặc \(\mathbf{C}\)) là một ánh xạ đa tuyến tính (multilinear map):

\[
T:\; 
\underbrace{(V^*) \times \cdots \times (V^*)}_{k\text{ lần}}
\;\times\;
\underbrace{V \times \cdots \times V}_{l\text{ lần}}
\;\longrightarrow\;\mathbf{F}.
\]

- **Đa tuyến tính (multilinear)** có nghĩa là \(T\) tuyến tính trên từng biến khi cố định các biến còn lại.  
- **\(V^*\)** là **dual space** (không gian đối ngẫu, chứa **covector**), tức tập tất cả các ánh xạ tuyến tính \(V \to \mathbf{F}\).  
- Hai số nguyên \(k\) và \(l\) biểu thị số lần \(T\) nhận **covector** và **vector** làm đầu vào.

### Tại sao gọi là “\((k,l)\)-tensor”?

- \(k\) đôi khi được gọi là **contravariant rank** (gắn với chỉ số **trên**, “upper indices” trong dạng tọa độ).  
- \(l\) là **covariant rank** (gắn với chỉ số **dưới**, “lower indices”).  

Trong một số tài liệu cũ, người ta dùng cụm “rank-(k,l) object” để nhấn mạnh tổng cộng có \(k + l\) “chỗ” (slots) — \(k\) cho covector, \(l\) cho vector.

---

## 2. Các ví dụ quan trọng

### (0,1)-Tensor = Covector

Một **\((0,1)\)-tensor** lấy **một vector** làm đầu vào rồi trả về một vô hướng (scalar):

\[
T: V \;\longrightarrow\;\mathbf{F}.
\]

Trong ngôn ngữ thông thường, đây chính là một **covector** (hay **1-form**). Ví dụ, một hàm tuyến tính \(\omega(\mathbf{v}) = \alpha \,\bigl(\text{thành phần }x\bigr) + \cdots\) thuộc \(V^*\).

### (1,0)-Tensor = Vector

Một **\((1,0)\)-tensor** lấy **một covector** làm đầu vào và trả về một vô hướng:

\[
T: V^* \;\longrightarrow\;\mathbf{F}.
\]

Bất kỳ ánh xạ tuyến tính \(\phi: V^* \to \mathbf{F}\) nào cũng có thể nhận dạng (isomorphic) với một vector trong \(V\) (thông qua đồng cấu kép, **double dual** \((V^*)^* \cong V\) nếu \(V\) hữu hạn chiều).

Đây là lý do **một \((1,0)\)-tensor về bản chất tương đương với một vector**.

### (0,2)-Tensor = Bilinear Form trên \(V\)

Một **\((0,2)\)-tensor** lấy **hai vector** làm đầu vào và trả về một số thực:

\[
T: V \times V \;\longrightarrow\;\mathbf{R}.
\]

Ví dụ điển hình là **tích vô hướng** (dot product) hoặc **bất kỳ dạng song tuyến (bilinear form)** nào:

\[
T(\mathbf{v}, \mathbf{w}) 
\;=\; 
g_{ij}\,v^i\,w^j
\]
(khi biểu diễn bằng tọa độ), thỏa mãn tính tuyến tính trên cả \(\mathbf{v}\) lẫn \(\mathbf{w}\).

### (2,2)-Tensor

Một **\((2,2)\)-tensor** lấy **hai covector** và **hai vector** làm đầu vào, trả về một số thực:

\[
T: (V^*)^2 \times V^2 \;\longrightarrow\;\mathbf{R}.
\]

Một ví dụ cụ thể:

\[
T(\alpha, \beta;\; \mathbf{v}, \mathbf{w}) \;=\; \alpha(\mathbf{v}) \,\beta(\mathbf{w}).
\]

Ở đây, \(\alpha(\mathbf{v})\) và \(\beta(\mathbf{w})\) đều là những số thực, lấy tích của chúng cũng là một số thực.

---

## 3. Tại sao lại có nhầm lẫn?

1. **Lẫn lộn “slots” với “loại”**  
   - Người ta dễ nghĩ “\((k,l)\) = k\text{ vector} + l\text{ covector}”. Nhưng trong định nghĩa chuẩn, **\(k\)** là số lần nhận **covector** (\(V^*\)), còn **\(l\)** là số lần nhận **vector** (\(V\)).  
   - Điều này có thể “ngược” so với trực giác ban đầu về ký hiệu.

2. **“(1,0)” có phải nghĩa là 1 “chỗ” cho vector?**  
   - Thật ra, \((1,0)\) đồng nghĩa với “1 contravariant slot,” tức là đầu vào từ **\(V^*\)** chứ **không** phải \(V\). Vì nó “ăn” một covector, nên tương đương với một **vector** trong \(V\) (nhờ \((V^*)^* \cong V\)).  
   - Trong khi đó, \((0,1)\) nghĩa là “1 covariant slot” (đầu vào từ \(V\)), nên đó là một **covector**.

3. **Rank của Tensor vs. Rank của Ma Trận**  
   - “Rank” trong ma trận (matrix) nghĩa là “số chiều không gian ảnh” (dimension of the image). Đây là khái niệm **hoàn toàn khác** với “rank-(k,l)” của tensor.

---

## 4. Bảng tóm tắt

| **Loại Tensor** | **Định nghĩa hình thức**                                | **Tương đương với**                  | **Ví dụ**                                                   |
|:---------------:|:-------------------------------------------------------:|:-------------------------------------:|:-----------------------------------------------------------:|
| \((0,0)\)       | Ánh xạ không có đầu vào                                 | Số vô hướng (real number)            | Đơn giản là một số thực                                     |
| \((0,1)\)       | \(V \to \mathbb{R}\)                                    | **Covector (1-form)**                | Hàm tuyến tính \(\omega(\mathbf{v})\)                       |
| \((1,0)\)       | \(V^* \to \mathbb{R}\)                                  | **Vector** (thông qua double-dual)    | \(\phi(\alpha)\), \(\alpha \in V^*\)                         |
| \((0,2)\)       | \(V\times V \to \mathbb{R}\)                            | **Bilinear form**                     | Tích vô hướng, metric, v.v.                                 |
| \((1,1)\)       | \(V^*\times V \to \mathbb{R}\)                          | Ánh xạ tuyến tính \(V \to V\)         | Dạng ma trận trong hệ tọa độ                                |
| \((2,2)\)       | \((V^*)^2 \times V^2 \to \mathbb{R}\)                   | Kiểu “phức tạp” hơn                   | \(T(\alpha,\beta;\mathbf{v},\mathbf{w}) = \alpha(\mathbf{v})\beta(\mathbf{w})\)                  |

---

## 5. Những điểm rút ra

1. **\((k,l)\)-tensor** nghĩa là nhận \(k\) đầu vào từ \(V^*\) (**covector**) và \(l\) đầu vào từ \(V\) (**vector**).  
2. **“\((1,0)\)-tensor” là một vector**, vì nó là ánh xạ \(V^* \to \mathbb{R}\) và nhờ \((V^*)^* \cong V\), ta xác định được nó với một vector duy nhất trong \(V\).  
3. **“\((0,1)\)-tensor” là một covector**, tức là **1-form**.  
4. Từ “**rank**” ở đây nói về số lượng slots “contravariant” và “covariant”, **không** giống với “rank của ma trận”.  
5. Khi viết ra dạng tọa độ (coordinate expression), chỉ số **trên** thường đại diện cho các slot covariant, và chỉ số **dưới** đại diện cho các slot vector, nên cảm giác bị “ngược” nếu chưa quen.

---

# Lời kết

Mỗi khi bạn gặp **rank-(k,l) tensors**:

- Hãy nhớ định nghĩa: nó là ánh xạ đa tuyến tính với \(k\) đầu vào từ \(V^*\) và \(l\) đầu vào từ \(V\).  
- Đừng nhầm “\((1,0)\) nghĩa là 1 slot cho vector.” Thật ra “1” chỉ số contravariant đồng nghĩa với **một slot cho covector**, khiến tensor tương đương với một vector.  

Với cách nhìn này, bạn sẽ nắm bắt ký hiệu **tensor** một cách tự tin hơn!
