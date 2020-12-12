---
description: '자세한 정보: BSCMAKE 오류 BK1503'
title: BSCMAKE 오류 BK1503
ms.date: 11/04/2016
f1_keywords:
- BK1503
helpviewer_keywords:
- BK1503
ms.assetid: e6582344-b91e-486f-baf3-4f9028d83c3b
ms.openlocfilehash: 0e789aa54241df5245f4c3a02a9307a97d51730c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323001"
---
# <a name="bscmake-error-bk1503"></a>BSCMAKE 오류 BK1503

' filename ' 파일에 쓸 수 없습니다 [: reason]

BSCMAKE는 컴파일하는 동안 생성 된 .sbr 파일을 하나의 브라우저 데이터베이스로 결합 합니다. 결과 브라우저 데이터베이스가 64 MB를 초과 하거나 입력 (.sbr) 파일의 수가 4092를 초과 하는 경우이 오류가 내보내집니다.

4092 개 이상의 .sbr 파일로 인해 문제가 발생 한 경우 입력 파일 수를 줄여야 합니다. Visual Studio 내에서 전체 프로젝트를 만든 다음 파일을 기준으로 파일을 다시 확인 [하 여이](../../build/reference/fr-fr-create-dot-sbr-file.md) 를 수행할 수 있습니다.

64MB 보다 큰 .bsc 파일로 인해 문제가 발생 하는 경우 .sbr 파일의 수를 입력으로 줄이면 결과로 생성 되는 .bsc 파일의 크기가 줄어듭니다. 또한/Em (매크로 확장 기호 제외),/El (지역 변수 제외) 및/Es (시스템 파일 제외)를 사용 하 여 찾아보기 정보의 크기를 줄일 수 있습니다.

## <a name="see-also"></a>참고 항목

[BSCMAKE 옵션](../../build/reference/bscmake-options.md)
