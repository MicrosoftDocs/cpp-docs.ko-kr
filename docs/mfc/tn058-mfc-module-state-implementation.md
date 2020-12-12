---
description: 'TN058: MFC 모듈 상태 구현에 대해 자세히 알아보세요.'
title: 'TN058: MFC 모듈 상태 구현'
ms.date: 06/28/2018
helpviewer_keywords:
- thread state [MFC]
- module states [MFC], managing state data
- TN058
- MFC, managing state data
- module states [MFC], switching
- DLLs [MFC], module states
- process state [MFC]
ms.assetid: 72f5b36f-b3da-4009-a144-24258dcd2b2f
ms.openlocfilehash: c4b300b9aa184e9fa1c6cfd5a8cf668d163d85ef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214782"
---
# <a name="tn058-mfc-module-state-implementation"></a>TN058: MFC 모듈 상태 구현

> [!NOTE]
> 다음 기술 노트는 온라인 설명서에 먼저 포함되어 있었으므로 업데이트되지 않았습니다. 따라서 일부 절차 및 항목은 만료되거나 올바르지 않을 수 있습니다. 최신 정보를 보려면 온라인 설명서 색인에서 관심 있는 항목을 검색하는 것이 좋습니다.

이 기술 정보는 MFC "모듈 상태" 구문의 구현에 대해 설명 합니다. DLL 또는 OLE in-process 서버에서 MFC 공유 Dll을 사용 하는 경우 모듈 상태 구현을 이해 하는 것이 중요 합니다.

이 정보를 읽기 전에 [새 문서, 창 및 뷰 만들기](../mfc/creating-new-documents-windows-and-views.md)의 "MFC 모듈의 상태 데이터 관리"를 참조 하세요. 이 문서에는이 주제에 대 한 중요 한 사용 정보와 개요 정보가 포함 되어 있습니다.

## <a name="overview"></a>개요

MFC 상태 정보에는 모듈 상태, 프로세스 상태 및 스레드 상태의 세 가지 종류가 있습니다. 이러한 상태 유형을 결합할 수도 있습니다. 예를 들어, MFC의 핸들 맵은 모듈 로컬 및 스레드 로컬입니다. 이렇게 하면 서로 다른 두 모듈의 각 스레드에 서로 다른 맵이 있을 수 있습니다.

프로세스 상태와 스레드 상태는 유사 합니다. 이러한 데이터 항목은 일반적으로 전역 변수 이지만 적절 한 Win32s 지원 또는 적절 한 다중 스레딩 지원에 대 한 지정 된 프로세스 또는 스레드와 관련이 있어야 합니다. 지정 된 데이터 항목에 적합 한 범주는 프로세스 및 스레드 경계와 관련 하 여 해당 항목 및 원하는 의미 체계에 따라 달라 집니다.

모듈 상태는 로컬 또는 스레드 로컬 프로세스의 실제 상태 또는 상태를 포함할 수 있다는 면에서 고유 합니다. 또한 신속 하 게 전환할 수 있습니다.

## <a name="module-state-switching"></a>모듈 상태 전환

각 스레드에는 "current" 또는 "active" 모듈 상태에 대 한 포인터가 포함 되어 있습니다. 포인터는 MFC의 스레드 로컬 상태에 속합니다. 이 포인터는 실행 스레드가 OLE 컨트롤이 나 DLL로 호출 하는 응용 프로그램 또는 응용 프로그램으로 다시 호출 하는 OLE 컨트롤 등의 모듈 경계를 전달할 때 변경 됩니다.

을 호출 하 여 현재 모듈 상태를 전환 합니다 `AfxSetModuleState` . 대부분의 경우 API를 직접 처리 하지 않습니다. 대부분의 경우 MFC는 사용자를 위해 (WinMain, OLE 진입점, 등)를 호출 합니다 `AfxWndProc` . 이 작업은 특별 한 방식으로 정적으로 링크 하 여 작성 하는 모든 구성 요소에서 수행 되며 `WndProc` , `WinMain` `DllMain` 현재 상태 여야 하는 모듈 상태를 파악 하는 특수 (또는)입니다. DLLMODUL를 살펴보면이 코드를 볼 수 있습니다. CPP 또는 APPMODUL. MFC\SRC 디렉터리의 CPP.

