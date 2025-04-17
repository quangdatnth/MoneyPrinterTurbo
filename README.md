<div align="center">
<h1 align="center">MoneyPrinterTurbo 💸</h1>

<p align="center">
  <a href="https://github.com/harry0703/MoneyPrinterTurbo/stargazers"><img src="https://img.shields.io/github/stars/harry0703/MoneyPrinterTurbo.svg?style=for-the-badge" alt="Stargazers"></a>
  <a href="https://github.com/harry0703/MoneyPrinterTurbo/issues"><img src="https://img.shields.io/github/issues/harry0703/MoneyPrinterTurbo.svg?style=for-the-badge" alt="Issues"></a>
  <a href="https://github.com/harry0703/MoneyPrinterTurbo/network/members"><img src="https://img.shields.io/github/forks/harry0703/MoneyPrinterTurbo.svg?style=for-the-badge" alt="Forks"></a>
  <a href="https://github.com/harry0703/MoneyPrinterTurbo/blob/main/LICENSE"><img src="https://img.shields.io/github/license/harry0703/MoneyPrinterTurbo.svg?style=for-the-badge" alt="License"></a>
</p>
<br>
<h3>Tiếng Việt | <a href="README-en.md">English</a> | <a href="README-ch.md">中文</a></h3>
<div align="center">
  <a href="https://trendshift.io/repositories/8731" target="_blank"><img src="https://trendshift.io/api/badge/repositories/8731" alt="harry0703%2FMoneyPrinterTurbo | Trendshift" style="width: 250px; height: 55px;" width="250" height="55"/></a>
</div>
<br>
Chỉ cần cung cấp một <b>chủ đề</b> hoặc <b>từ khóa</b> video, hệ thống sẽ tự động tạo kịch bản video, tìm kiếm tài liệu video, tạo phụ đề và nhạc nền, sau đó kết hợp tất cả thành một video ngắn độ phân giải cao.
<br>

<h4>Giao diện Web</h4>

![](docs/webui.jpg)

<h4>Giao diện API</h4>

![](docs/api.jpg)

</div>

## Lời cảm ơn đặc biệt 🙏

Vì việc **triển khai** và **sử dụng** dự án này có thể khó khăn đối với người mới, nên chúng tôi đặc biệt cảm ơn nền tảng **RecCloud (Nền tảng dịch vụ đa phương tiện AI thông minh)** đã phát triển dựa trên dự án này và cung cấp dịch vụ `Trình tạo video AI` miễn phí. Người dùng có thể sử dụng trực tiếp mà không cần triển khai, rất thuận tiện.

- Phiên bản tiếng Trung: https://reccloud.cn
- Phiên bản tiếng Anh: https://reccloud.com

![](docs/reccloud.cn.jpg)

## Cảm ơn nhà tài trợ 🙏

Cảm ơn PicWish https://picwish.cn đã hỗ trợ và tài trợ cho dự án này, giúp dự án có thể tiếp tục cập nhật và bảo trì.

PicWish tập trung vào **lĩnh vực xử lý hình ảnh**, cung cấp nhiều **công cụ xử lý hình ảnh** đa dạng, đơn giản hóa các thao tác phức tạp, thực sự giúp việc xử lý hình ảnh trở nên dễ dàng hơn.

![picwish.jpg](docs/picwish.jpg)

## Tính năng 🎯

- [x] **Kiến trúc MVC** đầy đủ, cấu trúc mã **rõ ràng**, dễ bảo trì, hỗ trợ cả `API` và `Giao diện Web`
- [x] Hỗ trợ **tự động tạo kịch bản video bằng AI**, hoặc có thể **tùy chỉnh kịch bản**
- [x] Hỗ trợ nhiều **kích thước video HD**
    - [x] Màn hình dọc 9:16, `1080x1920`
    - [x] Màn hình ngang 16:9, `1920x1080`
