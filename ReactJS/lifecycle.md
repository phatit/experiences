1. Từ phiên bản 16.3 trở đi, ReactJS có lifecycle mới (Vẫn hỗ trợ lifecycle cũ). Tuy nhiên, từ phiên bản 17 trở đi lifecycle cũ sẽ không còn được hỗ trợ nữa.
**Lý do phải có lifecycle mới**
    - Naming dễ gây hiểu nhầm
    - Thường dùng `constructor`, `componentWillMount`, `comonentWillReceiveProps` để init `state` => Dễ gây duplicate code => `getDerivedStateFromProps` được sinh ra để giải quyết vấn đề này.
    - Hoặc bạn muốn get thông tin nào đó của các ref trước khi render chẳng hạn, và sử dụng nó sau khi nó sau khi render lại. Đó là lý do mà `getSnapshotBeforeUpdate` ra đời để thay thế `componentWillUpdate`, và `componentDidUpdate` có thêm một param mới là **snapshoot**. 

2. Lifecycle mới sẽ có dạng như sau:
    - Mounting: `constructor` → `getDerivedStateFromProps` → `render` → `componentDidMount`
    - Updating: `getDerivedStateFromProps` → `shouldComponentUpdate` → `render` → `getSnapshootBeforeUpdate`→ `componentDidUpdate`
    - Unmouting: `componentWillUnmount`
3. 