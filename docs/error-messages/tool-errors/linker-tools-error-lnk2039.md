---
title: 링커 도구 오류 LNK2039 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2039
dev_langs:
- C++
helpviewer_keywords:
- LNK2039
ms.assetid: eaa296bd-4901-41f6-8410-6d03ee827144
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ac4fdde90911427a1a193bfb6f3a950a7bdcf180
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081795"
---
# <a name="linker-tools-error-lnk2039"></a>링커 도구 오류 LNK2039

ref 클래스 가져오기\<유형 >' another.obj에 정의 된; 중 가져온 또는 정의 하지만 둘 다가 아닌 것

Ref 클래스 ' <`type`>'에 지정된 된.obj 파일로 가져왔지만 다른.obj 파일에 정의 됩니다. 이 조건은 런타임 오류 또는 기타 예기치 않은 동작을 일으킬 수 있습니다.

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

1. 다른 .obj 파일에 '`type`'을 정의해야 하는지 여부 및 .winmd 파일에서 가져와야 하는지 여부를 확인합니다.

1. 정의 또는 가져오기를 제거합니다.

## <a name="see-also"></a>참고 항목

[링커 도구 오류 및 경고](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)<br/>
[링커 도구 오류 LNK1332](../../error-messages/tool-errors/linker-tools-error-lnk1332.md)