- [x] Hỗ trợ **tạo video hàng loạt**, có thể tạo nhiều video cùng lúc và chọn video ưng ý nhất
- [x] Hỗ trợ cài đặt **thời lượng đoạn video**, thuận tiện điều chỉnh tần suất chuyển đổi tài liệu
- [x] Hỗ trợ kịch bản video bằng **tiếng Trung** và **tiếng Anh**
- [x] Hỗ trợ tổng hợp **nhiều giọng nói**, có thể **nghe thử** ngay lập tức
- [x] Hỗ trợ **tạo phụ đề**, có thể điều chỉnh `phông chữ`, `vị trí`, `màu sắc`, `kích thước`, đồng thời hỗ trợ cài đặt `viền phụ đề`
- [x] Hỗ trợ **nhạc nền**, ngẫu nhiên hoặc chỉ định tệp nhạc, có thể điều chỉnh `âm lượng nhạc nền`
- [x] Tài liệu video có độ phân giải **cao** và **không có bản quyền**, cũng có thể sử dụng **tài liệu cục bộ** của riêng bạn
- [x] Hỗ trợ nhiều mô hình như **OpenAI**, **Moonshot**, **Azure**, **gpt4free**, **one-api**, **通义千问**, **Google Gemini**, **Ollama**, **DeepSeek**, **文心一言**, v.v.
    - Người dùng Trung Quốc nên sử dụng **DeepSeek** hoặc **Moonshot** làm nhà cung cấp mô hình (có thể truy cập trực tiếp từ Trung Quốc mà không cần VPN. Đăng ký được tặng hạn mức, đủ để sử dụng)

### Kế hoạch tương lai 📅

- [ ] Hỗ trợ lồng tiếng GPT-SoVITS
- [ ] Tối ưu hóa tổng hợp giọng nói, sử dụng mô hình lớn để tạo ra giọng nói tự nhiên hơn, phong phú cảm xúc hơn
- [ ] Thêm hiệu ứng chuyển cảnh video để làm cho video mượt mà hơn
- [ ] Thêm nhiều nguồn tài liệu video, tối ưu hóa sự phù hợp giữa tài liệu video và kịch bản
- [ ] Thêm tùy chọn độ dài video: ngắn, trung bình, dài
- [ ] Hỗ trợ nhiều nhà cung cấp dịch vụ tổng hợp giọng nói hơn, như OpenAI TTS
- [ ] Tự động tải lên YouTube

## Video demo 📺

### Màn hình dọc 9:16

<table>
<thead>
<tr>
<th align="center"><g-emoji class="g-emoji" alias="arrow_forward">▶️</g-emoji> 《Làm thế nào để thêm niềm vui vào cuộc sống》</th>
<th align="center"><g-emoji class="g-emoji" alias="arrow_forward">▶️</g-emoji> 《Vai trò của tiền bạc》<br>Giọng nói tổng hợp chân thực hơn</th>
<th align="center"><g-emoji class="g-emoji" alias="arrow_forward">▶️</g-emoji> 《Ý nghĩa của cuộc sống là gì》</th>
</tr>
</thead>
<tbody>
<tr>
<td align="center"><video src="https://github.com/harry0703/MoneyPrinterTurbo/assets/4928832/a84d33d5-27a2-4aba-8fd0-9fb2bd91c6a6"></video></td>
<td align="center"><video src="https://github.com/harry0703/MoneyPrinterTurbo/assets/4928832/af2f3b0b-002e-49fe-b161-18ba91c055e8"></video></td>
<td align="center"><video src="https://github.com/harry0703/MoneyPrinterTurbo/assets/4928832/112c9564-d52b-4472-99ad-970b75f66476"></video></td>
</tr>
</tbody>
</table>

### Màn hình ngang 16:9

<table>
<thead>
<tr>
<th align="center"><g-emoji class="g-emoji" alias="arrow_forward">▶️</g-emoji>《Ý nghĩa của cuộc sống là gì》</th>
<th align="center"><g-emoji class="g-emoji" alias="arrow_forward">▶️</g-emoji>《Tại sao chúng ta nên tập thể dục》</th>
</tr>
</thead>
<tbody>
<tr>
<td align="center"><video src="https://github.com/harry0703/MoneyPrinterTurbo/assets/4928832/346ebb15-c55f-47a9-a653-114f08bb8073"></video></td>
<td align="center"><video src="https://github.com/harry0703/MoneyPrinterTurbo/assets/4928832/271f2fae-8283-44a0-8aa0-0ed8f9a6fa87"></video></td>
</tr>
</tbody>
</table>

## Yêu cầu cấu hình 📦

- Đề xuất tối thiểu CPU 4 nhân trở lên, RAM 8GB trở lên, card đồ họa không bắt buộc
- Windows 10 hoặc MacOS 11.0 trở lên

