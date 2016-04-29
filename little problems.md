##stack vs heap
When a value is assigned to a variable, the ECMAScript interpreter must decide if it is a primitive or reference
value. To do this, the interpreter tries to determine if the value is one of the ECMAScript primitive
types: Undefined, Null, Boolean, Number, or String. Because each one of these primitive types takes up a
fixed amount of space, it can be stored in the small memory area known as the stack. Doing so allows for
quick look up of variable values.<br>

If the value is a reference, then space is allocated on the heap. Because a reference value’s size can vary, it
cannot be placed on the stack because it would reduce the speed of variable lookup. Instead, the value
placed in the variable’s stack space is an address of a location in the heap where the object is stored. This
address does have a fixed size; so storing it in the stack has no negative effect on variable performance

stack 放原始类型变量（int, boolean 等）<br>
heap 放用户定义变量（object， 可变长度的数组，等）<br>
stack 空间小； 若变量放在stack中存储速度快，但编译时要预先设定其大小与生命周期<br>
heap 空间大；变量放在其中能动态编译（运行时才确定大小、生命周期等）<br>
<br>
javascript 中，一个变量若是用户自定义，那么它就会在stack中存有一个指向heap的地址。

##进程vs线程
一个进程可以包含一个或多个线程；如果进程是个项目组，线程就是程序员。
