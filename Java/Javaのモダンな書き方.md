# Javaのモダンな書き方

## なぜこれを書いたか

- Javaの資格取得時に自分には知らない機能があった
    - 自分の書き方は古い

## なぜモダンな書き方をする必要があるのか

- 冗長的な書き方を無くして、簡潔なコードになる
    - 処理が追いやすくなる
- バグを発生しにくくなる


## try-with-resources （Java7）

リソースの`close()`を書かなくてもtry句の中を抜けた時に自動でリソースを閉じてくれる。

java.lang.AutoCloseable インタフェースを実装しているオブジェクトであれば使用可能。

メモリリークを防いでくれる。

#### Java7より前

```java

    public static void main(String [] args){

        // プロジェクトフォルダからの相対パスを指定
        File file = new File("test.txt");

        BufferedReader br = null;

        // try-with-resources構文未使用
        try{

            br = new BufferedReader(new FileReader(file));

            String str = br.readLine();

            while(str != null){

                System.out.println(str);
                str = br.readLine();

            }

        }catch (FileNotFoundException e){

            System.out.println(e);

        }catch (IOException e){

            System.out.println(e);

        }finally {

            // finallyにclose()処理が実装されている
            // BufferedReaderがNullの場合があるためclose()前にさらにtryで囲む必要がある
            try {

                br.close();

            }catch (IOException e){

                System.out.println(e);

            }
        }

    }


```

#### Java7

```java

    public static void main(String [] args){

        // プロジェクトフォルダからの相対パスを指定
        File file = new File("test.txt");

        // try-with-resources構文使用
        // BufferedReaderのclose()が記載されていないことを確認
        try(BufferedReader br = new BufferedReader(new FileReader(file))){

            String str = br.readLine();

            while(str != null){

                System.out.println(str);
                str = br.readLine();

            }

        }catch (FileNotFoundException e){

            System.out.println(e);

        }catch (IOException e){

            System.out.println(e);

        }

    }

```


## ラムダ式　（Java8）

匿名クラスで実装していた処理が簡潔に処理できる

## Stream （Java8）

コレクションに対して行っていた煩雑な処理をわかりやすいコードで記述することが可能

#### 処理結果

```
言語名:VB.NET
言語名:Python
言語名:Java
言語名:ECMAScript
言語名:C#
```

#### Java8より前

```java
    /**
     * プログラミング言語を降順に並び替える
     * @param args
     */
    public static void main(String [] args){

        List<String> list = new ArrayList<>();

        list.add("C#");
        list.add("Python");
        list.add("VB.NET");
        list.add("Java");
        list.add("ECMAScript");

        // ラムダ式未使用
        // 匿名クラスでソート処理の実装を行っている
        list.sort(new Comparator<String>() {
            @Override
            public int compare(String o1, String o2) {
                return o2.compareTo(o1);
            }
        });

        // Stream未使用
        // 拡張for文で処理
        for(String str:list){

            System.out.println("言語名:" + str);

        }
    }

```

#### Java8

```java
    /**
     * プログラミング言語を降順に並び替える
     * @param args
     */
    public static void main(String [] args){

        List<String> list = new ArrayList<>();

        list.add("C#");
        list.add("Python");
        list.add("VB.NET");
        list.add("Java");
        list.add("ECMAScript");

        // ラムダ式使用
        list.sort((o1, o2) -> o2.compareTo(o1));

        // Stream使用
        list.stream().map(str -> "言語名:" + str).forEach(s -> System.out.println(s));

    }

```

## Optional （Java8）

Optionalは値をラップし、 その値がnullかもしれないことを表現する

#### Java8より前

```java
    /**
     * 指定したインデックスに格納されている値を出力する
     * Nullの場合は100を出力する
     * @param args
     */
    public static void main(String [] args){

        Integer result = getInteger(2);

        // Optional未使用のためNullチェックをする
        if(result == null){

            result = 100;

        }

        System.out.println(result);

    }

    /**
     * 指定されたインデックスの値を返す
     * @param index
     * @return
     */
    private static Integer getInteger(int index){

        List<Integer>  list = Arrays.asList(new Integer[]{1,2,null});

        return list.get(index);

    }


```

#### Java8

```java
    /**
     * 指定したインデックスに格納されている値を出力する
     * Nullの場合は100を出力する
     * @param args
     */
    public static void main(String [] args){

        Optional<Integer> optional = getInteger(2);

        Integer result = optional.orElse(100);

        System.out.println(result);

    }

    private static Optional<Integer> getInteger(int index){

        List<Integer>  list = Arrays.asList(new Integer[]{1,2,null});

        return Optional.ofNullable(list.get(index));
        
    }
```

## JShell （Java9）

JavaのREPL機能

## Javaのリリースについて


## 参考サイト

- https://qiita.com/Usek/items/3b0ae76a08d2f1678884#%E4%BE%8B%E5%A4%96%E3%81%AE%E3%83%9E%E3%83%AB%E3%83%81%E3%82%AD%E3%83%A3%E3%83%83%E3%83%81

- https://qiita.com/oohira/items/9c13f92815266cc5112c#stream

- https://qiita.com/yuusuke_s/items/a24e1fb056de450a50b2#%E3%83%A9%E3%83%A0%E3%83%80%E5%BC%8F%E3%81%A3%E3%81%A6%E4%BD%95%E3%81%A0%E3%82%8D%E3%81%86

- https://qiita.com/sunadiary/items/e905f8752f6c2da2d8f2