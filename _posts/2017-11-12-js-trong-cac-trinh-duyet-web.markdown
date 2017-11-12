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

Nhiệm vụ chính của một trình duyệt web là hiển thị HTML document trong một window.
