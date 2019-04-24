Resource : <http://www.cs.cmu.edu/~ab/15-121N11/>

### Array and ArrayList

```java
//Cloning Arrays:
double[] prices = (double[]) data.clone;

//Copying Array Elements
System.arraycopy(from, fromStart, to, toStart, count);

//Shifting and copying
System.arraycopy(data, i, data, i+1, data.length - i - 1);
data[i] = x;

```

![Screenshot 2019-04-23 16.21.59](/Users/xinqunye/Dropbox/Screenshots/Screenshot 2019-04-23 16.21.59.png)



### Java API Strings and IOs

```java
// String properties
//Construct a string
String s = "Hello world";
//Get the length of the string
int length = s.length();//length = 11
//Access a part of the string
String sub = s.substring(6);//"world"
char c = s.charAt(1); //'e'
//Concatenate strings
String t = " of java";
String s1 = s + t; //"Hello world of java"

//comparing string
String s1 = "word";
String s2 = "work";
System.out.println(s1.equals(s2)); //false
System.out.println(s1.compareTo(s2)); // -3, meaning
//"word” < "work"
/* 
two strings are compared lexicographically. The
result is a negative integer if this s1
lexicographically precedes s2. The result is a positive
integer if s1 lexicographically follows
*/

//breaking words apart
String s = "Hello world of java";
StringTokenizer st = new StringTokenizer(s);
while (st.hasMoreTokens()) {System.out.println(st.nextToken());}

String s = "Hello, world of java";
StringTokenizer st = new StringTokenizer(s, ", ");
//”, “ is the delimiter. Notice we need to supply all the
possible delimiters in the string. “,” and a space “ “
while (st.hasMoreTokens()) {
System.out.println(st.nextToken());
}

//String Advanced Usage – Concatenate strings repetitively
//Q: Suppose you have a list of 100 strings. You want to concatenate them into one string?

//Solution 1
List stringList = new ArrayList();
for (int i = 0; i < 10; i++) {
		stringList.add("string" + i);
}
String finalString = "";
for (Iterator iter = stringList.iterator(); iter.hasNext();) {
		String s = (String) iter.next();
		finalString += s;
}
/* work but inefficient for large strings and large amount of
concatenation because String is immutable. Intuitively, Java
needs to maintain an a old string, a new string, and a
concatenate string in each iteration. */

//Solution 2
List stringList = new ArrayList();
for (int i = 0; i < 10; i++) {
		stringList.add("string" + i);
}
StringBuffer sb = new StringBuffer(); //StringBuffer is
mutable. Recommended for a large amount of string
concatenation.
for (Iterator iter = stringList.iterator(); iter.hasNext(); )
{
String s = (String) iter.next();
sb.append(s);
}

//Convert between strings to primitives
//String.valueOf(), Integer.parseInt()
int i = 123;
String s = i + “”;
String t = String.valueOf(i);
String u = Integer.toString(i); //s = t = u = 123
int j = Integer.parseInt(s); // j = 123
//Extension – Double.parseDouble(); 


/******************************/
// JAVA IO
/********************************/

// Scanner class
// how to read an integer from stdin

Scanner sc = new Scanner(System.in);
int i = sc.nextInt();

//how to read a set of long integers from a file

Scanner sc = new Scanner(new FileReader("file.txt"));
while(sc.hasNextLog()){
  System.out.ptiny(sc.nextLog());
}

//How to read a set of strings(words) from a file
Scanner sc = new Scanner(new FileReader("file.txt"));
while (sc.hasNext()) {
	System.out.println(sc.next());
}

/*
boolean hasNext()
Returns true if this scanner has another token in its input.

boolean hasNext(String pattern)
Returns true if the next token matches the pattern constructed from the specified string.

boolean hasNextDouble()
Returns true if the next token in this scanner's input can be interpreted as a double value using the nextDouble() method.
*/

/*How do I read input from the keyboard?
 To get input from the user from a consol instead of a GUI
 By using System.in.read() */
int b = 0;
try {
	b = System.in.read();//returns an integer
} catch (Exception e) {
	System.out.println("Caught " + e);
}
System.out.println("Read this data: " + (char)b);

/*
 Q: How do I read a line from the keyboard?
 Use BufferedReader is = new BufferedReader(new
*/
InputStreamReader(System.in));
try {
BufferedReader is = new BufferedReader(new
InputStreamReader(System.in));
String inputLine;
while ((inputLine = is.readLine()) != null) {
System.out.println(inputLine);
}
is.close();
} catch (IOException e) {
System.out.println("IOException: " + e);
}
// abc (after I typed abc)
//This gives you the ability to read one line at a time.


 /*How do I write data to the hard drive?
 Use PrintWriter out = new PrintWriter(new
BufferedWriter(new FileWriter("c://output.txt")));
*/
try {
	PrintWriter out = new PrintWriter(new
	BufferedWriter(new FileWriter("c://output.txt")));
	out.println("output data");
	out.close();
}
catch (IOException e) {
	System.out.println("IOException: " + e);
}
//you will find a file named output.txt under c:\ and it contains a line "output data"

```



