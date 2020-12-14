---
description: '자세한 정보: 심각한 오류 C1854'
title: 심각한 오류 C1854
ms.date: 11/04/2016
f1_keywords:
- C1854
helpviewer_keywords:
- C1854
ms.assetid: 8c21a9cc-1737-475c-9e57-8725cd8937c1
ms.openlocfilehash: 1c08db55089853545afa511213fc164c978bd4ff
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97276207"
---
# <a name="fatal-error-c1854"></a>심각한 오류 C1854

> 미리 컴파일된 헤더를 개체 파일 '*filename*'에 만드는 동안 구성 된 정보를 덮어쓸 수 없습니다.

동일한 파일에 대해 [/yc (미리 컴파일된 헤더 파일 만들기)](../../build/reference/yc-create-precompiled-header-file.md) 옵션을 지정한 후 [/Yu (미리 컴파일된 헤더 파일 사용)](../../build/reference/yu-use-precompiled-header-file.md) 옵션을 지정 했습니다.

이 문제를 해결 하려면 일반적으로 **/yc** 옵션을 사용 하 여 프로젝트에서 하나의 파일만 컴파일하도록 설정 하 고 **/yu** 옵션을 사용 하 여 다른 모든 파일을 컴파일하도록 설정 합니다. **/Yc** 옵션 사용에 대 한 자세한 내용 및 VISUAL Studio IDE에서 설정 하는 방법에 대 한 자세한 내용은 [/Yc (미리 컴파일된 헤더 파일 만들기)](../../build/reference/yc-create-precompiled-header-file.md)를 참조 하세요. 미리 컴파일된 헤더를 사용 하는 방법에 대 한 자세한 내용은 [미리 컴파일된 헤더 파일 만들기](../../build/creating-precompiled-header-files.md)를 참조 하세요.
