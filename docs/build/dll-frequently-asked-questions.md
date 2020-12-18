---
description: '자세한 정보: DLL 관련 질문과 대답'
title: MFC DLL 관련 질문과 대답
ms.date: 05/06/2019
helpviewer_keywords:
- troubleshooting [C++], DLLs
- DLLs [C++], frequently asked questions
- FAQs [C++], DLLs
ms.assetid: 09dd068e-fc33-414e-82f7-289c70680256
ms.openlocfilehash: 501ec5cb5c5a8f4993e4f54e5d0434e31a26af9e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97156712"
---
# <a name="dll-frequently-asked-questions"></a>DLL 관련 질문과 대답

다음은 DLL과 관련된 몇 가지 FAQ(질문과 대답)입니다.

- [MFC DLL은 여러 스레드를 만들 수 있습니까?](#mfc_multithreaded_1)

- [다중 스레드 애플리케이션이 서로 다른 스레드에서 MFC DLL에 액세스할 수 있습니까?](#mfc_multithreaded_2)

- [MFC DLL에서 사용할 수 없는 MFC 클래스 또는 함수가 있습니까?](#mfc_prohibited_classes)

- [로드 시 클라이언트 애플리케이션의 성능을 향상시키려면 어떤 최적화 기법을 사용해야 합니까?](#mfc_optimization)

- [일반 MFC DLL에는 메모리 누수가 있지만 코드는 정상으로 보입니다. 메모리 누수를 어떻게 찾을 수 있나요?](#memory_leak)

## <a name="can-an-mfc-dll-create-multiple-threads"></a><a name="mfc_multithreaded_1"></a> MFC DLL은 여러 스레드를 만들 수 있습니까?

초기화 도중을 제외하고, MFC DLL은 **TlsAlloc** 같은 Win32 TLS(스레드 로컬 스토리지) 함수를 사용하여 스레드 로컬 스토리지를 할당하는 동안 안전하게 여러 스레드를 만들 수 있습니다. 그러나 MFC DLL이 **`__declspec(thread)`** 을 사용하여 스레드 로컬 스토리지를 할당하는 경우 클라이언트 애플리케이션은 DLL에 암시적으로 연결되어야 합니다. 클라이언트 애플리케이션이 DLL에 명시적으로 연결하는 경우 **LoadLibrary** 를 호출하면 DLL이 성공적으로 로드되지 않습니다. DLL의 스레드 로컬 변수에 대한 자세한 내용은 [스레드](../cpp/thread.md)를 참조하세요.

시작하는 동안 새 MFC 스레드를 만드는 MFC DLL은 애플리케이션에 의해 로드될 때 응답을 중지합니다. 여기에는 다음 내부에서 `AfxBeginThread` 또는 `CWinThread::CreateThread`를 호출하여 스레드를 만드는 경우가 모두 포함됩니다.

- 일반 MFC DLL의 `CWinApp` 파생 개체의 `InitInstance`.

- 일반 MFC DLL의 제공된 `DllMain` 또는 **RawDllMain** 함수.

- MFC 확장 DLL의 제공된 `DllMain` 또는 **RawDllMain** 함수.

## <a name="can-a-multithreaded-application-access-an-mfc-dll-in-different-threads"></a><a name="mfc_multithreaded_2"></a> 다중 스레드 애플리케이션이 서로 다른 스레드에서 MFC DLL에 액세스할 수 있습니까?

다중 스레드 애플리케이션은 여러 스레드에서 MFC 및 MFC 확장 DLL에 동적으로 연결하는 일반 MFC DLL에 액세스할 수 있습니다. 애플리케이션은 애플리케이션이 만든 여러 스레드에서 정적으로 MFC에 링크하는 일반 MFC DLL에 액세스할 수 있습니다.

## <a name="are-there-any-mfc-classes-or-functions-that-cannot-be-used-in-an-mfc-dll"></a><a name="mfc_prohibited_classes"></a> MFC DLL에서 사용할 수 없는 MFC 클래스 또는 함수가 있습니까?

확장 DLL은 클라이언트 애플리케이션의 `CWinApp` 파생 클래스를 사용합니다. 자체 `CWinApp` 파생 클래스가 없어야 합니다.

기본 MFC DLL에는 MFC 애플리케이션과 마찬가지로 `CWinApp` 파생 클래스와 해당 애플리케이션 클래스의 단일 개체가 있어야 합니다. 애플리케이션의 `CWinApp` 개체와 달리 DLL의 `CWinApp` 개체는 기본 메시지 펌프를 포함하지 않습니다.

`CWinApp::Run` 메커니즘이 DLL에 적용되지 않기 때문에 애플리케이션은 주 메시지 펌프를 소유합니다. DLL이 모덜리스 대화 상자를 열거나 자체의 주 프레임 창이 있으면 애플리케이션의 기본 메시지 펌프는 DLL에서 내보낸 루틴을 호출해야 하고, 이 루틴은 다시 DLL의 애플리케이션 개체의 `CWinApp::PreTranslateMessage` 멤버 함수를 호출합니다.

## <a name="what-optimization-techniques-should-i-use-to-improve-the-client-application39s-performance-when-loading"></a><a name="mfc_optimization"></a> 로드 시 클라이언트 애플리케이션의 성능을 향상시키려면 어떤 최적화 기법을 사용해야 합니까?

DLL이 정적으로 MFC에 연결된 일반 MFC DLL인 경우 동적으로 MFC에 연결된 일반 MFC DLL로 변경하면 파일 크기가 줄어듭니다.

DLL에 내보낸 함수가 많은 경우 **`__declspec(dllexport)`** 을 사용하는 대신 .def 파일을 사용하여 함수를 내보내고, 각 내보낸 함수에 .def 파일 [NONAME 특성](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)을 사용합니다. NONAME 특성은 함수 이름이 아닌 서수 값만 DLL의 내보내기 테이블에 저장되게 하므로 파일 크기가 줄어듭니다.

애플리케이션에 암시적으로 연결된 DLL은 애플리케이션이 로드될 때 로드됩니다. 로드 성능을 향상시키려면 DLL을 여러 DLL로 분할해 보세요. 로드 후 호출 애플리케이션에 즉시 필요한 모든 함수를 한 DLL에 배치하고 호출 애플리케이션이 해당 DLL에 암시적으로 연결되도록 합니다. 호출 애플리케이션에 즉시 필요하지 않은 다른 함수를 다른 DLL에 배치하고 애플리케이션이 해당 DLL에 명시적으로 연결되도록 합니다. 자세한 내용은 [DLL에 실행 파일 연결](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)을 참조하세요.

## <a name="there39s-a-memory-leak-in-my-regular-mfc-dll-but-my-code-looks-fine-how-can-i-find-the-memory-leak"></a><a name="memory_leak"></a> 일반 MFC DLL에는 메모리 누수가 있지만 코드는 정상으로 보입니다. 메모리 누수를 어떻게 찾을 수 있나요?

메모리 누수의 가능한 원인 한 가지는 MFC가 메시지 처리기 함수 내에서 사용되는 임시 개체를 만들기 때문입니다. MFC 애플리케이션에서 이러한 임시 개체는 처리 메시지 사이에서 호출되는 `CWinApp::OnIdle()` 함수에서 자동으로 정리됩니다. 그러나 MFC DLL(동적 연결 라이브러리)에서는 `OnIdle()` 함수가 자동으로 호출되지 않습니다. 따라서 임시 개체가 자동으로 정리되지 않습니다. 임시 개체를 정리하려면 DLL이 정기적으로 `OnIdle(1)`를 명시적으로 호출해야 합니다.

## <a name="see-also"></a>참조

[Visual Studio에서 C/C++ DLL 만들기](dlls-in-visual-cpp.md)
