---
title: 컴파일러 오류 C2384 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2384
dev_langs:
- C++
helpviewer_keywords:
- C2384
ms.assetid: 8145f7ad-31b1-406d-ac43-0d557feab635
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f3aa9ec8a6a94f53123c443a1149df7cdbc95c83
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46020461"
---
# <a name="compiler-error-c2384"></a>컴파일러 오류 C2384

'member' : 관리되는 클래스 또는 WinRT 클래스의 멤버에__declspec(thread)를 적용할 수 없습니다.

합니다 [스레드](../../cpp/thread.md) `__declspec` 한정자는 관리 되는 멤버 또는 Windows 런타임 클래스에서 사용할 수 없습니다.

관리 코드의 정적 스레드 로컬 저장소는 정적으로 로드된 DLL에 대해서만 사용할 수 있습니다(프로세스가 시작될 때 DLL을 정적으로 로드해야 함). Windows 런타임은 스레드 로컬 저장소를 지원하지 않습니다.

다음 줄은 C++/CLI 코드에서 C2384 오류가 발생하는 경우 및 이를 해결하는 방법을 보여 줍니다.

```
// C2384.cpp
// compile with: /clr /c
public ref class B {
public:
   __declspec( thread ) static int tls_i = 1;   // C2384

   // OK - declare with attribute instead
   [System::ThreadStaticAttribute]
   static int tls_j;
};
```