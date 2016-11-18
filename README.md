# My-Hello-World
The First Repository
package ArrayTest;

/*
 * 书名是《轻松学算法-互联网算法面试宝典》
 * 
 * 
 * 
 * 
 */

//寻找旋转数组的拐点，数组一定要有序
public class ArrayDot {
	// 直接遍历法,1,2,3,4,5,6,7->4,5,6,7,1,2,3跟旋转字符串相同
	// 时间复杂度为O(n)
	public static void findDot1(int[] array) {
		for (int i = 1; i < array.length; i++) {
			if (array[i] < array[i - 1]) {
				System.out.println("拐点元素为" + array[i] + "下标为" + i);
				return;
			}
		}
	}

	// 二分查找，时间复杂度为O(logn)
	public static void findDot2(int[] array) {
		int low = 0;
		int high = array.length - 1;
		while (low < high) {
			if (high - low == 1) {
				// 如果只剩两个元素
				if (array[low] < array[0]) {
					System.out.println("拐点元素为" + array[low] + "下标为" + low);
					return;
				} else {
					System.out.println("拐点元素为" + array[high] + "下标为" + high);
					return;
				}
			}
			int middle = (low + high) / 2;
			if (array[middle] >= array[low]) {
				// 说明左边是非递减的，拐点在右边
				low = middle;
			} else {
				high = middle;
			}
		}
	}

	public static void main(String[] args) {
		int[] array = { 4, 5, 6, 7, 1, 2, 3 };
		int[] array2 = { 1, 1, 1, 0, 0, 0, 1 };
		findDot1(array);
		findDot1(array2);
		findDot2(array);
		findDot2(array2);
	}
}
