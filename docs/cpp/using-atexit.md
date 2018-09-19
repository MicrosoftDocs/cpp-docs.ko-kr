---
title: Atexit 사용 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- atexit
dev_langs:
- C++
helpviewer_keywords:
- atexit function
ms.assetid: d28fda17-c3d4-4af6-ba44-f44886bbb237
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9d5164394853d2ac4f18efc94863b8fc3fa5ba78
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053130"
---
# <a name="using-atexit"></a>atexit 사용

사용 하 여 합니다 [atexit](../c-runtime-library/reference/atexit.md) 함수 프로그램 종료 전에 실행 되는 종료 처리 함수를 지정할 수 있습니다. 호출 하기 전에 초기화 없는 전역 정적 개체 **atexit** 종료 처리 함수의 실행 전에 소멸 됩니다.

## <a name="see-also"></a>참고자료

[추가 종료 고려 사항](../cpp/additional-termination-considerations.md)