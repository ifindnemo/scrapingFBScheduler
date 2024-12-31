# Scheduler cào dữ liệu từ Facebook (group hoặc fanpage)
> Group 09
> 
> Lớp học phần: (ELC3009_1)
> 
> Giáo viên: Nguyễn Thành Thủy
> 
## Chạy trên heroku:
### Bước 1: Tạo clone của github này [https://github.com/ifindnemo/scrapingFBScheduler](https://github.com/ifindnemo/scrapingFBScheduler), kết nối với heroku, bật auto deploy trên heroku để tự động deploy khi push file lên github.
### Bước 2: Tạo 1 cluster trên MongoDB, tạo 1 database mới trong cluster đó (Xài cluster loại M0-free cũng ổn). (Bỏ qua bước này nếu đã có cluster MongoDB)
- Database access thêm một user với role *Read and write any database*. Network access thêm địa chỉ ip để có thể truy cập từ bất cứ đâu, hoặc ip cụ thể bạn muốn.
### Bước 3: Cài đủ buildpack trên heroku, bao gồm:
> buildpack python có sẵn
> 
> https://github.com/heroku/heroku-buildpack-chrome-for-testing
- Thiết lập các Config Vars bao gồm: MONGODB, PASSWORD_SECRET.
- Về worker dyno thì nên dùng Standard-2X (8 CPU, 1GB RAM)
### Bước 4: Thêm add-on Advanced Scheduler: https://elements.heroku.com/addons/advanced-scheduler
- Setup để chạy dòng này: "python scrapingScheduler.py", chỉnh thời gian và ngồi chờ nó cào thui :v
