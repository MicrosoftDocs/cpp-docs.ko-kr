---
description: '다음에 대 한 자세한 정보: HSE_VERSION_INFO 구조체'
title: HSE_VERSION_INFO 구조체
ms.date: 11/04/2016
f1_keywords:
- HSE_VERSION_INFO
helpviewer_keywords:
- HSE_VERSION_INFO structure [MFC]
ms.assetid: 4837312d-68c8-4d05-9afa-1934d7d49b20
ms.openlocfilehash: fe03f3c4e00f9af62398993838927ce75410f17b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97219631"
---
# <a name="hse_version_info-structure"></a>HSE_VERSION_INFO 구조체

이 구조체는 멤버 함수의 *Pver* 매개 변수에 의해 가리킵니다 `CHttpServer::GetExtensionVersion` . Isa 버전 번호와 ISA에 대 한 텍스트 설명을 제공 합니다.

## <a name="syntax"></a>구문

```
typedef struct _HSE_VERSION_INFO {
    DWORD dwExtensionVersion;
    CHAR lpszExtensionDesc[HSE_MAX_EXT_DLL_NAME_LEN];
} HSE_VERSION_INFO, *LPHSE_VERSION_INFO;
```

#### <a name="parameters"></a>매개 변수

*dwExtensionVersion*<br/>
ISA의 버전 번호입니다.

*lpszExtensionDesc*<br/>
ISA에 대 한 텍스트 설명입니다. 기본 구현에서는 자리 표시자 텍스트를 제공 합니다. `CHttpServer::GetExtensionVersion` 사용자 고유의 설명을 제공 하려면를 재정의 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** httpext .h

## <a name="see-also"></a>참고 항목

[구조체, 스타일, 콜백 및 메시지 맵](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)
