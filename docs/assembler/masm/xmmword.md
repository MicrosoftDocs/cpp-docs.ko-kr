---
title: XMMWORD
ms.date: 08/30/2018
f1_keywords:
- XMMWORD
helpviewer_keywords:
- XMMWORD directive
ms.assetid: 18026d32-5cab-403e-ad7e-382fb41aa9b8
ms.openlocfilehash: 59d1ba71260ed08b761c332e887cf27517762303
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326344"
---
# <a name="xmmword"></a>XMMWORD

MMX와 SSE (XMM) 지침을 사용 하 여 128 비트 멀티미디어 피연산자에 사용 됩니다.

## <a name="syntax"></a>구문

> XMMWORD

## <a name="remarks"></a>설명

`XMMWORD` 동일한 형식으로 표시 하기 위해 [__m128](../../cpp/m128.md)합니다.

## <a name="example"></a>예제

```asm
    movdqa   xmm0, xmmword ptr [ebx]
```