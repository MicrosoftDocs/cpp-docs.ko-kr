---
description: '자세히 알아보기: ICommandUI 인터페이스'
title: ICommandUI 인터페이스
ms.date: 09/07/2019
f1_keywords:
- ICommandUI
- AFXWINFORMS/ICommandUI
- AFXWINFORMS/icommandui__Check
- AFXWINFORMS/ICommandUI::ContinueRouting
- AFXWINFORMS/ICommandUI::Enabled
- AFXWINFORMS/ICommandUI::ID
- AFXWINFORMS/ICommandUI::Index
- AFXWINFORMS/ICommandUI::Radio
- AFXWINFORMS/ICommandUI::Text
helpviewer_keywords:
- ICommandUI interface [MFC]
ms.assetid: 134afe8d-dcdf-47ca-857a-a166a6b665dd
ms.openlocfilehash: 26ddd4366994c9e0cecba2b4902a36e1038896c2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97219540"
---
# <a name="icommandui-interface"></a>ICommandUI 인터페이스

사용자 인터페이스 명령을 관리 합니다.

## <a name="syntax"></a>구문

```
interface class ICommandUI
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[icommandui__Check](#check)|이 명령에 대 한 사용자 인터페이스 항목을 적절 한 검사 상태로 설정 합니다.|
|[ICommandUI::ContinueRouting](#continuerouting)|현재 메시지를 처리기 체인으로 계속 라우팅하는 명령 라우팅 메커니즘에 지시 합니다.|
|[ICommandUI:: Enabled](#enabled)|이 명령에 대 한 사용자 인터페이스 항목을 사용 하거나 사용 하지 않도록 설정 합니다.|
|[ICommandUI:: ID](#id)|개체가 나타내는 사용자 인터페이스 개체의 ID를 가져옵니다 `ICommandUI` .|
|[ICommandUI:: Index](#index)|개체가 나타내는 사용자 인터페이스 개체의 인덱스를 가져옵니다 `ICommandUI` .|
|[ICommandUI:: Radio](#radio)|이 명령에 대 한 사용자 인터페이스 항목을 적절 한 검사 상태로 설정 합니다.|
|[ICommandUI:: Text](#text)|이 명령에 대 한 사용자 인터페이스 항목의 텍스트를 설정 합니다.|

### <a name="remarks"></a>설명

이 인터페이스는 사용자 인터페이스 명령을 관리 하는 메서드와 속성을 제공 합니다. `ICommandUI`는 [](../../mfc/reference/ccmdui-class.md) `ICommandUI` .net 구성 요소와 상호 운용 되는 MFC 응용 프로그램에 사용 된다는 점을 제외 하 고는 CCmdUI 클래스와 유사 합니다.

`ICommandUI` 는 [ICommandTarget](../../mfc/reference/icommandtarget-interface.md)파생 클래스의 ON_UPDATE_COMMAND_UI 처리기 내에서 사용 됩니다. 응용 프로그램의 사용자가 메뉴를 활성화 (선택 또는 클릭) 하면 각 메뉴 항목이 사용 또는 사용 안 함으로 표시 됩니다. 각 메뉴 명령의 대상은 ON_UPDATE_COMMAND_UI 처리기를 구현 하 여이 정보를 제공 합니다. 응용 프로그램의 각 명령 사용자 인터페이스 개체에 대해 [클래스 마법사](mfc-class-wizard.md) 를 사용 하 여 각 처리기에 대 한 메시지 맵 항목 및 함수 프로토타입을 만듭니다.

명령 라우팅에서 인터페이스를 사용 하는 방법에 대 한 자세한 내용은 `ICommandUI` [방법: Windows Forms 컨트롤에 명령 라우팅 추가](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)를 참조 하세요.

Windows Forms 사용에 대 한 자세한 내용은 [MFC에서 Windows Form 사용자 정의 컨트롤 사용](../../dotnet/using-a-windows-form-user-control-in-mfc.md)을 참조 하세요.

MFC에서 사용자 인터페이스 명령을 관리 하는 방법에 대 한 자세한 내용은 [CCmdUI 클래스](../../mfc/reference/ccmdui-class.md)를 참조 하세요.

## <a name="icommanduicheck"></a><a name="check"></a> ICommandUI:: Check

이 명령에 대 한 사용자 인터페이스 항목을 적절 한 검사 상태로 설정 합니다.

```
property UICheckState Check;
```

### <a name="remarks"></a>설명

이 속성은이 명령에 대 한 사용자 인터페이스 항목을 적절 한 검사 상태로 설정 합니다. Check를 다음 값으로 설정 합니다.

- 0 선택 취소
- 1 개 검사
- 2 설정 미정

## <a name="icommanduicontinuerouting"></a><a name="continuerouting"></a> ICommandUI::ContinueRouting

현재 메시지를 처리기 체인으로 계속 라우팅하는 명령 라우팅 메커니즘에 지시 합니다.

```cpp
void ContinueRouting();
```

### <a name="remarks"></a>설명

FALSE를 반환 하는 ON_COMMAND_EX 처리기와 함께 사용 해야 하는 고급 멤버 함수입니다. 자세한 내용은 기술 참고 TN006: 메시지 맵을 참조 하세요.

## <a name="icommanduienabled"></a><a name="enabled"></a> ICommandUI:: Enabled

이 명령에 대 한 사용자 인터페이스 항목을 사용 하거나 사용 하지 않도록 설정 합니다.

```
property bool Enabled;
```

### <a name="remarks"></a>설명

이 속성은이 명령에 대 한 사용자 인터페이스 항목을 사용 하거나 사용 하지 않도록 설정 합니다. 사용을 TRUE로 설정 하 여 항목을 사용 하도록 설정 합니다. 그렇지 않으면 FALSE로 설정 합니다.

## <a name="icommanduiid"></a><a name="id"></a> ICommandUI:: ID

ICommandUI 개체가 나타내는 사용자 인터페이스 개체의 ID를 가져옵니다.

```
property unsigned int ID;
```

### <a name="remarks"></a>설명

이 속성은 ICommandUI 개체가 나타내는 메뉴 항목, 도구 모음 단추 또는 기타 사용자 인터페이스 개체의 ID (핸들)를 가져옵니다.

## <a name="icommanduiindex"></a><a name="index"></a> ICommandUI:: Index

ICommandUI 개체가 나타내는 사용자 인터페이스 개체의 인덱스를 가져옵니다.

```
property unsigned int Index;
```

### <a name="remarks"></a>설명

이 속성은 ICommandUI 개체가 나타내는 메뉴 항목, 도구 모음 단추 또는 기타 사용자 인터페이스 개체의 인덱스 (핸들)를 가져옵니다.

## <a name="icommanduiradio"></a><a name="radio"></a> ICommandUI:: Radio

이 명령에 대 한 사용자 인터페이스 항목을 적절 한 검사 상태로 설정 합니다.

```
property bool Radio;
```

### <a name="remarks"></a>설명

이 속성은이 명령에 대 한 사용자 인터페이스 항목을 적절 한 검사 상태로 설정 합니다. 항목을 사용 하도록 설정 하려면 Radio를 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다.

## <a name="icommanduitext"></a><a name="text"></a> ICommandUI:: Text

이 명령에 대 한 사용자 인터페이스 항목의 텍스트를 설정 합니다.

```
property String^ Text;
```

### <a name="remarks"></a>설명

이 속성은이 명령에 대 한 사용자 인터페이스 항목의 텍스트를 설정 합니다. 텍스트를 텍스트 문자열 핸들로 설정 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** afxwinforms (어셈블리 atlmfc\lib\mfcmifc80.dll에 정의 됨)

## <a name="see-also"></a>참고 항목

[CCmdUI 클래스](../../mfc/reference/ccmdui-class.md)
