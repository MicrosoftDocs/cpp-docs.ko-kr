---
description: '자세히 알아보기: 기본적으로 해제 되어 있는 컴파일러 경고'
title: 기본적으로 해제되어 있는 컴파일러 경고
ms.date: 08/29/2019
helpviewer_keywords:
- warnings, compiler
- cl.exe compiler, setting options
ms.assetid: 69809cfb-a38a-4035-b154-283a61938df8
ms.openlocfilehash: 5bc482d12026bb8358d773be6a0c8b32cc2317fc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269382"
---
# <a name="compiler-warnings-that-are-off-by-default"></a>기본적으로 해제되어 있는 컴파일러 경고

컴파일러는 기본적으로 해제 되어 있는 경고를 지원 합니다. 대부분의 개발자는 이러한 경고를 유용 하 게 찾을 수 없기 때문입니다. 일부 경우에는 스타일 선택 이나 이전 코드의 일반적인 관용구에 대해 경고 합니다. 다른 경고는 언어에 대 한 Microsoft 확장 사용에 대 한 것입니다. 일부 경고는 프로그래머가 종종 잘못 된 가정을 만드는 영역을 나타내므로 예기치 않은 동작이 나 정의 되지 않은 동작이 발생할 수 있습니다. 이러한 경고를 모두 사용 하는 경우 일부는 라이브러리 헤더에 여러 번 나타날 수 있습니다. C 런타임 라이브러리 및 c + + 표준 라이브러리는 경고 수준 [/W4](../build/reference/compiler-option-warning-level.md)에만 경고를 표시 하지 않습니다.

## <a name="enable-warnings-that-are-off-by-default"></a>기본적으로 해제 된 경고 사용

다음 옵션 중 하나를 사용 하 여 기본적으로 발생 하는 경고를 사용 하도록 설정할 수 있습니다.

- **#pragma 경고 (기본값:** *warning_number* **)**

   지정 된 경고 (*warning_number*)는 기본 수준에서 사용 하도록 설정 됩니다. 경고 설명서에 경고의 기본 수준이 포함되어 있습니다.

- **#pragma 경고 (** *warning_level* **:** *warning_number* **)**

   지정 된 경고 (*warning_number*)는 지정 된 수준 (*warning_level*)에서 사용 하도록 설정 됩니다.

- [/Wall](../build/reference/compiler-option-warning-level.md)

   `/Wall`은 기본적으로 해제되어 있는 모든 경고가 사용되게 만듭니다. 이 옵션을 사용 하는 경우 [/wd](../build/reference/compiler-option-warning-level.md) 옵션을 사용 하 여 개별 경고를 해제할 수 있습니다.

- [/w *Lnnnn*](../build/reference/compiler-option-warning-level.md)

   이 옵션은 수준 *L* 에서 경고 *nnnn* 을 사용 하도록 설정 합니다.

## <a name="warnings-that-are-off-by-default"></a>기본적으로 해제 되어 있는 경고

다음 경고는 Visual Studio 2015 이상 버전에서 기본적으로 해제 되어 있습니다.

