# HUAWEI

### 1.HW1:

next() 和 nextLine()的区别

next()方法读取到空白符就结束l；

nextLine()读取到回车结束也就是“\r”；

### 3. HW3  

```java
去重方法
ArrayList<Integer> list = new ArrayList<>();
HashSet<Integer> set = new HashSet<>(list);
list.clear();
list.addAll(set);
System.out.println(list);
```

```java
import java.util.*;

public class HW3 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();  //输入的个数
        Random random = new Random();
//        System.out.println(r);
        ArrayList<Integer> list = new ArrayList<>();
        //生成随机数
        for (int i = 0; i < n; i++) {
            int r = random.nextInt(1000)+1;  //从1到1000
            list.add(r);
        }
//        System.out.println(list);
        Collections.sort(list); // 需要在 ArrayList<Integer> list 把 Integer 加上
        System.out.println(list);
        HashSet<Object> set = new HashSet<>(list);
//        System.out.println(set);
//        list.sort();
        System.out.println(set);
    }
}
```

### 4. HW4

注意这个 List 如果想要取出元素的话需要用到get方法

### 5. HW5

sc.next().subString(2); 表示去掉前面两个字符后得到的字符串

parseint( , ) 就是将字符串变成数字的函数 第二个参数是基数(之后你想变成的几进制的数) 

int n = Integer.parseInt()

### 7. HW7

```java
import java.lang.reflect.Type;
import java.util.Scanner;

public class HW7 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        float f = sc.nextFloat();
        String str = Float.toString(f);
//        System.out.println(str);
        String a = "6.3";
        String[] split = a.split(".");
        System.out.println(split[0]);
//        String[] split = str.split(".");
//
//        System.out.println(split.length);
    }
}
```

 判断类型 str instanceof String 只有String才能变成Charrray() 所以要将int变成string
 str.contains(chars[i]+"") 

注意这个chars[i] 必须加上一个 ""
可以用str.caontains()方法去重

##### ASCII:   A 65-90  a 97-122



##### split("\\s+") 和 split(" +") 有什么区别?

"hello world, this is Al".split("\\s+")

首先要明白split方法的参数含义：
split
public String[] split(String regex)根据给定的正则表达式的匹配来拆分此字符串。 

然后就要明确正则表达式的含义了：
\\s表示   空格,回车,换行等空白符,    
 +号表示一个或多个的意思,所以...

数据结构“双向链表”比较满足。将句子的每个单词依次放到双向链表头部，最后从链表头部依次遍历出单词即可达到句子反向的目的。

```java
String[] split = str.split("\\s+"); // 可以根据空格分成多个 存数组里面
Deque<String> list = new LinkedList<>();//定义一个双向链表  必须加上这个String的范型
```

Java中的LinkedList底层使用的就是双向链表。

Deque的含义是“double ended queue”，即双端队列，它既可以当作栈使用，也可以当作队列使用。
使用java.util.Deque双端队列来实现队列与栈的各种需求.方法结合了栈和队列
String.join()方法是JDK1.8之后新增的一个静态方法

参数列表：

　　1、表示连接的符号

　　2、表示被连接的数组（也可以是集合），或者是要连接的多个字符串

Arrays.sort()里面存放的是数组 
String se = Integer.toBinaryString(n);default V getOrDefault(Object key, V defaultValue) {
        V v;
        return (((v = get(key)) != null) || containsKey(key))
            ? v
            : defaultValue;
    }



这是源码，意思就是当Map集合中有这个key时，就使用这个key值，如果没有就使用默认值defaultValue

下面就具体的例子，再说明一下：

```java
public class Demo13 {
    public static void main(String[] args) {
        Map<String, String> map = new HashMap<>();
        map.put("name", "lxj");
        map.put("age", "24");
        map.put("sex", "女");
        String name = map.getOrDefault("name", "test");
        System.out.println(name);// lxj，map中存在name,获得name对应的value
        String address = map.getOrDefault("address", "北京");
        System.out.println(address);// 北京，map中不存在address,使用默认值“北京”
    }
}


```

### 20. HW20

```java
public class HW20 {
    public static void main(String[] args) {
        System.out.println("-------continue测试----------");
        for (int i = 0; i < 5; i++) {
            if (i == 2) {
                System.out.println("跳过下面输出语句，返回for循环");
                continue;
//                System.out.println("无法执行到这里");  直接报错
            }

            System.out.println(i);
        }

        System.out.println("----------break测试----------");
        for (int i = 0; i < 5; i++) {
            if (i == 2) {
                System.out.println("跳过下面输出语句，返回for循环");
                break;
            }
            System.out.println(i);
        }
    }
}
```

大写到小写的变换 ***+32*** A->a

比较字母出现的次数时 可以用一个长度为26的数组存储次数
 //记录所有字符的次数

```java
for (int i = 0; i < str.length(); i++) {
                times[str.charAt(i)-'a']++;
}
```

涉及到将数字转换成英文表示 要创建一个从zero 到 ninteen 的字符串数组 

注意hundred 后面要加上一个 and 