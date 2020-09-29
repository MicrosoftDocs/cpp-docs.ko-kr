---
title: C++의 최선의 보안 구현 방법
ms.date: 05/08/2018
f1_keywords:
- securitybestpracticesVC
helpviewer_keywords:
- Visual C++, security
- security [C++]
- security [C++], best practices
ms.assetid: 86acaccf-cdb4-4517-bd58-553618e3ec42
ms.openlocfilehash: 63c5567cf1b06d52aa4b458a9ca127039e5c5daf
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499592"
---
# <a name="security-best-practices-for-c"></a>C++의 최선의 보안 구현 방법

이 문서에는 보안 도구와 구현 방법에 대한 정보가 포함되어 있습니다. 이러한 정보를 사용해도 애플리케이션이 공격으로부터 완전히 보호되는 것은 아니지만 공격 성공 가능성이 줄어듭니다.

## <a name="visual-c-security-features"></a>Visual C++ 보안 기능

이러한 보안 기능은 Microsoft c + + 컴파일러 및 링커에 기본 제공 됩니다.

[`/guard` (제어 흐름 보호 사용)](../build/reference/guard-enable-control-flow-guard.md)<br/>
컴파일러가 컴파일 시간에 간접 호출 대상에 대 한 제어 흐름을 분석 한 다음 런타임에 대상을 확인 하는 코드를 삽입 합니다.

[`/GS` (버퍼 보안 검사)](../build/reference/gs-buffer-security-check.md)<br/>
악용될 위험이 있는 함수에 오버런 감지 코드를 삽입하도록 컴파일러에 지시합니다. 오버런이 감지되면 실행이 중지됩니다. 이 옵션은 기본적으로 켜져 있습니다.

[`/SAFESEH` (이미지에 안전한 예외 처리기 포함)](../build/reference/safeseh-image-has-safe-exception-handlers.md)<br/>
각 예외 처리기의 주소를 포함하는 테이블을 출력 이미지에 포함하도록 링커에 지시합니다. 런타임에 운영 체제는 이 테이블을 사용하여 적합한 예외 처리기만 실행되도록 합니다. 이렇게 하면 런타임에 악의적인 공격에 의한 예외 처리기 실행을 방지하는 데 도움이 됩니다. 이 옵션은 기본적으로 해제되어 있습니다.

[`/NXCOMPAT`](../build/reference/nxcompat.md)[ `/NXCOMPAT` (데이터 실행 방지와 호환 됨)](../build/reference/nxcompat-compatible-with-data-execution-prevention.md) 이러한 컴파일러 및 링커 옵션을 사용 하면 DEP (데이터 실행 방지) 호환성이 가능 합니다. DEP는 비코드 페이지 실행에 대해 CPU를 보호합니다.

[`/analyze` (코드 분석)](../build/reference/analyze-code-analysis.md)<br/>
이 컴파일러 옵션은 버퍼 오버런, 초기화되지 않은 메모리, null 포인터 역참조 및 메모리 누수와 같은 잠재적인 보안 문제를 보고하는 코드 분석을 활성화합니다. 이 옵션은 기본적으로 해제되어 있습니다. 자세한 내용은 [c/c + + 용 코드 분석 개요](../code-quality/code-analysis-for-c-cpp-overview.md)를 참조 하세요.

[`/DYNAMICBASE` (주소 공간 레이아웃의 임의 사용)](../build/reference/dynamicbase-use-address-space-layout-randomization.md)<br/>
이 링커 옵션은 실행을 시작할 때 메모리의 다른 위치에 로드될 수 있는 실행 가능한 이미지를 작성할 수 있게 합니다. 또한 이 옵션을 사용하면 메모리의 스택 위치를 예측하기가 훨씬 어렵습니다.

## <a name="security-enhanced-crt"></a>보안이 강화된 CRT

확인되지 않은 `strcpy` 문자열 복사 함수와 같이 보안 문제가 발생할 수 있는 함수의 보안 버전을 포함하도록 CRT(C 런타임 라이브러리)가 강화되었습니다. 이러한 함수의 보안되지 않은 이전 버전은 사용되지 않으므로 컴파일 시간 경고가 발생합니다. 컴파일 경고가 표시되지 않도록 하는 대신 이러한 CRT 함수의 보안 버전을 사용하는 것이 좋습니다. 자세한 내용은 [CRT의 보안 기능](../c-runtime-library/security-features-in-the-crt.md)을 참조하세요.

## <a name="safeint-library"></a>SafeInt 라이브러리

[SafeInt 라이브러리](../safeint/safeint-library.md) 는 응용 프로그램에서 수학적 작업을 수행할 때 발생할 수 있는 정수 오버플로 및 기타 악용 가능 오류를 방지 하는 데 도움이 됩니다. `SafeInt`라이브러리는 [SafeInt 클래스](../safeint/safeint-class.md), [safeintexception 클래스](../safeint/safeintexception-class.md)및 몇 가지 [SafeInt 함수](../safeint/safeint-functions.md)를 포함 합니다.

