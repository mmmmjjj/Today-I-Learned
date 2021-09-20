# NextPermutation

- 현 순열에서 사전 순으로 다음 순열 생성

- 재귀는 사용하지 않고 조합으로 활용 가능
- c++은 API로 제공되지만 JAVA에는 없다 코테에 많이 나온다 NP구현

## 알고리즘

- 배열을 오름차순으로 정렬

- 아래의 과정을 반복하여 사전 순으로 다음으로 큰 순열 찾기
    - 뒤쪽부터 탐색하며 교환위치(i-1) 찾기 (i : 꼭대기)
    
    - 뒤쪽부터 탐색하며 교환위치와 교환할 큰 값 위치(j) 찾기
    - 두 위치 값 (i-1, j) 교환
    - 꼭대기 위치 (i) 부터 맨 뒤까지 오름차순 정렬

    ![image](https://user-images.githubusercontent.com/67090601/132951260-7e205d84-186c-4cea-80e2-18d8963edec7.png)

## 코드

```java
public class NextPermutationTest {

	public static void main(String[] args) {

		int[] input = { 7, 1, 4 };

		Arrays.sort(input); // 가장 작은 순열 만들기. 1 4 7

		do {
			// 순열 사용
			System.out.println(Arrays.toString(input));
			// 넥퍼 돌려
		} while (np(input));
	}

	// 다음 큰 순열이 있으면 true, 없으면 false
	private static boolean np(int[] numbers) {

		int N = numbers.length;

		// step1. 꼭대기를 찾는다. 꼭대기를 통해 교환위치 찾기
		int i = N - 1;
		while (i > 0 && numbers[i - 1] >= numbers[i]) --i;
		
		if(i==0) return false; //당신이 제일 크기 때문에 다음 순열은 없어요
		
		//step2. 리턴이 안됐다는 소리. 꼭대기를 찾았음 i-1 위치값과 교환할 큰 값을 찾아야 한다.
		int j = N-1;
		
		while(numbers[i-1]>=numbers[j]) --j;
		
		//step3. i-1 위치값과 j위치값 교환
		swap(numbers,i-1,j);
		
		//step4.  꼭대기 (i)부터 맨 뒤 까지 내림차순 형태의 순열을 오름차순으로 처리
		int k = N-1;
		while(i<k) {
			swap(numbers,i++,k--);
		}
		
		return true;

	}
	
	private static void swap(int[] numbers, int i, int j) {
		int temp = numbers[i];
		numbers[i] = numbers[j];
		numbers[j] = temp;
	}

}
```

- 조합

```java
public class CombNextPermutationTest {

	public static void main(String[] args) {

		int[] input = { 7, 1, 4, 2, 3 };
		int N = input.length;
		int R = 3;
		
		int []p = new int[N]; //넥퍼를 돌릴 배열
		//뒤쪽부터 r개 만큼 1채우기
		
		int cnt = 0;
		while(++cnt<=R) p[N-cnt] = 1; // 0 0 1 1 1 상태가 된다.
		
		do {
			// 조합 사용
			for (int i = 0; i < N; i++) {
				if(p[i]==1) System.out.println(input[i]+" ");
			}
			System.out.println();
		} while (np(p));
	}

	이하 아래는 위 NP 코드와 같다.
```
