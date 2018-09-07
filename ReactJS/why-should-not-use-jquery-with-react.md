*Lý do không nên dùng jQuery trong ReactJS*
- React tương tác với Vitural DOM còn jQuery tương tác với Real DOM nên có nhiều bug sinh ra

Vì jQuey tương tác với *Real DOM* nên bạn phải sử dụng trong hook componentDidMount của React. Nghĩa là phải render ra DOM thật đã thì jQuery mới tương tác được. Đó là lý do bạn thấy hiệu ứng fade của jQuery khi load xong trang.
Nhưng khi bạn update state thì chẳng xuất hiện hiệu ứng đó thêm lần nào nữa
Lý do là khi componentDidMount thì jQuery chỉ get được 2 Node Element trong RealDOM thôi, còn khi React re-render thì đã update lại Real DOM tức là thêm những Node Element, tuy có cùng class="love" những jQuery cần phải get lại từ đầu mới get được Real DOM mới nhất được. Đó là lý do performance rất kém, rất rất kèm.