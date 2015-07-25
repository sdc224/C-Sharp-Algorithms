# C# ALGORITHMS

Implementations of Data Structures and Algorithms in C#.

I started writing this organized collection of classes as part of my preparation for technical interviews. This is for educational purposes only. However, the source code is stable.

This is a .NET solution and it can be opened with both Xmarian (MonoDevelop) and Visual Studio. It has two separate projects: 1) Algorithms, 2) DataStructures. Both of them are class-library projects.

## Data Structures

#### Lists:

 * **[Single-Linked List](DataStructures/Lists/SLinkedList.cs).**
 * **[Double-Linked List](DataStructures/Lists/DLinkedList.cs).**
 * **[Array List](DataStructures/Lists/ArrayList.cs).** A generic arrays-based list. Implements auto-resizing and handles overflow.
 * **[Stack](DataStructures/Lists/Stack.cs).** Based on my *ArrayList\<T\>*.
 * **[Queue](DataStructures/Lists/Queue.cs).** Based on my *ArrayList\<T\>*.

#### Priority Queues:

 * **[Priority Queue](DataStructures/Heaps/PriorityQueue.cs).** Based on my *MaxHeap\<T\>*.
 * **[Keyed Priority Queue](DataStructures/Heaps/KeyedPriorityQueue.cs).** Based on my *MaxHeap\<T\>*.

#### Heaps:

 * **[Binary Min-Heap](DataStructures/Heaps/BinaryMinHeap.cs).** Uses the *ArrayList\<T\>* class.
 * **[Binary Max-Heap](DataStructures/Heaps/BinaryMaxHeap.cs).** Uses the *ArrayList\<T\>* class.
 * **[Binomial Min-Heap](DataStructures/Heaps/BinomialMinHeap.cs).** Uses the *ArrayList\<T\>* class as a collection of connected BinomialNode lists. The BinomialNode is a private class inside the Heap data structure class.
 
#### Trees:

 * **[Binary Search Tree](DataStructures/Trees/BinarySearchTree.cs).** Standard BST.
 * **[Augmented Binary Search Tree](DataStructures/Trees/AugmentedBinarySearchTree.cs).** A BST that is augmented to keep track of the subtrees-size for each node. Extends the *BinarySearchTree\<T\>* class.
 * **[AVL Tree](DataStructures/Trees/AVLTree.cs).** The self-balancing AVL binary-search tree. Extends the *BinarySearchTree\<T\>* class.

#### Hashing Functions:
 * **[Prime Hashing Family](DataStructures/Hashing/PrimeHashingFamily.cs).** Implements a simple family of hash functions using primes. The functions are initialized by randomly selecting primes. Supports re-generation of functions.
 * **[Universal Hashing Family](DataStructures/Hashing/UniversalHashingFamily.cs).** Implements a family class of simple universal-hashing functions. Supports re-generation of functions. It uses the [Common/PrimesList](DataStructures/Common/PrimesList.cs) helper class.

#### Hash Tables / Dictionaries:

 * **[Chained Hash Table](DataStructures/Dictionaries/ChainedHashTable.cs).** A hash table that implements the **Separate-Chaining** scheme for resolving keys-collisions. It also implements auto-resizing (expansion and contraction).
 * **[Cuckoo Hash Table](DataStructures/Dictionaries/CuckooHashTable.cs).** A hash table that implements the **Cuckoo Hashing** algorithm for resolving keys-collisions. This is a single-table implementation, the source behind this is the work of Mark Allen Weiss, 2014.

#### Graphs:
 * **[Undirected Sparse Graph](DataStructures/Graphs/UndirectedSparseGraph.cs).** An adjacency-list graph representation. Implemented using a Dictionary of IComparable\<T\> keys and Double-Linked Lists values. The IComparable\<T\> keys serve as the nodes (vertices), and the lists serve as each node's adjacent nodes.
 * **[Undirected Dense Graph](DataStructures/Graphs/UndirectedDenseGraph.cs).** An adjacency-matrix graph representation. Implemented using the native two dimensional arrays in C#. The two dimenssional array holds boolean values that represent the edges connectivity between vertices. The vertices are held inside an internal dynamic list. The index of each vertex represent its key. Keys of vertices are managed systematically between the vertices-vector and the adjacency-matrix. It was implemented this way to achieve the capability of inserting any IComparable\<Type\> of vertex into the graph.


