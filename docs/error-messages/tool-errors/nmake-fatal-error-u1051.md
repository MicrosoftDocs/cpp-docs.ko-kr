---
description: '자세한 정보: NMAKE 심각한 오류 U1051'
title: NMAKE 심각한 오류 U1051
ms.date: 11/04/2016
f1_keywords:
- U1051
helpviewer_keywords:
- U1051
ms.assetid: fede5cd5-dac3-47b7-b86d-e1acfb78699f
ms.openlocfilehash: c7d465eaf34adb69e41f523006fb0740eea722ef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272112"
---
# <a name="nmake-fatal-error-u1051"></a>NMAKE 심각한 오류 U1051

메모리가 부족 합니다.

메이크파일이 너무 크거나 복잡 하므로 NMAKE에 가상 메모리를 포함 한 메모리가 부족 합니다.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>아래의 해결 방법 따라 수정합니다.

1. 디스크의 공간을 확보 합니다.

1. Windows NT 페이징 파일 또는 Windows 스왑 파일의 크기를 늘립니다.

1. 메이크파일의 일부만 사용 하는 경우 메이크파일을 개별 파일로 나누고!를 사용 합니다 **.** NMAKE가 처리 해야 하는 양을 제한 하는 전처리 지시문입니다. **!** 지시문에!가 포함 되어 있는 경우 **이면** 이 고, 그렇지 않으면 `!IFDEF` **입니다. IFNDEF**, **! 그렇지 않으면** **입니다. 기타** `IFDEF` , 및 **! 그렇지 않으면** `IFNDEF` 입니다.
