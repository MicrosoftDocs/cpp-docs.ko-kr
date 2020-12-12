---
description: '자세한 정보: 리소스 컴파일러 심각한 오류 RC1120'
title: 리소스 컴파일러 심각한 오류 RC1120
ms.date: 11/04/2016
f1_keywords:
- RC1120
helpviewer_keywords:
- RC1120
ms.assetid: 4e462931-e42e-42e3-8bfc-847677194286
ms.openlocfilehash: bc0c90bf5d8dd4290ab20369235c53fcd2c80182
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272034"
---
# <a name="resource-compiler-fatal-error-rc1120"></a>리소스 컴파일러 심각한 오류 RC1120

메모리 부족, 필요한 바이트 수

리소스 컴파일러는 힙에 저장 하는 항목에 대 한 저장소 부족을 실행 했습니다. 일반적으로 기호가 너무 많은 경우에 발생 합니다.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>아래의 해결 방법 따라 수정합니다.

1. Windows 스왑 파일 공간을 늘립니다. 스왑 파일 공간을 높이는 방법에 대 한 자세한 내용은 Windows 도움말의 가상 메모리를 참조 하십시오.

1. 불필요 한 포함 파일, 특히 불필요 `#define` 한 및 함수 프로토타입을 제거 합니다.

1. 현재 파일을 둘 이상의 파일로 분할 하 고 별도로 컴파일합니다.

1. 시스템에서 실행 되는 다른 프로그램 또는 드라이버를 제거 합니다 .이로 인해 많은 양의 메모리가 소비 될 수 있습니다.
