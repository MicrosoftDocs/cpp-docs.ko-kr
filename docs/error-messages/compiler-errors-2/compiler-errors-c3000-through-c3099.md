---
description: '자세한 정보: 컴파일러 오류 C3000 ~ C3099'
title: 컴파일러 오류 C3000 ~ C3099
ms.date: 04/21/2019
f1_keywords:
- C3051
- C3061
- C3064
- C3067
- C3074
- C3078
- C3079
- C3081
- C3082
- C3086
- C3088
- C3089
- C3090
- C3091
- C3092
- C3093
- C3098
helpviewer_keywords:
- C3051
- C3061
- C3064
- C3067
- C3074
- C3078
- C3079
- C3081
- C3082
- C3086
- C3088
- C3089
- C3090
- C3091
- C3092
- C3093
- C3098
ms.assetid: 01b7b9cb-b351-4b5a-8cb0-1fcddb08d2ab
ms.openlocfilehash: ce4e088a1d69da20cae87fd9b824ddef4769c8da
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97238702"
---
# <a name="compiler-errors-c3000-through-c3099"></a>컴파일러 오류 C3000 ~ C3099

설명서의이 섹션에 있는 문서는 컴파일러에 의해 생성 되는 오류 메시지의 하위 집합을 설명 합니다.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>오류 메시지

