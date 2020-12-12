---
description: '자세한 정보: 링커 도구 오류 LNK1223'
title: 링커 도구 오류 LNK1223
ms.date: 11/04/2016
f1_keywords:
- LNK1223
helpviewer_keywords:
- LNK1223
ms.assetid: c4728c36-daee-462f-a1c7-8733dcdec88e
ms.openlocfilehash: eb1937f253d324781834d0b6f465c79f7009787f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194061"
---
# <a name="linker-tools-error-lnk1223"></a>링커 도구 오류 LNK1223

파일이 잘못되었거나 손상되었습니다. 파일의 .pdata 정보가 잘못되었습니다.

pdata를 사용하는 RISC 플랫폼에서는 컴파일러가 정렬되지 않은 항목을 포함하는 .pdata 섹션을 내보낼 때 이 오류가 발생합니다.

이 문제를 해결 하려면 [/gl (전체 프로그램 최적화)](../../error-messages/tool-errors/linker-tools-error-lnk1223.md) 을 사용 하지 않고 컴파일을 시도 합니다. 빈 함수 본문으로 인해 이 오류가 발생하는 경우도 있습니다.
