---
description: '자세한 정보: NMAKE 심각한 오류 U1035'
title: NMAKE 심각한 오류 U1035
ms.date: 11/04/2016
f1_keywords:
- U1035
helpviewer_keywords:
- U1035
ms.assetid: 68f0cc59-007e-4109-ac30-7ac4ac447e6d
ms.openlocfilehash: e41b65cbec43a0b19e06767c555df9cfede9b69c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97197753"
---
# <a name="nmake-fatal-error-u1035"></a>NMAKE 심각한 오류 U1035

구문 오류: ': ' 또는 ' = ' 구분 기호가 필요 합니다.

콜론 (**:**) 또는 등호 ( **=** )가 필요 합니다.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>다음과 같은 가능한 원인을 확인하여 수정하려면

1. 콜론이 대상 뒤에 올 수 없습니다.

1. 콜론 및 공백 없음 (예:) 한 문자로 된 대상을 입력 합니다. NMAKE는이를 드라이브 사양으로 해석 합니다.

1. 콜론이 유추 규칙을 따르지 않았습니다.

1. 매크로 정의 뒤에 등호가 없습니다.

1. **\\** 명령을 새 줄로 계속 하는 데 사용 된 백슬래시 () 뒤에 오는 문자

1. NMAKE 구문 규칙을 따르지 않는 문자열이 나타났습니다.

1. 단어 처리기에서 메이크파일의 형식이 지정 되었습니다.
