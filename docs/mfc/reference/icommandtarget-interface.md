---
description: '자세히 알아보기: ICommandTarget 인터페이스'
title: ICommandTarget 인터페이스
ms.date: 11/04/2016
f1_keywords:
- ICommandTarget
- AFXWINFORMS/ICommandTarget
- AFXWINFORMS/ICommandTarget::Initialize
helpviewer_keywords:
- ICommandTarget interface [MFC]
ms.assetid: dd9927f6-3479-4e7c-8ef9-13206cf901f3
ms.openlocfilehash: 6deb11ecca94160ea19225fb955826845a4cdefa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97219579"
---
# <a name="icommandtarget-interface"></a>ICommandTarget 인터페이스

명령 소스 개체에서 명령을 수신 하는 인터페이스를 사용 하 여 사용자 정의 컨트롤을 제공 합니다.

## <a name="syntax"></a>구문

```
interface class ICommandTarget
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[ICommandTarget:: Initialize](#initialize)|명령 대상 개체를 초기화 합니다.|

## <a name="remarks"></a>설명

MFC 뷰에서 사용자 정의 컨트롤을 호스트 하는 경우 [CWinFormsView](../../mfc/reference/cwinformsview-class.md) 는 명령을 라우팅하고 사용자 정의 컨트롤에 명령 UI 메시지를 업데이트 하 여 mfc 명령을 처리할 수 있도록 합니다 (예: 프레임 메뉴 항목 및 도구 모음 단추). 을 구현 하 여 `ICommandTarget` [ICommandSource](../../mfc/reference/icommandsource-interface.md) 개체에 대 한 참조를 사용자 컨트롤에 제공 합니다.

사용 방법의 예제는 [방법: Windows Forms 컨트롤에 명령 라우팅 추가](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) 를 참조 하세요 `ICommandTarget` .

Windows Forms 사용에 대 한 자세한 내용은 [MFC에서 Windows Form 사용자 정의 컨트롤 사용](../../dotnet/using-a-windows-form-user-control-in-mfc.md)을 참조 하세요.

## <a name="requirements"></a>요구 사항

**헤더:** afxwinforms (어셈블리 atlmfc\lib\mfcmifc80.dll에 정의 됨)

## <a name="icommandtargetinitialize"></a><a name="initialize"></a> ICommandTarget:: Initialize

명령 대상 개체를 초기화 합니다.

```cpp
void Initialize(ICommandSource^ cmdSource);
```

### <a name="parameters"></a>매개 변수

*cmdSource*<br/>
명령 소스 개체에 대 한 핸들입니다.

### <a name="remarks"></a>설명

MFC 뷰에서 사용자 정의 컨트롤을 호스트 하는 경우 CWinFormsView는 명령을 라우팅하고 사용자 정의 컨트롤에 명령 UI 메시지를 업데이트 하 여 MFC 명령을 처리할 수 있게 합니다.

이 메서드는 명령 대상 개체를 초기화 하 고이를 지정 된 명령 소스 개체 cmdSource에 연결 합니다. 사용자 정의 컨트롤 클래스 구현에서 호출 해야 합니다. 초기화 시 Initialize 구현에서 ICommandSource:: AddCommandHandler를 호출 하 여 명령 소스 개체에 명령 처리기를 등록 해야 합니다. Initialize를 사용 하 여이 작업을 수행 하는 방법에 대 한 예제는 방법: Windows Forms 컨트롤에 명령 라우팅 추가를 참조 하세요.

## <a name="see-also"></a>참고 항목

[방법: Windows Forms 컨트롤에 명령 라우팅 추가](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[ICommandSource 인터페이스](../../mfc/reference/icommandsource-interface.md)
