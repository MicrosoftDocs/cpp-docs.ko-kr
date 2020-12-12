---
description: '자세한 정보: 컴파일러 오류 C2300 ~ C2399'
title: 컴파일러 오류 C2300 ~ C2399
ms.date: 04/21/2019
f1_keywords:
- C2303
- C2304
- C2305
- C2306
- C2314
- C2321
- C2323
- C2328
- C2329
- C2330
- C2331
- C2335
- C2336
- C2339
- C2340
- C2342
- C2343
- C2347
- C2354
- C2358
- C2359
- C2363
- C2366
- C2367
- C2398
- C2399
helpviewer_keywords:
- C2303
- C2304
- C2305
- C2306
- C2314
- C2321
- C2323
- C2328
- C2329
- C2330
- C2331
- C2335
- C2336
- C2339
- C2340
- C2342
- C2343
- C2347
- C2354
- C2358
- C2359
- C2363
- C2366
- C2367
- C2398
- C2399
ms.assetid: 07ca45b5-b2f0-4049-837b-40a7a3caed88
ms.openlocfilehash: 95763db7f8be0c0918d2f15f515f327325c386dc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318951"
---
# <a name="compiler-errors-c2300-through-c2399"></a>컴파일러 오류 C2300 ~ C2399

설명서의이 섹션에 있는 문서는 컴파일러에 의해 생성 되는 오류 메시지의 하위 집합을 설명 합니다.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>오류 메시지

