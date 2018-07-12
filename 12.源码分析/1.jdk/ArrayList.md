## 类图
![](http://p6m5e5j2t.bkt.clouddn.com/18-5-24/63415057.jpg)

它是线程不安全的，允许元素为null.因其底层数据结构是数组，所以可想而知，它是占据一块连续的内存空间（容量就是数组的length），所以它也有数组的缺点，空间效率不高.由于数组的内存连续，可以根据下标以O1的时间读写(改查)元素，因此时间效率很高。
当集合中的元素超出这个容量，便会进行扩容操作。扩容操作也是ArrayList 的一个性能消耗比较大的地方，所以若我们可以提前预知数据的规模，应该通过public ArrayList(int initialCapacity) {}构造方法，指定集合的大小，去构建ArrayList实例，以减少扩容次数，提高效率。
或者在需要扩容的时候，手动调用public void ensureCapacity(int minCapacity) {}方法扩容。不过该方法是ArrayList的API，不是List接口里的，所以使用时需要强转:((ArrayList)list).ensureCapacity(30);
当每次修改结构时，增加导致扩容，或者删，都会修改modCount。

## ArrayList源码剖析
### ArrayList定义

```java
public class ArrayList<E> extends AbstractList<E>
        implements List<E>, RandomAccess, Cloneable, java.io.Serializable {}     
```

ArrayList本质上是一个数组，但是与Java中基础的数组所不同的是，它能够动态增长自己的容量。
通过ArrayList的定义，可以知道ArrayList继承了AbstractList，同时实现了List,RandomAccess,Cloneable和java.io.Serializable接口
继承了AbstractList类，实现了List，意味着ArrayList是一个数组队列，提供了诸如增删改查、遍历等功能。

实现了RandomAccess接口，意味着ArrayList提供了随机访问的功能。RandomAccess接口在Java中是用来被List实现，用来提供快速访问功能的。在ArrayList中，即我们可以通过元素的序号快速获取元素对象。

实现了Cloneable接口，意味着ArrayList实现了clone()函数，能被克隆。

实现了java.io.Serializable接口，意味着ArrayList能够通过序列化进行传输。

### ArrayList关键属性

```java
private static final int DEFAULT_CAPACITY = 10;
transient Object[] elementData;
private int size;
```
1. ArrayList的默认容量为10；
2. elementData是"Object类型的数组"，所有ArrayList元素都保存在elementData中。在ArrayList中，elementData是一个动态数组。需要注意的是，ArrayList通过构造函数ArrayList(int initialCapacity)定义初始量initialCapacity；
3. size是动态数组的实际大小。

### ArrayList构造函数
```java
//ArrayList带容量的构造函数
public ArrayList(int initialCapacity) {
    if (initialCapacity > 0) {
    //新建一个容量为initialCapacity的数组
        this.elementData = new Object[initialCapacity];
    } else if (initialCapacity == 0) {
        this.elementData = EMPTY_ELEMENTDATA;
    } else {
        throw new IllegalArgumentException("Illegal Capacity: "+
                                           initialCapacity);
    }
}
//ArrayList默认构造函数，默认为空
public ArrayList() {

    this.elementData = DEFAULTCAPACITY_EMPTY_ELEMENTDATA;
}
// 构造一个包含指定元素的list
public ArrayList(Collection<? extends E> c) {
    elementData = c.toArray();
    if ((size = elementData.length) != 0) {
        if (elementData.getClass() != Object[].class)
            elementData = Arrays.copyOf(elementData, size, Object[].class);
    } else {
        this.elementData = EMPTY_ELEMENTDATA;
    }
}
```

第一个构造方法使用提供的initialCapacity来初始化elementData数组的大小。
第二个构造方法默认数组为0。
第三个构造方法则将提供的集合转成数组返回给elementData（返回若不是Object[]将调用Arrays.copyOf方法将其转为Object[]）

### ArrayList主要方法源码剖析
#### 增加
```java
public boolean add(E e) {
    //扩容判断
    ensureCapacityInternal(size + 1);  // Increments modCount!!
    elementData[size++] = e;
    return true;
}

public void add(int index, E element) {
    //判断index是否越界，错误产生IndexOutOfBoundsException
    rangeCheckForAdd(index);
    //进行扩容检查
    ensureCapacityInternal(size + 1);  // Increments modCount!!
    //对数组进行复制，将空出的Index位置出入element，并将index后的所有数据后移一个位置。
    System.arraycopy(elementData, index, elementData, index + 1,
                     size - index);
    //将index上的数据设置为element
    elementData[index] = element;
    //容量+1
    size++;
}
```
#### 删除
```java
public E remove(int index) {
    //边界检查
    rangeCheck(index);
        
    modCount++;
    //oldValue即要删除的元素
    E oldValue = elementData(index);
    //要复制的元素
    int numMoved = size - index - 1;
    if (numMoved > 0)
        System.arraycopy(elementData, index+1, elementData, index,
                         numMoved);
    //释放最后一个元素
    elementData[--size] = null; // clear to let GC do its work

    return oldValue;
}

public boolean remove(Object o) {
    //对o进行判断
    if (o == null) {
        for (int index = 0; index < size; index++)
            if (elementData[index] == null) {
                fastRemove(index);
                return true;
            }
    } else {
        for (int index = 0; index < size; index++)
            if (o.equals(elementData[index])) {
                fastRemove(index);
                return true;
            }
    }
    return false;
}
```

#### 更新
```java
public E set(int index, E element) {
    //数组扩容
    rangeCheck(index);
    //获取要更新的位置的数据
    E oldValue = elementData(index);
    //更新元素
    elementData[index] = element;
    return oldValue;
}

```
### 总结
1.ArrayList底层是通过数组来保存数据的。默认的容量是10.
2.JDK1.8中，ArrayList扩容使用位运算newCapacity = oldCapacity + (oldCapacity >> 1)
3.ArrayList实现java.io.Serializable的方式。当写入到输出流时，先写入“容量”，再依次写入“每一个元素”；当读出输入流时，先读取“容量”，再依次读取“每一个元素”。