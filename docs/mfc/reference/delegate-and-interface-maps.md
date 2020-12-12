---
description: '자세한 정보: 대리자 및 인터페이스 맵 매크로'
title: 대리자 및 인터페이스 맵 매크로 (MFC)
ms.date: 03/30/2017
helpviewer_keywords:
- delegate map macros [MFC]
- event map macros [MFC]
- interface map macros [MFC]
ms.assetid: 3840e642-ff7d-4bdc-998b-c7d8fc50890e
ms.openlocfilehash: 222625514fa0d6d1d683a6ee4098812298f7ed72
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220151"
---
# <a name="delegate-and-interface-map-macros"></a>대리자 및 인터페이스 맵 매크로

MFC는 대리자 및 인터페이스 맵에 대해 이러한 매크로를 지원 합니다.

|Name|설명|
|-|-|
|[BEGIN_DELEGATE_MAP](#begin_delegate_map)|대리자 맵을 시작 합니다.|
|[BEGIN_INTERFACE_MAP](#begin_interface_map)|되 map의 정의를 시작 합니다.|
|[CommandHandler 대리자](#commandhandler)|명령 소스를 사용 하 여 콜백 메서드를 등록 합니다.  |
|[END_DELEGATE_MAP](#end_delegate_map)|대리자 맵을 끝냅니다.|
|[END_INTERFACE_MAP](#end_interface_map)|구현 파일에서 인터페이스 맵을 종료 합니다. |
|[EVENT_DELEGATE_ENTRY](#event_delegate_entry)|대리자 맵에 항목을 만듭니다.|
|[INTERFACE_PART](#interface_part)|BEGIN_INTERFACE_MAP 매크로와 개체에서 지원할 각 인터페이스에 대 한 END_INTERFACE_MAP 매크로 사이에 사용 됩니다.|
|[MAKE_DELEGATE](#make_delegate)|관리 되는 컨트롤에 이벤트 처리기를 연결 합니다.|

## <a name="begin_delegate_map"></a><a name="begin_delegate_map"></a> BEGIN_DELEGATE_MAP

대리자 맵을 시작 합니다.

### <a name="syntax"></a>구문

```
BEGIN_DELEGATE_MAP(  CLASS );
```

### <a name="parameters"></a>매개 변수

*클래스*<br/>
관리 되는 컨트롤이 호스팅되는 클래스입니다.

### <a name="remarks"></a>설명

이 매크로는 대리자 맵을 구성 하는 대리자 항목 목록의 시작 부분을 표시 합니다. 이 매크로를 사용 하는 방법에 대 한 예제는 [EVENT_DELEGATE_ENTRY](#event_delegate_entry)를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** msclr\event.h

## <a name="begin_interface_map"></a><a name="begin_interface_map"></a> BEGIN_INTERFACE_MAP

구현 파일에서 사용 되는 경우 되 map의 정의를 시작 합니다.

### <a name="syntax"></a>구문

```
BEGIN_INTERFACE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>매개 변수

*theClass*<br/>
인터페이스 맵을 정의할 클래스

*baseClass*<br/>
*Theclass* 가 파생 되는 클래스입니다.

### <a name="remarks"></a>설명

구현 된 각 인터페이스에 대해 하나 이상의 INTERFACE_PART 매크로 호출이 있습니다. 클래스에서 사용 하는 각 집계에 대해 하나의 매크로 호출 INTERFACE_AGGREGATE 있습니다.

인터페이스 맵에 대 한 자세한 내용은 [Technical Note 38](../tn038-mfc-ole-iunknown-implementation.md)를 참조 하십시오.

### <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="commandhandler-delegate"></a><a name="commandhandler"></a> CommandHandler 대리자

명령 소스를 사용 하 여 콜백 메서드를 등록 합니다.

### <a name="syntax"></a>구문

```
delegate void CommandHandler(  UINT^ cmdID  );
```

### <a name="parameters"></a>매개 변수

*cmdID*<br/>
명령 ID입니다.

### <a name="remarks"></a>설명

이 대리자는 콜백 메서드를 명령 소스에 등록 합니다. 명령 소스 개체에 대리자를 추가 하는 경우 콜백 메서드는 지정 된 소스에서 가져온 명령에 대 한 처리기가 됩니다.

자세한 내용은 [방법: Windows Forms 컨트롤에 명령 라우팅 추가](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)를 참조 하세요.

Windows Forms 사용에 대 한 자세한 내용은 [MFC에서 Windows Form 사용자 정의 컨트롤 사용](../../dotnet/using-a-windows-form-user-control-in-mfc.md)을 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxwinforms (어셈블리 atlmfc\lib\mfcmifc80.dll에 정의 됨)

## <a name="commanduihandler"></a><a name="commanduihandler"></a> CommandUIHandler

사용자 인터페이스 업데이트 명령 메시지를 사용 하 여 콜백 메서드를 등록 합니다.

### <a name="syntax"></a>구문

```
delegate void CommandUIHandler(  unsigned int cmdID, ICommandUI^ cmdUI);
```

### <a name="parameters"></a>매개 변수

*cmdID*<br/>
명령 ID입니다.

*cmdUI*<br/>
명령 메시지 ID입니다.

### <a name="remarks"></a>설명

이 대리자는 사용자 인터페이스 업데이트 명령 메시지를 사용 하 여 콜백 메서드를 등록 합니다. `CommandUIHandler` 는이 대리자가 사용자 인터페이스 개체 업데이트 명령과 함께 사용 된다는 점을 제외 하 고는 [Commandhandler](#commandhandler) 와 비슷합니다. 사용자 인터페이스 업데이트 명령은 메시지 처리기 메서드를 사용 하 여 일대일로 매핑되어야 합니다.

Windows Forms 사용에 대 한 자세한 내용은 [MFC에서 Windows Form 사용자 정의 컨트롤 사용](../../dotnet/using-a-windows-form-user-control-in-mfc.md)을 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxwinforms (어셈블리 atlmfc\lib\mfcmifc80.dll에 정의 됨)

## <a name="end_delegate_map"></a><a name="end_delegate_map"></a> END_DELEGATE_MAP

대리자 맵을 끝냅니다.

### <a name="syntax"></a>구문

```
END_DELEGATE_MAP();
```

### <a name="remarks"></a>설명

이 매크로는 대리자 맵을 구성 하는 대리자 항목 목록의 끝을 표시 합니다. 이 매크로를 사용 하는 방법에 대 한 예제는 [EVENT_DELEGATE_ENTRY](#event_delegate_entry)를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** msclr\event.h

## <a name="end_interface_map"></a><a name="end_interface_map"></a> END_INTERFACE_MAP

구현 파일에서 인터페이스 맵을 종료 합니다.

### <a name="syntax"></a>구문

```
END_INTERFACE_MAP( )
```

### <a name="remarks"></a>설명

인터페이스 맵에 대 한 자세한 내용은 [Technical Note 38](../tn038-mfc-ole-iunknown-implementation.md)를 참조 하십시오.

### <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="event_delegate_entry"></a><a name="event_delegate_entry"></a> EVENT_DELEGATE_ENTRY

대리자 맵에 항목을 만듭니다.

### <a name="syntax"></a>구문

```
EVENT_DELEGATE_ENTRY(MEMBER, ARG0, ARG1);
```

### <a name="parameters"></a>매개 변수

*구성원과*<br/>
컨트롤에 연결할 이벤트 처리기 메서드입니다.

*ARG0*<br/>
과 같은 관리 되는 이벤트 처리기 메서드의 첫 번째 인수 `Object^` 입니다.

*ARG1*<br/>
관리 되는 이벤트 처리기 메서드의 두 번째 인수 (예:) `EventArgs^` 입니다.

### <a name="remarks"></a>설명

대리자 맵의 각 항목은 [MAKE_DELEGATE](#make_delegate)에서 만든 관리 되는 이벤트 처리기 대리자에 해당 합니다.

### <a name="example"></a>예제

다음 코드 예제에서는 EVENT_DELEGATE_ENTRY 사용 하 여 이벤트 처리기에 대 한 대리자 맵에 항목을 만드는 방법을 보여 줍니다 `OnClick` . MAKE_DELEGATE의 코드 예제도 참조 하세요. 자세한 내용은 [방법: 네이티브 c + + 클래스에서 Windows Forms 이벤트 싱크](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)를 참조 하세요.

```cpp
BEGIN_DELEGATE_MAP(CMyView)
   EVENT_DELEGATE_ENTRY(OnClick, System::Object^, System::EventArgs^)
END_DELEGATE_MAP()
```

### <a name="requirements"></a>요구 사항

**헤더:** msclr\event.h

## <a name="interface_part"></a><a name="interface_part"></a> INTERFACE_PART

BEGIN_INTERFACE_MAP 매크로와 개체에서 지원할 각 인터페이스에 대 한 END_INTERFACE_MAP 매크로 사이에 사용 됩니다.

### <a name="syntax"></a>구문

```
INTERFACE_PART( theClass, iid, localClass)
```

### <a name="parameters"></a>매개 변수

*theClass*<br/>
인터페이스 맵을 포함하는 클래스의 이름
*iid*<br/>
포함 된 클래스에 매핑될 IID입니다.
*localClass*<br/>
로컬 클래스의 이름입니다.

### <a name="remarks"></a>설명

이를 통해 IID를 *Theclass* 및 *localclass* 로 표시 되는 클래스의 멤버에 매핑할 수 있습니다.

인터페이스 맵에 대 한 자세한 내용은 [Technical Note 38](../tn038-mfc-ole-iunknown-implementation.md)를 참조 하십시오.

### <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="make_delegate"></a><a name="make_delegate"></a> MAKE_DELEGATE

관리 되는 컨트롤에 이벤트 처리기를 연결 합니다.

### <a name="syntax"></a>구문

```
MAKE_DELEGATE( DELEGATE,  MEMBER) ;
```

### <a name="parameters"></a>매개 변수

*대리자나*<br/>
[EventHandler](/dotnet/api/system.eventhandler)와 같은 관리 되는 이벤트 처리기 대리자의 형식입니다.

*구성원과*<br/>
컨트롤에 연결할 이벤트 처리기 메서드의 이름입니다.

### <a name="remarks"></a>설명

이 매크로는 *대리자* 및 name *멤버* 형식의 관리 되는 이벤트 처리기 대리자를 만듭니다. 관리 되는 이벤트 처리기 대리자를 사용 하면 네이티브 클래스에서 관리 되는 이벤트를 처리할 수 있습니다.

### <a name="example"></a>예제

다음 코드 예제에서는를 호출 하 `MAKE_DELEGATE` 여 `OnClick` 이벤트 처리기를 MFC 컨트롤에 연결 하는 방법을 보여 줍니다 `MyControl` . MFC 응용 프로그램에서이 매크로가 작동 하는 방법에 대 한 자세한 설명은 [방법: 네이티브 c + + 클래스에서 Windows Forms 이벤트 싱크](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)를 참조 하세요.

```cpp
// CMyView derives from CWinFormsView.
void CMyView::OnInitialUpdate()
{
   CWinFormsView::OnInitialUpdate();

   GetControl()->Click += MAKE_DELEGATE(System::EventHandler, OnClick);
}
```

### <a name="requirements"></a>요구 사항

**헤더:** msclr\event.h

## <a name="see-also"></a>참고 항목

[방법: 네이티브 c + + 클래스에서 Windows Forms 이벤트 싱크](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)<br/>
[방법: Windows Forms 컨트롤에 명령 라우팅 추가](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[매크로 및 전역](mfc-macros-and-globals.md)<br/>
