---
title: "Welcome to Tranquilpeak 0.5.2-BETA"
date: 2021-09-14
categories:
- javascript
tags:
- slice
- splice
- split
keywords:
- slice
- splice
- split
autoThumbnailImage: false
thumbnailImagePosition: "top"
# thumbnailImage: //d1u9biwaxjngwg.cloudfront.net/welcome-to-tranquilpeak/city-750.jpg
# coverImage: //d1u9biwaxjngwg.cloudfront.net/welcome-to-tranquilpeak/city.jpg
metaAlignment: center
---
紀錄自己的筆記讓自己回頭來看更容易統整

這邊處理的型態分為兩種
<!--more-->

<!-- ![Tranquilpeak](/img/showcase.png) -->

{{< toc >}}

這邊處理的型態分為兩種

1. 陣列
    - Array.prototype.slice()

        會改變原始陣列：不會

        是否有 return：有！

        return 什麼：會回傳一個指定索引範圍的新陣列（不改變原陣列）。

        ```jsx
        arr.slice([begin[, end]])

        const arr = [0, 1, 2, 3, 4, 5];

        // 無參數，從 0 ~ (arr.length - 1)
        console.log(arr.slice()); // [0, 1, 2, 3, 4, 5]

        // 從 2 開始到 (arr.length - 1) 結束
        console.log(arr.slice(2)); // [2, 3, 4, 5]

        // 從 2 開始到 (3 - 1) 結束
        console.log( arr.slice(2, 4) ); // [2, 3]

        // 從開始直接填寫負數 (arr.length - 2) 到 (arr.length - 1) 結束
        // 這個部分比較不直觀，可以再多幾個範例來理解，目前實務上我不會想用
        console.log( arr.slice(-2) );  // [4, 5]
        ```

    - Array.prototype.splice()

        會改變原始陣列：會

        是否有 return：有！注意有條件的 return

        return 什麼：

        依照所填入的參數來決定 return 什麼，直接看下面的範例

        注意：第一個參數是必填的後面兩個參數是選擇性的

        ```jsx
        array.splice(start[, deleteCount[, item1[, item2[, ...]]]])

        1. 簡單運用
        const arr = [0, 1, 2, 3, 4, 5];

        console.log( arr.splice() ) // []
        console.log( arr.splice(2) ) // [2, 3, 4, 5]
        console.log( arr ) // [0, 1]

        2. 只填第一個參數
        const arr2 = [0, 1, 2, 3, 4, 5];
        const removed2 = arr2.splice(2);

        console.log( arr2 );  // [0, 1]
        console.log( removed2 ); // [2, 3, 4, 5]

        3. 填入第一個與第二個參數
        const arr3 = [0, 1, 2, 3, 4, 5];
        const removed3 = arr3.splice(2, 2);

        console.log(arr3);     // [0, 1, 4, 5]
        console.log(removed3); // [2, 3]

        4. 填入第一個、第二個及第三個參數
        const arr4 = [0, 1, 2, 3, 4, 5];
        const removed4 = arr4.splice(2, 3, 'aa');

        console.log(arr4); // [ 0, 1, 'aa', 5 ]
        console.log(removed4); // [2, 3, 4]
        ```

2. 字串
    - String.prototype.slice()

        會改變原始字串：不會

        是否有 return：有！

        會回傳一個指定索引範圍字元的新字串

        ```jsx
        str.slice(beginIndex[, endIndex])

        const str = 'The quick brown fox jumps over the lazy dog.'

        console.log(str.slice(31)); // 'the lazy dog.'
        console.log(str) // 'The quick brown fox jumps over the lazy dog.'
        ```

    - String.prototype.split()

        會改變原始字串：不會

        是否有 return：有！

        會依照指定規則分割字串，並回傳一個陣列，內容為拆分的字串

        ```jsx
        str.split([separator[, limit]])

        const monthString = 'Jan,Feb,Mar,Apr,May,Jun,Jul,Aug,Sep,Oct,Nov,Dec';

        console.log( monthString.split(',') );
        // [ 'Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec' ]

        const num = '00000000';

        console.log( num.split('', 2) ); // [ '0', '0' ]
        ```
