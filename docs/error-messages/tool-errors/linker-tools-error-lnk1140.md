---
description: '자세한 정보: 링커 도구 오류 LNK1140'
title: 링커 도구 오류 LNK1140
ms.date: 11/04/2016
f1_keywords:
- LNK1140
helpviewer_keywords:
- LNK1140
ms.assetid: 468d7651-a7cd-47b9-aead-5bb2fab56121
ms.openlocfilehash: cde57e3594035aecc1cc3608d1329c5bc0752624
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97281199"
---
# <a name="linker-tools-error-lnk1140"></a>링커 도구 오류 LNK1140

프로그램 데이터베이스용 모듈이 너무 많습니다. /PDB: NONE 링크

프로젝트에 4096 개 이상의 모듈이 포함 되어 있습니다.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>아래의 해결 방법 따라 수정합니다.

1. [/Pdb: NONE](../../build/reference/pdb-use-program-database.md)을 사용 하 여 다시 연결 합니다.

1. 디버깅 정보를 사용 하지 않고 일부 모듈을 컴파일합니다.

1. 모듈 수를 줄입니다.
