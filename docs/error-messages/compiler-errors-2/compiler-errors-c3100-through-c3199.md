---
description: '자세한 정보: 컴파일러 오류 C3100 ~ C3199'
title: 컴파일러 오류 C3100 ~ C3199
ms.date: 04/21/2019
f1_keywords:
- C3102
- C3105
- C3107
- C3108
- C3109
- C3111
- C3112
- C3119
- C3122
- C3123
- C3124
- C3125
- C3127
- C3128
- C3129
- C3143
- C3144
- C3146
- C3147
- C3148
- C3151
- C3158
- C3164
- C3165
- C3169
- C3177
- C3178
- C3184
- C3188
- C3191
- C3193
helpviewer_keywords:
- C3102
- C3105
- C3107
- C3108
- C3109
- C3111
- C3112
- C3119
- C3122
- C3123
- C3124
- C3125
- C3127
- C3128
- C3129
- C3143
- C3144
- C3146
- C3147
- C3148
- C3151
- C3158
- C3164
- C3165
- C3169
- C3177
- C3178
- C3184
- C3188
- C3191
- C3193
ms.assetid: 7bc40c2f-6a8d-488a-b665-f39375afee77
ms.openlocfilehash: d2398fa8ae783a34662efc361730a5054a982458
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97238715"
---
# <a name="compiler-errors-c3100-through-c3199"></a>컴파일러 오류 C3100 ~ C3199

설명서의이 섹션에 있는 문서는 컴파일러에 의해 생성 되는 오류 메시지의 하위 집합을 설명 합니다.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>오류 메시지

