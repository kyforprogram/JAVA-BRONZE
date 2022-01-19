#試験合格するまでのメモとして活用

##JAVA黒本Bronzeの問題集の進め方
１章→２章→３章→４章→６章→７章→５章で解いていくのをお勧めする
理由はすっきりわかるJAVA入門書にそって解いていけるから
５章はとりあえず最後に解いた方がいい！！
まぁ人それぞれだけど。。。

#7章　オブジェクト指向
##オブジェクト指向を学ぶ理由
大規模開発が可能になって開発者自身がその内容を把握しきれなくなる課題が発生　　
人間の頭が開発に追いつかない(´;ω;｀)
開発のボトルネックになる　　
###そこでObject Oriented Programming = OOP  
が誕生！！！！　　


##オブジェクト指向の定義　　
ソフトウェア開発の部品化  
##オブジェクト指向のメリット
ラクに、楽しく、いいものを

#オブジェクトの姿7.4.2
属性 = 情報
操作 = 動作

#三代機能7.5
##継承
過去に作った部品を使って新機能を作れる

##多様性「ポリモーフィズム」
似ている部品を同じようなものとみなして使う

##カプセル化
属性や操作の利用を制限させる

#8章　インスタンスとクラス
##8.1.1 オブジェクトを生み出す手順
①各オブジェクトが負うべき責務を考え、属性や操作の内容を定義する　　
②仮想世界に生み出して、動かす

##8.1.2 クラスとオブジェクト
>https://freesworder.net/class-instance-object/
クラスとオブジェクトとインスタンスの違いがなんとなくわかるサイト

##8.2 クラスの定義
UML　Unfied Modeling Language  

|   勇者  |クラス名|
| :----: |:----:|
|  名前<br>HP  |属性| 
|  戦う<br>寝る<br>座る<br>転ぶ<br>逃げる  |操作|


```java
public class Hero{
 //属性の定義↓
 String name;
 int hp;
 //操作の定義↓
 public void attack () {}
 public void sleep () {}
 public void sit () {}
 public void slip () {}
 public void run () {}
}
```

##8.2.3 属性宣言

下記のようにクラスブロック内に宣言された変数をJAVAでは<span style="color: red; "><strong>フィールド</strong></span>という

``` java
public class Hero{
 //属性の定義↓
 String name;
 int hp;
}
```

##8.2.4初期値指定と定数フィールド

```java
public class Hero{
 //初期値を10と指定
 int level = 10;

 //定数フィールドとはfinalを先頭につけて変数名を大文字にする
 final int LEVEL = 10;
 大文字にすることでわかりやすいようにする
}
```

##8.3クラス定義による効果
１．クラスに基づいて、インスタンスを生成できる
２．クラスから生まれたインスタンスを入れる変巣の方が利用できる
>クラス型：Hero「勇者」型というデータ型を「持つ　又は　作る」ことができる

```java
Hero h;
```

>クラス型変数を用いる理由は
>複数の同名インスタンスから特定のインスタンスをプログラムとして識別するため

##8.4.2インスタンス生成

>　クラス名　変数名 = new クラス名();

```java
public class Main{
 public static void main (String [] args){
  Hero h = new Hero();
 }
}
```

##8.4.3インスタンスのフィールド利用

>　変数名.フィールド名 = 値;

```java
public class Main{
 public static void main (String [] args){
  Hero h = new Hero();
  h.name = "minato";
  h.hp = 100;

 }
}
```

##9様々なクラス
ヒープとはJVMがプログラムを実行する際にコンピューターのメモリ領域を確保する事
Hero h = new hero();
実際には　Hero型のhに代入されて作られたhero();インスタンスがコンピューターの一部のメモリ確保している

箱とかという概念が大事
自分は何となく駅とかにあるロッカーみたいなものと捉えている。
１番のロッカーにはHero型hという領域がJVMによって確保される
２番ロッカーにheroクラスがある
２番のHeroのクラスにはnameやhpがある
Hero hになにが代入されているのか？
２番ロッカーを開けて（参照）みることでわかる

##9.2コンストラクタ
フィールド初期値

|型|初期値|
|:----:|:----:|
|int,short,long|0|
|char|¥u0000|
|boolean|false|
|int[]|null|
|String|null|

##9,2,3コンストラクタの定義
メゾット名がクラス名と一致
メゾット宣言に戻り値が記述されていない（voidもダメ）

> ###new Hero();でコンストラクタが実行されるには

>```java
>public class Hero{
> public Hero(){
> this.hp = 100; //hpに100を代入
> { 
>}
>```


##コンストラクタとオーバーロード
引数を渡すことも可能でオーバーロード（多重定義）も可能

コンストラクタは
###引数の型・数・順番
に一致するコンストラクタが動作する

```java
public class Main {
    public static void main(String[] args) throws Exception {
        // Your code here!
        
        Hero h = new Hero("minami");
        System.out.println(h.name);
        Hero h1 = new Hero();
        System.out.println(h1.name);
    }
}
```

