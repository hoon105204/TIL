# 컬렉션(Collection)

- 메모리상에서 자료를 구조적으로  처리하는 방법을 *자료구조라* 일컫는데 *컬렉션(Collection)*은 자바에서 제공하는 자료구조를 담당하는 프레임워크
- 추가, 삭제, 정렬 등의 기능처리가 간단하게 해결되어 자료구조적 알고리즘을 구현할 필요 없음
- `java.util`패키지에 포함되며, 인터페이스를 통해 정형화된 방법으로 다양한 컬렉션 클래스 이용 가능

**배열의 문제점**

   	1. 한 번 크기를 정하면 변경할 수 없음
   	2. 배열에 기록된 데이터에 대한 중간 위치의 추가, 삭제가 불편
   	   - 추가, 삭제할 데이터부터 마지막 기록된 데이터까지 하나씩 뒤로 밀어내고 추가해야함
   	1. 한 타입의 데이터만 저장 가능

**컬렉션의 장점**

 	1. 저장하는 크기의 제약이 없다.
 	2. 추가, 삭제 ,정렬 등의 기능 처리가 간단하게 해결된다.
 	 - 자료를 구조적으로 처리하는 자료구조가 내장되어 있음
 	3. 여러 타입의 데이터가 저장 가능하다.
 	 - 객체만 저장할 수 있기 때문에 필요에 따라 기본 자료형을 저장해야 하는 경우 Wapper 이용

**컬렉션의 주요 인터페이스**

<table>
    <tr>
    	<td colspan="2" style="color: withe; font-weight: bold; text-align: center; background-color: black">인터페이스 분류</td>
    	<td style="color: withe; font-weight: bold; text-align: center; background-color: black">특징</td>
        <td style="color: withe; font-weight: bold; text-align: center; background-color: black">구현 클래스</td>
    </tr>
    <tr>
        <td rowspan="2">Collection</td>
        <td>List 계열</td>
        <td>-순서를 유지하고 저장<br>- 중복 저장 가능</td>
        <td>ArrayList, Vector, LinkedList</td>
    </tr>
    <tr>
        <td>Set 계열</td>
        <td>-순서를 유지하지 않고 저장<br>- 중복 저장 안됨</td>
        <td>HashSet, TreeSet</td>
    </tr>
    <tr>
        <td colspan="2">Map 계열</td>
        <td>- 키와 값의 쌍으로 저장<br>- 키는 중복 저장 안됨</td>
        <td>HashMap, HashTable, TreeMap, Properties</td>
    </tr>
</table>
## List

- 자료를 순차적으로 나열한 자료구조로 인덱스로 관리되며, 중복해서 객체 저장 가능

**ArrayList**

- List의 후손으로 초기 저장 용량은 10으로 자동설정 되며 저장용량을 초과한 객체가 들어오면 자동으로 늘어남
- 동기화를 제공하지 않음
- ex) `List<E> list = new ArrayList<E>();`

```java
import java.util.ArrayList;
import java.util.Collections;

public void testArrayList() {
    // ArrayList

    ArrayList alist = new ArrayList();
	// add를 통해 객체 추가
    alist.add("apple");
    alist.add(123);
    alist.add(45.67);
    
    Collections.sort(alist); // sort를 통해 정렬
    System.out.println(alist.get(2)); // get 주어진 인덱스에 저장된 객체 리턴(시작 0)
}
```

**LinkedList**

- 리스트의 후손으로, 인접 참조를 링크해 체인처럼 관리
- 특정 인덱스에서 객체를 제거하거나 추가하게 되면 바로 앞/뒤 링크만 변경하면 되기 때문에 객체 삭제와 삽입이 빈번하게 일어나는 곳에서는 ArrayList보다 성능이 좋음
- ex) `List<E> list = new LinkedList<E>();`

### 🔸Comparable, Comparator

> Comparable : 정렬 수행시 기본적으로 적용되는 정렬 기준이 되는 메서드를 정의하는 인터페이스
> Comparator : 정렬 가능한 클래스들의 <b>기본 정렬 기준과 다르게 정렬</b>하고 싶을때 사용하는 인터페이스

