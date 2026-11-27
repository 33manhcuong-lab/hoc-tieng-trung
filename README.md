# 学中文 · Chinese Learning Studio

Website học từ vựng tiếng Trung (HSK 1–6 và từ vựng công xưởng) dành cho người Việt, giao diện **Blue Glass** hiện đại, chạy hoàn toàn trên trình duyệt, không cần máy chủ hay cơ sở dữ liệu.

🔗 Trang web: <https://33manhcuong-lab.github.io/hoc-tieng-trung/>

## Tính năng

**Học từ vựng**
- Thẻ lật hiển thị chữ Hán, pinyin, nghĩa tiếng Việt, Hán Việt, câu ví dụ (kèm pinyin và nghĩa), ghi chú phân biệt và icon minh họa.
- Lọc theo cấp độ (HSK 1–6, Công xưởng), tìm kiếm theo chữ Hán, pinyin hoặc nghĩa, phân trang 60 từ mỗi trang.
- Nút bật/tắt pinyin (拼), chế độ sáng/tối.
- Nhập trực tiếp câu ví dụ, ghi chú và emoji ngay trên thẻ, rồi xuất ra file `hsk-words.json`.

**Luyện tập**
- **Quiz** chọn nghĩa đúng cho chữ Hán, có chế độ đếm ngược (cài số giây trước khi làm, hết giờ tự sang câu khác) và thao tác hoàn toàn bằng phím.
- **Luyện gõ chữ Hán**: nhìn nghĩa tiếng Việt, gõ chữ Hán (cần bộ gõ Pinyin), đúng thì tự chuyển từ.
- **Ôn tập thông minh** theo hộp Leitner (6 hộp, nhắc lại sau 0, 1, 3, 7, 16, 35 ngày). Từ sai trong Quiz hoặc Luyện gõ tự vào danh sách ôn. Chấm mỗi từ: Quên, Khó nhớ, Nhớ.

**Theo dõi tiến độ**
- Dashboard: số từ cần ôn, đang học, đã thuộc, biểu đồ lượt luyện 7 ngày, lịch tháng, chuỗi ngày học liên tiếp, từ của ngày.
- Mục tiêu hằng ngày có vòng tiến độ và pháo giấy khi hoàn thành.
- Thanh tiến độ cho từng cấp độ (tỷ lệ từ đã đưa vào ôn tập).

**Đăng nhập bằng tên**
- Không cần mật khẩu, chỉ cần tên có trong `users.json`. Mỗi người có tiến độ học riêng.

## Cấu trúc thư mục

```
hoc-tieng-trung/
├─ index.html          # toàn bộ giao diện và logic (HTML + CSS + JavaScript thuần)
├─ hsk-words.json      # dữ liệu từ vựng
├─ users.json          # danh sách tên được phép đăng nhập
├─ README.md
└─ images/
   └─ openmoji/        # icon SVG của OpenMoji + LICENSE.txt
```

> `hsk-words.xlsx` (nếu có) chỉ dùng để soạn từ vựng, **không cần** đưa lên web.

## Dữ liệu từ vựng (`hsk-words.json`)

File gồm các nhóm `hsk1` … `hsk6` và `xuong` (công xưởng). Mỗi từ là một đối tượng:

```json
{
  "h": "苹果",
  "p": "píngguǒ",
  "v": "táo",
  "hv": "bình quả",
  "ex": "我喜欢吃苹果。",
  "exv": "Tôi thích ăn táo.",
  "exp": "Wǒ xǐhuan chī píngguǒ.",
  "note": "Ghi chú phân biệt (tùy chọn)",
  "emo": "🍎"
}
```

| Trường | Ý nghĩa | Bắt buộc |
|---|---|---|
| `h` | Chữ Hán | Có |
| `p` | Pinyin | Có |
| `v` | Nghĩa tiếng Việt | Có |
| `hv` | Hán Việt | Không |
| `ex` | Câu ví dụ (chữ Hán) | Không |
| `exv` | Nghĩa câu ví dụ | Không |
| `exp` | Pinyin câu ví dụ | Không |
| `note` | Ghi chú phân biệt | Không |
| `emo` | Emoji minh họa | Không |

