---
title: 컴파일러 오류 C2592 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2592
dev_langs:
- C++
helpviewer_keywords:
- C2592
ms.assetid: 833a4d7b-66ef-4d4c-ae83-a533c2b0eb07
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3f2377f48eb8102771705f2dedc67a7a15f6fa95
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030993"
---
# <a name="compiler-error-c2592"></a>컴파일러 오류 C2592

'class': 'base_class_2'는 'base_class_1'에서 상속되며 다시 지정할 수 없습니다.

다른 기본 클래스에서 상속되지 않는 기본 클래스만 지정할 수 있습니다. 이 경우에는 `base_class_1`이 이미 `base_class_2`를 상속하기 때문에 `class`의 사양에 `base_class_1`만 필요합니다.