---
description: 에 대해 자세히 알아보세요. Xml 파일 처리
title: .Xml 파일 처리
ms.date: 11/04/2016
helpviewer_keywords:
- XML documentation, processing XML file
ms.assetid: e70fdeae-80ac-4872-ab24-771c5635cfbf
ms.openlocfilehash: ded4551adcc4bec4aef27fe38f47470065ea9ef4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192696"
---
# <a name="xml-file-processing"></a>.Xml 파일 처리

컴파일러는 문서 생성을 위해 태그가 지정되는 코드의 각 구문에 대해 ID 문자열을 생성합니다. 자세한 내용은 [권장 태그 문서 주석](recommended-tags-for-documentation-comments-visual-cpp.md)을 참조하세요. ID 문자열은 구문을 고유하게 식별합니다. .xml 파일을 처리하는 프로그램은 ID 문자열을 사용하여 문서가 적용되는 해당 .NET Framework 메타데이터 또는 리플렉션 항목을 식별할 수 있습니다.

.xml 파일은 코드의 계층적 표현이 아니며 각 요소에 대해 생성된 ID를 포함하는 단순 목록입니다.

컴파일러는 ID 문자열을 생성할 때 다음 규칙을 관찰합니다.

- 문자열에 공백이 배치되지 않았습니다.

- ID 문자열의 첫 부분이 뒤에 콜론이 붙은 한 글자로 식별 대상 멤버를 식별합니다. 사용되는 멤버 유형은 다음과 같습니다.

  | 문자 | 설명 |
  |---------------|-----------------|
  | N | namespace<br /><br /> 네임스페이스에 문서 주석을 추가할 수는 없으며 네임스페이스에 대한 cref 참조는 가능합니다. |
  | T | 유형: 클래스, 인터페이스, 구조체, 열거형, 대리자 |
  | D | 형식 정의 |
  | F | 필드(field) |
  | P | 속성(인덱서 또는 기타 인덱싱된 속성 포함) |
  | M | 메서드(생성자, 연산자 등의 특수 메서드 포함) |
  | E | event |
  | ! | 오류 문자열<br /><br /> 문자열의 나머지 부분은 오류에 대한 정보를 제공합니다. MSVC 컴파일러는 확인할 수 없는 링크에 대 한 오류 정보를 생성 합니다. |

- 문자열의 두 번째 부분은 네임스페이스의 루트부터 시작되는 항목의 정규화된 이름입니다. 항목의 이름과 바깥쪽 형식 또는 형식들 및 네임스페이스는 마침표로 구분됩니다. 항목 자체의 이름에 마침표가 있으면 이러한 요소를 구분하는 마침표가 해시 기호('#')로 바뀝니다. 항목 이름에는 해시 기호가 직접적으로 포함되지 않는다고 가정합니다. 예를 들어 `String` 생성자의 정규화된 이름은 "System.String.#ctor"일 수 있습니다.

- 속성 및 메서드의 경우 메서드에 대한 인수가 있으면 괄호로 묶인 인수 목록이 문자열 뒤에 붙습니다. 인수가 없으면 괄호도 없습니다. 인수는 쉼표로 구분됩니다. 각 인수의 인코딩은 .NET Framework 서명에서 인수가 인코딩되는 방식을 그대로 따릅니다.

  - 기본 형식. 일반 형식(ELEMENT_TYPE_CLASS 또는 ELEMENT_TYPE_VALUETYPE)은 해당 형식의 정규화된 이름으로 표시됩니다.

  - 내장 형식(ELEMENT_TYPE_I4, ELEMENT_TYPE_OBJECT, ELEMENT_TYPE_STRING, ELEMENT_TYPE_TYPEDBYREF, ELEMENT_TYPE_VOID)은 해당하는 전체 형식의 정규화된 이름으로 표시됩니다(예: **System.Int32** 또는 **System.TypedReference**).

  - ELEMENT_TYPE_PTR은 수정된 형식 뒤에 '*'로 표시됩니다.

  - ELEMENT_TYPE_BYREF는 수정된 형식 뒤에 ‘\@’으로 표시됩니다.

  - ELEMENT_TYPE_PINNED는 수정된 형식 뒤에 '^'로 표시됩니다. MSVC 컴파일러는이를 생성 하지 않습니다.

  - ELEMENT_TYPE_CMOD_REQ는 수정된 형식 뒤에 '&#124;' 및 한정자 클래스의 정규화된 이름으로 표시됩니다. MSVC 컴파일러는이를 생성 하지 않습니다.

  - ELEMENT_TYPE_CMOD_OPT는 수정된 형식 뒤에 '!' 및 한정자 클래스의 정규화된 이름으로 표시됩니다.

  - ELEMENT_TYPE_SZARRAY는 배열의 요소 형식 뒤에 "[]"로 표시됩니다.

  - ELEMENT_TYPE_GENERICARRAY는 배열의 요소 형식 뒤에 "[?]"로 표시됩니다. MSVC 컴파일러는이를 생성 하지 않습니다.

  - ELEMENT_TYPE_ARRAY는 [*lowerbound*:`size`,*lowerbound*:`size`]로 표시됩니다. 여기서 쉼표 수는 순위 - 1에 해당하는 값이고, 각 차원의 하한과 크기(확인된 경우)는 10진수로 표시됩니다. 하한이나 크기가 지정되지 않은 경우에는 생략됩니다. 특정 차원의 하한과 크기를 생략하면 ':'도 생략됩니다. 예를 들어 하한이 1이고 크기가 지정되지 않은 2차원 배열은 [1:,1:]로 표시됩니다.

  - ELEMENT_TYPE_FNPTR은 "=FUNC:`type`(*signature*)"로 표시됩니다. 여기서 `type`은 반환 형식이고 *signature* 는 메서드의 인수입니다. 인수가 없으면 괄호는 생략됩니다. MSVC 컴파일러는이를 생성 하지 않습니다.

  다음 서명 구성 요소는 오버로드된 메서드를 구분하는 데 사용되지 않으므로 표시되지 않습니다.

  - 호출 규칙

  - 반환 형식

  - ELEMENT_TYPE_SENTINEL

