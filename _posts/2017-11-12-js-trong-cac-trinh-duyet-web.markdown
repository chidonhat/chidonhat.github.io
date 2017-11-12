---
layout: post
title: JavaScript trong các trình duyệt
date: 2017-11-12 00:00:00
description: JavaScript khi được sử dụng trong các trình duyệt web.
img: 2017-11-12-js-trong-cac-trinh-duyet-web/js-1.png
tags: [JavaScript]
---
Bài này nói về JavaScript khi được sử dụng trong các trình duyệt, thường gọi là client-side JavaScript. Thuật ngữ *client-side JavaScript* sinh ra khi JavaScript được sử dụng ở hai nơi: trình duyệt (web browser) và web server. Nhưng khi JavaScript ngày càng được sử dụng ở nhiều môi trường thì thuật ngữ này càng trở nên vô nghĩa, vì nó không chỉ ra client side của *cái gì*. Tuy nhiên chúng ta vẫn tiếp tục với thuật ngữ này.

Để hiểu client-side JavaScript, bạn phải hiểu môi trường lập trình (programming environment) mà trình duyệt cung cấp. Có ba đặc điểm quan trọng trong môi trường này là:

* Đối tượng `Window`, là một global object và global execution context cho JavaScript code.

* Hệ thống đối tượng (Object hierarchy) và Document Object Model là một phần trong đó.

* Mô hình lập trình hướng sự kiện (event-driven programming model).

## `Window` là global execution context

Nhiệm vụ chính của một trình duyệt web là hiển thị HTML document trong một window. Trong client-side JavaScript, đối tượng `Document` biểu diễn một HTML document, và đối tượng `Window` biểu diễn browser window (hoặc frame) hiển thị document đó. Cả hai đều quan trọng, nhưng `Window` quan trọng hơn vì một lý do lớn sau: `Window` là global object.

Nhớ rằng trong tất cả đối tượng của JavaScript, luôn luôn có một global object là điểm đầu của *scope chain*; và các *thuộc tính (property)* của global object này là các biến toàn cục (global variable). Trong client-side JavaScript, `Window` là global object. `Window` định nghĩa một số thuộc tính và hàm cho phép bạn thao tác với browser window. Nó cũng có một số thuộc tính trỏ tới các đối tượng khác, như `document` trỏ tới đối tượng `Document`. Cuối cùng, `Window` có hai thuộc tính tự trỏ đến nó, là `window` và `self`. Bạn có thể sử dụng một trong hai biến toàn cục này để tham chiếu trực tiếp tới `Window`.

Vì `Window` là global object trong client-side JavaScript, nên tất cả biến toàn cục khi khai báo đều là thuộc tính của nó. Ví dụ, hai dòng code sau thực hiện cùng một chức năng:

{% highlight javascript %}
var answer = 42;      // Khai báo và khởi tạo một biến toàn cục
window.answer = 42;   // Tạo một thuộc tính mới cho đối tượng Window
{% endhighlight %}

`Window` biểu diễn một browser window (hay một frame trong window; trong client-side JavaScript, window và frame tương đương nhau). Chúng ta có thể viết một ứng dụng sử dụng nhiều window (hay frame). Mỗi window đó có một đối tượng `Window` riêng và định nghĩa một execution context riêng. Nói cách khác, một biến toàn cục được khai báo trong một window này không phải là biến toàn cục trong một window khác.

## Object hierarchy và DOM

`Window` là đối tượng chủ chốt trong client-side JavaScript. Tất cả đối tượng khác đều truy cập được thông qua đối tượng này. Ví dụ, `Window` có một thuộc tính `document` trỏ tới đối tượng `Document` liên kết với window, một thuộc tính `location` trỏ tới đối tượng `Location` liên kết với window. Khi window hiển thị một framed document, mảng `frames[]` của `Window` chứa tham chiếu tới đối tượng `Window` biểu diễn frame đó. Nên biểu thức `document` trỏ tới `Document` của window hiện tại, và `frames[1].document` trỏ tới `Document` của frame thứ hai của window hiện tại.

`Document` cũng có các thuộc tính trỏ tới các đối tượng khác. Ví dụ, mảng các đối tượng `Form`, `forms[]`, biểu diễn tất cả HTML form xuất hiện trong document. Để tham chiếu tới một trong những form này, bạn có thể viết:

{% highlight javascript %}
window.document.forms[0]
{% endhighlight %}