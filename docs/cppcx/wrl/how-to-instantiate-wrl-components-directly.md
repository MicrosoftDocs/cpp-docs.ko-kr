---
description: '자세히 알아보기: 방법: WRL 구성 요소 직접 인스턴스화'
title: '방법: 직접 WRL 구성 요소 인스턴스화'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1a9fa011-0cee-4abf-bf83-49adf53ff906
ms.openlocfilehash: 424b3ec70921de9558fd8c5035e96b2fe4d58f7b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97249895"
---
# <a name="how-to-instantiate-wrl-components-directly"></a>방법: 직접 WRL 구성 요소 인스턴스화

WRL (c + + 템플릿 라이브러리)[Microsoft:: WRL::](make-function.md) 및 [MICROSOFT:: WRL::D Etails:: makeandinitialize](makeandinitialize-function.md) 함수를 Windows 런타임 사용 하 여 구성 요소를 정의 하는 모듈에서 구성 요소를 인스턴스화하는 방법에 대해 알아봅니다.

구성 요소를 직접 인스턴스화하면 클래스 팩터리 또는 다른 메커니즘이 필요 하지 않을 때 오버 헤드를 줄일 수 있습니다. 유니버설 Windows 플랫폼 apps와 데스크톱 앱에서 구성 요소를 직접 인스턴스화할 수 있습니다.

Windows 런타임 c + + 템플릿 라이브러리를 사용 하 여 클래식 COM 구성 요소를 만들고 외부 데스크톱 앱에서 인스턴스화하는 방법에 대해 알아보려면 [방법: 클래식 Com 구성 요소 만들기](how-to-create-a-classic-com-component-using-wrl.md)를 참조 하세요.

이 문서에서는 두 가지 예를 보여 줍니다. 첫 번째 예제에서는 함수를 사용 하 여 `Make` 구성 요소를 인스턴스화합니다. 두 번째 예제에서는 함수를 사용 하 여 `MakeAndInitialize` 생성 중에 실패할 수 있는 구성 요소를 인스턴스화합니다. COM은 일반적으로 예외 대신 HRESULT 값을 사용 하 여 오류를 나타내므로 COM 형식은 일반적으로 해당 생성자에서 throw 되지 않습니다. `MakeAndInitialize` 구성 요소가 메서드를 통해 해당 생성 인수의 유효성을 검사할 수 있도록 `RuntimeClassInitialize` 합니다. 두 예제 모두 기본로 거 인터페이스를 정의 하 고 메시지를 콘솔에 쓰는 클래스를 정의 하 여 해당 인터페이스를 구현 합니다.

> [!IMPORTANT]
> 연산자를 사용 `new` 하 여 Windows 런타임 c + + 템플릿 라이브러리 구성 요소를 인스턴스화할 수 없습니다. 따라서 항상 또는를 사용 하 여 `Make` 구성 요소를 직접 인스턴스화하는 것이 좋습니다 `MakeAndInitialize` .

### <a name="to-create-and-instantiate-a-basic-logger-component"></a>기본로 거 구성 요소를 만들고 인스턴스화하려면

1. Visual Studio에서 **Win32 콘솔 응용 프로그램** 프로젝트를 만듭니다. 프로젝트 이름을 *WRLLogger* 로 합니다 (예:).

2. **Midl 파일 (.idl)** 파일을 프로젝트에 추가 하 고 파일 이름을 `ILogger.idl` 지정한 후 다음 코드를 추가 합니다.

   [!code-cpp[wrl-logger-make#1](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_1.idl)]

3. 다음 코드를 사용 하 여의 내용을 바꿉니다 `WRLLogger.cpp` .

   [!code-cpp[wrl-logger-make#2](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_2.cpp)]

### <a name="to-handle-construction-failure-for-the-basic-logger-component"></a>기본로 거 구성 요소에 대 한 생성 오류를 처리 하려면

1. 다음 코드를 사용 하 여 클래스의 정의를 바꿉니다 `CConsoleWriter` . 이 버전은 전용 문자열 멤버 변수를 보유 하 고 `RuntimeClass::RuntimeClassInitialize` 메서드를 재정의 합니다. `RuntimeClassInitialize` 에 대 한 호출이 실패 하면 실패 `SHStrDup` 합니다.

   [!code-cpp[wrl-logger-makeandinitialize#1](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_3.cpp)]

2. 다음 코드를 사용 하 여의 정의를 바꿉니다 `wmain` . 이 버전은를 사용 하 여 `MakeAndInitialize` 개체를 인스턴스화하고 `CConsoleWriter` HRESULT 결과를 확인 합니다.

   [!code-cpp[wrl-logger-makeandinitialize#2](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_4.cpp)]

## <a name="see-also"></a>참고 항목

[Windows 런타임 C++ 템플릿 라이브러리(WRL)](windows-runtime-cpp-template-library-wrl.md)<br/>
[Microsoft:: WRL:: 만들기](make-function.md)<br/>
[Microsoft:: WRL::D etails:: MakeAndInitialize](makeandinitialize-function.md)