## Bắt đầu nhanh 🚀

Tải gói khởi động một chạm, giải nén và sử dụng trực tiếp (đường dẫn không nên có **ký tự Trung Quốc**, **ký tự đặc biệt**, **khoảng trắng**)

### Windows
- Baidu Netdisk (phiên bản mới nhất 1.2.1): https://pan.baidu.com/s/1pSNjxTYiVENulTLm6zieMQ?pwd=g36q Mã trích xuất: g36q

Sau khi tải xuống, nên **nhấp đúp vào** `update.bat` để cập nhật lên **mã nguồn mới nhất**, sau đó nhấp đúp vào `start.bat` để khởi động

Sau khi khởi động, trình duyệt sẽ tự động mở (nếu trang trống, hãy thử dùng **Chrome** hoặc **Edge**)

### Các hệ điều hành khác

Chưa có gói khởi động một chạm, vui lòng xem phần **Cài đặt và triển khai** bên dưới, nên sử dụng **docker** để triển khai, thuận tiện hơn.

## Cài đặt và triển khai 📥

### Điều kiện tiên quyết

- Nên tránh sử dụng **đường dẫn tiếng Trung Quốc** để tránh các vấn đề không lường trước được
- Đảm bảo **kết nối mạng** hoạt động bình thường, VPN cần bật chế độ `luồng lưu lượng toàn cầu`

#### ① Sao chép mã nguồn

```shell
git clone https://github.com/harry0703/MoneyPrinterTurbo.git
```

#### ② Sửa đổi tệp cấu hình

- Sao chép tệp `config.example.toml` và đổi tên thành `config.toml`
- Theo hướng dẫn trong tệp `config.toml`, cấu hình `pexels_api_keys` và `llm_provider`, và dựa vào nhà cung cấp llm_provider tương ứng, cấu hình API Key liên quan

### Triển khai Docker 🐳

#### ① Khởi động Docker

Nếu chưa cài đặt Docker, hãy cài đặt trước: https://www.docker.com/products/docker-desktop/

Nếu bạn dùng Windows, hãy tham khảo tài liệu của Microsoft:

1. https://learn.microsoft.com/zh-cn/windows/wsl/install
2. https://learn.microsoft.com/zh-cn/windows/wsl/tutorials/wsl-containers

```shell
cd MoneyPrinterTurbo
docker-compose up
```

> Lưu ý: Phiên bản docker mới nhất sẽ tự động cài đặt docker compose dưới dạng plugin, lệnh khởi động đã được điều chỉnh thành docker compose up

#### ② Truy cập giao diện Web

Mở trình duyệt, truy cập http://0.0.0.0:8501

#### ③ Truy cập tài liệu API

Mở trình duyệt, truy cập http://0.0.0.0:8080/docs hoặc http://0.0.0.0:8080/redoc

### Triển khai thủ công 📦

> Hướng dẫn video

- Demo sử dụng đầy đủ: https://v.douyin.com/iFhnwsKY/
- Cách triển khai trên Windows: https://v.douyin.com/iFyjoW3M

#### ① Tạo môi trường ảo

