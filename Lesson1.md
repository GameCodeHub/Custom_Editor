# Bài 1: Khái Niệm UnityEditor Namespace

## UnityEditor Namespace là gì?
`UnityEditor` là một namespace trong Unity cung cấp các công cụ và API để tùy chỉnh và mở rộng Unity Editor. Các tính năng chính bao gồm:  
- **Tạo Custom Inspector:** Tùy chỉnh cách hiển thị và chỉnh sửa thuộc tính trong cửa sổ Inspector.  
- **Tạo Editor Windows:** Cung cấp giao diện riêng để thực hiện các chức năng đặc biệt.  
- **Thêm Menu Items:** Thêm các tùy chọn tùy chỉnh vào Unity Editor.

> **Lưu ý:** Các mã sử dụng `UnityEditor` không hoạt động trong bản build của game. Để tránh lỗi khi xuất bản, các file chứa mã này nên được đặt trong thư mục **Editor**.

---

## Cách sử dụng cơ bản
Trong ví dụ này, bạn sẽ học cách tạo một **Custom Inspector** đơn giản hiển thị nút bấm trong cửa sổ Inspector.

---

### Code: Tùy chỉnh Inspector
```csharp
using UnityEngine;
using UnityEditor; // Import UnityEditor namespace

[CustomEditor(typeof(CustomEditorExample))] // Gắn Custom Editor vào một script cụ thể
public class CustomEditorExampleEditor : Editor
{
    public override void OnInspectorGUI()
    {
        // Hiển thị nội dung mặc định của Inspector
        DrawDefaultInspector();

        // Thêm một nút vào cửa sổ Inspector
        if (GUILayout.Button("Hiển thị Thông báo"))
        {
            Debug.Log("Nút đã được nhấn!");
        }
    }
}

// Script mẫu cho Custom Editor
public class CustomEditorExample : MonoBehaviour
{
    public string playerName;
    public int playerScore;
}
```
## Hướng dẫn thực hành
1. Tạo một script mới, đặt tên là `CustomEditorExample.cs`.  
2. Copy đoạn mã trên vào script.  
3. Đảm bảo script nằm trong thư mục **Editor**.  
4. Trong Unity Editor, thêm component `CustomEditorExample` vào một GameObject bất kỳ.  
5. Kiểm tra cửa sổ **Inspector** để thấy nút mới hiển thị.  
6. Nhấn nút và mở **Console** để kiểm tra thông báo.

---

## Kết quả mong đợi
- **Inspector:** Cửa sổ Inspector của GameObject hiển thị một nút mới với nội dung **"Hiển thị Thông báo"**.  
- **Console:** Khi nhấn nút, thông báo xuất hiện trong **Console**.

![Ảnh chụp màn hình 2025-06-28 131400](https://github.com/user-attachments/assets/f3d67cfa-ba14-43b9-98aa-21a00621dca3)

---

## Tổng kết
`UnityEditor` giúp mở rộng và tùy chỉnh Unity Editor, tăng hiệu quả làm việc và tối ưu hóa quy trình phát triển. Bắt đầu từ các ví dụ cơ bản, bạn sẽ dần dần làm quen với các tính năng nâng cao như tạo công cụ tùy chỉnh hoặc tự động hóa.

---

👉 **Bài tiếp theo:** Tìm hiểu **EditorGUILayout vs EditorGUI** và tạo giao diện tùy chỉnh nâng cao.