|Error|메시지|
|-----------|-------------|
|[컴파일러 오류 C3100](compiler-error-c3100.md)|'*identifier*': 알 수 없는 특성 한정자입니다.|
|[컴파일러 오류 C3101](compiler-error-c3101.md)|명명 된 특성 인수 '*identifier*'의 식이 잘못 되었습니다.|
|컴파일러 오류 C3102|사용되지 않습니다.|
|[컴파일러 오류 C3103](compiler-error-c3103.md)|'*identifier*': 명명 된 인수가 반복 되었습니다.|
|[컴파일러 오류 C3104](compiler-error-c3104.md)|특성 인수가 잘못 되었습니다.|
|컴파일러 오류 C3105|'*symbol*': 특성으로 사용할 수 없습니다.|
|[컴파일러 오류 C3106](compiler-error-c3106.md)|'*attribute*': 명명 되지 않은 인수는 명명 된 인수 앞에와 야 합니다.|
|컴파일러 오류 C3107|'*attribute*': 네이티브 특성의 멤버 함수를 정의할 수 없습니다.|
|컴파일러 오류 C3108|이니셜라이저 목록이 식이 아니므로 형식을 추론할 수 없습니다.|
|컴파일러 오류 C3109|'*identifier*': 인터페이스 메서드는 ' __stdcall ' 또는 ' __cdecl ' 호출 규칙을 사용 해야 합니다.|
|[컴파일러 오류 C3110](compiler-error-c3110.md)|'*function*': COM 인터페이스 메서드를 오버 로드할 수 없습니다.|
|컴파일러 오류 C3111|이니셜라이저 목록은 템플릿 매개 변수의 기본 인수로 사용할 수 없습니다.|
|컴파일러 오류 C3112|'*interface*': 전역 또는 네임 스페이스 범위 에서만 인터페이스를 선언할 수 있습니다.|
|[컴파일러 오류 C3113](compiler-error-c3113.md)|' interface/enum '은 template/generic 일 수 없습니다.|
|[컴파일러 오류 C3114](compiler-error-c3114.md)|'*identifier*': 명명 된 특성 인수가 잘못 되었습니다.|
|[컴파일러 오류 C3115](compiler-error-c3115.md)|'*attribute*':이 특성은 '*생성*'에 사용할 수 없습니다.|
|[컴파일러 오류 C3116](compiler-error-c3116.md)|'*지정자*': 인터페이스 메서드에 대 한 저장소 클래스가 잘못 되었습니다.|
|[컴파일러 오류 C3117](compiler-error-c3117.md)|'*interface*': 인터페이스에 기본 클래스를 하나만 사용할 수 있습니다.|
|[컴파일러 오류 C3118](compiler-error-c3118.md)|'*interface*': 인터페이스가 가상 상속을 지원 하지 않습니다.|
|컴파일러 오류 C3119|alignas (void)는 허용 되지 않습니다.|
|[컴파일러 오류 C3120](compiler-error-c3120.md)|'*identifier*': 인터페이스 메서드는 가변 인수 목록을 사용할 수 없습니다.|
|[컴파일러 오류 C3121](compiler-error-c3121.md)|'*class*' 클래스의 GUID를 변경할 수 없습니다.|
|컴파일러 오류 C3122|'*interface*': WinRT 제네릭 인터페이스에는 GUID를 사용할 수 없습니다.|
|컴파일러 오류 C3123|WinRT 제네릭 인터페이스에는 제약 조건이 있을 수 없습니다.|
|컴파일러 오류 C3124|' signed char '은 올바른 WinRT 데이터 형식이 아닙니다. 대신 ' unsigned char ', ' wchar_t ' 또는 ' signed short '를 사용 하세요.|
|컴파일러 오류 C3125|'*type*': 형식은 ' Platform:: Exception '에서 직접 또는 간접적으로 파생 될 수 없습니다.|
|[컴파일러 오류 C3126](compiler-error-c3126.md)|'*type*' 관리 되는/WinRT 형식 내에서 '*union*' 공용 구조체를 정의할 수 없습니다.|
|컴파일러 오류 C3127|'*type*': '*성분*' 특성은 WinRT ref 클래스에만 사용할 수 있습니다.|
|컴파일러 오류 C3128|' t r u *e '에*' t r u *e '에* 의해 정의 된 vtable이 없습니다.|
|컴파일러 오류 C3129|'*type*': __default_vptr_for_base은 로컬로 정의 된 다형성 형식 및 기본에만 사용할 수 있습니다.|
|[컴파일러 오류 C3130](compiler-error-c3130.md)|내부 컴파일러 오류: 삽입 된 코드 블록을 PDB에 쓰지 못했습니다.|
|[컴파일러 오류 C3131](compiler-error-c3131.md)|프로젝트에는 ' name ' 속성이 있는 ' module ' 특성이 있어야 합니다.|
|[컴파일러 오류 C3132](compiler-error-c3132.md)|'*parameter*': 매개 변수 배열은 ' 싱글 차원 관리/WinRT 배열 ' 형식의 형식 인수에만 적용할 수 있습니다.|
|[컴파일러 오류 C3133](compiler-error-c3133.md)|C + + varargs에 특성을 적용할 수 없습니다.|
|[컴파일러 오류 C3134](compiler-error-c3134.md)|'*value*': 특성 인수 '*argument*'의 값은 '*type*' 형식이 잘못 되었습니다.|
|[컴파일러 오류 C3135](compiler-error-c3135.md)|'*identifier*': 속성에는 ' const ' 또는 ' volatile ' 형식을 사용할 수 없습니다.|
|[컴파일러 오류 C3136](compiler-error-c3136.md)|'*interface*': com 인터페이스는 다른 com 인터페이스 에서만 상속할 수 있습니다. '*INTERFACE*'는 com 인터페이스가 아닙니다.|
|[컴파일러 오류 C3137](compiler-error-c3137.md)|'*identifier*': 속성을 초기화할 수 없습니다.|
|[컴파일러 오류 C3138](compiler-error-c3138.md)|'*identifier*': '*attribute*' 인터페이스는 IDispatch에서 상속 하거나 idispatch에서 상속 하는 인터페이스에서 상속 해야 합니다.|
|[컴파일러 오류 C3139](compiler-error-c3139.md)|'*type*': 멤버 없이 UDT를 내보낼 수 없습니다.|
|[컴파일러 오류 C3140](compiler-error-c3140.md)|같은 컴파일 단위에 여러 개의 ' module ' 특성을 사용할 수 없습니다.|
|[컴파일러 오류 C3141](compiler-error-c3141.md)|'*interface*': 인터페이스는 공용 상속만 지원 합니다.|
|[컴파일러 오류 C3142](compiler-error-c3142.md)|'*property*': 속성의 주소를 가져올 수 없습니다.|
|컴파일러 오류 C3143|'*argument*': 특성 인수에는 여러 값을 사용할 수 없습니다.|
|컴파일러 오류 C3144|'*attribute*': 특성에는 명시적 인수가 필요 합니다. '*argument*'는 이름이 없습니다.|
|[컴파일러 오류 C3145](compiler-error-c3145.md)|'*identifier*': 전역 또는 정적 변수에는 '*type*' 형식을 사용할 수 없습니다.|
|컴파일러 오류 C3146|사용되지 않습니다.|
|컴파일러 오류 C3147|사용되지 않습니다.|
|컴파일러 오류 C3148|사용되지 않습니다.|
|[컴파일러 오류 C3149](compiler-error-c3149.md)|'*type*': 최상위 '*token*' 없이 여기에이 형식을 사용할 수 없습니다.|
|[컴파일러 오류 C3150](compiler-error-c3150.md)|'*구문*': '*attribute*'는 클래스, 구조체, 인터페이스, 배열 또는 포인터에만 적용할 수 있습니다.|
|컴파일러 오류 C3151|사용되지 않습니다.|
|[컴파일러 오류 C3152](compiler-error-c3152.md)|'*function*': '*keyword*'는 클래스, 구조체 또는 가상 멤버 함수에만 적용할 수 있습니다.|
|[컴파일러 오류 C3153](compiler-error-c3153.md)|'*interface*': 인터페이스의 인스턴스를 만들 수 없습니다.|
|[컴파일러 오류 C3154](compiler-error-c3154.md)|줄임표 앞에 ', '가 필요 합니다. 매개 변수 배열 함수에서는 쉼표가 아닌 구분 된 줄임표가 지원 되지 않습니다.|
|[컴파일러 오류 C3155](compiler-error-c3155.md)|속성 인덱서에는 특성을 사용할 수 없습니다.|
|[컴파일러 오류 C3156](compiler-error-c3156.md)|'*class*': 관리 되는/WinRT 형식의 지역 정의를 사용할 수 없습니다.|
|[컴파일러 오류 C3157](compiler-error-c3157.md)|ParamArray 특성은 마지막 매개 변수에만 적용할 수 있습니다.|
|컴파일러 오류 C3158|'*function*': '*keyword*'는 가상 멤버 함수에만 적용할 수 있습니다.|
|[컴파일러 오류 C3159](compiler-error-c3159.md)|'*identifier*': 값 형식에 대 한 포인터 배열을 선언할 수 없습니다.|
|[컴파일러 오류 C3160](compiler-error-c3160.md)|'*type*': 관리 되는/WinRT 클래스의 데이터 멤버는이 형식을 가질 수 없습니다.|
|[컴파일러 오류 C3161](compiler-error-c3161.md)|'*interface*': 인터페이스에 클래스, 구조체 또는 인터페이스를 중첩할 수 없습니다. 클래스 또는 구조체의 중첩 인터페이스가 잘못 되었습니다.|
|[컴파일러 오류 C3162](compiler-error-c3162.md)|'*type*': 소멸자가 있는 참조 형식은 정적 데이터 멤버 '*member*'의 형식으로 사용할 수 없습니다.|
|[컴파일러 오류 C3163](compiler-error-c3163.md)|'*class*': 특성이 이전 선언과 일치 하지 않습니다.|
|컴파일러 오류 C3164|사용되지 않습니다.|
|컴파일러 오류 C3165|'*value*': 정수 계열 또는 부동 소수점 값으로 변환할 수 없습니다.|
|[컴파일러 오류 C3166](compiler-error-c3166.md)|사용되지 않습니다. '*type*': 관리 되는/WinRT 클래스의 데이터 멤버는 '*pointer_type* 내부 *managed_pointer_type*' 형식일 수 없습니다.|
|[컴파일러 오류 C3167](compiler-error-c3167.md)|.NET Framework를 초기화할 수 없습니다. 설치 되어 있는지 확인 하십시오.|
|[컴파일러 오류 C3168](compiler-error-c3168.md)|'*type*': 열거형의 내부 형식이 잘못 되었습니다.|
|컴파일러 오류 C3169|'*type*': '*type*'에서 ' auto '의 형식을 추론할 수 없습니다.|
|[컴파일러 오류 C3170](compiler-error-c3170.md)|프로젝트에 다른 모듈 식별자를 사용할 수 없습니다.|
|[컴파일러 오류 C3171](compiler-error-c3171.md)|'*module*': 프로젝트에 다른 모듈 특성을 지정할 수 없습니다.|
|[컴파일러 오류 C3172](compiler-error-c3172.md)|'*identifier*': 프로젝트에 다른 idl_module 특성을 지정할 수 없습니다.|
|[컴파일러 오류 C3173](compiler-error-c3173.md)|idl 병합에서 버전이 일치 하지 않습니다.|
|[컴파일러 오류 C3174](compiler-error-c3174.md)|모듈 특성을 지정 하지 않았습니다.|
|[컴파일러 오류 C3175](compiler-error-c3175.md)|'*function*': 관리 되는 형식의 메서드를 관리 되지 않는 함수 '*function*'에서 호출할 수 없습니다.|
|[컴파일러 오류 C3176](compiler-error-c3176.md)|'*type*': 지역 값 형식을 선언할 수 없습니다.|
|컴파일러 오류 C3177|*' t r u* e '가 포함 된 형식에 변환 함수를 사용할 수 없습니다.|
|컴파일러 오류 C3178|'*type*': 기본 인수가 있는 함수에는 ParamArray를 사용할 수 없습니다.|
|[컴파일러 오류 C3179](compiler-error-c3179.md)|명명 되지 않은 관리/WinRT 형식은 사용할 수 없습니다.|
|[컴파일러 오류 C3180](compiler-error-c3180.md)|'*type*': 이름이 메타 데이터 한계인 '*number*' 자를 초과 합니다.|
|[컴파일러 오류 C3181](compiler-error-c3181.md)|'*type*': *연산자* 에 대 한 피연산자가 잘못 되었습니다.|
|[컴파일러 오류 C3182](compiler-error-c3182.md)|'*type*': 관리 되는/WinRT 형식 내에서 using 선언 또는 액세스 선언 멤버를 사용할 수 없습니다.|
|[컴파일러 오류 C3183](compiler-error-c3183.md)|관리 되는/WinRT 형식 '*class*' 내부에 명명 되지 않은 클래스, 구조체 또는 공용 구조체를 정의할 수 없습니다.|
|컴파일러 오류 C3184|사용되지 않습니다.|
|[컴파일러 오류 C3185](compiler-error-c3185.md)|' typeid ': 관리 되는/WinRT 형식 '*t y p e '에* 사용 되었습니다. 대신 '*operator*'를 사용 하십시오.|
|컴파일러 오류 C3186|사용되지 않습니다.|
|[컴파일러 오류 C3187](compiler-error-c3187.md)|'*identifier*': 함수 본문 내 에서만 사용할 수 있습니다.|
|컴파일러 오류 C3188|사용되지 않습니다.|
|[컴파일러 오류 C3189](compiler-error-c3189.md)|' typeid<*선언 자*> ':이 구문은 더 이상 지원 되지 않습니다. 대신:: typeid를 사용 하십시오.|
|[컴파일러 오류 C3190](compiler-error-c3190.md)|제공 된 템플릿 인수를 가진 '*선언 자*'는 '*t r u e ' 인* 멤버 함수의 명시적 인스턴스화가 아닙니다.|
|컴파일러 오류 C3191|사용되지 않습니다.|
|[컴파일러 오류 C3192](compiler-error-c3192.md)|구문 오류: ' ^ '은 (는) 전위 연산자가 아닙니다 (' * '를 의미 함).|
|컴파일러 오류 C3193|'*구문*': '/clr ' 또는 '/zw ' 명령줄 옵션이 필요 합니다.|
|[컴파일러 오류 C3194](compiler-error-c3194.md)|'*type*': 값 형식에는 할당 연산자를 사용할 수 없습니다.|
|[컴파일러 오류 C3195](compiler-error-c3195.md)|'*keyword*': 예약 되어 있으며 ref 클래스 또는 값 형식의 멤버로 사용할 수 없습니다. CLR/WinRT 연산자는 ' operator ' 키워드를 사용 하 여 정의 해야 합니다.|
|[컴파일러 오류 C3196](compiler-error-c3196.md)|'*identifier*': 두 번 이상 사용 되었습니다.|
|[컴파일러 오류 C3197](compiler-error-c3197.md)|'*keyword*': 정의 에서만 사용할 수 있습니다.|
|[컴파일러 오류 C3198](compiler-error-c3198.md)|부동 소수점 pragma를 잘못 사용 했습니다. fenv_access pragma는 정확한 모드 에서만 작동 합니다.|
|[컴파일러 오류 C3199](compiler-error-c3199.md)|부동 소수점 pragma를 잘못 사용 했습니다. 비 precise 모드에서는 예외가 지원 되지 않습니다.|

## <a name="see-also"></a>참고 항목

[C/c + + 컴파일러 및 빌드 도구 오류 및 경고](../compiler-errors-1/c-cpp-build-errors.md) \
[컴파일러 오류 C2000 ~ C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