<table>
	<tr>
    	<td style="background: black;"></td>
        <td style="background: black; text-align:center;"><b>Comparable</b></td>
        <td style="background: black; text-align:center;"><b>Comparator</b></td>
    </tr>
    <tr>
    	<td style="background: black; text-align:center;"><b>패키지</b></td>
        <td style="text-align: center;">java.lang</td>
        <td style="text-align: center;">java.util</td>
    </tr>
    <tr>
    	<td style="background: black; text-align:center;"><b>사용 메서드</b></td>
        <td style="text-align: center;">compareTo()</td>
        <td style="text-align: center;">compare()</td>
    </tr>
    <tr>
    	<td style="background: black; text-align:center;"><b>정렬</b></td>
        <td>기존의 정렬기준을 구현하는데 사용</td>
        <td>그 외 다른 여러기준으로 정렬하고자 할 때 사용</td>
    </tr>
    <tr>
    	<td style="background: black; text-align:center;"><b>사용법</b></td>
        <td>정렬하고자 하는 객체에 Comparable를 상속받아<br>compareTo()메서드를 오버라이딩해 기존의 정렬 기준 재정의<br>→ 한 개의 정렬만 가능</td>
        <td>vo 패키지 안에 필요한 정렬 기준에 맞춘<br>클래스들을 생성하고 Comparator를 상속받아<br>compare()메서드를 오버라이딩해 기존의 정렬 기준 재정의<br>→ 여러 개의 정렬 가능</td>
    </tr>
</table>

```java
// [1] CompareTo() ▶ 정렬 실행 : Collections.sort(리스트);
public class Score implements Comparable{
	private String name;
	private int score;
	
	public Score() {}
    // name을 기준으로 오름차순 정렬하도록 compareTo() Override
    @Override
	public int compareTo(Object o) {
		String otherName = ((Score)o).getName();
		return name.compareTo(otherName);  
		// 오름차순 기준으로
		// 나.compareTo(가)면 양수가 나오고 자리바꾸기가 실행됨 즉 오름차순으로 정렬됨
		// 내림차순으로 하고싶으면 (-)부호 하나만 넣어주면 됨
	}
}

// [2] Comparator ▶ 정렬 실행 : Collections.sort(리스트, new AscScore());
// 기준이 되는 객체 AscScore의 방법대로 '리스트'를 정렬 가능
public class AscScore implements Comparator{

	@Override
	public int compare(Object o1, Object o2) {
		// 점수 오름차순
		int other1 = ((Score)o1).getScore();
		int other2 = ((Score)o2).getScore();
		
		if(other1>other2) { //내림차순 이용시 if(other1<other2) 사용
			return 1;
		} else {
			return -1;
		}
	}
}
```

## Set

- 저장 순서가 유지되지 않고, 중복 객체도 저장하지 못하게 하는 자료구조
- null도 중복을 허용하지 않기 때문에 1개의 null만 저장

```java
import java.util.Date;
import java.util.HashSet;
import java.util.Iterator;

public class HashSetTest {
	
	public void testHashSet() {
		HashSet hset = new HashSet();
		// .add() 객체 추가
		hset.add("java");
		hset.add(123);
		hset.add(45.67);
		hset.add(new Date());
		hset.add(123);
		hset.add(123);
		
		System.out.println("hset: " + hset);
		System.out.println("저장된 객체수: " + hset.size());
		
		// 1. toArray() 통해 배열로 바꾼뒤 원소 확인
		Object[] arr = hset.toArray();
		for(int i=0; i<arr.length; i++) {
			System.out.println(i + " : " + arr[i]);
		}
		
		// 2. Iterator()를 이용하여 저장된 객체를 한번씩 가져옴
		Iterator iter = hset.iterator();
		
		while(iter.hasNext()) {
			System.out.println(iter.next());
		}
		
		hset.remove("java");// 하나씩 지우고
		hset.clear();		// 다지우고
		System.out.println(hset);
		
		// 사용자 정의 객체를 넣을 수 있음
		hset.add(new Score("lee",23,63));
		hset.add(new Score("kim",55,40));
		hset.add(new Score("bin",73,14));
		hset.add(new Score("zin",35,88));
		
		System.out.println("hset: " + hset);
	}
}
```

## Map

- 키(key)와 값(value)으로 구성되어 있으며, 키와 값은 모두 객체
- 키는 중복 저장을 허용하지 않고(Set방식), 값은 중복 저장 가능(List방식)
- 키가 중복되는 경우, 기존에 있는 키에 해당하는 값을 덮어 씌움

