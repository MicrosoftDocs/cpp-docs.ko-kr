---
title: ATL 인코딩 참조 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- encoding
- encoding, functions
ms.assetid: 82d4fdf3-3c4a-4fe2-b297-8ffb4714406f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ebd514b0135de4ac438b406201dc069257d1bce
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43752476"
---
# <a name="atl-encoding-reference"></a>ATL 인코딩 참조

다양 한 uuencode, 16 진수 등 공통 인터넷 표준에 UTF8 인코딩이 atlenc.h의 있는 코드에서 지원 됩니다.

### <a name="functions"></a>함수

|||
|-|-|
|[AtlGetHexValue](reference/atl-text-encoding-functions.md#atlgethexvalue)|16진수의 숫자 값을 가져오려면 이 함수를 호출합니다.|
|[AtlHexDecode](reference/atl-text-encoding-functions.md#atlhexdecode)|에 대 한 이전 호출에서와 같이 16 진수 텍스트로 인코딩된 데이터의 문자열을 디코딩합니다 [AtlHexEncode](reference/atl-text-encoding-functions.md#atlhexencode)합니다.|
|[AtlHexDecodeGetRequiredLength](reference/atl-text-encoding-functions.md#atlhexdecodegetrequiredlength)|지정된 길이의 16진수로 인코딩된 문자열에서 디코딩된 데이터를 포함할 수 있는 버퍼를 바이트 크기로 가져오려면 이 함수를 호출합니다.|
|[AtlHexEncode](reference/atl-text-encoding-functions.md#atlhexencode)|16진수 텍스트 문자열로 일부 데이터를 인코딩하려면 이 함수를 호출합니다.|
|[AtlHexEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#atlhexencodegetrequiredlength)|지정된 크기의 데이터에서 디코딩된 문자열을 포함할 수 있는 버퍼를 문자 크기로 가져오려면 이 함수를 호출합니다.|
|[AtlUnicodeToUTF8](reference/atl-text-encoding-functions.md#atlunicodetoutf8)|유니코드 문자열을 UTF-8로 변환하려면 이 함수를 호출합니다.|
|[BEncode](reference/atl-text-encoding-functions.md#bencode)|"B" 인코딩을 사용하여 일부 데이터를 변환하려면 이 함수를 호출합니다.|
|[BEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#bencodegetrequiredlength)|지정된 크기의 데이터에서 디코딩된 문자열을 포함할 수 있는 버퍼를 문자 크기로 가져오려면 이 함수를 호출합니다.|
|[EscapeXML](reference/atl-text-encoding-functions.md#escapexml)|XML에서 사용하기에 안전하지 않은 문자를 안전한 문자로 변환하려면 이 함수를 호출합니다.|
|[GetExtendedChars](reference/atl-text-encoding-functions.md#getextendedchars)|문자열에서 확장된 문자 수를 가져오려면 이 함수를 호출합니다.|
|[IsExtendedChar](reference/atl-text-encoding-functions.md#isextendedchar)|지정한 문자가 확장된 문자(32보다 작거나 126보다 크고 탭, 줄 바꿈 또는 캐리지 리턴이 아님)인지 확인하려면 이 함수를 호출합니다.|
|[QEncode](reference/atl-text-encoding-functions.md#qencode)|"Q" 인코딩을 사용하여 일부 데이터를 변환하려면 이 함수를 호출합니다.|
|[QEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#qencodegetrequiredlength)|지정된 크기의 데이터에서 디코딩된 문자열을 포함할 수 있는 버퍼를 문자 크기로 가져오려면 이 함수를 호출합니다.|
|[QPDecode](reference/atl-text-encoding-functions.md#qpdecode)|에 대 한 이전 호출에서 같이 quoted-printable 형식으로 인코딩된 데이터의 문자열을 디코딩합니다 [QPEncode](reference/atl-text-encoding-functions.md#qpencode)합니다.|
|[QPDecodeGetRequiredLength](reference/atl-text-encoding-functions.md#qpdecodegetrequiredlength)|지정된 길이의 quoted-printable로 인코딩된 문자열에서 디코딩된 데이터를 포함할 수 있는 버퍼를 바이트 크기로 가져오려면 이 함수를 호출합니다.|
|[QPEncode](reference/atl-text-encoding-functions.md#qpencode)|quoted-printable 형식으로 일부 데이터를 인코딩하려면 이 함수를 호출합니다.|
|[QPEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#qpencodegetrequiredlength)|지정된 크기의 데이터에서 디코딩된 문자열을 포함할 수 있는 버퍼를 문자 크기로 가져오려면 이 함수를 호출합니다.|
|[UUDecode](reference/atl-text-encoding-functions.md#uudecode)|에 대 한 이전 호출에서와 같이 uuencode 된 데이터의 문자열을 디코딩합니다 [UUEncode](reference/atl-text-encoding-functions.md#uuencode)합니다.|
|[UUDecodeGetRequiredLength](reference/atl-text-encoding-functions.md#uudecodegetrequiredlength)|지정된 길이의 uuencode된 문자열에서 디코딩된 데이터를 포함할 수 있는 버퍼를 바이트 크기로 가져오려면 이 함수를 호출합니다.|
|[UUEncode](reference/atl-text-encoding-functions.md#uuencode)|일부 데이터를 uuencode하려면 이 함수를 호출합니다.|
|[UUEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#uuencodegetrequiredlength)|지정된 크기의 데이터에서 디코딩된 문자열을 포함할 수 있는 버퍼를 문자 크기로 가져오려면 이 함수를 호출합니다.|

## <a name="see-also"></a>참고 항목

[개념](../atl/active-template-library-atl-concepts.md)   
[ATL COM 데스크톱 구성 요소](../atl/atl-com-desktop-components.md)

