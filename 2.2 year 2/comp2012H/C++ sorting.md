bubble sort
```C++
#include<iostream>
using namespace std;
int main ()
{
	int i, j,temp;
	int a[5] = {10,2,0,43,12};
	cout <<"Input list ...\n";
	for(i = 0; i<5; i++) {
	cout <<a[i]<<"\t";
}
cout<<endl;
for(i = 0; i<5; i++) {
   for(j = i+1; j<5; j++)
   {
     if(a[j] < a[i]) {
         int temp = a[i];
         a[i] = a[j];
         a[j] = temp;
      }
   }
}
cout <<"Sorted Element List ...\n";
for(i = 0; i<5; i++) {
   cout <<a[i]<<"\t";
   }
return 0;
}
```
selection sort
```C++
#include<iostream>
using namespace std;
int findSmallest (int[],int);
int main ()
{
   int myarray[5] = {12,45,8,15,33};
   int pos,temp;
   cout<<"\n Input list of elements to be Sorted\n";
   for(int i=0;i<5;i++)
   {
      cout<<myarray[i]<<"\t";
   }
   for(int i=0;i<5;i++)
   {
      pos = findSmallest (myarray,i);
      temp = myarray[i];
      myarray[i]=myarray[pos];
      myarray[pos] = temp;
   }
   cout<<"\n Sorted list of elements is\n";
   for(int i=0;i<5;i++)
   {
      cout<<myarray[i]<<"\t";
   }
return 0;
}
int findSmallest(int myarray[],int i)
{
   int ele_small,position,j;
   ele_small = myarray[i];
   position = i;
   for(j=i+1;j<5;j++)
   {
      if(myarray[j]<ele_small)
      {
      ele_small = myarray[j];
      position=j;
      }
   }
   return position;
}
```
Insertion sort
```C++
#include<iostream>
using namespace std;
int main ()
{
   int myarray[5] = { 12,4,3,1,15};
   cout<<"\nInput list is \n";
   for(int i=0;i<5;i++)
   {
      cout <<myarray[i]<<"\t";
   }
   for(int k=1; k<5; k++)
   {
      int temp = myarray[k];
      int j= k-1;
      while(j>=0 && temp <= myarray[j])
      {
         myarray[j+1] = myarray[j];
         j = j-1;
      }
   myarray[j+1] = temp;
   }
cout<<"\nSorted list is \n";
for(int i=0;i<5;i++)
   {
   cout <<myarray[i]<<"\t";
   }
}
```
Quick Sort
```C++
// Swap two elements - Utility function
void swap(int* a, int* b)
{
   int t = *a;
   *a = *b;
   *b = t;
}

// partition the array using last element as pivot

int partition (int arr[], int low, int high)
{
   int i = (low - 1);
   for (int j = low; j <= high- 1; j++)
  {
      //if current element is smaller than pivot, increment the low element
      //swap elements at i and j
      if (arr[j] <= pivot)
      {
         i++; // increment index of smaller element
         swap(&arr[i], &arr[j]);
      }
   }
swap(&arr[i + 1], &arr[high]);
return (i + 1);
}
//quicksort algorithm
void quickSort(int arr[], int low, int high)
{
if (low < high)
   {
   //partition the array
    int pivot = partition(arr, low, high);
   //sort the sub arrays independently
   quickSort(arr, low, pivot - 1);
   quickSort(arr, pivot + 1, high);
   }
}
void displayArray(int arr[], int size)
  {
   int i;
   for (i=0; i < size; i++)
   cout<<arr[i]<<"\t";
   }
int main()
{
   int arr[] = {12,23,3,43,51};
   int n = sizeof(arr)/sizeof(arr[0]);
   cout<<"Input array"<<endl;
   displayArray(arr,n);
   cout<<endl;
   quickSort(arr, 0, n-1);
   cout<<"Array sorted with quick sort"<<endl;
   displayArray(arr,n);
   return 0;
}
```
Merge Sort
```C++
#include <iostream>
using namespace std;
void merge(int *,int, int , int );
void merge_sort(int *arr, int low, int high)
{
   int mid;
   if (low < high){
      //divide the array at mid and sort independently using merge sort
      mid=(low+high)/2;
      merge_sort(arr,low,mid);
      merge_sort(arr,mid+1,high);
      //merge or conquer sorted arrays
      merge(arr,low,high,mid);
   }
}
// Merge sort
void merge(int *arr, int low, int high, int mid)
{
   int i, j, k, c[50];
   i = low;
   k = low;
   j = mid + 1;
   while (i <= mid && j <= high) {
   if (arr[i] < arr[j]) {
   c[k] = arr[i];
   k++;
   i++;
}
else {
   c[k] = arr[j];
   k++;
   j++;
   }
}
while (i <= mid) {
   c[k] = arr[i];
   k++;
   i++;
}
while (j <= high) {
   c[k] = arr[j];
   k++;
   j++;
}
for (i = low; i < k; i++) {
   arr[i] = c[i];
}
}
// read input array and call mergesort
int main()
{
int myarray[30], num;
cout<<"Enter number of elements to be sorted:";
cin>>num;
cout<<"Enter "<<num<<" elements to be sorted:";
for (int i = 0; i < num; i++) { cin>>myarray[i];
}
merge_sort(myarray, 0, num-1);
cout<<"Sorted array\n";
for (int i = 0; i < num; i++)
{
   cout<<myarray[i]<<"\t";
}
}
```
Shell Sort
```C++
#include <iostream>
using namespace std;
// shellsort implementation
int shellSort(int arr[], int N)
{
for (int gap = N/2; gap > 0; gap /= 2) {
 for (int i = gap; i < N; i += 1) {
      //sort sub lists created by applying gap
int temp = arr[i];
int j;
for (j = i; j >= gap && arr[j - gap] > temp; j -= gap)
arr[j] = arr[j - gap];
      arr[j] = temp;
   }
}
return 0;
}
int main()
{
int arr[] = {45,23,53,43,18};
   //Calculate size of array
int N = sizeof(arr)/sizeof(arr[0]);
 cout << "Array to be sorted: \n";
 for (int i=0; i<N; i++)
 cout << arr[i] << " ";
 shellSort(arr, N);
cout << "\nArray after shell sort: \n";
for (int i=0; i<N; i++)
cout << arr[i] << " ";
 return 0;
}
```
Heap Sort
```C++
// function to heapify the tree
void heapify(int arr[], int n, int root)
{
int largest = root; // root is the largest element
int l = 2*root + 1; // left = 2*root + 1
int r = 2*root + 2; // right = 2*root + 2
   // If left child is larger than root
if (l < n && arr[l] > arr[largest])
largest = l;
   // If right child is larger than largest so far
if (r < n && arr[r] > arr[largest])
largest = r;
   // If largest is not root
if (largest != root)
   {
      //swap root and largest
swap(arr[root], arr[largest]);
      // Recursively heapify the sub-tree
heapify(arr, n, largest);
   }
}
// implementing heap sort
void heapSort(int arr[], int n)
{
   // build heap
for (int i = n / 2 - 1; i >= 0; i--)
heapify(arr, n, i);
   // extracting elements from heap one by one
for (int i=n-1; i>=0; i--)
   {
      // Move current root to end
swap(arr[0], arr[i]);
      // again call max heapify on the reduced heap
heapify(arr, i, 0);
   }
}
/* print contents of array - utility function */
void displayArray(int arr[], int n)
{
   for (int i=0; i<n; ++i)
   cout << arr[i] << " ";
   cout << "\n";
}
// main program
int main()
{
int heap_arr[] = {4,17,3,12,9};
int n = sizeof(heap_arr)/sizeof(heap_arr[0]);
cout<<"Input array"<<endl;
displayArray(heap_arr,n);
heapSort(heap_arr, n)
cout << "Sorted array"<<endl;
displayArray(heap_arr, n);
}
```
https://www.softwaretestinghelp.com/sorting-techniques-in-cpp/
