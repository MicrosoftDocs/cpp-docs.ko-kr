---
description: '자세한 정보: MFC의 예외 처리'
title: MFC의 예외 처리
ms.date: 11/19/2019
helpviewer_keywords:
- DAO [MFC], exceptions
- assertions [MFC], When to use exceptions
- exception handling [MFC], MFC
- resource allocation exception
- resources [MFC], allocating
- keywords [MFC], exception handling
- errors [MFC], detected by assertions
- ODBC exceptions [MFC]
- serialization [MFC], exceptions
- Automation [MFC], exceptions
- exception macros [MFC]
- predefined exceptions [MFC]
- C++ exception handling [MFC], enabling
- C++ exception handling [MFC], MFC applications
- requests for unsupported services [MFC]
- database exceptions [MFC]
- archive exceptions [MFC]
- MFC, exceptions
- C++ exception handling [MFC], types of
- macros [MFC], exception handling
- abnormal program execution [MFC]
- OLE exceptions [MFC], MFC exception handling
- error handling [MFC], exceptions and
- class libraries [MFC], exception support
- exceptions [MFC], MFC macros vs. C++ keywords
- memory [MFC], out-of-memory exceptions
- Windows [MFC], resource allocation exceptions
- macros [MFC], MFC exception macros
- function calls [MFC], results
- out-of-memory exceptions [MFC]
ms.assetid: 0926627d-2ba7-44a6-babe-d851a4a2517c
ms.openlocfilehash: 15b0a054d3b1c0353c60c1c8dda03c9e704c077e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97290754"
---
# <a name="exception-handling-in-mfc"></a>MFC의 예외 처리

이 문서에서는 MFC에서 사용할 수 있는 예외 처리 메커니즘에 대해 설명 합니다. 다음 두 가지 메커니즘을 사용할 수 있습니다.

- C + + 예외 (MFC 버전 3.0 이상에서 사용 가능)

- Mfc 예외 매크로 (MFC 버전 1.0 이상에서 사용 가능)

MFC를 사용 하 여 새 응용 프로그램을 작성 하는 경우 c + + 메커니즘을 사용 해야 합니다. 기존 응용 프로그램에서 이미 해당 메커니즘을 광범위 하 게 사용 하는 경우 매크로 기반 메커니즘을 사용할 수 있습니다.

MFC 예외 매크로 대신 c + + 예외를 사용 하도록 기존 코드를 쉽게 변환할 수 있습니다. 코드를 변환 하는 경우의 이점 및이에 대 한 지침은 [예외: MFC 예외 매크로에서 변환](exceptions-converting-from-mfc-exception-macros.md)문서에 설명 되어 있습니다.

MFC 예외 매크로를 사용 하 여 응용 프로그램을 이미 개발한 경우 새 코드에서 c + + 예외를 사용 하 여 기존 코드에서 이러한 매크로를 계속 사용할 수 있습니다. 문서 [예외: 버전 3.0의 예외 매크로 변경 내용](exceptions-changes-to-exception-macros-in-version-3-0.md) 에 대 한 지침을 제공 합니다.

> [!NOTE]
> 코드에서 c + + 예외 처리를 사용 하도록 설정 하려면 프로젝트의 [속성 페이지](../build/reference/property-pages-visual-cpp.md) 대화 상자에서 c/c + + 폴더의 코드 생성 페이지에서 c + + 예외 사용을 선택 하거나 [/ehsc](../build/reference/eh-exception-handling-model.md) 컴파일러 옵션을 사용 합니다.

이 문서는 다음 항목을 설명합니다.

