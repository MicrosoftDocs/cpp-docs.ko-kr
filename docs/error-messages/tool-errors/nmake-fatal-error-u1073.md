---
description: '자세한 정보: NMAKE 심각한 오류 U1073'
title: NMAKE 심각한 오류 U1073
ms.date: 11/04/2016
f1_keywords:
- U1073
helpviewer_keywords:
- U1073
ms.assetid: d46bf2dd-400a-4802-9db2-f832e1c97f02
ms.openlocfilehash: bd622f37720cf5e992a1d82ea97ca1ff50344c0c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345448"
---
# <a name="nmake-fatal-error-u1073"></a>NMAKE 심각한 오류 U1073

' targetname '을 만드는 방법을 모릅니다.

지정 된 대상이 존재 하지 않습니다. 실행할 명령이 나 적용할 유추 규칙이 없습니다.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>아래의 해결 방법 따라 수정합니다.

1. 대상 이름의 철자를 확인 합니다.

1. Targetname이 의사 ( *targetname* ) 인 경우 다른 설명 블록의 대상으로 지정 합니다.

1. *Targetname* 이 매크로 호출이 면 null 문자열로 확장 되지 않아야 합니다.
