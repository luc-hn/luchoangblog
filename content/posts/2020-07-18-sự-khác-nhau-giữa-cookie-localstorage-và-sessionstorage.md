---
template: post
title: Sự khác nhau giữa Cookie, localStorage và sessionStorage
slug: su-khac-nhau-giua-cookie-localstorage-va-sessionstorage
draft: false
date: 2020-07-18T05:58:41.886Z
description: >
  Hiện nay với nhu cầu lưu trữ thông tin người dùng trên trình duyệt, chúng ta
  có thể sử dụng localStorage, sessionStorage, hay cookie. Những dữ liệu này
  thường đơn giản chỉ là những thông tin như ngôn ngữ, theme, tùy chỉnh layout,
  …


  Nhưng trên thực tế, chúng ta thường nhầm lẫn giữa cookie, localStorage và sessionStorage.


  Vậy hôm nay chúng ta tìm hiểu kỹ hơn về 3 khái niệm này và nêu lên sự khác nhau giữa chúng như thế nào nhé.
category: Javascript
featuredimage: /media/84dfeb78-3009-4808-971c-065310bc18a6.jpg
tags:
  - javascript
---
Hiện nay với nhu cầu lưu trữ thông tin người dùng trên trình duyệt, chúng ta có thể sử dụng **localStorage**, **sessionStorage**, hay **cookie**. Những dữ liệu này thường đơn giản chỉ là những thông tin như ngôn ngữ, theme, tùy chỉnh layout, …

Nhưng trên thực tế, chúng ta thường nhầm lẫn giữa cookie, localStorage và sessionStorage.

Vậy hôm nay chúng ta tìm hiểu kỹ hơn về 3 khái niệm này và nêu lên sự khác nhau giữa chúng như thế nào nhé.

## **localStorage**

localStorage giống như một database trên browser. Với những trình duyệt hiện đại ngày nay, chúng ta có thể lưu những thông tin đơn giản của người dùng vào browser. Thông tin này được lưu vĩnh viễn trừ khi bạn xoá nó đi.

Về cơ bản, nó như một table trong Excel, nhưng chỉ có hai trường là: **key và value.**

Một số ví dụ dùng localStorage như một số user preferences: ngôn ngữ, theme, danh mục sản phẩm được chọn, giao diện tuỳ chỉnh, dashboard, layout, …

## **sessionStorage**

sessionStorage khá giống với localStorage. Ngoại trừ sessionStorage sẽ mất đi khi chúng ta đóng tab, đóng trình duyệt.

Một khuyết điểm của cả localStorage và sessionStorage là có thể bị đọc bởi Javascript. Do đó dễ bị đánh cắp thông tin thông qua một *cross-site scriting*.

Vì vậy, chúng ta không nên lưu trữ những thông tin nhạy cảm như token ID, password, username, email của người dùng vào localStorage hay sessionStorage.

## **Cookie**

Đây là một em khá hot gây ra nhiều tranh cãi cho mọi người. Một phần vì lỗi bảo mật này nọ. Và bản chất lưu trữ Cookie cũng là một bản ghi đơn giản gồm **key, value.**

Một số điểm nổi bật của **Cookie** so với **localStorage** và **sessionStorage** là:

* Khi đóng một tab, Cookie vẫn còn được lưu trên trình duyệt.
* Cookie có thể **mất đi sau khi đóng trình duyệt** nếu nó được set **expires**là **N/A**
* **Cookie** sẽ tự động được include vào XHR khi chúng ta gửi request REST lên **API**. Điều này cho phép chúng ta không cần phải tự chèn authentication info(kỹ thuật này gọi là interceptor) vào header của mỗi request. Và dựa vào cookie, server có thể nhận biết được client này đã được *authenticate* thành công hay chưa. Đây là lí do chính cookie khó bị thay thế bởi storage thông thường.
* Cookie có option để chúng ta set ngày quá hạn cho nó. Nghĩa là có thể định nghĩa khi nào nó tự động xoá được.

**Một số lưu ý khi dùng cookie:**

* Bị giới hạn về dung lượng lưu trữ khoảng 4KB.
* Nên xác định thời gian expire/max-age. Thông thường chỉ nên cho phép một cookie chứa thông tin để authenticate trong khoảng 3-4 tháng. Để tránh người dùng phải đăng nhập nhiều lần, chúng ta cung cấp một option lưu trữ thông tin để lần sau user không cần đăng nhập nữa.
* Nếu cookie dùng để authenticate nên set **httpOnly** bằng true. Dùng cờ này để không cho phép đọc được cookie từ Javascript. Tránh được sự tấn công từ bên ngoài bằng thủ thuật scripting.
* Dễ bị đánh cắp thông tin người dùng. Cho nên đừng bao giờ lưu password nguyên gốc của user mà hãy mã hoá nó, hay dùng token-based authentication.

<!--EndFragment-->