모듈 상태를 설정 하 고 다시 설정 하지 않으려는 경우는 거의 없습니다. 대부분의 경우에는 자신의 모듈 상태를 현재 상태로 "푸시" 한 다음 완료 한 후 원래 컨텍스트를 다시 "pop" 할 수 있습니다. 매크로 [AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state) 및 특수 클래스에서이 작업을 수행 합니다 `AFX_MAINTAIN_STATE` .

`CCmdTarget` 에는 모듈 상태 전환을 지원 하기 위한 특별 한 기능이 있습니다. 특히는 `CCmdTarget` ole 자동화 및 OLE COM 진입점에 사용 되는 루트 클래스입니다. 시스템에 노출 된 다른 진입점과 마찬가지로 이러한 진입점은 올바른 모듈 상태를 설정 해야 합니다. 지정 된에서 "올바른" 모듈 상태가 무엇 인지 확인 하는 것은 "현재" 모듈 상태를 생성할 때 "기억" 하는 것입니다 .이는 `CCmdTarget` 나중에 호출 될 때 현재 모듈 상태를 "기억 됨" 값으로 설정할 수 있다는 것입니다. 따라서 지정 된 개체가 연결 된 모듈 상태는 `CCmdTarget` 개체가 생성 될 때의 현재 상태 였던 모듈 상태입니다. INPROC 서버를 로드 하 고, 개체를 만들고, 해당 메서드를 호출 하는 간단한 예제를 수행 합니다.

1. DLL은를 사용 하 여 OLE에서 로드 됩니다 `LoadLibrary` .

1. `RawDllMain` 가 먼저 호출 됩니다. 모듈 상태를 DLL의 알려진 정적 모듈 상태로 설정 합니다. 이러한 이유로 `RawDllMain` 는 DLL에 정적으로 연결 됩니다.

1. 개체와 연결 된 클래스 팩터리의 생성자가 호출 됩니다. `COleObjectFactory` 는 및에서 파생 되 `CCmdTarget` 고 그 결과로 인스턴스화된 모듈 상태를 기억 합니다. 이는 클래스 팩터리가 개체를 만들도록 요청 하는 경우 현재에 사용할 모듈 상태를 확인 하는 것이 중요 합니다.

1. `DllGetClassObject` 는 클래스 팩터리를 가져오기 위해 호출 됩니다. MFC는이 모듈과 연결 된 클래스 팩터리 목록을 검색 하 여 반환 합니다.

1. `COleObjectFactory::XClassFactory2::CreateInstance`이 호출됩니다. 이 함수는 개체를 만들기 전에이를 반환 하기 전에 3 단계에서 현재 있던 모듈 상태 (가 인스턴스화될 때의 현재 상태)로 모듈 상태를 설정 합니다 `COleObjectFactory` . [METHOD_PROLOGUE](com-interface-entry-points.md)내에서 수행 됩니다.

1. 개체를 만들 때이 개체는 파생 된 것 `CCmdTarget` 과 같은 방식으로 파생 되 고 모듈 상태가 활성 상태 인지와 동일한 방식으로 `COleObjectFactory` 이 새 개체를 수행 합니다. 이제 개체가 호출 될 때마다 전환할 모듈 상태를 알 수 있습니다.

1. 클라이언트는 호출에서 받은 OLE COM 개체에 대해 함수를 호출 `CoCreateInstance` 합니다. 개체를 호출 하면에서와 마찬가지로를 사용 하 여 `METHOD_PROLOGUE` 모듈 상태를 전환 `COleObjectFactory` 합니다.

여기에서 볼 수 있듯이 모듈 상태는 생성 될 때 개체에서 개체로 전파 됩니다. 모듈 상태를 적절 하 게 설정 하는 것이 중요 합니다. 설정 되지 않은 경우에는 DLL 또는 COM 개체가 호출 하는 MFC 응용 프로그램과 제대로 상호 작용 하거나, 자체 리소스를 찾을 수 없거나, 다른 진심으 방식으로 실패할 수 있습니다.

