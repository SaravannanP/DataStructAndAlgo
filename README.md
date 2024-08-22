# Data Structure and Algorithms 
Could be doing 75 or 150 qns . Havent decided yet 

![image](https://github.com/user-attachments/assets/25146ad2-3007-4ad8-ade7-b2966eed622f)

![image](https://github.com/user-attachments/assets/0b9a1eb8-3e27-450c-9dae-530999ceb1ca)



Algos 
============

Sorting Algo (shuffled deck of cards to put in order) 
-------------------
- method or process used to rearrange elemetns in a list of an array in a certain order weather 
it be ascnding descending or even based on complex rules 


      import java.util.Random;
      import java.util.Arrays;
      import java.util.LinkedList;
      
      
      class Algos 
      {
      	// memoization 
      	private static int [] fiboCache;
      	
      	private static void printArray(int [] arr)
      	{
      		for(int i=0;i <arr.length;i++)
      		{
      			System.out.print(arr[i] + " ");
      		}
      		
      	}
      	
      	public static void main(String [] args)
      	{
      		Random rand = new Random();
      		
      		int [] arr = new int[1000];
      		
      		for(int i = 0 ; i < arr.length; i++)
      		{
      			arr[i]= rand.nextInt(1000+1);
       		}
      		
      		System.out.println("Before:");
      		printArray(arr);
      		System.out.println();
      		
      		//bubbleSort(arr);
      		//mergeSort(arr);
      		//quickSort(arr,0,arr.length-1);
      		//insertionSort(arr);
      		//selectionSort(arr);
      		
      		System.out.println("After:");
      		//printArray(arr);
      		System.out.println();
      		
      		
      		int n = 6;
      		fiboCache = new int [n+1];
      		System.out.print("Fibo " + n + " term : " + fibo(n));
  
      		System.out.println();
  
      		System.out.println(leapYear(1996));
      		
      		rockPaperScissorsGame();
      		
      		System.out.println();
      		reverseString("Hello");
  
      		palindrome();
  
      		characterCount("Saravannan");
  
      		anagram();
  
      		vovelsConsonants();
  
      		matchingElements();
  
      		reverseArray();
  
      		System.out.println();
  
      		reverseLinkedList();
  
      		secondLargestElement();
  
      		removeCharacteroccurence();
  
      		System.out.println(isPrime(13));
      		System.out.println(isPrime(8));
  
      		sumOfElements();
      	}
  
      	/* Bubble sort  (john) 
      	- simple sorting algo that repeatedly steps through array,elemtn by element comparing
      	current element with one after swapping value if former larger than the latter   */
      	private static void bubbleSort(int [] arr)
      	{
      		// 2)
      		boolean swappedSomething = true;
      		
      		// 3)
      		while(swappedSomething)
      		{
      			// 4) start optimistically 
      			swappedSomething = false;
      			//  1) once second last element reached compare with last element 
      			for(int i = 0 ; i < arr.length - 1; i++)
      			{
      				if(arr[i] > arr[i+1])
      				{
      					// 5) 
      					swappedSomething = true;
      					int  temp = arr[i];
      					arr[i] = arr[i+1];
      					arr[i+1] = temp;
      					
      				}
      				
      
      			}
      		}
      		
      	}
      	
      
      /* Insertion sort (john) 
      - simple sort algo that builds final sorted array element one at a time
      */
       private static void insertionSort(int [] arr)
       {
      	// index 0 already sorted with self so start at index 1  
      	for(int i = 1 ; i < arr.length; i++)
      	{
      		int currentValue = arr[i];
      		int j = i - 1;
      		// j >=0 stop waling back once hit start of array
      		while(j >= 0 && arr[j] > currentValue)
      		{
      			arr[j+1] = arr[j];
      			j--;
      		}
      		
      		arr[j+1] = currentValue;
      	}
      	 
      	 
       }
      
      /*
      Merge sort  (john) 
      - Efficient,stable and comparison based DIVIDE AND CONQUER sorting algo and is recursive 
        Dividess input array into halces,calls itself for the two halves,sorting them and merges
        two sorted halves  */
        
        //1) divide unsorted arr into two halves untill only one element remaining
        //2) Conquer portion by merging  
      	private static void mergeSort(int [] arr)
      	{
      		int inputLength = arr.length;
      		
      		// intance where the array only has one element left 
      		if(inputLength < 2){
      			return; 
      		}
      		
      		int midIndex = inputLength/2;
      		
      		int [] leftHalf = new int[midIndex];
      		// in case array is odd numbered 
      		int [] rightHalf = new int[inputLength - midIndex];
      		
      		for(int i = 0 ; i < midIndex ; i++)
      		{
      			leftHalf[i] = arr[i];
      		}
      		
      		for(int k = midIndex; k < inputLength; k++)
      		{
      			// k - midIndex has to start from 0
      			rightHalf[k - midIndex] = arr[k];
      		}
      		
      		mergeSort(leftHalf);
      		mergeSort(rightHalf); 
      		
      		merge(arr,leftHalf,rightHalf);
      		
      	}
      	// merge smaller sorted array to one large array 
      	private static void merge(int [] inputArray, int [] leftHalf, int [] rightHalf)
      	{
      		int leftSize = leftHalf.length;
      		int rightSize = rightHalf.length;
      		
      		
      		// i is the iterator for left half 
      		int i = 0;
      		// j is the iterator for right half 
      		int j = 0;
      		// k is iterator for merged array 
      		int k = 0;
      		
      		// loop till run out of elements on both arrays 
      		while(i < leftSize && j < rightSize)
      		{
      			// lefthalf[j] is smaller of the two nums
      			if(leftHalf[i] <= rightHalf[j])
      			{
      				inputArray[k] = leftHalf[i];
      				i++;
      			}
      			else 
      			{
      				inputArray[k] = rightHalf[j];
      				j++;
      			}
      			k++;
      			
      		}
      		
      		while(i < leftSize) 
      		{
      			inputArray[k] = leftHalf[i];
      			i++;
      			k++;
      		}
      		while(j < rightSize) 
      		{
      			inputArray[k] = rightHalf[j];
      			j++;
      			k++;
      		}
      		
      			
      	}
      
      
      /* Quick  sort  (john)
      choose one of the number in array as pivot 
      move  number loser than pivot to left of array and all num higher than pivot to right (partition)
      recurse calls using low index and highindex 
      */
      	private static void quickSort(int [] arr, int lowIndex,int highIndex)
      	{
      		// if only one element in subarray 
      		if(lowIndex >= highIndex)
      		{
      			return;
      		}
      		int pivot = arr[highIndex];
      		// partitioning 
      		// leftptr looks for number more than pivot
      		// right ptr looks for number less than pivot
      		// swap 
      		int leftPtr = lowIndex;
      		int rightPtr = highIndex;
      		
      		
      		while(leftPtr < rightPtr)
      		{
      			while(arr[leftPtr] <= pivot && leftPtr < rightPtr)
      			{
      				leftPtr ++;
      			}
      			
      			while(arr[rightPtr] >= pivot &&  leftPtr < rightPtr)
      			{
      				rightPtr --;
      			}
      			
      			swap(arr,leftPtr,rightPtr);
      			
      		}
      		
      		swap(arr,leftPtr,highIndex);
      		// partitonign done 
      		quickSort(arr,lowIndex,leftPtr-1);
      		quickSort(arr,leftPtr + 1,highIndex);
      	}
      	
      	private static void swap(int [] arr, int index1, int index2)
      	{
      		int temp = arr[index1];
      		arr[index1] = arr[index2];
      		arr[index2] = temp;
      	}
      
      
      
      
      
      /*
      selection sort (john)
      find the lowerst and swap index 
       */
       
       private static void selectionSort(int [] arr)
       {
      	 int length = arr.length;
      	for(int i =	0; i < arr.length-1 ; i++)
      	{
      		int min = arr[i];
      		int indexOfmin = i;
      		
      		for( int j = i+1 ; j < arr.length;j++)
      		{
      			if( arr[j] < min)
      			{
      				min = arr[j];
      				indexOfmin = j;
      				
      			}
      				
      		}
      		
      		selectionSwap(arr,i,indexOfmin);
      		
      	}
      	 
       }
       
       
       private static void selectionSwap(int [] arr,int a, int b)
       {
      	int temp = arr[a];
      	arr[a] = arr[b];
      	arr[b] = temp;
      
       }
       
       
      /*
      heap sort 
      */
      
      
      
      /* Searching (Yellow pages) 
      -------------------
      - A searching algorithm is a method or process used to find or retrieve 
      and elemnt from a data strcuture.
      The goal is to find whether an item exists in the data set,
      and determine its location 
      
      linear search
      - Each element checked in sequence utill element is found or list ends 
      if current element equals what we are looking for then return it.
       */
       private static boolean linearSearch(int [] arr, int chosenValue)
       {
      	boolean found = false;
      	for(int i = 0 ; i < arr.length; i++)
      	{
      		if(arr[i] == chosenValue)
      		{
      			found = true;
      		}
      	}
      	
      	return found;
      	 
       }
      
      
      
      /* Binary search (john) 
      - works by repeatedly dividing in half the portionof the list that may contain the element 
      ultil you narrowed down the the possible location to just one.
      */
      
      
      /*
      Graph (G maps) 
      -------------------
      - Graps algos are a set of instrcution used to solve problems related to graph 
      theory where data is represented as a collaction of nodes connected by edges,like trees
      */
      
      /*
      DFS 
      - Start at root node and explore as far as possible along each branch before backtracking 
      */
      
      /*
      BFS 
      - layer by layer approach ,casting a wide net from start point and gradually widening it 
      */
      
      /*
      Dijkstra (best) 
      - finds shortes path between given nodes and all other nodes in a graph using 
      the weights of the edges to find the path that minimizes the total weight between source node 
      and all other nodes 
      */
      
      
      /*
      A*
      - graph traversal and pathfinding algo.Same as dijkstra but uses heuristic function giving 
      priority to nodes that are supposed to be better than others 
      */
      
      /*
      Fibo (john)
      */
      
      	private static int fibo (int n)
      	{
      		// BASE CASE each recursive algo needs a base case in order to not recurse indefinitely
      		// 0 1 1 2 3 
      		// first term 0 second term 1 
      		if(n <= 1)
      		return n;
      		
      		// check for 0 and not null because primitives can never be null
      		if(fiboCache[n] != 0)
      		{
      			return fiboCache[n];
      		}
      		
      		int nthFiboNum = (fibo(n-1) + fibo(n-2));
      		fiboCache[n] = nthFiboNum;
      		return  nthFiboNum;
      		
      	}
      
      /* leapyear */
      	private static boolean leapYear(int year)
      	{
      		boolean isLeap = false;
      		isLeap = year % 400 == 0 || year % 100 != 0 || year % 4 == 0 ? true : false;
      		return isLeap;
      		
      	}
      
      
      /* Rock paper scissors */
      	private static void rockPaperScissorsGame()
      	{
      		String [] arr = {"Rock","Paper","Scissors"};
      		Random rand = new Random();
      		Random r =  new Random(); 
      		int com1 = rand.nextInt(3);
      		int com2 = r.nextInt(3); 
      		System.out.println("com 1 " + arr[com1]);
      		System.out.println("com 2 " + arr[com2]);
      		
      		
      		if(arr[com1].equals(arr[com2]))
      			System.out.println("its a tie");
      		else
      		{
      			if(arr[com1].equals("Paper"))
      			{	
      				if(arr[com2].equals("Rock"))
      					System.out.println("com 1 wins");
      				else 
      					System.out.println("com 2 wins");
      			}
      			if(arr[com1].equals("Rock"))
      				if(arr[com2].equals("Scissors"))
      					System.out.println("com 1 wins");
      				else 
      					System.out.println("com 2 wins");
      			if(arr[com1].equals("Scissors"))
      				if(arr[com2].equals("Paper"))
      					System.out.println("com 1 wins");
      				else 
      					System.out.println("com 2 wins");
      		}
      	}
      
      
      
      // https://www.simplilearn.com/coding-interview-questions-article
      
      
      /* Reverse a string */
      
      	private static String reverseString(String str)
      	{
      		// using example "Hello"
      		String reverse = "";
      		
      		int length;
      		
      		// Note String class has it own length() method 
      		length = str.length();
      
      
      		for(int i = 0 ; i < length; i++)
      		{
      			// note the placement of str.charAt() is infront instead of behind 
      			reverse = str.charAt(i) + reverse  ;
      			// prints H then eH then leH thne olleH 
      			System.out.println(reverse);
      		}
      		
      		System.out.println(reverse);
      
      		return reverse;
      	}
      	
      
      /* Palindrome */
      
      	private static void palindrome()
      	{
      		// dog and god mom and mon 
      		String sample = "level";
      		String reverse = reverseString(sample);
      		if(sample.equals(reverse))
      			System.out.println("Palindrome");
      		else 
      			System.out.println("Not Palindrome");
      		
      		
      	}
      
      
      /* Number of occurences of a character in String */
      
      	private static void characterCount(String name)
      	{
      		char search ='a';
      		int count = 0; 
      		for(int i = 0; i< name.length(); i++)
      		{
      			
      			if(name.charAt(i) == search)
      			{
      				count++;
      			}
      		}
      		
      		System.out.println(count);
      		
      		
      	}
      
      
      
      
      
      
      /* Anagram - 
      For example, if you take the letters from the words a 'gentleman'
      you can rearrange them to spell 'elegant man' */
      	
      	private static void anagram()
      	{
      		String original = "a gentleman";
      		String rearranged = "elegant man";
      		boolean anagramStatus = false; 
      		
      		
      		if(original.length() != rearranged.length())
      		{
      			System.out.println(original + " and " + " not anagram string");
      			
      			
      		}
      		else 
      		{
      			char [] anagram1 = original.toCharArray();
      			char [] anagram2 = rearranged.toCharArray();
      			
      			Arrays.sort(anagram1);
      			Arrays.sort(anagram2);
      			
      			anagramStatus = Arrays.equals(anagram1,anagram2); 
      				
      		}
      		
      		if(anagramStatus == true)
      		{
      			System.out.println("Anagram");			
      		}
      		else
      		{
      			System.out.println("Not an Anagram");		
      		}			
      	
      	}
      	
      
      /* How many vovels and consonants in my name  */
      
      	private static void vovelsConsonants ()
      	{
      		String name = "Saravannan";
      		int vovels = 0;
      		int consonants = 0;
      		char c;
      		for(int i = 0; i < name.length(); i++)
      		{
      			c = name.charAt(i);
      			if( c == 'a' || c == 'e'|| c == 'i'|| c == 'o'|| c == 'u')
      				vovels++;
      			else 
      				consonants++;
      		}
      		
      		System.out.println("Number of vovels " + vovels );
      		System.out.println("Number of consonants "+ consonants);
      		
      	}
      
      /* How to get matching elements in an integer array */
      	private static void matchingElements()
      	{
      		int []  a = {1,2,3,4,5,1,2,6,7};
      		
      		for(int m = 0; m < a.length; m++)
      			for(int n = m + 1 ; n < a.length-1; n++)
      			{
      				if(a[m] == a[n])
      				{
      					System.out.println("Number " + a[m]);
      				}
      			}
      		
      		
      	}
      
      
      /* Reverse an array 
      	loop till half length and swap corresponding index values from start to end 
       */
      
      	private static void reverseArray()
      	{
      		int [] num = {1,2,7,6,4,9,12};
      		int temp;
      		printArray(num);
      		System.out.println();
      		for(int i = 0 ; i < num.length/2;i++)
      		{
      			temp = num[i];
      			num[i] = num[num.length - i - 1];
      			num[num.length - i - 1] = temp;
      		}
      		printArray(num);
      		
      		
      	}
      
      
      /* Swap two numbers without using a variable 
      1 Declare two variables and initialize them with values.
      2 Make b the sum of both numbers.
      3 Then subtract the sum (b) from a, so a is now swapped.
      4 Lastly, subtract a from the sum (b), so b is also swapped.
      */
      
      	private static void swapTwoNumberswithoutTemp()
      	{
      		int a = 10;
      		int b = 20;
      		
      		b = b + a; // (b is sum of a + b)
      		a = b - a; //(a is swapped)
      		b = b - a; //(b is swapped)
      		
      		
      	}
      
      
      /* Factorial of an integer
      1 A factorial is a function that multiplies a number by every number below it. For example, 5!= 5*4*3*2*1=120.
      2 Recursive function multiples the numbers until it reaches 1.
       */
      	private static long factorial(long n)
      	{
      		// base case 
      		if(n == 1)
      			return 1;
      		else 
      			return (n * factorial(n-1));
      	}
       
       
      /* How to reverse a linked list
      1 Declare a linked list.
      2 Add elements to that linked list.
      3 Apply the descending iterator method to the linked list.
      4 This reverses the order of elements in the linked list. */
      
      	private static void reverseLinkedList ()
      	{
      		LinkedList<Integer> original = new LinkedList<>();
      
      		original.add(1);
      		original.add(2);
      		original.add(3);
      		
      		System.out.println(original);
      		LinkedList<Integer> reversed = new LinkedList<>();
      		original.descendingIterator().forEachRemaining(reversed::add);
      		System.out.println(reversed);
      	}
      
      /* Find second largest number in array */ 
      	private static void secondLargestElement()
      	{
      		int  highest = Integer.MIN_VALUE;
      		int  secondHighest = Integer.MIN_VALUE;
      		int [] num = {1,2,7,6,4,9,12};	
      			
      		for(int i : num)
      		{
      			if(i > highest)
      			{
      				secondHighest = highest;
      				
      				highest = i; 
      				
      				
      			}else if(i > secondHighest)
      			{
      				
      				secondHighest = i;
      			}
      			
      		}
      		
      		System.out.println("secondHighest is " + secondHighest);
      		
      	}
      
      
      /* remove all occurences of a given characer 
         Use the built-in string method 'replace' to replace a character with any other character, including symbols and white spaces.
      */
      	private static void removeCharacteroccurence()
      	{
      		
      		String str1 = "australia";
      		str1 = str1.replace("a",""); 
      		System.out.println(str1); 
      		
      		
      	}
      	
      	
      /* Prime number 
      If the number is 0 or 1, it cannot be prime.
      If the number is 2, it is prime number.
      If the number is indivisible by other numbers, it is prime. */
      	
      	private static boolean isPrime(int  num)
      	{
      		
      		if(num <= 1)
      			return false;
      		
      		if(num == 2)
      			return true;
      		
      		// start 2ith 2 as its the smallest denominator 
      		for(int i = 2; i < num/2 ; i++)
      		{
      			
      			if( num % i == 0)
      			{
      				return false;
      			}
      		}
      		
      		return true;
      		
      		
      	}
      	
      	
      // Sum of all elements in an array 
      
      	private static void sumOfElements()
      	{
      		int [] arr = {1,2,3,4,5};
      		int sum = 0;
      		
      		for(int i : arr)
      		{
      			//sum = sum + i;
      			sum += i; 
      		}
      		
      		System.out.println("sum : " + sum);
      		
      		
      	}
      }
      
      /* Showcase Inheritance with the help of a program?
      The class Cat inherits the property color from the class Animal by extending the parent class (Animal).
      This way a class Cat can have more parent classes if it wishes to inherit their properties. */
      
      class Animal{
      	
      	String color;
      }
      
      
      class Cat extends Animal{
      	
      	void meow()
      	{
      		System.out.println("Meow");
      	}
      }
      
      
      
      /* Overloading 
      When a class has two or more methods with the saem name, they are called overloaded methods 
       */
      
      class Foo {
      	
      	void print(String s)
      	{
      		System.out.println(s);
      	}
      	
      	void print(String s, int count) 
      	{
      
              while (count > 0) {
      
                  System.out.println(s);
      
                  count--;
              }
      
          }
      	
      }
      
      
      /* Overriding 
      When a superlass method is also implmented in child class its a case of overriding */
      
      class Base {
      	
      	void printName(){
      		System.out.println("Base Class");
      	}
      	
      }
      
      
      class Child extends Base {
      	
      	@Override
      	void printName(){
      		System.out.println("Child Class");
      	}
      }
      
      
      //https://www.javatpoint.com/corejava-interview-questions