Nên sử dụng [conda](https://conda.io/projects/conda/en/latest/user-guide/install/index.html) để tạo môi trường ảo Python

```shell
git clone https://github.com/harry0703/MoneyPrinterTurbo.git
cd MoneyPrinterTurbo
conda create -n MoneyPrinterTurbo python=3.11
conda activate MoneyPrinterTurbo
pip install -r requirements.txt
```

#### ② Cài đặt ImageMagick

- Windows:
    - Tải xuống từ https://imagemagick.org/script/download.php, chọn phiên bản Windows, nhớ chọn phiên bản **thư viện tĩnh**, ví dụ: ImageMagick-7.1.1-32-Q16-x64-**static**.exe
    - Cài đặt ImageMagick đã tải xuống, **chú ý không thay đổi đường dẫn cài đặt**
    - Sửa đổi `imagemagick_path` trong `tệp cấu hình config.toml` thành **đường dẫn cài đặt thực tế** của bạn

- MacOS:
  ```shell
  brew install imagemagick
  ````
- Ubuntu
  ```shell
  sudo apt-get install imagemagick
  ```
- CentOS
  ```shell
  sudo yum install ImageMagick
  ```

#### ③ Khởi động giao diện Web 🌐

Lưu ý cần thực hiện các lệnh sau trong `thư mục gốc` của dự án MoneyPrinterTurbo

###### Windows

```bat
conda activate MoneyPrinterTurbo
webui.bat
```

###### MacOS hoặc Linux

```shell
conda activate MoneyPrinterTurbo
sh webui.sh
```

Sau khi khởi động, trình duyệt sẽ tự động mở (nếu trang trống, hãy thử dùng **Chrome** hoặc **Edge**)

#### ④ Khởi động dịch vụ API 🚀

```shell
python main.py
```

Sau khi khởi động, bạn có thể xem `tài liệu API` tại http://127.0.0.1:8080/docs hoặc http://127.0.0.1:8080/redoc để gỡ lỗi giao diện trực tuyến và trải nghiệm nhanh chóng.

## Tổng hợp giọng nói 🗣

Để xem danh sách tất cả giọng nói được hỗ trợ, hãy xem: [Danh sách giọng nói](./docs/voice-list.txt)

Ngày 16-04-2024, phiên bản v1.1.2 đã thêm 9 giọng tổng hợp Azure mới, cần cấu hình API KEY, giọng nói này tổng hợp chân thực hơn.

## Tạo phụ đề 📜

Hiện tại hỗ trợ 2 phương pháp tạo phụ đề:

- **edge**: Tạo `nhanh`, hiệu suất tốt hơn, không yêu cầu cấu hình máy tính, nhưng chất lượng có thể không ổn định
- **whisper**: Tạo `chậm`, hiệu suất kém hơn, có yêu cầu nhất định về cấu hình máy tính, nhưng `chất lượng đáng tin cậy hơn`.

Có thể sửa đổi `subtitle_provider` trong tệp cấu hình `config.toml` để chuyển đổi

Nên sử dụng chế độ `edge`, nếu chất lượng phụ đề không tốt, hãy chuyển sang chế độ `whisper`

> Lưu ý:

1. Chế độ whisper yêu cầu tải xuống một tệp mô hình từ HuggingFace, khoảng 3GB, hãy đảm bảo kết nối mạng thông suốt
2. Nếu để trống, nghĩa là không tạo phụ đề.

> Do Trung Quốc không thể truy cập HuggingFace, bạn có thể sử dụng phương pháp sau để tải xuống tệp mô hình `whisper-large-v3`

Địa chỉ tải xuống:

- Baidu Netdisk: https://pan.baidu.com/s/11h3Q6tsDtjQKTjUu3sc5cA?pwd=xjs9
- Quark Netdisk: https://pan.quark.cn/s/3ee3d991d64b

Sau khi tải xuống mô hình, giải nén và đặt toàn bộ thư mục vào `.\MoneyPrinterTurbo\models`,
đường dẫn tệp cuối cùng sẽ là: `.\MoneyPrinterTurbo\models\whisper-large-v3`

```
MoneyPrinterTurbo  
  ├─models
  │   └─whisper-large-v3
  │          config.json
  │          model.bin
  │          preprocessor_config.json
  │          tokenizer.json
  │          vocabulary.json
```

## Nhạc nền 🎵

Nhạc nền cho video nằm trong thư mục `resource/songs` của dự án.
> Dự án hiện có một số nhạc mặc định, lấy từ video YouTube, nếu vi phạm bản quyền, vui lòng xóa.

## Phông chữ phụ đề 🅰

Dùng để hiển thị phụ đề video, nằm trong thư mục `resource/fonts` của dự án, bạn cũng có thể thêm phông chữ riêng.

## Câu hỏi thường gặp 🤔

### ❓Làm thế nào để sử dụng mô hình OpenAI GPT-3.5 miễn phí?

[OpenAI đã thông báo rằng ChatGPT 3.5 đã miễn phí](https://openai.com/blog/start-using-chatgpt-instantly), và một số nhà phát triển đã đóng gói nó thành API để gọi trực tiếp

**Đảm bảo bạn đã cài đặt và khởi động dịch vụ docker**, thực hiện lệnh sau để khởi động dịch vụ docker

```shell
docker run -p 3040:3040 missuo/freegpt35
```

Sau khi khởi động thành công, sửa đổi cấu hình trong `config.toml`

- Đặt `llm_provider` thành `openai`
- `openai_api_key` điền bất kỳ giá trị nào, ví dụ '123456'
- Thay đổi `openai_base_url` thành `http://localhost:3040/v1/`
- Thay đổi `openai_model_name` thành `gpt-3.5-turbo`

> Lưu ý: Phương pháp này kém ổn định

### ❓AttributeError: 'str' object has no attribute 'choices'`

Vấn đề này xảy ra do mô hình lớn không trả về phản hồi chính xác.

Khả năng cao là do vấn đề mạng, hãy sử dụng **VPN** hoặc đặt `openai_base_url` thành proxy của bạn để giải quyết.

Đồng thời, nên sử dụng **Moonshot** hoặc **DeepSeek** làm nhà cung cấp mô hình lớn, hai nhà cung cấp này có tốc độ truy cập nhanh hơn và ổn định hơn tại Trung Quốc.

### ❓RuntimeError: No ffmpeg exe could be found

Thông thường, ffmpeg sẽ được tự động tải xuống và phát hiện.
Nhưng nếu môi trường của bạn có vấn đề, không thể tự động tải xuống, bạn có thể gặp lỗi sau:

```
RuntimeError: No ffmpeg exe could be found.
Install ffmpeg on your system, or set the IMAGEIO_FFMPEG_EXE environment variable.
```

Lúc này bạn có thể tải ffmpeg từ https://www.gyan.dev/ffmpeg/builds/, sau khi giải nén, đặt `ffmpeg_path` thành đường dẫn cài đặt thực tế của bạn.

```toml
[app]
# Vui lòng đặt theo đường dẫn thực tế của bạn, lưu ý dấu phân cách đường dẫn Windows là \\
ffmpeg_path = "C:\\Users\\harry\\Downloads\\ffmpeg.exe"
```

### ❓Chính sách bảo mật của ImageMagick ngăn chặn các hoạt động liên quan đến tệp tạm thời @/tmp/tmpur5hyyto.txt

Bạn có thể tìm thấy các chính sách này trong tệp cấu hình policy.xml của ImageMagick.
Tệp này thường nằm tại /etc/ImageMagick-`X`/ hoặc vị trí tương tự trong thư mục cài đặt ImageMagick.
Sửa đổi mục có `pattern="@"`, thay đổi `rights="none"` thành `rights="read|write"` để cho phép đọc và ghi tệp.

### ❓OSError: [Errno 24] Too many open files

Vấn đề này do giới hạn số lượng tệp mở của hệ thống, có thể giải quyết bằng cách sửa đổi giới hạn.

Kiểm tra giới hạn hiện tại

```shell
ulimit -n
```

Nếu quá thấp, có thể tăng lên, ví dụ

```shell
ulimit -n 10240
```

### ❓Lỗi tải xuống mô hình Whisper

LocalEntryNotfoundEror: Cannot find an appropriate cached snapshotfolderfor the specified revision on the local disk and
outgoing trafic has been disabled.
To enablerepo look-ups and downloads online, pass 'local files only=False' as input.

Hoặc

An error occured while synchronizing the model Systran/faster-whisper-large-v3 from the Hugging Face Hub:
An error happened while trying to locate the files on the Hub and we cannot find the appropriate snapshot folder for the
specified revision on the local disk. Please check your internet connection and try again.
Trying to load the model directly from the local cache, if it exists.

Cách giải quyết: [Nhấp vào để xem cách tải xuống mô hình thủ công từ disk cloud](#t%E1%BA%A1o-ph%E1%BB%A5-%C4%91%E1%BB%81-)

## Phản hồi và đề xuất 📢

- Bạn có thể gửi [issue](https://github.com/harry0703/MoneyPrinterTurbo/issues)
  hoặc [pull request](https://github.com/harry0703/MoneyPrinterTurbo/pulls).

## Dự án tham khảo 📚

Dự án này được xây dựng lại từ https://github.com/FujiwaraChoki/MoneyPrinter với nhiều tối ưu hóa và tính năng bổ sung.
Cảm ơn tác giả gốc vì tinh thần mã nguồn mở.

## Giấy phép 📝

Nhấp để xem tệp [`LICENSE`](LICENSE)

## Lịch sử Star

[![Star History Chart](https://api.star-history.com/svg?repos=harry0703/MoneyPrinterTurbo&type=Date)](https://star-history.com/#harry0703/MoneyPrinterTurbo&Date)
</div> 