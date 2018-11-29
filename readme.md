
## 文法
```
<程序> := [<变量定义部分>] {<自定义函数定义部分>} <主函数>
<变量定义部分> :=  int id {, id};
<自定义函数定义部分> :=  ( int id | void id) '(' ')' <分程序>
<主函数> := void main'(' ')' <分程序>
<分程序> := '{' [<变量定义部分>] <语句序列> '}'  
<语句序列> := <语句> {<语句>}
<语句> :=  <条件语句>｜<循环语句> | '{'<语句序列>'}' | <自定义函数调用语句> | <赋值语句> | <返回语句> | <读语句> | <写语句> | ;
<条件语句> := if '('<表达式>')' | <语句> [else <语句> ]
<循环语句> := while '(' <表达式>')' <语句>
<自定义函数调用语句> := <自定义函数调用>;
<赋值语句> := id = <表达式>;
<返回语句> := return ['(' <表达式> ')'] ;
<读语句> := scanf '(' id ')';
<写语句> := printf '(' [ <表达式>] ')';
<表达式> :=  [+｜-] <项> { (+｜-) <项>} 
<项>  :=  <因子>｛(*｜/) <因子>｝
<因子>  :=  id｜'(' <表达式>')' | num | <自定义函数调用>
<自定义函数调用> := id '(' ')'

```

## 指令对应

| pl0        |c0        | description|
|------------|----------|------|
| LIT 0 2	 | LIT 0 a  |                      |
| LOD L a	 | LOD t a	|a为相对地址，t为层数      |
| STP L a	 | STO t a  |                      |
| CAL t a	 | CAL 0 a  |                      |
| INT 0 a	 | INT 0 a  |                      |
| JMP 0 a	 | JMP 0 a  |                      |
| JPC 0 a	 | JPC 0 a	|当栈顶值为0则跳转至a地址        |
| OPR 0 2	 | ADD 0 0	|次栈顶与栈顶相加             |
| OPR 0 3	 | SUB 0 0	|次栈顶减去栈顶              |
| OPR 0 4	 | MUL 0 0	|次栈顶乘以栈顶              |
| OPR 0 5	 | DIV 0 0	|次栈顶除以栈顶              |
| OPR 0 16	 | RED 0 0	|从命令行读入一个输入置于栈顶       |
| OPR 0 14                                    |
  OPR 0 15	 | WRT 0 0	|栈顶值输出至屏幕并换行          |
| OPR 0 0	 | RET 0 0 |                      |
                                   |