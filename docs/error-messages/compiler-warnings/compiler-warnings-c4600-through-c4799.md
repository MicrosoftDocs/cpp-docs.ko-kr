---
title: 컴파일러 경고 C4600 C4799 ~ | Microsoft Docs
ms.date: 11/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4602
- C4603
- C4609
- C4612
- C4613
- C4620
- C4622
- C4629
- C4631
- C4634
- C4635
- C4636
- C4637
- C4638
- C4645
- C4646
- C4655
- C4657
- C4658
- C4662
- C4670
- C4671
- C4672
- C4674
- C4676
- C4678
- C4681
- C4682
- C4685
- C4688
- C4689
- C4690
- C4693
- C4694
- C4695
- C4696
- C4718
- C4719
- C4720
- C4721
- C4722
- C4724
- C4725
- C4728
- C4729
- C4732
- C4739
- C4750
- C4751
- C4752
- C4754
- C4755
- C4757
- C4764
- C4767
- C4770
- C4792
- C4794
dev_langs:
- C++
ms.assetid: 22bd4392-f3be-445c-9f23-6126aebac901
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ad29989e89bfe60f2180ee48c411ebd4d3098ce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warnings-c4600-through-c4799"></a>컴파일러 경고 C4600 C4799 ~

설명서의이 섹션의 문서 컴파일러에 의해 생성 되는 경고 메시지의 하위 집합에 설명 합니다.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>경고 메시지

