---
description: '자세한 정보: 컴파일러 오류 C2500 ~ C2599'
title: 컴파일러 오류 C2500 ~ C2599
ms.date: 04/21/2019
f1_keywords:
- C2501
- C2508
- C2515
- C2519
- C2520
- C2522
- C2525
- C2527
- C2536
- C2538
- C2539
- C2546
- C2547
- C2559
- C2560
- C2564
- C2565
- C2576
- C2578
- C2580
- C2590
- C2591
- C2595
- C2596
helpviewer_keywords:
- C2501
- C2508
- C2515
- C2519
- C2520
- C2522
- C2525
- C2527
- C2536
- C2538
- C2539
- C2546
- C2547
- C2559
- C2560
- C2564
- C2565
- C2576
- C2578
- C2580
- C2590
- C2591
- C2595
- C2596
ms.assetid: a869aaed-e9f6-49e3-b273-00ea7f45bed7
ms.openlocfilehash: 36b0b1e0d1abbbd0b3752d275011eb12282aec18
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97238949"
---
# <a name="compiler-errors-c2500-through-c2599"></a>컴파일러 오류 C2500 ~ C2599

설명서의이 섹션에 있는 문서는 컴파일러에 의해 생성 되는 오류 메시지의 하위 집합을 설명 합니다.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>오류 메시지

