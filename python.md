## Clojure
- 参照時はローカル、呼び出しもとの関数、呼び出しもと・・・と辿っていく（スコープチェーン）
- 代入時はローカルに無ければローカル変数新規定義となる
- jsは代入時も辿る
`# Python`
```
def f():
    a = False
    def f2():
        a = True
    f2()
    return a


y = f()
print('y:', y)
```
`>>> y:False`
`// Js`
```
function f() {
    let a = false
    function f2() {
        a = true
    }
    f2()
    return a
}

let y = f()
console.log('y:', y)
```
`>>> y:true`
