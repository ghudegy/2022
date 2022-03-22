# 진짜 최종 구데기컵 2 2 에디토리얼

(하고 싶은 말)

## 들어가기 전에

올해 구데기컵을 부활시키기 위해 제2회 진짜 최종 구데기컵 2를 열었습니다. 대회 이름에 2가 두 개고 마침 2022년이라서 시작 시각도 22:22:22고 만점도 222,222점입니다.

* "셀 수 없는 문제를 해결하신 모든 분들께 solved.ac 배경과 뱃지를 드립니다": 문제 번호가 자연수가 아니라서 셀 수 없습니다. 아무 문제나 하나 풀면 드립니다.
* "⅔ 이하의 인터랙티브 문제가 출제될 예정입니다": 원래는 문제 번호가 ⅔번 이하인 인터랙티브 문제를 출제하려고 했는데, 수식에 이모지를 섞어넣을 수 있다는 사실을 알아버렸습니다. 이제부터 📏 < 0입니다.

## ![1](https://user-images.githubusercontent.com/4417431/159480297-0b813cb4-d176-47c8-aa5d-50ba1b943c48.png)번. 한별 찍기

## ![2](https://user-images.githubusercontent.com/4417431/159480764-988028d3-5238-42f2-981f-8e25d6a47aa8.png)번. Binary Game 2

만점을 받으려면 **C++, Java, Swift, Ruby로 모두 컴파일 가능한 하나의 코드**를 제출해야 한다. 이런 코드를 [polyglot](https://en.wikipedia.org/wiki/Polyglot_(computing))이라고 한다.

### C++ & Swift
Polyglot을 작성하는 좋은 방법은 주석을 활용하는 것이다. 한 언어에서 주석이고 다른 언어에서 주석이 아닌 공간을 만들면, 그 공간에서는 한 언어의 문법을 신경쓰지 않고 다른 언어를 자유롭게 쓸 수 있기 때문이다.

C++과 Swift의 주석 기호는 `//`와 `/* */`로 동일하지만, 한 가지 중요한 차이는 Swift에서만 `/* /* */ */` 같은 식의 다중 주석을 쓸 수 있다는 것이다. 따라서 `/* /* */`로 Swift에서는 주석이고, C++에서는 주석이 아닌 공간을 만들 수 있다. 이제 문제를 푸는 C++ 코드를 작성한 뒤, `// */`을 통해 C++에서는 주석이고, Swift에서는 주석이 아닌 공간을 만들면 된다. 딱 한 줄만 쓸 수 있다는 제약이 있지만, 어차피 모든 구문을 한 줄에 몰아 쓸 수 있으므로 상관없다.

```
/* /* */
cpp_code
// */ swift_code
```

### C++ & Ruby
Ruby는 한 줄 주석으로 `#`을, 여러 줄 주석으로 `=begin`과 `=end`를 사용한다. 단, `=begin`과 `=end`를 쓸 때는 그 줄에 주석 기호를 제외한 아무 것도 없어야 한다.

어차피 `#`은 C++에서도 헤더를 include하기 위해 쓰일 테니까, iostream을 include하는 동시에 Ruby에서 주석인 공간을 만들자. 같은 줄에 `/*`을 쓰면 그 다음 줄은 Ruby에서만 주석이 아닌 공간이 되므로 자유롭게 Ruby 코드를 작성할 수 있다. 그 다음 줄에 `=begin`으로 Ruby 주석을 시작하고, `*/`으로 C++ 주석을 닫으면 C++ 코드를 작성할 수 있다. 이제 같은 방식으로 `=end`를 넣어주면 된다.

```
#include <iostream> /*
ruby_code
=begin
*/
cpp_code
/*
=end
# */
```

### C++ & Swift & Ruby
`#if true`와 `#endif`는 C++과 Swift에서 모두 유효한 지시문이다. 따라서 위의 두 테크닉을 적절히 조합하여 풀 수 있다.

```
#if true /*
ruby_code
=begin
/* */
cpp_code
// */ swift_code
#endif
/*
=end
# */
```

### C++ & Java
Java에서는 모든 문자를 `\uxxxx`의 형태로 쓸 수 있다. 심지어 개행 문자도 `\u000a`으로 쓸 수 있고, Java는 이를 진짜로 개행 문자로 취급하고 `//` 주석을 해제한다. 이를 사용하면 C++에서만 주석인 공간을 쉽게 만들 수 있다.

```
// \u000a java_code /*
cpp_code
// */
```

추가로, `//` 주석이 있는 줄의 마지막에 `\`이 오면 C++에서만 다음 줄도 주석이 된다. 출제자의 풀이는 이 테크닉을 사용하지 않는다.

### C++ & Java & Swift & Ruby
이제 C++ & Swift & Ruby 코드에 위의 `\u000a` 테크닉을 적용하여 Java 코드를 넣어주면 된다. 우연히도 `//`는 Ruby에서 empty regex로 인식하기 때문에, `//; #`을 사용하여 모든 언어에서 주석인 공간을 만들 수 있다. 여기에 `\u000a`를 쓰면 Java에서만 주석이 아닌 공간이 만들어진다.

그 다음 줄부터는 모든 공간을 주석으로 만들어야 한다. 그러려면 주석이 해제될 때마다 주석을 다시 달아야 하고, 이는 `// \u000a /*`로 해결할 수 있다.

```
//; # \u000a java_code /*
#if true /*
ruby_code
=begin
/* */ // \u000a /*
cpp_code
// */
// */ swift_code // \u000a /*
#endif
/*
=end
# */
```

## ![3](https://user-images.githubusercontent.com/4417431/159481765-13b348f4-29cb-45fb-81b3-0dec2141c30f.png)번. Fewest Moves Challenge

## ![4](https://user-images.githubusercontent.com/4417431/159481027-fedee281-4f4a-4d7f-8b8e-427eefebd0a9.png)번. _multiple_ edges

## ![5](https://user-images.githubusercontent.com/4417431/159481133-ea41767d-f5be-49a3-ad41-b51112e6c92b.png)번. Baekjoon Wordline Judge

[Wordle](https://en.wikipedia.org/wiki/Wordle) 275 3/6

```
⬜⬜⬜🟨🟨
🟩🟨⬜🟨🟩
🟩🟩🟩🟩🟩
```

## ![6](https://user-images.githubusercontent.com/4417431/159481232-3aa3fdf6-af20-47e2-8a8f-6f316b091f06.png)번.  (=BOJ 문제 번호)

## ![7](https://user-images.githubusercontent.com/4417431/159481340-8269345b-2208-4ab4-9291-8be95fcb5e09.png)번. 문제 이름

## ![8](https://user-images.githubusercontent.com/4417431/159481340-8269345b-2208-4ab4-9291-8be95fcb5e09.png)번. 문제 이름

## ![9](https://user-images.githubusercontent.com/4417431/159481562-1cf2838c-8b4e-42b1-b87f-bfbc2743f59f.png)번. 제1회 구데기그릇 (홀수형)

## ![10](https://user-images.githubusercontent.com/4417431/159481986-271660e3-5667-4f1a-b417-a6a84718f2db.png)번. 제1회 구데기그릇 (짝수형)

## ![11](https://user-images.githubusercontent.com/4417431/159481708-96effd29-70d8-4964-b218-5ab76438a444.png)번. 하이퍼하게 누울 하이퍼 자리를 찾아라

## ![12](https://user-images.githubusercontent.com/4417431/159480900-7a162c89-02fd-4ff0-aff9-88145c359537.png)번. 🅰➕🅱