|Error|메시지|
|-----------|-------------|
|[컴파일러 오류 C2500](compiler-error-C2500.md)|'*identifier1*': '*identifier2*'은 (는) 이미 직접 기본 클래스입니다.|
|컴파일러 오류 C2501|'*identifier*': ' __declspec (*지정자*) '는 구조체, 공용 구조체, 클래스 또는 부호 없는 비트 필드 멤버에만 적용할 수 있습니다.|
|[컴파일러 오류 C2502](compiler-error-C2502.md)|'*identifier*': 기본 클래스에 액세스 한정자가 너무 많습니다.|
|[컴파일러 오류 C2503](compiler-error-C2503.md)|'*class*': 기본 클래스는 크기가 0 인 배열을 포함할 수 없습니다.|
|[컴파일러 오류 C2504](compiler-error-C2504.md)|'*class*': 기본 클래스를 정의 하지 않았습니다.|
|[컴파일러 오류 C2505](compiler-error-C2505.md)|'*symbol*': ' __declspec (*지정자*) '은 (는) 전역 개체 또는 정적 데이터 멤버의 선언 또는 정의에만 적용할 수 있습니다.|
|[컴파일러 오류 C2506](compiler-error-C2506.md)|'*member*': ' __declspec (*지정자*) '은 (는)이 기호에 적용할 수 없습니다.|
|[컴파일러 오류 C2507](compiler-error-C2507.md)|'*identifier*': 기본 클래스에 가상 한정자가 너무 많습니다.|
|컴파일러 오류 C2508|'*identifier*': ' __declspec (*specifier1*) '은 (는) ' __declspec (*2*) '과 (와) 함께 사용할 수 없습니다.|
|[컴파일러 오류 C2509](compiler-error-C2509.md)|'*identifier*': 멤버 함수가 '*class*'에 선언 되지 않았습니다.|
|[컴파일러 오류 C2510](compiler-error-C2510.md)|'*identifier*': ':: ' 왼쪽은 클래스/구조체/공용 구조체 여야 합니다.|
|[컴파일러 오류 C2511](compiler-error-C2511.md)|'*identifier*': 오버 로드 된 멤버 함수를 '*class*'에서 찾을 수 없습니다.|
|[컴파일러 오류 C2512](compiler-error-C2512.md)|'*identifier*': 사용할 수 있는 적절 한 기본 생성자가 없습니다.|
|[컴파일러 오류 C2513](compiler-error-C2513.md)|' * type ': ' = ' 앞에 변수를 선언 하지 않았습니다.|
|[컴파일러 오류 C2514](compiler-error-C2514.md)|'*class*': 클래스에 생성자가 없습니다.|
|컴파일러 오류 C2515|'*identifier*': ' vtguard '는 클래스 선언 또는 정의에만 적용할 수 있습니다.|
|[컴파일러 오류 C2516](compiler-error-C2516.md)|'*class*': 올바른 기본 클래스가 아닙니다.|
|[컴파일러 오류 C2517](compiler-error-C2517.md)|'*identifier*': ':: '의 오른쪽이 정의 되지 않았습니다.|
|[컴파일러 오류 C2518](compiler-error-C2518.md)|기본 클래스 목록에 '*keyword*' 키워드가 잘못 되었습니다. 무시|
|컴파일러 오류 C2519|'*identifier*': WinRT 특성은 public 필드만 포함할 수 있습니다.|
|컴파일러 오류 C2520|'*class*': 암시적 변환에 사용할 수 있는 비 명시적 생성자가 없습니다.|
|[컴파일러 오류 C2521](compiler-error-C2521.md)|소멸자/종료자는 인수를 사용 하지 않습니다.|
|컴파일러 오류 C2522|'*identifier*': 오버 로드 식별자는 '*identifier2*'에 이미 지정 되어 있으므로 '*identifier1*'에 사용할 수 없습니다.|
|[컴파일러 오류 C2523](compiler-error-C2523.md)|'*class*:: ~*identifier*': 소멸자/종료자 태그가 일치 하지 않습니다.|
|[컴파일러 오류 C2524](compiler-error-C2524.md)|'*identifier*': 소멸자/종료자에는 ' void ' 매개 변수 목록이 있어야 합니다.|
|컴파일러 오류 C2525|'*identifier*': '*identifier1*' 매개 변수는 기본 함수에서 이름이 '*identifier2*'이 고 게시 된 구현에서 일치 해야 합니다.|
|[컴파일러 오류 C2526](compiler-error-C2526.md)|'*identifier1*': c 링크 함수는 c + + 클래스 '*identifier2*'를 반환할 수 없습니다.|
|컴파일러 오류 C2527|'*identifier*': DefaultOverload은 '*function1*' 및 '*function2*' 모두에 지정할 수 없습니다. 구현 중에 하나의 지정을 제거 하거나 함수 이름을 바꿉니다.|
|[컴파일러 오류 C2528](compiler-error-C2528.md)|'*identifier*': 참조에 대 한 포인터가 잘못 되었습니다.|
|[컴파일러 오류 C2529](compiler-error-C2529.md)|'*identifier*': 참조에 대 한 참조가 잘못 되었습니다.|
|[컴파일러 오류 C2530](compiler-error-C2530.md)|'*identifier*': 참조를 초기화 해야 합니다.|
|[컴파일러 오류 C2531](compiler-error-C2531.md)|'*identifier*': 비트 필드에 대 한 참조가 잘못 되었습니다.|
|[컴파일러 오류 C2532](compiler-error-C2532.md)|'*identifier*': 참조에 대 한 한정자가 잘못 되었습니다.|
|[컴파일러 오류 C2533](compiler-error-C2533.md)|'*identifier*': 생성자는 반환 형식을 사용할 수 없습니다.|
|[컴파일러 오류 C2534](compiler-error-C2534.md)|'*identifier*': 생성자는 값을 반환할 수 없습니다.|
|[컴파일러 오류 C2535](compiler-error-C2535.md)|'*identifier*': 멤버 함수를 이미 정의 했거나 선언 했습니다.|
|컴파일러 오류 C2536|사용되지 않습니다.|
|[컴파일러 오류 C2537](compiler-error-C2537.md)|'*지정자*': 잘못 된 링크 사양입니다.|
|컴파일러 오류 C2538|사용되지 않습니다.|
|컴파일러 오류 C2539|사용되지 않습니다.|
|[컴파일러 오류 C2540](compiler-error-C2540.md)|배열이 바인딩된 비상수 식|
|[컴파일러 오류 C2541](compiler-error-C2541.md)|'*identifier*': 포인터가 아닌 개체를 삭제할 수 없습니다.|
|[컴파일러 오류 C2542](compiler-error-C2542.md)|'*identifier*': 클래스 개체에 초기화를 위한 생성자가 없습니다.|
|[컴파일러 오류 C2543](compiler-error-C2543.md)|' [] ' 연산자에 '] '가 필요 합니다.|
|[컴파일러 오류 C2544](compiler-error-C2544.md)|' () ' 연산자에 ') '가 필요 합니다.|
|[컴파일러 오류 C2545](compiler-error-C2545.md)|'*operator*': 오버 로드 된 연산자를 찾을 수 없습니다.|
|컴파일러 오류 C2546|'*identifier*': 형식이 pia와 비 pia 둘 다에서 정의 되는 경우 pia를 먼저 참조 해야 합니다.|
|컴파일러 오류 C2547|'*identifier*': 게시 된 메서드의 모든 매개 변수는 선언에서 명시적으로 이름이 지정 되어야 합니다.|
|[컴파일러 오류 C2548](compiler-error-C2548.md)|'*function*': 매개 변수 *매개* 변수에 대 한 기본 매개 변수가 없습니다.|
|[컴파일러 오류 C2549](compiler-error-C2549.md)|사용자 정의 변환은 반환 형식을 지정할 수 없습니다.|
|[컴파일러 오류 C2550](compiler-error-C2550.md)|'*identifier*': 생성자 이니셜라이저 목록은 생성자 정의에만 사용할 수 있습니다.|
|[컴파일러 오류 C2551](compiler-error-C2551.md)|'void *' 형식의 경우 명시적 캐스트가 필요합니다.|
|[컴파일러 오류 C2552](compiler-error-C2552.md)|'*identifier*': 이니셜라이저 목록을 사용 하 여 비 집합체를 초기화할 수 없습니다.|
|[컴파일러 오류 C2553](compiler-error-C2553.md)|'*type* *derived_class*::*function*': 재정의 가상 함수 반환 형식이 '*type* *base_class*::*function*'과 (와) 다릅니다.|
|[컴파일러 오류 C2555](compiler-error-C2555.md)|'*derived_class*::*function*': 재정의 가상 함수 반환 형식이 다르고 '*base_class*::*function*'에서 공변 (covariant)이 아닙니다.|
|[컴파일러 오류 C2556](compiler-error-C2556.md)|'*type1* *class*::*function*': 오버 로드 된 함수는 '*type2* *class*::*function*'의 반환 형식만 다릅니다.|
|[컴파일러 오류 C2557](compiler-error-C2557.md)|'*identifier*': 전용 및 보호 된 멤버는 생성자 없이 초기화할 수 없습니다.|
|[컴파일러 오류 C2558](compiler-error-C2558.md)|'*class*' 클래스: 사용 가능한 복사 생성자가 없거나 복사 생성자가 ' 명시적 '으로 선언 되었습니다.|
|컴파일러 오류 C2559|'*identifier*': ref-한정자가 있는 멤버 함수를 사용 하 여 ref-한정자가 없는 멤버 함수를 오버 로드할 수 없습니다.|
|컴파일러 오류 C2560|'*identifier*': ref-한정자를 사용 하지 않는 멤버 함수를 사용 하 여 참조 한정자로 멤버 함수를 오버 로드할 수 없습니다.|
|[컴파일러 오류 C2561](compiler-error-C2561.md)|'*function*': 함수는 값을 반환 해야 합니다.|
|[컴파일러 오류 C2562](compiler-error-C2562.md)|'*function*': ' void ' 함수에서 값을 반환 합니다.|
|[컴파일러 오류 C2563](compiler-error-C2563.md)|정식 매개 변수 목록의 불일치|
|컴파일러 오류 C2564|사용되지 않습니다.|
|컴파일러 오류 C2565|'*identifier*': 참조-생성자/소멸자에 대 한 한정자가 잘못 되었습니다.|
|[컴파일러 오류 C2566](compiler-error-C2566.md)|조건식의 오버 로드 된 함수|
|[컴파일러 오류 C2567](compiler-error-C2567.md)|'*filename*'에서 메타 데이터를 열 수 없습니다. *possible_reason*|
|[컴파일러 오류 C2568](compiler-error-C2568.md)|'*identifier*': 함수 오버 로드를 확인할 수 없습니다.|
|[컴파일러 오류 C2569](compiler-error-C2569.md)|'*identifier*': 열거형/공용 구조체를 기본 클래스로 사용할 수 없습니다.|
|[컴파일러 오류 C2570](compiler-error-C2570.md)|'*identifier*': 공용 구조체에 기본 클래스를 사용할 수 없습니다.|
|[컴파일러 오류 C2571](compiler-error-C2571.md)|'*identifier*': 가상 함수는 '*union*' 공용 구조체에 있을 수 없습니다.|
|[컴파일러 오류 C2572](compiler-error-C2572.md)|'*function*': 기본 인수 재정의: 매개 변수 *번호*|
|[컴파일러 오류 C2573](compiler-error-C2573.md)|'*class*':이 형식의 개체에 대 한 포인터를 삭제할 수 없습니다. 클래스에 ' operator delete '에 대 한 비 배치 오버 로드가 없습니다. :D e)를 사용 하거나 클래스에 ' operator delete (void *) '를 추가 합니다.|
|[컴파일러 오류 C2574](compiler-error-C2574.md)|'*소멸자*': static으로 선언할 수 없습니다.|
|[컴파일러 오류 C2575](compiler-error-C2575.md)|'*identifier*': 멤버 함수와 기본만 virtual 일 수 있습니다.|
|컴파일러 오류 C2576|'*identifier*': 새 가상 메서드를 ' public '으로 도입할 수 없습니다. 메서드를 비가상으로 설정 하거나 액세스 가능성을 ' internal ' 또는 ' protected private '로 변경 하십시오.|
|[컴파일러 오류 C2577](compiler-error-C2577.md)|'*identifier*': 소멸자/종료자에는 반환 형식을 사용할 수 없습니다.|
|컴파일러 오류 C2578|'*class*': 형식에는 ' protected ' 또는 ' protected public ' 생성자를 사용할 수 없습니다.|
|[컴파일러 오류 C2579](compiler-error-C2579.md)|유형 *유형* (*오프셋*)을 확인할 수 없습니다. *파일 이름* 에 필요 합니다.|
|컴파일러 오류 C2580|'*identifier*': 여러 버전의 기본값으로 설정 된 특수 멤버 함수를 사용할 수 없습니다.|
|[컴파일러 오류 C2581](compiler-error-C2581.md)|'*type*': static ' operator = ' 함수가 잘못 되었습니다.|
|[컴파일러 오류 C2582](compiler-error-C2582.md)|' operator *operator*' 함수는 '*type*'에서 사용할 수 없습니다.|
|[컴파일러 오류 C2583](compiler-error-C2583.md)|'*identifier*': ' const/volatile ' ' this ' 포인터는 생성자/소멸자에 사용할 수 없습니다.|
|[컴파일러 오류 C2584](compiler-error-C2584.md)|'*class*': 직접 기본 '*base_class2*'에 액세스할 수 없습니다. 이미 '*base_class1*'의 기본입니다.|
|[컴파일러 오류 C2585](compiler-error-C2585.md)|*' t r u* e '로의 명시적 변환이 모호 합니다.|
|[컴파일러 오류 C2586](compiler-error-C2586.md)|사용자 정의 변환 구문이 잘못 되었습니다. 간접 참조가 잘못 되었습니다.|
|[컴파일러 오류 C2587](compiler-error-C2587.md)|'*identifier*': 지역 변수를 기본 매개 변수로 잘못 사용 했습니다.|
|[컴파일러 오류 C2588](compiler-error-C2588.md)|':: ~*identifier*': 전역 소멸자/종결자가 잘못 되었습니다.|
|[컴파일러 오류 C2589](compiler-error-C2589.md)|'*identifier*': ':: ' 오른쪽에 잘못 된 토큰이 있습니다.|
|컴파일러 오류 C2590|'*identifier*': 생성자에만 기본/멤버 이니셜라이저 목록을 사용할 수 있습니다.|
|컴파일러 오류 C2591|ExclusiveTo는 '*type*'을 인수로 사용할 수 없습니다. ' Ref 클래스 '만 유효한 인수입니다.|
|[컴파일러 오류 C2592](compiler-error-C2592.md)|'*class*': '*base_class2*'은 (는) '*base_class1*'에서 상속 되며 다시 지정할 수 없습니다.|
|[컴파일러 오류 C2593](compiler-error-C2593.md)|' operator *identifier*'가 모호 합니다.|
|[컴파일러 오류 C2594](compiler-error-C2594.md)|'*operator*': '*type1*'에서 '*type2*' (으)로의 변환이 모호 합니다.|
|컴파일러 오류 C2595|'*identifier*' WinRT 특성 형식은 sealed 여야 합니다.|
|컴파일러 오류 C2596|'*identifier*' WinRT 특성 필드는 ' public enum class ', ' int ', ' unsigned int ', ' bool ', ' Platform:: Type ', ' Platform:: String ' 또는 ' Windows:: Foundation:: HResult ' 일 수만 있습니다.|
|[컴파일러 오류 C2597](compiler-error-C2597.md)|비정적 멤버 '*identifier*'에 대 한 참조가 잘못 되었습니다.|
|[컴파일러 오류 C2598](compiler-error-C2598.md)|링크 사양은 전역 범위에 있어야 합니다.|
|[컴파일러 오류 C2599](compiler-error-C2599.md)|'*identifier*': 관리 되는/WinRT 열거형의 전방 선언을 사용할 수 없습니다.|

## <a name="see-also"></a>참고 항목

[C/c + + 컴파일러 및 빌드 도구 오류 및 경고](../compiler-errors-1/c-cpp-build-errors.md) \
[컴파일러 오류 C2000 ~ C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
