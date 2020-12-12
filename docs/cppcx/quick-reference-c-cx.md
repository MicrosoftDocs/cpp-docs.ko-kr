---
description: '자세한 정보: 빠른 참조 (c + +/CX)'
title: 빠른 참조(C++/CX)
ms.date: 12/30/2016
ms.assetid: ba457195-26e5-43aa-b99d-24a871e550f4
ms.openlocfilehash: 74640449df21787d059509e80deb1e1e0cdaf94c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97204656"
---
# <a name="quick-reference-ccx"></a>빠른 참조(C++/CX)

Windows 런타임는 신뢰할 수 있는 운영 체제 환경 에서만 실행 되 고, 권한 있는 함수, 데이터 형식 및 장치를 사용 하며, Microsoft Store를 통해 배포 되는 UWP (유니버설 Windows 플랫폼) 앱을 지원 합니다. C + +/CX는 Windows 런타임에 대 한 앱 작성을 간소화 합니다. 이 문서는 빠른 참조입니다. 전체 설명서는 [형식 시스템](../cppcx/type-system-c-cx.md)을 참조 하세요.

명령줄에서 빌드할 때 **/Zw** 컴파일러 옵션을 사용 하 여 UWP 앱 또는 Windows 런타임 구성 요소를 빌드합니다. Windows 런타임 메타 데이터 (winmd) 파일에 정의 된 Windows 런타임 선언에 액세스 하려면 `#using` 지시문 또는 **/fu** 컴파일러 옵션을 지정 합니다. UWP 앱에 대 한 프로젝트를 만들 때 Visual Studio는 기본적으로 이러한 옵션을 설정 하 고 모든 Windows 런타임 라이브러리에 대 한 참조를 추가 합니다.

## <a name="quick-reference"></a>빠른 참조