- [예외 사용 시기](#_core_when_to_use_exceptions)

- [MFC 예외 지원](#_core_mfc_exception_support)

- [예외에 대 한 추가 정보](#_core_further_reading_about_exceptions)

## <a name="when-to-use-exceptions"></a><a name="_core_when_to_use_exceptions"></a> 예외를 사용 하는 경우

프로그램 실행 중에 함수가 호출 되는 경우 (일반적인 실행, 잘못 된 실행 또는 비정상적인 실행) 세 가지 범주의 결과가 발생할 수 있습니다. 각 범주는 아래에 설명 되어 있습니다.

- 일반 실행

   함수는 정상적으로 실행 되 고를 반환할 수 있습니다. 일부 함수는 결과 코드를 호출자에 게 반환 하며,이는 함수의 결과를 나타냅니다. 가능한 결과 코드는 함수에 대해 엄격 하 게 정의 되며 함수의 가능한 결과 범위를 나타냅니다. 결과 코드는 성공 또는 실패를 나타내거나 일반적인 예상 범위 내에 있는 특정 유형의 오류를 나타낼 수도 있습니다. 예를 들어 파일 상태 함수는 파일이 없다는 것을 나타내는 코드를 반환할 수 있습니다. 결과 코드는 예상 되는 많은 결과 중 하나를 나타내므로 "오류 코드" 라는 용어는 사용 되지 않습니다.

- 잘못 실행

   호출자는 함수에 인수를 전달 하거나 적절 하지 않은 컨텍스트에서 함수를 호출 하는 실수를 발생 시킬 수 있습니다. 이 경우 오류가 발생 하 고 프로그램 개발 중 어설션이 어설션에 의해 검색 됩니다. 어설션에 대 한 자세한 내용은 [C/c + + 어설션](/visualstudio/debugger/c-cpp-assertions)(영문)을 참조 하세요.

- 비정상적인 실행

   비정상적인 실행에는 메모리 부족 또는 i/o 오류와 같은 프로그램 제어 외부의 조건이 함수의 결과에 영향을 주는 경우가 포함 됩니다. 예외를 catch 하 고 throw 하 여 비정상적인 상황을 처리 해야 합니다.

예외를 사용 하는 것은 비정상적인 실행에 특히 적합 합니다.

## <a name="mfc-exception-support"></a><a name="_core_mfc_exception_support"></a> MFC 예외 지원

C + + 예외를 직접 사용 하거나 MFC 예외 매크로를 사용 하는 경우에 [](reference/cexception-class.md) 는 `CException` 프레임 워크 또는 응용 프로그램에서 throw 될 수 있는 cexception 클래스 또는 파생 개체를 사용 합니다.

다음 표에서는 MFC에서 제공 하는 미리 정의 된 예외를 보여 줍니다.

|Exception 클래스|의미|
|---------------------|-------------|
|[CMemoryException 클래스](reference/cmemoryexception-class.md)|메모리 부족|
|[CFileException 클래스](reference/cfileexception-class.md)|파일 예외|
|[CArchiveException 클래스](reference/carchiveexception-class.md)|보관/Serialization 예외|
|[CNotSupportedException 클래스](reference/cnotsupportedexception-class.md)|지원 되지 않는 서비스 요청에 대 한 응답|
|[CResourceException 클래스](reference/cresourceexception-class.md)|Windows 리소스 할당 예외|
|[CDaoException 클래스](reference/cdaoexception-class.md)|데이터베이스 예외 (DAO 클래스)|
|[CDBException 클래스](reference/cdbexception-class.md)|데이터베이스 예외 (ODBC 클래스)|
|[COleException 클래스](reference/coleexception-class.md)|OLE 예외|
|[COleDispatchException 클래스](reference/coledispatchexception-class.md)|디스패치 (자동화) 예외|
|[CUserException 클래스](reference/cuserexception-class.md)|메시지 상자를 사용 하 여 사용자에 게 경고 한 다음 일반 [Cexception 클래스](reference/cexception-class.md) 를 throw 하는 예외입니다.|

버전 3.0 이상에서는 MFC가 C++ 예외를 사용했으나 형식에서 C++ 예외와 유사한 이전 예외 처리 매크로를 여전히 지원합니다. 이러한 매크로는 새 프로그래밍에는 권장되지 않지만 여전히 역 호환성에 대해 지원됩니다. 매크로를 이미 사용하는 프로그램에서 자유롭게 C++ 예외를 사용할 수 있습니다. 전처리 하는 동안 매크로는 Visual C++ 버전 2.0에서 c + + 언어의 MSVC 구현에 정의 된 예외 처리 키워드로 평가 됩니다. C++ 예외를 사용하는 동안 기존 예외 매크로를 남겨둘 수 있습니다. 매크로와 c + + 예외 처리를 혼합 하 고 새 메커니즘을 사용 하기 위해 이전 코드를 변환 하는 방법에 대 한 자세한 내용은 [예외: Mfc 매크로 사용 및 c + + 예외](exceptions-using-mfc-macros-and-cpp-exceptions.md) 및 [예외: mfc 예외 매크로에서 변환](exceptions-converting-from-mfc-exception-macros.md)문서를 참조 하세요. 이전 MFC 예외 매크로를 계속 사용하는 경우 C++ 예외 키워드로 평가합니다. [예외: 버전 3.0의 예외 매크로에 대 한 변경 내용을](exceptions-changes-to-exception-macros-in-version-3-0.md)참조 하세요. MFC는 [구조적 예외 처리](/windows/win32/debug/structured-exception-handling)에 설명 된 대로 WINDOWS NT SEH (구조적 예외 처리기)를 직접 지원 하지 않습니다.

## <a name="further-reading-about-exceptions"></a><a name="_core_further_reading_about_exceptions"></a> 예외에 대 한 추가 정보

다음 문서에서는 예외 처리를 위해 MFC 라이브러리를 사용 하는 방법을 설명 합니다.

- [예외: 예외 Catch 및 삭제](exceptions-catching-and-deleting-exceptions.md)

- [예외: 예외 내용 검사](exceptions-examining-exception-contents.md)

- [예외: 예외의 개체 해제](exceptions-freeing-objects-in-exceptions.md)

- [예외: 자체 함수에서 예외 Throw](exceptions-throwing-exceptions-from-your-own-functions.md)

- [예외: 데이터베이스 예외](exceptions-database-exceptions.md)

- [예외: OLE 예외](exceptions-ole-exceptions.md)

다음 문서에서는 c + + 예외 키워드와 MFC 예외 매크로를 비교 하 고 코드를 조정 하는 방법을 설명 합니다.

- [예외: 버전 3.0의 예외 매크로에 대 한 변경 내용](exceptions-changes-to-exception-macros-in-version-3-0.md)

- [예외: MFC 예외 매크로에서 변환](exceptions-converting-from-mfc-exception-macros.md)

- [예외: MFC 매크로 및 c + + 예외 사용](exceptions-using-mfc-macros-and-cpp-exceptions.md)

## <a name="see-also"></a>참고 항목

[예외 및 오류 처리에 대 한 최신 c + + 모범 사례](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[방법: 고유한 사용자 지정 예외 클래스 만들기](https://go.microsoft.com/fwlink/p/?linkid=128045)
