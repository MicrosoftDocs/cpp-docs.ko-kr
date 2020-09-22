---
title: FILE_DATA 구조체
description: C++ Build Insights SDK FILE_DATA 구조체 참조입니다.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FILE_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b5f793df0340005665a8f4ab42e9793f51f3aa0c
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041811"
---
# <a name="file_data-structure"></a>FILE_DATA 구조체

::: moniker range="<=vs-2015"

C++ Build Insights SDK는 Visual Studio 2017 이상 버전과 호환됩니다. 이러한 버전에 대한 설명서를 보려면 이 문서에 대한 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2017 또는 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end
::: moniker range=">=vs-2017"

`FILE_DATA` 구조체는 파일 입력 또는 출력을 설명합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct FILE_DATA_TAG
{
    const wchar_t*      Path;
    int                 TypeCode;

} FILE_DATA;
```

## <a name="members"></a>멤버

| Name | Description |
|--|--|
| `Path` | 파일의 절대 경로입니다. |
| `TypeCode` | 파일 형식을 설명하는 코드입니다. 자세한 내용은 [FILE_TYPE_CODE](file-type-code-enum.md)를 참조하세요. |

::: moniker-end
