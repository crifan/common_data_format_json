# JSON常见问题

## JSON中不支持多行字符串

结论是：

JSON语法规范本身就说了：

* 不能包含换行符
  * 换行符属于：`控制字符`=`control character`
  * JSON规范就不支持`控制字符`
  * JSON规范支持`\n`（这是两个字符）

规避办法：

* 方案1：把 单个的表示换行的控制字符`\n` ，保存为 `"\n"`（2个字符，一个是`反斜杠`，一个是字母`n`）
  * 这样前端，比如web端，小程序段，移动端等，自己再去替换"\n"为\n
  * 比如：
    * `"this is first line 此处想要换行and second line"`
    * 保存为：
    * `"this is first line \nand second line"`
* 方案2：把包含换行的字符串，保存为字符串列表，每个字符串是换行后的某一行
  * 比如：
    ```bash
    "this is first line
    and second line"
    ```
  * 保存为：
    ```json
    [
      "this is first line"
      "and second line"
    ]
    ```