Số từ tại lần cập nhật gần nhất: HSK 1: 156 · HSK 2: 362 · HSK 3: 273 · HSK 4: 522 · HSK 5: 1.293 · HSK 6: 2.430 · Công xưởng: 885 (**tổng 5.921 từ**).

### Cách bổ sung và cập nhật từ vựng

**Cách 1. Nhập trên web.** Mở thẻ từ, bấm "＋ Thêm ví dụ và ghi chú", điền rồi Lưu. Nội dung lưu tạm trong trình duyệt. Bấm **"Tải hsk-words.json đã cập nhật"** ở đầu trang Từ vựng, rồi tải file đó lên GitHub ghi đè `hsk-words.json`.

**Cách 2. Soạn trong Excel.** Bảng tính có các cột: Cấp độ, Chữ Hán, Pinyin, Nghĩa tiếng Việt, Hán Việt, Câu ví dụ, Nghĩa câu ví dụ, Ghi chú phân biệt, Pinyin câu ví dụ, Emoji. Thêm từ ở các dòng cuối rồi chuyển dữ liệu sang JSON. Từ có cùng cấp độ, chữ Hán và pinyin được tính là một từ.

Sau khi sửa `hsk-words.json`, nên kiểm tra cú pháp JSON (ví dụ bằng jsonlint.com) trước khi tải lên.

## Icon minh họa (OpenMoji)

