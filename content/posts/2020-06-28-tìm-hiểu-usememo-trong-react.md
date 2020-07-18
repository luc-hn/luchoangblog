---
template: post
title: Tìm hiểu useMemo trong React
slug: tim-hieu-usememo-trong-react
draft: true
date: 2020-06-28T07:50:41.748Z
description: Tìm hiểu useMemo trong React
category: React
featuredimage: /media/untitled.png
tags:
  - react
---
Không biết mọi người như nào, nhưng với mình thì sau khi làm việc với React khoảng nửa năm mình mới bắt đầu tìm hiểu useMemo :D. Lúc mới làm quen React mình tập trung làm với useState và useEffect là nhiều, sản phẩm công ty mình yêu cầu hard deadline nên mình cũng bị cuốn theo, không có thời gian nghiên cứu để tối ưu ứng dụng. Thực ra mình vẫn nghĩ useMemo là 1 hook "nâng cao", vì ứng dụng của bạn có thể chạy trơn tru hoàn toàn nếu không dùng useMemo, và chỉ nên dùng useMemo trong 1 vài trường hợp nhất định chứ đừng nên lạm dụng, lý do vì sao mình sẽ bật mí cuối bài nhé :v. Ok giờ chúng ta bắt tay vào tìm hiểu useMemo.

Như bạn đã biết (hoặc không biết), React component render lại mỗi khi component đó có sự thay đổi. Mình sẽ lấy ví dụ về feature Build Pc mà mình xây dựng trên website [phongvu.vn](https://phongvu.vn)

![](/media/untitled.png)

Khi bạn click vào lọc sản phẩm, toàn bộ modal này sẽ render lại, từ bộ lọc tới sản phẩm và pagination. useMemo giúp chúng ta optimize việc render, ví dụ click vào bộ lọc tôi chỉ muốn khối sản phẩm render lại thôi, khối bộ lọc bên trên không thay đổi gì thì không cần render lại. Hoặc tôi có 1 hàm để tính toán ra được các bộ lọc đang được áp dụng (`getActivatedFilters`), nhưng tôi chỉ muốn render hàm này khi bộ lọc được click, nếu không dùng useMemo thì khi chúng ta chuyển trang, sort sản phẩm hàm `getActivatedFilters` cũng sẽ render lại gây lãng phí.

VD: 

`const `

`console.log("hihi");`

`}`

`//Không dùng useMemo`

`const activatedFilters = getActivatedFilters();`

`//Dùng useMemo`

`const activatedFilters = useMemo(() => getActivatedFilters(), [queryFilters]);`