* Summary 

  

  * Java API is a dictionary of the Java language, and the interface for programmers to manipulate Java classes as black boxes.

  String is a class, and immutable.

  1. Construct a string String s = "Hello world";
  2. Get its length s.length();
  3. Get a substring s.substring(6)
  4. Concatenate strings s + t or StringBuffer
  5. Compare strings s1.equals(s2), s1.compareTo(s2)
  6. s.startsWith("hell"), s.endsWith("world")
  7. Convert cases s.toUpperCase();
  8. Finding the index of a substring s.indexOf("o")
  9. Break a string apart StringTokenizer st = new StringTokenizer(s);
  10. Convert a string to primitives Integer.parseInt(s);
  11. Convert a primitive to a string 4+ “”

  * Data can be in the form of characters or bytes.
     IO is comprehensive

    1. Output a message to screen

       System.out.println("Hello, World of Java");

    2. Output text data to a file
       PrintWriter out = new PrintWriter(new BufferedWriter(new
       FileWriter("c://output.txt")));

    3. Read an integer from the consol
       int b = System.in.read();

    4. Read a line from the consol
       BufferedReader is = new BufferedReader(new
       InputStreamReader(System.in));

    5. Read a file
       BufferedReader is = new BufferedReader(new
       FileReader("c://data.txt"));

### JAVA Collections

Example:

​	Arrays, hashtables, vector, set, map, tree



* ArrayList Collection

  ```
  ArrayList A = new ArrayList();
  A.add(new Integer(10));
  System.out.println(A.get(0));
  If (A.contains(new Integer(10))) { ….}
  A.remove(0);
  ```

  ![Screenshot 2019-04-23 16.50.41](/Users/xinqunye/Dropbox/Screenshots/Screenshot 2019-04-23 16.50.41.png)

