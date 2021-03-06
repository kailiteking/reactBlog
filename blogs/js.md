---
title: 'JS å°è®°'
date: '2022-2-2'
description: 'We supply a series of design principles, practical patterns and high quality design resources (Sketch and Axure), to help people create their product prototypes beautifully and efficiently.'
---


# js å°è®°ð¥

## å½æ°åºç¡ç¥è¯

### å½æ°çå£°æ

- å½æ°è¡¨è¾¾å¼ï¼å¿åå½æ°ï¼

    ~~~javascript
    // æ­¤æ¶çå½æ°ä¸ºå¿åå½æ°ï¼funæ¯åéåç§°ï¼å¯ä»¥ä½¿ç¨åéåå¯¹å½æ°è¿è¡è°ç¨
    var fun = function(a, b) {return a* b}
    fun(1, 2);
    ~~~

- Function() æé å½æ°

    ~~~javascript
    var myFunction = new Function("a", "b", "return a * b");
    var x = myFunction(4, 3);
    ~~~

- èªè°ç¨å½æ°

    - å½æ°å®ä¹åä¼ç«å³æ§è¡
    - å¨å½æ°ä½åè£¹ä¸ä¸ªæ¬å·ï¼ç¶ååè·ä¸ä¸ä¸ªæ¬å·ã

    ~~~javascript
    (function () {
        var x = "Hello!!";
    })();
    
    ~~~

- ç®­å¤´å½æ°

    - ç®­å¤´å½æ°æ¯ `ES6` çè¯­æ³ï¼ä¸ä¸ä¼è¢«æå

    ~~~javascript
    (x1, x2) => {å½æ°ä½}
    (x1, x2) => åä¸è¡¨è¾¾å¼ // ç­ä»·äº (x1, x2) => {return è¡¨è¾¾å¼;}
    
    x => {å½æ°ä½} // åä¸åæ°æ¶ï¼æ¬å·å¯çç¥
    
    () => {å½æ°ä½} // æ²¡æåæ°æ¶ï¼éè¦åä¸å¯¹æ¬å·
    
    ~~~

### å½æ°åæ°å¯¹åºé®é¢

- å¦æå®åæ¯å½¢åå¤ï¼åä»åå¾ååå®åè¿è¡å¯¹åº
- å¦æå®åæ¯å½¢åå°ï¼åæªè¢«èµå¼çå½¢åä¼é»è®¤ä¸º `undefined`
- **å¦æå®åæ°éä¸ç¡®å®ï¼å¯ä»¥ä½¿ç¨ `arguments` è·åå®å**
    - `arguments` ç±»ä¼¼æ°ç»ï¼å¯ä»¥åæ°ç»ä¸æ ·ä½¿ç¨ä¸æ è·åä¼ å¥çåæ°
    - å¯ä»¥ä½¿ç¨ `arguments.length` è·ååæ°æ°é

### return è¿åå¼

- å¦æå½æ°ä¸å `return` é£ä¹é»è®¤è¿å `undefined` 
- `return` åè·å¤ä¸ªæ°å¼æ¶ï¼è¿åæåä¸ä¸ª

### é¢è§£æ

- JavaScript ä¼ä¸è§£æä»£ç ï¼æ**åéå£°æ**å**å½æ°å£°æ**æåå°å½åä½ç¨åçæåæ¹ã

    - åéæåï¼ä»æååéå£°æï¼ä¸ä¼æåèµå¼æä½ï¼**åæ¬å½æ°è¡¨è¾¾å¼çåé**ã
    - å½æ°æåï¼æåå½æ°å£°æå°æåï¼ä¸æ§è¡å½æ°ã

    ~~~javascript
    f1();
    console.log(c);
    console.log(b);
    console.log(a);
    
    function f1() {
        var a = b = c = 9;
        console.log(a);
        console.log(b);
        console.log(c);
    }
    
    // ç¸å½äºä»¥ä¸æ§è¡é¡ºåº 
    function f1() {
        var a
        a = b = c = 9;  // æ­¤å¤æ§è¡ç¸å½äº var a = 9; b = 9; c = 9;
        				// èé var a = 9, b = 9, c = 9;
        				// å¯¼è´ åªæ a æ¶å±é¨åéï¼bãc æ²¡æå£°æç´æ¥èµå¼ï¼åä¸ºå¨å±åé
        console.log(a);
        console.log(b);
        console.log(c);
    }
    
    f1();
    console.log(c);
    console.log(b);	//bãcæ­£å¸¸è¾åºï¼ç»æä¸º 9
    console.log(a); //æææ­¤å¤ a è¾åºæ¥éï¼åå ä¸ºæªå®ä¹
    ~~~

    

## å¯¹è±¡å°è®°ð¥

### å¯¹è±¡çåå»º

- å­é¢éçæ¹å¼åå»º

    ~~~javascript
    var obj = {
        x : 'a';
        fun : function() {};// æ­¤å½æ°ä¸ºå¿åå½æ°ï¼ä¸ä½¿ç¨å­é¢éå£°æå½æ°çæ¹å¼ç¸å
    }
    ~~~

- new Object

    ~~~javascript
    var obj = new Object();
    obj.x = 'a';
    obj.fun = function() {};
    ~~~

- æé å½æ°

    ~~~ javascript
    function Construct(x, fun) { // ååå»ºä¸ä¸ªæé å½æ°ï¼è®¾ç½®éè¦å®ä¹çå¯¹è±¡åéä¸ºå½¢å
        this.x = x;		// å¯¹è±¡åéèµå¼
        this.fun = fun;  // ä¸éè¦return
    }
    
    var obj = new Construct('a', function(){});
    ~~~

- **`new` å³é®å­åäºä»ä¹**

    - [[new è¿ç®ç¬¦ - JavaScript | MDN (mozilla.org)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/new)]

    1. åå»ºä¸ä¸ªç©ºå¯¹è±¡ï¼objectï¼
    2. è®© `this` æåæ°åå»ºçå¯¹è±¡
    3. æ§è¡æé å½æ°çä»£ç ï¼ä¸ºæ°å¯¹è±¡æ·»å å±æ§
    4. å¦æå½æ°æ²¡æè¿åå¯¹è±¡ï¼è¿å `this` ï¼å³å¶æåçå¯¹è±¡ï¼ 

