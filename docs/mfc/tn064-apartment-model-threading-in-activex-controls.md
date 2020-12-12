---
description: 'TN064: Apartment-Model 스레딩 in ActiveX 컨트롤에 대해 자세히 알아보세요.'
title: 'TN064: ActiveX 컨트롤의 아파트 모델 스레딩'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE controls [MFC], container support
- containers [MFC], multithreaded
- TN064 [MFC]
- multithread container [MFC]
- apartment model threading [MFC]
ms.assetid: b2ab4c88-6954-48e2-9a74-01d4a60df073
ms.openlocfilehash: 977f429dfc7be6583f7021d1837caae15fca1495
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214691"
---
# <a name="tn064-apartment-model-threading-in-activex-controls"></a>TN064: ActiveX 컨트롤의 아파트 모델 스레딩

> [!NOTE]
> 다음 기술 노트는 온라인 설명서에 먼저 포함되어 있었으므로 업데이트되지 않았습니다. 따라서 일부 절차 및 항목은 만료되거나 올바르지 않을 수 있습니다. 최신 정보를 보려면 온라인 설명서 색인에서 관심 있는 항목을 검색하는 것이 좋습니다.

이 기술 정보에서는 ActiveX 컨트롤에서 아파트 모델 스레딩을 사용 하도록 설정 하는 방법을 설명 합니다. 아파트 모델 스레딩은 Visual C++ 버전 4.2 이상 에서만 지원 됩니다.

## <a name="what-is-apartment-model-threading"></a>Apartment-Model 스레딩 이란?

아파트 모델은 다중 스레드 컨테이너 응용 프로그램 내에서 ActiveX 컨트롤과 같은 포함 된 개체를 지 원하는 방법입니다. 응용 프로그램에 스레드가 여러 개 있을 수 있지만 포함 된 개체의 각 인스턴스는 하나의 스레드에서만 실행 되는 하나의 "아파트"에 할당 됩니다. 즉, 컨트롤의 인스턴스에 대 한 모든 호출은 동일한 스레드에서 수행 됩니다.

그러나 동일한 컨트롤 형식의 다른 인스턴스는 서로 다른 아파트에 할당 될 수 있습니다. 따라서 컨트롤의 여러 인스턴스가 공통 데이터를 공유 하는 경우 (예: 정적 또는 글로벌 데이터)이 공유 데이터에 대 한 액세스는 임계 영역 등의 동기화 개체로 보호 되어야 합니다.

아파트 스레딩 모델에 대 한 자세한 내용은 *OLE 프로그래머 참조* 의 [프로세스 및 스레드](/windows/win32/ProcThread/processes-and-threads) 를 참조 하세요.

## <a name="why-support-apartment-model-threading"></a>Apartment-Model 스레딩을 지 원하는 이유

아파트 모델 스레딩을 지 원하는 컨트롤은 아파트 모델도 지 원하는 다중 스레드 컨테이너 응용 프로그램에서 사용할 수 있습니다. 아파트 모델 스레딩을 사용 하지 않는 경우 컨트롤을 사용할 수 있는 컨테이너의 잠재적 집합을 제한 합니다.

아파트 모델 스레딩을 사용 하는 것은 대부분의 컨트롤에서 간단 하 게 사용할 수 있습니다. 특히 공유 데이터가 거의 없거나 전혀 없는 경우입니다.

## <a name="protecting-shared-data"></a>공유 데이터 보호

컨트롤이 정적 멤버 변수와 같은 공유 데이터를 사용 하는 경우 두 개 이상의 스레드가 동시에 데이터를 수정 하는 것을 방지 하기 위해 해당 데이터에 대 한 액세스를 임계 영역으로 보호 해야 합니다. 이 목적을 위해 임계 영역을 설정 하려면 컨트롤의 클래스에서 클래스의 정적 멤버 변수를 선언 `CCriticalSection` 합니다. `Lock` `Unlock` 코드가 공유 데이터에 액세스 하는 경우이 임계 영역 개체의 및 멤버 함수를 사용 합니다.

예를 들어 모든 인스턴스에서 공유 하는 문자열을 유지 해야 하는 컨트롤 클래스를 생각해 보겠습니다. 이 문자열은 정적 멤버 변수에서 유지 관리 되 고 임계 영역으로 보호 될 수 있습니다. 컨트롤의 클래스 선언에는 다음이 포함 됩니다.

```cpp
class CSampleCtrl : public COleControl
{
...
    static CString _strShared;
    static CCriticalSection _critSect;
};
```

클래스에 대 한 구현은 이러한 변수에 대 한 정의를 포함 합니다.

```cpp
int CString CSampleCtrl::_strShared;
CCriticalSection CSampleCtrl::_critSect;
```

그런 다음, 정적 멤버에 대 한 액세스를 `_strShared` 중요 섹션으로 보호할 수 있습니다.

```cpp
void CSampleCtrl::SomeMethod()
{
    _critSect.Lock();
if (_strShared.Empty())
    _strShared = "<text>";
    _critSect.Unlock();

...
}
```

## <a name="registering-an-apartment-model-aware-control"></a>아파트 모델 인식 컨트롤 등록

아파트 모델 스레딩을 지 원하는 컨트롤은 *클래스 id* \\ **InprocServer32** key의 클래스 id 레지스트리 항목에서 "아파트" 값을 가진 명명 된 값 "ThreadingModel"를 추가 하 여 레지스트리에이 기능을 표시 해야 합니다. 컨트롤에 대해이 키가 자동으로 등록 되도록 하려면 여섯 번째 매개 변수의 *afxRegApartmentThreading* 플래그를에 전달 합니다 `AfxOleRegisterControlClass` .

```cpp
BOOL CSampleCtrl::CSampleCtrlFactory::UpdateRegistry(BOOL bRegister)
{
    if (bRegister)
    return AfxOleRegisterControlClass(
    AfxGetInstanceHandle(),
    m_clsid,
    m_lpszProgID,
    IDS_SAMPLE,
    IDB_SAMPLE,
    afxRegApartmentThreading,
    _dwSampleOleMisc,
    _tlid,
    _wVerMajor,
    _wVerMinor);

else
    return AfxOleUnregisterClass(m_clsid,
    m_lpszProgID);

}
```

컨트롤 프로젝트가 Visual C++ 버전 4.1 이상에서 ControlWizard에 의해 생성 된 경우이 플래그는 이미 코드에 표시 됩니다. 스레딩 모델을 등록 하기 위해 변경할 필요가 없습니다.

프로젝트가 이전 버전의 ControlWizard에서 생성 된 경우 기존 코드는 여섯 번째 매개 변수로 부울 값을 갖게 됩니다. 기존 매개 변수가 TRUE 이면 *afxRegInsertable | afxRegApartmentThreading* 로 변경 합니다. 기존 매개 변수가 FALSE 이면 *afxRegApartmentThreading* 로 변경 합니다.

컨트롤이 아파트 모델 스레딩 규칙을 따르지 않는 경우에는이 매개 변수에 *afxRegApartmentThreading* 를 전달 하면 안 됩니다.

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