- Icon hiển thị từ `images/openmoji/<mã Unicode>.svg`. Ví dụ 🍎 là `1F34E.svg`, ❤️ là `2764-FE0F.svg`.
- Trường `emo` trong JSON cho trang biết từ nào dùng emoji nào. File SVG là hình ảnh tương ứng. Cần **cả hai** để hiện đúng icon OpenMoji.
- Nếu có `emo` mà chưa có file SVG, trang tự hiện emoji của hệ điều hành thay thế.
- Muốn thêm icon mới: tải file SVG trùng tên mã từ thư mục `color/svg` của kho [OpenMoji](https://github.com/hfg-gmuend/openmoji) vào `images/openmoji/`, rồi ghi emoji vào từ đó.

## Đăng nhập (`users.json`)

```json
{
  "users": [
    { "name": "何孟刚", "aliases": ["Hà Mạnh Cương"] },
    { "name": "阮氏娥", "aliases": ["Nguyễn Thị Nga"] }
  ]
}
```

- `name` là tên chính. `aliases` là các cách gõ khác của cùng một người (pinyin, tên tiếng Việt…).
- Khớp tên: bỏ khoảng trắng thừa, không phân biệt hoa thường, không cần gõ dấu tiếng Việt.
- Giữa hai người phải có dấu phẩy `,`, người cuối cùng thì không. Sai cú pháp thì trang báo "File users.json bị lỗi định dạng JSON".
- ⚠️ **Đây không phải bảo mật thật.** Trang tĩnh nên `users.json` công khai, ai cũng đọc được danh sách tên và có thể bỏ qua màn hình đăng nhập. Chức năng này chỉ dùng để nhận diện người học và tách tiến độ riêng.

## Phím tắt

**Quiz — màn hình cài đặt**

| Phím | Tác dụng |
|---|---|
| `0`–`7` hoặc `←` `→` | Chọn cấp độ (0 Tất cả, 1–6 HSK, 7 Công xưởng) |
| `T` | Bật/tắt đếm ngược |
| `+` `-` / `↑` `↓` | Đổi số giây ±1 / ±5 |
| `Enter` | Bắt đầu |

**Quiz — khi làm bài**

| Phím | Tác dụng |
|---|---|
| `1`–`4` hoặc `A`–`D` | Chọn đáp án |
| `Enter`, `Space`, `→` hoặc `N` | Câu tiếp |
| `R` | Làm lại từ đầu |
| `Esc` | Về màn hình cài đặt |

**Luyện gõ**

| Phím | Tác dụng |
|---|---|
| `Ctrl + Enter` | Xem đáp án |
| `Ctrl + →` | Bỏ qua |
| `Ctrl + Shift + Backspace` | Luyện lại |
| `Enter` (sau khi xem đáp án) | Sang từ tiếp theo |

## Dữ liệu lưu trên trình duyệt

Tiến độ học lưu trong `localStorage`, theo từng trình duyệt và từng địa chỉ web, **không** đồng bộ giữa các thiết bị:

| Khóa | Nội dung |
|---|---|
| `hsk-srs-v1:<tên>` | Danh sách Ôn tập |
| `hsk-profile-v1:<tên>` | Tên hiển thị và mục tiêu hằng ngày |
| `hsk-daily-v1:<tên>`, `hsk-history-v1:<tên>` | Lượt luyện hôm nay và lịch sử |
| `hsk-edits-v1` | Ví dụ, ghi chú, emoji bạn nhập trên web (dùng chung) |
| `hsk-session-v1` | Phiên đăng nhập |
| `hsk-theme`, `hsk-pinyin`, `hsk-quiz-timer` | Giao diện sáng/tối, bật/tắt pinyin, cài đặt đếm ngược |

Xóa dữ liệu trình duyệt hoặc đổi máy sẽ mất các dữ liệu trên. Hãy tải `hsk-words.json` định kỳ để giữ phần ví dụ và ghi chú đã nhập.

## Chạy thử trên máy

Không mở `index.html` bằng cách bấm đúp, vì trình duyệt chặn việc đọc file JSON. Hãy chạy một máy chủ cục bộ trong thư mục dự án:

```bash
python -m http.server 8000
```

Rồi mở <http://localhost:8000>.

## Đăng lên GitHub Pages

1. Tải `index.html`, `hsk-words.json`, `users.json` và thư mục `images/` lên repository (nhánh `main`).
2. Vào **Settings → Pages**, chọn nhánh `main`, thư mục `/ (root)`, rồi Save.
3. Sau 1–2 phút trang sẵn sàng. Nhấn `Ctrl + F5` để xóa bộ nhớ đệm khi cập nhật.

Lưu ý: giao diện web của GitHub chỉ nhận tối đa **100 file mỗi lần tải lên**. Thư mục `images/openmoji` có hơn 300 file nên cần chia thành nhiều lần, hoặc dùng GitHub Desktop để đẩy một lần. Giữ nguyên tên file, kể cả chữ hoa, vì máy chủ phân biệt hoa thường.

## Công nghệ

HTML, CSS và JavaScript thuần (không cần build). Phông chữ Noto Serif SC và Be Vietnam Pro từ Google Fonts. Icon minh họa từ OpenMoji.

## Hạn chế đã biết

- Đăng nhập chỉ là cổng nhận diện, không bảo mật (xem phần Đăng nhập).
- Tiến độ lưu theo trình duyệt, chưa có sao lưu hoặc đồng bộ giữa các thiết bị.
- Khoảng 7% số từ có icon (411 từ). Từ trừu tượng và nhiều từ chuyên ngành xưởng không có emoji phù hợp.
- Một phần câu ví dụ và pinyin được nhập từ các file nguồn bên ngoài, chưa được rà soát hết. Bạn có thể sửa trực tiếp trên thẻ.

## Giấy phép và ghi công

- Icon trong `images/openmoji/` là của [OpenMoji](https://openmoji.org), © HfG Schwäbisch Gmünd và những người đóng góp, theo giấy phép [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). Cần giữ phần ghi công này ở cuối trang web và trong file `images/openmoji/LICENSE.txt`.
- Chưa chọn giấy phép cho mã nguồn và dữ liệu từ vựng. Nếu muốn chia sẻ công khai, bạn có thể bổ sung giấy phép tại đây.