|경고|메시지|
|-------------|-------------|
|[컴파일러 경고(수준 1) C4600](../../error-messages/compiler-warnings/compiler-warning-level-1-c4600.md)|#pragma '매크로 name': 유효한 비어 있지 않은 문자열이 필요 합니다.|
|컴파일러 경고 (수준 1) C4602|#pragma pop_macro: '매크로 이름'이 식별자에 대 한 이전 #pragma push_macro가 없습니다|
|컴파일러 경고 (수준 1) C4603|'*식별자*': 매크로가 정의 되지 않았거나 미리 컴파일된 헤더 사용 후 정의가 다릅니다|
|컴파일러 경고 (수준 1) C4604|'*형식*': 유효한 복사 생성자가 필요 네이티브 및 관리 되는 경계 값으로 인수를 전달 합니다. 그렇지 않으면 런타임 동작이 정의 되지 않습니다.|
|컴파일러 경고 (수준 1) C4605|' /D*매크로*' 현재 명령줄에 지정 되었지만 미리 컴파일된 헤더 빌드 했을 때 지정 되지 않았습니다|
|[컴파일러 경고(수준 1) C4606](../../error-messages/compiler-warnings/compiler-warning-level-1-c4606.md)|#pragma 경고: '경고 번호'이 무시 됩니다. 코드 분석 경고가 경고 수준과 연결 되어 있지 않습니다.|
|[컴파일러 경고(수준 3) C4608](../../error-messages/compiler-warnings/compiler-warning-level-3-c4608.md)|'union_member'가 이미 이니셜라이저 목록의 다른 공용 구조체 멤버 'union_member'에 의해 초기화되었습니다.|
|컴파일러 경고 (수준 3, 오류) C4609|'*type1*'기본 인터페이스에서 파생'*인터페이스*'유형에'*type2*'. 에 대 한 다른 기본 인터페이스를 사용 하 여 '*type1*', 또는 기본/파생 관계를 중단 합니다.|
|[컴파일러 경고(수준 4) C4610](../../error-messages/compiler-warnings/compiler-warning-level-4-c4610.md)|'class' 개체를 인스턴스화할 수 없습니다-사용자 정의 생성자가 있어야 합니다.|
|[컴파일러 경고(수준 4) C4611](../../error-messages/compiler-warnings/compiler-warning-level-4-c4611.md)|'function' 및 c + + 개체 소멸 사이의 상호 작용이 이식 가능 하지 않습니다.|
|컴파일러 경고 (수준 1) C4612|포함 파일 이름에 오류가 있습니다.|
|컴파일러 경고 (수준 1) C4613|'*기호*': 세그먼트 클래스를 변경할 수 없습니다|
|[컴파일러 경고(수준 1) C4615](../../error-messages/compiler-warnings/compiler-warning-level-1-c4615.md)|#pragma 경고: 알 수 없는 사용자 경고 형식|
|[컴파일러 경고(수준 1) C4616](../../error-messages/compiler-warnings/compiler-warning-level-1-c4616.md)|#pragma 경고: 경고 번호 '번호' 올바른 컴파일러 경고가 아닙니다|
|[컴파일러 경고(수준 1) C4618](../../error-messages/compiler-warnings/compiler-warning-level-1-c4618.md)|pragma 매개 변수 포함 빈 문자열인 경우. pragma가 무시 되었습니다|
|[컴파일러 경고(수준 3) C4619](../../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md)|#pragma warning: 경고 번호 '번호'이(가) 없습니다.|
|컴파일러 경고 (수준 1) C4620|'type' 형식에 대한 'operator ++' 후위 형식이 없으므로 전위 형식이 사용됩니다.|
|[컴파일러 경고(수준 1) C4621](../../error-messages/compiler-warnings/compiler-warning-level-1-c4621.md)|'operator--' 전위 형태를 사용 하 여 ' type' 형식에 대 한의 후 위 형식이 없으므로|
|컴파일러 경고 (수준 3) C4622|미리 컴파일된 헤더를 개체 파일을 만드는 동안 생성 된 디버그 정보를 덮어쓰고: 'file'|
|[컴파일러 경고(수준 4) C4623](../../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md)|'derived class': 기본 생성자가 암시적으로 기본 클래스 기본 생성자를 액세스할 수 없거나 삭제 된 삭제 된 것으로 정의 됩니다|
|[컴파일러 경고(수준 1) C4624](../../error-messages/compiler-warnings/compiler-warning-level-1-c4624.md)|'derived class': 기본 클래스 소멸자를 액세스할 수 없거나 삭제 된 삭제 된 것으로 소멸자가 암시적으로 된 정의|
|[컴파일러 경고(수준 4) C4625](../../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md)|'derived class': 복사 생성자가 기본 클래스 복사 생성자를 액세스할 수 없거나 삭제 된 삭제 된 것으로 암시적으로 정의 됩니다|
|[컴파일러 경고(수준 4) C4626](../../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md)|'derived class': 기본 클래스 할당 연산자를 액세스할 수 없거나 삭제 된 삭제 된 것으로 할당 연산자가 암시적 된 정의|
|[컴파일러 경고(수준 1) C4627](../../error-messages/compiler-warnings/compiler-warning-level-1-c4627.md)|'\<식별자 >': 미리 컴파일된 헤더 사용을 찾을 때 건너뛰었습니다|
|[컴파일러 경고(수준 1) C4628](../../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md)|-Ze에는 digraph가 지원되지 않습니다. 문자 시퀀스 'digraph' '%s'에 대 한 대체 토큰으로 해석 되지 않습니다|
|컴파일러 경고 (수준 4) C4629|digraph가 사용되었습니다. 문자 시퀀스 'digraph'는 토큰 'char'로 해석됩니다. 이렇게 해석하려는 경우가 아니라면 두 문자 사이에 공백을 넣으세요.|
|[컴파일러 경고(수준 1) C4630](../../error-messages/compiler-warnings/compiler-warning-level-1-c4630.md)|'symbol': 멤버 정의에 잘못 된 'extern' 저장소 클래스 지정자|
|컴파일러 경고 (수준 2) C4631|MSXML 또는 XPath를 사용할 수 없습니다. XML 문서 주석이 처리되지 않습니다. 이유|
|[컴파일러 경고(수준 1) C4632](../../error-messages/compiler-warnings/compiler-warning-level-1-c4632.md)|XML 문서 주석: file-액세스 거부: 이유|
|[컴파일러 경고(수준 3) C4633](../../error-messages/compiler-warnings/compiler-warning-level-3-c4633.md)|XML 문서 주석 target: 오류: 이유|
|컴파일러 경고 (수준 4) C4634|XML 문서 주석 target: 적용할 수 없습니다: 이유|
|컴파일러 경고 (수준 3) C4635|XML 문서 주석 대상: 잘못된 형식의 XML: 이유|
|컴파일러 경고 (수준 3) C4636|구성에 적용 하는 XML 문서 주석: 태그 비어 있지 않은 'attribute' 특성이 필요 합니다.|
|컴파일러 경고 (수준 3 및 수준 4) C4637|XML 문서 주석 target: \<포함 > 태그가 삭제 되었습니다. 이유|
|컴파일러 경고 (수준 3) C4638|XML 문서 주석 대상: 'symbol' 알 수 없는 기호에 대 한 참조입니다.|
|[컴파일러 경고(수준 4) C4639](../../error-messages/compiler-warnings/compiler-warning-level-4-c4639.md)|MSXML 오류, XML 문서 주석이 처리 되지 것입니다. 이유|
|[컴파일러 경고(수준 3) C4640](../../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md)|'instance': 지역 정적 개체를 생성할 때 스레드로부터 안전하게 보호되지 않습니다.|
|[컴파일러 경고(수준 3) C4641](../../error-messages/compiler-warnings/compiler-warning-level-3-c4641.md)|XML 문서 주석에 모호한 상호 참조가 있습니다.|
|컴파일러 경고 (수준 3) C4645|__declspec(noreturn)으로 선언된 함수에 return 문이 있습니다.|
|컴파일러 경고 (수준 3) C4646|__declspec(noreturn)으로 선언된 함수에 void가 아닌 반환 형식이 있습니다.|
|컴파일러 경고 (수준 3) C4647|동작 변경: __is_pod (*형식*) 이전 버전에 서로 다른 값|
|컴파일러 경고 (수준 3) C4648|표준 특성 'carries_dependency'는 무시 됩니다.|
|컴파일러 경고 (수준 3) C4649|특성이이 컨텍스트에서 무시 됩니다.|
|[컴파일러 경고(수준 1) C4650](../../error-messages/compiler-warnings/compiler-warning-level-1-c4650.md)|미리 컴파일된 헤더에는 없는 정보가 디버깅 헤더의 전역 기호만 사용할 수 있습니다.|
|[컴파일러 경고(수준 1) C4651](../../error-messages/compiler-warnings/compiler-warning-level-1-c4651.md)|' 정의 ' 미리 컴파일된 헤더에 대 한 있지만 현재 컴파일에 대 한 지정|
|[컴파일러 경고(수준 1) C4652](../../error-messages/compiler-warnings/compiler-warning-level-1-c4652.md)|미리 컴파일된 헤더와 일치 하지 않는 ' option' 컴파일러 옵션 현재 명령줄 옵션이 미리 컴파일된 헤더에 정의 된 것을 재정의 합니다.|
|[컴파일러 경고(수준 2) C4653](../../error-messages/compiler-warnings/compiler-warning-level-2-c4653.md)|미리 컴파일된 헤더와 일치 하지 않는 ' option' 컴파일러 옵션 현재 명령줄 옵션이 무시|
|컴파일러 경고 (수준 4) C4654|미리 컴파일된 헤더의 앞에 배치 하는 코드는 무시 됩니다. 미리 컴파일된 헤더에 코드를 추가 합니다.|
|컴파일러 경고 (수준 1) C4655|'symbol': 변수 형식이 최근 빌드 후 새로 만들어졌거나 다른 곳에서 다르게 정의 된|
|[컴파일러 경고(수준 1) C4656](../../error-messages/compiler-warnings/compiler-warning-level-1-c4656.md)|'symbol': 새로운 또는 최근 빌드 후 변경 되거나 다른 곳에서 다르게 정의 된 데이터 형식|
|컴파일러 경고 (수준 1) C4657|식에는 최근 빌드 후 새로 추가 된 데이터 형식이 들어 있습니다.|
|컴파일러 경고 (수준 1) C4658|'function': 함수 프로토타입이 최근 빌드 후 새로 만들어졌거나 다른 곳에서 다르게 선언 된|
|[컴파일러 경고(수준 1) C4659](../../error-messages/compiler-warnings/compiler-warning-level-1-c4659.md)|'pragma' #pragma: #pragma 주석 (linker,...)를 사용 하 여, 사용 하 여 예약 된 세그먼트 'segment' 동작이 정의 되지 않았습니다|
|[컴파일러 경고(수준 1) C4661](../../error-messages/compiler-warnings/compiler-warning-level-1-c4661.md)|'identifier': 명시적 템플릿 인스턴스화 요청에 대해 제공 된 적합 한 정의가 없습니다|
|컴파일러 경고 (수준 1) C4662|명시적 인스턴스화. 템플릿-클래스 'identifier1'에 'identifier2'를 특수화하는 데 사용된 정의가 없습니다.|
|[컴파일러 경고(수준 1) C4667](../../error-messages/compiler-warnings/compiler-warning-level-1-c4667.md)|'function': 강제 인스턴스화와 일치 하는 정의 된 함수 템플릿이 없습니다|
|[컴파일러 경고(수준 4) C4668](../../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md)|'symbol' 'directive'에 '0'으로 바뀝니다. 전처리기 매크로로 정의 되지 않았습니다.|
|[컴파일러 경고(수준 1) C4669](../../error-messages/compiler-warnings/compiler-warning-level-1-c4669.md)|'cast': 안전 하지 않은 변환: 'class'는 관리 되는 형식 개체|
|컴파일러 경고 (수준 4) C4670|'identifier':이 기본 클래스를 액세스할 수 없는 경우|
|컴파일러 경고 (수준 4) C4671|'identifier': 복사 생성자가 액세스할 수 없습니다|
|컴파일러 경고 (수준 4) C4672|'identifier1': 모호 합니다. 우선 'identifier2'로 표시됩니다.|
|[컴파일러 경고(수준 4) C4673](../../error-messages/compiler-warnings/compiler-warning-level-4-c4673.md)|'identifier' 다음 형식 발생 고려 되지 않습니다. catch 쪽에서|
|컴파일러 경고 (수준 1) C4674|'method'는 'static'으로 선언해야 하며 하나의 매개 변수만 가져야 합니다.|
|컴파일러 경고 (수준 4) C4676|'%s': 소멸자에 액세스할 수 없으면|
|[컴파일러 경고(수준 1) C4677](../../error-messages/compiler-warnings/compiler-warning-level-1-c4677.md)|'function': 전용이 아닌 멤버의 시그니처에 어셈블리 전용 형식 'private_type'|
|컴파일러 경고 (수준 1) C4678|기본 클래스 'base_type'이 'derived_type'보다 액세스하기 어렵습니다.|
|[컴파일러 경고(수준 1) C4679](../../error-messages/compiler-warnings/compiler-warning-level-1-c4679.md)|'member': 멤버를 가져올 수 없습니다|
|[컴파일러 경고(수준 4) C4680](../../error-messages/compiler-warnings/compiler-warning-level-4-c4680.md)|'class': coclass는 기본 인터페이스를 지정 하지 않습니다|
|컴파일러 경고 (수준 4) C4681|'class': coclass가 이벤트 소스인 기본 인터페이스를 지정 하지 않습니다|
|컴파일러 경고 (수준 4) C4682|'parameter': 방향 매개 변수 특성을 지정 하지 [in]를 기본값으로 설정|
|[컴파일러 경고(수준 1) C4683](../../error-messages/compiler-warnings/compiler-warning-level-1-c4683.md)|'function': 이벤트 소스에 'out'-매개 변수 여러 이벤트 처리기를 후크 하는 경우에 주의|
|[컴파일러 경고(수준 1) C4684](../../error-messages/compiler-warnings/compiler-warning-level-1-c4684.md)|'attribute': 경고!! 특성에 잘못 된 코드가 생성 발생할 수 있습니다: 주의 하 여 사용|
|컴파일러 경고 (수준 1) C4685|템플릿 매개 변수를 분석하는 경우 '> >'가 있어야 하는데 '>>'가 왔습니다.|
|[컴파일러 경고(수준 3) C4686](../../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md)|'user-defined type': 동작과 UDT 반환 호출 규칙이 변경되었을 수 있습니다.|
|[컴파일러 경고 (오류) C4687](../../error-messages/compiler-warnings/compiler-warning-c4687.md)|'class': 봉인된 추상 클래스는 ' interface '인터페이스를 구현할 수 없습니다|
|컴파일러 경고 (수준 1) C4688|'constraint': 제약 조건 목록에 어셈블리 전용 형식 'type'이 있습니다.|
|컴파일러 경고 (수준 1) C4689|'%c': 문자; #pragma detect_mismatch에 지원 되지 않습니다. #pragma 무시|
|컴파일러 경고 (수준 4) C4690|[ emitidl ( pop ) ]: 푸시 횟수 보다 팝|
|[컴파일러 경고(수준 1) C4691](../../error-messages/compiler-warnings/compiler-warning-level-1-c4691.md)|'type': 참조 하는 형식이 참조 되지 않은 어셈블리 'file'를 대신 사용 하는 현재 변환 단위에 정의 된 형식에에서 필요|
|[컴파일러 경고(수준 1) C4692](../../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md)|'function': 전용이 아닌 멤버의 시그니처에 어셈블리 전용 네이티브 형식 'native_type'이(가) 있습니다.|
|[컴파일러 경고 (수준 1, 오류) C4693](../../error-messages/compiler-warnings/compiler-warning-c4693.md)|'class': 봉인된 추상 클래스 인스턴스 멤버 '인스턴스 멤버' 가질 수 없습니다|
|[컴파일러 경고 (수준 1, 오류) C4694](../../error-messages/compiler-warnings/compiler-warning-c4694.md)|'class': 봉인된 추상 클래스는 기본 클래스 'base_class' 여야 합니다.|
|컴파일러 경고 (수준 1) C4695|#pragma execution_character_set: '문자 집합' 지원 되는 인수가 아닙니다: ' u t F-8'을 현재만 지원 됩니다|
|컴파일러 경고 (수준 1) C4696|/ ZBvalue1 옵션이; 범위를 벗어났습니다. 'value2' 가정합니다.|
|[컴파일러 경고(수준 1 및 수준 4) C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)|'name'가 사용 되는 초기화 되지 않은 지역 변수|
|[컴파일러 경고(수준 4) C4701](../../error-messages/compiler-warnings/compiler-warning-level-4-c4701.md)|'name'가 사용 되는 잠재적으로 초기화 되지 않은 지역 변수|
|[컴파일러 경고(수준 4) C4702](../../error-messages/compiler-warnings/compiler-warning-level-4-c4702.md)|코드에 접근할 수|
|[컴파일러 경고(수준 4) C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)|잠재적으로 초기화 되지 않은 지역 포인터 변수를 사용 하는 '%s'|
|[컴파일러 경고(수준 4) C4706](../../error-messages/compiler-warnings/compiler-warning-level-4-c4706.md)|조건식 내에서 할당|
|[컴파일러 경고(수준 4) C4709](../../error-messages/compiler-warnings/compiler-warning-level-4-c4709.md)|배열 인덱스 식 내에 쉼표 연산자|
|[컴파일러 경고(수준 4) C4710](../../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md)|'function': 함수를 인라이닝하지 못했습니다.|
|[컴파일러 경고(수준 1) C4711](../../error-messages/compiler-warnings/compiler-warning-level-1-c4711.md)|' function '함수를 자동 인라인 확장 선택|
|[컴파일러 경고(수준 4) C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md)|' function' 인라인이 아니라 __forceinline로 표시|
|[컴파일러 경고(수준 1) C4715](../../error-messages/compiler-warnings/compiler-warning-level-1-c4715.md)|'function': 모든 제어 경로 값을 반환|
|[컴파일러 경고 (수준 1, 오류) C4716](../../error-messages/compiler-warnings/compiler-warning-level-1-c4716.md)|'function': 값을 반환 해야|
|[컴파일러 경고(수준 1) C4717](../../error-messages/compiler-warnings/compiler-warning-level-1-c4717.md)|'function': 모든 제어 경로에서 재귀적으로 함수 런타임 스택 오버플로가 발생 하면|
|컴파일러 경고 (수준 4) C4718|'function call': 재귀 호출에 파생 작업이 없습니다. 삭제|
|컴파일러 경고 (수준 1) C4719|이중 상수를 Qfast로 지정 된 경우-사용 하 여 'f'를 단 정밀도 찾았습니다.|
|컴파일러 경고 (수준 2) c 4720|인라인 어셈블러 보고서: 'message'|
|컴파일러 경고 (수준 1) C4721|'function': 내장 함수로 사용할 수 없음|
|컴파일러 경고 (수준 1) C4722|'function': 소멸자 반환 하지 않습니다. 잠재적인 메모리 누수|
|[컴파일러 경고(수준 3) C4723](../../error-messages/compiler-warnings/compiler-warning-level-3-c4723.md)|0 나누기 연산이 발생할 수|
|컴파일러 경고 (수준 3) C4724|0의 나머지 연산이 발생할 수 있습니다.|
|컴파일러 경고 (수준 3) C4725|명령이 일부 Pentium에서 정확하지 않을 수 있습니다.|
|[컴파일러 경고(수준 1) C4727](../../error-messages/compiler-warnings/compiler-warning-level-1-c4727.md)|Pch pch_file obj_file_1 및 obj_file_2에 타임 스탬프가 동일한가 있습니다.  첫 번째 PCH를 사용합니다.|
|컴파일러 경고 (수준 1) C4728|/Yl-옵션이 PCH 참조가 필요 하기 때문에 무시 됩니다.|
|컴파일러 경고 (수준 4) C4729|선형 그래프 기반 경고에 사용하기에는 함수가 너무 큽니다.|
|[컴파일러 경고 (수준 1) C4730](../../error-messages/compiler-warnings/compiler-warning-level-1-c4730.md)컴파일러 경고 (수준 1) C4730|'main': _m64 혼합 및 부동 소수점에 잘못 된 코드 식으로 인해 수|
|[컴파일러 경고(수준 1) C4731](../../error-messages/compiler-warnings/compiler-warning-level-1-c4731.md)|'pointer': 프레임 포인터 레지스터가 인라인 어셈블리 코드에 의해 수정 '등록'|
|컴파일러 경고 (수준 1) C4732|이 아키텍처에서 내장 함수 '%s'를 사용할 수 없습니다.|
|[컴파일러 경고(수준 1) C4733](../../error-messages/compiler-warnings/compiler-warning-level-1-c4733.md)|인라인 asm 'fs: 0'에 할당: 처리기 안전한 처리기로 등록 되지 않았습니다|
|[컴파일러 경고(수준 3) C4738](../../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md)|32비트 float 결과를 메모리에 저장하면 성능이 저하될 수 있습니다.|
|컴파일러 경고 (수준 1) C4739|'var' 변수에 대한 참조가 저장 공간을 초과합니다.|
|[컴파일러 경고(수준 4) C4740](../../error-messages/compiler-warnings/compiler-warning-level-4-c4740.md)|내부 / 외부로 인라인 asm 코드 흐름을 선택 하면 전역 최적화|
|[컴파일러 경고(수준 1) C4742](../../error-messages/compiler-warnings/compiler-warning-level-1-c4742.md)|'var'에 'file1' 및 'file2'에서 서로 다른 맞춤: 번호와 번호|
|[컴파일러 경고(수준 1) C4743](../../error-messages/compiler-warnings/compiler-warning-level-1-c4743.md)|'type'에 'file1' 및 'file2'에서 다른 크기: 수와 바이트 수입니다.|
|[컴파일러 경고(수준 1) C4744](../../error-messages/compiler-warnings/compiler-warning-level-1-c4744.md)|'var'의 'file1' 및 'file2'에서 형식이 다릅니다.: 'type1' 및 'type2'|
|[컴파일러 경고 C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md)|volatile 액세스 '*식*' /volatile:\<iso&#124;ms > __iso_volatile_load/store 내장 함수를 사용 하 여 고려 설정;|
|[컴파일러 경고(수준 1) C4747](../../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md)|관리 되는 '진입점' 호출: DLL 진입점 및 DLL 진입점에서 접근 하는 호출을 포함 하 여 로더 잠금 상태에서 관리 되는 코드는 실행 되지 않을 수 있습니다|
|컴파일러 경고 (수준 4) C4749|조건에 따라 지원: non standard-레이아웃 형식에 적용 된 offsetof '*형식*'|
|컴파일러 경고 (수준 1) C4750|'identifier': 루프에 인라이닝된 _alloca()를 사용하는 함수|
|컴파일러 경고 (수준 4) C4751|/arch: avx intel (r) 스트리밍 SIMD 확장 인라인 ASM 내에 있는에 적용 되지 않습니다.|
|컴파일러 경고 (수준 4) C4752|intel (r) Advanced Vector Extensions;를 찾을 수합니다 /arch: avx를 사용 하는 것이 좋습니다.|
|컴파일러 경고 (수준 4) C4754|분기 하나를 실행할 수 없음을 의미 하는 %에서 비교에 사용 된 산술 연산의 변환 규칙입니다. '%S' '%s' (또는 비슷한 형식의 %d 바이트) 캐스팅 합니다.|
|컴파일러 경고 C4755|%에서 비교에 사용 된 산술 연산의 변환 규칙 인라인 된 함수에서 분기 하나를 실행할 수 없음을 의미 합니다. '%S' '%s' (또는 비슷한 형식의 %d 바이트) 캐스팅 합니다.|
|[컴파일러 경고(수준 2) C4756](../../error-messages/compiler-warnings/compiler-warning-level-2-c4756.md)|상수 산술 연산에서 오버플로가 발생 했습니다.|
|컴파일러 경고 (수준 4) C4757|첨자는 부호 없는 큰 값, 음의 상수가 사용 하려고 했습니까?|
|컴파일러 경고 (수준 4) C4764|16 바이트를 초과 하도록 catch 개체를 맞출 수 없습니다.|
|컴파일러 경고 (수준 4) C4767|섹션 이름 '%s'이 8 자 보다 긴 및 링커에서 잘립니다.|
|컴파일러 경고 (수준 3) C4768|링크 사양이 이전 __declspec 특성이 무시 됩니다.|
|컴파일러 경고 C4770|enum 유효성을 부분적으로 검사 '*이름*' 인덱스로 사용|
|컴파일러 경고 C4771|범위는 단순한 포인터를 사용 하 여 만들어야 무시 MPX 내장 함수|
|[컴파일러 경고 (수준 1, 오류) C4772](../../error-messages/compiler-warnings/compiler-warning-level-1-c4772.md)|#import; 누락 된 형식 라이브러리에서 형식을 참조 했습니다. 자리 표시자로 사용 되는 ' missing_type'|
|컴파일러 경고 (수준 4) C4774|'*문자열*': 서식 문자열 인수에 필요한 *번호* 이 문자열 리터럴|
|컴파일러 경고 (수준 3) C4775|형식 문자열에 사용 되는 비표준 확장 '*문자열*'함수의'*함수*'|
|컴파일러 경고 (수준 1) C4776|' %*문자*'함수의 서식 문자열에서 허용 되지 않는'*함수*'|
|컴파일러 경고 (수준 4) C4777|'*함수*': 서식 문자열 '*문자열*'형식의 인수를 사용 해야'*type1*', 하지만 variadic 인수 *번호* 형식이 '*type2*'|
|컴파일러 경고 (수준 3) C4778|'*함수*': 서식 문자열을 종결 되지 않은 '*문자열*'|
|[컴파일러 경고(수준 1) C4788](../../error-messages/compiler-warnings/compiler-warning-level-1-c4788.md)|'identifier': 식별자 'number' 자로 잘렸습니다.|
|[컴파일러 경고(수준 1) C4789](../../error-messages/compiler-warnings/compiler-warning-level-1-c4789.md)|버퍼 'identifier'(크기: N바이트)이(가) 오버런됩니다. M바이트가 오프셋 L부터 쓰입니다.|
|컴파일러 경고 (수준 2) C4792|'%s' 함수가 sysimport를 사용 하 여 선언 및; 네이티브 코드에서 참조 연결 하는 데 필요한 가져오기 라이브러리|
|[컴파일러 경고(수준 1 및 3) C4793](../../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md)|'function': 네이티브: \n\t'reason으로 컴파일된 함수 '|
|컴파일러 경고 (수준 1) C4794|스레드 로컬 저장소 변수 '%s' '%s'에서 '%s'로 변경 된의 세그먼트|
|[컴파일러 경고(수준 1) C4799](../../error-messages/compiler-warnings/compiler-warning-level-1-c4799.md)|'function' 함수에 EMMS 명령이 없습니다.|