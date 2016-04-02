# arduino学习笔记5 Arduuino复合运算符 {#arduino-5-arduuino}

+= , -= , *= , /= Description描述Perform a mathematical operation on a variable with another constant or variable. The += (et al) operators are just a convenient shorthand for the expanded syntax, listed below. 对一个变量和另一个参数或变量完成一个数学运算。+=（以及其他）可以缩短语法长度。

Syntax语法x += y;   // equivalent to the expression x = x + y;          // 等价于 x = x + y;x -= y;   // equivalent to the expression x = x - y;           // 等价于 x = x - y;x *= y;   // equivalent to the expression x = x * y;           // 等价于 x = x * y;x /= y;   // equivalent to the expression x = x / y;           // 等价于 x = x / y;

Parameters参数x: any variable type x：任何变量类型

y: any variable type or constant y：任何变量类型或常数

Examples范例x = 2;x += 4;      // x now contains 6             // x现在为6x -= 3;      // x now contains 3             // x现在为3x *= 10;     // x now contains 30             // x现在为30x /= 2;      // x now contains 15             // x现在为15

Syntax语法x++; // increment x by one and returns the old value of x      // 将x的值加1并返回原来的x的值。    ++x; // increment x by one and returns the new value of x      // 将x的值加1并返回现在的x的值。   x-- ;   // decrement x by one and returns the old value of x       // 将x的值减1并返回原来的x的值。   --x ;   // decrement x by one and returns the new value of x        // 将x的值减1并返回现在的x的值。

Parameters参数x: an integer or long (possibly unsigned) x：一个整数或长整数（可以无符号）

Returns返回The original or newly incremented / decremented value of the variable. 返回变量原始值或增加/消耗后的新值。

Examples范例x = 2;y = ++x;      // x now contains 3, y contains 3              // x现在为3，y为3y = x--;      // x contains 2 again, y still contains 3              // x现在仍然为2，y将为3