특정 종류의 Dll, 특히 "MFC 확장" Dll은에서 모듈 상태를 전환 하지 않습니다 `RawDllMain` (실제로는 일반적으로는 포함 되지 않음 `RawDllMain` ). 이것은 실제로이를 사용 하는 응용 프로그램에 있는 것 처럼 "동작 하는 것 처럼" 동작 하기 때문입니다. 이러한 응용 프로그램은 실행 중인 응용 프로그램의 일부 이며 응용 프로그램의 전역 상태를 수정 하려고 합니다.

OLE 컨트롤 및 기타 Dll은 매우 다릅니다. 호출 응용 프로그램의 상태를 수정 하지 않으려고 합니다. 이를 호출 하는 응용 프로그램은 MFC 응용 프로그램이 아니더라도 수정할 상태가 없을 수 있습니다. 이는 모듈 상태 전환이 고안 된 이유입니다.

Dll에서 대화 상자를 시작 하는 함수 등의 내보낸 함수는 함수 시작 부분에 다음 코드를 추가 해야 합니다.

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState())
```

현재 범위 끝까지 [AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate) 에서 반환 된 상태로 현재 모듈 상태를 바꿉니다.

Dll의 리소스 문제는 AFX_MODULE_STATE 매크로를 사용 하지 않을 경우 발생 합니다. 기본적으로 MFC는 주 응용 프로그램의 리소스 핸들을 사용 하 여 리소스 템플릿을 로드 합니다. 이 템플릿은 실제로 DLL에 저장 됩니다. 근본 원인은 MFC의 모듈 상태 정보가 AFX_MODULE_STATE 매크로로 전환 되지 않았기 때문입니다. 리소스 핸들은 MFC의 모듈 상태에서 복구 됩니다. 모듈 상태를 전환 하지 않으면 잘못 된 리소스 핸들이 사용 됩니다.

AFX_MODULE_STATE DLL의 모든 함수에 넣을 필요가 없습니다. 예를 들어는 `InitInstance` AFX_MODULE_STATE 없이 응용 프로그램의 mfc 코드에 의해 호출 될 수 있습니다 .이 경우 mfc는 먼저 모듈 상태를 자동으로 이동한 `InitInstance` 다음가 반환 된 후 다시 전환 `InitInstance` 합니다. 모든 메시지 맵 처리기의 경우에도 마찬가지입니다. 일반 MFC Dll은 메시지를 라우팅하기 전에 모듈 상태를 자동으로 전환 하는 특수 한 마스터 창 프로시저를 포함 합니다.

## <a name="process-local-data"></a>로컬 데이터 처리

로컬 데이터를 처리 하는 것이 Win32s DLL 모델의 어려움 없이 이러한 문제가 발생 하는 것은 아닙니다. Win32s에서는 여러 응용 프로그램에서 로드 한 경우에도 모든 Dll이 글로벌 데이터를 공유 합니다. 이는 각 DLL이 DLL에 연결 되는 각 프로세스에서 데이터 공간의 개별 복사본을 가져오는 "실제" Win32 DLL 데이터 모델과 매우 다릅니다. 복잡성에 추가 하기 위해 Win32s DLL의 힙에 할당 되는 데이터는 팩트 프로세스에 따라 다릅니다 (최소한 소유권이 이동 함). 다음 데이터 및 코드를 고려 합니다.

```cpp
static CString strGlobal; // at file scope

__declspec(dllexport)
void SetGlobalString(LPCTSTR lpsz)
{
    strGlobal = lpsz;
}

