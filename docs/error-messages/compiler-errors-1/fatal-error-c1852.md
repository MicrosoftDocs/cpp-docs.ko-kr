---
title: 심각한 오류 C1852 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1852
dev_langs:
- C++
helpviewer_keywords:
- C1852
ms.assetid: fa011004-b8d6-46f1-ba80-4785e4ce137f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0adfa7eed25f1902300fa2378b8ffc19eb8dfafd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023802"
---
# <a name="fatal-error-c1852"></a>심각한 오류 C1852

'filename'은 올바른 미리 컴파일된 헤더 파일이 아닙니다.

파일은 미리 컴파일된 헤더가 아닙니다.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>다음과 같은 가능한 원인을 확인하여 수정하려면

1. **/Yu** 또는 **#pragma hdrstop**으로 지정된 잘못된 파일입니다.

1. 달리 지정하지 않는 경우 컴파일러는 파일 확장명을 .pch로 간주합니다.