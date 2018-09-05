---
title: 빠른 참조 (C + + /cli CX) | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: ba457195-26e5-43aa-b99d-24a871e550f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 272921d0a9ac00ec5ee69fb50a17a34e257b1725
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43692590"
---
# <a name="quick-reference-ccx"></a>빠른 참조(C++/CX)
Windows 런타임에서 신뢰할 수 있는 운영 체제 환경 에서만에서 실행 하 고 권한 있는 함수, 데이터 형식 및 장치를 사용 하 여 Microsoft Store 통해 배포 되는 유니버설 Windows 플랫폼 (UWP) 앱을 지원 합니다. C + + /cli CX Windows 런타임에 대 한 앱의 작성을 단순화 합니다. 이 문서는 빠른 참조입니다. 전체 설명서를 참조 하세요. [형식 시스템](../cppcx/type-system-c-cx.md)입니다.  
  
 명령줄에서 빌드할 때 사용 합니다 **/ZW** 컴파일러 옵션을 사용 하는 UWP 앱 또는 Windows 런타임 구성 요소를 작성 합니다. Windows 런타임 메타 데이터 (.winmd) 파일에 정의 된, Windows 런타임 선언에 액세스 하려면 지정 된 `#using` 지시문 또는 **/FU** 컴파일러 옵션입니다. UWP 앱 용 프로젝트를 만들면 Visual Studio는 기본적으로 이러한 옵션을 설정 하 고 모든 Windows 런타임 라이브러리에 대 한 참조를 추가 합니다.  
  
## <a name="quick-reference"></a>빠른 참조  
  
