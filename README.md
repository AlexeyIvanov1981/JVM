# JVM
### «JVM. Организация памяти, сборщики мусора, VisualVM»

~~~java
public class JvmComprehension {

    public static void main(String[] args) {
        int i = 1;                      // 1
        Object o = new Object();        // 2
        Integer ii = 2;                 // 3
        printAll(o, i, ii);             // 4
        System.out.println("finished"); // 7
    }

    private static void printAll(Object o, int i, Integer ii) {
        Integer uselessVar = 700;                   // 5
        System.out.println(o.toString() + i + ii);  // 6
    }
}
~~~
### Разбор кода

~~~java
    public class JvmComprehension {

        public static void main(String[] args) {
            int i = 1;        
~~~
>1) В стэке создается фрейм метода **main**, инициализиреутся переменная **'i'** типа **int** со значением 1.

~~~java
        Object o = new Object();
~~~
>2) В хипе создается объект типа **Object**, во фрейме **(main)** создается переменная **'о'** которой присваевается ссылка на этот объект.

~~~java
        Integer ii = 2;    
~~~
>3) В хипе создается объект типа **Integer**, во фрейме **(main)** создается переменная **'ii'** которой присваевается ссылка на этот объект. 

~~~java
        printAll(o, i, ii);
~~~
>4) В стэке создается фрейм метода **printAll**, в нем создаются переменные **'о'**, **'ii'** которым присваиваются ссылки объектов находящиеся в хипе и инициализируется переменная **'i'** типа **int** со значением 1.

~~~java
        System.out.println("finished"); 
    }
~~~
>7) Создается новый фрейм.

~~~java
        private static void printAll(Object o, int i, Integer ii) {
        Integer uselessVar = 700;    
~~~
>5) В хипе создается объект типа **Integer**, в стеке создается фрейм метода **printAll** в котором создается переменная **uselessVar** со ссылкой на этот объект в хипе.

~~~java
        System.out.println(o.toString() + i + ii);
        }
    }
~~~
>6) Создается новый фрейм создаются переменные **'о'** и **'ii'** куда передаются ссылки на объекты в хипе, инициализируется переменная **'i'** типа **int** со значением 1.
