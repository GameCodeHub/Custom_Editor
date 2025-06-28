# Bài 2: Tạo Custom Inspector Cơ Bản

## Giới thiệu
Custom Inspector là công cụ mạnh mẽ trong Unity, cho phép bạn tạo giao diện tùy chỉnh cho các script trong cửa sổ **Inspector**. Điều này giúp tăng tính trực quan và cải thiện trải nghiệm chỉnh sửa thuộc tính.

---

## Mục tiêu bài học
- Hiểu cách tạo một Custom Inspector.
- Tùy chỉnh giao diện của cửa sổ **Inspector**.
- Sử dụng các thành phần cơ bản như `GUILayout` và `EditorGUILayout`.

---

## Code: Tạo Custom Inspector
Dưới đây là ví dụ cơ bản về cách tạo Custom Inspector hiển thị các trường dữ liệu và một nút trong cửa sổ **Inspector**:

### Custom Inspector Script
```csharp
using UnityEngine;
using UnityEditor;

[CustomEditor(typeof(PlayerStats))] // Gắn Custom Inspector vào script PlayerStats
public class PlayerStatsEditor : Editor
{
    public override void OnInspectorGUI()
    {
        // Hiển thị nội dung mặc định
        DrawDefaultInspector();

        // Tạo một dòng phân cách
        EditorGUILayout.LabelField("Tùy chỉnh Inspector", EditorStyles.boldLabel);

        // Tạo một nút trong Inspector
        if (GUILayout.Button("Tăng Điểm"))
        {
            PlayerStats playerStats = (PlayerStats)target; // Lấy đối tượng PlayerStats hiện tại
            playerStats.IncreaseScore(10); // Gọi hàm tăng điểm
            Debug.Log($"Điểm của {playerStats.playerName} đã tăng thêm 10!");
        }
    }
}
```
### Script PlayerStats
```
using UnityEngine;

public class PlayerStats : MonoBehaviour
{
    public string playerName;
    public int playerScore;

    // Hàm tăng điểm
    public void IncreaseScore(int amount)
    {
        playerScore += amount;
    }
}
```
## Hướng dẫn thực hành

1. **Tạo hai script:**
   - `PlayerStats.cs`: Đặt trong thư mục bất kỳ.
   - `PlayerStatsEditor.cs`: Đặt trong thư mục **Editor**.

2. **Gán component `PlayerStats`** vào một GameObject trong Unity.

3. Mở cửa sổ **Inspector** và kiểm tra các thay đổi.

4. Nhấn nút **"Tăng Điểm"** và mở **Console** để xem thông báo.

---

## Kết quả mong đợi

- Cửa sổ **Inspector** hiển thị thông tin của `PlayerStats` cùng với một dòng nhãn tùy chỉnh và một nút.
- Khi nhấn nút **"Tăng Điểm"**, điểm số của người chơi tăng lên và thông báo hiển thị trong **Console**.

![image](https://github.com/user-attachments/assets/4888688d-5c24-4fd9-a148-a9a1328a5dce)

---

## Tổng kết

**Custom Inspector** giúp tạo giao diện chỉnh sửa thuộc tính độc đáo và thân thiện hơn. Với `EditorGUILayout`, bạn có thể dễ dàng thêm các thành phần giao diện như:
- Nút
- Nhãn
- Thanh trượt
- Thậm chí tạo toàn bộ bố cục phức tạp

---

👉 **Bài tiếp theo:** Tìm hiểu **EditorGUILayout Properties** để xây dựng giao diện **Inspecto
