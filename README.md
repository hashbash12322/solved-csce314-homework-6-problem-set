Download Link: https://assignmentchef.com/product/solved-csce314-homework-6-problem-set
<br>
<strong>Problem 0.  README. </strong>Explain in a README.txt file how to compile (using the javac command) and execute your codes (using the java command), and what is the expected output of your codes when tested. It should be detailed enough so that whoever grades your codes can understand what you were doing with your code clearly and should be able to reproduce your tests following what you wrote in it.

<strong>Problem 1.  Implement generic interfaces. </strong>First study the Cell class that is given in pages 247–248. It can represent a generic singly linked list. You will modify the Cell class as below: call it MyNode:

public final class MyNode&lt;E&gt; { // class header needs to be modified also (see below)

private E data;        // data field must be private private MyNode&lt;E&gt; next; // next field must also be private public MyNode (E val, MyNode&lt;E&gt; node) { . . . } //constructor

// other necessary methods such as getter/setter and iterator() (see below)

}

Task 1. for the MyNodeIterator&lt;E&gt; class) As an <strong>inner class </strong>of MyNode, define class MyNodeIterator&lt;E&gt; to iterate over the values stored in a linked list of MyNode&lt;E&gt; objects. To do so, have your MyNodeIterator&lt;E&gt; class implement the java.util.Iterator&lt;E&gt; interface (see https://docs.oracle.com/javase/8/docs/api/java/util/Iterator.html), with the class header class MyNodeIterator&lt;E&gt; implements Iterator&lt;E&gt;. Also, let it have a private field MyNode&lt;E&gt; p.

The constructor of class MyNodeIterator&lt;E&gt; should take a MyNode&lt;E&gt; as an argument, and thus have the header: public MyNodeIterator (MyNode&lt;E&gt; n).

Task 2. for making MyNode&lt;E&gt; class iterable) with the class header public final class MyNode&lt;E&gt; implements Iterable&lt;E&gt;. See https://docs.oracle.com/javase/8/docs/api/java/lang/Iterable.html. To do so, you need to define the iterator() method that returns MyNodeIterator&lt;E&gt; for this MyNode&lt;E&gt; object; public MyNodeIterator&lt;E&gt; iterator() {…}.

Task 3.for the MyNodeTest class – use the skeleton code provided.) Now, if list is of type MyNode&lt;E&gt;, you should be able to iterate over list using Java’s “for each” for-loop:

for (E e : list) { /* do something with e */ }

Implement the class MyNodeTest that contains the following four static methods:

<ul>

 <li> int sum() that accepts a linked list of type MyNode&lt;Integer&gt; and sums up the values in each node in the linked list, and</li>

 <li> num sum() accepts a linked list of type MyNode with any element type that extends Number, and sums up the values in each node in the linked list into a double value (since double is the largest type within the Number type). Use a <em>bounded wildcard</em>.</li>

 <li>print() accepts a linked list of type MyNode with any element type and prints out the values in each node in the linked list.</li>

 <li>The method main() (provided) tests your MyNode&lt;E&gt; and MyNodeIterator&lt;E&gt; In the main(), an Integer list intlist of type MyNode&lt;Integer&gt; and a Double list doublelist of type MyNode&lt;Double&gt; are created by explicitly invoking the MyNode constructor recursively. And then, we invoke the two methods print() and int sum() passing intlist as the argument. Also, invoke print() and num sum() with doublelist as the argument. Furthermore, invoke num sum() with intlist as the argument, and notice the power of bounded wildcards! As seen in the main(), the only collection structure you are allowed to use in this problem is your own MyNode and nothing else, that is, you cannot use existing Collection provided by Java such as ArrayList or LinkedList. Have fun!</li>

</ul>

<strong>Problem 2.  Implement a nicer linked list. </strong>You may notice in Problem 1 that it is rather inconvenient to build lists with MyNode. Implement another generic class MyList&lt;E&gt;, in terms of MyNode, that has a nicer interface. Class MyList&lt;E&gt; must have private fields MyNode&lt;E&gt; n and int length.

To do Tasks 1, 2 and 3, the class header of MyList&lt;E&gt; should be public class MyList&lt;E&gt; implements Iterable&lt;E&gt;, Cloneable, Comparable&lt;MyList&lt;E&gt;&gt;.

Task 1.  Make MyList&lt;E&gt; <em>iterable </em>by implementing the Iterable&lt;E&gt; interface and giving an implementation of iterator().

Task 2.  Make MyList&lt;E&gt; <em>clonable </em>by implementing the Cloneable interface and overriding the Object.clone() method. You must give your own <em>explicit implementation </em>for the clone() method using the for-each loop.

Task 3.  Make MyList&lt;E&gt; <em>comparable </em>by implementing the Comparable&lt;MyList&lt;E&gt;&gt; interface and overriding the compareTo() method. The comparison criterion is the length of the lists.

Task 4.  Also, override the Object.equals() and Object.hashCode() methods. The equals() criteria are (i) the length and (ii) the contents of the lists (but not the order of the values in the list). For example, if l1 = [1,2,3], l2

= [2,1,3], and l3 = [1,1,2,3], then l1.equals(l2) and l2.equals(l1) must return true but not l1.equals(l3) or l3.equals(l1) (nor for l2 and l3).

[Hint: Since you will first check whether the lengths of the two lists are the same, your hashCode() can simply return the length of the list. If the lengths are the same, then check if the elements are all the same using a nested for-each loop.]

Task 5. Define the two constructors for the MyList&lt;E&gt; class:

public MyList(); // create an empty list public MyList(Iterable&lt;E&gt; iterable);

The second constructor should copy the elements in iterable to MyNodes of this list.

Task 6. Implement these member methods (with their expected meaning, see below):

public MyList&lt;E&gt; reverse(); (10 points) public String toString(); (10 points) public void push(E item); (10 points) public E pop();  public E peek(); (5 points)

Also include public int getLength() { return length; }; (no points)

A call x.reverse() should reverse x, and return the reversed list as the result. An easy way to implement reverse() is to reconstruct a new list, and swap that in place of the original. The toString() method should print out the list in the following form: a list of integers 1, 2, and 3 should be printed as

[(head: 1) -&gt; (2) -&gt; (3)].

The push method works the same way as the cons (:) operator in Haskell, i.e., it prepends item at the head of the list as the left-most element. The pop method removes the head (left-most) element from the list and returns its value. The push and pop method should modify the length of the list appropriately. The peek method returns the head element’s value without removing the element.

Class MyListTest with a main() that tests those requirements is provided. Feel free to expand it to test your implementations. Include the MyListTest class in your .zip fi