__declspec(dllexport)
void GetGlobalString(LPCTSTR lpsz, size_t cb)
{
    StringCbCopy(lpsz, cb, strGlobal);
}
```

위의 코드는 DLL에 있고 해당 DLL은 A와 B 라는 두 개의 프로세스에 의해 로드 된 경우에 발생 하는 상황을 고려해 야 합니다 (실제로 동일한 응용 프로그램의 두 인스턴스인 경우). 를 호출 `SetGlobalString("Hello from A")` 합니다. 따라서 프로세스 A의 컨텍스트에서 데이터에 대 한 메모리가 할당 됩니다 `CString` . `CString` 자체는 전역 이며 a와 B 모두에 게 표시 된다는 점에 유의 하세요. 이제 B `GetGlobalString(sz, sizeof(sz))` 를 호출 합니다. B는 집합의 데이터를 볼 수 있습니다. Win32s는 Win32와 같은 프로세스 간에 보호를 제공 하지 않기 때문입니다. 첫 번째 문제입니다. 대부분의 경우 응용 프로그램이 다른 응용 프로그램이 소유 하 고 있는 것으로 간주 되는 글로벌 데이터에 영향을 주는 것은 바람직하지 않습니다.

추가 문제도 있습니다. 가 종료 되는 것을 가정해 보겠습니다. 가 종료 되 면 ' ' 문자열에 사용 되는 메모리를 `strGlobal` 시스템에 사용할 수 있습니다. 즉, 프로세스 A에서 할당 한 모든 메모리가 운영 체제에 의해 자동으로 해제 됩니다. 소멸자가 호출 되 고 있기 때문에 해제 되지 않았습니다 `CString` . 아직 호출 되지 않았습니다. 할당 된 응용 프로그램이 장면을 나갔습니다 .이는 간단히 해제 됩니다. 이제 B가 호출 `GetGlobalString(sz, sizeof(sz))` 되 면 유효한 데이터를 얻지 못할 수 있습니다. 다른 응용 프로그램에서 다른 응용 프로그램에 해당 메모리를 사용 했을 수 있습니다.

분명히 문제가 있습니다. MFC 3.x는 TLS (스레드 로컬 저장소) 라고 하는 기술을 사용 했습니다. MFC 3.x는 Win32s 아래에 있는 TLS 인덱스를 할당 합니다 .이 인덱스는 호출 되지 않더라도 해당 TLS 인덱스를 기반으로 하는 모든 데이터를 참조 하는 경우에도 마찬가지입니다. 이는 Win32에 스레드 로컬 데이터를 저장 하는 데 사용 된 TLS 인덱스와 비슷합니다 (해당 주제에 대 한 자세한 내용은 아래 참조). 이로 인해 모든 MFC DLL은 프로세스 당 두 개 이상의 TLS 인덱스를 사용 합니다. 여러 OLE 컨트롤 Dll (OCXs)을 로드 하는 경우에는 TLS 인덱스가 빠르게 실행 됩니다 (64만 사용할 수 있음). 또한 MFC는이 모든 데이터를 단일 구조에 한 곳에 넣어야 했습니다. 매우 확장 가능 하지 않으며 TLS 인덱스 사용과 관련 하 여 적합 하지 않습니다.

MFC 4.x는 클래스 템플릿 집합을 사용 하 여 이러한 문제를 해결 하 고 로컬에서 처리 해야 하는 데이터를 "래핑할" 수 있습니다. 예를 들어 위에서 언급 한 문제는 다음을 작성 하 여 해결할 수 있습니다.

```cpp
struct CMyGlobalData : public CNoTrackObject
{
    CString strGlobal;
};
CProcessLocal<CMyGlobalData> globalData;

__declspec(dllexport)
void SetGlobalString(LPCTSTR lpsz)
{
    globalData->strGlobal = lpsz;
}

