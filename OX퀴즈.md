# 코딩테스트 연습 - OX퀴즈 (LV.0)

## 풀이

**1. 식 문자열을 잘라서 숫자와 연산자를 꺼낸다**

`quiz` 안에는 `"3 - 4 = -3"` 같은 식이 들어 있다

맞으면 `"O"`, 틀리면 `"X"`를 배열로 반환하면 된다

<span style="color:red">ex)</span>

- `"3 - 4 = -3"` → `3-4=-1` 이라서 `"X"`
- `"5 + 6 = 11"` → `5+6=11` 이라서 `"O"`

<br>

**2. `split()`으로 공백 기준으로 나눈다**

```python
parts = q.split()
```

`"3 - 4 = -3"` → `["3", "-", "4", "=", "-3"]`

- `parts[0]` → X
- `parts[1]` → 연산자
- `parts[2]` → Y
- `parts[4]` → Z (`=` 다음)

<br>

**3. 연산해서 Z랑 같으면 O, 다르면 X**

```python
if op == '+':
    result = x + y
else:
    result = x - y

if result == z:
    answer.append("O")
else:
    answer.append("X")
```

음수도 `int()`로 바꾸면 된다

`"-3"` → `-3`

---

## 오답노트

**1. 식 전체를 한 번에 계산하려고 했다**

`eval(q)` 같은 걸 쓰면 편해 보이지만, 코테에서는 보통 안 쓰는 편이다

공백으로 나눠서 X, 연산자, Y, Z를 직접 꺼내는 게 안전하다

<br>

**2. `=`도 split 결과에 들어간다**

`parts[3]`은 `"="` 이다

답은 `parts[4]`에 있다

<br>

**3. 파이썬은 `append`로 리스트에 넣는다**

자바 `add`랑 비슷하다

`answer.append("O")`

---

## 정답

```python
def solution(quiz):
    answer = []

    for q in quiz:
        parts = q.split()
        x = int(parts[0])
        op = parts[1]
        y = int(parts[2])
        z = int(parts[4])

        if op == '+':
            result = x + y
        else:
            result = x - y

        if result == z:
            answer.append("O")
        else:
            answer.append("X")

    return answer
```