```java
import java.util.Collection;
import java.util.Date;
import java.util.HashMap;
import java.util.Iterator;
import java.util.Map;
import java.util.Set;

public class HashMapTest {
	
	public void testHashMap() {
		HashMap hmap = new HashMap();
		
		hmap.put("one",new Date());
		hmap.put(12,"red");
		hmap.put(34, 33.56);
		
		System.out.println("hmap: " + hmap);
		
		// 키값이 같으면 벨류가 덮어씌워진다
		hmap.put(12, "yellow");
		System.out.println("hmap: " + hmap);
		
		// 키값만 중복이되지 않으면 벨류가 중복되더라도 상관없음
		hmap.put("wow", "yellow");
		System.out.println("hmap: " + hmap);
		
		System.out.println("key 12에 대한 value: " + hmap.get(12));
		System.out.println("key 12 삭제"+hmap.remove(12));
		System.out.println("hmap: " + hmap);
		
		System.out.println("저장된 객체 수: " + hmap.size());
	}
	
	public void testHashMap2() {
		
		HashMap hmap = new HashMap();
		
		hmap.put("one", "variable");
		hmap.put("two", "Operator");
		hmap.put("three", "if");
		hmap.put("four", "switch");
		hmap.put("five", "while");
		
		// 1. keySet() : 키만 따로 Set으로 만든다.
		Set keys = hmap.keySet();
		Iterator keyItor = keys.iterator();
		
		System.out.println("====key, value====");
		while(keyItor.hasNext()) {
			String key = (String)keyItor.next();
			String value = (String)hmap.get(key);
			
			System.out.println("(" +key+ ", " +value+ ")");			
		}
		
		// 2. entrySet() : 내부클래스이며 entry만 set으로 만든다.
		Set set = hmap.entrySet();
		Iterator entryIter = set.iterator();
		while(entryIter.hasNext()) {
			Map.Entry entry = (Map.Entry)entryIter.next();
			System.out.println(entry.getKey() + " : " + entry.getValue());
		}
				
		// 3. values() : Collection 타입으로 가져옴
		Collection values = hmap.values();
		
		// 3-1. Iterator
		Iterator valueIter = values.iterator();
		while(valueIter.hasNext()) {
			System.out.println(valueIter.next());
		}
		
		// 3-2. toArray
		Object[] vArr = values.toArray();
		for(int i=0; i<vArr.length; i++) {
			System.out.println(vArr[i]);
		}		
	}
}
```

## Properties

- 키와 값을 String 타입으로 제한한 Map 컬렉션
- 주로 Properties는 프로퍼티 파일을 읽어 들일 때 주로 이용

```java
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.FileWriter;
import java.io.IOException;
import java.util.Properties;

public class PropertiesTest {
	
	public void test1() {
		// properties 생성후 외부파일로 저장
		Properties prop = new Properties();
		
		prop.setProperty("id", "student");
		prop.setProperty("password","1234");
		
		System.out.println(prop);
		
		// .properties 파일로 저장하게 된다면 알아서 key/value를 구분하여 저장
		try {
			prop.store(new FileOutputStream("idpw.properties"), "id/pw");
			prop.store(new FileWriter("idpw.txt"), "id/pw");
			prop.storeToXML(new FileOutputStream("driver.xml"), "id/pw");
		} catch (FileNotFoundException e) {
			e.printStackTrace();
		} catch (IOException e) {
			e.printStackTrace();
		} 	
	}
	
	public void test2() {
        // 외부 .properties 파일 불러와서 읽기
		Properties prop = new Properties();
		
		try {
			//prop.load(new FileInputStream("idpw.properties"));
			//prop.load(new FileReader("idpw.txt")); //--> 텍스트 파일도 형식 맞게 작성되어 있다면 k,v 구분
			prop.loadFromXML(new FileInputStream("driver.xml"));
			
			System.out.println(prop.getProperty("id")); // key 값이 "id"인 value를 가져옴
			System.out.println(prop.get("password"));
			
			prop.list(System.out); // 콘솔창에 key=value를 보여줌
			
		} catch (FileNotFoundException e) {
			e.printStackTrace();
		} catch (IOException e) {
			e.printStackTrace();
		}
	}
}
```

