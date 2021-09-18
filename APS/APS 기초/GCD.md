## 최대 공약수 (GCD, Greatest Common Divisor)

- 두 자연수의 공통 약수 중 최댓값

## 최소 공배수 (LCM, Least Common Multiple)

- 두  자연수의 공통 배수 중 최솟값
- 최소공배수 = 두 자연수의 곱 / 최대공약수

## 유클리드 호제법 (Euclidean Algorithm)

- 2개의 자연수 a,b에 대하여  a와 b의 최대공약수 = b와 a를 b로 나눈 나머지의 최대공약수

- `시간복잡도` : `O(logN)`

1) 입력 받은 두 수중 큰 수를 a , 작은수를 b로 정한다.

2) a를 b로 나눈 값의 나머지를 r이라고 지칭한다.

3) r이 0이라면 a는 b로 나누어 지기 때문에 최대 공약수는 b가 된다.

4) 만약 r이 0이 아니라면, a값은 b로 b값은 r로 변경한 뒤 3번 과정을 반복한다.

  → 유클리드 호제법으로 GCD, LCM 둘 다 구할 수 있다.

## 구현

`code` `재귀`

```java
int gcd(int a, int b) {	
	if(b==0) return a;

	return gcd(b, a%b);
}

int lcm(int a, int b) {
	return a * b / gcd(a,b);
} 

//재귀로 풀면 런타임이 길다..
```

`code` `재귀x`

```java
int gcd(int a, int b){
        while (b != 0) {
            int tmp = b;
            b = a % b;
            a = tmp;
        }
        return a;
    }
```

### 참고 문제::

[2609번: 최대공약수와 최소공배수](https://www.acmicpc.net/problem/2609)
