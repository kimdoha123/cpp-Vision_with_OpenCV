# 📌 포인터와 캐스팅 정리

---

## 1. 포인터의 3가지 측면

### 1.1 일반 포인터
- **char \*pMap = nullptr**  
  - `pMap`은 **char** 타입 데이터를 가리키는 포인터로, 초기화되지 않았을 때 `nullptr`로 설정

### 1.2 캐스팅된 포인터
- **(char \*) pMap**  
  - `pMap`을 명시적으로 **char 포인터 타입**으로 캐스팅

### 1.3 복잡한 포인터 선언
- **char (\* pMap)**  
  - `pMap`은 **char를 가리키는 포인터**를 선언한 것

---

## 2. 다형성 포인터 예제

### void 타입 포인터와 다양한 캐스팅
- **void \*pObj = nullptr**  
  - `pObj`는 **아무 타입**의 데이터를 가리킬 수 있는 **범용 포인터**

#### pObj에 캐스팅된 데이터 할당
1. **pObj = (char \*) pMap**  
   - `pMap`을 `char \*`로 캐스팅 후 `pObj`에 할당.
2. **pObj = (double \*) pMap**  
   - `pMap`을 `double \*`로 캐스팅 후 `pObj`에 할당.
3. **pObj = (Person \*) pMap**  
   - `pMap`을 사용자 정의 데이터 타입인 `Person \*`로 캐스팅 후 `pObj`에 할당.

---

## 3. 캐스팅 종류

### 3.1 정적 캐스팅 (static_cast)
- 컴파일 시간에 타입 변환을 수행하며, 타입 안정성이 보장됨
- **예제**:  
  ```cpp
  int a = static_cast<int>(10.1);  // 결과: a = 10
  ```
---
### 3.2 const_cast
- const로 선언된 변수를 상수로 취급하지 않도록 변환
- **예제**:
  ```cpp
  const char* name = "hello";
  char* modi = const_cast<char*>(name);	//const 제거
  ```
---
### 3.3 reinterpret_cast
- 포인터를 전혀 다른 데이터 타입으로 변환
- 주의: 안전성을 보장하지 않으므로, 사용할 때 주의
- **예제**:
  ```cpp
  Person* person = reinterpret_cast<Person*>(pHuman);  // pHuman을 Person*로 변환
  ```
---
### 3.4 dynamic_cast
- 상속 관계에서 부모 클래스 포인터를 자식 클래스 포인터로 변환하며, 런타임에 타입 안정성을 검증
- **예제**:
  ```cpp
  	Child* child = dynamic_cast<Child*>(pParent);  // 부모 포인터를 자식 포인터로 변환
	if (child) {
	    // 변환 성공
	} else {
   	 // 변환 실패
	}
  ```

## 요약
  1. 포인터는 데이터를 가리키는 도구로, 타입에 따라 다양한 형태로 선언 및 변환이 가능
  2. void 포인터는 모든 타입을 가리킬 수 있지만, 명시적 캐스팅이 필요
  3. 캐스팅은 static_cast, const_cast, reinterpert_cast, dynamic_cast 등 여러 방식이 있으며, 각각의 목적과 상황에 맞게 사용해야함