|경고|메시지|
|-|-|
|[C4061](../error-messages/compiler-warnings/compiler-warning-level-4-c4061.md) (수준 4)|'*enumeration*' 열거형의 switch에 있는 '*identifier*' 열거자는 case 레이블에 의해 명시적으로 처리 되지 않습니다.|
|[C4062](../error-messages/compiler-warnings/compiler-warning-level-4-c4062.md) (수준 4)|'*enumeration*' 열거형의 switch에 있는 '*identifier*' 열거자가 처리 되지 않습니다.|
| [C4165](../error-messages/compiler-warnings/compiler-warning-level-1-c4165.md) (수준 1) | ' HRESULT '가 ' bool '로 변환 되 고 있습니다. 원하는 작업을 수행 하 시겠습니까? |
| [C4191](../error-messages/compiler-warnings/compiler-warning-level-3-c4191.md) (수준 3)|'*operator*': '*type_of_expression*'에서 '*type_required*' (으)로의 변환이 안전 하지 않습니다.|
|[C4242](../error-messages/compiler-warnings/compiler-warning-level-4-c4242.md) (수준 4)|'*identifier*': '*type1*'에서 '*type2*' (으)로 변환 하 여 데이터가 손실 될 수 있습니다.|
|[C4254](../error-messages/compiler-warnings/compiler-warning-level-4-c4254.md) (수준 4)|'*operator*': '*type1*'에서 '*type2*' (으)로 변환 하 여 데이터가 손실 될 수 있습니다.|
|[C4255](../error-messages/compiler-warnings/compiler-warning-level-4-c4255.md) (수준 4)|'*function*': 함수 프로토타입이 지정 되지 않았습니다. ' () '에서 ' (void) '로 변환 합니다.|
|[C4263](../error-messages/compiler-warnings/compiler-warning-level-4-c4263.md) (수준 4)|'*function*': 멤버 함수가 기본 클래스 가상 멤버 함수를 재정의 하지 않습니다.|
|[C4264](../error-messages/compiler-warnings/compiler-warning-level-1-c4264.md) (수준 1)|'*virtual_function*': 기본 '*class*'의 가상 멤버 함수에 대해 재정의를 사용할 수 없습니다. 함수가 숨겨집니다.|
|[C4265](../error-messages/compiler-warnings/compiler-warning-level-3-c4265.md) (수준 3)|'*class*': 클래스에 가상 함수가 있지만 소멸자가 가상이 아닙니다.|
|[C4266](../error-messages/compiler-warnings/compiler-warning-level-4-c4266.md) (수준 4)|'*function*': 기본 '*type*'의 가상 멤버 함수에 대해 재정의를 사용할 수 없습니다. 함수가 숨겨집니다.|
|[C4287](../error-messages/compiler-warnings/compiler-warning-level-3-c4287.md) (수준 3)|'*operator*': 부호 없는 상수 또는 음의 상수가 일치 하지 않습니다.|
|[C4289](../error-messages/compiler-warnings/compiler-warning-level-4-c4289.md) (수준 4)|비표준 확장이 사용 됨: '*var*': for 루프에서 선언 된 루프 제어 변수가 for 루프 범위 외부에서 사용 됩니다.|
|[C4296](../error-messages/compiler-warnings/compiler-warning-level-4-c4296.md) (수준 4)|'*operator*': 식이 항상 false입니다.|
|[C4339](../error-messages/compiler-warnings/compiler-warning-level-4-c4339.md) (수준 4)|'*type*': CLR 메타 데이터에 정의 되지 않은 형식이 사용 되었습니다 .이 형식을 사용 하면 런타임 예외가 발생할 수 있습니다.|
|[C4342](../error-messages/compiler-warnings/compiler-warning-level-1-c4342.md) (수준 1)|동작 변경: '*function*'이 호출 되었지만 이전 버전에서는 멤버 연산자가 호출 되었습니다.|
|[C4350](../error-messages/compiler-warnings/compiler-warning-level-1-c4350.md) (수준 1)|동작 변경: '*member2*' 대신 '*member1*'이 호출 되었습니다.|
|[C4355](../error-messages/compiler-warnings/compiler-warning-c4355.md)|'this' : 기본 멤버 이니셜라이저 목록에서 사용되었습니다.|
|[C4365](../error-messages/compiler-warnings/compiler-warning-level-4-c4365.md) (수준 4)|'*action*': '*type_1*'에서 '*type_2*' (으)로 변환, signed/unsigned가 일치 하지 않습니다.|
|C4370 (수준 3)|압축 기능이 향상되어 이전 버전의 컴파일러에서 클래스 레이아웃이 변경되었습니다.|
|[C4371](../error-messages/compiler-warnings/c4371.md) (수준 3)|'*classname*': '*member*' 멤버를 더 잘 압축 했기 때문에 이전 버전의 컴파일러에서 클래스 레이아웃이 변경 되었을 수 있습니다.|
|C4388 (수준 4)|signed 또는 unsigned가 일치하지 않습니다.|
|[C4412](../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md) (수준 2)|'*function*': 함수 시그니처에 '*type*' 형식이 포함 되어 있습니다. C + + 개체는 순수형 코드와 mixed 또는 native 사이에서 전달 하기에 안전 하지 않습니다.|
|C4426 (수준 1)|헤더를 포함 한 후 최적화 플래그가 변경 되었습니다. #pragma optimize () <sup>14.1</sup> 때문일 수 있습니다.|
|[C4435](../error-messages/compiler-warnings/compiler-warning-level-4-c4435.md) (수준 4)|'*class1*': 가상 기본 '*class2*'로 인해/vd2 아래의 개체 레이아웃이 변경 됩니다.|
|[C4437](../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md) (수준 4)|가상 기본 '*class1*'에서 '*class2*' (으)로 dynamic_cast 일부 컨텍스트에서 실패할 수 있습니다.|
|C4444 (수준 3)|이 컨텍스트에서는 최상위 '__unaligned'가 구현되지 않았습니다.|
|[C4464](../error-messages/compiler-warnings/c4464.md) (수준 4)|상대 포함 경로에 '.. '가 포함 되어 있습니다.|
|[C4471](../error-messages/compiler-warnings/compiler-warning-level-4-c4471.md) (수준 4)|범위가 없는 열거형의 전방 선언에는 기본 형식 (int로 <sup>가정)이</sup> 있어야 합니다.|
|4472 (수준 1)|'*identifier*'는 네이티브 열거형입니다. 관리 되는 열거형을 선언 하려면 액세스 지정자 (전용/공용)를 추가 하세요.|
|[C4514](../error-messages/compiler-warnings/compiler-warning-level-4-c4514.md) (수준 4)|'*function*': 참조 되지 않은 인라인 함수를 제거 했습니다.|
|[C4536](../error-messages/compiler-warnings/compiler-warning-level-4-c4536.md) (수준 4)|' type name ': 형식-이름이 메타 데이터 한계인 '*limit*' 자를 초과 합니다.|
|[C4545](../error-messages/compiler-warnings/compiler-warning-level-1-c4545.md) (수준 1)|쉼표 앞의 식이 인수 목록이 없는 함수로 계산됩니다.|
|[C4546](../error-messages/compiler-warnings/compiler-warning-level-1-c4546.md) (수준 1)|쉼표 앞의 함수에 인수 목록이 없습니다.|
|[C4547](../error-messages/compiler-warnings/compiler-warning-level-1-c4547.md) (수준 1)|'*operator*': 쉼표 앞의 연산자는 적용 되지 않습니다. 부작용이 있는 연산자가 필요 합니다.|
|[C4548](../error-messages/compiler-warnings/compiler-warning-level-1-c4548.md) (수준 1)|쉼표 앞의 식은 의미 없는 식입니다. 파생 작업이 있는 식이어야 합니다.|
|[C4549](../error-messages/compiler-warnings/compiler-warning-level-1-c4549.md) (수준 1)|'*operator1*': 쉼표 앞의 연산자는 적용 되지 않습니다. '*operator2*' 하려고 했습니까?|
|[C4555](../error-messages/compiler-warnings/compiler-warning-level-1-c4555.md) (수준 1)|식이 효과가 없습니다. 파생 작업이 있는 식이어야 합니다.|
|[C4557](../error-messages/compiler-warnings/compiler-warning-level-3-c4557.md) (수준 3)|' __assume '에 '*효과*' 효과가 있습니다.|
|[C4571](../error-messages/compiler-warnings/compiler-warning-level-4-c4571.md) (수준 4)|알림: Visual C++ 7.1부터 catch (...) 의미 체계가 변경 되었습니다. 구조적 예외 (SEH)는 더 이상 catch 되지 않습니다.|
|C4574 (수준 4)|'*identifier*'가 ' 0 '이 되도록 정의 되어 있습니다. ' #if *identifier*'를 사용 하 시겠습니까?|
|C4577 (수준 1)|예외 처리 모드를 지정 하지 않고 ' noexcept '을 사용 했습니다. 예외에서 종료는 보장 되지 않습니다. /EHsc 지정|
|C4582 (수준 4)|'*type*': 생성자가 암시적으로 호출 되지 않습니다.|
|C4583 (수준 4)|'*type*': 소멸자가 암시적으로 호출 되지 않습니다.|
|C4587 (수준 1)|'*anonymous_structure*': 동작 변경: 생성자가 더 이상 암시적으로 호출 되지 않습니다.|
|않습니다 (수준 1)|'*anonymous_structure*': 동작 변경: 소멸자가 더 이상 암시적으로 호출 되지 않습니다.|
|[C4596](../error-messages/compiler-warnings/c4596.md) (수준 4)|'*identifier*': 멤버 선언 <sup>14.3</sup> <sup>Perm</sup> 의 정규화 된 이름이 잘못 되었습니다.|
|C4598 (수준 1 및 수준 3)|' #include "*헤더*" ': 미리 컴파일된 헤더의 헤더 번호 *헤더 번호가* <sup>14.3</sup> 위치에서 현재 컴파일과 일치 하지 않습니다.|
|C4599 (수준 3)|'*option* *path*': 명령줄 인수 번호는 미리 컴파일된 헤더 <sup>14.3</sup> 과 일치 *하지 않습니다.*|
|C4605 (수준 1)|'/D *macro*'은 (는) 현재 명령줄에서 지정 되었지만 미리 컴파일된 헤더를 빌드할 때 지정 되지 않았습니다.|
|[C4608](../error-messages/compiler-warnings/compiler-warning-level-3-c4608.md) (수준 3)|'*union_member*'은 (는) 이미 이니셜라이저 목록의 다른 공용 구조체 멤버 '*union_member*' <sup>Perm</sup> 에서 초기화 되었습니다.|
|[C4619](../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md) (수준 3)|#pragma 경고: 경고 번호 '*number*'가 없습니다.|
|[C4623](../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md) (수준 4)|'derived class': 기본 클래스의 기본 생성자에 액세스할 수 없으므로 기본 생성자를 생성할 수 없습니다.|
|[C4625](../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md) (수준 4)|'derived class': 기본 클래스의 복사 생성자에 액세스할 수 없으므로 복사 생성자를 생성할 수 없습니다.|
|[C4626](../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md) (수준 4)|'derived class': 기본 클래스의 대입 연산자에 액세스할 수 없으므로 대입 연산자를 생성할 수 없습니다.|
|[C4628](../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md) (수준 1)|-Ze에는 digraph가 지원되지 않습니다. '*D i g*' 문자 시퀀스는 '*char*'의 대체 토큰으로 해석 되지 않습니다.|
|[C4640](../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md) (수준 3)|'*instance*': 지역 정적 개체의 생성은 스레드로부터 안전 하지 않습니다.|
| C4643 (수준 4) | 네임 스페이스 std에서 '*identifier*'를 선언 하는 것은 c + + 표준에서 허용 되지 않습니다. <sup>15.8</sup> |
|C4647 (수준 3)|동작 변경: 이전 버전과 __is_pod (*형식*)의 값이 다릅니다.|
|C4654 (수준 4)|미리 컴파일된 헤더 줄의 포함 앞에 배치 된 코드는 무시 됩니다. 미리 컴파일된 헤더에 코드를 추가 합니다. <sup>14.1</sup>|
|[C4668](../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md) (수준 4)|'*symbol*'은 (는) 전처리기 매크로로 정의 되어 있지 않습니다. '*지시문*'의 경우 ' 0 '으로 바꿉니다.|
|[C4682](../error-messages/compiler-warnings/compiler-warning-level-4-c4682.md) (수준 4)|'*symbol*': 방향 매개 변수 특성이 지정 되지 않았습니다. 기본값은 [in]입니다.|
|[C4686](../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md) (수준 3)|'*사용자 정의 형식*': 동작이 변경 될 수 있습니다. UDT 반환 호출 규칙이 변경 되었습니다.|
|[C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md) (수준 1)|'*function*': 전용이 아닌 멤버의 시그니처에 어셈블리 전용 네이티브 형식 '*native_type*'이 (가) 있습니다.|
|[C4710](../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md) (수준 4)|'*function*': 함수가 인라인되지 있지 않습니다.|
|[C4738](../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md) (수준 3)|32비트 float 결과를 메모리에 저장하면 성능이 저하될 수 있습니다.|
|[C4746](../error-messages/compiler-warnings/compiler-warning-c4746.md)|'*expression*'의 volatile 액세스에는/volatile: 설정이 적용 됩니다 \<iso&#124;ms> ./store 내장 함수를 사용 __iso_volatile_load 하는 것이 좋습니다.|
|C4749 (수준 4)|조건부로 지원 됨: 비표준 레이아웃 형식 '*type*'에 적용 된 offsetof|
|C4767 (수준 4)|섹션 이름 '*symbol*'이 8 자 보다 길어 링커에서 잘립니다.|
|C 4768 (수준 3)|링크 사양 이전의 __declspec 특성은 무시 됩니다.|
|C4774 (수준 4)|'*string*': 인수 *번호* 에 필요한 형식 문자열이 문자열 리터럴이 아닙니다.|
|C4777 (수준 4)|'*function*': '*string*' 형식 문자열에는 '*type1*' 형식의 인수가 필요 하지만 variadic 인수 *번호* 는 '*type2*' 형식입니다.|
|C4786 (수준 3)|'*symbol*': 디버그 정보에서 개체 이름이 '*number*' 자로 잘렸습니다.|
| [C4800](../error-messages/compiler-warnings/compiler-warning-level-3-c4800.md) (수준 4) | '*Type*'에서 bool로의 암시적 변환입니다. 가능한 정보 손실 <sup>16.0</sup> |
|[C4820](../error-messages/compiler-warnings/compiler-warning-level-4-c4820.md) (수준 4)|'*member_name*' 구문을 생성 한 후 '*바이트*' 바이트 패딩 추가|
| [C4822](../error-messages/compiler-warnings/compiler-warning-level-1-c4822.md) (수준 1) | '*member*': 지역 클래스 멤버 함수에 본문이 없습니다. |
|C4826 (수준 2)|'*Type1*'에서 '*type2*' (으)로의 변환이 부호 확장 되었습니다. 이로 인해 예기치 않은 런타임 동작이 발생할 수 있습니다.|
|C4837 (수준 4)|검색 된 삼중 자: '?? '*character '로* 바뀐 *문자*|
|C4841 (수준 4)|비표준 확장이 사용 됨: offsetof에 사용 되는 복합 멤버 지정자|
|C4842 (수준 4)|여러 상속을 사용 하는 형식에 적용 된 ' offsetof '의 결과가 컴파일러 릴리스 간에 일치 하지 않을 수 있습니다.|
|[C4868](../error-messages/compiler-warnings/compiler-warning-c4868.md) (수준 4)|'_file_(*line_number*) ' 컴파일러는 중괄호로 묶인 초기화 목록에서 왼쪽에서 오른쪽으로 계산 순서를 적용할 수 없습니다.|
|[C4905](../error-messages/compiler-warnings/compiler-warning-level-1-c4905.md) (수준 1)|와이드 문자열 리터럴을 'LPSTR'로 캐스팅했습니다.|
|[C4906](../error-messages/compiler-warnings/compiler-warning-level-1-c4906.md) (수준 1)|문자열 리터럴을 'LPWSTR'로 캐스팅했습니다.|
|[C4917](../error-messages/compiler-warnings/compiler-warning-level-1-c4917.md) (수준 1)|'*선언 자*': GUID는 클래스, 인터페이스 또는 네임 스페이스와만 연결할 수 있습니다.|
|[C4928](../error-messages/compiler-warnings/compiler-warning-level-1-c4928.md) (수준 1)|복사 초기화가 잘못되었습니다. 사용자 정의 변환이 암시적으로 두 번 이상 적용되었습니다.|
|[C4931](../error-messages/compiler-warnings/compiler-warning-level-4-c4931.md) (수준 4)|number비트 포인터에 대한 형식 라이브러리를 빌드했다고 간주합니다.|
|[C4946](../error-messages/compiler-warnings/compiler-warning-level-1-c4946.md) (수준 1)|관련 클래스 '*class1*' 및 '*class2*' 사이에 reinterpret_cast 사용 됩니다.|
|C4962|'*function*': 최적화로 인해 프로필 데이터가 일관성이 없어지므로 프로필 기반 최적화를 사용 하지 않도록 설정 했습니다.|
|[C4986](../error-messages/compiler-warnings/compiler-warning-c4986.md) (수준 4)|'*symbol*': 예외 사양이 이전 선언과 일치 하지 않습니다.|
|C4987 (수준 4)|비표준 확장 사용: 'throw (...)'|
|C4988 (수준 4)|'*symbol*': 클래스/함수 범위 밖에 변수가 선언 되었습니다.|
|C5022|'*type*': 여러 개의 이동 생성자가 지정 되었습니다.|
|C5023|'*type*': 여러 개의 이동 할당 연산자가 지정 되었습니다.|
|C5024 (수준 4)|'*type*': 이동 생성자가 암시적으로 삭제 된 것으로 정의 되었습니다.|
|C5025 (수준 4)|'*type*': 이동 할당 연산자가 암시적으로 삭제 된 것으로 정의 되었습니다.|
|C5026 (수준 1 및 수준 4)|'*type*': 이동 생성자가 암시적으로 삭제 된 것으로 정의 되었습니다.|
|C5027 (수준 1 및 수준 4)|'*type*': 이동 할당 연산자가 암시적으로 삭제 된 것으로 정의 되었습니다.|
|C5029 (수준 4)|비표준 확장이 사용 됨: c + +의 맞춤 특성은 변수, 데이터 멤버 및 태그 형식에만 적용 됩니다.|
|C5031 (수준 4)|#pragma 경고 (pop): 다른 파일 <sup>14.1</sup> 에 푸시된 경고 상태를 표시 하지 않을 수 있습니다.|
|C5032 (수준 4)|해당 하는 #pragma 경고 (pop) <sup>14.1</sup> #pragma 경고 (push)가 발견 됨|
|에서는 "c5034|내장 '*내장* 함수를 사용 하면 함수 *함수 이름이* 게스트 코드 <sup>15.3</sup> 로 컴파일됩니다.|
|C5035|'*feature*' 기능을 사용 하면 함수 *함수 이름이* 게스트 코드 <sup>15.3</sup> 로 컴파일됩니다.|
|C5036 (수준 1)|/wks를 사용 하 여 컴파일할 때 varargs 함수 포인터 변환: x86arm64 '*type1*'에서 '*type2*' <sup>15.3</sup>|
|[C5038](../error-messages/compiler-warnings/c5038.md) (수준 4)|데이터 멤버 '*member1*'는 데이터 멤버 '*member2*' <sup>15.3</sup> 다음에 초기화 됩니다.|
|C5039 (수준 4)|'*function*': 잠재적으로 throw 되는 함수에 대 한 포인터 또는 참조는 EHc의 extern C 함수에 전달 됩니다. 이 함수가 예외를 throw 하는 경우 정의 되지 않은 동작이 발생할 수 있습니다. <sup>15.5</sup>|
|C5042 (수준 3)|'*function*': 블록 범위에 있는 함수 선언은 표준 c + +에서 ' i n i t '로 지정할 수 없습니다. ' inline ' 지정자 <sup>15.5</sup> 제거|
|[C5045](../error-messages/compiler-warnings/c5045.md)|컴파일러는/Qspectre 스위치가 지정 <sup>15.7</sup> 된 경우 메모리 로드를 위해 스펙터 완화를 삽입 합니다.|