|Error|메시지|
|-----------|-------------|
|[컴파일러 오류 C2300](compiler-error-c2300.md)|'*class*': 클래스에 ' ~*class*' (이) 라는 소멸자가 없습니다.|
|[컴파일러 오류 C2301](compiler-error-c2301.md)|'->~*identifier*' 왼쪽은 클래스/구조체/공용 구조체를 가리켜야 합니다.|
|[컴파일러 오류 C2302](compiler-error-c2302.md)|'. ~*identifier*' 왼쪽에는 클래스/구조체/공용 구조체 형식이 있어야 합니다.|
|컴파일러 오류 C2303|구조적 예외 처리는 코 루틴에서 사용할 수 없습니다.|
|컴파일러 오류 C2304|'*keyword*'는 catch 블록 내부에서 사용할 수 없습니다.|
|컴파일러 오류 C2305|'*file*'에이 모듈에 대 한 디버깅 정보가 포함 되어 있지 않습니다.|
|컴파일러 오류 C2306|'*file*'에이 모듈에 대 한 최신 디버깅 정보가 포함 되어 있지 않습니다.|
|[컴파일러 오류 C2307](compiler-error-c2307.md)|증분 컴파일을 사용 하도록 설정한 경우에는 함수 외부에서 pragma *지시문* 을 이동 해야 합니다.|
|[컴파일러 오류 C2308](compiler-error-c2308.md)|일치 하지 않는 문자열 연결|
|[컴파일러 오류 C2309](compiler-error-c2309.md)|catch 처리기에 괄호로 묶은 예외 선언이 필요 합니다.|
|[컴파일러 오류 C2310](compiler-error-c2310.md)|catch 처리기는 형식을 하나 지정 해야 합니다.|
|[컴파일러 오류 C2311](compiler-error-c2311.md)|'*type*': ' ... '에 의해 catch 되었습니다. 줄 *번호*|
|[컴파일러 오류 C2312](compiler-error-c2312.md)|'*type1*': 줄 *번호* 에서 '*type2*'에 의해 catch 되었습니다.|
|[컴파일러 오류 C2313](compiler-error-c2313.md)|'*type1*': 줄 *번호* 에서 참조 ('*type2*')에 의해 catch 되었습니다.|
|컴파일러 오류 C2314|'*keyword1*' 키워드는 사용 되지 않습니다. 대신 '*keyword2*'를 사용 하세요.|
|[컴파일러 오류 C2315](compiler-error-c2315.md)|'*type1*': 줄 *번호* 의 '*type2*'에서 참조를 catch 했습니다.|
|[컴파일러 오류 C2316](compiler-error-c2316.md)|'*type*': 소멸자로 catch 할 수 없거나 복사 생성자에 액세스할 수 없거나 삭제 되었습니다.|
|[컴파일러 오류 C2317](compiler-error-c2317.md)|'*number*' 줄에서 시작 하는 ' try ' 블록에 catch 처리기가 없습니다.|
|[컴파일러 오류 C2318](compiler-error-c2318.md)|이 catch 처리기와 관련된 try 블록이 없습니다.|
|[컴파일러 오류 C2319](compiler-error-c2319.md)|'try/catch'는 복합 문이 뒤에 와야 합니다. '{'가 없습니다.|
|[컴파일러 오류 C2320](compiler-error-c2320.md)|액세스 지정자 '*지정자*' 다음에 ': '이 필요 합니다.|
|컴파일러 오류 C2321|'*identifier*'는 키워드 이며이 컨텍스트에서 사용할 수 없습니다.|
|[컴파일러 오류 C2322](compiler-error-c2322.md)|'*identifier*': dllimport '*identifier*'의 주소가 정적 주소가 아닙니다.|
|컴파일러 오류 C 2323|'*identifier*': 멤버가 아닌 operator new 또는 delete 함수는 static으로 선언 하거나 전역 네임 스페이스가 아닌 네임 스페이스에서 선언할 수 없습니다.|
|[컴파일러 오류 C2324](compiler-error-c2324.md)|'*identifier*': ':: ~ '의 오른쪽에는 적합 하지 않습니다.|
|[컴파일러 오류 C2325](compiler-error-c2325.md)|'*type1*': '->~ ' 오른쪽에 예기치 않은 형식이 있습니다. '*type2*'가 필요 합니다.|
|[컴파일러 오류 C2326](compiler-error-c2326.md)|'*선언 자*': 함수에서 '*identifier*'에 액세스할 수 없습니다.|
|[컴파일러 오류 C2327](compiler-error-c2327.md)|'*identifier*': 형식 이름, 정적 또는 열거자가 아닙니다.|
|컴파일러 오류 C2328|'*keyword*': 아직 지원 되지 않는 키워드입니다.|
|컴파일러 오류 C2329|'*identifier*': 함수에 대 한 포인터에 __ptr64 사용할 수 없습니다.|
|컴파일러 오류 C2330|' implementation_key () '는 #pragma start_map_region/stop_map_region에 의해 제한 된 영역 에서만 유효 합니다.|
|컴파일러 오류 C2331|'*identifier*'에 대 한 액세스는 이제 '*accessibility1*'로 정의 되었으며 이전에는 '*accessibility2*'로 정의 되었습니다.|
|[컴파일러 오류 C2332](compiler-error-c2332.md)|'*typedef*': 태그 이름이 없습니다.|
|[컴파일러 오류 C2333](compiler-error-c2333.md)|'*function*': 함수 선언에 오류가 있습니다. 함수 본문을 건너뛰는 중|
|[컴파일러 오류 C2334](compiler-error-c2334.md)|'*token*' 앞에 예기치 않은 토큰이 있습니다. 명백한 함수 본문을 건너뜁니다.|
|컴파일러 오류 C2335|'*identifier*': 형식은 함수 매개 변수 목록에 사용할 수 없습니다.|
|컴파일러 오류 C2336|'*type*': 잘못 된 형식입니다.|
|[컴파일러 오류 C2337](compiler-error-c2337.md)|'*attribute*': 특성을 찾을 수 없습니다.|
|[컴파일러 오류 C2338](compiler-error-c2338.md)|*(외부 공급자의 오류 메시지)*|
|컴파일러 오류 C2339|'*identifier*': 포함 된 IDL에 잘못 된 형식이 있습니다.|
|컴파일러 오류 C2340|'*identifier*': ' s t r u e '는 클래스 정의 내 에서만 사용할 수 있습니다.|
|[컴파일러 오류 C2341](compiler-error-c2341.md)|'*section*': 세그먼트를 사용 하려면 먼저 #pragma data_seg, code_seg 또는 섹션을 사용 하 여 세그먼트를 정의 해야 합니다.|
|컴파일러 오류 C2342|구문 오류: 형식 한정자가 충돌 합니다.|
|컴파일러 오류 C2343|'*section*': 섹션 특성이 충돌 합니다.|
|[컴파일러 오류 C2344](compiler-error-c2344.md)|align (*number*): 맞춤은 2의 거듭제곱 이어야 합니다.|
|[컴파일러 오류 C2345](compiler-error-c2345.md)|align (*number*): 맞춤 값이 잘못 되었습니다.|
|[컴파일러 오류 C2346](compiler-error-c2346.md)|'*function*'은 네이티브로 컴파일할 수 없습니다. '*설명*'|
|컴파일러 오류 C2347|사용되지 않습니다.|
|[컴파일러 오류 C2348](compiler-error-c2348.md)|'*type*': C 스타일 집합체가 아니므로 포함 IDL에서 내보낼 수 없습니다.|
|[컴파일러 오류 C2349](compiler-error-c2349.md)|'*function*'은 (는) 관리 되는 것으로 컴파일할 수 없습니다. '*설명*'; #pragma 관리 되지 않는 사용|
|[컴파일러 오류 C2350](compiler-error-c2350.md)|'*identifier*'는 정적 멤버가 아닙니다.|
|[컴파일러 오류 C2351](compiler-error-c2351.md)|사용 되지 않는 c + + 생성자 초기화 구문|
|[컴파일러 오류 C2352](compiler-error-c2352.md)|'*identifier*': 비정적 멤버 함수를 잘못 호출 했습니다.|
|[컴파일러 오류 C2353](compiler-error-c2353.md)|예외 사양을 사용할 수 없습니다.|
|컴파일러 오류 C2354|사용되지 않습니다.|
|[컴파일러 오류 C2355](compiler-error-c2355.md)|' this ': 비정적 멤버 함수 또는 비정적 데이터 멤버 이니셜라이저 내 에서만 참조할 수 있습니다.|
|[컴파일러 오류 C2356](compiler-error-c2356.md)|초기화 세그먼트는 변환 단위 동안 변경 되지 않아야 합니다.|
|[컴파일러 오류 C2357](compiler-error-c2357.md)|'*identifier*': '*type*' 형식의 함수 여야 합니다.|
|컴파일러 오류 C2358|'*identifier*': 클래스 정의 외부에서 정적 속성을 정의할 수 없습니다.|
|컴파일러 오류 C2359|사용되지 않습니다.|
|[컴파일러 오류 C2360](compiler-error-c2360.md)|' case ' 레이블에서 '*identifier*' 초기화를 건너뛰었습니다.|
|[컴파일러 오류 C2361](compiler-error-c2361.md)|'*identifier*' 초기화는 ' default ' 레이블에 의해 생략 됩니다.|
|[컴파일러 오류 C2362](compiler-error-c2362.md)|' goto *label*'에서 '*identifier*' 초기화를 건너뜁니다.|
|컴파일러 오류 C2363|컴파일러 내장 숫자 제한 함수에는 문자열 리터럴 인수가 필요 합니다.|
|[컴파일러 오류 C2364](compiler-error-c2364.md)|'*type*': 사용자 지정 특성의 형식이 잘못 되었습니다.|
|[컴파일러 오류 C2365](compiler-error-c2365.md)|'*member1*': 재정의 이전 정의는 '*member2*'입니다.|
|컴파일러 오류 C2366|'*identifier*': 재정의 다른 implementation_key 지정자|
|컴파일러 오류 C2367|사용되지 않습니다.|
|[컴파일러 오류 C2368](compiler-error-c2368.md)|'*identifier*': 재정의 다른 할당 지정자|
|[컴파일러 오류 C2369](compiler-error-c2369.md)|'*identifier*': 재정의 다른 첨자가 있습니다.|
|[컴파일러 오류 C2370](compiler-error-c2370.md)|'*identifier*': 재정의 다른 저장소 클래스|
|[컴파일러 오류 C2371](compiler-error-c2371.md)|'*identifier*': 재정의 다양 한 기본 형식|
|[컴파일러 오류 C2372](compiler-error-c2372.md)|'*identifier*': 재정의 서로 다른 유형의 간접 참조|
|[컴파일러 오류 C2373](compiler-error-c2373.md)|'*identifier*': 재정의 다른 형식 한정자|
|[컴파일러 오류 C2374](compiler-error-c2374.md)|'*identifier*': 재정의 여러 초기화|
|[컴파일러 오류 C2375](compiler-error-c2375.md)|'*identifier*': 재정의 다른 링크|
|[컴파일러 오류 C2376](compiler-error-c2376.md)|'*identifier*': 재정의 다른 기반 할당|
|[컴파일러 오류 C2377](compiler-error-c2377.md)|'*identifier*': 재정의 typedef는 다른 기호를 사용 하 여 오버 로드할 수 없습니다.|
|[컴파일러 오류 C2378](compiler-error-c2378.md)|'*identifier*': 재정의 typedef를 사용 하 여 기호를 오버 로드할 수 없습니다.|
|[컴파일러 오류 C2379](compiler-error-c2379.md)|승격 시 형식 매개 변수 *번호* 의 형식이 다릅니다.|
|[컴파일러 오류 C2380](compiler-error-c2380.md)|'*identifier*' 앞의 형식 (반환 형식이 있는 생성자 또는 현재 클래스 이름에 대 한 잘못 된 재정의)|
|[컴파일러 오류 C2381](compiler-error-c2381.md)|'*identifier*': 재정의 ' __declspec (noreturn) ' 또는 ' [[noreturn]] '이 (가) 다릅니다.|
|[컴파일러 오류 C2382](compiler-error-c2382.md)|'*identifier*': 재정의 다른 예외 사양|
|[컴파일러 오류 C2383](compiler-error-c2383.md)|'*identifier*':이 기호에는 기본 인수를 사용할 수 없습니다.|
|[컴파일러 오류 C2384](compiler-error-c2384.md)|'*member*': 관리 되는/WinRT 클래스의 멤버에 thread_local 또는 __declspec (thread)를 적용할 수 없습니다.|
|[컴파일러 오류 C2385](compiler-error-c2385.md)|'*member*'의 모호한 액세스|
|[컴파일러 오류 C2386](compiler-error-c2386.md)|'*identifier*': 이름이 같은 기호가 현재 범위에 이미 있습니다.|
|[컴파일러 오류 C2387](compiler-error-c2387.md)|'*identifier*': 모호한 기본 클래스입니다.|
|[컴파일러 오류 C2388](compiler-error-c2388.md)|'*identifier*': 기호는 __declspec (appdomain)와 __declspec (process)를 사용 하 여 선언할 수 없습니다.|
|[컴파일러 오류 C2389](compiler-error-c2389.md)|'*operator*': ' nullptr ' 피연산자가 잘못 되었습니다.|
|[컴파일러 오류 C2390](compiler-error-c2390.md)|'*identifier*': '*지정자*' 저장소 클래스가 잘못 되었습니다.|
|[컴파일러 오류 C2391](compiler-error-c2391.md)|'*identifier*': 형식 정의 중에는 ' friend '를 사용할 수 없습니다.|
|[컴파일러 오류 C2392](compiler-error-c2392.md)|'*member1*': 공변 (covariant) 반환 형식은 관리 되는/WinRT 형식에서 지원 되지 않습니다. 그렇지 않으면 '*member2*'가 재정의 됩니다.|
|[컴파일러 오류 C2393](compiler-error-c2393.md)|'*symbol*': '*segment*' 세그먼트에 appdomain 별 기호를 할당할 수 없습니다.|
|[컴파일러 오류 C2394](compiler-error-c2394.md)|'*type*:: operator *Operator*': CLR/WinRT 연산자가 잘못 되었습니다. 하나 이상의 매개 변수가 ' t ^ ', ' t ^% ', ' T ^& ' 형식 이어야 합니다. 여기서 T *= ' t* r u e '입니다.|
|[컴파일러 오류 C2395](compiler-error-c2395.md)|'*type*:: operator *Operator*': CLR/WinRT 연산자가 잘못 되었습니다. 하나 이상의 매개 변수가 ' t ', ' t% '&, ' t ', ' t ^ ', ' t ^&% ', ' t = '*형식*' 형식 이어야 합니다.|
|[컴파일러 오류 C2396](compiler-error-c2396.md)|'*type1*:: operator *Type2*': CLR/WinRT 사용자 정의 변환 함수가 잘못 되었습니다. Convert 또는 convert에서 ' t ^ ', ' t ^% ', ' t ^& ' (여기서 T = '*type1*') 중 하나 여야 합니다.|
|[컴파일러 오류 C2397](compiler-error-c2397.md)|'*type1*'에서 '*type2*' (으)로의 변환에는 축소 변환이 필요 합니다.|
|컴파일러 오류 C2398|요소 '*number*': '*type1*'에서 '*type2*' (으)로 변환 하려면 축소 변환이 필요 합니다.|
|컴파일러 오류 C2399|사용되지 않습니다.|

## <a name="see-also"></a>참고 항목

[C/c + + 컴파일러 및 빌드 도구 오류 및 경고](../compiler-errors-1/c-cpp-build-errors.md) \
[컴파일러 오류 C2000 ~ C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
