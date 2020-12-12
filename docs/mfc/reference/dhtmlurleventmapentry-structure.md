---
description: '자세히 알아보기: DHtmlUrlEventMapEntry Structure'
title: DHtmlUrlEventMapEntry 구조체
ms.date: 11/04/2016
f1_keywords:
- DHtmlUrlEventMapEntry
helpviewer_keywords:
- DHtmlUrlEventMapEntry structure [MFC]
ms.assetid: 43117c1f-1a51-406c-aa2f-fea647080049
ms.openlocfilehash: c35e3ac70d8530042ca73397b0f7c6df13501497
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220060"
---
# <a name="dhtmlurleventmapentry-structure"></a>DHtmlUrlEventMapEntry 구조체

`DHtmlUrlEventMapEntry`구조는 다중 URL 이벤트 맵 지원을 제공 합니다.

## <a name="syntax"></a>구문

```
struct DHtmlUrlEventMapEntry
{
LPCTSTR szUrl;
const DHtmlEventMapEntry *pEventMap;
};
```

#### <a name="parameters"></a>매개 변수

*szUrl*<br/>
URL입니다.

*pEventMap*<br/>
URL과 연결 된 이벤트 맵입니다.

## <a name="requirements"></a>요구 사항

**헤더:** afxdhtml

## <a name="see-also"></a>참고 항목

[구조체, 스타일, 콜백 및 메시지 맵](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)
