---
description: '자세한 정보: 심각한 오류 C1081'
title: 심각한 오류 C1081
ms.date: 11/04/2016
f1_keywords:
- C1081
helpviewer_keywords:
- C1081
ms.assetid: e58adf17-cbe1-4955-a5c7-80622bbba249
ms.openlocfilehash: 97e1070cb24a70750e9c7d9f78a3860b26a7831a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330694"
---
# <a name="fatal-error-c1081"></a>심각한 오류 C1081

' symbol ': 파일 이름이 너무 깁니다.

파일 경로 이름의 길이가 `_MAX_PATH` (stdlib.h에 의해 260 자로 정의 됨)를 초과 합니다. 파일의 이름을 줄입니다.

짧은 파일 이름으로 CL.exe를 호출 하는 경우 컴파일러에서 전체 경로 이름을 생성 해야 할 수 있습니다. 예를 들어는 `cl -c myfile.cpp` 컴파일러에서 다음과 같이 생성 될 수 있습니다.

```
D:\<very-long-directory-path>\myfile.cpp
```
