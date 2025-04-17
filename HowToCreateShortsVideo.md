# Hướng Dẫn Chi Tiết Tạo Video Shorts Với MoneyPrinterTurbo API

Hướng dẫn này giả định bạn đã cài đặt thành công MoneyPrinterTurbo, đã cấu hình API keys trong file `config.toml`, và đang chạy Docker hoặc đã cài đặt đầy đủ các phụ thuộc cần thiết. Dưới đây là quy trình chi tiết từng bước để tạo video shorts thông qua gọi APIs.

## Mục Lục

1. [Khởi động API Server](#khởi-động-api-server)
2. [Tìm Hiểu Các Endpoints](#tìm-hiểu-các-endpoints)
3. [Quy Trình Tạo Video Step-by-Step](#quy-trình-tạo-video-step-by-step)
   - [Bước 1: Tạo Task Mới](#bước-1-tạo-task-mới)
   - [Bước 2: Theo Dõi Trạng Thái Task](#bước-2-theo-dõi-trạng-thái-task)
   - [Bước 3: Tải Video Xuống](#bước-3-tải-video-xuống)
4. [Các Tham Số API Chi Tiết](#các-tham-số-api-chi-tiết)
5. [Ví Dụ Gọi API Thông Qua Các Công Cụ](#ví-dụ-gọi-api-thông-qua-các-công-cụ)
6. [Xử Lý Lỗi Phổ Biến](#xử-lý-lỗi-phổ-biến)
7. [Tối Ưu Quy Trình](#tối-ưu-quy-trình)

## Khởi động API Server

Nếu sử dụng Docker:
```shell
docker compose up -d  # Chạy ở chế độ nền
```

Nếu cài đặt thủ công:
```shell
python main.py
```

API Server mặc định chạy tại:
- Nếu sử dụng Docker: http://0.0.0.0:8080
- Nếu cài đặt thủ công: http://127.0.0.1:8080

## Tìm Hiểu Các Endpoints

Truy cập tài liệu API tự động được tạo:
- Swagger UI: http://127.0.0.1:8080/docs
- ReDoc: http://127.0.0.1:8080/redoc

Các endpoints chính:
- `POST /api/v1/videos`: Tạo task mới để tạo video hoàn chỉnh
- `POST /api/v1/subtitle`: Tạo phụ đề cho video
- `POST /api/v1/audio`: Tạo âm thanh cho video
- `GET /api/v1/tasks/{task_id}`: Lấy thông tin về task cụ thể
- `GET /api/v1/tasks`: Liệt kê tất cả các task
- `DELETE /api/v1/tasks/{task_id}`: Xóa task và các tệp liên quan
- `GET /api/v1/stream/{file_path:path}`: Phát trực tuyến video
- `GET /api/v1/download/{file_path:path}`: Tải xuống video hoàn chỉnh

## Quy Trình Tạo Video Step-by-Step

### Bước 1: Tạo Task Mới

```http
POST /api/v1/videos
Content-Type: application/json

{
  "topic": "Lợi ích của việc tập thể dục mỗi ngày",
  "aspect_ratio": "9:16",
  "language": "vi",
  "duration": 60,
  "voice_name": "vi-VN-HoaiMyNeural-Female",
  "generate_subtitles": true,
  "font_name": "Arial-Bold.ttf",
  "subtitle_position": "bottom",
  "subtitle_color": "#FFFFFF",
  "subtitle_stroke_color": "#000000",
  "subtitle_stroke_width": 1.5,
  "font_size": 65,
  "generate_script": true,
  "script_length": "medium",
  "background_music_volume": 0.15,
  "background_music": "random"
}
```

**Cách gọi bằng curl:**

```shell
curl -X 'POST' \
  'http://127.0.0.1:8080/api/v1/videos' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "topic": "Lợi ích của việc tập thể dục mỗi ngày",
  "aspect_ratio": "9:16",
  "language": "vi",
  "duration": 60,
  "voice_name": "vi-VN-HoaiMyNeural-Female",
  "generate_subtitles": true,
  "font_name": "Arial-Bold.ttf",
  "subtitle_position": "bottom",
  "subtitle_color": "#FFFFFF",
  "subtitle_stroke_color": "#000000",
  "subtitle_stroke_width": 1.5,
  "font_size": 65,
  "generate_script": true,
  "script_length": "medium",
  "background_music_volume": 0.15,
  "background_music": "random"
}'
```

API sẽ trả về một response với `task_id`, ví dụ:

```json
{
  "status": 200,
  "message": "success",
  "data": {
    "task_id": "2024071012345678",
    "request_id": "c4dfe8a3-7b3a-4ff5-8f1e-ee65e12d67bf",
    "params": {
      "topic": "Lợi ích của việc tập thể dục mỗi ngày",
      "aspect_ratio": "9:16",
      "language": "vi",
      "duration": 60,
      "voice_name": "vi-VN-HoaiMyNeural-Female",
      "generate_subtitles": true,
      "font_name": "Arial-Bold.ttf",
      "subtitle_position": "bottom",
      "subtitle_color": "#FFFFFF",
      "subtitle_stroke_color": "#000000",
      "subtitle_stroke_width": 1.5,
      "font_size": 65,
      "generate_script": true,
      "script_length": "medium",
      "background_music_volume": 0.15,
      "background_music": "random"
    }
  }
}
```

Lưu lại `task_id` này để kiểm tra trạng thái trong bước tiếp theo.

### Bước 2: Theo Dõi Trạng Thái Task

```http
GET /api/v1/tasks/{task_id}
```

**Cách gọi bằng curl:**

```shell
curl -X 'GET' \
  'http://127.0.0.1:8080/api/v1/tasks/2024071012345678' \
  -H 'accept: application/json'
```

Response sẽ hiển thị trạng thái hiện tại và tiến độ:

```json
{
  "status": 200,
  "message": "success",
  "data": {
    "task_id": "2024071012345678",
    "state": 1,
    "progress": 70,
    "step": "generating_video",
    "message": "Đang tạo video...",
    "videos": [
      "http://127.0.0.1:8080/api/v1/tasks/2024071012345678/final-1.mp4"
    ],
    "combined_videos": [
      "http://127.0.0.1:8080/api/v1/tasks/2024071012345678/combined-1.mp4"
    ],
    "created_at": "2024-07-10T12:34:56.789Z",
    "updated_at": "2024-07-10T12:40:45.123Z"
  }
}
```

Các trạng thái (`state`) có thể có:
- `0`: Đang chờ xử lý (pending)
- `1`: Đang xử lý (processing)
- `2`: Hoàn thành (completed)
- `-1`: Thất bại (failed)

Các bước xử lý (`step`) có thể có:
- `generating_script`: Đang tạo kịch bản bằng AI
- `generating_voice`: Đang tổng hợp giọng nói
- `downloading_videos`: Đang tải video từ Pexels/Pixabay
- `generating_subtitles`: Đang tạo phụ đề
- `generating_video`: Đang tạo video hoàn chỉnh
- `completed`: Hoàn thành

Tiếp tục kiểm tra trạng thái cho đến khi `state` là `2` (completed).

### Bước 3: Tải Video Xuống

Sau khi task hoàn thành (`state` = `2`), bạn có thể tải xuống video từ URL được trả về trong trường `videos` của response. Hoặc bạn có thể sử dụng endpoint chuyên dụng `/api/v1/download`:

```http
GET /api/v1/download/{task_id}/final-1.mp4
```

**Cách gọi bằng curl:**

```shell
curl -X 'GET' \
  'http://127.0.0.1:8080/api/v1/download/2024071012345678/final-1.mp4' \
  -H 'accept: application/octet-stream' \
  --output video.mp4
```

Lệnh này sẽ tải xuống video và lưu thành file `video.mp4`.

Ngoài ra, bạn có thể sử dụng endpoint phát trực tuyến để xem video trực tiếp:

```http
GET /api/v1/stream/{task_id}/final-1.mp4
```

## Các Tham Số API Chi Tiết

### Tham Số Khi Tạo Task Mới (POST /api/v1/videos)

| Tham số | Loại | Mô tả | Giá trị mặc định |
|---------|------|-------|-----------------|
| `topic` | string | Chủ đề hoặc từ khóa cho video | (bắt buộc) |
| `aspect_ratio` | string | Tỷ lệ khung hình | "9:16" (có thể là "9:16" hoặc "16:9") |
| `language` | string | Ngôn ngữ kịch bản | "en" (có thể là "en", "zh", "vi", etc.) |
| `duration` | integer | Thời lượng mỗi đoạn video (giây) | 60 |
| `voice_name` | string | Tên giọng đọc | Tùy thuộc vào ngôn ngữ |
| `generate_subtitles` | boolean | Có tạo phụ đề không | true |
| `font_name` | string | Phông chữ phụ đề | "Arial-Bold.ttf" |
| `subtitle_position` | string | Vị trí phụ đề | "bottom" (có thể là "top", "middle", "bottom") |
| `subtitle_color` | string | Màu phụ đề (HEX) | "#FFFFFF" |
| `subtitle_stroke_color` | string | Màu viền phụ đề (HEX) | "#000000" |
| `subtitle_stroke_width` | number | Độ rộng viền phụ đề | 1.5 |
| `font_size` | integer | Kích thước phông chữ | 65 |
| `generate_script` | boolean | Tự động tạo kịch bản bằng AI | true |
| `custom_script` | string | Kịch bản tùy chỉnh (nếu generate_script=false) | "" |
| `script_length` | string | Độ dài kịch bản | "medium" (có thể là "short", "medium", "long") |
| `background_music_volume` | number | Âm lượng nhạc nền (0.0-1.0) | 0.15 |
| `background_music` | string | Tên file nhạc nền hoặc "random" | "random" |

### Tiếng Việt và Các Giọng Đọc Tiếng Việt

Nếu muốn tạo video tiếng Việt, sử dụng:
- `language`: "vi"
- `voice_name`: Một trong những giọng tiếng Việt sau:
  - "vi-VN-HoaiMyNeural-Female": Giọng nữ Hoài My
  - "vi-VN-NamMinhNeural-Male": Giọng nam Nam Minh

Xem danh sách đầy đủ các giọng đọc tại: https://speech.microsoft.com/portal/voicegallery

## Ví Dụ Gọi API Thông Qua Các Công Cụ

### Python (requests)

```python
import requests
import time
import shutil

# Khởi tạo task mới
api_url = "http://127.0.0.1:8080"
data = {
    "topic": "Lợi ích của việc tập thể dục mỗi ngày",
    "aspect_ratio": "9:16",
    "language": "vi",
    "voice_name": "vi-VN-HoaiMyNeural-Female",
    "background_music": "random"
}

# Bước 1: Tạo task mới
response = requests.post(f"{api_url}/api/v1/videos", json=data)
task = response.json()["data"]
task_id = task["task_id"]
print(f"Đã tạo task: {task_id}")

# Bước 2: Kiểm tra trạng thái
while True:
    response = requests.get(f"{api_url}/api/v1/tasks/{task_id}")
    task_info = response.json()["data"]
    
    state_map = {0: "pending", 1: "processing", 2: "completed", -1: "failed"}
    current_state = state_map.get(task_info.get("state", 0))
    
    print(f"Trạng thái: {current_state}")
    print(f"Tiến trình: {task_info.get('progress', 0)}% - {task_info.get('step', 'N/A')}")
    
    if task_info.get("state") == 2:  # completed
        print("Task đã hoàn thành!")
        break
    elif task_info.get("state") == -1:  # failed
        print("Task thất bại!")
        break
    
    # Chờ 10 giây trước khi kiểm tra lại
    print("Đang chờ...")
    time.sleep(10)

# Bước 3: Tải video
if task_info.get("state") == 2:
    if "videos" in task_info and len(task_info["videos"]) > 0:
        video_url = task_info["videos"][0]
        filename = video_url.split("/")[-1]
        download_url = f"{api_url}/api/v1/download/{task_id}/{filename}"
        response = requests.get(download_url, stream=True)
        with open(f"video_{filename}", "wb") as f:
            shutil.copyfileobj(response.raw, f)
        print(f"Đã tải video xuống: video_{filename}")
```

### JavaScript (fetch)

```javascript
const apiUrl = "http://127.0.0.1:8080";

// Bước 1: Tạo task mới
async function createTask() {
  const response = await fetch(`${apiUrl}/api/v1/videos`, {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json'
    },
    body: JSON.stringify({
      topic: "Lợi ích của việc tập thể dục mỗi ngày",
      aspect_ratio: "9:16",
      language: "vi",
      voice_name: "vi-VN-HoaiMyNeural-Female",
      background_music: "random"
    })
  });
  
  const result = await response.json();
  const task = result.data;
  console.log(`Đã tạo task: ${task.task_id}`);
  return task.task_id;
}

// Bước 2: Kiểm tra trạng thái
async function checkTaskStatus(taskId) {
  const response = await fetch(`${apiUrl}/api/v1/tasks/${taskId}`);
  const result = await response.json();
  const taskInfo = result.data;
  
  const stateMap = {0: "pending", 1: "processing", 2: "completed", "-1": "failed"};
  const currentState = stateMap[taskInfo.state] || "unknown";
  
  console.log(`Trạng thái: ${currentState}`);
  console.log(`Tiến trình: ${taskInfo.progress || 0}% - ${taskInfo.step || 'N/A'}`);
  
  return taskInfo;
}

// Bước 3: Tải video
async function downloadVideo(taskId, filename) {
  window.location.href = `${apiUrl}/api/v1/download/${taskId}/${filename}`;
  console.log(`Đang tải video...`);
}

// Quy trình hoàn chỉnh
async function runVideoCreationProcess() {
  try {
    // Tạo task
    const taskId = await createTask();
    
    // Kiểm tra trạng thái mỗi 10 giây
    let taskInfo;
    do {
      await new Promise(resolve => setTimeout(resolve, 10000));
      taskInfo = await checkTaskStatus(taskId);
    } while (taskInfo.state === 0 || taskInfo.state === 1); // pending hoặc processing
    
    // Tải video nếu thành công
    if (taskInfo.state === 2) { // completed
      console.log("Task đã hoàn thành!");
      if (taskInfo.videos && taskInfo.videos.length > 0) {
        const videoUrl = taskInfo.videos[0];
        const filename = videoUrl.split('/').pop();
        await downloadVideo(taskId, filename);
      }
    } else {
      console.log("Task thất bại!");
    }
  } catch (error) {
    console.error("Lỗi:", error);
  }
}

// Chạy quy trình
runVideoCreationProcess();
```

## Xử Lý Lỗi Phổ Biến

### 1. API Key Không Hợp Lệ

**Lỗi:** API trả về mã lỗi 401 hoặc 403
**Giải pháp:** Kiểm tra lại API keys trong file `config.toml`

### 2. Không Tìm Thấy Video Phù Hợp

**Lỗi:** Task thất bại với thông báo "Không tìm thấy video phù hợp"
**Giải pháp:** 
- Thử sử dụng từ khóa khác, cụ thể hơn
- Kiểm tra xem có vấn đề với Pexels API hoặc Pixabay API không
- Thử chuyển `video_source` trong config.toml sang nguồn khác nếu có sẵn

### 3. Lỗi Tạo Phụ Đề

**Lỗi:** Task thất bại ở bước "generating_subtitles"
**Giải pháp:**
- Thử đổi `subtitle_provider` từ "whisper" sang "edge" hoặc ngược lại
- Nếu không cần phụ đề, đặt `generate_subtitles` thành `false`

### 4. Lỗi Tổng Hợp Giọng Nói

**Lỗi:** Task thất bại ở bước "generating_voice"
**Giải pháp:**
- Kiểm tra xem `voice_name` có hợp lệ và tương thích với `language` không
- Nếu sử dụng Azure TTS, kiểm tra lại Azure API key

## Tối Ưu Quy Trình

### 1. Tạo Nhiều Video Cùng Lúc

MoneyPrinterTurbo hỗ trợ xử lý nhiều task cùng lúc. Bạn có thể gửi nhiều yêu cầu tạo task với các chủ đề khác nhau và theo dõi tiến độ của chúng.

### 2. Thử Nghiệm Tối Ưu

- **Kịch bản:** Bắt đầu với `generate_script: true` và `script_length: "short"` để tạo nhanh. Khi tìm được chủ đề phù hợp, hãy sử dụng `script_length: "medium"` hoặc `"long"` để có nội dung phong phú hơn.
- **Giọng đọc và phụ đề:** Thử nghiệm các giọng đọc khác nhau và kiểm tra tính phù hợp với nội dung video.
- **Thời lượng đoạn:** Điều chỉnh `duration` (thời lượng mỗi đoạn video) để có nhịp độ phù hợp. Giá trị thấp hơn (30-45 giây) tạo nhịp nhanh hơn, giá trị cao hơn (60-90 giây) tạo cảm giác chậm rãi hơn.

### 3. Tái Sử Dụng Kịch Bản

Nếu bạn đã có kịch bản chất lượng cao, hãy sử dụng:
```json
{
  "generate_script": false,
  "custom_script": "Kịch bản tùy chỉnh của bạn..."
}
```

---

Đây là Voice Gallery: https://speech.microsoft.com/portal/voicegallery