|개념|표준 C++|C++/CX|설명|
|-------------|--------------------|------------------------------------------------------------------|-------------|
|기본 형식|C++ 기본 형식|Windows 런타임에 정의 된 기본 형식을 구현 하는 c + +/CX 기본 형식입니다.|`default`네임 스페이스에는 c + +/cx 기본 제공 기본 형식이 포함 되어 있습니다. 컴파일러는 c + +/CX 기본 형식을 표준 c + + 형식에 암시적으로 매핑합니다.<br /><br /> `Platform`네임 스페이스의 패밀리에는 기본 Windows 런타임 형식을 구현 하는 형식이 포함 되어 있습니다.|
||**`bool`**|**`bool`**|8비트 부울 값입니다.|
||**`wchar_t`**, **`char16_t`**|`char16`|유니코드(UTF-16) 코드 포인트를 나타내는 숫자가 아닌 16비트 값입니다.|
||**`short`**<br /><br /> **`unsigned short`**|`int16`<br /><br /> `uint16`|16비트 부호 있는 정수입니다.<br /><br /> 16비트 부호 없는 정수입니다.|
||**`int`**<br /><br /> **`unsigned int`**|**`int`**<br /><br /> `uint32`|32비트 부호 있는 정수입니다.<br /><br /> 32비트 부호 없는 정수입니다.|
||**`long long`** 디스크나 **`__int64`**<br /><br /> **`unsigned long long`**|`int64`<br /><br /> `uint64`|64비트 부호 있는 정수입니다.<br /><br /> 64비트 부호 없는 정수입니다.|
||**`float`**, **`double`**|`float32, float64`|32비트 또는 64비트 IEEE 754 부동 소수점 숫자입니다.|
||**`enum`**|**`enum class`**<br /><br /> 또는<br /><br /> **`enum struct`**|32비트 열거형입니다.|
||(해당 없음)|`Platform::Guid`|`Platform` 네임스페이스의 숫자가 아닌 128비트 값(GUID)입니다.|
||`std::time_get`|`Windows::Foundation::DateTime`|날짜/시간 구조체입니다.|
||(해당 없음)|`Windows::Foundation::TimeSpan`|시간 범위 구조체입니다.|
||(해당 없음)|`Platform::Object^`|Windows 런타임 형식 시스템의 c + + 뷰에서 참조 횟수가 계산 되는 기본 개체입니다.|
||`std::wstring`<br /><br /> `L"..."`|`Platform::String^`|`Platform::String^` 은 참조 횟수가 계산된 변경할 수 없는 유니코드 문자의 시퀀스(텍스트를 나타냄)입니다.|
|포인터|개체에 대한 포인터(`*`)<br /><br /> `std::shared_ptr`|개체 핸들(`^`, "햇"으로 발음)<br /><br /> *T ^ 식별자*|모든 Windows 런타임 클래스는 개체 핸들 한정자를 사용 하 여 선언 됩니다. 개체의 멤버는 화살표(`->`) 클래스 멤버 액세스 연산자를 사용하여 액세스됩니다.<br /><br /> Hat 한정자는 "자동으로 참조 횟수가 계산 되는 Windows 런타임 개체에 대 한 포인터"를 의미 합니다. 더 정확하게 말하자면, 개체 핸들은 컴파일러가 개체의 참조 횟수를 자동으로 관리하고 참조 횟수가 0이 되면 개체를 삭제하기 위해 코드를 삽입해야 함을 선언합니다.|
|참조|개체(`&`)에 대한 참조입니다.<br /><br /> *T* `&` *식별자*|추적 참조(`%`):<br /><br /> *T* `%` *식별자*|Windows 런타임 형식만 추적 참조 한정자를 사용 하 여 선언할 수 있습니다. 개체의 멤버는 점(`.`) 클래스 멤버 액세스 연산자를 사용하여 액세스됩니다.<br /><br /> 추적 참조는 "자동으로 참조 횟수가 계산 되는 Windows 런타임 개체에 대 한 참조"를 의미 합니다. 더 정확하게 말하자면, 추적 참조는 컴파일러가 개체의 참조 횟수를 자동으로 관리하고 참조 횟수가 0이 되면 개체를 삭제하기 위해 코드를 삽입해야 함을 선언합니다.|
|동적 형식 선언|`new`|`ref new`|Windows 런타임 개체를 할당 한 다음 해당 개체에 대 한 핸들을 반환 합니다.|
|개체 수명 관리|`delete`*식별자*<br /><br /> `delete[]`  *한정자*|소멸자를 호출합니다.|수명은 참조 횟수에 따라 결정됩니다. 삭제 호출은 소멸자를 호출하지만 자체적으로 메모리를 해제하지는 않습니다.|
|배열 선언|*T  identifier* `[]`<br /><br /> `std::array`*식별자*|`Array<` *T* `^>^` *식별자* `(` *size* `)`<br /><br /> 또는<br /><br /> `WriteOnlyArray<` *T* `^>`  *식별자* `(` *size* `)`|수정 가능하거나 쓰기 전용인 1차원 T^ 형식 배열을 선언합니다. 배열 자체도 개체 핸들 한정자를 사용하여 선언해야 하는 참조 횟수가 계산되는 개체입니다.<br /><br /> 배열 선언에서는 `Platform` 네임스페이스에 있는 템플릿 헤더 클래스를 사용합니다.|
|클래스 선언|**`class`***식별자*`{}`<br /><br /> **`struct`***식별자*`{}`|**`ref class`***식별자*`{}`<br /><br /> **`ref struct`***식별자*`{}`|기본 private 액세스 가능성이 있는 런타임 클래스를 선언합니다.<br /><br /> 기본 public 액세스 가능성이 있는 런타임 클래스를 선언합니다.|
|구조체 선언|**`struct`***식별자*`{}`<br /><br /> (즉, POD(Plain Old Data) 구조체)|**`value class`***식별자*`{}`<br /><br /> **`value struct`***식별자*`{}`|기본 private 액세스 가능성이 있는 POD 구조체를 선언합니다.<br /><br /> 값 클래스는 Windows 메타데이터로 표현될 수 있지만 표준 C++ 클래스는 Windows 메타데이터로 표현될 수 없습니다.<br /><br /> 기본 public 액세스 가능성이 있는 POD 구조체를 선언합니다.<br /><br /> 값 구조체는 Windows 메타데이터로 표현될 수 있지만 표준 C++ 구조체는 Windows 메타데이터로 표현될 수 없습니다.|
|인터페이스 선언|순수 가상 함수만 포함하는 추상 클래스입니다.|**`interface class`***식별자*`{}`<br /><br /> **`interface struct`***식별자*`{}`|기본 private 액세스 가능성이 있는 인터페이스를 선언합니다.<br /><br /> 기본 public 액세스 가능성이 있는 인터페이스를 선언합니다.|
|대리자|`std::function`|`public delegate` *return-type* *delegate-type-identifier* `(` *[ parameters ]* `);`|함수 호출과 같이 호출할 수 있는 개체를 선언합니다.|
|이벤트|(해당 없음)|**`event`***대리자-형식 식별자* *이벤트-식별자*`;`<br /><br /> *대리자 형식-* 식별자 대리자 *-식별자*  =  `ref new` *대리자-형식-식별자* `( this` *[, parameters]*`);`<br /><br /> *event-identifier* `+=` *delegate-identifier* `;`<br /><br /> 또는<br /><br /> `EventRegistrationToken`*토큰-식별자*  =  *obj* `.` *이벤트-식별자* `+=` *대리자-식별자*`;`<br /><br /> 또는<br /><br /> **`auto`***토큰-식별자*  =  *obj*. *이벤트-식별자* `::add(` *대리자-식별자*`);`<br /><br /> *obj* `.` *event-identifier* `-=` *token-identifier* `;`<br /><br /> 또는<br /><br /> *obj* `.` *event-identifier* `::remove(` *token-identifier* `);`|이벤트가 발생한 경우에 호출되는 이벤트 처리기(대리자) 컬렉션을 저장하는 이벤트 개체를 선언합니다.<br /><br /> 이벤트 처리기를 만듭니다.<br /><br /> 이벤트 처리기를 추가합니다.<br /><br /> 이벤트 처리기를 추가하면 이벤트 토큰(*token-identifier*)이 반환됩니다. 이벤트 처리기를 명시적으로 제거하려면 나중에 사용하도록 이벤트 토큰을 저장해야 합니다.<br /><br /> 이벤트 처리기를 제거합니다.<br /><br /> 이벤트 처리기를 제거하려면 이벤트 처리기가 추가될 때 저장한 이벤트 토큰을 지정해야 합니다.|
|속성|(해당 없음)|**`property`***T* *식별자*<br /><br /> **`property`***T* *식별자* `[` *인덱스*`];`<br /><br /> **`property`***T* `default[` *인덱스*`];`|클래스 또는 개체 멤버 함수가 데이터 멤버 또는 인덱싱된 배열 요소에 액세스하는 데 사용된 같은 구문을 사용하여 액세스됨을 선언합니다.<br /><br /> 클래스 또는 개체 멤버 함수의 속성을 선언합니다.<br /><br /> 개체 멤버 함수의 인덱싱된 속성을 선언합니다.<br /><br /> 클래스 멤버 함수의 인덱싱된 속성을 선언합니다.|
|매개 변수화된 형식|템플릿|`generic <typename` *T* `> interface class` *식별자* `{}`<br /><br /> `generic <typename` *T* `> delegate` *[return-type]* *delegate-identifier* `() {}`|매개 변수화된 인터페이스 클래스를 선언합니다.<br /><br /> 매개 변수화된 대리자를 선언합니다.|
|Nullable 값 형식|`boost::optional<T>`|[Platform:: IBox \<T>](../cppcx/platform-ibox-interface.md)|스칼라 형식 및 값 구조체의 변수가 값을 가질 수 있도록 **`nullptr`** 합니다.|

## <a name="see-also"></a>참고 항목

[C + +/CX 언어 참조](../cppcx/visual-c-language-reference-c-cx.md)
