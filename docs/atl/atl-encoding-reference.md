---
description: '자세한 정보: ATL 인코딩 참조'
title: ATL 인코딩 참조
ms.date: 11/04/2016
helpviewer_keywords:
- encoding
- encoding, functions
ms.assetid: 82d4fdf3-3c4a-4fe2-b297-8ffb4714406f
ms.openlocfilehash: 309c4cbf695b5f40e58116c9422f8da481799cbc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148670"
---
# <a name="atl-encoding-reference"></a>ATL 인코딩 참조

에 있는 코드에서 uuencode, 16 진수, UTF8 등의 일반적인 인터넷 표준에 대 한 인코딩을 지원 *`atlenc.h`* 합니다.

### <a name="functions"></a>Functions

| 함수 | 사용 사례 |
|--|--|
| [AtlGetHexValue](reference/atl-text-encoding-functions.md#atlgethexvalue) | 16진수의 숫자 값을 가져오려면 이 함수를 호출합니다. |
| [AtlHexDecode](reference/atl-text-encoding-functions.md#atlhexdecode) | [AtlHexEncode](reference/atl-text-encoding-functions.md#atlhexencode)에 대 한 이전 호출과 같이 16 진수 텍스트로 인코딩된 데이터의 문자열을 디코딩합니다. |
| [AtlHexDecodeGetRequiredLength](reference/atl-text-encoding-functions.md#atlhexdecodegetrequiredlength) | 지정된 길이의 16진수로 인코딩된 문자열에서 디코딩된 데이터를 포함할 수 있는 버퍼를 바이트 크기로 가져오려면 이 함수를 호출합니다. |
| [AtlHexEncode](reference/atl-text-encoding-functions.md#atlhexencode) | 16진수 텍스트 문자열로 일부 데이터를 인코딩하려면 이 함수를 호출합니다. |
| [AtlHexEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#atlhexencodegetrequiredlength) | 지정된 크기의 데이터에서 디코딩된 문자열을 포함할 수 있는 버퍼를 문자 크기로 가져오려면 이 함수를 호출합니다. |
| [AtlUnicodeToUTF8](reference/atl-text-encoding-functions.md#atlunicodetoutf8) | 유니코드 문자열을 UTF-8로 변환하려면 이 함수를 호출합니다. |
| [BEncode](reference/atl-text-encoding-functions.md#bencode) | "B" 인코딩을 사용하여 일부 데이터를 변환하려면 이 함수를 호출합니다. |
| [BEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#bencodegetrequiredlength) | 지정된 크기의 데이터에서 디코딩된 문자열을 포함할 수 있는 버퍼를 문자 크기로 가져오려면 이 함수를 호출합니다. |
| [EscapeXML](reference/atl-text-encoding-functions.md#escapexml) | XML에서 사용하기에 안전하지 않은 문자를 안전한 문자로 변환하려면 이 함수를 호출합니다. |
| [GetExtendedChars](reference/atl-text-encoding-functions.md#getextendedchars) | 문자열에서 확장된 문자 수를 가져오려면 이 함수를 호출합니다. |
| [IsExtendedChar](reference/atl-text-encoding-functions.md#isextendedchar) | 지정 된 문자가 확장 문자 (32 미만, 126 보다 큼, 탭, 줄 바꿈 또는 캐리지 리턴) 인지 여부를 확인 하려면이 함수를 호출 합니다. |
| [QEncode](reference/atl-text-encoding-functions.md#qencode) | "Q" 인코딩을 사용하여 일부 데이터를 변환하려면 이 함수를 호출합니다. |
| [QEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#qencodegetrequiredlength) | 지정된 크기의 데이터에서 디코딩된 문자열을 포함할 수 있는 버퍼를 문자 크기로 가져오려면 이 함수를 호출합니다. |
| [QPDecode](reference/atl-text-encoding-functions.md#qpdecode) | [Qpencode](reference/atl-text-encoding-functions.md#qpencode)에 대 한 이전 호출과 같이 따옴표를 사용한 인쇄 가능 형식으로 인코딩된 데이터 문자열을 디코딩합니다. |
| [QPDecodeGetRequiredLength](reference/atl-text-encoding-functions.md#qpdecodegetrequiredlength) | 지정된 길이의 quoted-printable로 인코딩된 문자열에서 디코딩된 데이터를 포함할 수 있는 버퍼를 바이트 크기로 가져오려면 이 함수를 호출합니다. |
| [QPEncode](reference/atl-text-encoding-functions.md#qpencode) | quoted-printable 형식으로 일부 데이터를 인코딩하려면 이 함수를 호출합니다. |
| [QPEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#qpencodegetrequiredlength) | 지정된 크기의 데이터에서 디코딩된 문자열을 포함할 수 있는 버퍼를 문자 크기로 가져오려면 이 함수를 호출합니다. |
| [UUDecode](reference/atl-text-encoding-functions.md#uudecode) | [UUEncode](reference/atl-text-encoding-functions.md#uuencode)의 이전 호출과 같이 uuencode 된 데이터의 문자열을 디코딩합니다. |
| [UUDecodeGetRequiredLength](reference/atl-text-encoding-functions.md#uudecodegetrequiredlength) | 지정된 길이의 uuencode된 문자열에서 디코딩된 데이터를 포함할 수 있는 버퍼를 바이트 크기로 가져오려면 이 함수를 호출합니다. |
| [UUEncode](reference/atl-text-encoding-functions.md#uuencode) | 일부 데이터를 uuencode하려면 이 함수를 호출합니다. |
| [UUEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#uuencodegetrequiredlength) | 지정된 크기의 데이터에서 디코딩된 문자열을 포함할 수 있는 버퍼를 문자 크기로 가져오려면 이 함수를 호출합니다. |

## <a name="see-also"></a>참고 항목

[개념](../atl/active-template-library-atl-concepts.md)<br/>
[ATL COM 데스크톱 구성 요소](../atl/atl-com-desktop-components.md)