- 변환 연산자에 한해 메서드의 반환 값은 전에 인코딩된 것처럼 뒤에 반환 형식이 붙은 '~'로 인코딩됩니다.

- 제네릭 형식의 경우에는 형식 이름 뒤에 역따옴표와 제네릭 형식 매개 변수의 수를 나타내는 숫자가 차례로 붙습니다.  예를 들면 다음과 같습니다.

    ```xml
    <member name="T:MyClass`2">
    ```

  `public class MyClass<T, U>`로 정의된 형식의 경우입니다.

  제네릭 형식을 매개 변수로 사용하는 메서드의 경우 제네릭 형식 매개 변수는 \`0, \`1과 같이 앞에 역따옴표가 붙은 숫자로 지정됩니다.  각 숫자는 해당 형식의 제네릭 매개 변수에 대한 0부터 시작되는 배열 표기법을 나타냅니다.

## <a name="example"></a>예제

다음 예제에서는 클래스와 해당 멤버의 ID 문자열이 생성되는 방식을 보여 줍니다.

```cpp
// xml_id_strings.cpp
// compile with: /clr /doc /LD
///
namespace N {
// "N:N"

   /// <see cref="System" />
   //  <see cref="N:System"/>
   ref class X {
   // "T:N.X"

   protected:
      ///
      !X(){}
      // "M:N.X.Finalize", destructor's representation in metadata

   public:
      ///
      X() {}
      // "M:N.X.#ctor"

      ///
      static X() {}
      // "M:N.X.#cctor"

      ///
      X(int i) {}
      // "M:N.X.#ctor(System.Int32)"

      ///
      ~X() {}
      // "M:N.X.Dispose", Dispose function representation in metadata

      ///
      System::String^ q;
      // "F:N.X.q"

      ///
      double PI;
      // "F:N.X.PI"

      ///
      int f() { return 1; }
      // "M:N.X.f"

      ///
      int bb(System::String ^ s, int % y, void * z) { return 1; }
      // "M:N.X.bb(System.String,System.Int32@,System.Void*)"

      ///
      int gg(array<short> ^ array1, array< int, 2 >^ IntArray) { return 0; }
      // "M:N.X.gg(System.Int16[], System.Int32[0:,0:])"

      ///
      static X^ operator+(X^ x, X^ xx) { return x; }
     // "M:N.X.op_Addition(N.X,N.X)"

      ///
      property int prop;
      // "M:N.X.prop"

      ///
      property int prop2 {
      // "P:N.X.prop2"

         ///
         int get() { return 0; }
         // M:N.X.get_prop2

         ///
         void set(int i) {}
         // M:N.X.set_prop2(System.Int32)
      }

      ///
      delegate void D(int i);
      // "T:N.X.D"

      ///
      event D ^ d;
      // "E:N.X.d"

      ///
      ref class Nested {};
      // "T:N.X.Nested"

      ///
      static explicit operator System::Int32 (X x) { return 1; }
      // "M:N.X.op_Explicit(N.X!System.Runtime.CompilerServices.IsByValue)~System.Int32"
   };
}
```

## <a name="see-also"></a>참고 항목

[XML 문서](xml-documentation-visual-cpp.md)