```java
public class Hero {
    String name;
    int hp;
    
    public Hero(String name){
        this.hp = 100;
        this.name = name;
    }
    
    public Hero(){
        this.hp = 100;
        this.name = "初期値";
    }
}
```

>実行結果
>minami
>初期値

##コンストラクタの特例
全てのクラスはインスタンス化に際して必ず何らかのコンストラクタを実行することになっている。
クラスにコンストラクタが定義されていなかった場合はデフォルトコンストラクタが自動的に追加される

##同一クラスの別のコンストラクタを呼び出す方法
>this(引数）；

this.nameと混同しないように
this.name = nameで右辺のnameの引数を受け取り左辺のnameに代入できた
だが
this("namae");は別のコンストラクトを実行するためにある

```java
public class Hero {
    String name;
    int hp;
    
    public Hero(String name){⓵コンストラクタ
        this.hp = 100;
        this.name = name;
    }
    
    public Hero(){⓶コンストラクタ
        this("JAVA");⓵のコンストラクトを呼び出す
    }
}
```

##9練習問題

```java
public class Thief {
    String name;
    int hp;
    int mp;
    
    //一個目のコンストラクトは名前とHPとmpを指定できる
    public Thief(String name, int hp, int mp){
        this.name = name;
        this.hp = hp;
        this.mp = mp;
    }
    
    //二個目のコンストラクトは名前とhpを指定できる
    //mpは５で指定
    //Thief("二浪",80);
    public Thief(String name, int hp) {
        this(name, hp, 5);//一個目のコンストラクトに引き継ぐ
    }
    //二浪,80,
    
    //三個目のコンストラクトは名前だけ指定できる
    //Thief("三郎")
    public Thief(String name){
        this(name, 40);//二個目のコンストラクトに引き継いでもらいmp5を代入してもらう
    }
    //三郎,40,5と表示されるように   
}
```

#10章　継承
##extends
SuperHeroクラスはHeroクラスをベースにして定義したい場合はextendsを使う

```java
public class Hero {
:親クラス
:スーパークラス
 public void run(){
 }
}

public class SuperHero extends Hero {
:子クラス
:サブクラス
 public void run(){オーバーライドできる
 }
}
```

###多重継承
子クラスは親クラスを何個も継承できないけど
親クラスから子クラスには複数継承することができる
Hero→SuperHero〇
Hero→HyperHero〇

　　　　／Hero✖
People
　　　　＼Demon✖

##10.2.3親インスタンスにアクセス
###親インスタンス部分のフィールドを利用する
super.フィールド名
###親インスタン部分のメゾットを呼び出すには
super.methods(arg)

```java
public class SuperHero extends Hero {
    public void attack(Matango m){
        super.attack(m);
        if (this.flying){
            super.attack(m);親インスタンスのattack()が呼び出せる
        }
    }
}
```


## 情報隠蔽
公開すべき物と非公開にする物でわける
そのためには、密結合してるとわからないから
間に公開するインターフェイスを作成

パッケージ宣言をする
パッケージをわけることでアクセス制御ができるから

コンストラクタをprotectedにする
データ隠蔽が外部からアクセスできないようにすること
フィルード


##データ隠蔽と情報隠蔽の違い
データはアクセス拒否、制御する
情報隠蔽は公開、非公開をわける

##ポリモーフィズムの利点
変更を極小化して使える


## proteced private publicについて
public 全てのクラスからアクセス可能
protected　
none
private



##戻り値の例
``` java
public class Main{
 public static int add (int x, int y){
 int ans = x + y;
 ⓶return ans;
 }
 
 pubic static void main (String[] args) {
 ⓵まずadd();のメゾットが実行され、引数に100と10が渡る
 ⓶add()で処理され、戻り値returnによって帰ってきた値がandに代入される
 int ans = ⓵add(100, 10);
 System.out.println("100+10=" + ans);
 }
}
```



##クラス命名規則
$と英語が一文字目使える
その他に使えるのが＿「アンダーバー」

##シグニチャを構成する要素
引数の数
引数の型
メゾット名
引数の順番

##パッケージに関する説明
　名前空間を提供する
　アクセス制御を提供する
　クラスの分類を可能にする





##勉強日記 
###1日目はjavaなんて簡単よ～
1章2章暗記系が多いな・・・
###2日目は暗記系が多いけど暗記系なら覚えるだけや
3章4章は演算とかループ文
rubyの知識だけでも解けた！
###3日目はチンプンカンプン
5章は一通りすっきりわかるJAVA入門を読んでおかないとわからないな
###4日目少し躓き始める
すっきりわかるJAVA入門書を読み始める
最初から読んでおくべきだったかも...
一通り目を通して6.7章を解いてみると
黒本の進め方に気が付く1.2.3.4.6.7.5章と左から順に進めていくのがいいと気づく
###5日目復習していく
苦手な問題の箇所を読んだり解いていく必要があるな～
コンストラクトとオーバーロード、継承、ポリモーフィズム、抽象化、オーバーライド
