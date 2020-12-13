---
description: '자세한 정보: 링커 도구 오류 LNK1201'
title: 링커 도구 오류 LNK1201
ms.date: 11/04/2016
f1_keywords:
- LNK1201
helpviewer_keywords:
- LNK1201
ms.assetid: 64c3f496-a428-4b54-981e-faa82ef9c8a1
ms.openlocfilehash: 2817e8f84d0a5d28aa012de5459eb7e09f383172
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341635"
---
# <a name="linker-tools-error-lnk1201"></a>링커 도구 오류 LNK1201

' filename ' 프로그램 데이터베이스에 쓰는 동안 오류가 발생 했습니다. 디스크 공간이 부족 하거나, 경로가 잘못 되었거나, 권한이 부족 한지 확인 하십시오.

링크에서 출력 파일에 대 한 PDB (프로그램 데이터베이스)에 쓸 수 없습니다.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>다음과 같은 가능한 원인을 확인하여 수정하려면

1. 파일이 손상 되었습니다. PDB 파일을 삭제 하 고 다시 링크 합니다.

1. 디스크 공간이 부족 하 여 파일을 쓸 수 없습니다.

1. 네트워크 문제로 인해 드라이브를 사용할 수 없습니다.

1. 연결 하려는 프로그램에서 디버거가 활성화 되어 있습니다.

1. 힙 공간이 부족 합니다.  자세한 내용은 [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) 를 참조 하세요.