* Set[<https://docs.oracle.com/javase/8/docs/api/java/util/HashSet.html#HashSet-->]

  ```java
  public interface Set {
  // Basic Operations
  int size();
  boolean isEmpty();
  boolean contains(Object element);
  boolean add(Object element);
  // Optional
  boolean remove(Object element);
  Iterator iterator();
  boolean removeAll(Collection c);
  boolean retainAll(Collection c);
  void clear();
  // Bulk Operations
  boolean containsAll(Collection c);
  boolean addAll(Collection c);
  //Array Operations
  Object[] toArray(); Object[] toArray(Object a[]);
  } 
  ```

  

![Screenshot 2019-04-23 17.00.43](/Users/xinqunye/Dropbox/Screenshots/Screenshot 2019-04-23 17.00.43.png)

* List

  ```java
  public interface List extends Collection
  { 
  // index based Access
  Object get(int index);
  Object set(int index, Object element);
  // Optional
  void add(int index, Object element);
  Object remove(int index);
  abstract boolean addAll(int index, Collection c); //
  Search int indexOf(Object o);
  int lastIndexOf(Object o);
  ListIterator listIterator();
  ListIterator listIterator(int index);
  // Range-view
  List subList(int from, int to); 
  } 
  ```

  * iterators

  ```java
  public interface ListIterator extends Iterator {
  boolean hasNext();
  Object next();
  boolean hasPrevious();
  Object previous();
  int nextIndex();
  int previousIndex();
  void remove();
  // Optional
  void set(Object o);
  void add(Object o);
  } 
  ```

* Map

  ```java
  public interface Map {
  // Basic Operations
  Object put(Object key, Object value);
  Object get(Object key);
  Object remove(Object key);
  boolean containsKey(Object key);
  boolean containsValue(Object value);
  int size();
  boolean isEmpty();
  // Bulk Operations
  void putAll(Map t);
  void clear();
  // Collection Views
  public Set keySet();
  public Collection values();
  public Set entrySet();
  // Interface for entrySet elements
  public interface Entry { Object getKey(); Object getValue(); Object setValue(Object value); }
  } 
  ```

### Stack and Queue

[http://www.cs.cmu.edu/~adamchik/15-121/lectures/Stacks%20and%20Queues/Stacks%20and%20Queues.html](http://www.cs.cmu.edu/~adamchik/15-121/lectures/Stacks and Queues/Stacks and Queues.html)

* Stack 

  ```java
  public interface StackInterface<AnyType>
  {
     public void push(AnyType e);
  
     public AnyType pop();
  
     public AnyType peek();
  
     public boolean isEmpty();
  }
  ```

* Queue

  ```java
  interface QueueInterface‹AnyType>
  {
     public boolean isEmpty();
  
     public AnyType getFront();
  
     public AnyType dequeue();
  
     public void enqueue(AnyType e);
  
     public void clear();
  }
  ```

* DFS & BFS

  ![Screenshot 2019-04-23 17.13.36](/Users/xinqunye/Dropbox/Screenshots/Screenshot 2019-04-23 17.13.36.png)

###  Binary Search Tree

![Screenshot 2019-04-23 17.20.58](/Users/xinqunye/Dropbox/Screenshots/Screenshot 2019-04-23 17.20.58.png)

![Screenshot 2019-04-23 17.21.33](/Users/xinqunye/Dropbox/Screenshots/Screenshot 2019-04-23 17.21.33.png)

![Screenshot 2019-04-23 17.23.10](/Users/xinqunye/Dropbox/Screenshots/Screenshot 2019-04-23 17.23.10.png)

![Screenshot 2019-04-23 17.24.02](/Users/xinqunye/Dropbox/Screenshots/Screenshot 2019-04-23 17.24.02.png)

![Screenshot 2019-04-23 17.25.02](/Users/xinqunye/Dropbox/Screenshots/Screenshot 2019-04-23 17.25.02.png)

![Screenshot 2019-04-23 17.26.32](/Users/xinqunye/Dropbox/Screenshots/Screenshot 2019-04-23 17.26.32.png)

![Screenshot 2019-04-23 17.26.51](/Users/xinqunye/Dropbox/Screenshots/Screenshot 2019-04-23 17.26.51.png)

![Screenshot 2019-04-23 17.27.49](/Users/xinqunye/Dropbox/Screenshots/Screenshot 2019-04-23 17.27.49.png)

#### BST.java

```java
/** **************************************************************************
 *                     The  generic Binary Search Tree class.
 *
 * V.S.Adamchik 2010
 *****************************************************************************/

import java.util.*;

public class BST <T extends Comparable<T>> implements Iterable<T>
{
   public static void main(String[] args)
   {
      Integer[] a = {1,5,2,7,4};
      BST<Integer> bst = new BST<Integer>();
      for(Integer n : a) bst.insert(n);

      bst.preOrderTraversal();
      System.out.println();

      //testing comparator
      //build a mirror BST with a rule:  Left > Parent > Right
      //code for the comparator at the bottom of the file
      bst = new BST<Integer>(new MyComp1());
      for(Integer n : a) bst.insert(n);

      bst.preOrderTraversal();
      System.out.println();
      bst.inOrderTraversal();
      System.out.println();


      for(Integer n : bst) System.out.print(n);
      System.out.println();

      System.out.println(bst);

      //testing restoring a tree from two given traversals
      bst.restore(new Integer[] {11,8,6,4,7,10,19,43,31,29,37,49},
                      new Integer[] {4,6,7,8,10,11,19,29,31,37,43,49});
      bst.preOrderTraversal();
      System.out.println();
      bst.inOrderTraversal();
      System.out.println();

      //testing diameter
      System.out.println("diameter = " + bst.diameter());
      //testing width
      System.out.println("width = " + bst.width());
   }


   private Node<T> root;
   private Comparator<T> comparator;

   public BST()
   {
      root = null;
      comparator = null;
   }

   public BST(Comparator<T> comp)
   {
      root = null;
      comparator = comp;
   }

   private int compare(T x, T y)
   {
      if(comparator == null) return x.compareTo(y);
      else
      return comparator.compare(x,y);
   }

/*****************************************************
*
*            INSERT
*
******************************************************/
   public void insert(T data)
   {
      root = insert(root, data);
   }
   private Node<T> insert(Node<T> p, T toInsert)
   {
      if (p == null)
         return new Node<T>(toInsert);

      if (compare(toInsert, p.data) == 0)
      	return p;

      if (compare(toInsert, p.data) < 0)
         p.left = insert(p.left, toInsert);
      else
         p.right = insert(p.right, toInsert);

      return p;
   }

/*****************************************************
*
*            SEARCH
*
******************************************************/
   public boolean search(T toSearch)
   {
      return search(root, toSearch);
   }
   private boolean search(Node<T> p, T toSearch)
   {
      if (p == null)
         return false;
      else
      if (compare(toSearch, p.data) == 0)
      	return true;
      else
      if (compare(toSearch, p.data) < 0)
         return search(p.left, toSearch);
      else
         return search(p.right, toSearch);
   }

/*****************************************************
*
*            DELETE
*
******************************************************/

   public void delete(T toDelete)
   {
      root = delete(root, toDelete);
   }
   private Node<T> delete(Node<T> p, T toDelete)
   {
      if (p == null)  throw new RuntimeException("cannot delete.");
      else
      if (compare(toDelete, p.data) < 0)
      p.left = delete (p.left, toDelete);
      else
      if (compare(toDelete, p.data)  > 0)
      p.right = delete (p.right, toDelete);
      else
      {
         if (p.left == null) return p.right;
         else
         if (p.right == null) return p.left;
         else
         {
         // get data from the rightmost node in the left subtree
            p.data = retrieveData(p.left);
         // delete the rightmost node in the left subtree
            p.left =  delete(p.left, p.data) ;
         }
      }
      return p;
   }
   private T retrieveData(Node<T> p)
   {
      while (p.right != null) p = p.right;

      return p.data;
   }

/*************************************************
 *
 *            toString
 *
 **************************************************/

   public String toString()
   {
      StringBuffer sb = new StringBuffer();
      for(T data : this) sb.append(data.toString());

      return sb.toString();
   }

/*************************************************
 *
 *            TRAVERSAL
 *
 **************************************************/

   public void preOrderTraversal()
   {
      preOrderHelper(root);
   }
   private void preOrderHelper(Node r)
   {
      if (r != null)
      {
         System.out.print(r+" ");
         preOrderHelper(r.left);
         preOrderHelper(r.right);
      }
   }

   public void inOrderTraversal()
   {
      inOrderHelper(root);
   }
   private void inOrderHelper(Node r)
   {
      if (r != null)
      {
         inOrderHelper(r.left);
         System.out.print(r+" ");
         inOrderHelper(r.right);
      }
   }

/*************************************************
 *
 *            CLONE
 *
 **************************************************/

   public BST<T> clone()
   {
      BST<T> twin = null;

      if(comparator == null)
         twin = new BST<T>();
      else
         twin = new BST<T>(comparator);

      twin.root = cloneHelper(root);
      return twin;
   }
   private Node<T> cloneHelper(Node<T> p)
   {
      if(p == null)
         return null;
      else
         return new Node<T>(p.data, cloneHelper(p.left), cloneHelper(p.right));
   }

/*************************************************
 *
 *            MISC
 *
 **************************************************/

   public int height()
   {
      return height(root);
   }
   private int height(Node<T> p)
   {
      if(p == null) return -1;
      else
      return 1 + Math.max( height(p.left), height(p.right));
   }

   public int countLeaves()
   {
      return countLeaves(root);
   }
   private int countLeaves(Node<T> p)
   {
      if(p == null) return 0;
      else
      if(p.left == null && p.right == null) return 1;
      else
      return countLeaves(p.left) + countLeaves(p.right);
   }



  //This method restores a BST given preorder and inorder traversals
   public void restore(T[] pre, T[] in)
   {
      root = restore(pre, 0, pre.length-1, in, 0, in.length-1);
   }
   private Node<T> restore(T[] pre, int preL, int preR, T[] in, int inL, int inR)
   {
      if(preL <= preR)
      {
         int count = 0;
         //find the root in the inorder array
         while(pre[preL] != in[inL + count]) count++;

         Node<T> tmp = new Node<T>(pre[preL]);
         tmp.left = restore(pre, preL+1, preL + count, in, inL, inL +count-1);
         tmp.right = restore(pre, preL+count+1, preR, in, inL+count+1, inR);
         return tmp;
      }
      else
         return null;
   }


   //The width of a binary tree is the maximum number of elements on one level of the tree.
   public int width()
   {
      int max = 0;
      for(int k = 0; k <= height(); k++)
      {
         int tmp = width(root, k);
         if(tmp > max) max = tmp;
      }
      return max;
   }
   //rerturns the number of node on a given level
   public int width(Node<T> p, int depth)
   {
      if(p==null) return 0;
      else
      if(depth == 0) return 1;
      else
      return width(p.left, depth-1) + width(p.right, depth-1);
   }

   //The diameter of a tree is the number of nodes
   //on the longest path between two leaves in the tree.
   public int diameter()
   {
      return diameter(root);
   }
   private int diameter(Node<T> p)
   {
      if(p==null) return 0;

      //the path goes through the root
      int len1 = height(p.left) + height(p.right) +3;

      //the path does not pass the root
      int len2 = Math.max(diameter(p.left), diameter(p.right));

      return Math.max(len1, len2);
   }


/*****************************************************
*
*            TREE ITERATOR
*
******************************************************/

   public Iterator<T> iterator()
   {
      return new MyIterator();
   }
   //pre-order
   private class MyIterator implements Iterator<T>
   {
      Stack<Node<T>> stk = new Stack<Node<T>>();

      public MyIterator()
      {
         if(root != null) stk.push(root);
      }
      public boolean hasNext()
      {
         return !stk.isEmpty();
      }

      public T next()
      {
         Node<T> cur = stk.peek();
         if(cur.left != null)
         {
            stk.push(cur.left);
         }
         else
         {
            Node<T> tmp = stk.pop();
            while( tmp.right == null )
            {
               if(stk.isEmpty()) return cur.data;
               tmp = stk.pop();
            }
            stk.push(tmp.right);
         }

         return cur.data;
      }//end of next()

      public void remove()
      {

      }
   }//end of MyIterator

/*****************************************************
*
*            the Node class
*
******************************************************/

   private class Node<T>
   {
      private T data;
      private Node<T> left, right;

      public Node(T data, Node<T> l, Node<T> r)
      {
         left = l; right = r;
         this.data = data;
      }

      public Node(T data)
      {
         this(data, null, null);
      }

      public String toString()
      {
         return data.toString();
      }
   } //end of Node
}//end of BST

class MyComp1 implements Comparator<Integer>
{
   public int compare(Integer x, Integer y)
   {
        return y-x;
   }
}
```

### Binary Heap

### Sort in java

![Screenshot 2019-04-23 17.34.39](/Users/xinqunye/Dropbox/Screenshots/Screenshot 2019-04-23 17.34.39.png)

![Screenshot 2019-04-23 17.34.56](/Users/xinqunye/Dropbox/Screenshots/Screenshot 2019-04-23 17.34.56.png)