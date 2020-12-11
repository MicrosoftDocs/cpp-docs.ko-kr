---
description: '자세한 정보: 프로그래밍 방식 인쇄'
title: 프로그래밍 방식 인쇄
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC], active documents
- active documents [MFC], printing
- printing [MFC], programmatic
- IPrint interface
- printing [MFC]
ms.assetid: 3db0945b-5e13-4be4-86a0-6aecdae565bd
ms.openlocfilehash: c97a3938a97970e1479add4f62b68250845ba7e1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154697"
---
# <a name="programmatic-printing"></a>프로그래밍 방식 인쇄

OLE는 영구 문서 ()를 고유 하 게 식별 하 `GetClassFile` 고 연결 된 코드 (,, `CoCreateInstance` `QueryInterface(IID_IPersistFile)` `QueryInterface(IID_IPersistStorage)` , `IPersistFile::Load` 및 `IPersistStorage::Load` )로 로드 하는 방법을 제공 합니다. 문서 인쇄를 추가로 사용 하도록 설정 하기 위해 액티브 문서 포함 (OLE 2.0 원래 기존 OLE 디자인을 사용 하지 않음)은 `IPrint` 일반적으로 문서 유형의 영구 상태를 로드할 수 있는 개체를 통해 사용할 수 있는 기본 표준 인쇄 인터페이스인를 도입 합니다. 활성 문서의 각 보기는 `IPrint` 이러한 기능을 제공 하기 위해 선택적으로 인터페이스를 지원할 수 있습니다.

`IPrint` 인터페이스는 다음과 같이 정의됩니다.

```
interface IPrint : IUnknown
    {
    HRESULT SetInitialPageNum([in] LONG nFirstPage);
    HRESULT GetPageInfo(
        [out] LONG *pnFirstPage,
        [out] LONG *pcPages);
    HRESULT Print(
        [in] DWORD grfFlags,
        [in,out] DVTARGETDEVICE **pptd,
        [in,out] PAGESET ** ppPageSet,
        [in,out] STGMEDIUM **ppstgmOptions,
        [in] IContinueCallback* pCallback,
        [in] LONG nFirstPage,
        [out] LONG *pcPagesPrinted,
        [out] LONG *pnPageLast);
    };
```

클라이언트와 컨테이너는를 사용 `IPrint::Print` 하 여 문서가 로드 된 후 인쇄 제어 플래그, 대상 장치, 인쇄할 페이지 및 추가 옵션을 지정 하 여 문서를 인쇄 하도록 지시 합니다. 클라이언트는 인터페이스를 통한 인쇄 연속을 제어할 수도 있습니다 `IContinueCallback` (아래 참조).

또한에서는 `IPrint::SetInitialPageNum` 페이지 번호를 원활 하 게 지정 하 여 일련의 문서를 한 문서로 인쇄 하는 기능을 지원 하며, Office 바인더와 같은 액티브 문서 컨테이너의 혜택을 제공 합니다. `IPrint::GetPageInfo` 호출자가 이전에 전달 된 시작 페이지 번호 `SetInitialPageNum` (또는 문서의 내부 기본 시작 페이지 번호)와 문서에 있는 페이지 수를 검색할 수 있도록 하 여 페이지 매김 정보를 간단 하 게 표시 합니다.

에서 지 원하는 개체 `IPrint` 는 해당 개체의 CLSID 아래에 저장 된 "인쇄 가능" 키가 있는 레지스트리에 표시 됩니다.

HKEY_CLASSES_ROOT\CLSID\\ {...} \ 인쇄 가능

`IPrint` 는 일반적으로 또는를 지 원하는 동일한 개체에서 구현 됩니다 `IPersistFile` `IPersistStorage` . 호출자는 "인쇄 가능" 키에 대 한 레지스트리를 살펴보면 일부 클래스의 영구 상태를 프로그래밍 방식으로 인쇄 하는 기능을 확인 합니다. 현재 "인쇄 가능"은 이상에 대 한 지원을 나타냅니다 `IPrint` . 다른 인터페이스는 나중에 정의 될 수 있으며이는에서 `QueryInterface` `IPrint` 기본 지원 수준을 나타내는 경우에만 사용할 수 있습니다.

인쇄 절차 중에 인쇄를 시작 하는 클라이언트나 컨테이너에서 인쇄를 계속할지 여부를 제어 하는 것이 좋습니다. 예를 들어 컨테이너는 가능한 한 빨리 인쇄 작업을 종료 해야 하는 "인쇄 중지" 명령을 지원할 수 있습니다. 이 기능을 지원 하기 위해 인쇄 가능한 개체의 클라이언트는 인터페이스를 사용 하 여 작은 알림 싱크 개체를 구현할 수 있습니다 `IContinueCallback` .

```
interface IContinueCallback : IUnknown
    {
    HRESULT FContinue(void);
    HRESULT FContinuePrinting(
        [in] LONG cPagesPrinted,
        [in] LONG nCurrentPage,
        [in] LPOLESTR pszPrintStatus);
    };
```

이 인터페이스는 Win32 API에서 다양 한 연속 프로시저를 사용 하는 일반 연속 콜백 함수로 유용 하 게 사용할 수 있도록 설계 되었습니다 (예: `AbortProc` 인쇄용 및 `EnumMetafileProc` 메타 파일 열거의 경우). 따라서이 인터페이스 디자인은 다양 한 시간이 많이 걸리는 프로세스에서 유용 합니다.

가장 일반적인 경우에서 `IContinueCallback::FContinue` 함수는 시간이 오래 걸리는 프로세스에 의해 주기적으로 호출 됩니다. 싱크 개체는 S_OK을 반환 하 여 작업을 계속 하 고 S_FALSE 하 여 가능한 한 빨리 프로시저를 중지 합니다.

`FContinue`그러나는의 컨텍스트에서 사용 되지 않고 인쇄는를 `IPrint::Print` 사용 `IContinueCallback::FContinuePrint` 합니다. 인쇄 개체는 `FContinuePrinting` 인쇄 되는 페이지 수, 인쇄 되는 페이지 수, 클라이언트에서 사용자에 게 표시 하도록 선택할 수 있는 인쇄 상태를 설명 하는 추가 문자열 (예: "페이지 5/19")을 전달 하 여 정기적으로 호출 해야 합니다.

## <a name="see-also"></a>참고 항목

[액티브 문서 컨테이너](../mfc/active-document-containers.md)