__declspec(dllexport)
void GetGlobalString(LPCTSTR lpsz, size_t cb)
{
    StringCbCopy(lpsz, cb, globalData->strGlobal);
}
```

MFC는 두 단계로이를 구현 합니다. 첫째, 보유 한 Dll 수에 관계 없이 프로세스 마다 두 개의 TLS 인덱스만 사용 하는 계층 (**TlsAlloc**, **tlssetvalue**, **Tlssetvalue** 등)이 Win32 __Tls \*__ api 위에 있습니다. 둘째, `CProcessLocal` 이 데이터에 액세스 하기 위한 템플릿이 제공 됩니다. 위에 표시 된 직관적인 구문을 허용 하는 operator->를 재정의 합니다. 로 래핑된 모든 개체는 `CProcessLocal` 에서 파생 되어야 합니다 `CNoTrackObject` . `CNoTrackObject` / 프로세스가 종료 될 때 MFC가 프로세스 로컬 개체를 자동으로 삭제할 수 있도록 하위 수준 할당자 (localalloc **LocalFree**) 및 가상 소멸자를 제공 합니다. 추가 정리가 필요한 경우 이러한 개체는 사용자 지정 소멸자를 가질 수 있습니다. 컴파일러가 포함 된 개체를 삭제 하는 기본 소멸자를 생성 하므로 위의 예제에는 하나가 필요 하지 않습니다 `CString` .

이 방법에는 다른 흥미로운 이점이 있습니다. 모든 개체가 자동으로 제거 되는 것은 아니므로 `CProcessLocal` 필요할 때까지 생성 되지 않습니다. `CProcessLocal::operator->` 는 처음 호출 될 때 연결 된 개체를 인스턴스화하고 더 빨리 발생 하지 않습니다. 위의 예제에서이는 `strGlobal` 첫 번째 `SetGlobalString` 또는가 호출 될 때까지 ' ' 문자열이 생성 되지 않음을 의미 합니다 `GetGlobalString` . 일부 경우에는 DLL 시작 시간을 줄이는 데 도움이 될 수 있습니다.

## <a name="thread-local-data"></a>스레드 로컬 데이터

로컬 데이터를 처리 하는 것과 마찬가지로, 데이터가 지정 된 스레드에 로컬인 경우에는 스레드 로컬 데이터를 사용 합니다. 즉, 해당 데이터에 액세스 하는 각 스레드에 대해 별도의 데이터 인스턴스가 필요 합니다. 이는 광범위 한 동기화 메커니즘 대신 여러 번 사용할 수 있습니다. 여러 스레드에서 데이터를 공유할 필요가 없는 경우 이러한 메커니즘은 비용이 많이 들고 불필요 합니다. `CString`위의 샘플과 매우 유사한 개체가 있다고 가정 합니다. 템플릿을 사용 하 여이를 스레드로 래핑하여 스레드를 로컬로 만들 수 있습니다 `CThreadLocal` .

```cpp
struct CMyThreadData : public CNoTrackObject
{
    CString strThread;
};
CThreadLocal<CMyThreadData> threadData;

void MakeRandomString()
{
    // a kind of card shuffle (not a great one)
    CString& str = threadData->strThread;
    str.Empty();
    while (str.GetLength() != 52)
    {
        unsigned int randomNumber;
        errno_t randErr;
        randErr = rand_s(&randomNumber);

        if (randErr == 0)
        {
            TCHAR ch = randomNumber % 52 + 1;
            if (str.Find(ch) <0)
            str += ch; // not found, add it
        }
    }
}
```

`MakeRandomString`가 서로 다른 두 스레드에서 호출 된 경우 각각은 다른 방법으로 방해 하지 않고 문자열의 순서를 "순서 섞기" 합니다. 이는 실제로 `strThread` 하나의 전역 인스턴스만이 아니라 스레드 당 인스턴스가 있기 때문입니다.

참조를 사용 하 여 `CString` 루프 반복 당 한 번이 아니라 주소를 한 번 캡처하는 방법을 확인 합니다. 루프 코드는 모든 위치에서 ' '이 (가) 사용 되는 것으로 작성 될 수 `threadData->strThread` `str` 있지만 코드 실행 속도가 훨씬 느립니다. 이러한 참조가 루프에서 발생 하면 데이터에 대 한 참조를 캐시 하는 것이 가장 좋습니다.

`CThreadLocal`클래스 템플릿은 동일한 메커니즘과 `CProcessLocal` 동일한 구현 기법을 사용 합니다.

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
