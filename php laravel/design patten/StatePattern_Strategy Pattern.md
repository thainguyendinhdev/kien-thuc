### State Pattern 
State là một mẫu thiết kế hành vi cho phép một đối tượng thay đổi hành vi của nó khi trạng thái bên trong của nó thay đổi. Điều này giúp gia tăng tính linh hoạt, phân chia trách nhiệm rõ ràng giữa khi đối tượng thay đổi trạng thái và tăng khả năng bảo trì.
Dấu hiệu nhận biết:
Bài toán kinh điển nhất có lẽ là thay đổi trạng thái đơn hàng: Khi đơn hàng đó mới được tiếp nhận, nhân viên lấy hàng sẽ được quyền thao tác với đơn hàng đó. Tuy nhiên khi đơn hàng chuyển sang trạng đã giao hàng, nhân viên giao hàng sẽ không được phép tác động vào đơn hàng nữa. Bất kể khi nào hành vi của đối tượng có thể được thay đổi bởi trạng thái của nó, bạn có thể nghĩ tới State Pattern.

![Alt text](../images/design%20patten/StatePattern.jpg)

### Strategy Pattern 
Strategy là một mẫu thiết kế hành vi cho phép bạn xác định một tập hợp các công việc tương tự nhau, được đặt trong các class riêng biệt (implement chung một interface), và cho phép chúng có thể hoán đổi lẫn nhau. Điều này giúp bạn thay đổi các class này tại thời gian chạy (Runtime) mà không làm ảnh hưởng tới chức năng của ứng dụng.
Dấu hiệu nhận biết:
Strategy rất dễ để nhận biết. Trong các tình huống mà bạn cảm thấy mình có nhiều phương án (và các phương án này tương tự nhau ở input / output) để xử lý cho một vấn đề, bạn có thể nghĩ tới Strategy. Ví dụ khi implement các phương thức vận chuyển, các phương thức thanh toán cho đơn hàng trên website thương mại điện tử. Hoặc cách mà Laravel có thể thay đổi giữa các driver khác nhau trên Cache chẳng hạn (file, Redis, array, …), cũng là nhờ sử dụng đến Strategy.

![Alt text](../images/design%20patten/StrategyPattern.jpg)