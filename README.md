**安装环境**

PUPPETEER_DOWNLOAD_HOST=https://storage.googleapis.com.cnpmjs.org npm i puppeteer

**接口定义**

### 1. 创建对象

```
import SpiderFlow from '../src';
let t = new SpiderFlow();
```

### 2. 启动浏览器

```
await t.starUp(options);

options: 浏览器启动参数，同puppeteer.launch
```

### 3. 运行命令
```
let data = await t.step(config);

config格式：
{
    url: '', // 页面url
    pageSymbol: '', // 页面id
    cookies: [], //页面cookie, 非必须
    operation, // 要进行的操作 ['openPage', 'input', 'click', 'slide']
    inputs: [{   // 要输入的内容
        selector : '',
        value: ''
    }],
    clicks: [{  //  要点击的内容
       selector: ''
    }], 
    confirms: {
       'selector1': ['value1', 'value2'] 
    },
    points: [{  // 要拖拽的轨迹
      toX,
      toY,
      timespan 
    }],
    getCookie: false,  // 是否获取页面cookie
    cookies: []        // 要设置的页面cookie,，默认不传
}

返回值：
{
    pageSymbol: '', // 页面标志（参数没有url时，必须传递给config）
    cookies: []     // 当前页面的cookie值
}
 ```
 
 ### 4. 关闭浏览器
 ```
 await t.stop();
```