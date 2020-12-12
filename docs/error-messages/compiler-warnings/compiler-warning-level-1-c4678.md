---
description: '자세한 정보: 컴파일러 경고 (수준 1) C 4678'
title: 컴파일러 경고(수준 1) C4678
ms.date: 11/04/2016
f1_keywords:
- C4678
helpviewer_keywords:
- C4678
ms.assetid: 0c588f34-595d-4e5c-9470-8723fca2cc06
ms.openlocfilehash: a590bd03ba73fc4f8d5421727e5e35ac1384ffaa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97285385"
---
# <a name="compiler-warning-level-1-c4678"></a>컴파일러 경고(수준 1) C4678

기본 클래스 'base_type'이 'derived_type'보다 액세스하기 어렵습니다.

public 형식이 전용 형식에서 파생됩니다. 참조된 어셈블리에서 public 형식을 인스턴스화할 경우 전용 기본 형식의 멤버에 액세스할 수 없습니다.

C 4678는 사용 되지 않는 컴파일러 옵션 **/clr: oldSyntax** 를 사용 하는 경우에만 연결할 수 있습니다. **/Clr** 을 사용 하 여 파생 된 클래스에서 액세스할 수 없는 기본 클래스를 사용 하는 경우 오류가 발생 합니다.
