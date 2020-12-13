---
description: '자세한 정보: 링커 도구 오류 LNK1200'
title: 링커 도구 오류 LNK1200
ms.date: 11/04/2016
f1_keywords:
- LNK1200
helpviewer_keywords:
- LNK1200
ms.assetid: 55771145-915e-4006-ac6c-ac702041eb2f
ms.openlocfilehash: b8c380b16cef47a4b340e4a48853d58d1ab203e5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341648"
---
# <a name="linker-tools-error-lnk1200"></a>링커 도구 오류 LNK1200

' filename ' 프로그램 데이터베이스를 읽는 동안 오류가 발생 했습니다.

PDB (프로그램 데이터베이스)를 읽을 수 없습니다.

이 오류는 파일이 손상 된 경우에 발생할 수 있습니다.

`filename`가 개체 파일의 PDB 인 경우 [/zi](../../build/reference/z7-zi-zi-debug-information-format.md)를 사용 하 여 개체 파일을 다시 컴파일합니다.

`filename`가 주 출력 파일의 PDB이 고 증분 링크를 실행 하는 동안이 오류가 발생 한 경우에는 PDB를 삭제 하 고 다시 링크 합니다.
