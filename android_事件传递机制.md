#Android 事件传递机制

===
###View的传递机制
+ View首先执行dispatchTouchEvent方法

+ 在dispatchTouchEvent中首先执行onTouch方法

+ 如果View的onTouch事件返回false或者控件没有设置setOnTouchListener方法，或者View的enable为false的情况下会调用onTouchEvent,dispatchTouchEvent返回值与onTouchEvent一样

+ 如果view的enable为false不会执行onTouch方法，只能重写控件的onTouchEvent方法处理

+ 如果view的enable为true切onTouch为true则dispatchTouchEvent直接返回true,不会调用onTouchEvent

+ 当dispatchEvent分发事件的时候，只有前一个action为true才会触发下一个action

###ViewGroup
+ Android事件派发先传递到最顶级的ViewGroup，再由ViewGroup传递到View

+ ViewGroup中可以通过onInterceptTouchEvent方法拦截事件，为true则表示不允许事件继续向子View传递，返回false则表示不对事件进行拦截，默认返回false

+ 子View中如果将事件消费掉则ViewGroup中将无法接收到任何事件
