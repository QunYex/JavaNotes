# Data structure in Java

### Chapter 1.  LinkedList

1. Single Linked List

   1.  Link class

      ```java
      // Link class
      public class Link {
          public int iData;
          public double dData;
          public Link next;
      
          public Link(int id, double dd){
              iData = id;
              dData = dd;
          }
      
          public void displayLink(){
              System.out.print("{"+ iData+", "+ dData+"} ");
          }
      }
      ```

      

   2.  Linked List class

      ```java
      public class LinkList {
          private Link first;
      
          public void LinkList(){
              first = null;
          }
      
          public boolean isEmpty(){
              return (first == null);
          }
      
          public void insertFirst(int id, double dd){
              /*
              * insert a new node into the first one
              * make a new link including the new node
              * make the new link.next points the first
              * change the first so it points the new link
              * */
              Link newLink = new Link(id, dd);
              newLink.next = first;
              first = newLink;
          }
      
          public Link deleteFirst(){
              /*
              * change the first to point the next node
              * */
              Link temp = first;
              first = first.next;
              return temp;
          }
      
          public void displayList(){
             System.out.println("List (first -->last): ");
             Link current = first;
             while (current != null){
                 current.displayLink();
                 current = current.next;
             }
             System.out.println(" ");
          }
      
          public Link find(int key) {
                  Link current = first;
                  while (current.iData != key) {
                      if (current.next == null) {
                          return null;
                      } else {
                          current = current.next;
                      }
                  }
                  return current;
          }
      
          public Link delete(int key){
              Link current  = first;
              Link previous = first;
              while(current.iData != key){
                  if(current.next == null){
                      return null;
                  }else{
                      previous = current;
                      current = current.next;
                  }
              }
              if(current == first){
                  first = first.next;
              }else{
                  previous.next = current.next;
              }
              return current;
          }
      }
      
      ```

      

   3.  Examples

      ```java
      // example 1
      public class LinkListApp {
          public static void main(String[] args){
              LinkList theList = new LinkList();
      
              theList.insertFirst(22,2.99);
              theList.insertFirst(44,4.99);
              theList.insertFirst(66, 6.99);
              theList.insertFirst(99, 9.99);
      
              theList.displayList();
      
              while (!theList.isEmpty()){
                  Link aLink = theList.deleteFirst();
                  System.out.print("Deleted ");
                  aLink.displayLink();
                  System.out.println("");
              }
      
              theList.displayList();
          }
      }
      
      ```

      ```java
      //example 2
      public class LinkList2App {
          public static void main(String[] args){
              LinkList theList = new LinkList();
      
              theList.insertFirst(22,2.99);
              theList.insertFirst(44,4.99);
              theList.insertFirst(66, 6.99);
              theList.insertFirst(99, 9.99);
      
              theList.displayList();
      
              Link f = theList.find(44);
      
              if(f != null){
                  System.out.println("Found link with the key"+ f.iData);
              }else{
                  System.out.println("Can not find link");
              }
      
              Link d = theList.delete(66);
              if (d != null){
                  System.out.println("Deleted link with the key"+ d.iData);
              }else{
                  System.out.println("Can not delete link");
              }
      
              theList.displayList();
              }
      
          }
      
      
      ```

      

2.  Double-End List

   A double-ended list is similar to an ordinary linked list, but it has one additional feature: a reference to the last link as well as to the first. 

   1. Fisrt Last List

      ```java
      class FLLink{
          public long dData;
          public FLLink next;
      
          public FLLink(long d){
              dData = d;
          }
      
          public void displayLink(){
              System.out.print(dData + " ");
          }
      }
      
      class FirstLastList {
          private FLLink first;
          private FLLink last;
      
          public FirstLastList(){
              first = null;
              last = null;
          }
      
          public boolean isEmpty(){
              return first == null;
          }
      
          public void insertFirst(long dd){
              FLLink newLink = new FLLink(dd);
      
              if (isEmpty()){
                  last = newLink;
              }
              newLink.next = first;
              first = newLink;
          }
      
          public void insertLast(long dd){
              FLLink newLink = new FLLink(dd);
              if( isEmpty()){
                  first = newLink;
              }else{
                  last.next = newLink;
              }
              last = newLink;
          }
          public long deleteFirst(){
              long temp = first.dData;
              if (first.next == null){
                  last = null;
              }
              first = first.next;
              return temp;
          }
      
          public void displayList(){
              System.out.print("first-->last:");
              FLLink current = first;
              while (current != null){
                  current.displayLink();
                  current = current.next;
              }
              System.out.println(" ");
          }
      }
      ```

   2. Example 

      ```java
      public class FirstLastApp {
          public static void main(String[] args){
              FirstLastList theList = new FirstLastList();
      
              theList.insertFirst(22);
              theList.insertFirst(44);
              theList.insertFirst(66);
              theList.insertLast(11);
              theList.insertLast(33);
              theList.insertLast(55);
      
              theList.displayList();
      
              theList.deleteFirst();
              theList.deleteFirst();
      
              theList.displayList();
          }
      }
      
      ```

      

3.  Linked list Efficiency

   Insertion and deletation at the beginning of the list is very fast, which takes $ \O(1)$. Finding, deleting, or inserting next to a specific item requires searching through, on the average, half the items in the list. This requires O(N) comparisons. An array is also O(N) for these operations, but the linked list is nevertheless faster because nothing needs to be moved when an item is inserted or deleted. The increased efficiency can be significant, especially if a copy takes much longer than a comparison.

   Another important advantage of linked lists over arrays is that a linked list uses exactly as much memory as it needs and can expand to fill all of available memory. The size of an array is fixed when it’s created; this usually leads to inefficiency because the array is too large, or to running out of room because the array is too small. 

4.  

5.  

6. 

