---
description: '자세한 정보: 심각한 오류 C1852'
title: 심각한 오류 C1852
ms.date: 11/04/2016
f1_keywords:
- C1852
helpviewer_keywords:
- C1852
ms.assetid: fa011004-b8d6-46f1-ba80-4785e4ce137f
ms.openlocfilehash: 0b4976566b8101ecd4f35d20854ef6124a15246e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97276246"
---
# <a name="fatal-error-c1852"></a>심각한 오류 C1852

'filename'은 올바른 미리 컴파일된 헤더 파일이 아닙니다.

파일은 미리 컴파일된 헤더가 아닙니다.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>다음과 같은 가능한 원인을 확인하여 수정하려면

1. **/Yu** 또는 **#pragma hdrstop** 으로 지정된 잘못된 파일입니다.

1. 달리 지정하지 않는 경우 컴파일러는 파일 확장명을 .pch로 간주합니다.