|Error|메시지|
|-----------|-------------|
|컴파일러 오류 C3000|사용되지 않습니다.|
|[컴파일러 오류 C3001](compiler-error-c3001.md)|'*message*': OpenMP 지시문 이름이 필요 합니다.|
|[컴파일러 오류 C3002](compiler-error-c3002.md)|'*name1* *Name2*': OpenMP 지시문 이름이 여러 개 있습니다.|
|[컴파일러 오류 C3003](compiler-error-c3003.md)|'*지시어*': 지시문 절 다음에는 OpenMP 지시문 이름이 올 수 없습니다.|
|[컴파일러 오류 C3004](compiler-error-c3004.md)|'*clause*': OpenMP '*지시어*' 지시문에는 절을 사용할 수 없습니다.|
|[컴파일러 오류 C3005](compiler-error-c3005.md)|'*message*': OpenMP '*지시어*' 지시문에 예기치 않은 토큰이 있습니다.|
|[컴파일러 오류 C3006](compiler-error-c3006.md)|'*clause*': OpenMP '*지시어*' 지시문의 절에 필요한 인수가 없습니다.|
|[컴파일러 오류 C3007](compiler-error-c3007.md)|'*clause*': OpenMP '*지시문*' 지시문의 절이 인수를 사용 하지 않습니다.|
|[컴파일러 오류 C3008](compiler-error-c3008.md)|'*argument*': OpenMP '*지시문*' 지시문에서 인수에 닫는 ') '가 없습니다.|
|[컴파일러 오류 C3009](compiler-error-c3009.md)|'*label*': OpenMP 구조화 된 블록으로 점프할 수 없습니다.|
|[컴파일러 오류 C3010](compiler-error-c3010.md)|'*label*': OpenMP 구조화 된 블록 밖으로 점프할 수 없습니다.|
|[컴파일러 오류 C3011](compiler-error-c3011.md)|병렬 영역 내부에서는 직접 인라인 어셈블리를 사용할 수 없습니다.|
|[컴파일러 오류 C3012](compiler-error-c3012.md)|'*function*': 병렬 영역 내부에서는 직접 내장 함수를 사용할 수 없습니다.|
|[컴파일러 오류 C3013](compiler-error-c3013.md)|'*clause*': OpenMP '*지시어*' 지시문에는 절이 한 번만 표시 될 수 있습니다.|
|[컴파일러 오류 C3014](compiler-error-c3014.md)|OpenMP '*지시어*' 지시문 다음에 for 루프가와 야 합니다.|
|[컴파일러 오류 C3015](compiler-error-c3015.md)|OpenMP 'for' 문의 초기화 형식이 잘못되었습니다.|
|[컴파일러 오류 C3016](compiler-error-c3016.md)|'*identifier*': OpenMP ' for ' 문의 인덱스 변수는 부호 있는 정수 계열 형식 이어야 합니다.|
|[컴파일러 오류 C3017](compiler-error-c3017.md)|OpenMP 'for' 문의 종료 테스트 형식이 잘못되었습니다.|
|[컴파일러 오류 C3018](compiler-error-c3018.md)|'*identifier*': OpenMP ' for ' 테스트 또는 증가값은 '*variable*' 인덱스 변수를 사용 해야 합니다.|
|[컴파일러 오류 C3019](compiler-error-c3019.md)|OpenMP ' for ' 문의 증가값 형식이 잘못 되었습니다.|
|[컴파일러 오류 C3020](compiler-error-c3020.md)|'*variable*': OpenMP ' for ' 루프의 인덱스 변수는 루프 본문에서 수정할 수 없습니다.|
|[컴파일러 오류 C3021](compiler-error-c3021.md)|'*argument*': OpenMP '*지시어*' 지시문에서 인수가 비어 있습니다.|
|[컴파일러 오류 C3022](compiler-error-c3022.md)|'*지시어*': OpenMP '*지시어*' 지시문에서 '*지시어*'의 예약 종류가 잘못 되었습니다.|
|[컴파일러 오류 C3023](compiler-error-c3023.md)|'*argument*': OpenMP '*지시어*' 절에 대 한 인수에 예기치 않은 토큰이 있습니다.|
|[컴파일러 오류 C3024](compiler-error-c3024.md)|' schedule (runtime) ': chunk_size 식은 사용할 수 없습니다.|
|[컴파일러 오류 C3025](compiler-error-c3025.md)|'*clause*': 정수 계열 식이 필요 합니다.|
|[컴파일러 오류 C3026](compiler-error-c3026.md)|'*clause*': 상수 식이 양수 여야 합니다.|
|[컴파일러 오류 C3027](compiler-error-c3027.md)|'*clause*': 산술 식 또는 포인터 식이 필요 합니다.|
|[컴파일러 오류 C3028](compiler-error-c3028.md)|'*member*': 데이터 공유 절에는 변수 또는 정적 데이터 멤버만 사용할 수 있습니다.|
|[컴파일러 오류 C3029](compiler-error-c3029.md)|'*symbol*': OpenMP 지시문의 데이터 공유 절에 한 번만 나타날 수 있습니다.|
|[컴파일러 오류 C3030](compiler-error-c3030.md)|'*identifier*': '*지시어*' 절/지시문의 변수는 참조 형식이 될 수 없습니다.|
|[컴파일러 오류 C3031](compiler-error-c3031.md)|'*identifier*': ' reduction ' 절의 변수는 스칼라 산술 형식 이어야 합니다.|
|[컴파일러 오류 C3032](compiler-error-c3032.md)|'*identifier*': '*clause*' 절의 변수는 불완전 한 '*type*' 형식일 수 없습니다.|
|[컴파일러 오류 C3033](compiler-error-c3033.md)|'*identifier*': '*clause*' 절의 변수는 const 한정 형식이 될 수 없습니다.|
|[컴파일러 오류 C3034](compiler-error-c3034.md)|OpenMP '*지시어*' 지시문은 '*지시어*' 지시문 내부에 직접 중첩 될 수 없습니다.|
|[컴파일러 오류 C3035](compiler-error-c3035.md)|OpenMP 'ordered' 지시문은 'ordered' 절이 있는 'for' 또는 'parallel for' 지시문에 직접 바인딩되어야 합니다.|
|[컴파일러 오류 C3036](compiler-error-c3036.md)|'*clause*': OpenMP ' reduction ' 절에 잘못 된 연산자 토큰이 있습니다.|
|[컴파일러 오류 C3037](compiler-error-c3037.md)|'*identifier*': '*clause*' 절의 변수는 바깥쪽 컨텍스트에서 shared 여야 합니다.|
|[컴파일러 오류 C3038](compiler-error-c3038.md)|'*identifier*': ' private ' 절의 변수는 바깥쪽 컨텍스트에서 환산 (reduction) 변수가 될 수 없습니다.|
|[컴파일러 오류 C3039](compiler-error-c3039.md)|'*identifier*': OpenMP ' for ' 문의 인덱스 변수는 환산 (reduction) 변수일 수 없습니다.|
|[컴파일러 오류 C3040](compiler-error-c3040.md)|'*identifier*': ' reduction ' 절의 변수 형식이 '*operator*' 환산 연산자와 호환 되지 않습니다.|
|[컴파일러 오류 C3041](compiler-error-c3041.md)|'*identifier*': ' copyprivate ' 절의 변수는 바깥쪽 컨텍스트에서 private 이어야 합니다.|
|[컴파일러 오류 C3042](compiler-error-c3042.md)|OpenMP '*지시어*' 지시문에는 ' copyprivate ' 및 ' nowait ' 절을 함께 사용할 수 없습니다.|
|[컴파일러 오류 C3043](compiler-error-c3043.md)|OpenMP 'critical' 지시문은 같은 이름의 'critical' 지시문 내부에 중첩될 수 없습니다.|
|[컴파일러 오류 C3044](compiler-error-c3044.md)|' section ': OpenMP ' sections ' 지시문에 직접 중첩 될 수 있습니다.|
|[컴파일러 오류 C3045](compiler-error-c3045.md)|OpenMP 'sections' 지시문 다음에는 복합 문이 와야 합니다. '{'가 없습니다.|
|[컴파일러 오류 C3046](compiler-error-c3046.md)|OpenMP '#pragma omp sections' 영역에 구조화된 블록이 없습니다.|
|[컴파일러 오류 C3047](compiler-error-c3047.md)|OpenMP 'sections' 영역의 구조화된 블록 앞에는 '#pragma omp section'이 있어야 합니다.|
|[컴파일러 오류 C3048](compiler-error-c3048.md)|'#pragma omp atomic' 다음에 나오는 식의 형식이 잘못되었습니다.|
|[컴파일러 오류 C3049](compiler-error-c3049.md)|'*argument*': OpenMP ' default ' 절의 인수가 잘못 되었습니다.|
|[컴파일러 오류 C3050](compiler-error-c3050.md)|'*class*': ref 클래스는 '*identifier*'에서 상속할 수 없습니다.|
|컴파일러 오류 C3051|사용되지 않습니다.|
|[컴파일러 오류 C3052](compiler-error-c3052.md)|'*identifier*': 변수가 default (none) 절 아래의 데이터 공유 절에 표시 되지 않습니다.|
|[컴파일러 오류 C3053](compiler-error-c3053.md)|'*identifier*': ' threadprivate '는 전역 또는 정적 데이터 항목에만 사용할 수 있습니다.|
|[컴파일러 오류 C3054](compiler-error-c3054.md)|현재 제네릭 클래스 또는 함수에서는 '#pragma omp parallel'가 지원되지 않습니다.|
|[컴파일러 오류 C3055](compiler-error-c3055.md)|'*identifier*': ' threadprivate ' 지시문에서 사용 하기 전에는 기호를 참조할 수 없습니다.|
|[컴파일러 오류 C3056](compiler-error-c3056.md)|'*identifier*': 기호가 ' threadprivate ' 지시문과 같은 범위에 없습니다.|
|[컴파일러 오류 C3057](compiler-error-c3057.md)|'*identifier*': ' threadprivate ' 기호의 동적 초기화는 현재 지원 되지 않습니다.|
|[컴파일러 오류 C3058](compiler-error-c3058.md)|'*identifier*': 기호를 ' copyin ' 절에 사용 하기 전에 ' threadprivate '로 선언 하지 않았습니다.|
|[컴파일러 오류 C3059](compiler-error-c3059.md)|'*identifier*': ' threadprivate ' 기호는 '*clause*' 절에서 사용할 수 없습니다.|
|[컴파일러 오류 C3060](compiler-error-c3060.md)|'*identifier*': friend 함수는 클래스 내부에서 정규화 된 이름을 사용 하 여 정의할 수 없습니다. 선언 될 수만 있습니다.|
|컴파일러 오류 C3061|'*operator*' 연산자: 기본 형식이 '*type*' 인 '*type*' 열거형에는 사용할 수 없습니다.|
|[컴파일러 오류 C3062](compiler-error-c3062.md)|'*identifier*': 기본 *형식이 ' t r u* e ' 이므로 열거자에 값이 필요 합니다.|
|[컴파일러 오류 C3063](compiler-error-c3063.md)|연산자 '*operator*': 모든 피연산자의 열거형 형식이 동일 해야 합니다.|
|컴파일러 오류 C3064|'*identifier*': 단순 형식 이거나 1로 확인 되어야 합니다.|
|[컴파일러 오류 C3065](compiler-error-c3065.md)|클래스 범위가 아닌 범위에서는 속성을 선언할 수 없습니다.|
|[컴파일러 오류 C3066](compiler-error-c3066.md)|이러한 인수를 사용 하 여이 형식의 개체를 호출할 수 있는 여러 가지 방법이 있습니다.|
|컴파일러 오류 C3067|이니셜라이저 목록은 기본 제공 operator []와 함께 사용할 수 없습니다.|
|[컴파일러 오류 C3068](compiler-error-c3068.md)|'*identifier*': ' naked ' 함수는 c + + 예외가 발생 했을 때 해제가 필요한 개체를 포함할 수 없습니다.|
|[컴파일러 오류 C3069](compiler-error-c3069.md)|연산자 '*operator*': 열거형 형식에 사용할 수 없습니다.|
|[컴파일러 오류 C3070](compiler-error-c3070.md)|'*identifier*': 속성에 ' set ' 메서드가 없습니다.|
|[컴파일러 오류 C3071](compiler-error-c3071.md)|'*operator*' 연산자는 ref 클래스 또는 값 형식의 인스턴스에만 적용할 수 있습니다.|
|[컴파일러 오류 C3072](compiler-error-c3072.md)|'*operator*' 연산자는 ref 클래스의 인스턴스에 적용할 수 없습니다. 단항 '% ' 연산자를 사용 하 여 ref 클래스 인스턴스를 핸들 형식으로 변환 하십시오.|
|[컴파일러 오류 C3073](compiler-error-c3073.md)|'*identifier*': ref 클래스에 사용자 정의 복사 생성자가 없습니다.|
|컴파일러 오류 C3074|배열은 괄호로 묶은 이니셜라이저로 초기화할 수 없습니다.|
|[컴파일러 오류 C3075](compiler-error-c3075.md)|'*identifier*': 참조 형식 '*type*'의 인스턴스는 값 형식에 포함할 수 없습니다.|
|[컴파일러 오류 C3076](compiler-error-c3076.md)|'*identifier*': 참조 형식 '*type*'의 인스턴스는 네이티브 형식에 포함할 수 없습니다.|
|[컴파일러 오류 C3077](compiler-error-c3077.md)|'*identifier*': 종료자는 참조 형식의 멤버일 수만 있습니다.|
|컴파일러 오류 C3078|새 식에는 배열 크기를 지정 해야 합니다.|
|컴파일러 오류 C3079|이니셜라이저 목록을이 할당 연산자의 오른쪽 피연산자로 사용할 수 없습니다.|
|[컴파일러 오류 C3080](compiler-error-c3080.md)|'*finalizer*': 종료자에는 저장소 클래스 지정자를 사용할 수 없습니다.|
|컴파일러 오류 C3081|사용되지 않습니다.|
|컴파일러 오류 C3082|사용되지 않습니다.|
|[컴파일러 오류 C3083](compiler-error-c3083.md)|'*identifier*': ':: '의 왼쪽에 있는 기호는 형식 이어야 합니다.|
|[컴파일러 오류 C3084](compiler-error-c3084.md)|'*identifier*': 소멸자/종료자는 '*keyword*' 일 수 없습니다.|
|[컴파일러 오류 C3085](compiler-error-c3085.md)|'*identifier*': 생성자는 '*keyword*' 일 수 없습니다.|
|컴파일러 오류 C3086|' std:: initializer_list '를 찾을 수 없습니다. #include 해야 합니다. \<initializer_list>|
|[컴파일러 오류 C3087](compiler-error-c3087.md)|'*identifier*':*' i n t '를* 호출할 때 이미이 멤버가 초기화 되었습니다.|
|컴파일러 오류 C3088|'*class*': 특성 생성자에는 명명 된 형식 인수가 있어야 합니다.|
|컴파일러 오류 C3089|'*identifier*': 매개 변수 이름이 데이터 멤버 이름과 일치 하지 않습니다.|
|컴파일러 오류 C3090|'*class*': 특성 클래스는 템플릿이 될 수 없습니다.|
|컴파일러 오류 C3091|'*class*': 특성 클래스는 기본 클래스를 가질 수 없습니다.|
|컴파일러 오류 C3092|'*class*': 특성 클래스 멤버는 ' static ' 또는 ' const ' 비트 필드 일 수 없습니다.|
|컴파일러 오류 C3093|'*type*': 특성 클래스 멤버 '*member*'에는 형식이 허용 되지 않습니다.|
|[컴파일러 오류 C3094](compiler-error-c3094.md)|'*attribute*': 익명 사용이 허용 되지 않습니다.|
|[컴파일러 오류 C3095](compiler-error-c3095.md)|'*attribute*': 특성을 반복할 수 없습니다.|
|[컴파일러 오류 C3096](compiler-error-c3096.md)|'*attribute*': 특성은 특성 클래스의 데이터 멤버에만 사용할 수 있습니다.|
|[컴파일러 오류 C3097](compiler-error-c3097.md)|'*attribute*': 특성의 범위는 ' assembly: ' 또는 ' module: ' 이어야 합니다.|
|컴파일러 오류 C3098|'*identifier*': 특성에 사용자 정의 생성자가 없습니다.|
|[컴파일러 오류 C3099](compiler-error-c3099.md)|'*keyword*': 관리 되는/WinRT 특성에 [System:: AttributeUsageAttribute]/[Windows:: Foundation:: Metadata:: AttributeUsageAttribute]를 사용 하십시오.|

## <a name="see-also"></a>참고 항목

[C/c + + 컴파일러 및 빌드 도구 오류 및 경고](../compiler-errors-1/c-cpp-build-errors.md) \
[컴파일러 오류 C2000 ~ C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
