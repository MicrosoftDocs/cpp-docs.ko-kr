---
description: '자세한 정보: BSCMAKE 오류 BK1513'
title: BSCMAKE 오류 BK1513
ms.date: 11/04/2016
f1_keywords:
- BK1513
helpviewer_keywords:
- BK1513
ms.assetid: 9ba87c09-8d82-4c80-b0cf-a8de63dcf9da
ms.openlocfilehash: bdf26e3268f98e5ab41ef27bbeaa3734a001671a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97238091"
---
# <a name="bscmake-error-bk1513"></a>BSCMAKE 오류 BK1513

비증분 업데이트에는 모든 .SBR 파일이 필요합니다.

하나 이상의 .sbr 파일이 잘렸으므로 BSCMAKE에서 새 찾아보기 정보(.bsc) 파일을 빌드할 수 없습니다. 잘린 .sbr 파일의 이름을 찾으려면이 오류와 함께 표시 되는 [BK4502](../../error-messages/tool-errors/bscmake-warning-bk4502.md) 경고를 읽으십시오.

BSCMAKE는 잘린 .sbr 파일로 .bsc 파일을 업데이트할 수는 있지만 새 파일을 빌드할 수는 없습니다. BSCMAKE는 다음과 같은 경우 새 .bsc 파일을 빌드할 수 있습니다.

- .bsc 파일이 없는 경우

- .bsc 파일에 잘못된 파일 이름을 지정한 경우

- .bsc 파일이 손상된 경우

이 문제를 해결하려면 잘린.sbr 파일을 삭제하고 다시 빌드하거나 솔루션을 정리하고 다시 빌드합니다. IDE에서 **빌드**, **솔루션 정리** 를 선택한 다음 **빌드**, **솔루션 다시** 빌드를 차례로 선택 합니다.
