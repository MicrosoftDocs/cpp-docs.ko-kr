---
description: '자세한 정보: DHTML 편집 명령 맵'
title: DHTML 편집 명령 맵
ms.date: 11/04/2016
ms.assetid: c1b49876-039e-4a26-bb24-ea98ccf254a1
ms.openlocfilehash: da50d9b58e5294622da0685450e01ad0acabad3f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220112"
---
# <a name="dhtml-editing-command-maps"></a>DHTML 편집 명령 맵

다음 매크로를 사용 하 여 [CHtmlEditView](../../mfc/reference/chtmleditview-class.md)파생 클래스에서 DHTML 편집 명령을 매핑할 수 있습니다. 사용에 대 한 예제는 [HTMLEdit 샘플](../../overview/visual-cpp-samples.md)을 참조 하세요.

### <a name="dhtml-editing-command-map-macros"></a>DHTML 편집 명령 맵 매크로

|Name|설명|
|-|-|
|[DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap)|클래스의 DHTML 편집 명령 맵을 선언 합니다.|
|[BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap)|클래스 내에서 DHTML 편집 명령 맵의 정의를 시작 합니다.|
|[END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap)|DHTML 편집 명령 맵의 끝을 표시 합니다.|
|[DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry)|명령 ID를 HTML 편집 명령에 매핑합니다.|
|[DHTMLEDITING_CMD_ENTRY_FUNC](#dhtmlediting_cmd_entry_func)|명령 ID를 HTML 편집 명령 및 메시지 처리기에 매핑합니다.|
|[DHTMLEDITING_CMD_ENTRY_TYPE](#dhtmlediting_cmd_entry_type)|명령 ID를 HTML 편집 명령 및 사용자 인터페이스 요소에 매핑합니다.|
|[DHTMLEDITING_CMD_ENTRY_FUNC_TYPE](#dhtmlediting_cmd_entry_func_type)|명령 ID를 HTML 편집 명령, 메시지 처리기 및 사용자 인터페이스 요소로 매핑합니다.|

## <a name="declare_dhtmlediting_cmdmap"></a><a name="declare_dhtmlediting_cmdmap"></a> DECLARE_DHTMLEDITING_CMDMAP

클래스의 DHTML 편집 명령 맵을 선언 합니다.

```
DECLARE_DHTMLEDITING_CMDMAP(className)
```

### <a name="parameters"></a>매개 변수

*className*<br/>
클래스의 이름입니다.

### <a name="remarks"></a>설명

이 매크로는 [CHtmlEditView](../../mfc/reference/chtmleditview-class.md)파생 클래스의 정의에 사용 됩니다.

[BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap) 를 사용 하 여 맵을 구현 합니다.

### <a name="example"></a>예제

[HTMLEdit 샘플](../../overview/visual-cpp-samples.md)을 참조 하세요.

### <a name="requirements"></a>요구 사항

  **Header** afxhtml .h

## <a name="begin_dhtmlediting_cmdmap"></a><a name="begin_dhtmlediting_cmdmap"></a> BEGIN_DHTMLEDITING_CMDMAP

클래스 내에서 DHTML 편집 명령 맵의 정의를 시작 합니다.

```
BEGIN_DHTMLEDITING_CMDMAP(className)
```

### <a name="parameters"></a>매개 변수

*className*<br/>
DHTML 편집 명령 맵을 포함 하는 클래스의 이름입니다. 이 클래스는 [CHtmlEditView](../../mfc/reference/chtmleditview-class.md) 에서 직접 또는 간접적으로 파생 되 고 해당 클래스 정의 내에 [DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap) 매크로를 포함 해야 합니다.

### <a name="remarks"></a>설명

사용자 인터페이스 명령을 HTML 편집 명령에 매핑하기 위해 클래스에 DHTML 편집 명령 맵을 추가 합니다.

클래스의 구현 파일 (.cpp)에 BEGIN_DHTMLEDITING_CMDMAP 매크로를 추가 하 고 클래스를 매핑할 명령에 대 한 [DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry) 매크로를 추가 합니다 (예: ID_EDIT_CUT에서 IDM_CUT로). [END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap) 매크로를 사용 하 여 이벤트 맵의 끝을 표시 합니다.

### <a name="requirements"></a>요구 사항

  **Header** afxhtml .h

## <a name="end_dhtmlediting_cmdmap"></a><a name="end_dhtmlediting_cmdmap"></a> END_DHTMLEDITING_CMDMAP

DHTML 편집 명령 맵의 끝을 표시 합니다.

```
END_DHTMLEDITING_CMDMAP()
```

### <a name="remarks"></a>설명

[BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap)와 함께 사용 합니다.

### <a name="example"></a>예제

[HTMLEdit 샘플](../../overview/visual-cpp-samples.md)을 참조 하세요.

### <a name="requirements"></a>요구 사항

  **Header** afxhtml .h

## <a name="dhtmlediting_cmd_entry"></a><a name="dhtmlediting_cmd_entry"></a> DHTMLEDITING_CMD_ENTRY

명령 ID를 HTML 편집 명령에 매핑합니다.

```
DHTMLEDITING_CMD_ENTRY(cmdID,  dhtmlcmdID)
```

### <a name="parameters"></a>매개 변수

*cmdID*<br/>
명령 ID(예: ID_EDIT_COPY).

*i Htmlcmdid*<br/>
IDM_COPY와 같이 *cmdID* 가 매핑되는 HTML 편집 명령입니다.

### <a name="example"></a>예제

[HTMLEdit 샘플](../../overview/visual-cpp-samples.md)을 참조 하세요.

### <a name="requirements"></a>요구 사항

  **Header** afxhtml .h

## <a name="dhtmlediting_cmd_entry_func"></a><a name="dhtmlediting_cmd_entry_func"></a> DHTMLEDITING_CMD_ENTRY_FUNC

명령 ID를 HTML 편집 명령 및 메시지 처리기에 매핑합니다.

```
DHTMLEDITING_CMD_ENTRY_FUNC(cmdID, dhtmlcmdID,  member_func_name)
```

### <a name="parameters"></a>매개 변수

*cmdID*<br/>
명령 ID(예: ID_EDIT_COPY).

*i Htmlcmdid*<br/>
IDM_COPY와 같이 *cmdID* 가 매핑되는 HTML 편집 명령입니다.

*member_func_name*<br/>
명령이 매핑되는 메시지-처리기 함수의 이름입니다.

### <a name="example"></a>예제

[HTMLEdit 샘플](../../overview/visual-cpp-samples.md)을 참조 하세요.

### <a name="requirements"></a>요구 사항

  **Header** afxhtml .h

## <a name="dhtmlediting_cmd_entry_type"></a><a name="dhtmlediting_cmd_entry_type"></a> DHTMLEDITING_CMD_ENTRY_TYPE

명령 ID를 HTML 편집 명령 및 사용자 인터페이스 요소에 매핑합니다.

```
DHTMLEDITING_CMD_ENTRY_TYPE(cmdID  ,   dhtmlcmdID  ,    elemType)
```

### <a name="parameters"></a>매개 변수

*cmdID*<br/>
명령 ID(예: ID_EDIT_COPY).

*i Htmlcmdid*<br/>
IDM_COPY와 같이 *cmdID* 가 매핑되는 HTML 편집 명령입니다.

*elemType*<br/>
AFX_UI_ELEMTYPE_NORMAL, AFX_UI_ELEMTYPE_CHECKBOX 또는 AFX_UI_ELEMTYPE_RADIO 중 하나인 사용자 인터페이스 요소 형식입니다.

### <a name="example"></a>예제

[HTMLEdit 샘플](../../overview/visual-cpp-samples.md)을 참조 하세요.

### <a name="requirements"></a>요구 사항

  **Header** afxhtml .h

## <a name="dhtmlediting_cmd_entry_func_type"></a><a name="dhtmlediting_cmd_entry_func_type"></a> DHTMLEDITING_CMD_ENTRY_FUNC_TYPE

명령 ID를 HTML 편집 명령, 메시지 처리기 및 사용자 인터페이스 요소로 매핑합니다.

```
DHTMLEDITING_CMD_ENTRY_FUNC_TYPE(cmdID, dhtmlcmdID, member_func_name,  elemType)
```

### <a name="parameters"></a>매개 변수

*cmdID*<br/>
명령 ID(예: ID_EDIT_COPY).

*i Htmlcmdid*<br/>
IDM_COPY와 같이 *cmdID* 가 매핑되는 HTML 편집 명령입니다.

*member_func_name*<br/>
명령이 매핑되는 메시지-처리기 함수의 이름입니다.

*elemType*<br/>
AFX_UI_ELEMTYPE_NORMAL, AFX_UI_ELEMTYPE_CHECKBOX 또는 AFX_UI_ELEMTYPE_RADIO 중 하나인 사용자 인터페이스 요소 형식입니다.

### <a name="example"></a>예제

[HTMLEdit 샘플](../../overview/visual-cpp-samples.md)을 참조 하세요.

### <a name="requirements"></a>요구 사항

  **Header** afxhtml .h

## <a name="see-also"></a>참고 항목

[매크로 및 전역](../../mfc/reference/mfc-macros-and-globals.md)