`SafeInt` 클래스는 정수 오버플로 및 0으로 나누기 악용으로부터 보호합니다. 서로 다른 형식의 값 간의 비교를 처리하는 데 사용할 수 있습니다. 이 클래스는 두 가지 오류 처리 정책을 제공 합니다. 기본 정책은 `SafeInt` 클래스가 `SafeIntException` 클래스 예외를 발생시켜 산술 연산을 완료할 수 없는 이유를 보고하기 위한 것입니다. 두 번째 정책은 `SafeInt` 클래스가 프로그램 실행을 중지하기 위한 것입니다. 사용자 지정 정책을 정의할 수도 있습니다.

각 `SafeInt` 함수는 악용 가능한 오류로부터 하나의 산술 연산을 보호합니다. 동일한 형식으로 변환하지 않고 두 가지 종류의 매개 변수를 사용할 수 있습니다. 여러 개의 산술 연산을 보호하려면 `SafeInt` 클래스를 사용합니다.

## <a name="checked-iterators"></a>Checked Iterators

확인된 반복기는 컨테이너 경계를 적용합니다. 기본적으로 확인된 반복기는 범위를 벗어날 경우 예외를 생성하고 프로그램 실행을 종료합니다. 확인 된 반복기는 및와 같은 전처리기 정의에 할당 된 값에 따라 달라 지는 다른 수준의 응답을 제공 합니다 `_SECURE_SCL_THROWS` `_ITERATOR_DEBUG_LEVEL` . 예를 들어에서 `_ITERATOR_DEBUG_LEVEL=2` 확인 된 반복기는 어설션을 사용 하 여 사용할 수 있는 디버그 모드에서 포괄적인 정확성 검사를 제공 합니다. 자세한 내용은 [확인 된 반복기](../standard-library/checked-iterators.md) 및를 참조 하세요 [`_ITERATOR_DEBUG_LEVEL`](../standard-library/iterator-debug-level.md) .

## <a name="code-analysis-for-managed-code"></a>관리 코드에 대한 코드 분석

관리 코드에 대한 코드 분석은 FxCop라고도 하며, 어셈블리에서 .NET Framework 디자인 지침을 준수하는지 검사합니다. FxCop는 각 어셈블리의 코드 및 메타데이터를 분석하여 다음 영역에 결함이 있는지 검사합니다.

- 라이브러리 디자인

- 지역화

- 명명 규칙

- 성능

- 보안

## <a name="windows-application-verifier"></a>Windows 애플리케이션 검증 도구

[애플리케이션 검증 도구 (AppVerifier)](/windows-hardware/drivers/debugger/enable-application-verifier) 는 잠재적 응용 프로그램 호환성, 안정성 및 보안 문제를 식별 하는 데 도움이 될 수 있습니다.

AppVerifier는 애플리케이션에서 운영 체제를 사용하는 방식을 모니터링합니다. 애플리케이션이 실행되는 동안 파일 시스템, 레지스트리, 메모리 및 API를 감시하고 발견된 문제에 대한 소스 코드 수정을 권장합니다.

AppVerifier를 사용하여 다음 작업을 수행할 수 있습니다.

- 일반적인 프로그래밍 실수로 인해 발생하는 잠재적인 애플리케이션 호환성 오류를 테스트합니다.

- 애플리케이션에서 메모리 관련 문제를 검사합니다.

- 애플리케이션에서 잠재적인 보안 문제를 식별합니다.

## <a name="windows-user-accounts"></a>Windows 사용자 계정

Administrators 그룹에 속하는 Windows 사용자 계정을 사용하면 개발자 및 확장에 의해 고객이 보안 위험에 노출됩니다. 자세한 내용은 [사용자 그룹의 구성원으로 실행](running-as-a-member-of-the-users-group.md) 및 [UAC (사용자 계정 컨트롤)가 응용 프로그램에 미치는 영향](how-user-account-control-uac-affects-your-application.md)을 참조 하세요.

## <a name="guidance-for-speculative-execution-side-channels"></a>잘못 실행 측 채널에 대 한 지침

C + + 소프트웨어의 잘못 실행 측 채널 하드웨어 취약점을 식별할 하 고 완화 하는 방법에 대 한 자세한 내용은 [추론 실행 측 채널에 대 한 c + + 개발자 지침](developer-guidance-speculative-execution.md)을 참조 하세요.

## <a name="see-also"></a>참조

<xref:System.Security> <br/>
[보안](/dotnet/standard/security/index)<br/>
[UAC (사용자 계정 컨트롤)가 응용 프로그램에 미치는 영향](how-user-account-control-uac-affects-your-application.md)
