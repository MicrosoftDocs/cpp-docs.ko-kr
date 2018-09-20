---
title: DEVNAMES 구조체 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- DEVNAMES
dev_langs:
- C++
helpviewer_keywords:
- DEVNAMES [MFC]
ms.assetid: aac97f60-2169-471a-ba5d-c0baed9eed9a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 637843873bbb0e12a76168bd08b613e14b391ef8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392465"
---
# <a name="devnames-structure"></a>DEVNAMES 구조체

`DEVNAMES` 구조 드라이버, 장치 및 프린터의 출력 포트 이름을 식별 하는 문자열을 포함 합니다.

## <a name="syntax"></a>구문

```
typedef struct tagDEVNAMES { /* dvnm */
    WORD wDriverOffset;
    WORD wDeviceOffset;
    WORD wOutputOffset;
    WORD wDefault; */* driver,
    device,
    and port-name strings follow wDefault */
} DEVNAMES;
```

#### <a name="parameters"></a>매개 변수

*wDriverOffset*<br/>
(입/출력) 장치 드라이버의 파일 이름 (확장명 없음)를 포함 하는 null로 끝나는 문자열에 문자에서 오프셋을 지정 합니다. 입력에 대해이 문자열은 대화 상자에서 처음 표시할 프린터를 확인 하려면 사용 합니다.

*wDeviceOffset*<br/>
(입/출력) Null로 끝나는 문자열에 (null을 포함 하는 32 바이트입니다 최대) 장치의 이름을 포함 하는 문자에서 오프셋을 지정 합니다. 이 문자열은 동일 해야 합니다 `dmDeviceName` 의 멤버는 [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) 구조입니다.

*wOutputOffset*<br/>
(입/출력) 실제 출력 매체 (출력 포트)에 대해 DOS 장치 이름이 포함 된 null로 끝나는 문자열에 문자에서 오프셋을 지정 합니다.

*wDefault*<br/>
문자열을 포함 하는지 여부를 지정 합니다 `DEVNAMES` 구조 기본 프린터를 식별 합니다. 이 문자열을 기본 프린터로 인쇄 마지막 작업 이후 변경 되지 않았는지 확인 됩니다. 입력에 대해 DN_DEFAULTPRN 플래그가 설정 된 경우 다른 값을 `DEVNAMES` 구조는 현재 기본 프린터에 대해 확인 됩니다. 문자열이 일치 하지 않는 경우 문서를 재구성 해야 할 수 있는 사용자에 게 알리는 경고 메시지가 표시 됩니다. 출력에는 `wDefault` 인쇄 설정 대화 상자에 표시 된 사용자 확인 단추를 선택한 경우에 멤버를 변경 합니다. 기본 프린터를 선택한 경우 DN_DEFAULTPRN 플래그를 설정 합니다. 특정 프린터를 선택한 경우에 플래그가 설정 되지 않았습니다. 이 멤버의 다른 모든 비트는 인쇄 대화 상자 프로시저에서 내부 용도로 예약 되어 있습니다.

## <a name="remarks"></a>설명

`PrintDlg` 함수 이러한 문자열을 사용 하 여 시스템에 정의 된 인쇄 대화 상자에서 멤버를 초기화 합니다. 사용자가 대화 상자를 닫으면 선택한 프린터에 대 한 정보는이 구조에 반환 됩니다.

## <a name="requirements"></a>요구 사항

**헤더:** commdlg.h

## <a name="see-also"></a>참고 항목

[구조체, 스타일, 콜백 및 메시지 맵](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CPrintDialog::CreatePrinterDC](../../mfc/reference/cprintdialog-class.md#createprinterdc)


