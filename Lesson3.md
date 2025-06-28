# Bài 3: Tìm hiểu `EditorGUILayout` và `EditorGUI`

---

## Mục tiêu

Hiểu sự khác biệt giữa `EditorGUILayout` và `EditorGUI`, từ đó lựa chọn công cụ phù hợp để xây dựng giao diện tùy chỉnh trong Unity Editor.

---

## Nội dung bài học

### 1. **EditorGUILayout**  
- **Đặc điểm:**
  - Giao diện được tạo tự động với bố cục dựa trên nhóm dọc (Vertical Group).
  - Đơn giản hơn, thích hợp để tạo giao diện nhanh chóng.
  - Tự động điều chỉnh kích thước và căn chỉnh.

- **Ví dụ:**
  ```csharp
  using UnityEditor;
  using UnityEngine;

  [CustomEditor(typeof(PlayerStats))]
  public class PlayerStatsEditor : Editor
  {
      public override void OnInspectorGUI()
      {
          EditorGUILayout.LabelField("EditorGUILayout Example", EditorStyles.boldLabel);

          EditorGUILayout.BeginVertical("box");
          EditorGUILayout.LabelField("Player Name");
          EditorGUILayout.TextField("Player_001");

          EditorGUILayout.LabelField("Player Level");
          EditorGUILayout.IntField(5);
          EditorGUILayout.EndVertical();
      }
  }
``
## 2. EditorGUI

---

### **Đặc điểm**
- Cung cấp khả năng tùy chỉnh cao hơn với kiểm soát chi tiết về vị trí và kích thước của các thành phần giao diện.
- Yêu cầu chỉ định chính xác vùng hiển thị (`Rect`) cho mỗi thành phần.
- Phù hợp với giao diện phức tạp hoặc cần bố trí chi tiết.

---

### **Ví dụ:**
```csharp
using UnityEditor;
using UnityEngine;

[CustomEditor(typeof(PlayerStats))]
public class PlayerStatsEditor : Editor
{
    public override void OnInspectorGUI()
    {
        Rect rect = GUILayoutUtility.GetRect(100, 20);
        EditorGUI.LabelField(rect, "EditorGUI Example");

        rect.y += 25;
        EditorGUI.TextField(new Rect(rect.x, rect.y, rect.width, 20), "Player Name", "Player_001");

        rect.y += 25;
        EditorGUI.IntField(new Rect(rect.x, rect.y, rect.width, 20), "Player Level", 5);
    }
}
```
## So sánh: `EditorGUILayout` và `EditorGUI`

| **Tiêu chí**          | **EditorGUILayout**         | **EditorGUI**                     |
|------------------------|-----------------------------|------------------------------------|
| **Tự động bố cục**     | Có                         | Không                             |
| **Kiểm soát chi tiết** | Không                      | Có                                |
| **Dễ sử dụng**         | Cao                        | Thấp                              |
| **Tùy chỉnh giao diện**| Hạn chế                    | Cao                               |

---

## Kết luận

- **`EditorGUILayout`**: Lựa chọn lý tưởng cho các giao diện đơn giản, dễ tạo và nhanh chóng.
- **`EditorGUI`**: Phù hợp với giao diện cần độ tùy chỉnh cao và kiểm soát chi tiết về bố trí.

---

👉 **Bài tiếp theo:** Tạo **Custom Editor Window** bằng `EditorGUILayout` và `EditorGUI`.
