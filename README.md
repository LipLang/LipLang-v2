# LIP
```
Lisp语言(LISt Processor)等价于在树状列表(而非线性纸带)上的一种图灵机.
若引入整数, 整个语言可以相应简化, 操作可以更加直接, 思想也可以更加简明.
故此将整数引入核心语言层, 并命名为LIP: (List of Integers) Processor.
```

- `[a]` => `(quote a)`
  + `(get lst 3)`: 获取lst列表的3号元素, 并执行该元素
  + `[get lst 3]`: 获取lst列表的3号元素, 但不执行
- `{x y ...}` => `(quote (x y ...))`
- `,:;` => ` ` (空格)
- `(let fn (& double square))`: 生成函数fn, 该函数的作用是先将数值翻倍, 然后求平方
- `(let triple (^ fn 3))`: 生成函数triple, 该函数的作用是将fn操作重复执行3次

```lisp
;; 定义基本函数
(let double (lambda (x) (* x 2)))
(let square (lambda (x) (* x x)))

;; 列表操作
(let lst {1 2 3 double square})
(print (get lst 1))  ;; 输出: 2
(print ((get lst 3) 5))  ;; 输出: 10
(print [get lst 4])  ;; 输出: square（函数引用）

;; 函数组合
(let double-then-square (& double square))
(let square-thrice (^ square 3))

;; 使用组合函数
(print (double-then-square 3))  ;; 输出: 36
(print (square-thrice 2))  ;; 输出: 256
```

---

DOING: remove `case`, `while`, and replace with data op.

<!--
**LipLang/LipLang** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
