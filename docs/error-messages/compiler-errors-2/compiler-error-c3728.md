---
description: '자세한 정보: 컴파일러 오류 C3728'
title: 컴파일러 오류 C3728
ms.date: 11/04/2016
f1_keywords:
- C3728
helpviewer_keywords:
- C3728
ms.assetid: 6b510cb1-887f-4fcd-9a1f-3bb720417ed1
ms.openlocfilehash: 0cfcbd38928a153e3f5a58c1ec66b7e1c5bfd08d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97245098"
---
# <a name="compiler-error-c3728"></a>컴파일러 오류 C3728

' event ': 이벤트에 raise 메서드가 없습니다.

C #과 같은 언어를 사용 하 여 생성 된 메타 데이터 (예: c # [#using](../../preprocessor/hash-using-directive-cpp.md) )를 사용 하 여 이벤트가 정의 된 클래스 외부에서 발생 하는 것을 허용 하지 않으며, CLR 프로그래밍을 사용 하는 Visual C++ 프로그램에서 이벤트를 발생 시 키 려 고 했습니다.

C #과 같은 언어로 개발 된 프로그램에서 이벤트를 발생 시키려면 이벤트를 포함 하는 클래스가 이벤트를 발생 시키는 공용 메서드를 정의 해야 합니다.
