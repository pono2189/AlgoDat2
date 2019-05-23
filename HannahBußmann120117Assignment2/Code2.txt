import java.util.*;
public class Heapsort {
	
	
	public static void exchange(int[] array, int i, int j){ //i and j exchange places in the array
		int temp = array[i];
		array[i] = array[j];
		array[j] = temp;
	}

	public static void maxheap(int[] array ,int size, int i){
		int parent = i; 	// i is the parent of left and right
		int left = 2*i + 1;	// the left child of i
		int right = left + 1; // the right child of i 
		
		if ((left < size)){ 			//checks if the left child even exists 
			if(array[i]< array[left]){  //and if the parent(i) is bigger than its left child
				parent = left;
			}
		}
		
		if ((right < size)){ 			//same as with left but with the right child
			if(array[parent] < array[right]){
				parent = right;
			}
		}
		
		if (parent != i){ 					// if the parent is not equal to i anymore
			exchange(array, i, parent );	// it means the parent has changed
			maxheap(array, size, parent);	//so we need to exchange i and parent  
											// so that the variable parent is on the root 
		}
	}

	public static void heapsort(int [] arr){
		
		for (int i = arr.length; i >= 0; i-- ){
			maxheap(arr, arr.length, i);		// a heap is build
		}
		
		for (int i = arr.length-1; i >= 0; i-- ){ // the elements are each put to the right position 
			exchange(arr, i, 0); //
			maxheap(arr, i, 0);
		}
		
		for(int i = 0; i < arr.length; i++){
			System.out.print(arr[i] + " ");		//prints sorted array
		}
		System.out.println(" ");
	}
	
	public static void main(String[] args){
		
		System.out.println("Array 1: ");
		int[] array1 = {0,  3, 2, 25, 1, 104, 7};
		heapsort(array1);
		
		System.out.println("Array 2: ");
		int[] array2 = {-7, -1, 17, 0, 2, 5};
		heapsort(array2);
		
		System.out.println("Array 3: ");
		int[] array3 = {3, 7, 2, 3, 9, 23, 3};
		heapsort(array3);
		
	}
}

