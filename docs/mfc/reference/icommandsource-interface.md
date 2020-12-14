---
description: '자세히 알아보기: ICommandSource 인터페이스'
title: ICommandSource 인터페이스
ms.date: 03/27/2019
f1_keywords:
- ICommandSource
- AFXWINFORMS/ICommandSource
- AFXWINFORMS/ICommandSource::AddCommandHandler
- AFXWINFORMS/ICommandSource::AddCommandRangeHandler
- AFXWINFORMS/ICommandSource::AddCommandRangeUIHandler
- AFXWINFORMS/ICommandSource::AddCommandUIHandler
- AFXWINFORMS/ICommandSource::PostCommand
- AFXWINFORMS/ICommandSource::RemoveCommandHandler
- AFXWINFORMS/ICommandSource::RemoveCommandRangeHandler
- AFXWINFORMS/ICommandSource::RemoveCommandRangeUIHandler
- AFXWINFORMS/ICommandSource::RemoveCommandUIHandler
- AFXWINFORMS/ICommandSource::SendCommand
helpviewer_keywords:
- ICommandSource interface [MFC]
ms.assetid: a4b1f698-c09f-4ba8-9b13-0e74a0a4967e
ms.openlocfilehash: 711baeccd76c88db365b465cbc3c4cc05048a0f2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97219592"
---
# <a name="icommandsource-interface"></a>ICommandSource 인터페이스

명령 소스 개체에서 사용자 컨트롤로 전송 된 명령을 관리 합니다.

## <a name="syntax"></a>구문

