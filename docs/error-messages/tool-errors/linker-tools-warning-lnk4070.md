---
title: 링커 도구 경고 LNK4070 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4070
dev_langs:
- C++
helpviewer_keywords:
- LNK4070
ms.assetid: f95f179a-fff9-427e-bd51-466b3934517f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9cfb4ae1c5440742c491d9615a2b4929a9b04f66
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106962"
---
# <a name="linker-tools-warning-lnk4070"></a>링커 도구 경고 LNK4070

/Out: filename 지시문의 수입니다. EXP 출력 파일 'filename';에서 서로 다릅니다. 지시문이 무시 됩니다.

합니다 `filename` 에 지정 된 된 [이름](../../build/reference/name-c-cpp.md) 또는 [라이브러리](../../build/reference/library.md) 문을 사용 하는.exp 파일을 만들 때 출력에서 다른 `filename` 기본적으로 간주 되거나 를사용하여지정된는[/출력](../../build/reference/out-output-file-name.md) 옵션입니다.

개발 환경에서 및 프로젝트의.def 파일이 업데이트 되지 않은 출력 파일의 이름을 변경 하면이 경고가 표시 됩니다. 이 경고를 해결 하려면.def 파일을 수동으로 업데이트 합니다.

결과 DLL을 사용 하는 클라이언트 프로그램에는 문제가 발생할 수 있습니다.