## Algorithms

#### Sorting:
 Sorting algorithms are implemented as an extension method. They support the native Array\<T\>, and List\<T\> classes. They can takes value comparers. Insertion Sort supports my ArrayList\<T\> class.

  * [Insertion Sort](Algorithms/Sorting/InsertionSorter.cs)
  * [Quick Sort](Algorithms/Sorting/QuickSorter.cs)
  * [Merge Sort](Algorithms/Sorting/MergeSorter.cs)
  * [Heap Sort](Algorithms/Sorting/HeapSorter.cs)
  * [BST Sort](Algorithms/Sorting/BinarySearchTreeSorter.cs). Implements an unbalanced binary search tree sort.
  * [Counting Sort](Algorithms/Sorting/CountingSorter.cs). Only sorts arrays of integers.

    ```
    int[] array = new int[] { 23, 42, 4, 16, 8, 15, 3, 9, 55, 0 };
    List<long> list = new List<long> () { 23, 42, 4, 16, 8, 15, 3, 9, 55, 0 };
    
    // The value comparer object. Can be any value comparer that implmenets IComparer.
    var valueComparer = Comparer<long>.Default;
    
    list.InsertionSort (valueComparer);
    list.QuickSort (valueComparer);
    list.MergeSort (valueComparer);
    list.HeapSort (valueComparer);
    list.UnbalancedBSTSort();
    array.CountingSort();
    ```

#### Graphs:
 * **[Depth-First Searcher](Algorithms/Graphs/DepthFirstSearcher.cs).** Implements the DFS algorithm in two ways: Iterative and Recursive. Provides multiple functions for traversing graphs: PrintAll(), VisitAll(Action\<T\> forEachFunc), FindFirstMatch(Predicate\<T\> match). The VisitAll() applies a function to every graph nodes. The FindFirstMatch() function takes searches the graph for a predicate match.
 * **[Breadth-First Searcher](Algorithms/Graphs/BreadthFirstSearcher.cs).** Implements the DFS algorithm in an iterative fashion. Provides multiple functions for traversing graphs: PrintAll(), VisitAll(Action\<T\> forEachFunc), FindFirstMatch(Predicate\<T\> match). The VisitAll() applies a function to every graph nodes. The FindFirstMatch() function takes searches the graph for a predicate match.
 * **[Breadth First Paths](Algorithms/Graphs/BreadthFirstPaths.cs).** A class that takes a Graph instance upon object-instantiation as a parameter, and then applies BFS to the graph. Meanwhile applying BFS to the graph, it extracts information about shortest-paths and connectivity. It provides the capability to find shortest-paths from single-sources and multiple-sources. Also, to check for reachable and unreachable nodes from the specified source-node(s).

#### Numeric:
 * [Catalan Numbers](Algorithms/Numeric/CatalanNumbers.cs). A class that calculates the catalan numbers. A dynamic-programming solution.

#### Visualization:
 * [Tree Drawer](DataStructures/Trees/TreeDrawer.cs). Draws any tree that extends my *BinarySearchTree\<T\>* class. It is defined as an extension function.
    ```
    var avlTree = new AVLTree<int>();
    var treeDataList = new List<int>() { 15, 25, 5, 12, 1, 9, 7, -1, 11, 30, 8, 10, 13, 28, 39 };
    avlTree.Insert(treeDataList);
    
    Console.WriteLine( avlTree.DrawTree() );
    
    /***
     ** Drawer output:
     **           .......9......
     **          /              \
     **       .5       ....12...
     **      /  \     /         \
     **    1   7    11      .25.
     **    /\ / \   /\     /    \
     **  -1     8  10    15    30
     **  /\    /\  /\    /\   / \
     **                 13   28 39
     **                 /\   /\ /\
     */
    ```


## License

This project is licensed under the [MIT License](LICENSE).