```cpp
interface class ICommandSource
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[ICommandSource:: AddCommandHandler](#addcommandhandler)|명령 소스 개체에 명령 처리기를 추가 합니다.|
|[ICommandSource:: Addcommand범위 처리기](#addcommandrangehandler)|명령 처리기 그룹을 명령 소스 개체에 추가 합니다.|
|[ICommandSource:: AddCommandRangeUIHandler](#addcommandrangeuihandler)|사용자 인터페이스 명령 메시지 처리기 그룹을 명령 소스 개체에 추가 합니다.|
|[ICommandSource:: AddCommandUIHandler](#addcommandrangeuihandler)|명령 소스 개체에 사용자 인터페이스 명령 메시지 처리기를 추가 합니다.|
|[ICommandSource::P ostCommand](#postcommand)|메시지 처리를 기다리지 않고 메시지를 게시 합니다.|
|[ICommandSource:: RemoveCommandHandler](#removecommandhandler)|명령 소스 개체에서 명령 처리기를 제거 합니다.|
|[ICommandSource:: RemoveCommandRangeHandler](#removecommandrangehandler)|명령 소스 개체에서 명령 처리기 그룹을 제거 합니다.|
|[ICommandSource:: RemoveCommandRangeUIHandler](#removecommandrangeuihandler)|명령 원본 개체에서 사용자 인터페이스 명령 메시지 처리기 그룹을 제거 합니다.|
|[ICommandSource:: Removecom마나트 Duihandler](#removecommandrangeuihandler)|명령 소스 개체에서 사용자 인터페이스 명령 메시지 처리기를 제거 합니다.|
|[ICommandSource:: SendCommand](#sendcommand)|메시지를 전송 하 고가 반환 되기 전에 처리 될 때까지 기다립니다.|

### <a name="remarks"></a>설명

MFC 뷰에서 사용자 정의 컨트롤을 호스트 하는 경우 [CWinFormsView 클래스](../../mfc/reference/cwinformsview-class.md) 는 명령을 라우팅하고 사용자 정의 컨트롤에 명령 UI 메시지를 업데이트 하 여 mfc 명령을 처리할 수 있도록 합니다 (예: 프레임 메뉴 항목 및 도구 모음 단추). [ICommandTarget 인터페이스](../../mfc/reference/icommandtarget-interface.md)를 구현 하 여 사용자 컨트롤에 개체에 대 한 참조를 제공 합니다 `ICommandSource` .

사용 방법의 예제는 [방법: Windows Forms 컨트롤에 명령 라우팅 추가](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) 를 참조 하세요 `ICommandTarget` .

Windows Forms 사용에 대 한 자세한 내용은 [MFC에서 Windows Form 사용자 정의 컨트롤 사용](../../dotnet/using-a-windows-form-user-control-in-mfc.md)을 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxwinforms (어셈블리 atlmfc\lib\mfcmifc80.dll에 정의 됨)

## <a name="icommandsourceaddcommandhandler"></a><a name="addcommandhandler"></a> ICommandSource:: AddCommandHandler

명령 소스 개체에 명령 처리기를 추가 합니다.

```cpp
void AddCommandHandler(
    unsigned int cmdID,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>매개 변수

*cmdID*<br/>
명령 ID입니다.
*cmdHandler*<br/>
명령 처리기 메서드에 대 한 핸들입니다.

### <a name="remarks"></a>설명

이 메서드는 명령 처리기 cmdHandler를 명령 소스 개체에 추가 하 고이 처리기를 cmdID에 매핑합니다.
AddCommandHandler를 사용 하는 방법에 대 한 예제는 [방법: Windows Forms 컨트롤에 명령 라우팅 추가](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) 를 참조 하세요.

## <a name="icommandsourceaddcommandrangehandler"></a><a name="addcommandrangehandler"></a> ICommandSource:: Addcommand범위 처리기

명령 처리기 그룹을 명령 소스 개체에 추가 합니다.

```cpp
void AddCommandRangeHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>매개 변수

*cmdIDMin*<br/>
명령 ID 범위의 시작 인덱스입니다.
*cmdIDMax*<br/>
명령 ID 범위의 끝 인덱스입니다.
*cmdHandler*<br/>
명령이 매핑되는 메시지 처리기 메서드에 대 한 핸들입니다.

### <a name="remarks"></a>설명

이 메서드는 인접 한 명령 Id 범위를 단일 메시지 처리기에 매핑하고 명령 소스 개체에 추가 합니다. 이는 한 가지 방법을 사용 하 여 관련 단추 그룹을 처리 하는 데 사용 됩니다.

## <a name="icommandsourceaddcommandrangeuihandler"></a><a name="addcommandrangeuihandler"></a> ICommandSource:: AddCommandRangeUIHandler

사용자 인터페이스 명령 메시지 처리기 그룹을 명령 소스 개체에 추가 합니다.

```cpp
void AddCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>매개 변수

*cmdIDMin*<br/>
명령 ID 범위의 시작 인덱스입니다.
*cmdIDMax*<br/>
명령 ID 범위의 끝 인덱스입니다.
*cmdHandler*<br/>
명령이 매핑되는 메시지 처리기 메서드에 대 한 핸들입니다.

### <a name="remarks"></a>설명

이 메서드는 인접 한 명령 Id 범위를 단일 사용자 인터페이스 명령 메시지 처리기에 매핑하고 명령 소스 개체에 추가 합니다. 이는 한 가지 방법을 사용 하 여 관련 단추 그룹을 처리 하는 데 사용 됩니다.

## <a name="icommandsourceaddcommanduihandler"></a><a name="addcommanduihandler"></a> ICommandSource:: AddCommandUIHandler

명령 소스 개체에 사용자 인터페이스 명령 메시지 처리기를 추가 합니다.

```cpp
void AddCommandUIHandler(
    unsigned int cmdID,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>매개 변수

*cmdID*<br/>
명령 ID입니다.
*cmdUIHandler*<br/>
사용자 인터페이스 명령 메시지 처리기 메서드에 대 한 핸들입니다.

### <a name="remarks"></a>설명

이 메서드는 사용자 인터페이스 명령 메시지 처리기 cmdHandler를 명령 소스 개체에 추가 하 고이 처리기를 cmdID에 매핑합니다.

## <a name="icommandsourcepostcommand"></a><a name="postcommand"></a> ICommandSource::P ostCommand

메시지 처리를 기다리지 않고 메시지를 게시 합니다.

```cpp
void PostCommand(unsigned int command);
```

### <a name="parameters"></a>매개 변수

*command*<br/>
게시할 메시지의 명령 ID입니다.

### <a name="remarks"></a>설명

이 메서드는 명령에 지정 된 ID에 매핑된 메시지를 비동기적으로 게시 합니다. 그러면 CWnd::P Oststststststststststststststststststststststststststststststststststststststs

## <a name="icommandsourceremovecommandhandler"></a><a name="removecommandhandler"></a> ICommandSource:: RemoveCommandHandler

명령 소스 개체에서 명령 처리기를 제거 합니다.

```cpp
void RemoveCommandHandler(unsigned int cmdID);
```

### <a name="parameters"></a>매개 변수

*cmdID*<br/>
명령 ID입니다.

### <a name="remarks"></a>설명

이 메서드는 명령 소스 개체에서 cmdID에 매핑된 명령 처리기를 제거 합니다.

## <a name="icommandsourceremovecommandrangehandler"></a><a name="removecommandrangehandler"></a> ICommandSource:: RemoveCommandRangeHandler

명령 소스 개체에서 명령 처리기 그룹을 제거 합니다.

```cpp
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>매개 변수

*cmdIDMin*<br/>
명령 ID 범위의 시작 인덱스입니다.
*cmdIDMax*<br/>
명령 ID 범위의 끝 인덱스입니다.

### <a name="remarks"></a>설명

이 메서드는 명령 원본 개체에서 cmdIDMin 및 cmdIDMax로 지정 된 명령 Id에 매핑된 메시지 처리기 그룹을 제거 합니다.

## <a name="icommandsourceremovecommandrangeuihandler"></a><a name="removecommandrangeuihandler"></a> ICommandSource:: RemoveCommandRangeUIHandler

명령 원본 개체에서 사용자 인터페이스 명령 메시지 처리기 그룹을 제거 합니다.

```cpp
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>매개 변수

*cmdIDMin*<br/>
명령 ID 범위의 시작 인덱스입니다.
*cmdIDMax*<br/>
명령 ID 범위의 끝 인덱스입니다.

### <a name="remarks"></a>설명

이 메서드는 명령 원본 개체에서 cmdIDMin 및 cmdIDMax로 지정 된 명령 Id에 매핑된 사용자 인터페이스 명령 메시지 처리기 그룹을 제거 합니다.

## <a name="icommandsourceremovecommanduihandler"></a><a name="removecommanduihandler"></a> ICommandSource:: Removecom마나트 Duihandler

명령 소스 개체에서 사용자 인터페이스 명령 메시지 처리기를 제거 합니다.

```cpp
void RemoveCommandUIHandler(unsigned int cmdID);
```

### <a name="parameters"></a>매개 변수

*cmdID*<br/>
명령 ID입니다.

### <a name="remarks"></a>설명

이 메서드는 명령 소스 개체에서 cmdID에 매핑된 사용자 인터페이스 명령 메시지 처리기를 제거 합니다.

## <a name="icommandsourcesendcommand"></a><a name="sendcommand"></a> ICommandSource:: SendCommand

메시지를 전송 하 고가 반환 되기 전에 처리 될 때까지 기다립니다.

```cpp
void SendCommand(unsigned int command);
```

### <a name="parameters"></a>매개 변수

*command*<br/>
보낼 메시지의 명령 ID입니다.

### <a name="remarks"></a>설명

이 메서드는 명령에 지정 된 ID에 매핑된 메시지를 동기적으로 보냅니다. CWnd:: SendMessage를 호출 하 여 창의 메시지 큐에 메시지를 저장 하 고 해당 창 프로시저에서 반환 하기 전에 메시지를 처리할 때까지 대기 합니다.

## <a name="see-also"></a>참고 항목

[방법: Windows Forms 컨트롤에 명령 라우팅 추가](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[ICommandTarget 인터페이스](../../mfc/reference/icommandtarget-interface.md)
