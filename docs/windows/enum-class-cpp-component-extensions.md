---
title: "enum 클래스 (c + + 구성 요소 확장명) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 8010fa8c-bad6-45b4-8214-b4db64d7ffe1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 876cab344f1177000f63740ca6c33bc1db1afefe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="enum-class--c-component-extensions"></a>enum 클래스(C++ 구성 요소 확장)
열거자라는 명명된 상수 집합으로 구성된 사용자 정의 형식인 열거형을 네임스페이스 범위에서 선언합니다.  
  
## <a name="all-runtimes"></a>모든 런타임  
 **주의**  
  
 C++/CX 및 C++/CLI는 표준 C++ `public enum class` 와 유사하지만 액세스 가능성 한정자가 추가된 `private enum class` 및 `enum class` 를 지원합니다. **/clr**에서 C++11 `enum class` 형식은 허용되지만, C++/CX 및 C++/CLI 형식이 아닌 원하는 ISO 열거형 형식을 보장하도록 만들어진 경고 C4472를 생성합니다. ISO 표준 c + +에 대 한 자세한 내용은 `enum` 키워드를 참조 [열거형](../cpp/enumerations-cpp.md)합니다.  
  
## <a name="windows-runtime"></a>Windows 런타임  
 **구문**  
  
```  
  
      access  
      enum class  
      enumeration-identifier  
      [:underlying-type] { enumerator-list } [var];  
accessenum structenumeration-identifier[:underlying-type] { enumerator-list } [var];  
```  
  
 **매개 변수**  
  
 *access*  
 열거형의 접근성으로, `public` 또는 `private`일 수 있습니다.  
  
 *enumeration-identifier*  
 열거형의 이름입니다.  
  
 *underlying-type*  
 (선택 사항) 열거형의 내부 형식입니다.  
  
 (선택 사항. Windows 런타임 전용) 될 수 있는 열거형의 내부 형식 `bool`, `char`, `char16`, `int16`, `uint16`, `int`, `uint32`, `int64`, 또는 `uint64`합니다.  
  
 *enumerator-list*  
 열거자 이름의 쉼표로 구분된 목록입니다.  
  
 각 열거자의 값은 컴파일러에 의해 암시적으로 정의되거나 *enumerator*`=`*constant-expression*을 참조하세요. 기본적으로 첫 번째 열거자의 값은 암시적으로 정의된 경우 0입니다. 암시적으로 정의된 각 후속 열거자의 값은 이전 열거자의 값 + 1입니다.  
  
 *var*  
 (선택 사항) 열거형 형식의 변수 이름입니다.  
  
 **주의**  
  
 자세한 내용과 예제는 [열거형](http://msdn.microsoft.com/%20library/windows/apps/hh755820.aspx)을 참조하세요.  
  
 컴파일러는 열거자의 값을 정의하는 상수 식을 *underlying-type*으로 표현할 수 없는 경우 오류 메시지를 내보냅니다.  그러나 컴파일러는 내부 형식에 적합하지 않은 값에 대해 오류를 보고하지 않습니다. 예:  
  
-   *underlying-type* 이 숫자이고, 열거자가 해당 형식의 최대값을 지정하는 경우, 그 다음에 암시적으로 정의되는 열거형 값은 표현할 수 없습니다.  
  
-   *underlying-type* 이 `bool`이고 세 개 이상의 열거자가 암시적으로 정의될 경우 처음 두 열거자 다음의 열거자는 표현할 수 없습니다.  
  
-   *underlying-type* 이 `char16`이고 열거형 값이 0xD800에서 0xDFFF까지이면 값을 표현할 수 있습니다. 그러나 이 값은 유니코드 서로게이트 쌍의 절반을 나타내므로 논리적으로 잘못된 값이며 격리에 표시되면 안 됩니다.  
  
### <a name="requirements"></a>요구 사항  
 컴파일러 옵션: **/ZW**  
  
## <a name="common-language-runtime"></a>공용 언어 런타임 
 **구문**  
  
```  
  
      access  
      enum class  
      name [:type] { enumerator-list } var;  
accessenum structname [:type] { enumerator-list } var;  
```  
  
 **매개 변수**  
  
 `access`  
 열거형의 접근성입니다.  **public** 또는 `private`일 수 있습니다.  
  
 `enumerator-list`  
 열거형에서 식별자(열거자)의 쉼표로 구분된 목록입니다.  
  
 `name`  
 열거형의 이름입니다.  관리되는 익명 열거형은 허용되지 않습니다.  
  
 `type` (선택 사항)  
 *식별자*의 내부 형식입니다.  서명되거나 서명되지 않은 버전의 int, short 또는 long과 같은 스칼라 형식일 수 있습니다.  `bool` 또는 `char` 도 사용할 수 있습니다.  
  
 `var` (선택 사항)  
 열거형 형식의 변수 이름입니다.  
  
 **주의**  
  
 **enum 클래스** 및 **enum 구조체** 는 동일한 선언입니다.  
  
 열거형에는 관리되거나 또는 C++/CX 및 표준이라는 두 가지 유형이 있습니다.  
  
 다음과 같이 관리되거나 C++/CX 열거형을 정의할 수 있습니다.  
  
```cpp  
public enum class day {sun, mon };  
```  
  
 다음과 의미 체계가 같습니다.  
  
```cpp  
ref class day {  
public:  
   static const int sun = 0;  
   static const int mon = 1;  
};  
```  
  
 표준 열거형은 다음과 같이 정의할 수 있습니다.  
  
```cpp  
enum day2 { sun, mon };  
```  
  
 다음과 의미 체계가 같습니다.  
  
```cpp  
static const int sun = 0;  
static const int mon = 1;  
```  
  
 관리되는 열거자 이름(*식별자*)은 열거형이 정의되어 있는 범위에 삽입되지 않습니다. 열거자에 대한 모든 참조를 정규화해야 합니다(*이름*`::`*식별자*).  이러한 이유로, 관리되는 익명 열거형은 정의할 수 없습니다.  
  
 표준 열거형의 열거자는 바깥쪽 범위에 강력하게 삽입됩니다.  즉, 바깥쪽 범위에 열거자와 동일한 이름을 가진 다른 기호가 있을 경우 컴파일러에서 오류를 생성합니다.  
  
 Visual C++ 2002 및 Visual C++ 2003에서는 열거자가 약하게 삽입됩니다(동일한 이름을 가진 다른 식별자가 없을 경우 바깥쪽 범위에 표시됨).  
  
 표준 C++ enum이 정의된 경우( **클래스** 또는 `struct`없이) **/clr** 을 사용하여 컴파일하면 열거형이 관리되는 enum으로 컴파일됩니다.  열거형이 여전히 관리되지 않는 열거형의 의미 체계를 사용합니다.  컴파일러는 Visual C++ 컴파일러가 인식하는 `Microsoft::VisualC::NativeEnumAttribute`특성을 삽입하여 열거형을 네이티브 열거형으로 만들려는 프로그래머의 의도를 확인합니다.  다른 컴파일러에는 표준 열거형이 관리되는 열거형으로 표시됩니다.  
  
 /clr을 사용하여 컴파일된 명명된 표준 열거형은 어셈블리에 관리되는 열거형으로 표시되며 다른 관리되는 컴파일러에서 사용될 수 있습니다.   그러나 명명되지 않은 표준 열거형은 어셈블리에서 공개적으로 표시되지 않습니다.  
  
 Visual C++ 2002 및 Visual C++ 2003에서 함수 매개 변수  
  
```cpp  
// mcppv2_enum.cpp  
// compile with: /clr  
enum E { a, b };  
void f(E) {System::Console::WriteLine("hi");}  
  
int main() {  
   E myi = b;  
   f(myi);  
}  
```  
  
 에 형식으로 사용된 표준 열거형은 함수 서명에 대해 MSIL에서 다음을 내보냅니다.  
  
```  
void f(int32);  
```  
  
 그러나 현재 버전의 컴파일러에서는 표준 열거형이 [NativeEnumAttribute] 및 함수 서명에 대해 MSIL에서 다음을 사용하여 관리되는 열거형으로 내보내집니다.  
  
```  
void f(E)  
```  
  
 네이티브 열거형에 대한 자세한 내용은 [C++ Enumeration Declarations](../cpp/enumerations-cpp.md)를 참조하십시오.  
  
 CLR 열거형에 대한 자세한 내용은 다음을 참조하세요.  
  
-   [열거형의 내부 형식](../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md)  
  
### <a name="requirements"></a>요구 사항  
 컴파일러 옵션: **/clr**  
  
### <a name="examples"></a>예제  
 **예제**  
  
 내림차순  
  
```cpp  
// mcppv2_enum_2.cpp  
// compile with: /clr  
// managed enum  
public enum class m { a, b };  
  
// standard enum  
public enum n { c, d };  
  
// unnamed, standard enum  
public enum { e, f } o;  
  
int main()   
{  
   // consume managed enum  
   m mym = m::b;  
   System::Console::WriteLine("no automatic conversion to int: {0}", mym);  
   System::Console::WriteLine("convert to int: {0}", (int)mym);  
  
   // consume standard enum  
   n myn = d;  
   System::Console::WriteLine(myn);  
  
   // consume standard, unnamed enum  
   o = f;  
   System::Console::WriteLine(o);  
}   
```  
  
 **출력**  
  
```Output  
no automatic conversion to int: b  
  
convert to int: 1  
  
1  
  
1  
  
```  
  
## <a name="see-also"></a>참고 항목  
 [런타임 플랫폼용 구성 요소 확장](../windows/component-extensions-for-runtime-platforms.md)