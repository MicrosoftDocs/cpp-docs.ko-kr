---
description: '자세한 정보: 링커 도구 오류 LNK1106'
title: 링커 도구 오류 LNK1106
ms.date: 11/04/2016
f1_keywords:
- LNK1106
helpviewer_keywords:
- LNK1106
ms.assetid: 528f7e65-04be-4966-b8af-9276837c7cda
ms.openlocfilehash: 85f353b6424cdd9ad12a99b29fec4f6119472cdb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97281407"
---
# <a name="linker-tools-error-lnk1106"></a>링커 도구 오류 LNK1106

잘못 된 파일 또는 디스크가 꽉 찼습니다. 위치를 찾을 수 없습니다.

도구가 `location` 메모리 매핑된 파일에서 읽거나 쓸 수 없습니다.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>다음과 같은 가능한 원인을 확인하여 수정하려면

1. 디스크가 꽉 찼습니다.

   공간을 확보 하 고 다시 연결 하세요.

1. 네트워크를 통해 연결 하는 중입니다.

   일부 네트워크는 링커에서 사용 하는 메모리 매핑된 파일을 완벽 하 게 지원 하지 않습니다. 로컬 디스크에서 연결 해 보세요.

1. 디스크에 잘못 된 블록이 있습니다.

   운영 체제 및 디스크 하드웨어에서 이러한 오류를 발견 한 경우에도 디스크 검사 프로그램을 실행할 수 있습니다.

1. 힙 공간이 부족 합니다.

   자세한 내용은 [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) 를 참조 하세요.
