---
description: '자세히 알아보기: UICheckState 열거형'
title: UICheckState 열거형
ms.date: 04/03/2017
f1_keywords:
- afxwinforms/uicheckstate
helpviewer_keywords:
- uicheckstate enumeration [MFC]
ms.assetid: 2ac0098c-20e7-410c-9685-5ead5cb02b63
ms.openlocfilehash: 8c6f250dd6f6646d22aac0fa819b73537ee0f443
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218643"
---
# <a name="uicheckstate-enumeration"></a>UICheckState 열거형

명령에 대 한 사용자 인터페이스 항목의 check 상태를 설명 합니다.

### <a name="syntax"></a>구문

```
public enum class
{
   [DefaultValue(typeid<Microsoft::VisualC::MFC::UICheckState>, "Checked")]
   Unchecked,
   Checked,
   Indeterminate
};
```

### <a name="remarks"></a>설명

[ICommandUI:: Check](icommandui-interface.md#check) 는 이러한 값을 사용 하 여 사용자 인터페이스 항목의 상태를 설명 합니다.
Windows Forms 사용에 대 한 자세한 내용은 [MFC에서 Windows Form 사용자 정의 컨트롤 사용](../../dotnet/using-a-windows-form-user-control-in-mfc.md)을 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxwinforms (어셈블리 atlmfc\lib\mfcmifc80.dll에 정의 됨)
