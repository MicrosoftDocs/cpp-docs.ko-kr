---
description: '자세한 정보: 문자열 변환 매크로'
title: 문자열 변환 매크로
ms.date: 11/04/2016
f1_keywords:
- atlconv/ATL::DEVMODEA2W
- atlconv/ATL::TEXTMETRICA2W
- atlconv/ATL::DEVMODEOLE2T
- atlconv/ATL::TEXTMETRICOLE2T
- atlconv/ATL::DEVMODET2OLE
- atlconv/ATL::TEXTMETRICT2OLE
- atlconv/ATL::DEVMODEW2A
- atlconv/ATL::TEXTMETRICW2A
ms.assetid: 2ff7c0b6-2bde-45fe-897f-6128e18e0c27
ms.openlocfilehash: a7717f7876d9dbe23c0b95fd68b4bcd971e81267
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97138777"
---
# <a name="string-conversion-macros"></a>문자열 변환 매크로

이러한 매크로는 문자열 변환 기능을 제공 합니다.

## <a name="atl-and-mfc-string-conversion-macros"></a><a name="atl_and_mfc_string_conversion_macros"></a> ATL 및 MFC 문자열 변환 매크로

이 항목에서 설명하는 문자열 변환 매크로는 ATL과 MFC에 모두 사용 가능합니다. MFC 문자열 변환에 대 한 자세한 내용은 [TN059: USING MFC MBCS/Unicode Conversion macros](../../mfc/tn059-using-mfc-mbcs-unicode-conversion-macros.md) 및 [Mfc 매크로 및 Globals](../../mfc/reference/mfc-macros-and-globals.md)를 참조 하세요.

## <a name="devmode-and-textmetric-string-conversion-macros"></a><a name="devmode_and_textmetric_string_conversion_macros"></a> DEVMODE 및 TEXTMETRIC 문자열 변환 매크로

이러한 매크로는 [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) 또는 [textmetric](/windows/win32/api/wingdi/ns-wingdi-textmetricw) 구조체의 복사본을 만들고 새 구조체 내의 문자열을 새 문자열 형식으로 변환 합니다. 매크로는 새 구조체의 스택에 메모리를 할당 하 고 새 구조체에 대 한 포인터를 반환 합니다.

```cpp
MACRONAME( address_of_structure )
```

### <a name="remarks"></a>설명

예를 들어:

[!code-cpp[NVC_ATL_Utilities#128](../../atl/codesnippet/cpp/string-conversion-macros_1.cpp)]

and:

[!code-cpp[NVC_ATL_Utilities#129](../../atl/codesnippet/cpp/string-conversion-macros_2.cpp)]

매크로 이름에서 원본 구조의 문자열 형식은 왼쪽에 있고 (예 **:),** 대상 구조체의 문자열 형식은 오른쪽에 있습니다 (예: **W**). **A는** LPSTR을 의미 하 고, **OLE** 는 LPOLESTR을, **T** 는 LPTSTR를, **W** 는 LPWSTR를 나타냅니다.

따라서 DEVMODEA2W는 `DEVMODE` LPSTR 문자열을 포함 하는 구조체를 `DEVMODE` LPWSTR 문자열이 있는 구조체로 복사 하 고 TEXTMETRICOLE2T는 LPOLESTR 문자열이 포함 된 구조체를 `TEXTMETRIC` `TEXTMETRIC` LPTSTR 문자열이 있는 구조체로 복사 합니다.

구조에서 변환 되는 두 문자열은 `DEVMODE` 장치 이름 ( `dmDeviceName` )과 양식 이름 ( `dmFormName` )입니다. `DEVMODE`문자열 변환 매크로도 구조 크기 ()를 업데이트 합니다 `dmSize` .

구조체로 변환 된 네 개의 문자열은 `TEXTMETRIC` 첫 번째 문자 ( `tmFirstChar` ), 마지막 문자 (), `tmLastChar` 기본 문자 ( `tmDefaultChar` ) 및 break 문자 ( `tmBreakChar` )입니다.

`DEVMODE`및 `TEXTMETRIC` 문자열 변환 매크로의 동작은 적용 되는 컴파일러 지시문 (있는 경우)에 따라 달라 집니다. 소스와 대상 형식이 같으면 변환이 수행되지 않습니다. 컴파일러 지시문은 **T** 와 **OLE** 를 다음과 같이 변경 합니다.

|적용되는 컴파일러 지시문|T의 변경 결과|OLE의 변경 결과|
|----------------------------------|---------------|-----------------|
|없음|**A**|**W**|
|**\_유니코드**|**W**|**W**|
|**OLE2ANSI**|**A**|**A**|
|**\_ 유니코드** 및 **OLE2ANSI**|**W**|**A**|

다음 표에서는 `DEVMODE` 및 `TEXTMETRIC` 문자열 변환 매크로를 보여 줍니다.

|`DEVMODE` 매크로나|`TEXTMETRIC` 매크로나|
|-|-|
|DEVMODEA2W|TEXTMETRICA2W|
|DEVMODEOLE2T|TEXTMETRICOLE2T|
|DEVMODET2OLE|TEXTMETRICT2OLE|
|DEVMODEW2A|TEXTMETRICW2A|

## <a name="see-also"></a>참고 항목

[매크로](../../atl/reference/atl-macros.md)
