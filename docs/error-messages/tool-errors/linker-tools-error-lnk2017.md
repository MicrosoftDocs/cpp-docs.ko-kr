---
description: '자세한 정보: 링커 도구 오류 LNK2017'
title: 링커 도구 오류 LNK2017
ms.date: 11/04/2016
f1_keywords:
- LNK2017
helpviewer_keywords:
- LNK2017
ms.assetid: f7c21733-b0fb-4888-a295-9b453ba6ee77
ms.openlocfilehash: e4215d7c1730f85f43c2440163fa03ad97c741e5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338454"
---
# <a name="linker-tools-error-lnk2017"></a>링커 도구 오류 LNK2017

/LARGEADDRESSAWARE 없이 ' segment '로의 ' 기호 ' 재배치가 잘못 되었습니다.

32 비트 주소를 사용 하 여 64 비트 이미지를 빌드하려고 합니다. 이렇게 하려면 다음을 수행 해야 합니다.

- 고정 로드 주소를 사용 합니다.

- 이미지를 3gb로 제한 합니다.

- [/Largeaddressaware: no](../../build/reference/largeaddressaware-handle-large-addresses.md)를 지정 합니다.
