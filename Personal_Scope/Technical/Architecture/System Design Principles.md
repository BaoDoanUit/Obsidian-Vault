##  What is System Design?
- Think For The Now
     - You're building a system, that will function now. Something that will solve a problem your users have now.
     - Yeah, it's very good to think ahead, but you can easily get lost in doing so. Instead, try to solve and think about the problems you (or your users) have now.
- Scalability
     - Think For The Now, Make Room For The Future
     - Solve the problems you have now, while not bottlenecking yourself in the future!
- Flexibility
- Reusable
     - Make sure your code is fluid
     - Don't make specific functions that do only one thing, make broad or general-purpose functions
     - Use loops when necessary, define global rules (for example, your theme), etc.
     - Make sure your code can be reused. (D.R.Y)
- Don't GO into detail Prematurely, and K.I.S.S
     - Don't dive into your design head first.
     - Take your time. Relook at things twice, thrice, ten times.
     - Don't overthink it. If something looks more complicated than it should be, it probably is.
     - Don't focus on one specific thing, take a step back and look at the whole problem. And slowly, but surely, go into detail.

-- Commented about Domain Driven Design
Chia sẻ một chút về cách tiếp cập của mình.

Đầu tiên, sẽ có dùng Event Storming để quickly discover ra business flow và các entity tham gia vào.

Sau đó sẽ implement một bản MVP monolith, bao gồm tất cả các entity ở trên tương tác với nhau. Ở bản này có thể chưa cần persit data ngay xuống mà có thể lưu trên Ram. Mục tiêu là prove được flow mình chạy đúng.

Và sau mỗi aglie sprint, mọi người cùng nhìn lại xem entity nào cần gộp hoặc tách, hoặc chia thành một service độc lập. Tránh được việc tách service quá sớm khi chưa hiểu hết được domain.

Nhưng lý thuyết là vậy chứ thực tế thuyết phục được team member và domain experts tham gia khá là khó khăn.

Vấn đề chính đã được các bạn trên comment rồi, là chia Entity tức các đối tượng đủ tính độc lập và riêng rẽ vào các domain module khác nhau.

Trong quá trình chia domain module có thể sẽ gặp vấn đề là phân bổ không đủ Entity cho bussiness hoặc dư Entity dẫn đến domain module khác không có để dùng.

Ngoài ra nên lưu ý nên hạn chế nhất có thể tạo ra những domain module dạng common để dùng chung, bởi vì khi làm chức năng mới Nếu không biết thêm code vào domain module nào thì khả năng cao là sẽ nhét vào các domain module common này, dẫn đến ngày càng phình to ra.

microservices không phải là chi li về kỹ thuật, mà phương án để các services trao đổi với nhau.

Về mặt này thì như ABP framework triển khai, cần document chi tiết nghiệp vụ từng service, cách thức kết nối, viết luôn service client để service khác dùng (sharing code, hoặc nuget packages). Giải quyết được bài toán document về nghiệp vụ và các models trao đổi thông tin sẽ triển khai mô hình dễ dàng hơn. Domain expert không hẳn là 1 người mà có thể môt nhóm người.


 1 project có apply DDD kèm thêm Mediator, mình thấy boilerplate code rất nhiều. Project bị phình to rất nhiều so với mono

 với mình việc đầu tiên sẽ là xác định các Root Entity và các mối quan hệ. Sau đó group các Root Entity này lại. Các group này là cơ sở để xác định domain. Tiếp theo mình xác định chiến lược chia sẻ dữ liệu giữa các domain, có thể là call api trực tiếp, dùng event bus hoặc gRPC. Cuối cùng thì như bạn nói, mình sẽ phải refactor, ghép hoăc tách domain cho phù hợp hơn nữa

 ![[Pasted image 20230413162525.png]]
 Advantages of using API Gateway
 1. Improved performance
 2. Simplified system design
 3. Enhanced security
 4. Improved scalability
 5. Better monitoring and visibility

 Disadvantages of using API Gateway
 1. Increased complexity
 2. Performance overhead
 3. Single point of failure
 