<sup>14.1</sup> Visual Studio 2015 업데이트 1부터이 경고를 사용할 수 있습니다.
<sup>14.3</sup> 이 경고는 Visual Studio 2015 업데이트 3부터 사용할 수 있습니다.
<sup>15.3</sup> 이 경고는 Visual Studio 2017 버전 15.3부터 사용할 수 있습니다.
<sup>15.5</sup> 이 경고는 Visual Studio 2017 버전 15.5부터 사용할 수 있습니다.
<sup>15.7</sup> 이 경고는 Visual Studio 2017 버전 15.7부터 사용할 수 있습니다.
<sup>15.8</sup> 이 경고는 Visual Studio 2017 버전 15.8부터 사용할 수 있습니다.
<sup>16.0</sup> 이 경고는 Visual STUDIO 2019 RTM부터 사용할 수 있습니다.
<sup>Perm</sup> 이 경고는 [/permissive-](../build/reference/permissive-standards-conformance.md) 컴파일러 옵션이 설정 되지 않은 경우 해제 됩니다.

## <a name="warnings-off-by-default-in-earlier-versions"></a>이전 버전에서 기본적으로 발생 하는 경고

이러한 경고는 Visual Studio 2015 이전 버전의 컴파일러에서는 기본적으로 해제 되어 있습니다.

