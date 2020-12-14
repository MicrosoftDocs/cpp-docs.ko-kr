---
description: '자세한 정보: 링커 도구 경고 LNK4206'
title: 링커 도구 경고 LNK4206
ms.date: 12/05/2017
f1_keywords:
- LNK4206
helpviewer_keywords:
- LNK4206
ms.assetid: 6c108e33-00cf-4c5a-830d-d65d470930a7
ms.openlocfilehash: 40d7a8f18a835721ff747293696d0499c0a94ef3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97294147"
---
# <a name="linker-tools-warning-lnk4206"></a>링커 도구 경고 LNK4206

> 미리 컴파일된 형식 정보를 찾을 수 없습니다. '*filename*'은 (는) 연결 되지 않았거나 덮어 쓰여졌습니다. 디버그 정보가 없는 것 처럼 개체를 링크 합니다.

[/Yc](../../build/reference/yc-create-precompiled-header-file.md)를 사용 하 여 컴파일된 *파일 이름* 개체 파일이 LINK 명령에 지정 되지 않았거나 덮어쓰여집니다.

이 경고에 대 한 일반적인 시나리오는/Yc로 컴파일된 .obj가 라이브러리에 있고 코드에서 해당 .obj에 대 한 기호 참조가 없는 경우입니다.  이 경우 링커에서 .obj 파일을 사용 하거나 참조 하지 않습니다.  이 경우에는 코드를 다시 컴파일하고 [/yu](../../build/reference/yu-use-precompiled-header-file.md)를 사용 하 여 컴파일된 개체에 대해 [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) 를 사용 해야 합니다.
