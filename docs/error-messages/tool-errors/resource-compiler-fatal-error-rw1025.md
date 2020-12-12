---
description: '자세한 정보: 리소스 컴파일러 심각한 오류 RW1025'
title: 리소스 컴파일러 심각한 오류 RW1025
ms.date: 11/04/2016
f1_keywords:
- RW1025
helpviewer_keywords:
- RW1025
ms.assetid: 561a02af-e7e0-442a-8ad3-a00b2ca1b62e
ms.openlocfilehash: 40404f8d6dc16b73f93255a18ce8c632cc1e014a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97237194"
---
# <a name="resource-compiler-fatal-error-rw1025"></a>리소스 컴파일러 심각한 오류 RW1025

Far 힙 메모리가 부족 합니다.

너무 많은 공간을 차지 하는 메모리 상주 소프트웨어를 확인 합니다. CHKDSK 프로그램을 사용 하 여 보유 하 고 있는 메모리의 양을 확인 합니다.

대량 리소스 파일을 만드는 경우 리소스 스크립트를 두 개의 파일로 분할 합니다. 두 .res 파일을 만든 후에는 MS-DOS 명령줄을 사용 하 여 서로 조인 합니다.

```
copy first.res /b + second.res /b full.res
```
