---
description: '자세한 정보: 컴파일러 오류 C2220'
title: 컴파일러 오류 C2220
ms.date: 11/04/2016
f1_keywords:
- C2220
helpviewer_keywords:
- C2220
ms.assetid: d610802c-64d7-40ad-a2a6-0ed0b6815a6c
ms.openlocfilehash: f45a34d0cdaa5e82c3f5e6c051126c6df4eb2005
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97245436"
---
# <a name="compiler-error-c2220"></a>컴파일러 오류 C2220

경고가 오류로 처리 되었습니다. 개체 파일이 생성 되지 않았습니다.

[/Wx](../../build/reference/compiler-option-warning-level.md) 는 모든 경고를 오류로 처리 하도록 컴파일러에 지시 합니다. 오류가 발생했기 때문에 개체 또는 실행 파일이 생성되지 않았습니다.

이 오류는 **/wx** 플래그가 설정 되 고 컴파일 중에 경고가 발생 하는 경우에만 표시 됩니다. 이 오류를 해결하려면 프로젝트에서 모든 경고를 없애야 합니다.

### <a name="to-fix-use-one-of-the-following-techniques"></a>해결하려면 다음 방법 중 하나를 사용합니다.

- 프로젝트에서 경고를 일으키는 문제를 해결합니다.

- 낮은 경고 수준에서 컴파일합니다 (예: **/W4** 대신 **/W3** 사용).

- [경고](../../preprocessor/warning.md) pragma를 사용 하 여 특정 경고를 사용 하지 않도록 설정 하거나 표시 하지 않습니다.

- **/Wx** 를 사용 하 여 컴파일해야 합니다.
