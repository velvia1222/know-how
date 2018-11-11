# スライス
- シーケンスから部分集合を取得する
- 先頭、末尾の0は省略可能。負数も可能
- stride（増分）も可能だが可読性に注意

# 高階関数
- mapは関数とシーケンスを引数にとり、各要素に関数を適用したシーケンスを作成する
- filterは関数とシーケンスを引数にとり、関数の条件に一致するシーケンスを作成する
- zipは二つのシーケンスを引数にとり、各シーケンスの要素のタプルのシーケンスを作成する

# ジェネレータ式
- ジェネレータ式（リスト内包表記の書き方で[]を()にする）を使用すると、メモリが節約される
- ジェネレータ式は連鎖可能
`it2 = ((x, x**0.5) for x in it)`

# イテレータ
- イテレータは一度しか値を返却しない
- 一度終わったイテレータを再度呼び出してもStopIteration例外は出ない

# enumerate
- enumerateはシーケンスを引数にとって添字と要素を返却する
```
for i, host in enemerate(hosts):
    pass
```

# 比較
- ==はオブジェクトの内容を比較、isは参照を比較
- Noneかどうかを比較する時はisを使用する

# 引数
- 引数のデフォルト値に空配列を指定すると、複数回呼び出された際に配列が引き回されてしまうため、デフォルト値にNoneを指定しておいて値がNoneの場合に空配列を代入する
- 引数に*を指定すると、*以降の引数はキーワード専用引数となる

# namedtuple
- 名前付きのタプルを作成できる
- デフォルト値は指定できない

# クラス
- __call__を定義すると、インスタンスを関数のように実行できる
- 親クラスの__init__は自動では呼び出されない。明示的にsuper().__init__を実行する

# Clojure
- 参照時はローカル、呼び出しもとの関数、呼び出しもと・・・と辿っていく（スコープチェーン）
- 代入時はローカルに無ければローカル変数新規定義となる
- jsは代入時も辿る
```
# Python
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

# 親子でインスタンス変数名が重複した場合
```
// Java
class Parent {
    private String value;

    public Parent() {
        System.out.println("Parent construct");
        this.value = "Parent";
    }

    public String getParentValue() {
        return this.value;
    }
}

class Child extends Parent {
    private String value;

    public Child() {
        this.value = "Child";
    }

    public String getChildValue() {
        return this.value;
    }
}

public class Main {
    public static void main(String[] args) {
        Child child = new Child();
        System.out.println("Parent value:" + child.getParentValue());
        System.out.println("Child value:" + child.getChildValue());
    }
}
```
```
Parent construct
Parent value:Parent
Child value:Child
```
```
class Parent:
    def __init__(self):
        print('Parent construct')
        self._value = 'Parent'

    def get_parent_value(self):
        return self._value


class Child(Parent):
    def __init__(self):
        self._value = 'Child'

    def get_child_value(self):
        return self._value


child = Child()
print('Parent value:' + child.get_parent_value())
print('Child value:' + child.get_child_value())
```
```
Parent value:Child
Child value:Child
```
```
class Parent:
    def __init__(self):
        print('Parent init')
        self.__value = 'Parent'

    def get_parent_value(self):
        return self.__value


class Child(Parent):
    def __init__(self):
        super().__init__()
        self.__value = 'Child'

    def get_child_value(self):
        return self.__value


child = Child()
print('Parent value:' + child.get_parent_value())
print('Child value:' + child.get_child_value())
```
```
Parent init
Parent value:Parent
Child value:Child
```

# 並行実行
- Pythonでマルチスレッドで実行しても、Global Interpreter Lockのせいでマルチコアを活用できない
