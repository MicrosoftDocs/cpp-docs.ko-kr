---
description: '자세한 정보: OLE 초기화'
title: OLE 초기화
ms.date: 11/04/2016
f1_keywords:
- afxdisp/AfxOleInit
- afxdisp/AfxEnableControlContainer
helpviewer_keywords:
- OLE initialization
ms.assetid: aa8a54a7-24c3-4344-b2c6-dbcf6084fa31
ms.openlocfilehash: 0efed4fefe62b720852905b6eed44501d4369efa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218994"
---
# <a name="ole-initialization"></a>OLE 초기화

응용 프로그램에서 OLE 시스템 서비스를 사용 하려면 OLE 시스템 Dll을 초기화 하 고 Dll이 올바른 버전 인지 확인 해야 합니다. `AfxOleInit`함수는 OLE 시스템 dll을 초기화 합니다.

### <a name="ole-initialization"></a>OLE 초기화

|Name|설명|
|-|-|
|[AfxOleInit](#afxoleinit)|OLE 라이브러리를 초기화 합니다.|
|[AfxEnableControlContainer](#afxenablecontrolcontainer)|`InitInstance`OLE 컨트롤의 포함을 지원할 수 있도록 응용 프로그램 개체의 함수에서이 함수를 호출 합니다.|

## <a name="afxenablecontrolcontainer"></a><a name="afxenablecontrolcontainer"></a> AfxEnableControlContainer

`InitInstance`OLE 컨트롤의 포함을 지원할 수 있도록 응용 프로그램 개체의 함수에서이 함수를 호출 합니다.

### <a name="syntax"></a>구문

```cpp
void AfxEnableControlContainer( );
```

### <a name="remarks"></a>설명

OLE 컨트롤 (현재 ActiveX 컨트롤 이라고 함)에 대 한 자세한 내용은 [Activex 컨트롤 항목](../mfc-activex-controls.md)을 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxdisp.h

## <a name="afxoleinit"></a><a name="afxoleinit"></a> AfxOleInit

응용 프로그램에 대 한 OLE 지원을 초기화 합니다.

```
BOOL AFXAPI AfxOleInit();
```

### <a name="return-value"></a>반환 값

성공 하면 0이 아닌 값 초기화가 실패할 경우 0입니다. 잘못 된 버전의 OLE 시스템 Dll이 설치 되어 있기 때문일 수 있습니다.

### <a name="remarks"></a>설명

MFC 응용 프로그램에 대 한 OLE 지원을 초기화 하려면이 함수를 호출 합니다. 이 함수를 호출 하면 다음 작업이 수행 됩니다.

- 호출 하는 응용 프로그램의 현재 아파트에서 COM 라이브러리를 초기화 합니다. 자세한 내용은 [OleInitialize](/windows/win32/api/ole2/nf-ole2-oleinitialize)를 참조 하세요.

- [Imessagefilter.prefiltermessage](/windows/win32/api/objidl/nn-objidl-imessagefilter) 인터페이스를 구현 하는 메시지 필터 개체를 만듭니다. 이 메시지 필터는 [AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter)를 호출 하 여 액세스할 수 있습니다.

> [!NOTE]
> **AfxOleInit** 를 MFC DLL에서 호출 하는 경우 호출이 실패 합니다. 함수는 DLL에서 호출 되는 경우 호출 응용 프로그램에서 OLE 시스템을 이전에 초기화 한 것으로 가정 하므로 오류가 발생 합니다.

> [!NOTE]
> MFC 응용 프로그램을 STA (단일 스레드 아파트)로 초기화 해야 합니다. 재정의에서 [CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex) 를 호출 하 `InitInstance` 는 경우 COINIT_MULTITHREADED 대신 COINIT_APARTMENTTHREADED를 지정 합니다.

### <a name="requirements"></a>요구 사항

**헤더:** afxdisp.h

## <a name="see-also"></a>참고 항목

[매크로 및 전역](../../mfc/reference/mfc-macros-and-globals.md)