|경고|메시지|
|-|-|
|[C4302](../error-messages/compiler-warnings/compiler-warning-level-2-c4302.md) (수준 2)|'*conversion*': '*type1*'에서 '*type2*' (으)로 잘림|
|[C4311](../error-messages/compiler-warnings/compiler-warning-level-1-c4311.md) (수준 1)|'*variable*': '*type*'에서 '*type*'으로 포인터가 잘렸습니다.|
|[C4312](../error-messages/compiler-warnings/compiler-warning-level-1-c4312.md) (수준 1)|'*operation*': 더 큰 크기의 '*type1*'에서 '*type2*' (으)로의 변환입니다.|
|[C4319](../error-messages/compiler-warnings/compiler-warning-level-1-c4319.md) (수준 1)|'*operator*': '*type1*'을 더 큰 크기의 '*type2*'로 확장 하는 0입니다.|

이 경고는 Visual Studio 2012 이전 버전의 컴파일러에서 기본적으로 해제 되었습니다.

|경고|메시지|
|-|-|
|[C4431](../error-messages/compiler-warnings/compiler-warning-level-4-c4431.md) (수준 4)|형식 지정자가 없습니다. int로 가정합니다. 참고: C에서는 더 이상 기본 int를 지원하지 않습니다.|

## <a name="see-also"></a>참고 항목

[warning](../preprocessor/warning.md)
