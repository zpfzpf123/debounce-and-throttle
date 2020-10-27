防抖与节流

防抖

指的是触发函数事件后n秒内置执行一次此事件，如果早n秒内再次触发则重新计算

节流

连续发生的事件在n秒之内只执行一次

代码如下

    <!DOCTYPE html>
    <html lang="en">
    
    <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>Document</title>
    </head>
    <style>
      #a {
        width: 500px;
        height: 500px;
        background-color: #eeeeee;
      }
    </style>
    
    <body>
      <div id="a">
    
      </div>
      <p id="b"></p>
    </body>
    <script>
      let c = 1
      /* //METHOD防抖函数 函数触发后过两秒在执行，在两秒内如果再次触发函数，就重新计算时间
      function debounce(func,wait) {
        let timer
        return function () {
          if (timer) clearTimeout(timer);
          timer = setTimeout(function () {
            func.apply(this)
          }, wait)
        }
      } */
      /* //METHOD防抖函数二 先执行一次，然后如果一直动用函数，就一直不执行，不许等待wait后才能执行
      function debounce(func, wait) {
        let timeout
        return function () {
          if (timeout) clearTimeout(timeout)
          let now = !timeout
          timeout = setTimeout(() => {
            timeout = null
          }, wait)
          if (now) func.apply(this)
        }
      } */
      /*   //METHOD节流函数 触发相同的连续事件在n秒内只执行一次
        function throttle(func, wait) {
          let timeout
          return function () {
            if (!timeout) {
              timeout = setTimeout(() => {
                timeout = null
                func.apply(this)
              }, wait)
            }
          }
        } */
      /* //METHOD节流函数 时间戳
      function throttle(func, wait) {
        let pre = 0
        return function () {
          let now = Date.now()
          if (now - pre > wait) {
            func.apply(this)
            pre = now
          }
        }
      } */
      document.getElementById('a').onmousemove = throttle(function () {
        document.getElementById('b').innerHTML = c++
        console.log(document.getElementById('b').innerHTML)
      }, 1500)
    </script>
    
    </html>