|개념|표준 C++|C++/CX|설명|  
|-------------|--------------------|------------------------------------------------------------------|-------------|  
|기본 형식|C++ 기본 형식|C + + /CX Windows 런타임에서 정의 된 기본 형식을 구현 하는 기본 형식입니다.|`default` 네임 스페이스에는 다음이 포함 되어 C + + /CX 기본 제공 되는 기본 형식입니다. 컴파일러는 암시적으로 매핑합니다 C + + /cli CX 기본 형식을 표준 c + + 형식입니다.<br /><br /> `Platform` 네임 스페이스의 패밀리에서 기본적인 Windows 런타임 형식을 구현 하는 형식을 포함 합니다.|  
||`bool`|`bool`|8비트 부울 값입니다.|  
||`__wchar_t`|`char16`|유니코드(UTF-16) 코드 포인트를 나타내는 숫자가 아닌 16비트 값입니다.|  
||`short`<br /><br /> `unsigned short`|`int16`<br /><br /> `uint16`|16비트 부호 있는 정수입니다.<br /><br /> 16비트 부호 없는 정수입니다.|  
||`int`<br /><br /> `unsigned int`|`int`<br /><br /> `uint32`|32비트 부호 있는 정수입니다.<br /><br /> 32비트 부호 없는 정수입니다.|  
||`long long` 또는 `__int64`<br /><br /> `unsigned long long`|`int64`<br /><br /> `uint64`|64비트 부호 있는 정수입니다.<br /><br /> 64비트 부호 없는 정수입니다.|  
||`float, double`|`float32, float64`|32비트 또는 64비트 IEEE 754 부동 소수점 숫자입니다.|  
||`enum {}`|`enum class {}`<br /><br /> 또는<br /><br /> `enum struct {}`|32비트 열거형입니다.|  
||(해당 없음)|`Platform::Guid`|`Platform` 네임스페이스의 숫자가 아닌 128비트 값(GUID)입니다.|  
||`std::time_get`|`Windows::Foundation::DateTime`|날짜/시간 구조체입니다.|  
||(해당 없음)|`Windows::Foundation::TimeSpan`|시간 범위 구조체입니다.|  
||(해당 없음)|`Platform::Object^`|참조 횟수가 계산 기본 개체는 Windows 런타임 형식 시스템의 c + + 보기입니다.|  
||`std::wstring`<br /><br /> `L"..."`|`Platform::String^`|`Platform::String^` 은 참조 횟수가 계산된 변경할 수 없는 유니코드 문자의 시퀀스(텍스트를 나타냄)입니다.|  
|포인터|개체에 대한 포인터(`*`)<br /><br /> `std::shared_ptr`|개체 핸들(`^`, "햇"으로 발음)<br /><br /> *T^ identifier*|모든 Windows 런타임 클래스는 개체 핸들 한정자를 사용 하 여 선언 됩니다. 개체의 멤버는 화살표(`->`) 클래스 멤버 액세스 연산자를 사용하여 액세스됩니다.<br /><br /> Hat 한정자 의미 "계산 참조를 자동으로 Windows 런타임 개체에 대 한 포인터". 더 정확하게 말하자면, 개체 핸들은 컴파일러가 개체의 참조 횟수를 자동으로 관리하고 참조 횟수가 0이 되면 개체를 삭제하기 위해 코드를 삽입해야 함을 선언합니다.|  
|참조|개체(`&`)에 대한 참조입니다.<br /><br /> *T* `&` *식별자*|추적 참조(`%`):<br /><br /> *T* `%` *식별자*|한정자를 참조 하는 유일한 Windows 런타임 형식 추적을 사용 하 여 선언할 수 있습니다. 개체의 멤버는 점(`.`) 클래스 멤버 액세스 연산자를 사용하여 액세스됩니다.<br /><br /> 추적 참조는 "계산 참조를 자동으로 Windows 런타임 개체 참조입니다."를 의미 합니다. 더 정확하게 말하자면, 추적 참조는 컴파일러가 개체의 참조 횟수를 자동으로 관리하고 참조 횟수가 0이 되면 개체를 삭제하기 위해 코드를 삽입해야 함을 선언합니다.|  
|동적 형식 선언|`new`|`ref new`|Windows 런타임 개체를 할당 하 고 해당 개체에 대 한 핸들을 반환 합니다.|  
|개체 수명 관리|`delete` *식별자*<br /><br /> `delete[]`  *식별자*|소멸자를 호출합니다.|수명은 참조 횟수에 따라 결정됩니다. 삭제 호출은 소멸자를 호출하지만 자체적으로 메모리를 해제하지는 않습니다.|  
|배열 선언|*T  identifier* `[]`<br /><br /> `std::array` *식별자*|`Array<` *T* `^>^` *식별자* `(` *size* `)`<br /><br /> 또는<br /><br /> `WriteOnlyArray<` *T* `^>`  *식별자* `(` *size* `)`|수정 가능하거나 쓰기 전용인 1차원 T^ 형식 배열을 선언합니다. 배열 자체도 개체 핸들 한정자를 사용하여 선언해야 하는 참조 횟수가 계산되는 개체입니다.<br /><br /> 배열 선언에서는 `Platform` 네임스페이스에 있는 템플릿 헤더 클래스를 사용합니다.|  
|클래스 선언|`class`  *식별자* `{}`<br /><br /> `struct` *식별자* `{}`|`ref class` *식별자* `{}`<br /><br /> `ref struct` *식별자* `{}`|기본 private 액세스 가능성이 있는 런타임 클래스를 선언합니다.<br /><br /> 기본 public 액세스 가능성이 있는 런타임 클래스를 선언합니다.|  
|구조체 선언|`struct` *식별자* `{}`<br /><br /> (즉, POD(Plain Old Data) 구조체)|`value class` *식별자* `{}`<br /><br /> `value struct` *식별자* `{}`|기본 private 액세스 가능성이 있는 POD 구조체를 선언합니다.<br /><br /> 값 클래스는 Windows 메타데이터로 표현될 수 있지만 표준 C++ 클래스는 Windows 메타데이터로 표현될 수 없습니다.<br /><br /> 기본 public 액세스 가능성이 있는 POD 구조체를 선언합니다.<br /><br /> 값 구조체는 Windows 메타데이터로 표현될 수 있지만 표준 C++ 구조체는 Windows 메타데이터로 표현될 수 없습니다.|  
|인터페이스 선언|순수 가상 함수만 포함하는 추상 클래스입니다.|`interface class` *식별자* `{}`<br /><br /> `interface struct` *식별자* `{}`|기본 private 액세스 가능성이 있는 인터페이스를 선언합니다.<br /><br /> 기본 public 액세스 가능성이 있는 인터페이스를 선언합니다.|  
|대리자(delegate)|`std::function`|`public delegate` *return-type* *delegate-type-identifier* `(` *[ parameters ]* `);`|함수 호출과 같이 호출할 수 있는 개체를 선언합니다.|  
|이벤트(event)|(해당 없음)|`event` *delegate-type-identifier* *event-identifier* `;`<br /><br /> *delegate-type-identifier* *delegate-identifier* = `ref new`*delegate-type-identifier*`( this`*[, parameters]*`);`<br /><br /> *event-identifier* `+=` *delegate-identifier* `;`<br /><br /> 또는<br /><br /> `EventRegistrationToken` *token-identifier* = *obj*`.`*event-identifier*`+=`*delegate-identifier*`;`<br /><br /> 또는<br /><br /> `auto` *토큰 식별자* = *obj*합니다. *이벤트 식별자*`::add(`*대리자 식별자*`);`<br /><br /> *obj* `.` *event-identifier* `-=` *token-identifier* `;`<br /><br /> 또는<br /><br /> *obj* `.` *event-identifier* `::remove(` *token-identifier* `);`|이벤트가 발생한 경우에 호출되는 이벤트 처리기(대리자) 컬렉션을 저장하는 이벤트 개체를 선언합니다.<br /><br /> 이벤트 처리기를 만듭니다.<br /><br /> 이벤트 처리기를 추가합니다.<br /><br /> 이벤트 처리기를 추가하면 이벤트 토큰(*token-identifier*)이 반환됩니다. 이벤트 처리기를 명시적으로 제거하려면 나중에 사용하도록 이벤트 토큰을 저장해야 합니다.<br /><br /> 이벤트 처리기를 제거합니다.<br /><br /> 이벤트 처리기를 제거하려면 이벤트 처리기가 추가될 때 저장한 이벤트 토큰을 지정해야 합니다.|  
|속성|(해당 없음)|`property` *T* *identifier*;<br /><br /> `property` *T* *식별자* `[` *인덱스입니다.* `];`<br /><br /> `property` *T* `default[` *인덱스입니다.* `];`|클래스 또는 개체 멤버 함수가 데이터 멤버 또는 인덱싱된 배열 요소에 액세스하는 데 사용된 같은 구문을 사용하여 액세스됨을 선언합니다.<br /><br /> 클래스 또는 개체 멤버 함수의 속성을 선언합니다.<br /><br /> 개체 멤버 함수의 인덱싱된 속성을 선언합니다.<br /><br /> 클래스 멤버 함수의 인덱싱된 속성을 선언합니다.|  
|매개 변수화된 형식|템플릿|`generic <typename` *T* `> interface class` *식별자* `{}`<br /><br /> `generic <typename` *T* `> delegate` *[return-type]* *delegate-identifier* `() {}`|매개 변수화된 인터페이스 클래스를 선언합니다.<br /><br /> 매개 변수화된 대리자를 선언합니다.|  
|Nullable 값 형식|`boost::optional<T>`|[Platform:: ibox \<T >](../cppcx/platform-ibox-interface.md)|스칼라 형식의 변수 및 값 구조체가 `nullptr`값을 가질 수 있도록 합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [Visual c + + 언어 참조](../cppcx/visual-c-language-reference-c-cx.md)